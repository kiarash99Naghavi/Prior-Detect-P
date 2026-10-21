# Prompt 1: Multi-Model Description Generation

| | |
|---|---|
| **Model** | GPT-5-mini |
| **Where it is used** | Text-Based Model (block 1) and Transformer-VAE Model (blocks 6 and 8) |
| **Paper section** | Sec. 2.2.2 Generation; Sec. 2.4; Sec. 2.4.2 |

## Purpose
Turns a 3D-print image into a short textual description of visible characteristics only (no inferred causes). Used to describe FFF evaluation images (block 1), and, run through nine different MLLMs, to describe provider defect images for Transformer-VAE training data (block 6). The same prompt describes evaluation images before fragmentation (block 8).

## Inputs
An image (sent with the prompt).

## Prompt
> Look at this 3D print sample and describe ONLY the visible characteristics you observe. Focus on what IS present, not what's missing. Consider: filament organization, layer formation, surface appearance, material distribution, and structural form. Be specific about what you see without inferring causes. Response must be under 500 characters, single paragraph, no lists or numbering. Examples: (1) Material forms organized horizontal bands with consistent spacing and uniform width across the structure. Surface displays regular striations with smooth transitions between adjacent paths. (2) Filament appears as loose unconnected strands curving randomly through space without forming coherent layers or adhering to neighboring material. (3) Visible layers show pronounced upward curl at edges with base material lifting from initial position while central regions maintain their intended geometry. (4) Parallel extrusion paths visible but material appears sparse with gaps between adjacent lines creating incomplete surface coverage and mesh-like appearance. (5) Dense material accumulation with overlapping extrusion paths creating raised ridges and loss of detail definition throughout the structure.
