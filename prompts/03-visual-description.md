# Prompt 3: Visual Description

| | |
|---|---|
| **Model** | Qwen2.5-VL-32B |
| **Where it is used** | Image-Based Model, image retrieval (block 4), Stage A-1 |
| **Paper section** | Sec. 2.3.1 Retrieval; Fig. 4 |

## Purpose
Writes a dense, search-friendly visual description of each image extracted from the provider PDFs.

## Inputs
An extracted image.

## Prompt
> Describe everything visible in this figure: state the figure title (or panel labels), count of sub-plots, each axis label with units, legend items, marker/line colours, and the principal trend or conclusion. Use dense technical nouns only—no pronouns or filler—so the sentence can be pasted verbatim into a PDF search tool or VLM to locate the exact matching image.
