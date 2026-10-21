# Prompt 2: Defect Detection and Classification

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Text-Based Model (block 3) |
| **Paper section** | Sec. 2.2.2 Generation |

## Purpose
Decides, one defect type at a time, whether the defect is present, based only on the textual visual analysis from Prompt 1 and a defect definition retrieved from the provider information by KAG.

## Inputs
`{visual_analysis}`: output of Prompt 1; `{defect_name}`, `{defect_def}`: defect name and its KAG-retrieved definition.

## Prompt
> You are an expert in FFF 3D printing quality inspection. VISUAL ANALYSIS OF THE PRINT: {visual_analysis}. DEFECT DEFINITION - "{defect_name}": {defect_def}. TASK: Based SOLELY on the visual analysis above, determine if this print exhibits signs of "{defect_name}". Provide your response in this EXACT format: DETECTED: [Yes/No], REASONING: [Brief explanation of your decision]. Guidelines: DETECTED: "Yes" if defect is clearly present, "No" if not present. REASONING: 1-2 sentences explaining key evidence from the analysis. Be decisive - choose Yes or No based on the evidence.
