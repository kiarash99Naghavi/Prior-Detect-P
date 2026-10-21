# Prior-Detect: Prompts

This repository contains the full prompts used by the Foundation Models in **Prior-Detect**, a zero-shot framework for image-based defect classification in manufacturing under site-to-site concept drift.

> K. Naghavi Khanghah, A. Patel, Q. Yang, R. Malhotra, H. Xu. *Prior-Detect: Zero-Shot Expertise-Agnostic Process Monitoring Under Site-to-Site Concept Drift.* Submitted to the 55th SME North American Manufacturing Research Conference (NAMRC 55), Manufacturing Letters. *Under review.*

The conference paper had no room for the prompt tables, so all of them are collected here. Each prompt is in its own Markdown file in [`prompts/`](prompts/).

## What Prior-Detect does

Prior-Detect classifies defects in images from a local *evaluation site*. It uses no labeled training data from that site. Instead, it mines small amounts of unstructured, defect-related information from other *provider sites*; in the paper, this is the scientific literature on Fused Filament Fabrication (FFF). Three independent pipelines make predictions, and majority voting combines them:

- **Text-Based Model:** an LLM compares textual descriptions of evaluation images with defect characteristics retrieved from the provider information by Knowledge Augmented Generation (KAG).
- **Image-Based Model:** a multi-stage pipeline extracts single-defect reference images from the provider PDFs, and an MLLM compares them with each evaluation image.
- **Transformer-VAE Model:** a Transformer-VAE classifier is trained on MLLM-generated descriptions of the provider defect images. It then classifies fragments of the evaluation-image descriptions.
- **Ensemble Decision Fusion:** a defect is predicted when at least two of the three models detect it.

Target defect classes: over extrusion, under extrusion, warping and spaghetti.

## Repository structure

```
Prior-Detect-P/
├── README.md
└── prompts/
    ├── 01-multi-model-description-generation.md
    ├── 02-defect-detection-and-classification.md
    ├── 03-visual-description.md
    ├── 04-initial-filtering.md
    ├── 05-pdf-retrieval-colpali.md
    ├── 06-context-generation.md
    ├── 07-defect-specific-filtering.md
    ├── 08-dataset-defect-classification.md
    ├── 09-spatial-reasoning.md
    ├── 10-image-based-defect-detection.md
    └── 11-fragmentation-and-filtering.md
```

Each file gives the model, where the prompt is used in the pipeline (block numbers refer to Fig. 3 and stage labels to Fig. 4 of the paper), its purpose, its inputs, and the prompt text.

## Prompts at a glance

| # | Prompt | Model | Pipeline | Where (paper) |
|---|---|---|---|---|
| 1 | [Multi-Model Description Generation](prompts/01-multi-model-description-generation.md) | GPT-5-mini (and nine MLLMs for block 6) | Text-Based, Transformer-VAE | Blocks 1, 6, 8 |
| 2 | [Defect Detection and Classification](prompts/02-defect-detection-and-classification.md) | GPT-5-mini | Text-Based | Block 3 |
| 3 | [Visual Description](prompts/03-visual-description.md) | Qwen2.5-VL-32B-Instruct | Image-Based, image retrieval | Block 4, Stage A-1 |
| 4 | [Initial Filtering](prompts/04-initial-filtering.md) | GPT-4o-mini | Image-Based, image retrieval | Block 4, Stage A-2 |
| 5 | [PDF Retrieval System](prompts/05-pdf-retrieval-colpali.md) | ColPali | Image-Based, image retrieval | Block 4, Stage A-3 |
| 6 | [Context Generation](prompts/06-context-generation.md) | GPT-5-mini | Image-Based, image retrieval | Block 4, Stage A-4 |
| 7 | [Defect-Specific Filtering](prompts/07-defect-specific-filtering.md) | GPT-4o-mini | Image-Based, image retrieval | Block 4, Stage A-5 |
| 8 | [Dataset Defect Classification](prompts/08-dataset-defect-classification.md) | GPT-5-mini | Image-Based, image retrieval | Block 4, Stage B-1 |
| 9 | [Spatial Reasoning](prompts/09-spatial-reasoning.md) | GPT-5-mini | Image-Based, image retrieval | Block 4, Stage B-3 |
| 10 | [Image-Based Defect Detection](prompts/10-image-based-defect-detection.md) | GPT-5-mini | Image-Based | Block 5 |
| 11 | [Fragmentation and Filtering](prompts/11-fragmentation-and-filtering.md) | GPT-5-mini | Transformer-VAE | Block 8 |

## Notes

- **Placeholders.** Text in `{curly}` or `[square]` brackets is filled in at run time, for example `{visual_analysis}`, `[defect type]` or `[6 reference images]`. Images are sent as separate inputs alongside the prompt.
- **Prompts 3–7** are given in the summarized form used in the journal version of the paper. Prompts 1, 2 and 8–11 are given in full.
- **Stage B-2** (boundary-based image segmentation) has no prompt. It is implemented with adaptive thresholding, morphological closing and connected-component analysis in OpenCV.
- **The KAG step** (block 2) uses GPT-4o-mini to build the knowledge graph from the provider documents (semantic chunking, then entity and relation extraction).

## Citation

If you use these prompts, please cite the paper above.
