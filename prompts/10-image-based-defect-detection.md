# Prompt 10: Image-Based Defect Detection

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Image-Based Model (block 5) |
| **Paper section** | Sec. 2.3.2 Generation |

## Purpose
Few-shot visual comparison: six randomly sampled provider reference images of a defect are shown with the evaluation image, and the MLLM answers yes or no. Repeated in five runs; a defect is declared present if at least four runs say yes.

## Inputs
`[defect type]`; `[6 reference images]` from the Provider Dataset; `[test image]` from the evaluation site.

## Prompt
> These 6 images show examples of '[defect type]' (The defect is present in these images but there might be some samples that are incorrect so look at the general trend between all 6 images and choose that): [6 reference images]. Does '[defect type]' exist in this test image? Answer only 'yes' or 'no'. [test image]
