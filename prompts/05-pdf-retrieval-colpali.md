# Prompt 5: PDF Retrieval System

| | |
|---|---|
| **Model** | ColPali |
| **Where it is used** | Image retrieval (block 4), Stage A-3 |
| **Paper section** | Sec. 2.3.1; Fig. 4 |

## Purpose
Query used with the ColPali vision-based retrieval framework to locate the PDF pages that contain the figure. It combines the Stage A-1 visual description with a page-number hint taken from the image filename.

## Inputs
`[visual description]`: output of Prompt 3; `[page number]`: hint from the extraction stage.

## Prompt
> You are an expert assistant specialising in analysing complex PDF pages and attached images. Carefully read the retrieved pages and any extra image. Ground the answer strictly in the retrieved content. Find the figure with these visual characteristics: [visual description]. It is shown on page [page number] of the document.
