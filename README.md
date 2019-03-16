# CustomLoadouts
An smod plugin similar to default-item but much more customisable to specific players. Can give items based on steamid, class, server rank and random chance or any combination of these.

Can also be used to set up special subclasses with customized loadouts with a customisable chance to get the loadout on spawn.

## Installation

Extract the release zip and place the contents in sm_plugins.

## Config

This plugin has it's own config which is placed in your global config folder when the plugin is run for the first time.

The plugin only has one option in the server config, `cl_global`, it decides whether to use the global config folder or not, defaults to true.

Default config:
```yaml
# Prints a confirmation whenever a player is given a loadout
verbose: true
# Prints debug messages
debug: false
# Adds a ms delay if needed for plugin compatibility
delay: 0

# This sets up the loadouts and the permission nodes required to get them
# For instance "customloadouts.donatorloadouts" gives all loadouts under the donatorloadouts node below, as long as the class and chance checks are successful.
customloadouts:
    # Name of this permission node
    donatorloadouts:
        # Class, check #resources in the SMOD discord server for class names, set to all for all classes
        all:
            # Percentage chance for item group to spawn
            - 50:
                # Items to spawn, must be all caps, check #resources in the SMOD discord server for item names.
                # You can start with REMOVEITEMS and REMOVEAMMO to delete the existing items/ammo.
                # All weapons spawn with one mag/clip loaded which cannot be removed, giving ammo adds the ammo directly to the player instead of spawning it as an item in their inventory.
                # This example has a 50% chance to spawn a coin to all players with the rank donator
                - COIN
            - 10:
                - MEDKIT
        SCIENTIST:
            - 10:
                - REMOVEITEMS
                - MAJOR_SCIENTIST_KEYCARD
                - MEDKIT
            - 5:
                - REMOVEITEMS
                - REMOVEAMMO
                - USP
                - DROPPED_9
                - DROPPED_9
                - MAJOR_SCIENTIST_KEYCARD
                - MEDKIT
    moderatorloadouts:
        CLASSD:
            - 30:
                - FLASHLIGHT
    adminloadouts:
        all:
            - 100:
                - MICROHID
                - MICROHID
                - MICROHID
                - MICROHID
                - MICROHID
                - MICROHID
                - MICROHID
                - MICROHID
```

You can add more entries by following the example above. I believe each config option is pretty self explanatory with the example above.  If you have any questions, you can ask them in my discord server at the link above.

## Command
| Command | Permission | Description |
|----     |----        |----         |
| `cl_reload` | `customloadouts.relaod` | Reloads the cl config.
