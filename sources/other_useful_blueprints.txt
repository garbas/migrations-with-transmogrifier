Other usefull blueprints
========================

``plone.app.transmogrifier``
----------------------------

Contains several blueprints for collective.transmogrifier pipelines,
commonly used to import content into a Plone site.

``quintagroup.transmogrifier``
------------------------------

May be used to export/import Plone site content. It also overrides
GenericSetup ``Content`` step so this package can be used out-the-box
to migrate site content.

``transmogrify.sqlalchemy``
---------------------------

This package implements the `transmogrify.sqlalchemy` blueprint which
executes a SQL statement, generally a query, and feeds the return values
from that query into the transmogrifier pipeline.

``pretaweb.funnelweb``
----------------------

Crawls web page and imports found html into plone.

``collective.blueprint.translationlinker``
------------------------------------------

A transmogrifier blueprint to create links between content items to mark
them as Products.LinguaPlone translations of each other.

``collective.blueprint.dancing``
--------------------------------

Contains several blueprints for collective.transmogrifier pipelines,
dedicated to the Plone product collective.dancing.
