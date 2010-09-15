Example migration
=================

Problem
-------

 * Plone 2.0 site migrate Plone 4.0
 * plone site contains plone sites (yes this was possible in 2.0)
 * with some smart transforms in pipeline create subsites with ``collective.lineage``
 * lets not forget on localroles, states, workflows
 * also move users and groups

Steps
-----

 * export data to filesystem using extenal method with scripts that come
   with ``collective.blueprint.usersandgroups`` and
   ``collective.blueprint.jsonmigrator``
 * create tranmogrifier pipeline and register it with new site
 * import them using upgrade step


plone 2.0: http://localhost:8080/manage
plone 4.0: http://localhost:8081/manage
