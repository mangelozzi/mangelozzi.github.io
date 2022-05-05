# KICAD Tips

## SYMBOL and FOOTPRINT NAMING

- Upper-case acronym's, e.g. `PCB`

## PCB

### FOOTPRINTS

- Refer to <https://klc.kicad.org/>
- Dimensions rounded off to nearest 0.01mm
- Silkscreen:
    - Reference text: 1mm high, 1mm wide, 0.15mm thick.
    - Lines: 0.15mm thick (as per IPC-7351C).
    - Offset from component to middle of silkscreen bounding box = 0.2mm
    - Dimensions rounded off to nearest 0.1mm so one can position items on a mm grid, and draw and connect to them.
- Fabrication:
    - Reference text: 1mm high, 1mm wide, 0.15mm thick.
    - Lines: 0.1mm thick

#### Importing graphics

One can import SVG graphics directly into the footprints/pcb editor
- Even if no stroke is applied, it will use the stroke width and make it appear. To get around this set the stroke width to 0.000001mm even with no stroke applied.

#### Footprint Positioning

- Pin 1 top left
- Negative pin on left.
- Rectangular shapes place horizontally (screens are generally wider)

#### Footprint renaming

- Part1:
    - `SMD`
    - `THT` for through hole
    - `Both` if can be SMD or `THT`
    - `Edge` for edge mount connectors, include edge mount DSUB connectors.
    - `PCB` for logos, mounting holes etc.
- Part2: Function:
    - `R_`
        - `Array`
        - `Sense`
    - `C_`
    - `CP_`
    - `D_`
    - `L_`
    - `Package_` (e.g. `SOIC-32`)
    - `Module_` (e.g. modem, arduino)
    - `Mounting_Hole_`
        - `size_desc`, e.g. `M3_low_l`
    - `Logo`
        - `Name_size`, e.g. `NanoCube_10x5mm`
- Part3: type
    - For capacitors: `Cer`, `Elect`, `Tant`
    - Resistors:
    - For housing
- Ending if applicable:
    `Manufacturer_Series`

- If you rename the footprints in the OS, to make the libs update, must go to lib manager, remove the lib, click OK (the libs will now refresh). Then go back and add the lib again. Lib will refresh again.
- Prefix Resistor / Inductor / Capacitors / Diodes footprints with `R` / `L` / `C` / `D`
- Prefix Connector footprints with `Conn`.
- Prefix modules/assemblies with `Module_Function_`. E.g. `Module_DC-DC_`.

```
R_SMD__
R_THT__
C_SMD__
C_THT__
CP_SMD__
CP_THT__
D_SMD__
D_THT__ _
```

## PCB CALCULATOR

- Can use Saturn PCB calculator to verify the results (set to metric top right)
- To calculator how to route differential pairs, select the `TransLine` (transmission line) tab.
- For T (the conductor thickness), dont forget to add the affect of solder on the copper. The generally start at 35u, and gets plated to a final thickness of 55u (before the solder mask).
- For differential routing,
- So for 100Ohm, set separation (s) to 0.2 and track width to 0.8mm., and keep at least 3x0.2 = 0.6mm away from other tracks. Must be routed over the gnd plane.
