# Stock Green Screen Footage Sources and AI/ML Training Licensing (as of Sept 2026)

Method note: The sandbox's egress proxy blocked direct fetches of every stock-site page tried (pexels.com, help.pexels.com, pixabay.com, stock.adobe.com, elements.envato.com, mixkit.co, vecteezy.com, storyblocks.com). Clause wording below comes from search-engine excerpts of the official pages, and the official URL is cited each time. Wording is a close paraphrase or quote of those excerpts. It was not read from the full page, so confirm the exact text before any legal reliance. I did not collect volume or resolution counts per site (for example, "N green screen clips in 4K"), so they are listed as gaps.

## Q1: Free sources and whether their licenses allow ML training

### Takeaway
None of the major "free" stock video sites allows ML training under its default license. Pexels, Pixabay, Coverr, Mixkit (Envato), Vecteezy (free tier), ProductionCrate/FootageCrate and ActionVFX (including free assets) all ban AI/ML training, scraping or bulk collection outright, unless you get explicit permission or buy a separate enterprise/data license. Only openly licensed material (CC0 / CC BY on Wikimedia Commons, YouTube CC BY, Internet Archive) is usable without a separate deal, and it still carries attribution and people/likeness risk.

### Cited Findings
- **Pexels (owned by Canva):** The terms prohibit "data mining, extraction, scraping and the use of programs or robots for automatic data collection and/or extraction… for all unauthorised purposes, including machine learning purposes." The AI/ML FAQ says you may not use the API "to collect Pexels photos/videos or metadata at scale to train, fine-tune, evaluate, or otherwise develop ML/AI models or datasets, unless you have explicit permission from Pexels." — [Pexels Terms](https://www.pexels.com/terms-of-service/); [Pexels AI and ML FAQ](https://help.pexels.com/hc/en-us/articles/27292485713945-AI-and-ML-FAQ)
- **Pexels, other direction:** Pexels, its affiliates and "third party partners specifically authorised by Pexels" may use contributor content "including through the use of machine learning technology." Contributors can opt out of AI training in profile settings. So Pexels licenses or uses the content for AI itself, but downloaders may not. — [Pexels AI and ML FAQ](https://help.pexels.com/hc/en-us/articles/27292485713945-AI-and-ML-FAQ); [Terms & Policy Update 2024](https://help.pexels.com/hc/en-us/articles/22114560160409-Terms-Policy-Update-2024)
- **Pexels API:** A free API exists ([Pexels API](https://www.pexels.com/api/)), but the terms above forbid at-scale collection for ML.
- **Canva's content license** (Canva owns Pexels and Pixabay) prohibits use for ML/AI "for identification of natural persons." It notes that Pixabay, Pexels and CC0 licenses may differ and should be checked. — [Canva Content License Agreement](https://www.canva.com/policies/content-license-agreement/)
- **Pixabay:** The terms prohibit "data mining, extraction, scraping and the use of programs or robots for automatic data collection… including for machine learning purposes." "Bulk, large-scale or systematic copying" is prohibited without explicit permission. Content cannot be used to train ML models or be built into AI generation tools, and redistribution for ML or database-building is not allowed. Pixabay itself may use uploads to develop AI, with a contributor opt-out. — [Pixabay Terms](https://pixabay.com/service/terms/); [Pixabay FAQ](https://pixabay.com/service/faq/)
- **Coverr:** The license says videos and music "must not be used to train AI algorithms, develop AI models, or serve as part of any dataset for such purposes." It is otherwise free for commercial use with no attribution. — [Coverr License](https://coverr.co/license)
- **Mixkit (Envato):** Envato's Acceptable Use Policy covers Elements, Market, Placeit and Mixkit. It prohibits "the use of Envato Sites or Assets to train, develop, or enhance artificial intelligence models or machine learning algorithms, whether directly or indirectly." A breach is "material" and can lead to termination or legal action. The Mixkit License separately bars redistributing raw files or building a competing stock service. — [Envato Acceptable Use Policy](https://help.elements.envato.com/hc/en-us/articles/31035788503321-Acceptable-Use-Policy); [Mixkit License](https://mixkit.co/license/); [LicenseOrg Mixkit guide](https://www.licenseorg.com/guide/video/mixkit)
- **Vecteezy:** Content "may not be used for data training purposes" under the Free, Pro Standard, Pro Business or Pro Enterprise licenses unless the license explicitly permits data training. There is an Enterprise option that covers datasets, model development and training AI products (internal and commercial). — [Vecteezy License Agreement](https://www.vecteezy.com/licensing-agreement)
- **Videvo / Videezy:** The official license pages exist ([Videvo license types](https://help.videvo.net/article/27-license-types-and-usage); [Videezy Standard License](https://support.videezy.com/en_us/videezy-standard-license-and-usage-HylDtxsDK)), but my searches did not surface any AI/ML clause. **UNVERIFIED.** Some Videvo/Videezy free clips require attribution.
- **ProductionCrate / FootageCrate (free and paid):** The terms prohibit using media for "training, developing, testing, or fine-tuning" AI/ML/deep learning/neural network models, "generating synthetic data," or making derivative content to train generative or analytical models. Acceptance is framed as an "express contractual waiver" of any fair-use defense for AI use. — [ProductionCrate Terms](https://www.productioncrate.com/terms.html)
- **ActionVFX (free and paid assets):** Its EULA prohibits using assets to train ML models, AI systems, neural networks "or any other automated systems" without prior written consent. This applies to free and purchased assets alike, and violation means account termination or possible legal action. — [ActionVFX License](https://www.actionvfx.com/license)
- **Creative Commons (Wikimedia Commons, YouTube CC BY, Internet Archive CC items):** Creative Commons' own legal primer says the BY, SA and ND conditions are triggered only when works or adaptations are *publicly shared*, so training generally does not breach CC terms. Attribution applies if you redistribute the dataset. — [CC: Understanding CC Licenses and AI Training (May 2025)](https://creativecommons.org/2025/05/15/understanding-cc-licenses-and-ai-training-a-legal-primer/); [CC: Using CC-licensed works for AI training](https://creativecommons.org/using-cc-licensed-works-for-ai-training-2/)
- **YouTube** has a CC BY license option and search filter. It moved the license from CC BY 3.0 to 4.0 on Aug 1 (year per search excerpt: 2025). Wikimedia Commons has a "YouTube CC-BY" template for imported clips and a curated page of free video sources. — [YouTube Help: License types](https://support.google.com/youtube/answer/2797468?hl=en); [Commons: Template YouTube CC-BY](https://commons.wikimedia.org/wiki/Template:YouTube_CC-BY); [Commons: Free media resources/Video](https://commons.wikimedia.org/wiki/Commons:Free_media_resources/Video/en)

### Inferences
- In practice, every "free" stock site on the list is closed to ML training by default. Pexels, Pixabay and Vecteezy offer a paid or permission route. Envato, Coverr, ProductionCrate and ActionVFX require written consent.
- Pexels and Pixabay both reserve AI use for themselves and "authorized partners," which suggests they license data B2B. Contact Canva/Pexels directly for a data deal.
- CC BY / CC0 content (YouTube CC BY, Wikimedia Commons, Internet Archive) is the only legally open free pool. YouTube's platform Terms of Service still restrict automated downloading (not verified in this session), and CC does not clear the privacy or publicity rights of people shown.

### Gaps
- Exact current AI clauses for Videvo, Videezy, Mazwai, Internet Archive (varies by item) and Mixkit's standalone license page could not be fetched or confirmed.
- Green screen clip counts and resolutions per site were not gathered.
- YouTube Terms of Service wording on downloading and scraping was not checked this session.

## Q2: Paid / commercial stock libraries and their AI training terms

### Takeaway
Standard paid licenses (Shutterstock, Getty/iStock, Adobe Stock, Envato Elements) explicitly **prohibit** AI/ML training. Training rights are sold only through separate data-licensing programs: Shutterstock's data licensing (which includes Pond5 content), Storyblocks Data Licensing, Vecteezy Enterprise, and Getty/iStock "by representative." Pond5's standard AI terms and Artgrid's AI terms are unverified.

### Cited Findings
- **Shutterstock, standard license:** It prohibits using Visual Content "as training data for any artificial intelligence, machine learning, or generative AI system, tool, process, or dataset." AI-feature editing is allowed if the software does not train on the content. — [Shutterstock License](https://www.shutterstock.com/license)
- **Shutterstock, data licensing:** Datasets are built to a customer's model-training needs and may be used only to train ML/computer-vision models. Contributors are paid through a Contributor Fund. — [Shutterstock Data Licensing & Contributor Fund](https://submit.shutterstock.com/help/en/articles/10594694-shutterstock-data-licensing-and-the-contributor-fund)
- **Shutterstock deal history:**
  - In 2023 it signed a six-year training-data agreement with OpenAI covering images, video, music and metadata. — [TechCrunch 2023](https://techcrunch.com/2023/07/11/shutterstock-expands-deal-with-openai-to-build-generative-ai-tools)
  - Buyers named include Meta, Alphabet, Amazon, Apple and NVIDIA. — [AI Business](https://aibusiness.com/generative-ai/shutterstock-embraces-ai-image-licensing-deals); [AI Trace](https://www.aitrace.org/company/shutterstock/practice/a5a5b4bb-653c-4856-8da7-cb99b45ad7bb)
  - The "Data, Distribution, and Services" line reached $203.3M in 2025 (+16% YoY, about 21% of revenue). — [AI Trace summary](https://www.aitrace.org/company/shutterstock/practice/a5a5b4bb-653c-4856-8da7-cb99b45ad7bb) (secondary; verify against 10-K)
  - Oct 7, 2025: AI services for model training and evaluation launched. Mar 19, 2026: major expansion of licensed training datasets. — [Shutterstock IR Oct 2025](https://investor.shutterstock.com/news-releases/news-release-details/shutterstock-builds-data-licensing-strength-new-ai-services); [Shutterstock IR Mar 2026](https://investor.shutterstock.com/news-releases/news-release-details/shutterstock-announces-major-expansion-licensed-training)
- **Getty–Shutterstock merger:** Agreed Jan 6, 2025. The UK CMA required a sale of Shutterstock's editorial business, and Getty's board declined on Jun 30, 2026. The merger agreement was terminated Jul 7, 2026. — [Shutterstock SEC filings 2026](https://www.sec.gov/Archives/edgar/data/0001549346/000154934626000029/sstk-20260630.htm); [Yahoo Finance](https://finance.yahoo.com/markets/stocks/articles/getty-images-gety-shutterstock-merger-105429531.html)
- **Getty Images / iStock:**
  - "Unless expressly authorized… you may not use content (including any caption information, keywords or other metadata…) for any machine learning or artificial intelligence purposes, or for any technologies designed for or intended for the identification of natural persons."
  - "Training" is defined broadly: use "directly or indirectly (for example, by uploading to a third-party AI tool…) to develop, build, improve, fine-tune, optimize, evaluate…" ML/AI.
  - The only carve-outs are internal archiving, search and indexing, and permitted editing. Buyers are told to contact a representative for training needs.
  - Sources: [iStock Content License Agreement](https://www.istockphoto.com/legal/license-agreement); [Getty Images EULA](https://www.gettyimages.com/eula)
- **Getty–OpenAI (June 21, 2026):** A multi-year *display* partnership (Getty content in ChatGPT search). Reports say OpenAI may **not** train on it. — [Getty newsroom](https://newsroom.gettyimages.com/en/getty-images/getty-images-announces-display-partnership-with-openai); [Forbes](https://www.forbes.com/sites/legalentertainment/2026/06/24/gettys-deal-with-openai-leaves-ip-issues-open/)
- **Getty v. Stability AI** (UK High Court decision, Nov 2025) is still relevant to scraping risk. — [Mayer Brown](https://www.mayerbrown.com/en/insights/publications/2025/11/getty-images-v-stability-ai-what-the-high-courts-decision-means-for-rights-holders-and-ai-developers)
- **Adobe Stock:** The Product Specific Terms (Jan 16, 2026 PDF) and enterprise PSLT say you may not use Stock Assets "to directly or indirectly create, train, test, or otherwise improve any machine learning algorithms or artificial intelligence systems, including any architectures, models, or weights." — [Adobe Stock Product Specific Terms 2026-01-16](https://www.adobe.com/cc-shared/assets/pdf/legal/servicetou/stock-product-specific-terms-en-us-20260116.pdf); [PSLT Adobe Stock 2024v1](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-Stock-WW-2024v1.pdf)
- **Adobe as a buyer:** Adobe trains Firefly on Adobe Stock, now including Stock video. In 2024 it paid contributors about $2.62 per minute of video on average, and up to $7.25 per minute, for new footage of people's everyday actions, emotions, hands and feet, and people interacting with objects. — [PetaPixel Apr 2024](https://petapixel.com/2024/04/11/adobe-will-buy-your-videos-for-up-to-7-25-per-minute-to-train-ai-report/); [Adobe Stock Gen AI FAQ](https://helpx.adobe.com/stock/contributor/help/generative-ai-faq.html)
- **Envato Elements** (subscription; Mixkit is the same parent): The Acceptable Use Policy bans training "directly or indirectly." The Envato AI Product Terms bar using AI output "as part of any dataset to train machine learning and/or artificial intelligence technologies." — [Envato AUP](https://help.elements.envato.com/hc/en-us/articles/31035788503321-Acceptable-Use-Policy); [Envato AI Product Terms](https://help.elements.envato.com/hc/en-us/articles/50430113456793-Envato-AI-Product-Terms)
- **Storyblocks:** Runs a separate "Data Licensing for Generative AI Models" program. Its assets and metadata are "fully licensed from their copyright owners" and "cleared for machine learning and generative use cases." The standard subscription is not described as including training rights (not verified). — [Storyblocks Data Licensing](https://www.storyblocks.com/resources/business-solutions/data-licensing)
- **Pond5** (Shutterstock acquired it for $210M, 2022): It bans uploads of AI-generated content. Contributors can opt into "datasets" for AI training in exchange for extra pay. I could not confirm a standard-license ML clause. — [Pond5 Help](https://www.pond5.com/help/en/articles/10086182-does-pond5-allow-ai-generated-content-for-licensing); [Pond5 Content License](https://www.pond5.com/legal/license); [Pond5 Wikipedia](https://en.wikipedia.org/wiki/Pond5)
- **Artgrid:** Its license PDF exists ([Artgrid License Agreement](https://cdn.artgrid.io/footage-images/LicenseAgreement.pdf)), but no AI clause surfaced. **UNVERIFIED.**
- **Dissolve:** Not researched. **UNVERIFIED.**
- **Precedent for green screen matting research:** VideoMatte240K (484 green screen videos: 384 in 4K and 100 in HD; 240,709 frames) was built from clips bought on Storyblocks, Envato Elements and Motion Array. Its dataset license status is questioned in a GitHub issue. Under today's Envato terms, that kind of use would be prohibited. — [Papers with Code VideoMatte240K](https://paperswithcode.com/dataset/videomatte240k); [BackgroundMattingV2 repo](https://github.com/PeterL1n/BackgroundMattingV2); [GitHub issue #208](https://github.com/PeterL1n/BackgroundMattingV2/issues/208)

### Inferences
- A clean route to green screen training data from stock is a *data-licensing* contract (Shutterstock/Pond5, Storyblocks, Vecteezy Enterprise, Getty/iStock custom), not a subscription.
- The academic "buy on Envato/Storyblocks" pattern of 2021 is now contractually barred for Envato. It is likely barred on standard Storyblocks subscriptions too (unverified).

### Gaps
- Pricing for data-licensing deals is not public for Shutterstock, Storyblocks, Getty or Vecteezy.
- Green screen inventory counts on each platform were not gathered.
- Pond5, Artgrid and Dissolve standard-license AI clauses are unverified.

## Q3: Dedicated AI training data vendors (licensed video, including human performance)

### Takeaway
A licensed-video data market now exists: Troveo, Protege (which absorbed Calliope Networks), Wirestock, and Shutterstock/Storyblocks data programs. Reported prices for generic footage are about $1–4 per minute, and scarce categories cost more. None was confirmed to have an off-the-shelf *green screen* catalog. Custom capture briefs appear to be the route.

### Cited Findings
- **Troveo:** More than 8M hours of video and 4M hours of audio from more than 7,000 rights holders. It has paid out more than $20M, and serves the training, fine-tuning and evaluation stages. It says scarce categories (first-person, task demos) price above generic footage. — [Troveo](https://www.troveo.ai/); [Troveo: AI data licensing 2026](https://www.troveo.ai/resources/ai-data-licensing); [Dealroom](https://app.dealroom.co/news/feed/troveo-expands-ai-training-data-platform-to-five-new-categories-pays-out-20m-to-content-owners)
- **Protege** acquired **Calliope Networks**, which aggregates "hundreds of thousands of hours" of TV, film, news and sports content, including 4K and 3D. — [Protege press release](https://withprotege.ai/articles/news/protege-acquires-calliope-networks-unlocking-premium-video-data-for-ai-training); [PR Newswire](https://www.prnewswire.com/news-releases/protege-acquires-calliope-networks-unlocking-premium-video-data-for-ai-training-302335162.html)
- **Market pricing:** AI companies pay about $1–4 per minute for creator footage, with unused or unpublished footage in demand. — [The AI Optimist](https://www.theaioptimist.com/p/the-5m-ai-video-licensing-wave-why); [PetaPixel Jan 2025](https://petapixel.com/2025/01/13/ai-companies-are-paying-content-creators-for-their-unpublished-videos/); [Variety VIP](https://variety.com/vip/creators-are-licensing-content-to-train-ai-video-models-1236336720/)
- **Wirestock:** A marketplace of more than 700K creators that pivoted in 2025–26 to custom datasets (image, video, 3D) for pretraining, SFT and RLHF. Examples include a "Long Video Dataset" of 20,000 continuous human-activity clips and a stock video dataset. Data is from "consenting, paid" creators. — [Wirestock datasets](https://wirestock.io/datasets); [Long Videos](https://wirestock.io/datasets/long-videos); [Stock Videos dataset](https://wirestock.io/datasets/stock-videos)
- **Defined.ai, Datarade:** No green screen-specific offering found. **UNVERIFIED.**

### Inferences
- For green screen humans with clean alpha, commissioning custom capture from Wirestock, Troveo or Adobe-style creator networks is likely the most reliable route. Releases are gathered at capture, which also handles likeness consent.

### Gaps
- Confirmed green screen/chroma inventories at any vendor were not found.
- Per-vendor price sheets were not found.

## Q4: Model releases, likeness and biometric law (BIPA, GDPR)

### Takeaway
Stock model releases were written for advertising and editorial use, not for biometric or ML processing. Getty/iStock and Canva explicitly exclude person-identification uses. Training on faces or bodies creates BIPA exposure (US$1,000–5,000 per violation, counted per scan) and GDPR special-category exposure unless consent is collected specifically for training.

### Cited Findings
- Getty/iStock bars use of content for "technologies designed for or intended for the identification of natural persons." — [iStock License](https://www.istockphoto.com/legal/license-agreement)
- Canva (Pexels/Pixabay parent) prohibits ML/AI use "for identification of natural persons." — [Canva Content License](https://www.canva.com/policies/content-license-agreement/)
- **BIPA:**
  - It allows $1,000–$5,000 per violation, and each facial scan can be a separate violation.
  - The IBM "Diversity in Faces" suit (99M images) and the Clearview rulings show that publicly posted images are not consent, and that platform terms of service do not shield the trainer.
  - Sources: [Perkins Coie](https://perkinscoie.com/insights/update/new-biometrics-lawsuits-signal-potential-legal-risks-ai); [Financier Worldwide](https://www.financierworldwide.com/legal-risks-arising-from-the-use-of-biometric-data-and-ai); [DEV Community (secondary)](https://dev.to/tiamatenity/bipa-and-the-650m-wake-up-call-how-biometric-ai-is-exposing-companies-to-existential-litigation-b1o)
- GDPR treats biometric data as a special category that needs a lawful basis and a DPIA. — [Surveillant.ai guide (secondary)](https://surveillant.ai/guides/ai-video-surveillance-privacy-laws)

### Inferences
- A matting or segmentation model that does not extract face templates may fall outside "biometric identifier" definitions. That is untested, so budget for releases that explicitly cover AI training. Adobe's and Wirestock's creator-commissioned models suggest the industry norm is fresh, training-specific consent.

### Gaps
- No source found on whether standard stock model releases (Getty, Shutterstock) are being updated to cover AI training of third parties.
- There is no case law on matting/segmentation, as distinct from identification, under BIPA.

## Q5: Bulk download / API availability

### Takeaway
The free-site APIs (Pexels, Pixabay) exist but are contractually barred from at-scale ML collection. The paid "data licensing" channels (Shutterstock, Storyblocks, Troveo, Wirestock) are the ones built to deliver in bulk.

### Cited Findings
- **Pexels API:** Free, but not for collecting content at scale for ML without permission. — [Pexels API](https://www.pexels.com/api/); [Pexels AI and ML FAQ](https://help.pexels.com/hc/en-us/articles/27292485713945-AI-and-ML-FAQ)
- **Pixabay:** "Bulk, large-scale or systematic copying" is prohibited without permission. Third-party Apify scrapers exist but would breach the terms. — [Pixabay Terms](https://pixabay.com/service/terms/); [Apify Pixabay scraper](https://apify.com/shahidirfan/pixabay-image-scraper/api)
- **Shutterstock:** Delivers custom datasets with metadata to model builders. — [Shutterstock IR Mar 2026](https://investor.shutterstock.com/news-releases/news-release-details/shutterstock-announces-major-expansion-licensed-training)
- **Troveo:** Offers deal structures of flat license, per-hour or per-asset pricing, annual refresh, or revenue share. — [Troveo AI data licensing](https://www.troveo.ai/resources/ai-data-licensing)

### Inferences
- Bulk green screen training data is realistically available only through negotiated data licenses or open CC corpora.

### Gaps
- Rate limits and API terms for Storyblocks, Vecteezy and Adobe Stock APIs were not checked.
