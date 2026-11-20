# GR Film LUT Pack

19 款胶片模拟 `.cube` 与配套槽位图标，为理光 GR IV 制作。可在 GR Mod Origin 使用，也能在任何支持 `.cube` 的软件里打开。

理光与各胶片厂商都没有参与这个项目。每款文件模仿一种胶片的外观，结果是近似风格，不是胶片本身，也不是任何机内模拟的复刻。

[English](README.md) | 中文

## 目录内容

```
lut/            19 个 .cube（65³ 网格，8 位，sRGB 输入 / sRGB 输出）
icons/          19 张 PNG 图标，216×204，用于 GR Mod Origin 槽位
docs/           逐款清单、拟合评估、来源记录
licenses/       上游许可全文与声明
manifest.json   名称 / 品牌 / 槽位名 / 许可 / SHA-256 / 大小
SHA256SUMS.txt  校验清单
```

| 胶片 | 品牌 | 槽位名 | 许可 |
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
| Amber | 创意 / 无品牌 | `Amber` | 无 |
| BW400 | 创意 / 黑白 | `BW400` | 无 |
| Fade | 创意 / 无品牌 | `Fade` | 无 |
| Classic Chrome | Fujifilm | `Fuji CC` | 无 |
| Classic Negative | Fujifilm | `Fuji CNeg` | 无 |
| Kodak 5218 → 2395 | Kodak | `Koda 5218` | 无 |

槽位名限 1 至 12 个可打印 ASCII 字符，这是 GR Mod Origin 新增槽位的上限。它只填相机菜单里的一个字段，`.cube` 的 TITLE、文件名和图标都不变。

## 在 GR Mod Origin 里使用

1. 在 GR Mod Origin 打开官方 GR IV 固件（1.11、1.20 或 1.21）。
2. 影像控制 → 新增槽位 → 导入 `lut/` 里的 `.cube`。
3. 按上表填入槽位名，选 `icons/` 里对应的 PNG，样式选 `Plain`，不要选 Film。
4. 生成固件，写入存储卡，按官方流程更新相机。

相机不能直接加载 `.cube`。GR Mod Origin 会把每个文件拟合成 3×3 矩阵、三条色调曲线、后置矩阵和色相区，再由结果生成固件。写卡前先看预览。

这些是普通的 sRGB 互转 3D LUT，所以也能在 DaVinci Resolve、Affinity Photo、Capture One 里打开。只有 `icons/` 是给 GR Mod 用的。

## 拟合到底有多接近

`docs/Origin适用性复核.md` 列出了每一款的 ΔE00。

灰阶和肤色比高饱和色更接近。Gold、Ektar、Velvia、Superia 偏差明显更大，适合当风格用。

这些数字来自颜色模型的评估。没有测量相机成片，也没有生成或验证固件。仓库里没有固件，也没有刷写工具。

## 许可

许可按文件区分。

| 许可 | 文件 |
| --- | --- |
| CC BY-SA 4.0 | 11 款，全部为 spektrafilm 衍生 |
| MIT | 2 款：Aerocolor IV、Eterna 500T |
| 无 | 6 款：Amber、BW400、Fade、Classic Chrome、Classic Negative、Kodak 5218→2395 |

13 款许可明确的 LUT 由 [GRKit](https://github.com/ahonn/grkit) 开源源配方重新拟合（MIT），并适配 Standard sRGB 输入。spektrafilm 的 LUT 由 Andrea Volpato 制作（CC BY-SA 4.0），spectral_film_lut 由 Jan Lohse 制作（MIT）。许可全文与署名见 `NOTICE.md` 和 `licenses/`。

另外 6 款来自作者收集的公开免费 LUT 包，没有附许可声明，上游链接也没有记录在仓库里。它们按原样提供，供个人学习与测试；商用或再分发之前，请先确认原始来源。

如果你转发修改版，那 11 款 CC BY-SA 文件要保留署名和相同方式共享的条款。

## 校验

```bash
shasum -a 256 -c SHA256SUMS.txt
```
