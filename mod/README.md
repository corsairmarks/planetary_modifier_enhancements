# Overview

I wanted to tweak a few modifiers related to planetary bonuses to more flavorful bonuses.

1. The C.A.R.E Interactive Interface is an economic optimization engine, so I wanted it to give a bonus to trade value
2. The Extensive Moon System modifier adds mining districts and output... to gas giants which can't be colonized, so I changed it to give a bonus to mining stations (but not research stations) that also applies to any unhabitable moons, and moved the bonus mineral jobs production and mining districts onto any/all habitable moons
3. The Resource Consolidation origin goes through all the trouble of shrinking gas giants and converting them to molten worlds tagged with the "Chthonian Planet" modifier but then a game start event clears all modifiers, so I wanted to stop blanket deleting planetary modifiers in starting systems

# Compatibility

This mod should be widely compatible with other mods.  Incompatibilities would likely occur if other mods also overwrite or add same the planetary or static modifier IDs.  If another mod is attempting to specify the same modifiers: first in wins for static modifiers, but last in wins for planetary modifiers.  For now, only these `static_modifiers` are overridden (and no `planet_modifiers`):

* `extensive_moon_system`
* `pm_planetary_mechanocalibrator` (there is also a `planet_modifier` with the same key but it is unchanged)

This mod also overrides a game setup event `game_setup.2`. I find it unlikely other mods would be changing this event (it clears planetary modifiers for home systems); in any case first in wins for events.

Built for Stellaris version 3.1.* "Lem."  Not compatible with achievements.

### When to Install

This mod can be safely added to your save after the game has started, but not removed.  If this mod is not active at game start, you will miss out of the Extensive Moon System (Moon) modifier being applied to the moods of gas giants with Extensive Moon System.  Removing this mod will result in unknown planetary modifiers - which Stellaris may or may not handle gracefully.

## Known Issues

Overriding an event causes the game to log an error, so expect to see one line in the error.log file similar to:

```
[20:11:11][eventmanager.cpp:355]: an event with id [game_start.2] already exists!  file: events/game_start.txt line: 213
```

## Changelog

* 1.0.0 Initial version
* 2.0.0 Reverted to a single modifier for `extensive_moon_system_moon` that adds the bonus for habitable and unhabitable moons
* 2.0.1 Fix renamed trigger usage
* 2.0.2 Fix the **other** renamed trigger usage
* 2.0.3 Add preview images
* 2.1.0 Add overridden `game_start.2` event to avoid clearing planetary modifiers in starting systems (now limited to only homeworlds as described in code comments), add tag "Galaxy Generation"
* 2.2.0 Add event to set flag to mark as installed
* 2.2.1 Remove extra images files to keep distribution lightweight (no script changes)
* 2.3.0 Remove monthy pulse event, instead fire when a single-player game is loaded
* 2.4.0 Marked compatible with Stellaris version 3.1.* "Lem" - no actual changes
* 2.5.0 Allow multiple modifiers to spawn per planet, adjust mineral-based static modifiers to affect miner-category output and also mining stations
    * Overwrite most built-in planetary modifiers to allow multiple modifiers to spawn on a single planet (many modifiers were already coded to have increased or decreased spawn chances in the presence of other modifiers - so disabling them for planets with >1 modifier made no sense)
    * Overwrite many static modifiers related to planetary modifiers that affect planetary natural resources - instead of minerals-only output, these modifiers affect all "planet_miners" category jobs _and_ affect gatherer stations (aka mining stations) in orbit of the planet - e.g. Carbon World can only spawn on barren planets (which are unhabitable)
    * Moons of moons in Extensive Moon Systems now also have the Extensive Moon System Moon planetary modifier added

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/planetary_modifier_enhancements)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.