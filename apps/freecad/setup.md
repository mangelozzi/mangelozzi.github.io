# FreeCAD Setup

## ADDONS

1. `Tools` -> `Addon Manager`
2. Under `Show Addons containing:` select `Workbenches`, install:
    - `Fastenters`  - Add bolts/nuts/washers etc.
    - `SheetMetal`  - For bending sheet metal
    - `Manipulator`  - Various helper tools
    - `Render`  - Photo realistic rendering (required `LuxCodeRenderer`, see below)
2. Under `Show Addons containing:` select `Macros`, install:
    - `TreeToAcsii` (for creating fasteners BOM), click yes to add a tool bar when prompted
3. Download `Standalone release v2.6` NOT the blender plug in at the top from from <https://luxcorerender.org/download/>
    1. Extract the file to say `/home/michael/tools/luxcorerender-v2.6-linux64/LuxCore`
    2. Open `Edit` -> `Preferences` -> `Render` -> `LuxCore` Section
    3. Set `LuxCore UI path` = `/home/michael/tools/luxcorerender-v2.6-linux64/LuxCore/luxcoreui`

## EDIT -> PREFERENCES

- GENERAL
    - General
        - Size of Toolbar Icons = Small (16px)
        - `Main Window` Section
            - `Stylesheet` = whatever you feel like, e.g. `Light-green`
    - Document
        - Using Undo/Redo = Checked
        - Maximum Undo/Redo Steps = 99
        - Allow aborting recomputation = Checked
        - Set Authoring and License Information
    - Selection
        - Preselect the object in the 3D view when mouse over the tree item
    - Units
        - Number of decimals = 2
- DISPLAY
    - 3D View
        - Show the coordinate system in the corner = Checked
        - Show axis cross by default = Checked
        - Remember acitve workbench by tab = Checked
        - Marker size = 15px
        - Pick radius = 20px
    - Navigation Cube
        - Steps by turn = 24 (so can set isometric rotations)
        - Invert Zoom = Checked
    - Colors
        - Background Color
            - Simple color = #bab4ae
- IMPORT-EXPORT
    - DXF
        - Use legacy python exporter = Checked
        - Project exported objects along current view direction
- PART DESIGN
    - Shape appearance
        - Line width = 4px
        - Vertex side = 7px
- TECHDRAW
    - General
        - Default Template = `/home/michael/freecad_support/templates/a4_landscape_nanocube_template.svg`
        - Template Directory = `/home/michael/freecad_support/templates`
    - Scale
        - Size Adjustments
            - Vertex scale = 3
    - Dimensions
        - Standard and Style = ISO Orientated
        - Dimension Format = %.g
    - Annotations
        - Balloon Shape = None

## TOOLS -> CUSTOMISATION

- WORKBENCHES
    - Removed retarded ones
- KEYBOARD
    - Category - Sketcher
        - `Constrain radius or weight` = `SHIFT + r` for `Constrain radius`
        - `SHIFT + d` for `Constrain diameter`
        - `o` for circle
        - `w` for polyline
        - `p` for point
- TOOLBARS
    - Select `Global` on right
    - Select `File` on left
        - Add `&Recompute`
    - Select `Part` on left
        - Add Tape measure `Measure Linear`
        - Add Tape measure `Clear all` (dimenstions, directly above)
