# Kenwood SWC Mappings

## **CAUTION**
 Some of the commands in this map appear to be internal testing commands, used by the manufacturer to ensure functionality of the unit as part of Quality Control.
 Caution should be exercised when testing any command, and it is **strongly** recommended that all testing is done on a bench, not in a vehicle.
 As a precaution, ensure you can disconnect both `ACC` and `BAT` from the unit promptly, in case of untoward behaviour.

### Note:
 The following commands were manually mapped on a Kenwood KDC-BT34U, using an early (non-public) build of [x13-me/Kenwood-SWC-Arduino](https://github.com/x13-me/Kenwood-SWC-Arduino), they may not work on all units, and may behave in a different manner to that described.

Some command sequences have differing behaviour, depending on the `Source` selected or `Menu` the unit is in, so the following table reflects that.

This table represents all currently known mappings, however, should be considered incomplete, as not all command/mode pairs have been tested.
`-` means the command did not cause any response.

|dec|hex|bin     |Menu               |Standby            |TUNER mode         |iPod mode          |CD Mode            |
|---|---|--------|-------------------|-------------------|-------------------|-------------------|-------------------|
|1  |01 |00000001|-                  |-                  |Preset 1           |-                  |-                  |
|2  |02 |00000010|-                  |-                  |Preset 2           |-                  |-                  |
|3  |03 |00000011|-                  |-                  |Preset 3           |-                  |-                  |
|4  |04 |00000100|-                  |-                  |Preset 4           |-                  |-                  |
|5  |05 |00000101|-                  |-                  |Preset 5           |-                  |-                  |
|6  |06 |00000110|-                  |-                  |Preset 6           |-                  |-                  |
|10 |0A |00001010|-                  |-                  |Scan -             |Previous           |Previous           |
|11 |0B |00001011|-                  |-                  |Scan +             |Next               |Next               |
|12 |0C |00001100|Previous           |-                  |Switch LW          |-                  |-                  |
|13 |0D |00001101|Next               |-                  |Page FM            |-                  |-                  |
|14 |0E |00001110|Enter              |-                  |-                  |Play/Pause         |Play/Pause         |
|15 |0F |00001111|-                  |-                  |$$ BLINKS DISPLAY  |-                  |$$ BLINKS DISPLAY  |
|19 |13 |00010011|SOURCE             |SOURCE             |SOURCE             |SOURCE             |SOURCE             |
|20 |14 |00010100|Vol+               |-                  |Vol+               |Vol+               |Vol+               |
|21 |15 |00010101|Vol-               |-                  |Vol-               |Vol-               |Vol-               |
|22 |16 |00010110|ATT On/Off         |-                  |ATT On/Off         |ATT On/Off         |-                  |
|23 |17 |00010111|-                  |Audio Control      |Audio Control      |Audio Control      |Audio Control      |
|28 |1C |00011100|SOURCE             |SOURCE             |SOURCE             |SOURCE             |SOURCE             |
|30 |1E |00011110|SOURCE             |SOURCE             |SOURCE             |SOURCE             |SOURCE             |
|31 |1F |00011111|SOURCE             |SOURCE             |SOURCE             |SOURCE             |SOURCE             |
|131|83 |10000011|POWER OFF          |POWER OFF          |POWER OFF          |                   |POWER OFF          |
|133|85 |10000101|BACK               |-                  |-                  |                   |                   |
|134|86 |10000110|Previous           |-                  |-                  |                   |                   |
|135|87 |10000111|Next               |-                  |-                  |                   |                   |
|139|8B |10001011|EXIT               |-                  |-                  |                   |                   |
|142|8E |10001110|EXIT               |-                  |-                  |                   |                   |
|146|92 |10010010|$$ PHONE           |$$ PHONE           |$$ PHONE           |                   |$$ PHONE           |
|216|D8 |11011000|FACTORY TEST       |FACTORY TEST       |FACTORY TEST       |FACTORY TEST       |FACTORY TEST       |
|217|D9 |11011001|FACTORY RESET      |FACTORY REST       |FACTORY RESET      |FACTORY RESET      |FACTORY RESET      |
|220|DC |11011100|FACTORY PROGRAMMING|FACTORY PROGRAMMING|FACTORY PROGRAMMING|FACTORY PROGRAMMING|FACTORY PROGRAMMING|

#### Command explanations
 The following table describes the effect of each command referenced

| Command             | Explanation                                                                                                                                                |
| -------             | -----------                                                                                                                                                |
| Preset X            | Changes to radio preset X, exact behaviour varies depending on FM/MW/LW modes                                                                              |
| Scan -              | Scans downwards for next solid signal                                                                                                                      |
| Scan +              | Scans upwards for next solid signal                                                                                                                        |
| Vol+                | Volume increase                                                                                                                                            |
| Vol-                | Volume decrease                                                                                                                                            |
| Previous (Playback) | Previous track - same as on faceplate                                                                                                                      |
| Next (Playback)     | Next track - same as on faceplate                                                                                                                          |
| Previous (Menu)     | Previous menu option, same as rotating dial once CCW                                                                                                       |
| Next (Menu)         | Next menu option, same as rotating dial once CW                                                                                                            |
| Enter (Menu)        | Enters menu option, same as clicking dial                                                                                                                  |
| BACK (Menu)         | Goes back one menu level - same as on faceplate                                                                                                            |
| EXIT (Menu)         | Immediately exits menu, regardless of current level                                                                                                        |
| Switch LW           | Switches to long-wave tuner                                                                                                                                |
| Page FM             | Switches to FM tuner if not already, then selects between pages of FM presets                                                                              |
| $$ BLINKS DISPLAY   | Unsure of function, causes time/frequency display to blink `---`                                                                                           |
| SOURCE              | Changes to next available source - same as on faceplate                                                                                                    |
| POWER OFF           | Immediately turns off device, same as long-pressing the power button                                                                                       |
| $$ PHONE            | Opens phone menu - same as on faceplate                                                                                                                    |
| FACTORY TEST        | **CAUTION**: Turns on all LED segments in display, sets volume to maximum, used by factory                                                                 |
| FACTORY RESET       | **CAUTION**: Resets unit immediately, same as pressing button behind faceplate                                                                             |
| FACTORY PROGRAMMING | ***EXTRA CAUTION:*** Displays `SN WRITING`, appears to be a factory programming mode - ***DO NOT SEND THIS COMMAND*** it may irreparably damage the device |