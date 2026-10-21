# Prompt 7: Defect-Specific Filtering

| | |
|---|---|
| **Model** | GPT-4o-mini |
| **Where it is used** | Image retrieval (block 4), Stage A-5 |
| **Paper section** | Sec. 2.3.1; Fig. 4 |

## Purpose
Keeps only images whose combined visual description and generated context show one of the target FFF defects.

## Inputs
`[Generated Context]`: output of Prompt 6, together with the visual content.

## Prompt
> You are verifying whether visual content and text refer to the same scientific concept. Inputs: [Generated Context]. If the visual content is unrelated decorative/non-technical graphics (logos, padlocks, UI symbols) and not a scientific defect figure, classify as "Mismatch" with Category "Blank/Placeholder". If either description does not mention defects (Over Extrusion, Under Extrusion, Warped, Spaghetti), classify as "Mismatch". Otherwise classify as "Match" with Category "Full Match". Output JSON format.
