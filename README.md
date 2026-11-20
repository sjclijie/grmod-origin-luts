# GR Film LUT Pack

19 film-emulation `.cube` LUTs with matching slot icons, made for Ricoh GR IV — usable in **GR Mod Origin** (and any other app that loads `.cube` files).

English | [中文](#中文)

> **Not a Ricoh product.** Film and brand names describe the emulated stock only. No endorsement, no claim of equivalence to real film or to in-camera film simulations.

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
| Amber | creative / unbranded | `Amber` | unverified public |
| BW400 | creative / B&W | `BW400` | unverified public |
| Fade | creative / unbranded | `Fade` | unverified public |
| Classic Chrome | Fujifilm | `Fuji CC` | unverified public |
| Classic Negative | Fujifilm | `Fuji CNeg` | unverified public |
| Kodak 5218 → 2395 | Kodak | `Koda 5218` | unverified public |

Slot labels are **1–12 printable ASCII characters**, the limit for added slots in GR Mod Origin. They only fill a camera menu field — they do not change the `.cube` TITLE, filename or icon.

## Using them with GR Mod Origin

1. Open the official GR IV firmware (1.11 / 1.20 / 1.21) in GR Mod Origin.
2. Image Control → added slot → import a `.cube` from `lut/`.
3. Set the slot name from the table above; pick the matching PNG from `icons/` and choose the **Plain** icon style (not Film).
4. Build the firmware, write it to the card, update the camera the usual way.

These are **not native camera LUTs**. GR Mod Origin fits each one to a 3×3 matrix, three tone curves, a post-curve matrix and hue sectors. Check the preview before writing anything to the camera.

The `.cube` files are ordinary sRGB→sRGB 3D LUTs, so they also load in any other application that accepts `.cube` (DaVinci Resolve, Affinity Photo, Capture One, etc.). Only the `icons/` are specific to GR Mod.

## Fit quality, honestly

`docs/Origin适用性复核.md` has per-LUT ΔE00 figures. In short:

- Greys and skin tones fit better than highly saturated colours. **Gold, Ektar, Velvia and Superia are noticeably approximate** — expect a look, not a measurement-grade match.
- The numbers come from a colour-model evaluation, **not** from real camera output. No hardware playback, no firmware validation was done.
- This repository contains no firmware and no flashing tools.

## Licence

**Per file, not uniform.**

| Licence | Files |
| --- | --- |
| CC BY-SA 4.0 | 11 — spektrafilm derivatives |
| MIT | 2 — Aerocolor IV, Eterna 500T |
| Unverified public | 6 — Amber, BW400, Fade, Classic Chrome, Classic Negative, Kodak 5218→2395 |

The 13 clean-licence LUTs were rebuilt from [GRKit](https://github.com/ahonn/grkit) source recipes (MIT) and adapted to Standard sRGB input. Spektrafilm LUTs are by **Andrea Volpato** (CC BY-SA 4.0); spectral_film_lut is by **Jan Lohse** (MIT). Full texts and attribution: `NOTICE.md` and `licenses/`.

The six "unverified public" files come from free public LUT packs supplied by the maintainer; their upstream URLs and redistribution terms are **not documented here**. They are provided as-is for personal study and testing. Verify the original source before commercial use or redistribution.

**If you share a modified version, keep the attribution and the CC BY-SA 4.0 share-alike terms for those 11 files.**

## Verify

```bash
shasum -a 256 -c SHA256SUMS.txt
```

---

## 中文

19 款胶片模拟 `.cube` LUT 与配套槽位图标，面向理光 GR IV，可直接用于 **GR Mod Origin**，也可在任何支持 `.cube` 的软件里使用。

- **13 款**由 [GRKit](https://github.com/ahonn/grkit) 开源源配方重新拟合，适配 Standard sRGB 输入；**6 款**来自公开免费 LUT 包。
- 许可按文件区分：11 款 CC BY-SA 4.0、2 款 MIT、6 款来源未核实。详见 `NOTICE.md`。
- 槽位名限 1–12 个可打印 ASCII 字符（GR Mod Origin 新增槽位的限制），只影响相机菜单显示。
- 评估是颜色模型层面的逐点预测，**不是真机成片对比**；Gold、Ektar、Velvia、Superia 等高饱和风格偏差较大。
- 本仓库不含固件、不含刷写工具。

**这不是理光产品**，品牌与胶片名仅用于说明模拟对象。
