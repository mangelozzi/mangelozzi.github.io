# FreeCAD Tips

## PART DESIGN VS PART WORKBENCH

- If you make a part in ANY workbench outside of `part design`, and then try to edit it in `part design`, it will create a duplicate. If you can make a change in part design, do it in part design, because then you can still updated your model.
- If you make something in the `part workbench`, will probably be editable in any other workbench.

## PART DESIGN

- To colour it, right click on the `body` in the tree browser, and select `Appearance...`, don't choose a material (leave it on `default`), the shiny'ness makes it hard to see. This sets all faces, choose the most common color for the faces. Then right click on the tree tip node, and select `Set colors...` (2nd from top). Note there is a box select feature, handy for say a header.
    - WARNING: The colors only applies to one step, once you add any other steps, the coloring does not pull forward.

## LAND MINES

- Dont do boolean operations which result in zero thickness, may seem okay, but once you try fillet etc the models just dissappears.
-

## SKETCHER

- The order of symmetric constraint matters. hover over the cursor to see it explained
    - If using it on 3 points, first select the point to be symmetric, then lastly select the point to be point of symmetry.

## SPREADSHEET

- Don't have to burrow into menus to see `alias`, it is available top right.
- Can select multiple cells, right click, `properties`, `display units` tab, and can set to `mm`
- To reference a value in a dimensions, type `=` or click lil white/blue icon. Enter `spreadsheet_name.alias`, e.g. `ss.box_w`
- If try to place circles or shapes close to the bend line, if it fails, ensure there is a straight portion perpindicular to the bend line, e.g.:
    - bend line-> `| |)` is no good
    - bend line-> `| [)` is OK, has straight lines before the arc
    - bend line-> `| o` is OK

## TECHDRAW

- To show hidden lines set `Hard Hidden` to `True`, which means show hard edges.
- To change the template, in the model tree select the `page`, then the `template` sub item, in the `Property/View`.
- To add a 3D dimension:
    1. First add the dimension, it will show the projected (incorrect value).
    2. Goto the 3D view, and select an edge.
    3. Then `CTRL` click the page you would like to apply it to (don't have to if only one page).
    4. Then click `Link Dimension`
    5. Select the dimension from the list in the dialogue.
- If you get the error `can not determine correct page`, select the item in the tree view, then `CTRL` click the page,
then click TechDraw `Insert a view`. Or tab to the page.

## TOPOLOGICAL NAMING ERRORS

- Select the sketch in the model tree, check the `Property/Value` window and click the ellipses next to `Map Mode` then select the face you want it on. You will have to correct any edge references.
- [YouTube: Why do my FreeCAD models break? - "Topological Naming Problem"](https://www.youtube.com/watch?v=6p2vqEEmWq4)

# EXPORT

- Ensure the drawings is parallel with the view port.
    - Can use the Manipulator -> `Mover Tools` -> `Align view to the selected view` (looks like a speedgun pointing at a cube)
- `Preferences` -> `Import/Export` ->  `DXF` tab
    - Check `project exported objects along current view`
    - If export fails try `use legacy python exporter`

## RENDER

- Ensure `View` -> `Perspective view` is on before rendering, or else will use last view
- LuxCoreRender, the CLI .exe is called `luxcoreui.exe`
- Set `Ground Plane` to True and set a color.
- Refer to: <https://github.com/FreeCAD/FreeCAD-render>


## SHEET METAL WORKBENCH

![Sheet metal terms](./sheetmetal_terms.png)
