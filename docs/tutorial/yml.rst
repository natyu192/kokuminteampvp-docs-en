Writing YML
=============

How to write config.yml in the map folder.

.. toctree::
   :maxdepth: 1
   :caption: Contents:

* :ref:`base`
* :ref:`spawn`
* :ref:`region`
* :ref:`kit`

.. _base:

Basic config.yml
----------------------------

::

	name: 'Map Name'
	gametype: gamemode
	allow-build: true
	fall-damage: true
	
	// Write here the setting such as spawn, kits, and special settings of gametype.

===================== ====================================== ===================================== =============
Item(\* is required)  Description                            Value                                 Default
===================== ====================================== ===================================== =============
\*name                The name of the map.                   String
\*gametype            The gametype.                          :doc:`../data/gametype`
allow-build           Allows breaking/placing blocks.        true/false                            true
fall-damage           Enables fall damage.                   true/false                            true
allow-damage          Enables any damage.                    true/false                            true
===================== ====================================== ===================================== =============

.. _team:

Teams
-----------------------

Teams can be defined like this.

::

	teams:
	  red:
	    name: 'Red Team'
	    color: red
	    max: 16
	  blue:
	    name: 'Blue Team'
	    color: blue
	    max: 16

The value such as ``red`` and ``blue`` are Team ID used on settings such as spawns and kits. They don't have to be same as ``color`` value.

===================== ===================================================================== =========================================== =========================
Item(\* is required)  Description                                                           Value                                       Default
===================== ===================================================================== =========================================== =========================
\*name                The name of Team. If it is too long, it won't be displayed properly.  String
\*color               The color applied on Player Name and Team Name.                       :doc:`../data/chatcolor`
\*max                 Maximum players for this team.                                        Integer
===================== ===================================================================== =========================================== =========================

.. _spawn:

Spawns
-----------------------

Spawns can be defined like this.

::

	location:
	  red:
	    x: 0.0
	    y: 14.5
	    z: 128.0
	    yaw: -180
	    pitch: 0
	  blue:
	    x: 0.0
	    y: 14.5
	    z: -127.0
	    yaw: 0
	    pitch: 0
	  spectator:
	    x: -51.5
	    y: 46
	    z: 0.5
	    yaw: -90
	    pitch: 0

The value such as ``red`` and ``blue`` are Team ID.

===================== ======================================================= =========================================== =========================
Item(\* is required)  Description                                             Value                                       Default
===================== ======================================================= =========================================== =========================
\*spectator           The spawn position when a player join the game.         X, Y, Z
===================== ======================================================= =========================================== =========================

.. _region:

Regions
---------------
By setting regions up, deny entering and building in an enemy's base. Region can be defined as many as you want.

Regions can be defined like this.

::

	regions:
	  bluebase:
	    team: blue
	    name: 'Blue Base'
	    enter: false
	    pos1:
	      x: -15.5
	      y: 0
	      z: -135
	    pos2:
	      x: 15.5
	      y: 255
	      z: -118.5
	    deny-message: "You cannot enter the enemy's base."
	  redbase:
	    team: red
	    name: 'Red Base'
	    enter: false
	    pos1:
	      x: 15.5
	      y: 0
	      z: 135.5
	    pos2:
	      x: -15.5
	      y: 255
	      z: 118.5
	    deny-message: "You cannot enter the enemy's base."

The value such as ``bluebase`` and ``redbase`` are used internally. It can be anything.

===================== ============================================================ ===================================== ============================
Item(\* is required)  Description                                                  Value                                 Default
===================== ============================================================ ===================================== ============================
\*team                The team that can bypass ``enter`` flag.                     Team ID
\*name                | The name of Region.                                        String
                      | This is currently not used but may be used in the future.
enter                 Allows enter the Region.                                     true/false                            false
\*pos1                Pos 1 of the Region.                                         X, Y, Z
\*pos2                Pos 2 of the Region.                                         X, Y, Z
deny-message          | The message that                                           String                                You cannot enter that area.
                      | displayed when a team that cannot enter the region.
===================== ============================================================ ===================================== ============================

.. _kit:

Kits
---------------
Kits can be defined per team.

Kits can be defined like this.

::

	kits:
	  red:
	    armor:
	      helmet:
	        material: LEATHER_HELMET
	        slot: 40
	        leather_color: RED
	        soulbound: true
	      chestplate:
	        material: LEATHER_CHESTPLATE
	        slot: 41
	        leather_color: RED
	        soulbound: true
	      leggings:
	        material: LEATHER_LEGGINGS
	        slot: 42
	        leather_color: RED
	        soulbound: true
	      boots:
	        material: LEATHER_BOOTS
	        slot: 43
	        leather_color: RED
	        soulbound: true
	  blue:
	    armor:
	      helmet:
	        material: LEATHER_HELMET
	        slot: 40
	        leather_color: BLUE
	        soulbound: true
	      chestplate:
	        material: LEATHER_CHESTPLATE
	        slot: 41
	        leather_color: BLUE
	        soulbound: true
	      leggings:
	        material: LEATHER_LEGGINGS
	        slot: 42
	        leather_color: BLUE
	        soulbound: true
	      boots:
	        material: LEATHER_BOOTS
	        slot: 43
	        leather_color: BLUE
	        soulbound: true
	  parent:
	    inventory:
	      sword:
	        material: IRON_SWORD
	        slot: 0
	        soulbound: true
	        enchantments:
	        - DAMAGE_ALL:1
	      bow:
	        material: BOW
	        slot: 1
	        soulbound: true
	      food:
	        material: BAKED_POTATO
	        slot: 2
	        amount: 16
	        soulbound: true
	      pickaxe:
	        material: DIAMOND_PICKAXE
	        slot: 3
	        soulbound: true
	      axe:
	        material: DIAMOND_AXE
	        slot: 4
	        soulbound: true
	      log:
	        material: LOG
	        slot: 5
	        amount: 32
	        soulbound: true
	      arrow:
	        material: ARROW
	        slot: 9
	        amount: 64
	        soulbound: true
	  kill-rewards:
	    gapple:
	      material: GOLDEN_APPLE
	      amount: 1
	      soulbound: false
	      lore:
	      - 'Tasty apple'
	      - 'An apple for Kill reward.'

The value such as ``red`` and ``blue`` are team ID, and the kit defined there will be applied for only that team. ``parent`` kit will be applied on the team kit.

``kill-rewards`` items are given on killing.

The value such as ``helmet`` and ``chestplate`` are used internally. It can be anything.

Item define:

===================== ======================================================= =========================================== =========================
Item(\* is required)  Description                                             Value                                       Default
===================== ======================================================= =========================================== =========================
\*material            The type of the item.                                   :doc:`../data/material`
\*slot                The slot that the item will be set.                     Integer
amount                The amount of the item.                                 Integer                                     1
damage                The damage of the item.                                 Integer                                     0
soulbound             If set true, it will be disappear when it was dropped.  true/false                                  false
displayName           The name of the item.                                   String
lore                  The description of the item.                            String
unbreakable           If set true, it will have unbreakable tag.              true/false                                  false
enchantments          Applies enchantments                                    :doc:`../data/enchantment`:Level(Integer)
leather_color         Dyes Leather armors.                                    :doc:`../data/dyecolor` or color code.
===================== ======================================================= =========================================== =========================

``leather_color`` can be specified with :doc:`../data/dyecolor` or Hex formatted color code. (Example: #5555ff) If you set with Hex formatted color code, it must be surrounded with ``''`` .

For ``slot`` , this image can be helpful.

.. image:: inventory.png