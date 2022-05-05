# KICAD

KiCAD support libs, scripts, borders etc

# INSTALL

- **DON'T** just `sudo apt install kicad`, you wont have the 3D models.
- Follow <https://www.kicad.org/download/ubuntu/>:
    ```bash
    sudo add-apt-repository --yes ppa:kicad/kicad-6.0-releases
    sudo apt update
    sudo apt install --install-recommends kicad
    ```

# SETUP

## SET NANOCUBE ENV VARIABLE/LIBS

At the project screen, go to `Preferences`, then:

- `Configure Paths`, then add an environment variable:
    - `Name` = `NANOCUBE`,
    - `Path` = Location where this repo was checkout out to
        - e.g. `/home/michael/kicad_support`.
        - e.g. `C:\work\kicad_support\`.
- `Configure Paths`, then add an environment variable:
    - `Name` = `MODEL`,
    - `Path` = `/usr/share/kicad/3dmodels` or `C:\Program Files\KiCad\5.99\share\kicad\3dmodels`
    - Note, then one can refer to the 3d file simply as `LED_SMD.3dshapes/LED_0603_1608Metric.step` for a built in KiCAD file
- `Manage Symbol Libraries...`, go to the `Global Libraries` tab, add a new entry:
    - `Nickname` = `0_NanoCube` (so it appears at the top. Do not use a different name, or existing references to this name will break)
    - `Library Path` = `${NANOCUBE}/symbols/nanocube.kicad_sym`
- `Manage Footprint Libraries...`
- `Manage Symbol Libraries...`, go to the `Global Libraries` tab, add a new entry:
    - `Nickname` = `0_NanoCube` (so it appears at the top. Do not use a different name, or existing references to this name will break)
    - `Library Path` = `${NANOCUBE}/nanocube.pretty`


## PREFERENCES

- At the project screen, go to `Preferences`, then `Preferences...`, then in the tree select:
    - `SCHEMATIC EDITOR`
        - `Editing Options`
            - Uncheck `Automatically place symbol fields`
        - `Field Name Templates`
            1. `Value2` - Another part of the value, e.g. Cap voltage, L current, R power rating etc.
            2. `Part Number`
            3. `Manufacturer`
            4. `Description`
            5. `Supplier`
            5. `Stock Code` - The suppliers part number
            6. `URL` - Tick `URL`
            7. `Alternates`
            9. `Config` - FIT, DNF
            10. `Note` - Random notes

# Basic 3D Model geometric shapes:

e.g.:

- `${NANOCUBE}/3d_models/cube.step` for a generic 1x1x1mm cube.
- `${NANOCUBE}/3d_models/can.step` for a generic 1x1mm cylinder.

# BOM

1. Click `+`.
2. Navigate to `C:\Program Files\KiCad\5.99\bin\scripting\plugins`
3. Add `bom2grouped_csv.xls` Note the **.xls** extensions!

## SCHEMATIC

### Border

- Set to `${NANOCUBE}\borders\a4_landscape.kicad_wks`
