Default blueprints
==================

``collective.transmogrifier.sections.constructor``
--------------------------------------------------

contstructs plone content (_type, _path)


``collective.transmogrifier.sections.savepoint``
------------------------------------------------

commits a savepoint which as result free up memory

``collective.transmogrifier.sections.csvsource``
------------------------------------------------

reads csv file and puts lines of it in pipeline

``collective.transmogrifier.sections.splitter``
-----------------------------------------------

splits pipeline, which lets you proccess data flow separatly

``collective.transmogrifier.sections.manipulator``
--------------------------------------------------

rename, copy, delete data in pipeline

``collective.transmogrifier.sections.condition``
------------------------------------------------

Lets you discard data from pipeline

``collective.transmogrifier.sections.inserter``
-----------------------------------------------

Lets you create new fields for data (from other fields)

``collective.transmogrifier.sections.codec``
--------------------------------------------

Changes encoding for data in pipeline

``collective.transmogrifier.sections.constructor``
--------------------------------------------------

Creates parent folders when item needs them
