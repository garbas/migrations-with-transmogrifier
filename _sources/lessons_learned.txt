Lessons learned
===============

Migration from Plone 2.0 to 4.0
-------------------------------

 * >100.000 content objects
 * >40GB in size
 * many custom products
 * usual migration/upgrade failed

So what did I learn:

make migration repeatable (eg: using GenericSetup upgrade steps)
----------------------------------------------------------------

migrate parts of page separatly
-------------------------------

split migration into export and import part
-------------------------------------------

monitor and time migration
--------------------------

don't complicate in making blueprints extra reusable
----------------------------------------------------
