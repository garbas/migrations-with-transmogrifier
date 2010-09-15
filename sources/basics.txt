Basics
======

buildout configuration file::

    [transmogrifier]
    pipeline =
       source
       transform 1
       transform 2
       create
    
    [source]
    blueprint = example.transmogrifier.source
    
    [transform 1]
    blueprint = example.transmogrifier.transform
    from_field = text 
    to_field = text
    transform = rst
    condition = python:item['filename'].endswith('.rst')
    
    [transform 2]
    blueprint = example.transmogrifier.transform
    from_field = text 
    to_field = description
    transform = get_first_paragraph
    
    [create]
    blueprint = example.transmogrifier.constructor

::

    <configure
        xmlns="http://namespaces.zope.org/zope"   
        xmlns:tg="http://namespaces.plone.org/transmogrifier"
        i18n_domain="example.transmogrifier">
    
      <tg:registerConfig
        name="exampleconfig"
        title="Example"
        description="Example pipeline config"
        configuration="example.cfg"
        />


Pipeline
--------

**ordered list of blueprints**

::

    [transmogrifier]
    pipeline =
       source
       transform 1
       transform 2
       create

Blueprints
----------

source blueprints
"""""""""""""""""

::

    [source]
    blueprint = example.transmogrifier.source

::

    <utility
        component=".source.ExampleSource"
        name="example.transmogrifier.source"
        />

::

    class ExampleSource(object):
        classProvides(ISectionBlueprint)
        implements(ISection)

        def __init__(self, transmogrifier, name, options, previous):
            self.previous = previous
            self.name = name

        def __iter__(self):
            for item in self.previous:
                yield item

            for record in ReadJSONFile():
                yield dict(_path=normalize(record['title']),
                           _type=”Document”,
                           title=record['title'],
                           text=record['text'])


tranform blueprints
"""""""""""""""""""

::

    [transform 1]
    blueprint = example.transmogrifier.transform
    from_field = text 
    to_field = text
    transform = rst
    condition = python:item['filename'].endswith('.rst')

::

    <utility
        component=".transform.ExampleTransform"
        name="example.transmogrifier.transform"
        />

::

    class ExampleTranform(object):
        classProvides(ISectionBlueprint)
        implements(ISection)

        def __init__(self, transmogrifier, name, options, previous):
            self.previous = previous
            self.from_field = options['from_field']
            self.to_field = options['to_field']
            self.tranform = options['tranform']
            self.condition = Condition(condition, transmogrifier, name, options)

        def __iter__(self):
            for item in self.previous:
                if self.condition(item):
                    if 'rst' == self.transform:
                        item[self.to_field] = TransformFromRSTToHTML(item[self.from_field])
                    elif 'get_first_paragraph' == self.transform:
                        item[self.to_field] = GetFirstParagraph(item[self.to_field])
                yield item

