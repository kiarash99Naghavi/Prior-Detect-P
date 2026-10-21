# Prompt 11: Fragmentation and filtering pipeline

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Transformer-VAE Model (block 8) |
| **Paper section** | Sec. 2.4.2 |

## Purpose
Splits an evaluation-image description into self-contained fragments, one per distinct defect or problem, and drops descriptions of normal characteristics. Each fragment is then embedded and classified by the Transformer-VAE (block 9).

## Inputs
A textual description of an evaluation image (output of Prompt 1).

## Prompt
> Analyze the following 3D print description and split it into separate fragments, where each fragment describes a DISTINCT DEFECT or PROBLEM characteristic. Include a defect only if it is clearly explained, repeatedly emphasized, or supported by concrete evidence. Rules: (1) Each fragment should describe ONE specific defect or problem - Do not include structure description if it is not a problem or defect. (2) Do not return descriptions of normal/good characteristics together as one fragment (remove them). (3) Return ONLY a JSON array of strings, nothing else. (4) Each string should be a complete, self-contained description. (5) If the entire text describes only normal characteristics with no defects, return it as a single fragment. Return format (JSON array only): ["fragment 1 text here", "fragment 2 text here", ...]
