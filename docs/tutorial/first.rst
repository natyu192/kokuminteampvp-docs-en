About the map folder
=======================

.. toctree::
   :maxdepth: 1
   :caption: 目次:

* :ref:`kouzou`
* :ref:`siyou`

.. _kouzou:

The map folder
-----------------------------------------

Directory Structure of the folder includes world and YML file will be like this::

	config.yml
	<map name>
	└─<map name>
		├─data
		└─region

.. _siyou:

How the plugin loads the maps
-----------------------------
The maps will be loaded from ``plugins/KokuminTeamPvP/maps`` folder in order of the ``map-rotation`` list in ``config.yml``.

config.yml (Example)::

	map-rotation:
	  - 'Map 1'
	  - 'Map 2'
	  - 'Map 3'

Also, when the map is loading, its folder(:ref:`Directory Structure <kouzou>`) will be copied from ``plugins/KokuminTeamPvP/maps`` and game will be played on there.
If you want to modify the map, you must be editing the map folder in ``plugins/KokuminTeamPvP/maps`` .
Modified map will be updated when it was loaded next.
