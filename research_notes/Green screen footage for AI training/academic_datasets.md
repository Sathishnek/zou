# Open Academic Datasets for Green Screen / Chroma Key, Matting and Human Segmentation (as of Sept 2026)

Research-environment note: arxiv.org, huggingface.co, kaggle.com, opendatalab.com, grail.cs.washington.edu (BGMv2 dataset page), jizhizili.github.io (release-agreement PDFs) and maggie-matt.github.io were blocked by the network proxy during this session. GitHub READMEs and web search results were reachable. Where a licence could only be read second-hand (search snippet or README summary) it is marked **[unverified]**. Items stated from general knowledge with no fetched source are placed in Gaps.

## Q1. Which datasets exist? (catalog)

### Takeaway
There are roughly 20 relevant public or semi-public sets. Video matting sets with real alpha are almost all built by **keying purchased green-screen stock footage** (VideoMatte240K, VM800, VideoMatting108) and then compositing onto background sets (BG-20k, DVM backgrounds). Image matting sets (Adobe DIM/Composition-1k, Distinctions-646, AIM-500, P3M-10k, AM-2k, PPM-100, RefMatte) use hand-annotated alpha. The largest new set, VMReal (MatAnyone 2, CVPR 2026, 28K real clips, 2.4M frames), is announced but **not yet released**.

### Cited Findings

**Video matting: green-screen-derived**
- **VideoMatte240K** (Lin, Ryabtsev et al., "Real-Time High-Resolution Background Matting", CVPR 2021 / BGMv2). 484 high-resolution green-screen videos giving 240,709 unique frames of alpha mattes and foregrounds, extracted with chroma-key software (Adobe After Effects). 384 videos are 4K and 100 are HD; 479 train and 5 test. — [CVPR paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Lin_Real-Time_High-Resolution_Background_Matting_CVPR_2021_paper.pdf); [search summary of paper](https://arxiv.org/pdf/2012.07810)
  - Released April 21, 2021. Download is on the BGMv2 datasets page (grail.cs.washington.edu/projects/background-matting-v2/#/datasets). — [BGMv2 GitHub](https://github.com/PeterL1n/BackgroundMattingV2)
  - Comes in two variants: JPEG SD (6 GB) and JPEG HD (60 GB). RVM moves clips 0000, 0100, 0200 and 0300 from train to validation. — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)
  - The MatAnyone docs describe it as "475 foreground videos with alpha mattes" and as the publicly available alternative to VM800. — [MatAnyone TRAIN.md](https://github.com/pq-yang/MatAnyone/blob/main/doc/TRAIN.md)
  - The VideoMatte240K-Test benchmark has 5 foregrounds from purchased footage. — [MatAnyone GitHub](https://github.com/pq-yang/MatAnyone)
- **PhotoMatte13K / PhotoMatte85** (BGMv2, 2021). PhotoMatte13K has 13,665 images shot in front of a green screen with studio-quality lighting; mattes were extracted by chroma keying. Because of privacy and licensing issues, only 85 mattes of similar quality were released, as PhotoMatte85 (published Jan 9, 2021). — [search summary of BGMv2 paper](https://arxiv.org/pdf/2012.07810); [BGMv2 GitHub](https://github.com/PeterL1n/BackgroundMattingV2)
  - BGMv2 also released a background set of 8,861 high-resolution images crawled from Flickr and Google; all images have a CC licence. — [search summary of BGMv2 paper](https://arxiv.org/pdf/2012.07810) **[unverified snippet]**
- **VM800** (Yang et al., MatAnyone, CVPR 2025, NTU S-Lab). 826 green-screen foreground videos from stock sites (Storyblocks, Envato Elements, Motion Array), processed in Adobe After Effects to get foregrounds and alpha mattes. It has almost twice as many foreground videos as VideoMatte240K. **Status: "cannot be publicly released" because of licensing restrictions.** — [MatAnyone TRAIN.md](https://github.com/pq-yang/MatAnyone/blob/main/doc/TRAIN.md); [MatAnyone 2 paper](https://arxiv.org/html/2512.11782v1)
- **YouTubeMatte** (MatAnyone, 2025). Evaluation-only benchmark with 32 foregrounds taken from YouTube videos. It comes as 512x288 and 1920x1080 versions. Foregrounds are composited with harmonization (Harmonizer) to make the benchmark harder. Download is via Google Drive. — [MatAnyone GitHub](https://github.com/pq-yang/MatAnyone)
- **VideoMatting108** (Zhang et al., "Attention-guided Temporally Coherent Video Object Matting", TCVOM, 2021). 108 clips at 1080p with GT alpha: 80 train, 28 val. Stored as FG RGBA plus BG RGB with a frame_corr.json (a composite setup). Total size 192 GB via OneDrive or BaiduYun. — [TCVOM GitHub](https://github.com/yunkezhang/TCVOM)
  - Built from green-screen footage, including 68 high-quality footages collected from the Internet. — [search summary](https://arxiv.org/pdf/2105.11427) **[unverified snippet]**
  - Licence: "The code, the trained model and the dataset are for academic and non-commercial use only." — [TCVOM GitHub](https://github.com/yunkezhang/TCVOM)
- **CRGNN dataset** (Wang et al., "Video Matting via Consistency-Regularized Graph Neural Networks", ICCV 2021). The real-world test data is on Dropbox. It has 19 real-world videos with alpha and FG manually annotated every 10 frames. The composited training set is available on request from the author by email. — [CRGNN GitHub](https://github.com/TiantianWang/VideoMatting-CRGNN); [search summary via MaGGIe](https://arxiv.org/pdf/2404.16035)
  - Code and models are non-commercial only, because models trained on Adobe data fall under the Adobe Image Dataset License Agreement. — [CRGNN GitHub](https://github.com/TiantianWang/VideoMatting-CRGNN)
- **V-HIM2K5 / V-HIM60, I-HIM50K / M-HIM2K** (Huynh et al., MaGGIe, CVPR 2024). Human *instance* matting sets. V-HIM2K5 is a video instance-matte set synthesized from VM108, VideoMatte240K and CRGNN; I-HIM50K uses HHM50K as its foreground source. — [MaGGIe paper, search summary](https://arxiv.org/pdf/2404.16035); [search result](https://github.com/ViTAE-Transformer/ViTAE-Transformer-Matting) **[licence unverified; project page blocked]**
- **SynHairMan** (from "Generative Video Matting", SIGGRAPH 2025). A synthetic video matting set with fine-grained hair annotations. MatAnyone 2 describes it as small and "purely synthetic composites." — [MatAnyone 2 search summary](https://arxiv.org/html/2512.11782v1); [ACM DL](https://dl.acm.org/doi/full/10.1145/3721238.3730642) **[size and licence unverified]**
- **VMReal** (Yang et al., MatAnyone 2, CVPR 2026 Highlight). 28K real-world clips with 2.4M frames. Annotation is automatic: a dual-branch pipeline plus a learned Quality Evaluator, with **no green screen**. The authors call it the first large-scale real-world video matting dataset. The GitHub TODO still lists "Release real-world video matting dataset VMReal", so it is **not released**. Code and model are under the NTU S-Lab License 1.0. — [MatAnyone 2 project/search](https://pq-yang.github.io/projects/MatAnyone2/); [MatAnyone2 GitHub](https://github.com/pq-yang/MatAnyone2)

**Image matting (alpha GT)**
- **Adobe Deep Image Matting dataset / Composition-1k** (Xu, Price, Cohen, Huang, CVPR 2017). Access is by emailing Brian Price (bprice@adobe.com). Covered by the "Adobe Deep Image Matting Dataset License Agreement". Models pretrained on it "can only be used and distributed for noncommercial purposes." — [GCA-Matting README](https://github.com/Yaoyi-Li/GCA-Matting/blob/master/README.md); [licence PDF mirror](https://github.com/sinfere/Deep-Image-Matting-v2/blob/master/Combined_Dataset/Adobe%20Deep%20Image%20Mattng%20Dataset%20License%20Agreement.pdf); [DIM paper](https://openaccess.thecvf.com/content_cvpr_2017/papers/Xu_Deep_Image_Matting_CVPR_2017_paper.pdf)
- **Distinctions-646** (Qiao et al., HAttMatting, CVPR 2020). 646 foregrounds with manually annotated alpha. Obtained by email request, "for academic research" / non-commercial. — [HAttMatting GitHub](https://github.com/yuhaoliu7456/CVPR2020-HAttMatting)
- **"ImageMatte"** (RVM/MatAnyone convention). The human-only subset of D646 plus Adobe DIM, used in the final training stage. Because it inherits both licences, it is non-commercial. — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)
- **AIM-500** (Li et al., IJCAI 2021). 500 high-resolution natural images: Portrait 100, Animal 200, Transparent 34, Plant 75, Furniture 45, Toy 36, Fruit 10. Manually labelled alpha. Download via Google Drive or Baidu (pw 0l69). Described as "MIT License" plus a release agreement PDF. — [AIM GitHub](https://github.com/JizhiziLi/AIM)
- **AM-2k** (Li et al., GFM, IJCV 2022). 2,000 high-resolution animal images in 20 categories with manual alpha. Download via Google Drive or Baidu (pw 29r1). "MIT License" plus release agreement. — [GFM GitHub](https://github.com/JizhiziLi/GFM)
- **BG-20k** (GFM, 2022). 20,000 high-resolution background images with no salient objects, used for compositing. "MIT License" plus release agreement. — [GFM GitHub](https://github.com/JizhiziLi/GFM)
- **P3M-10k** (Li et al., ACM MM 2021 / IJCV 2023). 10,421 face-blurred portrait images with manual alpha: 9,421 train, P3M-500-P (blurred test) and P3M-500-NP (non-blurred celebrity test). Images were collected online "with free-use licenses." "MIT License" plus release agreement. — [P3M GitHub](https://github.com/JizhiziLi/P3M); [agreement PDF (search snippet)](https://jizhizili.github.io/files/p3m_dataset_agreement/P3M-10k_Dataset_Release_Agreement.pdf)
- **PPM-100** (Ke et al., MODNet, AAAI 2022). 100 finely annotated high-resolution portraits (full or half body). Images come from Flickr under a "Flickr Creative Commons License (Commercial use & mods allowed)"; the **alpha annotations are CC BY-NC-SA 4.0**. — [PPM GitHub](https://github.com/ZHKKKe/PPM)
- **RefMatte / RefMatte-RW100** (Li et al., Referring Image Matting, CVPR 2023). 47,500 synthetic composite images, 230 categories, 118,749 expression-region entities, 474,996 expressions; 43.7 GB via OneDrive. RW100 is a real-world test set of 66.6 MB. **CC BY-NC.** — [RIM GitHub](https://github.com/JizhiziLi/RIM)
- **MAGICK** (Burgert, Price et al., CVPR 2024, Stony Brook + Adobe). About 140K–150K captioned, single-subject 1024x1024 RGBA images. The alpha comes from **chroma keying generated images**: a text-to-image model renders subjects on a solid key colour, which is then keyed. About 200 GB, on HF OneOverZero/MAGICK. **CC BY-NC 4.0** [per search summary]. — [MAGICK GitHub](https://github.com/RyannDaGreat/MAGICK); [CVPR paper](https://openaccess.thecvf.com/content/CVPR2024/papers/Burgert_MAGICK_A_Large-scale_Captioned_Dataset_from_Matting_Generated_Images_using_CVPR_2024_paper.pdf); [HF](https://huggingface.co/datasets/OneOverZero/MAGICK)
- **AISegment.com Matting Human Datasets** (Kaggle). 34,427 half-length portraits at 600x800 with matting results. Images come from Flickr, Baidu and Taobao. Annotated by Beijing Play Star Convergence Technology; a model trained on it was commercialized. — [Kaggle](https://www.kaggle.com/datasets/laurentmih/aisegmentcom-matting-human-datasets) **[Kaggle licence field unverified; page blocked]**
- **Nexdata 25,080-image Alpha Matte Human Body Segmentation** (HF). A **commercial vendor sample** of a paid dataset, not an academic one. — [HF commit](https://huggingface.co/datasets/Nexdata/25080_Images_Alpha_Matte_Human_Body_Segmentation_Data_Basic_Version/commit/0f30dc7516754cee2e84c05d25412457f999dad4)

**Segmentation and background sets used alongside matting (RVM/MatAnyone recipe)**
- COCO train2017 + panoptic; YouTubeVIS 2021; Supervisely Person Dataset (preprocessed 800 MB); DVM background videos (train 14.6 GB, test 936 MB); 8,000 unpublished crawled image backgrounds. — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md); [MatAnyone TRAIN.md](https://github.com/pq-yang/MatAnyone/blob/main/doc/TRAIN.md)

### Inferences
- In practice, the only openly downloadable real-alpha **video** sets are VideoMatte240K (about 475–484 clips), VideoMatting108 and the small CRGNN test set. Every modern video matting model (RVM, MatAnyone, MaGGIe) mixes these with image matting sets and segmentation data.
- The field is moving from green-screen stock toward **auto-labelled real footage** (VMReal) and **generated-then-keyed** data (MAGICK). This suggests that producing proprietary green-screen footage in-house is still one of the few routes to commercially clean, high-quality alpha GT.

### Gaps
- Exact counts for HHM50K/HHM2K, Human-2K, Semantic Image Matting (SIMD), TransMatting (Transparent-460), and the SynHairMan and MaGGIe dataset licences could not be fetched (project pages and arXiv were blocked).
- Adobe DIM split sizes (431 train FG / 50 test FG composited into 43,100 / 1,000 images for Composition-1k) come from general knowledge and were not re-verified this session.
- Distinctions-646's split (596/50) was not verified.
- Hugging Face and Kaggle "green screen" collections could not be browsed directly. Only MAGICK, Nexdata and AISegment surfaced in search.

## Q2. Which were captured against green screen, and how were mattes derived?

### Takeaway
The green-screen-derived sets are VideoMatte240K, PhotoMatte13K/85, VM800, VideoMatting108 (largely) and MAGICK (a virtual key colour on generated images). Mattes were pulled with Adobe After Effects (Keylight plus cleanup). The image matting benchmarks (DIM, D646, AIM, P3M, AM-2k, PPM) are hand-annotated. VMReal uses no green screen at all.

### Cited Findings
- VideoMatte240K: 484 green-screen videos keyed with chroma-key software (Adobe After Effects). — [CVPR 2021 paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Lin_Real-Time_High-Resolution_Background_Matting_CVPR_2021_paper.pdf)
- PhotoMatte13K: studio-lit green-screen photos, keyed. — [BGMv2 paper summary](https://arxiv.org/pdf/2012.07810)
- VM800: stock green-screen footage keyed in After Effects. — [MatAnyone TRAIN.md](https://github.com/pq-yang/MatAnyone/blob/main/doc/TRAIN.md)
- The common practice is After Effects Keylight, supplemented by Key Cleaner and Advanced Spill Suppressor. Chroma-keyed alpha quality is often inconsistent and needs manual parameter tuning. — [search summary of Generative Video Matting / VM papers](https://arxiv.org/html/2508.07905v1) **[snippet-level]**
- Magenta Green Screen (2023) proposes a spectrally multiplexed alternative to green-screen keying. — [arXiv 2306.13702](https://arxiv.org/html/2306.13702) **[not fetched; dataset release unknown]**
- MAGICK: alpha is obtained by chroma keying of generated images. — [MAGICK GitHub](https://github.com/RyannDaGreat/MAGICK)
- VMReal: automatic dual-branch annotation plus a learned Quality Evaluator that scores alpha quality without GT. — [MatAnyone 2](https://pq-yang.github.io/projects/MatAnyone2/)
- Earlier sets (VM108, VideoMatte240K, VM800, SynHairMan) are "purely synthetic composites of foregrounds and backgrounds". — [MatAnyone 2](https://arxiv.org/html/2512.11782v1)

### Inferences
- Because these keyed mattes carry **foreground colour (FG RGB)** as well as alpha, they allow physically correct recompositing. That is an advantage over segmentation-only data, which is useful for a green-screen training pipeline.

### Gaps
- The per-dataset keying QA process (manual cleanup extent) is not documented publicly for VideoMatte240K.

## Q3. Commercial use vs research-only

### Takeaway
Almost nothing with high-quality alpha GT is clearly commercial-safe.
- **Explicitly non-commercial:** Adobe DIM/Composition-1k, Distinctions-646, VideoMatting108, CRGNN (via Adobe), RefMatte (CC BY-NC), MAGICK (CC BY-NC 4.0), PPM-100 annotations (CC BY-NC-SA 4.0).
- **Unreleased:** VM800 and VMReal.
- **Labelled "MIT" in the READMEs (with release agreements whose full text could not be verified):** the JizhiziLi sets (P3M-10k, AM-2k, AIM-500, BG-20k).
- **Unknown:** VideoMatte240K's own data licence could not be confirmed. The BGMv2 *code* is MIT, but that does not necessarily cover the purchased stock footage.

### Cited Findings
- BGMv2 code is MIT: "permits commercial use", relicensed Dec 21, 2020. — [BGMv2 GitHub](https://github.com/PeterL1n/BackgroundMattingV2)
- The PhotoMatte release was limited to 85 mattes because of "privacy and licensing issues". — [BGMv2 paper summary](https://arxiv.org/pdf/2012.07810)
- VM800 "cannot be publicly released" because of licensing restrictions (stock footage). — [MatAnyone TRAIN.md](https://github.com/pq-yang/MatAnyone/blob/main/doc/TRAIN.md)
- VideoMatting108 is "for academic and non-commercial use only". — [TCVOM GitHub](https://github.com/yunkezhang/TCVOM)
- Adobe DIM: its licence agreement means pretrained models are usable and distributable for noncommercial purposes only. — [GCA-Matting README](https://github.com/Yaoyi-Li/GCA-Matting/blob/master/README.md)
- Distinctions-646 is for academic, non-commercial use, by email request. — [HAttMatting GitHub](https://github.com/yuhaoliu7456/CVPR2020-HAttMatting)
- RefMatte is CC BY-NC. — [RIM GitHub](https://github.com/JizhiziLi/RIM)
- PPM-100 mattes are CC BY-NC-SA 4.0; the underlying Flickr images are commercial-OK CC. — [PPM GitHub](https://github.com/ZHKKKe/PPM)
- MAGICK is CC BY-NC 4.0. — [search summary citing HF/GitHub](https://huggingface.co/datasets/OneOverZero/MAGICK) **[unverified directly]**
- P3M-10k, AM-2k, BG-20k and AIM-500 are "MIT License" per the READMEs, subject to a Dataset Release Agreement. The P3M agreement states the dataset is "aimed to aid research efforts" and "is under MIT license". — [P3M GitHub](https://github.com/JizhiziLi/P3M); [GFM GitHub](https://github.com/JizhiziLi/GFM); [AIM GitHub](https://github.com/JizhiziLi/AIM); [P3M agreement PDF, snippet](https://jizhizili.github.io/files/p3m_dataset_agreement/P3M-10k_Dataset_Release_Agreement.pdf)
- MatAnyone and MatAnyone 2 code and models use the NTU S-Lab License 1.0 (typically non-commercial; full text not verified). — [MatAnyone GitHub](https://github.com/pq-yang/MatAnyone); [MatAnyone2 GitHub](https://github.com/pq-yang/MatAnyone2)
- RVM's final stage trains on D646 plus Adobe DIM, both non-commercial. — [RVM training.md](https://github.com/PeterL1n/RobustVideoMatting/blob/master/documentation/training.md)

### Inferences
- "MIT" on the JizhiziLi datasets covers the annotations. The images themselves are web-collected ("free-use licenses"), so commercial use still carries third-party image-rights and privacy risk (P3M contains real people). Legal review is needed before commercial training.
- Any model trained with the RVM or MatAnyone recipes inherits Adobe/D646 non-commercial constraints. Commercial green-screen AI projects would likely need their own captured or licensed footage.

### Gaps
- VideoMatte240K and PhotoMatte85 dataset terms: the BGMv2 datasets page was blocked, and no primary source was found stating the data licence. This is the key open item.
- The full text of the JizhiziLi release agreements (commercial clauses) could not be read.
- The licence for the Kaggle AISegment set, and details of Supervisely Person licensing, were not verified.
- Licences for HHM, Human-2K, SIMD, Transparent-460 and SynHairMan were not found.

## Q4. Hugging Face / Kaggle / Papers with Code green-screen collections

### Takeaway
Hub coverage is thin and was only partly checked, because HF and Kaggle were blocked. Notable entries:
- **HF:** OneOverZero/MAGICK (CC BY-NC) and World-Snapshot/MAGICK_Transparency.
- **Kaggle:** AISegment Matting Human (34K portraits).
- **Commercial vendor samples:** e.g. Nexdata.
- **Papers with Code:** has dataset pages for VideoMatte240K, PhotoMatte85 and P3M-10k.

### Cited Findings
- HF MAGICK and MAGICK_Transparency repos exist. — [HF MAGICK](https://huggingface.co/datasets/OneOverZero/MAGICK); [HF MAGICK_Transparency](https://huggingface.co/datasets/World-Snapshot/MAGICK_Transparency)
- Kaggle AISegment: 34,427 images, 600x800. — [Kaggle](https://www.kaggle.com/datasets/laurentmih/aisegmentcom-matting-human-datasets)
- Papers with Code dataset pages: [VideoMatte240K](https://paperswithcode.com/dataset/videomatte240k), [PhotoMatte85](https://paperswithcode.com/dataset/photomatte85), [P3M-10k](https://paperswithcode.com/dataset/p3m-10k)
- Free green-screen stock sites (Mixkit, Vecteezy) offer raw green-screen clips without GT. — [Mixkit](https://mixkit.co/free-stock-video/green-screen/); [Vecteezy](https://www.vecteezy.com/free-videos/green-screen)
- The MSU Video Matting Benchmark (videomatting.com) is an evaluation benchmark. — [videomatting.com](https://videomatting.com/)
- Background Matting v1 ("The World is Your Green Screen", CVPR 2020) is related work. — [Background-Matting GitHub](https://github.com/senguptaumd/Background-Matting)

### Inferences
- Stock-site green-screen clips could be keyed in-house, in the same way VM800 and VideoMatte240K were. The stock licence, though, governs whether the resulting mattes can be redistributed; this is why VM800 was not released.

### Gaps
- No systematic scan of HF or Kaggle "green screen" tags was possible. The licences of the MSU benchmark and Mixkit/Vecteezy, as they apply to ML training, were not checked.
