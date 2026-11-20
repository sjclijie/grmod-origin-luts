# LUT list (final 19)

English | [中文](lut-list.zh-CN.md)

18 colour looks plus BW400 as the only black-and-white one; 13 from GRKit recipes and 6 older files. LUT contents and filenames are unchanged.

## Confirmed menu labels

Kodak uses `Koda` and Fujifilm uses `Fuji`. The 19 labels below are unique, run 1 to 12 printable ASCII characters, and have no leading or trailing spaces. `P2` means pushed two stops. Amber, Fade and BW400 carry no invented brand.

These are suggestions for the name field in Origin, not a software project file. The full film name and recipe stay in this list and in the provenance record. The LUT and PNG filenames do not change with the menu label.

| Name | Brand / type | Source | Slot label | Characters | File |
| --- | --- | --- | --- | ---: | --- |
| Amber | Creative / unbranded | Older | `Amber` | 5 | [Amber.cube](../lut/Amber.cube) |
| BW400 | Creative / unbranded | Older | `BW400` | 5 | [BW400.cube](../lut/BW400.cube) |
| Fade | Creative / unbranded | Older | `Fade` | 4 | [Fade.cube](../lut/Fade.cube) |
| Classic Chrome | Fujifilm | Older | `Fuji CC` | 7 | [Fuji-ClassicChrome.cube](../lut/Fuji-ClassicChrome.cube) |
| Classic Negative | Fujifilm | Older | `Fuji CNeg` | 9 | [Fuji-ClassicNeg.cube](../lut/Fuji-ClassicNeg.cube) |
| Eterna 500T | Fujifilm | GRKit recipe | `Fuji Eterna` | 11 | [eterna-500t-3523xd-v1.cube](../lut/eterna-500t-3523xd-v1.cube) |
| Pro 400H | Fujifilm | GRKit recipe | `Fuji Pro400H` | 12 | [pro-400h-crystal-v1.cube](../lut/pro-400h-crystal-v1.cube) |
| Superia 400 | Fujifilm | GRKit recipe | `Fuji Sup400` | 11 | [xtra-400-crystal-v1.cube](../lut/xtra-400-crystal-v1.cube) |
| Velvia 100 | Fujifilm | GRKit recipe | `Fuji Vel100` | 11 | [velvia-100-v1.cube](../lut/velvia-100-v1.cube) |
| Aerocolor IV | Kodak | GRKit recipe | `Koda AeroIV` | 11 | [aerocolor-iv-v1.cube](../lut/aerocolor-iv-v1.cube) |
| Ektachrome E100 | Kodak | GRKit recipe | `Koda E100` | 9 | [ektachrome-e100-v1.cube](../lut/ektachrome-e100-v1.cube) |
| Ektar 100 | Kodak | GRKit recipe | `Koda Ekt100` | 11 | [ektar-100-edge-v1.cube](../lut/ektar-100-edge-v1.cube) |
| Gold 200 | Kodak | GRKit recipe | `Koda Gold200` | 12 | [gold-200-premier-v1.cube](../lut/gold-200-premier-v1.cube) |
| Kodachrome 64 | Kodak | GRKit recipe | `Koda K64` | 8 | [kodachrome-64-v1.cube](../lut/kodachrome-64-v1.cube) |
| Kodak 5218 → 2395 | Kodak | Older | `Koda 5218` | 9 | [Kodak-5218-2395.cube](../lut/Kodak-5218-2395.cube) |
| Portra 400 | Kodak | GRKit recipe | `Koda P400` | 9 | [portra-400-endura-v1.cube](../lut/portra-400-endura-v1.cube) |
| Portra 800 +2 | Kodak | GRKit recipe | `Koda P800P2` | 11 | [portra-800-push2-v1.cube](../lut/portra-800-push2-v1.cube) |
| Vision3 250D | Kodak | GRKit recipe | `Koda V3 250D` | 12 | [vision3-250d-2383-v1.cube](../lut/vision3-250d-2383-v1.cube) |
| Vision3 500T | Kodak | GRKit recipe | `Koda V3 500T` | 12 | [vision3-500t-supra-v1.cube](../lut/vision3-500t-supra-v1.cube) |

> 2026-11-16: `Fuji-Astia.cube` was removed. Its data was broken — mid-grey 0.5 landed near 0.21 and the green and blue channels of skin tones sat near 0, so the output was unusable. The removal applies to that file only, not to the rest of the collection.
