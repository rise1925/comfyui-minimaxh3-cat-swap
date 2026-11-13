# Models (official files)

## MiniMax H3 — https://huggingface.co/Comfy-Org/MiniMax-H3
| File | Folder |
|---|---|
| `minimax_h3_ref2va_pruned_int8_convrot.safetensors` (video model) | `models/diffusion_models` |
| `qwen3vl_32b_minimax_h3_nvfp4_awq.safetensors` (text encoder) | `models/text_encoders` |
| `minimax_h3_video_vae_int8_convrot.safetensors` (VAE) | `models/vae` |
| (optional) `minimax_h3_ref2v_turbo_4step_v0.1_comfyui_bf16.safetensors` (4-step turbo LoRA) | `models/loras` |

## Character swap LoRA — https://huggingface.co/akatz-ai/MiniMax-H3-Character-Swap-LoRA
- `h3_character_swap_pro4500_1000.safetensors` (V1) or `h3_character_swap_v1.5.safetensors` → `models/loras`
- In my comparison, V1 and V1.5 swapped equally well. Workflow 01 uses V1, workflow 03 uses V1.5.

## Settings
- Sampler res_multistep, scheduler simple, LoRA strength 1.0
- Official default 20 steps (4 with the turbo LoRA)
- Keep one fixed seed
- For comparison, er_sde + sigma shift 12 put stripes in the fur

## One cat out of several (advanced) — workflows 02, 03
- SAM3: `sam3.1_multiplex_fp16.safetensors` → `models/checkpoints` (https://huggingface.co/Comfy-Org/sam3.1)
- Custom nodes: [h3-relay](https://github.com/akatz-ai/h3-relay) (redraws only inside the mask)

## Upscaling (optional) — workflow 04, core nodes
- `seedvr2_7b_int8_convrot.safetensors` → `models/diffusion_models` (https://huggingface.co/Comfy-Org/SeedVR2)
- `seedvr2_ema_vae_fp16.safetensors` → `models/vae`
- On 8GB VRAM, about 9 minutes per 49 frames. For long videos, split into segments (workflow 04 loads 93 frames).

## What I actually ran on my laptop
- A lighter 8-step merged video model and a GGUF text encoder sized for 8GB VRAM.
- The times in the tutorial (7 s ≈ 70 min, 1 s test 7–15 min) are for that setup. The official 20-step files may take longer.
- If the official files are too slow or run out of memory on 8GB, ask Claude: "Find a lighter version that runs on 8GB VRAM."
