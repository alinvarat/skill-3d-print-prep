---
name: 3d-print-prep
description: "Check a finished CAD part for printing: valid solid, walls, fit, orientation, supports and verified export."
---

# Prepare a part for printing

1. Read the user's hardware preferences if they provide them. Use the actual printer, nozzle, material and intended load. Ask only for a missing condition that changes the design. Geometry edits use `freecad-part-design`; preserve the editable source.
2. In FreeCAD, run Check Geometry on the final body; require the intended single-solid count. Resolve invalid solids, open shells, self-intersections and zero-thickness faces. Check walls/ribs, stressed corners, first-layer edges and insert pilot holes against the material/process and insert datasheet.
3. For a mating fit, identify **clearance or interference**, and **per-side/radial or diametral** dimensions. Measure the mate; test a small coupon. A positive gap is not a press fit. Do not apply a universal hole offset.
4. Choose orientation for load paths: layers are weakest along Z. Check bed contact, overhangs, bridges and support damage. Use [starting settings](references/starting-settings.md) (general values plus Kobra X retraction, temperature, PETG, fit-offset and slicer notes) only as stated assumptions, not proven process limits. Hard limit on the Kobra X: retraction stays <=1.5 mm (heat-creep clog).
5. Export a new revision under `print/` or `export/`; never replace `.FCStd`. Check the installed slicer's supported format. STEP support is not universal; STL has no units. Reopen the export and compare size and watertightness with the CAD model.

Done: report dimensions, material/profile assumptions, orientation, supports, settings and output path. Without a print test, fit and strength remain unverified. Do not buy material or start a printer unless requested.
