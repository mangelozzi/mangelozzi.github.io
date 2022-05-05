# FreeCAD Setup

## ADDONS

1. `Tools` -> `Addon Manager`
2. Under the `Workbench Tab`, select and install:
    - `fastenters`
    - `sheetmetal`
    - `render`

## EDIT -> PREFERENCES

- GENERAL
    - General
        - Size of Toolbar Icons = Small (16px)
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
        - Default Template = C:/work/freecad_support/templates/a4_landscape_nanocube_template.svg
        - Template Directory = C:/work/freecad_support/templates
    - Scale
        - Size Adjustments
            - Vertex scale = 3
    - Dimensions
        - Standard and Style = ISO Orientated
    - Annotations
        - Balloon Shape = None
    - Advanced
        - Dimension Format = %.g

## TOOLS -> CUSTOMISATION

- WORKBENCHES
    - Removed retarded ones
- KEYBOARD
    - Category - Sketcher
        - `SHIFT + r` for `Constrain radius`
        - `SHIFT + d` for `Constrain diameter`
        - `o` for circle
        - `w` for polyline
        - `p` for point
