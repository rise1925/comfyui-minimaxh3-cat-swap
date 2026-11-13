# Installation and what to prepare

## Computer
- NVIDIA graphics card with 8GB VRAM or more (mine: RTX 4060 Laptop, 8GB VRAM)
- 32GB RAM, 50GB+ free disk space

## 1. ComfyUI Desktop
- Download the desktop app from comfy.org and install it (GPU: NVIDIA).
- Swap LoRA: https://huggingface.co/akatz-ai/MiniMax-H3-Character-Swap-LoRA
- MiniMax H3 official models: https://huggingface.co/Comfy-Org/MiniMax-H3 (see `models.en.md`)

## 2. Claude Code
- Install it on the same computer and sign in with a paid Claude plan.

## 3. Connect them
- Register the ComfyUI connector (comfy-mcp) in Claude Code.
- Ask Claude: "Set things up so you can connect to my ComfyUI (127.0.0.1:8188) and work with it." It will tell you the commands.
- Run or approve install commands yourself.

## 4. Missing nodes
- If a workflow shows red nodes: ComfyUI Manager → Install Missing Custom Nodes.
- Needed: ComfyUI-VideoHelperSuite; for workflow 03 also h3-relay.

## 5. First request after connecting
"I want to do a MiniMax H3 character swap in my ComfyUI. Check that all needed nodes and models are installed, and tell me how to install anything missing."

## Folders (inside ComfyUI)
- `input/`: the video to change (mp4), your cat's reference sheet
- `models/`: diffusion_models / text_encoders / vae / loras / checkpoints
- `output/`: results appear here

## Choosing the video
- One you filmed or are allowed to use
- 5–10 seconds, one continuous shot
- A video performed by a cat is the easiest
- If it isn't 24fps, ask Claude to convert it

## Your cat's photos
- 10–20 photos in good light
- Front face, profile, full body, fur colors clearly visible
- Unedited originals, no filters
- Before sharing photos anywhere, remove location data (EXIF/GPS)
