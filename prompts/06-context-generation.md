# Prompt 6: Context Generation

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Image retrieval (block 4), Stage A-4 |
| **Paper section** | Sec. 2.3.1; Fig. 4 |

## Purpose
Generates detailed context for the image (caption, surrounding text, scientific context) from the top-k pages returned by ColPali.

## Inputs
Screenshots of the retrieved PDF pages and the image.

## Prompt
> We have the provided document screenshots. Now, for the image shown below, identify where it appears in the document text and explain all the information related to it. Also include the caption of the corresponding image. Use only the information visible in the retrieved images. Only explain the image if it appears in the documents.
