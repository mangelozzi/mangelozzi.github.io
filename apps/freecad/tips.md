# FreeCAD

## PART DESIGN VS PART WORKBENCH

- If you make a part in ANY workbench outside of `part design`, and then try to edit it in `part design`, it will create a duplicate. If you can make a change in part design, do it in part design, because then you can still updated your model.
- If you make something in the `part workbench`, will probably be editable in any other workbench.

## PART DESIGN

### Hotkeys

- `SHIFT + r` for for radius dimension
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

## TECHDRAW

- To change the template, in the model tree select the `page`, then the `template` sub item, in the `Property/View`.

## TOPOLOGICAL NAMING ERRORS

- Select the sketch in the model tree, check the `Property/Value` window and click the ellipses next to `Map Mode` then select the face you want it on. You will have to correct any edge references.
- [YouTube: Why do my FreeCAD models break? - "Topological Naming Problem"](https://www.youtube.com/watch?v=6p2vqEEmWq4)
