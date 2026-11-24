---
name: 3d-print-prep
description: "Check a finished CAD part for printing: valid solid, walls, fit, orientation, supports and verified export."
---

# Prepare a part for printing

1. Read the user's hardware preferences if they provide them. Use the actual printer, nozzle, material and intended load. Ask only for a missing condition that changes the design. Geometry edits use `freecad-part-design`; preserve the editable source.
2. In FreeCAD, run Check Geometry on the final body; require the intended single-solid count. Resolve invalid solids, open shells, self-intersections and zero-thickness faces. Check walls/ribs, stressed corners, first-layer edges and insert pilot holes against the material/process and insert datasheet.
3. For a mating fit, identify **clearance or interference**, and **per-side/radial or diametral** dimensions. Measure the mate; test a small coupon. A positive gap is not a press fit. Do not apply a universal hole offset.
4. Choose orientation for load paths: layers are weakest along Z. Check bed contact, overhangs, bridges and support damage. Use [starting settings](references/starting-settings.md) only as stated assumptions, not proven process limits.
5. Export a new revision under `print/` or `export/`; never replace `.FCStd`. Check the installed slicer's supported format. STEP support is not universal; STL has no units. Reopen the export and compare size and watertightness with the CAD model.

## Printer-specific starting points (Anycubic Kobra X, direct drive; provisional, verify with a coupon)
- Retraction must stay <=1.5 mm (heat-creep clog); PETG 0.8–1.2 mm @ 35–45, PLA 0.6–0.8, TPU 0.4–0.6 or off. PETG 235–245 °C/bed 75–80, PLA 205–220/55–60, TPU 215–230/40–50 (TPU bypasses the ACE tubes).
- PETG: not on smooth PEI; wait until plate <35 °C before removal; dry 60–65 °C 6 h if it strings/pops.
- FDM CAD offsets at 0.2 mm layers (assumptions, not universal): bearing pocket +0.10 radial; rotating bore +0.30 dia; M3 clearance Ø3.3–3.4; M3 heat-set pilot Ø4.0–4.1, depth >=4.5.
- Slicer: wall order inner/outer/inner, calibrate pressure advance per filament batch, scarf/rear seam for journals. Colour change retraction 1.0 mm (never 0), extra restart +0.10–0.15 mm, prime tower on.

Done: report dimensions, material/profile assumptions, orientation, supports, settings and output path. Without a print test, fit and strength remain unverified. Do not buy material or start a printer unless requested.
