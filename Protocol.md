# Kenwood SWC Protocol

The protocol *appears* to be an implementation of the NEC IR transmission protocol, also known as "Japanese Format".

The 38kHz carrier is **not** used, as commodity IR receivers automatically decode this and provide a bitstream output.

The input to the radio is **inverted** (active-low), with an internal pullup, so it should be pulled to GND to transmit.

The NEC protocol uses pulse-distance encoding, with the follwing schema:

| Logical | Pulse     | Space      |  Total    |
| ------- | -----     | -----      |  -----    |
|   `0`   | `562.5µs` | `562.5µs`  | `1.125ms` |
|   `1`   | `562.5µs` | `1.6875ms` | `2.25ms`  |

The standard implementation of this, and the one Kenwood uses, is a 32-bit (four byte) transmission, with an 8-bit address and 8-bit command, with the second and fourth bytes being the logical inverse of the first and second respectively.

That is, `{Address}¬{Address}{Command}¬{Command}`.

Kenwood uses only a single address, `B9x`, `185d`, `10111001d`.

Bytes are transmitted *Least Significant Bit* **first**.

A leading pulse is used, `16` times the pulse length of a logical data bit, followed by a space of 8 bit-lengths.

The data then follows, in the format described above.

A final single length pulse is sent to terminate the transmission.

The full transmission for a 32-bit address and command combo is thus as follows:

| Segment               | Timing    |
| -------               | ------    |
| Initial Pulse         | `9ms`     |
| Initial Space         | `4.5ms`   |
| `{Address}¬{Address}` | `27ms`    |
| `{Command}¬{Command}` | `27ms`    |
| Termination Pulse     | `562.5µs` |

As each byte is transmitted as byte¬byte, they have equal transmission length, and thus each transmission is `67.5ms` in length.

## Repeat
 At this time, I am unable to determine whether repeat signals are interpreted correctly, and whether they have any function

However, for clarity's sake, I will include them nonetheless.

The repeat code is transmitted at `108ms` intervals, and is comprised of a `9ms` pulse, followed by a `2.25ms` space, and a `562.5µs` termination pulse.

| Segment | Timing    |
| ------- | ------    |
| Pulse   | `9ms`     |
| Space   | `2.25ms`  |
| Pulse   | `562.5µs` |

------

# References

[San Bergmans - NEC Protocol](https://www.sbprojects.net/knowledge/ir/nec.php)

[Altium - NEC Infrared Transmission Protocl](https://techdocs.altium.com/display/FPGA/NEC+Infrared+Transmission+Protocol)

[Michal Babik - Ford to Kenwood Radio Adapter](https://init6.pomorze.pl/projects/kenwood_ford/)