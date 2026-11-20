# GR Film LUT Pack

19 film-emulation `.cube` LUTs with matching slot icons, made for the Ricoh GR IV. They load in GR Mod Origin, and in any other application that reads `.cube` files.

Film and brand names describe the stock each LUT imitates. Nobody at Ricoh or at the film manufacturers has endorsed this pack, and these files are approximations: they are not the film, and they are not a copy of any camera's built-in simulations.

English | [中文](#中文)

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

Slot labels run 1 to 12 printable ASCII characters, the limit for added slots in GR Mod Origin. A label only fills a field in the camera menu; the `.cube` TITLE, the filenames and the icons stay as they are.

## Using them with GR Mod Origin

1. Open the official GR IV firmware (1.11, 1.20 or 1.21) in GR Mod Origin.
2. Image Control → added slot → import a `.cube` from `lut/`.
3. Type the slot name from the table, pick the matching PNG from `icons/`, and choose the **Plain** icon style rather than Film.
4. Build the firmware, write it to the card, update the camera the usual way.

The camera cannot load a `.cube` directly. GR Mod Origin fits each file to a 3×3 matrix, three tone curves, a post-curve matrix and hue sectors, and only then builds firmware from the result. Look at the preview before writing anything to a card.

Apart from `icons/`, nothing here belongs to GR Mod. The LUTs are ordinary sRGB-to-sRGB 3D LUTs and load in DaVinci Resolve, Affinity Photo, Capture One and similar tools.

## How close the fits come out

`docs/Origin适用性复核.md` lists ΔE00 for every LUT. Two things matter when reading it.

Greys and skin tones fit closer than saturated colours do. Gold, Ektar, Velvia and Superia land some way off: treat them as a look, not a measured match.

The numbers come from an evaluation of the colour model. No camera output was measured, and no firmware was built or checked. This repository holds no firmware and no flashing tools.

## Licences

Licensing differs from file to file.

| Licence | Files |
| --- | --- |
| CC BY-SA 4.0 | 11, all spektrafilm derivatives |
| MIT | 2: Aerocolor IV and Eterna 500T |
| Unverified public | 6: Amber, BW400, Fade, Classic Chrome, Classic Negative, Kodak 5218→2395 |

The 13 LUTs with clear licences were rebuilt from [GRKit](https://github.com/ahonn/grkit) source recipes (MIT) and adapted to Standard sRGB input. The spektrafilm LUTs are by Andrea Volpato (CC BY-SA 4.0) and spectral_film_lut is by Jan Lohse (MIT). Full texts and attribution sit in `NOTICE.md` and `licenses/`.

Six files come from free public LUT packs supplied by the maintainer. Their upstream URLs and redistribution terms are not recorded here. They are included as they are, for personal study and testing; check the original source before any commercial use or redistribution.

If you pass on a modified version, keep the attribution and the share-alike terms that apply to those 11 CC BY-SA files.

## Verify

```bash
shasum -a 256 -c SHA256SUMS.txt
```

---

## 中文

19 款胶片模拟 `.cube` 与配套槽位图标，为理光 GR IV 制作。可以在 GR Mod Origin 里使用，也能在任何支持 `.cube` 的软件中打开。

胶片与品牌名只说明模拟对象。理光与各胶片厂商都没有参与这个项目；这些文件是风格近似，既不是胶片本身，也不是任何机内模拟的复刻。

- 13 款由 [GRKit](https://github.com/ahonn/grkit) 开源源配方重新拟合，适配 Standard sRGB 输入；另外 6 款来自公开免费 LUT 包。
- 许可按文件区分：11 款 CC BY-SA 4.0、2 款 MIT、6 款来源未核实，详见 `NOTICE.md`。
- 槽位名限 1 至 12 个可打印 ASCII 字符，这是 GR Mod Origin 新增槽位的限制；它只填相机菜单里的一个字段，不改文件名和图标。
- 评估结果是颜色模型的逐点预测，没有测量相机成片，也没有生成或验证固件；Gold、Ektar、Velvia、Superia 这几款高饱和风格偏差比较大。
- 仓库里没有固件，也没有刷写工具。
