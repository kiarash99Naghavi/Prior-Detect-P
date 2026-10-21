# Prompt 9: Spatial Reasoning

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Image retrieval (block 4), Stage B-3 |
| **Paper section** | Fig. 4 |

## Purpose
After boundary-based segmentation (Stage B-2), selects which numbered regions of a multi-panel figure contain the defect, so only single-defect reference images are kept.

## Inputs
The segmented image with numbered green rectangles; `[type]`, `[description]`: defect type and description.

## Prompt
> You are a quality control expert analyzing a segmented 3D printed object image for defects. IMAGE CONTEXT: The image shows a 3D printed object divided into numbered rectangular regions (outlined in green). Each rectangle has a visible number label. Some rectangles may be nested inside larger rectangles. DEFECT INFORMATION: Defect Type: [type]. Defect Description: [description]. CRITICAL ANALYSIS RULES: 1) ONLY select rectangles if the defect description EXPLICITLY mentions their specific location (e.g., "middle row", "top left", "bottom section"), their number (e.g., "region 3", "area 5"), or unique visual characteristics that clearly identify them. 2) BE CONSERVATIVE: If the description is vague or general, return NONE. If you're uncertain whether a region matches, DO NOT select it. Only select regions you are HIGHLY CONFIDENT contain the described defect. 3) LOCATION MATCHING: If description says "middle row" → select ALL boxes in the middle row. If description says "top corner" → select ONLY the corner box. If description says "throughout" or "entire surface" → return NONE (too vague). 4) NESTED RECTANGLES: If a smaller rectangle is completely inside a larger one, select ONLY the smaller one. Never select both nested rectangles. 5) EVIDENCE REQUIREMENT: There MUST be specific evidence in the description pointing to particular regions. Generic descriptions like "visible defect" or "quality issue" → return NONE. If no location, number, or specific characteristic is mentioned → return NONE. OUTPUT: Return ONLY the rectangle numbers that DEFINITELY match the description. Format: comma-separated numbers (e.g., 2,5,7). If no clear match or description is vague: NONE.
