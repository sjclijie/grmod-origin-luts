# Fit evaluation: using these LUTs in GR Mod Origin

English | [中文](fit-evaluation.zh-CN.md)

> 2026-11-16: the Astia material below is the record from that run and stays as history. `Fuji-Astia.cube` was deleted from the collection the same day, because it pushed mid-grey 0.5 down to about 0.21 and left the green and blue channels of skin near 0, which produced a murky orange image. The scores in this document measure whether the camera can reproduce a given LUT. They do not say the LUT itself was usable.

Dated 2026-10-24. Origin was the only evaluation path, and all 20 files were re-run rather than reusing fork scores. No LUT was modified, no firmware was built, and nothing was written to a card or flashed.

## Conclusion

- The 20-file set is a reasonable library: 10 Kodak, 7 Fujifilm-related, two creative looks (Amber, Fade) and BW400, which gives 19 colour looks and one monochrome, with no exact duplicates.
- It is not accurate to call all 20 high-fidelity. All 20 passed parsing, fitting and the basic quantisation range check, but several strong looks drift clearly from their LUT on saturated colour, pure white and other edges.
- "Prefer GRKit" is a choice about provenance, recipes and style coverage. It is not proof that Origin fits those files more accurately. The numbers below measure closeness to the target LUT; they say nothing about whether a look is attractive, and they are not a camera sample or a firmware safety guarantee.

## 1. One measurement for all 20

Origin's default `convertCube` (post=true) feeding the `previewSlot` float model. Every LUT got the same 12,000 independent random sRGB colours outside the grid, 3,000 model natural colours, a 4,097-step grey ramp, a 24-patch ColorChecker, and the full 33³ grid. Scoring used D65 Lab and CIEDE2000. Quantisation was checked with `quantizeSlot` against the official 1.11 Standard matrix only; no full hardware fixed-point arithmetic, no saturation or hue sweep, no camera boot.

The natural-colour set leans low to mid saturation and comes from GRKit's `holdout()`, not from a third-party photo collection. ColorChecker is tied to the fitting design, so treat it as a diagnostic. Lower numbers mean the model predicts closer to the target the file defines. They do not mean equivalence with native Fujifilm or with real film.

| LUT | Natural mean | Natural p95 | Random RGB mean | Grey mean | Pure-white error | Verdict |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| Amber | 0.81 | 1.82 | 1.48 | 0.96 | 8.11 | Keep as creative; the white end is far off, so not a first choice for fidelity |
| BW400 | 0.53 | 1.76 | 1.22 | 0.33 | 0.00 | Try first; grey and natural colour both fit closely |
| Fade | 0.79 | 2.13 | 1.71 | 0.72 | 1.20 | Try first; natural colour fits well |
| Astia | 1.13 | 2.37 | 2.01 | 1.10 | 0.14 | Usable; the Fuji effect remains a third-party approximation |
| Classic Chrome | 1.24 | 2.70 | 1.24 | 1.67 | 1.59 | Usable; grey average departs more than the other older LUTs |
| Classic Negative | 0.79 | 1.52 | 1.17 | 0.71 | 0.71 | Numerically a good fit; the Provia conversion base and provenance still need separating |
| Kodak 5218 → 2395 | 0.59 | 1.46 | 1.04 | 0.47 | 1.04 | Try first; the cine look fits well, a few source outputs above 1 get clipped |
| Aerocolor IV | 0.95 | 2.37 | 3.13 | 0.73 | 0.15 | Natural colour fits well; a fairly specialised aerial negative recipe |
| Ektachrome E100 | 1.38 | 3.41 | 3.61 | 0.93 | 1.94 | Usable approximation; keeps the slide-film category covered |
| Ektar 100 | 1.74 | 3.33 | 5.03 | 1.53 | 1.29 | Careful with saturated colour; not a full-gamut match |
| Eterna 500T | 1.45 | 3.42 | 3.56 | 1.16 | 3.78 | Usable; the white end differs |
| Gold 200 | 1.71 | 3.57 | 5.56 | 1.58 | 1.30 | Careful with saturated colour; a GRKit source is not automatically the easiest fit for Origin |
| Kodachrome 64 | 1.32 | 2.60 | 3.64 | 1.04 | 1.63 | Usable approximation |
| Portra 400 | 1.50 | 3.05 | 4.11 | 1.34 | 1.55 | Common candidate; expect approximation error |
| Portra 800 +2 | 2.02 | 4.04 | 5.88 | 1.60 | 1.81 | Try later, with care; natural colour and ColorChecker errors are high |
| Pro 400H | 1.31 | 2.65 | 3.89 | 1.15 | 1.89 | Common candidate; natural colour is fairly even |
| Velvia 100 | 1.71 | 4.20 | 4.62 | 1.15 | 1.23 | Keeps a vivid slide look; careful with saturated colour |
| Vision3 250D | 1.38 | 2.95 | 3.66 | 1.19 | 2.29 | Common cine-look candidate |
| Vision3 500T | 1.40 | 3.38 | 3.64 | 1.41 | 3.88 | Usable; the white end differs and it is not the CineStill halation look |
| Superia 400 | 1.70 | 3.61 | 4.90 | 1.41 | 1.74 | Careful with saturated colour |

These are engineering judgements, not the A/B/C/D grades on the GRKit site. "Pure-white error" is ΔE00 against the target LUT for input [1,1,1]; it does not require every look to render pure white.

## 2. Looks worth extra attention

### Amber: good averages, inaccurate white

The target white is about [0.9995, 0.9995, 0.9995]; Origin predicts about [0.8413, 0.8637, 0.8622], roughly 8.11 ΔE00. White backgrounds and very bright areas can show a clear shift in brightness and hue. Keep it as a creative look rather than a fidelity pick. The 0.81 natural-colour average does not offset that boundary problem.

### Portra 800 +2: one of the recipes that needs the most tolerance

Natural mean about 2.02 and p95 about 4.04, ColorChecker mean about 2.60, random RGB mean about 5.88. Keeping it gives the set a pushed variant, but Portra 400 is the safer first try. Do not read "+2" as two stops of ordinary exposure.

### Gold, Ektar, Superia, Velvia: usable look, harder on vivid colour

Natural averages run about 1.70 to 1.74 while random RGB averages run about 4.62 to 5.56. Random RGB p95 for Gold, Ektar and Superia reaches about 15.8 to 19.1, so a few saturated colours can be far off. A natural-colour average under 2 does not mean saturated patches are accurate. None of this says the looks are unattractive.

### Eterna 500T and Vision3 500T: check the white end

White-end errors are about 3.78 and 3.88. Everyday colour in the cine looks holds up, but preview highlights and white backgrounds. Vision3 500T is a 5219 to Supra Endura paper scan recipe, not a CineStill look with added red halation.

## 3. Coverage and overlap

Grouped by use:

- Seven colour-negative recipes: Portra 400, Portra 800 +2, Gold, Ektar, Pro 400H, Superia, Aerocolor.
- Three slide films: Kodachrome, Ektachrome, Velvia.
- Four cine and print related: Vision3 250D, Vision3 500T, Eterna 500T, the older Kodak 5218 to 2395.
- Three Fujifilm in-camera styles: Astia, Classic Chrome, Classic Negative.
- Two general creative looks: Amber, Fade.
- One monochrome: BW400.

Portra 400, Pro 400H, Superia and Gold overlap in function without being duplicates, and the cine group has four entries. Twenty files make sense as a library; nobody needs all twenty switched on. For a first pass compare the representative looks: Classic Negative, Classic Chrome, Portra 400, Pro 400H, Vision3 250D, BW400. That is a list of preview candidates, not a suggestion to build a multi-slot firmware in one go.

## 4. Input and provenance limits

- The 13 GRKit-derived tables take Standard display RGB as input, not V-Log. They were adapted and resampled from the source recipes, so interpolation error is usually smaller than Origin's fit error. Raising the table from 65³ does not fix a transform the Origin model cannot express.
- Seven of the original source cubes have hashes that differ from the upstream records because they were rebuilt from pinned source recipes. Without the original reference bytes there is no proof the numbers match. That is a separate question from whether Origin can fit the delivered files.
- The GRKit adaptation uses GR IV base curves but keeps the GR III Standard matrix, grey point and CSY inverse assumptions. Treat it as a model, not as a full GR IV calibration.
- The older Fuji material such as Astia and Classic Negative came from third-party profiles and conversion chains. Upstream distinguishes a linear camera-profile path from a "Provia conversion" path, and the current GR Standard is not a Fujifilm Provia base. Older notes describe Classic Negative as the Provia conversion version, but the available cache is not enough to confirm the origin byte for byte. Use them as creative LUTs; do not promise a strict copy of Fujifilm's in-camera simulation.
- The upstream note "linear contrast / linear camera profile" does not by itself prove the transfer function must be linear-light sRGB. The existing Astia adaptation is left as it was; a strict calibration of the colour-space chain needs more source and camera evidence.
- The older Kodak 5218 source table contains a few outputs above 1. Origin clips them to 0..1 as its implementation does, and the scores here were measured against that clipped import target.
- Public redistribution rights for the pre-existing material need a separate check. This local fit evaluation does not grant permission to republish all 20 files.

## 5. Recommendation

Keep all 20 and do not prune further for now, while separating "I collected twenty looks" from "every one is exact". BW400, Kodak 5218 to 2395 and Fade fit well. Start previews with Portra 400, Pro 400H or Vision3 250D, and move Portra 800 +2, Amber's white end and the vivid looks later, once you accept the approximation.

This run validated the desktop colour import path only. Multi-slot combinations, menu patches, storage, boot behaviour and real camera output were not tested. A 20-out-of-20 pass on the parameter range does not mean writing twenty looks at once is safe.

## Evidence and reproduction

- Origin revision: `12c58a5d26f4fe045ada8bc926726c2c83012b4e`
- [Unified evaluation results](origin-evaluation.json), including the SHA-256 of each LUT and every error statistic.
- The reproduction script `review.py` and the raw point-by-point predictions stayed in the working copy (`analysis/origin-20-review-20261024/`) and are not included here.
- Fujifilm source documentation: [abpy/FujifilmCameraProfiles](https://github.com/abpy/FujifilmCameraProfiles).
