# Prompt 4: Initial Filtering

| | |
|---|---|
| **Model** | GPT-4o-mini |
| **Where it is used** | Image retrieval (block 4), Stage A-2 |
| **Paper section** | Sec. 2.3.1; Fig. 4 |

## Purpose
Removes non-informative images (logos, cover pages, blank figures, placeholders) using the Stage A-1 description.

## Inputs
`[Visual description]`: output of Prompt 3.

## Prompt
> You are verifying whether a visual figure description refers to informative scientific content. Inputs: [Visual description]. If the description mentions "logo", "cover", "blank", or "placeholder", classify as: Relation: "Mismatch", Category: "Blank/Placeholder". Otherwise classify as: Relation: "Match", Category: "Full Match". Output only JSON format with Relation, Category, and Explanation fields.
