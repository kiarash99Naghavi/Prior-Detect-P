# Prompt 8: Dataset Defect Classification

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Image retrieval (block 4), Stage B-1 |
| **Paper section** | Fig. 4 |

## Purpose
Assigns each filtered image to one or more defect categories (over extrusion, under extrusion, warping, spaghetti), answering Yes only when the defect is explicitly and visibly shown.

## Inputs
`[description]`: contextual description from Stage A-4.

## Prompt
> You are verifying the VISUAL presence of a specific additive-manufacturing defect. Description of the figure: [description]. Decision rule — answer Yes ONLY if ALL are true: 1) The description explicitly names the defect as shown in an image, and 2) It states or clearly implies the defect sample is visible in that image, and 3) There is no negation. Answer No if content is only charts/design rules, visibility is ambiguous, or figures are only tables, bar charts, line plots, or text summaries. Respond strictly with Yes or No.
