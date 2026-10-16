# DAFU-DEMO-V0.2.1 manufacturing files

Regenerated on 2026-10-12 from the user's latest saved project with KiCad 10.0.5.
PCB SHA-256: `16c16d32f7731cb15bf84564cf54f34b62e3aa2eb81f13218ef568a6f13b8d69`.

## Fabrication

- `gerbers/` contains eight manufacturing layers, Gerber job, metric Excellon
  drill and drill report. There is no B.Paste because the bottom has no paste pads.
- Two copper layers, nominal board thickness 1.6 mm, 30.0 x 31.6 mm outline,
  four 1 mm corner chamfers, 946.0 mm2 outline area.
- 74 plated through-vias, each with a 0.30 mm drill. All drill coordinates were
  checked against the saved PCB.
- Manufacturing layers and drill are exported from an exact source snapshot.
  Saved copper and 279 native teardrops are used without refilling, regenerating
  teardrops or saving changes to the project.
- The saved bottom GND is one solid zone, with direct pad connections and one
  filled polygon. Gerbers use normal manufacturing coordinates; do not mirror them.

## Assembly

- `assembly/DAFU-BOM.csv` groups references by value, footprint, manufacturer,
  MPN and assembly status. Manufacturer/MPN are inherited from the project;
  unspecified part numbers are left blank.
- U6 is Texas Instruments TLC2274AIDR; U9 is UMW OPA333AIDBVR.
- C11 is DNP in the schematic and is not populated. The saved PCB lacks its DNP
  flag; assembly exports use a temporary copy with that flag set. No copper,
  mask or paste aperture is removed for C11.
- `DAFU-front-pos.csv` contains the 42 fitted front components. `DAFU-back-pos.csv`
  has no fitted components. C11 and bare PCB pads TP1, TP2, TP5 and TP6 are excluded.
- `DAFU-reference-positions.csv` is a full 47-reference inspection list, including
  DNP and bare pads. It uses the source PCB's positive Y coordinates and is not
  a pick-and-place file.
- The front/back placement CSV coordinates are millimeters from the KiCad absolute
  origin: X is unchanged, Y is negated, and rotation follows KiCad. Top/bottom side
  is recorded.
- Assembly SVG/PDF show body/courtyard outlines and readable reference
  labels. C11 is crossed out. Bottom drawings show the physical back view.

## Checks and saved warnings

- Schematic ERC: 0 violations. PCB: 0 active DRC violations and 0 unconnected items.
- Five existing schematic-parity warnings remain: C11 DNP mismatch and absent
  U2 pads 10 (PA0), 17 (PA7), 18 (PB0), 19 (PB1). The schematic marks those U2
  pins No Connect. The physical MCU still has 48 leads; those four leads have no
  copper pads, soldermask openings or paste apertures in the saved design.
- The existing excluded U2 footprint-library mismatch remains. No new exclusion
  rule is added. This release has documented warnings and is not a zero-warning DRC.
- See `documentation/final-drc.json`, `final-erc.json`, `current-board-summary.json`
  and `release-verification.json` for current checks.

## Previews and integrity

- `previews/` contains newly generated front/back copper and silkscreen SVG/PNG,
  plus front/back 3D PNG. Bottom previews are mirrored for viewing only.
- 3D previews use the assembly copy to omit C11, matching the schematic DNP flag.
- `manifest.json` records exact source hashes and the size/SHA-256 of every
  delivered file except itself. Project source hashes are checked after export.
- `../dafu.zip` contains this complete directory under `dafu/`. Its adjacent
  `.sha256` file verifies the archive. The repository packaging was updated on
  2026-10-16; fabrication and assembly files remain from the 2026-10-12 export.
- `../dafu-gerbers.zip` is a separate fabrication-only archive containing the files
  in `gerbers/` without assembly or preview files.
- Source paths in `manifest.json` are relative to the repository root, two levels
  above this directory. Temporary workstation paths in check metadata are omitted.
- The manufacturing export does not establish measured impact-response or ADC
  performance; it preserves the saved circuit and layout.
