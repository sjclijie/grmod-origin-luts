# GR Origin LUT Pack

面向理光 GR IV（GR Mod Origin）的胶片模拟 LUT 包：**13 款 `.cube`** + 配套的 **Origin 槽位图标**，以及每款的适用性评估和使用说明。

所有 LUT 都由开放的 [GRKit](https://github.com/ahonn/grkit) 源配方**重新拟合**而来，适配到 **GR IV Standard 显示 RGB 输入 → sRGB 输出**，可直接导入 GR Mod Origin 的「影像控制」新增槽位。

> **这不是理光官方产品。** 名称中的胶片与品牌仅用于说明模拟对象，不代表品牌背书，也不等于真实胶片的实测等效。

## 包含什么

| 胶片 | 品牌 | 推荐槽名 | 许可 |
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

推荐槽名均为 **1–12 个可打印 ASCII 字符**，满足 GR Mod Origin 对新增槽位名称的限制。它们只用于填入相机菜单，**不改变 `.cube` 的 TITLE、文件名或图标**。

## 目录结构

```
lut/            13 个 .cube（65³ 网格）
icons/          13 张 216×204 PNG，Origin 槽位图标（选图片 + Plain 纯色，不要用 Film）
docs/           逐款清单、Origin 适用性复核、来源与许可
licenses/       上游许可全文与 NOTICE
manifest.json   名称 / 品牌 / 槽名 / 许可 / SHA-256 / 文件大小
SHA256SUMS.txt  校验清单
```

## 使用

1. 在 GR Mod Origin 打开官方 GR IV 固件（1.11 / 1.20 / 1.21）。
2. 影像控制 → 新增槽位 → 导入 `lut/` 里的 `.cube`。
3. 槽位名称按上表填写；图标选 `icons/` 对应 PNG，样式选 **Plain（纯色）**。
4. 生成固件、写卡、按官方流程更新相机。

**这些 `.cube` 不是相机的原生 LUT**，Origin 会再把它拟合为矩阵＋曲线＋色相区。写入前请先在 Origin 里看预览。

## 评估结果与局限

`docs/Origin适用性复核.md` 给出逐款的拟合误差（ΔE00）。要点：

- 灰阶与肤色普遍好于高饱和色；**Gold、Ektar、Velvia、Superia 这类鲜艳风格偏差较大**，请接受近似。
- 评估是**颜色模型层面**的逐点预测，不是真机成片对比，也没有做硬件回放或固件安全验证。
- 没有固件、没有刷写脚本。本仓库只提供 LUT 与图标。

## 许可

**文件级许可，不统一。**

- 11 款：**CC BY-SA 4.0**（源自 [spektrafilm](https://github.com/andreavolpato/spektrafilm) 0.3.4，作者 Andrea Volpato）
- 2 款：**MIT**（源自 [spectral_film_lut](https://github.com/JanLohse/spectral_film_lut)，作者 Jan Lohse）
- 拟合方法来自 [GRKit](https://github.com/ahonn/grkit)（MIT）；本仓库的 LUT 是从其源配方**重建**，不是复制其已发布的拟合参数。

逐款对应见 `manifest.json`，完整声明见 `NOTICE.md` 与 `licenses/`。

**分享修改版时请遵守 CC BY-SA 4.0 的相同方式共享要求并保留署名。**

## 未收录的部分

原始素材库还有 6 款更早收集的 LUT（Amber、BW400、Fade、Classic Chrome、Classic Negative、Kodak 5218→2395）。它们的**来源与再分发许可未能确认**，因此**不包含在本仓库中**。

如果你持有这些文件的明确许可，可以自行加入 `lut/` 并在 `manifest.json` 补一条记录。

## 校验

```bash
shasum -a 256 -c SHA256SUMS.txt
```

## English

A pack of 13 film-emulation `.cube` LUTs for Ricoh GR IV, rebuilt from the open GRKit recipes and adapted to Standard sRGB in / sRGB out, plus 216×204 slot icons for GR Mod Origin. Licences are per file: 11 are CC BY-SA 4.0 (spektrafilm), 2 are MIT (spectral_film_lut). Six older LUTs from the author's collection are excluded because their redistribution rights could not be established. Not affiliated with Ricoh. Film and brand names describe the emulated stock only.
