# Overview

I wanted to tweak several planetary modifiers to provide more flavorful and useful bonuses.

1. The C.A.R.E Interactive Interface is an economic optimization engine, so I wanted it to give a bonus to trade value
2. The Extensive Moon System modifier adds mining districts and output... to gas giants which can't be colonized, so I changed it to give a bonus to mining stations (but not research stations) that also applies to any unhabitable moons, and moved the bonus mineral jobs production and mining districts onto any/all habitable moons
3. The Resource Consolidation origin goes through all the trouble of shrinking gas giants and converting them to molten worlds tagged with the "Chthonian Planet" modifier but then a game start event clears all modifiers, so I wanted to stop blanket deleting planetary modifiers in starting systems
4. Allow multiple planetary modifiers to spawn on any given planet, as suggested by the majority of the planetary modifier spawn code (which weights some higher or lower in the presence of other planetary modifiers)
5. Convert all the "mineral richness" related modifiers to provide bonuses to the miner job category (rather than only minerals production) and mining station output, similar to the changes for \#2

# Compatibility

This mod should be fairly compatible with other mods.  Incompatibilities would likely occur if other mods also overwrite or add same the planetary or static modifier IDs.  If another mod is attempting to specify the same modifiers: first in wins for static modifiers, but last in wins for planetary modifiers.  These eight `static_modifiers` are overridden:

* `asteroid_impacts`
* `extensive_moon_system`
* `carbon_world`
* `asteroid_belt`
* `mineral_rich`
* `ultra_rich`
* `mineral_poor`
* `pm_planetary_mechanocalibrator` (there is also a `planet_modifiers` entry with the same key but it is unchanged)

And these twenty-three `planet_modifiers` are overridden:

* `pm_hazardous_weather`
* `pm_dangerous_wildlife`
* `pm_weak_magnetic_field`
* `pm_strong_magnetic_field`
* `pm_unstable_tectonics`
* `pm_tidal_locked`
* `pm_chthonian_planet`
* `pm_asteroid_impacts`
* `pm_extensive_moon_system`
* `pm_carbon_world`
* `pm_wild_storms`
* `pm_low_gravity`
* `pm_high_gravity`
* `pm_mineral_rich`
* `pm_ultra_rich`
* `pm_mineral_poor`
* `pm_titanic_life`
* `pm_asteroid_belt`
* `pm_natural_beauty`
* `pm_atmospheric_aphrodisiac`
* `pm_atmospheric_hallucinogen`
* `pm_lush`
* `pm_bleak`

This mod also overrides a game setup event `game_setup.2`. I find it unlikely other mods would be changing this event (it clears planetary modifiers for home systems); in any case first in wins for events.

Built for Stellaris version 3.7 "Canis Minor."  Not compatible with achievements.  Largely compatible with Guilli's Planet Modifiers and Features - Guilli's static modifier changes will take precedence but there are no error-causing conflicts.  Also has built-in compatibility with Planetary Diversity.

### When to Install

This mod can be safely added to your save after the game has started, but not removed.  If this mod is not active at game start, you will miss out of the Extensive Moon System (Moon) modifier being applied to the moons of gas giants with Extensive Moon System and minerals being added to some planets with modifiers but no deposits.  Removing this mod will result in unknown planetary modifiers - which Stellaris may or may not handle gracefully.

## Known Issues

Overriding static modifiers and preempting events cause the game to log errors, so expect to see twenty-four (!) lines in the error.log file similar to:

```
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_hazardous_weather already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 4
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_dangerous_wildlife already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 24
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_weak_magnetic_field already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 54
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_strong_magnetic_field already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 79
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_unstable_tectonics already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 104
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_tidal_locked already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 133
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_chthonian_planet already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 157
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_asteroid_impacts already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 177
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_extensive_moon_system already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 206
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_carbon_world already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 234
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_wild_storms already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 260
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_low_gravity already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 280
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_high_gravity already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 321
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_mineral_rich already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 362
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_ultra_rich already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 396
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_mineral_poor already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 421
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_titanic_life already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 452
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_asteroid_belt already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 484
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_natural_beauty already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 512
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_atmospheric_aphrodisiac already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 535
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_atmospheric_hallucinogen already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 555
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_lush already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 575
[20:57:42][game_singleobjectdatabase.h:165]: Object with key: pm_bleak already exists, using the one at  file: common/planet_modifiers/01_planetary_modifier_enhancements_planetary_modifier_overrides.txt line: 606
[20:57:44][eventmanager.cpp:368]: an event with id [game_start.2] already exists!  file: events/game_start.txt line: 253
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
* 2.3.0 Remove monthly pulse event, instead fire when a single-player game is loaded
* 2.4.0 Marked compatible with Stellaris version 3.1 "Lem" - no script changes
* 2.5.0 Allow multiple modifiers to spawn per planet, adjust mineral-based static modifiers to affect miner-category output and also mining stations
    * Overwrite most built-in planetary modifiers to allow multiple modifiers to spawn on a single planet (many modifiers were already coded to have increased or decreased spawn chances in the presence of other modifiers - so disabling them for planets with >1 modifier made no sense)
    * Overwrite many static modifiers related to planetary modifiers that affect planetary natural resources - instead of minerals-only output, these modifiers affect all "planet_miners" category jobs _and_ affect gatherer stations (aka mining stations) in orbit of the planet - e.g. Carbon World can only spawn on barren planets (which are unhabitable)
    * Moons of moons in Extensive Moon Systems now also have the Extensive Moon System Moon planetary modifier added
    * At game start, ensure unhabitable planets with a plentiful minerals modifier(s) have a minerals deposit if they doesn't already have an orbital deposit
* 2.6.0 Marked compatible with Stellaris version 3.2 "Herbert" - no script changes
* 2.7.0 Marked compatible with Stellaris version 3.3 "Libra" - no script changes
* 3.0.0 Update for Stellaris version 3.4 "Cepheus"
    * Integrate minor enhancement to the Carbon World spawn chances
    * Use memory optimization feature for effects and triggers
* 3.1.0 Use triggers for `habitable_planet` and `uninhabitable_regular_planet` instead of copy/pasted, inconsistent lists of planet classes - should also lead to wider compatibility with mods that replace these triggers to support additional planet classes
* 4.0.0 Update for Stellaris version 3.6 "Orion" (and changes from version 3.5 "Fornax") - integrate `game_start.2` changes
* 5.0.0 Add a compatibility trigger for other mods to check whether this one is active, remove old compatibility global flag
* 5.1.0 Add built-in support for [Planetary Diversity](https://steamcommunity.com/sharedfiles/filedetails/?id=819148835)
* 6.0.0 Update for Stellaris version 3.7 "Canis Minor" - integrate `game_start.2` changes

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/planetary_modifier_enhancements)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.