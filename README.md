# GR Film LUT Pack

19 film-emulation `.cube` LUTs with matching slot icons for the Ricoh GR IV. They open in GR Mod Origin and in any other application that reads `.cube` files.

Ricoh and the film manufacturers did not endorse this pack. Each file imitates the look of a film stock; the result is an approximation of that look, not the film itself and not a copy of any camera's built-in simulation.

English | [中文](README.zh-CN.md)

## What's inside

```
lut/            19 .cube files (65³ grid, 8-bit, sRGB in / sRGB out)
icons/          19 PNG icons, 216×204, for GR Mod Origin slots
docs/           per-LUT list, fit evaluation, provenance
licenses/       upstream licence texts and notices
manifest.json   name / brand / slot label / licence / SHA-256 / size
SHA256SUMS.txt  checksums
```

| Film | Brand | Slot label | Licence |
| --- | --- | --- | --- |
| Eterna 500T | Fujifilm | `Fuji Eterna` | MIT |
| Pro 400H | Fujifilm | `Fuji Pro400H` | CC BY-SA 4.0 |
| Superia 400 | Fujifilm | `Fuji Sup400` | CC BY-SA 4.0 |
| Velvia 100 | Fujifilm | `Fuji Vel100` | CC BY-SA 4.0 |
| Aerocolor IV | Kodak | `Koda AeroIV` | MIT |
| Ektachrome E100 | Kodak | `Koda E100` | CC BY-SA 4.0 |
| Ektar 100 | Kodak | `Koda Ekt100` | CC BY-SA 4.0 |
| Gold 200 | Kodak | `Koda Gold200` | CC BY-SA 4.0 |
| Kodachrome 64 | Kodak | `Koda K64` | CC BY-SA 4.0 |
| Portra 400 | Kodak | `Koda P400` | CC BY-SA 4.0 |
| Portra 800 +2 | Kodak | `Koda P800P2` | CC BY-SA 4.0 |
| Vision3 250D | Kodak | `Koda V3 250D` | CC BY-SA 4.0 |
| Vision3 500T | Kodak | `Koda V3 500T` | CC BY-SA 4.0 |
| Amber | creative / unbranded | `Amber` | none stated |
| BW400 | creative / B&W | `BW400` | none stated |
| Fade | creative / unbranded | `Fade` | none stated |
| Classic Chrome | Fujifilm | `Fuji CC` | none stated |
| Classic Negative | Fujifilm | `Fuji CNeg` | none stated |
| Kodak 5218 → 2395 | Kodak | `Koda 5218` | none stated |

Slot labels run 1 to 12 printable ASCII characters, the maximum for added slots in GR Mod Origin. A label fills one field in the camera menu. The `.cube` TITLE, the filenames and the icons stay as they are.

## Using them with GR Mod Origin

1. Open the official GR IV firmware (1.11, 1.20 or 1.21) in GR Mod Origin.
2. Image Control → added slot → import a `.cube` from `lut/`.
3. Type the slot name from the table, pick the matching PNG from `icons/`, and choose the `Plain` icon style rather than Film.
4. Build the firmware, write it to the card, update the camera the usual way.

The camera cannot load a `.cube` directly. GR Mod Origin fits each file to a 3×3 matrix, three tone curves, a post-curve matrix and hue sectors, then builds firmware from the result. Check the preview before you write anything to a card.

The LUTs are ordinary sRGB-to-sRGB 3D LUTs, so they also open in DaVinci Resolve, Affinity Photo and Capture One. Only `icons/` is written for GR Mod.

## How close the fits come out

`docs/Origin适用性复核.md` lists ΔE00 for every LUT.

Greys and skin tones come out closer than saturated colours. Gold, Ektar, Velvia and Superia sit further off; use them for the look.

The figures come from an evaluation of the colour model. No camera output was measured and no firmware was built or checked. This repository holds no firmware and no flashing tools.

## Licences

Licensing differs from file to file.

| Licence | Files |
| --- | --- |
| CC BY-SA 4.0 | 11, all spektrafilm derivatives |
| MIT | 2: Aerocolor IV and Eterna 500T |
| None stated | 6: Amber, BW400, Fade, Classic Chrome, Classic Negative, Kodak 5218→2395 |

The 13 LUTs with clear licences were rebuilt from [GRKit](https://github.com/ahonn/grkit) source recipes (MIT) and adapted to Standard sRGB input. Andrea Volpato wrote the spektrafilm LUTs (CC BY-SA 4.0); Jan Lohse wrote spectral_film_lut (MIT). Full texts and attribution are in `NOTICE.md` and `licenses/`.

Six files came from free public LUT packs the maintainer collected and carry no licence statement. Their upstream URLs are not recorded here. They ship as they are, for personal study and testing; confirm the original source before commercial use or redistribution.

If you pass on a modified version, keep the attribution and the share-alike terms for those 11 CC BY-SA files.

## Verify

```bash
shasum -a 256 -c SHA256SUMS.txt
```
