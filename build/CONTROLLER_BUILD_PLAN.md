# Intellivision II / Sears-compatible controller build plan

## Target

Build a compact replacement hand controller matching the saved listing: a
3D-printed, wired controller with a four-way D-pad, twelve-key number pad,
and three action buttons. It plugs into an Intellivision II or Sears Super
Video Arcade removable-controller port. The reference photograph is
[`reference-main.webp`](reference-main.webp).

This is a **passive controller**. It does not need a microcontroller, firmware,
USB interface, battery, or separate power supply. Every control simply grounds
one or more console input lines.

## Scope and compatibility

The number pad and three action buttons can reproduce the original controller
inputs completely. A conventional four-way D-pad can reproduce only four of
the original disc's sixteen directions. This is intentional for this compact
design, but it will not be a full substitute for a disc in games that depend
on its intermediate directions.

The listed controller uses the proprietary removable-controller plug. Confirm
the pin numbering from the *mating console socket* before soldering: connector
views often reverse pin order. The safest source of the plug and cable is a
non-working Intellivision II/Sears controller.

## Parts for one controller

| Qty. | Part | Notes |
|---:|---|---|
| 1 | Two-layer custom PCB | About 125 x 70 mm, final size set by the enclosure. |
| 1 | Original-style 9-conductor cable and console plug | Harvest from a donor controller if possible. |
| 1 | 4-way D-pad mechanism | Four 6 x 6 mm tactile switches plus a printed cap and centre pivot. |
| 15 | Tactile switches | Twelve keypad switches and three action switches; select a low-profile type for the keypad. |
| 1 | 3D-printed top shell | Cream/beige PETG, ABS, or ASA. |
| 1 | 3D-printed bottom shell | Black PETG, ABS, or ASA. |
| 12 | Printed keypad caps | `1`–`9`, `C`, `0`, `E`; use embossed legends or paint-filled recesses. |
| 3 | Round action caps | Printed or commercial caps sized to the selected switches. |
| 6 | M2 or M2.5 screws and heat-set inserts | The reference controller has six underside screws. |
| 1 | Cable clamp / strain-relief | Printed feature in the shell; do not rely on solder joints. |

## Electrical design

The cable has eight sense lines (`S1`–`S8`) and ground. Each button connects
the indicated sense lines to ground when pressed. Use a broad ground pour and
route the eight sense lines directly to the cable pads. Keep adjacent cable
pads clearly labelled on both PCB sides.

### Keypad and action matrix

| Control | Ground these console lines |
|---|---|
| `1` | S4 + S6 |
| `2` | S4 + S7 |
| `3` | S4 + S8 |
| `4` | S3 + S6 |
| `5` | S3 + S7 |
| `6` | S3 + S8 |
| `7` | S2 + S6 |
| `8` | S2 + S7 |
| `9` | S2 + S8 |
| `C` / Clear | S1 + S6 |
| `0` | S1 + S7 |
| `E` / Enter | S1 + S8 |
| top action | S6 + S8 |
| lower-left action | S7 + S8 |
| lower-right action | S6 + S7 |

Each switch joins its listed signal pads to the common ground pad. No active
components are required. Avoid pressing multiple keypad/action switches at
once; the original interface is a combination-coded input, not an independent
keyboard matrix.

### D-pad

Assign the cardinal directions as follows, then confirm in a game before
committing to labels or final assembly:

| D-pad direction | Grounded line |
|---|---|
| Up | S2 |
| Right | S3 |
| Down | S4 |
| Left | S1 |

This direct mapping yields the four cardinal disc positions. Do **not** assume
that pressing two D-pad switches produces a correct original diagonal; the
sixteen-position disc encodes several directions with special combinations.

## Mechanical design

1. Start from the reference photograph, not an assumed original-controller
   dimension. Make a 1:1 paper layout for the D-pad, keypad, and buttons, then
   size the shell around the selected switches and cable clamp.
2. Make the top shell a shallow wedge with 2.0–2.4 mm walls. Recess each cap
   opening so no cap can fall into the shell.
3. Put PCB mounting posts in the bottom shell, with at least 0.5 mm clearance
   around switch bodies and cable solder joints.
4. Print the D-pad as one part with a central underside pivot. The cap should
   rock far enough to actuate one tact switch without pressing its neighbours.
5. Use rounded key caps with 0.2–0.4 mm lateral clearance in their openings.
   Test a small four-key section before printing the full shell.
6. Add a bar or two-post clamp inside the cable exit. Clamp the cable jacket,
   never the individual conductors.
7. Install heat-set inserts only after a shell test-fit. A slight misalignment
   is much easier to correct in a prototype than in a finished case.

## Build order

1. **Acquire and map the plug.** With a continuity meter, label cable wires to
   the connector pins. Record the result in the PCB project. Do not copy a
   pinout without checking its viewing direction.
2. **Prototype the circuit on perfboard.** Wire one keypad switch and one
   action switch. Confirm that each works on the target console.
3. **Design the PCB in KiCad.** Add test pads for ground and S1–S8. Run ERC/DRC
   and print the board outline at full scale against the shell drawing.
4. **Order three PCB prototypes.** This makes connector or layout corrections
   inexpensive.
5. **Print a mechanical prototype.** Test cap travel, button spacing, cable
   exit, and the position of every mounting hole before finishing the case.
6. **Assemble and bench-test.** Before connecting to a console, verify with a
   meter that no signal line is grounded at rest and that every switch produces
   only its specified closure.
7. **Console-test in stages.** Test the D-pad, every number key, Clear, Enter,
   and all three action buttons in both controller ports.
8. **Finish the enclosure.** Sand/prime/paint only after the electrical and
   ergonomic prototype is proven. Add the `INTY` art with a vinyl decal,
   UV-print, or paint-filled engraving.

## Acceptance checklist

- At rest, S1–S8 are open to ground.
- Each keypad key grounds exactly its two specified lines.
- Each action button grounds exactly its two specified lines.
- Each D-pad direction grounds one and only one specified line.
- Pulling the cable does not transfer force to PCB solder pads.
- All six case screws engage inserts without splitting the shell.
- The controller works in both ports and after repeated cable flexing.

## Future full-disc variant

For faithful 16-direction control, replace the D-pad with a sixteen-position
disc and a dedicated contact arrangement, or add an externally powered
microcontroller plus open-drain outputs that assert the exact original
line-combinations. Keep that as a separate revision: it is materially more
complex than this passive gamepad.
