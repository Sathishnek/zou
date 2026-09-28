# Synthetic Generation Options and Technical Pipeline for Green Screen / Matting Training Data

Research date: 2026-09-28. Note: arxiv.org, openaccess.thecvf.com and runway.com were blocked by the network proxy during this research, so several paper/terms claims rely on search-result snippets of those pages rather than full-text reads. These are flagged where relevant.

## Synthetic data options (engines, compositing pipelines, AI video generators, synthetic-human datasets) and their licenses

### Takeaway
The dominant, proven approach in matting research is not full 3D rendering but *compositing*: real foregrounds with ground-truth alpha (from green screen captures) composited onto large background pools (BG-20k, DVM backgrounds, COCO-style crawled images) with heavy temporal augmentation. 3D engines give pixel-perfect masks but licenses often restrict AI training use (MetaHuman explicitly forbids it; BEDLAM and Microsoft FaceSynthetics are non-commercial/research by default). Commercial AI video generators are legally risky as training sources because OpenAI and Google terms prohibit using outputs to develop competing models, and Runway retains training rights over your outputs.

### Cited Findings
**Compositing pipelines (RVM / BGMv2 style)**
- RVM trains on VideoMatte240K (JPEG SD 6GB for stages 1-2; HD 60GB for stages 3-4) plus "ImageMatte" (Distinctions-646 + Adobe Image Matting, humans only, stage 4); backgrounds from DVM Background Set (14.6GB train) and 8,000 crawled image backgrounds; segmentation co-training on COCO 2017, YouTubeVIS 2021 and Supervisely Person — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)
- RVM uses a four-stage schedule: stage 1 512p/15 frames, stage 2 512p/50 frames, stage 3 512p+2048p hybrid (40/6 frames), stage 4 ImageMatte at same hybrid; trained on 4x V100, 48 CPU cores, 300GB RAM — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)
- VideoMatte240K provides 484 4K/HD green-screen-derived clips; RVM selected 3,118 human-free HD background video clips (first 100 frames each) with motions such as passing cars, shaking leaves, camera motion — [RVM paper (arXiv 2108.11515), via search snippet](https://arxiv.org/pdf/2108.11515)
- RVM applies motion/temporal augmentations to both FG and BG: affine translation, scale, rotation, shear, brightness, saturation, contrast, hue, noise, blur, changing continuously over time — [RVM paper, via snippet](https://arxiv.org/pdf/2108.11515)
- Other video matting works use 20,000 BG-20k image backgrounds, sometimes with DVM backgrounds and ~6,000 crawled images split 8:1:1 train/val/test — [Video Instance Matting (WACV 2024)](https://openaccess.thecvf.com/content/WACV2024/papers/Li_Video_Instance_Matting_WACV_2024_paper.pdf); [VMFormer](https://arxiv.org/pdf/2208.12801)
- BGMv2 (Real-Time High-Resolution Background Matting) is the reference for background-plate-conditioned matting (captured clean background as a second input) — [BGMv2 arXiv 2012.07810](https://ar5iv.labs.arxiv.org/html/2012.07810)

**New 2026 work relevant to green screen / LED volume data**
- CineMatte (CVPR 2026 Findings): background matting for LED virtual production; uses a Siamese frozen DINOv3 ViT encoding the frame and captured background separately, with cross-attention comparing them — [CineMatte CVPR 2026 repository page](https://openaccess.thecvf.com/content/CVPR2026F/html/He_CineMatte_Background_Matting_for_Virtual_Production_and_Beyond_CVPRF_2026_paper.html) (full text blocked; via search snippet)
- CineMatte-4K dataset: 4K HDR images/videos captured on a professional LED VP stage; image subset (500 samples, 100 test) is "non-synthetic, obtained via green-screen insertion"; video subset is 30 clips of ~10 s at 30 fps with tracked camera trajectories so backgrounds can be re-rendered with correct parallax — [arXiv 2605.18328 via search snippet](https://arxiv.org/abs/2605.18328); [awesomepapers CineMatte-4K](https://awesomepapers.io/generative-models/datasets/cinematte-4k)
- MatAnyone 2 (CVPR 2026 Highlight) built VMReal: 28,000 real-world clips / 2.4M frames, labelled automatically using a learned Matting Quality Evaluator (DINOv3+DPT, pixel-wise error map without GT) used both online during training and offline for data curation — [MatAnyone 2 project](https://pq-yang.github.io/projects/MatAnyone2/); [GitHub pq-yang/MatAnyone2](https://github.com/pq-yang/MatAnyone2)

**3D engines / synthetic rendering**
- Omniverse Replicator provides Semantic Schema Editor, Visualizer, Randomizers, omni.syntheticdata, Annotators and Writers; annotators include RGB, 2D/3D boxes, semantic and instance segmentation, depth, normals, occlusion — [NVIDIA Technical Blog](https://developer.nvidia.com/blog/build-custom-synthetic-data-generation-pipelines-with-omniverse-replicator/); [Replicator docs](https://docs.omniverse.nvidia.com/extensions/latest/ext_replicator.html)
- No search result showed a dedicated soft "alpha matte" annotator in Replicator; its segmentation outputs are hard masks — [search summary of Replicator docs](https://docs.omniverse.nvidia.com/extensions/latest/ext_replicator/visualization.html) (see Gaps)
- A study created >22,000 synthetic human images with Replicator for human body segmentation — [PMC11342039](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC11342039/)
- Blender Cycles: community reports of pitfalls with alpha in multilayer EXR (speckled alpha when "convert premultiplied" is toggled in After Effects; hair rendering black areas when alpha is misconfigured) — [Adobe community thread](https://community.adobe.com/questions-529/exr-multilayer-alpha-channel-issues-from-blender-50978); [Blender Artists thread](https://blenderartists.org/t/exr-multilayer-forgets-the-alpha-channel/1524495); [Blender bug T52680](https://developer.blender.org/T52680)

**Licenses of synthetic-human assets/datasets**
- MetaHuman (now in UE 5.6, standard UE EULA): may be used in AI workflows but not to train or enhance AI models; EULA adds "express language against use of the Licensed Technology as a training input or prompt-based input into Generative AI Programs" — [CG Channel](https://www.cgchannel.com/2025/06/you-can-now-sell-metahumans-or-use-them-in-unity-or-godot/); [Digital Production](https://digitalproduction.com/2025/06/05/metahumans-graduate-ready-for-unity-godot-and-the-fab-cash-register/); [UE EULA change log](https://www.unrealengine.com/eula-change-log/unreal)
- BEDLAM: Perceiving Systems PS:License 1.0; commercial use requires contacting Max Planck Innovation (smpl@max-planck-innovation.de / ps-license@tue.mpg.de). BEDLAM2.0 requires accepting a license and users must ensure use aligns with asset licensors — [BEDLAM license](https://bedlam.is.tuebingen.mpg.de/license.html); [bedlam_render LICENSE](https://github.com/PerceivingSystems/bedlam_render/blob/main/LICENSE.md); [BEDLAM2.0](https://bedlam2.is.tuebingen.mpg.de/)
- Microsoft "Fake It Till You Make It" Face Synthetics: 100,000 synthetic faces with 2D landmarks and per-pixel segmentation; Microsoft Research Use of Data Agreement v1.0, non-commercial research only — [FaceSynthetics README](https://github.com/microsoft/FaceSynthetics/blob/main/README.md); [project page](https://microsoft.github.io/FaceSynthetics/)

**AI video generators / RGBA generation**
- Runway: does not claim ownership of outputs and does not restrict commercial use for paid plans; but grants Runway a perpetual, irrevocable, sublicensable license over inputs/outputs for training (except Enterprise); free plan limited to non-commercial — [Terms.Law analysis of Runway](https://terms.law/ai-output-rights/runway/) (secondary; Runway ToS page itself was blocked: [Runway Terms](https://runway.com/terms-of-use))
- OpenAI terms prohibit using Output to develop models that compete with OpenAI; there is a permitted exception for classifiers/embedding-type models not distributed to third parties — [OpenAI Terms of Use](https://openai.com/policies/row-terms-of-use/); [OpenAI Services Agreement](https://openai.com/policies/services-agreement/)
- Google Gemini API terms: may not use the Services to develop models that compete with the Services; Google's Generative AI Additional Terms prohibit using the Services to develop ML models or related technology — [Gemini API Additional Terms](https://ai.google.dev/gemini-api/terms); [Google Generative AI Additional Terms](https://policies.google.com/terms/generative-ai)
- Veo: output is Customer Data (no Google ownership) on Vertex AI; all Veo output carries invisible SynthID watermark; consumer tiers add visible badge — [InVideo Kling vs Veo comparison](https://invideo.io/blog/kling-3-vs-veo-3-1/) (secondary)
- Kling: paid plans carry commercial-use rights; free-tier outputs watermarked and personal use — [InVideo](https://invideo.io/blog/kling-3-vs-veo-3-1/) (secondary)
- Research RGBA video generators exist: TransPixar/TransPixeler (CVPR 2025, Adobe et al.) extends a pretrained DiT video model with alpha tokens + LoRA to jointly generate RGB and alpha; the authors note RGBA generation is hard "due to limited datasets" — [TransPixar project](https://wileewang.github.io/TransPixar/); [HF paper page](https://huggingface.co/papers/2501.03006). Related: TransAnimate — [arXiv 2503.17934](https://arxiv.org/pdf/2503.17934)

### Inferences
- For a commercial product, the lowest-legal-risk synthetic path is: own green-screen captures (or licensed stock green-screen clips) → alpha extraction → compositing onto licensed/owned backgrounds, plus Blender/Omniverse renders using assets whose licenses permit ML training. MetaHuman is effectively excluded.
- AI-generated "green screen" clips from Sora/Veo/Kling/Runway do not come with true alpha; you would still have to key them, inheriting generator artifacts (fake spill, inconsistent hair) and the terms restrictions above (OpenAI/Google competing-model clauses; Runway's training license back to Runway). Watermarks (SynthID, visible badges) also contaminate data. Treat as low-value, high-risk for training labels.
- 3D rendering gives exact alpha (including motion blur and hair coverage) when rendered with transparent film and premultiplied EXR; the risk is domain gap in hair/cloth/skin realism, which is why research mixes synthetic with real-captured data.

### Gaps
- Could not verify Unity Perception's current status (it was reported deprecated by Unity in prior years; not re-confirmed in 2026).
- Could not confirm Microsoft SynthMoCap / SynthBody license or AGORA / SynBody licenses (search returned only FaceSynthetics).
- Could not read full Runway ToS or Kling ToS text to check for a specific clause prohibiting training third-party models on outputs.
- No official Replicator doc found describing a soft alpha-matte annotator; would need to derive alpha from RGB renders with transparent background.
- Sora-specific terms beyond OpenAI's general Terms of Use not checked.

## Deriving ground-truth alpha mattes from real green screen footage (keyers, spill, triangulation, clean plates, AI pseudo-labels)

### Takeaway
Single-background chroma keying is fundamentally under-constrained; the only mathematically exact real-capture method is Smith & Blinn triangulation matting (two known backgrounds, static subject). Practical pipelines combine a proper keyer (Keylight/IBK/Delta Keyer; ffmpeg chromakey+despill for batch) with clean plates, then increasingly use AI matting models plus automatic quality evaluation (MatAnyone 2's MQE) to produce/validate pseudo-labels at scale.

### Cited Findings
- Smith & Blinn (SIGGRAPH 1996) put blue-screen matting on an algebraic footing and introduced triangulation matting: imaging the foreground against two different known backgrounds allows solving alpha and foreground color without constraints on foreground colors — [Smith & Blinn PDF (Stanford mirror)](https://graphics.stanford.edu/courses/cs148-09-fall/papers/smith-blinn.pdf); [alvyray.com PDF](https://alvyray.com/Papers/CG/blusig96.pdf); [Brown CS1290 project](https://cs.brown.edu/courses/csci1290/2011/results/final/aabouche/)
- Real-time variants of triangulation exist, e.g., via passive polarization (SIGGRAPH 2006 sketch) — [ACM DL](https://dl.acm.org/doi/abs/10.1145/1179849.1179959)
- Magenta Green Screen: spectrally multiplexed alpha matting (lighting subject/background with different spectra) plus deep colorization — [arXiv 2306.13702](https://arxiv.org/pdf/2306.13702)
- ffmpeg `chromakey` performs YUV keying with `color`, `similarity` (0.01 = exact color only, 1.0 = everything), `blend` (0 = binary; higher = semi-transparency proportional to similarity), `yuv` flag — [FFmpeg filters docs](https://ffmpeg.org/ffmpeg-filters.html); [chromakey 7.1 docs](https://ayosec.github.io/ffmpeg-filters-docs/7.1/Filters/Video/chromakey.html)
- ffmpeg `despill` removes spill; green should be set to -1 for greenscreen (blue -1 for bluescreen), with brightness control to preserve colors — [despill 8.0 docs](https://ayosec.github.io/ffmpeg-filters-docs/8.0/Filters/Video/despill.html)
- BGMv2 uses a captured background (clean plate) as an extra input to estimate alpha — [BGMv2](https://ar5iv.labs.arxiv.org/html/2012.07810); CineMatte extends this idea to LED volumes with DINOv3 features — [CineMatte](https://openaccess.thecvf.com/content/CVPR2026F/html/He_CineMatte_Background_Matting_for_Virtual_Production_and_Beyond_CVPRF_2026_paper.html)
- MatAnyone 2's Matting Quality Evaluator produces a pixel-level map of reliable vs erroneous regions in generated mattes without reference GT, used to curate VMReal (2.4M frames); reports −26% MAD and −24.5% gradient error vs MatAnyone 1 on CRGNN — [MatAnyone 2 project](https://pq-yang.github.io/projects/MatAnyone2/); [aifilms summary](https://studio.aifilms.ai/blog/matanyone-2-video-matting) (secondary for numbers)
- MatAnyone's interactive demo uses SAM/SAM2 for the first-frame mask then propagates matting — [MatAnyone2 GitHub](https://github.com/pq-yang/MatAnyone2)
- SAM2Matting (2026) proposes generalized image/video matting built on SAM2 — [arXiv 2606.27339](https://arxiv.org/pdf/2606.27339) (only title/abstract snippet seen)

### Inferences
- Recommended label pipeline: (1) shoot with clean plate (empty-stage frames per setup); (2) key with a professional keyer (Nuke IBK/Keylight, Resolve Delta Keyer) using clean-plate difference, store alpha as 16-bit PNG or EXR; (3) despill foreground separately and store despilled FG (the FG color, not the original green-contaminated RGB) — RVM/VideoMatte240K store separate `fgr` and `pha`; (4) cross-check with an AI matting model (MatAnyone 2 / RVM / BiRefNet) and flag frames where they disagree strongly for manual review; (5) for a small "gold" evaluation set, capture static subjects with two-background triangulation.
- ffmpeg chromakey is fine for bulk previews/rough masks but its YUV-distance+blend model produces approximated edges; it should not be the sole source of hair-level GT.
- Keying and despill are different things: training labels need both alpha AND spill-free foreground color; otherwise composites onto new backgrounds show green fringes that the model learns.

### Gaps
- No primary docs fetched for Nuke Keylight/IBK, After Effects Keylight, or DaVinci Resolve Delta/Ultra Keyer (vendor manuals not retrieved in this pass).
- BiRefNet licensing/usage for pseudo-labels not verified in this pass.
- No quantitative comparison found between classic keyer mattes and triangulation GT error.

## Capture best practices (lighting, codec/bit depth, resolution, frame rate, motion blur, hair, wardrobe, green vs blue, LED volume)

### Takeaway
Shoot 10-bit (or RAW), 4:2:2 or 4:4:4, lightly compressed (ProRes 422 HQ / 4444 or RAW), light the screen evenly and separately from the subject, and keep the subject well away from the screen to minimize spill and shadows.

### Cited Findings
- 4:4:4 or 4:2:2 performs significantly better for keying; 4:2:0 causes jagged edges, poor keying, color bleeding; external recorders via clean HDMI/SDI can capture higher chroma sampling than internal codecs — [Luminxel chroma subsampling](https://luminxel.com/chroma-subsampling-explained-444-422-420/)
- Use the highest bit-rate / least compressed codec possible; 10-bit superior to 8-bit; ProRes 422/4444 good, RAW better — [PremiumBeat guide](https://www.premiumbeat.com/blog/chroma-key-green-screen-guide/)
- Light foreground and backdrop separately; light the screen evenly; light the screen first, then the subject; "biggest mistake" is lighting screen and subject as one — [PremiumBeat](https://www.premiumbeat.com/blog/chroma-key-green-screen-guide/); [Adobe green screen guide](https://www.adobe.com/ng/creativecloud/video/discover/how-to-use-green-screen.html)
- Keep subject at least ~6 feet from the screen to minimize spill and shadows — [Adobe](https://www.adobe.com/ng/creativecloud/video/discover/how-to-use-green-screen.html)
- Chroma subsampling background — [Wikipedia](https://en.wikipedia.org/wiki/Chroma_subsampling)
- LED VP: CineMatte-4K captured in 4K HDR on a professional LED stage, with tracked camera trajectories; the background shown on the LED wall is known and can be used as a background input — [CineMatte](https://arxiv.org/abs/2605.18328) (snippet)
- VideoMatte240K source clips are 4K/HD — [RVM paper snippet](https://arxiv.org/pdf/2108.11515)

### Inferences
- For training data specifically: capture at the resolution you intend to train high-res refiners at (RVM stage 3/4 uses 2048p crops, so 4K source is justified); 25-60 fps is common; keep natural motion blur (models must learn semi-transparent blur), but use shutter ≈180° so blur is realistic rather than excessive.
- Wardrobe: avoid green (or blue with blue screen), shiny/reflective and very fine semi-transparent fabrics unless intentionally sampling hard cases; include varied hair (loose, curly, flyaways) since hair is where metrics differ.
- Green vs blue: green typically preferred for digital sensors (more luminance/less noise in green channel) and blue for less spill/green wardrobe — general industry knowledge, not verified with a source in this pass.
- Record a clean plate each time lighting or camera changes; lock exposure/white balance.

### Gaps
- No authoritative source retrieved on green vs blue trade-offs, recommended shutter angle, or specific IRE/exposure targets for screen vs subject.
- No source retrieved on LED-volume-specific capture issues (moire, color shift) for matting data.

## Dataset formats, size and augmentation

### Takeaway
Standard layout is per-clip frame sequences with separate foreground (`fgr`) and alpha (`pha`) images, composited on the fly with backgrounds; EXR/16-bit PNG for alpha precision, JPEG only for bulk FG at lower stages. Research-scale datasets range from hundreds of clips (VideoMatte240K: 484 clips) to tens of thousands of auto-labelled real clips (VMReal: 28k clips/2.4M frames).

### Cited Findings
- RVM dataset structure: VideoMatte240K distributed as JPEG SD (6GB) and HD (60GB) with separate foreground and alpha frames; ImageMatte combines D646 + AIM humans — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)
- Scale reference points: VideoMatte240K 484 clips; RVM backgrounds 3,118 video clips + 8,000 images; BG-20k 20,000 images; CineMatte-4K 500 images + 30 clips; VMReal 28,000 clips / 2.4M frames — [RVM paper](https://arxiv.org/pdf/2108.11515); [VIM WACV24](https://openaccess.thecvf.com/content/WACV2024/papers/Li_Video_Instance_Matting_WACV_2024_paper.pdf); [CineMatte](https://arxiv.org/abs/2605.18328); [MatAnyone 2](https://pq-yang.github.io/projects/MatAnyone2/)
- Temporal augmentation (continuous affine, color jitter, noise, blur across frames) for FG and BG — [RVM paper](https://arxiv.org/pdf/2108.11515)
- Co-training with segmentation datasets (COCO, YouTubeVIS, Supervisely) is used to reduce synthetic-composite domain gap — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)

### Inferences
- Recommended storage: `clip_xxxx/fgr/000001.png` (despilled FG, 8/16-bit), `clip_xxxx/pha/000001.png` (16-bit single-channel or EXR), optional `bgr/` clean plate and `trimap/` (derived by eroding/dilating alpha). Keep premultiplied vs straight alpha convention documented; mismatches cause dark/bright fringes.
- A few hundred diverse green-screen clips is enough to fine-tune an existing matting model (RVM trained its main matting stages on 484 clips), provided backgrounds are large and diverse and segmentation data is mixed in.

### Gaps
- No authoritative statement found on minimum dataset size for training from scratch vs fine-tuning.

## Common pitfalls (green spill in labels, compression artifacts, synthetic→real domain gap)

### Takeaway
The main label-quality failures are 4:2:0/8-bit compression destroying edge chroma, green spill left in foreground colors, and composite-only training that fails on real footage; mitigations are high-quality capture, explicit despill + clean plates, mixing real data, and automated matte quality checks.

### Cited Findings
- 4:2:0 subsampling → jagged edges, poor keying, color bleeding — [Luminxel](https://luminxel.com/chroma-subsampling-explained-444-422-420/)
- Spill control depends on distance and separate lighting — [Adobe](https://www.adobe.com/ng/creativecloud/video/discover/how-to-use-green-screen.html)
- Despill is a separate processing step (ffmpeg despill) from alpha extraction — [ffmpeg despill](https://ayosec.github.io/ffmpeg-filters-docs/8.0/Filters/Video/despill.html)
- CineMatte uses frozen DINOv3 features to "preserve pretrained semantics and improve robustness to background shifts" and reports generalization to real-world footage across VideoMatte240K and YouTubeMatte — [CineMatte snippet](https://arxiv.org/abs/2605.18328)
- MatAnyone 2 motivates its quality evaluator by the difficulty of getting reliable real-world labels; erroneous regions are suppressed during training — [MatAnyone 2](https://pq-yang.github.io/projects/MatAnyone2/)
- Blender EXR alpha/premultiplication confusions produce speckled or wrong alpha in downstream tools — [Adobe community](https://community.adobe.com/questions-529/exr-multilayer-alpha-channel-issues-from-blender-50978)
- RGBA generative video is limited by scarce datasets — [TransPixar](https://wileewang.github.io/TransPixar/)

### Inferences
- Composites of green-screen foregrounds onto random backgrounds have lighting/color mismatches (subject lit for a studio, background outdoors); models can learn to exploit such cues. Mitigate with color/lighting harmonization augmentation and by mixing real in-the-wild data (segmentation or pseudo-labelled matting).
- Always check that alpha is not binarized by the keyer (e.g., ffmpeg chromakey with blend=0), and that motion-blurred edges retain fractional alpha.

### Gaps
- No quantitative study retrieved measuring how much spill contamination in labels degrades model accuracy.
