# Put Your Own Cat Into Any Video (ComfyUI + MiniMax H3)

[한국어](README.ko.md)

How I replaced a cat in a video with my own Maine Coon. No coding: I just asked Claude, step by step. These are the workflows and the requests I actually used.

- Video tutorial: https://youtu.be/qt0n4wPLDhE
- My laptop: RTX 4060 Laptop GPU (8GB VRAM), 32GB RAM. One 7-second render takes about an hour.

## What's inside

| File | What it does |
|---|---|
| `workflows/01_swap_basic_api.json` | Basic swap: replaces the cat in the video with the cat in your reference sheet. |
| `workflows/02_sam3_masks_api.json` | (Advanced) With several cats, makes mask videos for the cat to change and the cat to keep. |
| `workflows/03_one_cat_masked_edit_api.json` | (Advanced) Changes only the cat inside the mask. Needs the h3-relay nodes. |
| `workflows/04_seedvr2_7b_upscale_api.json` | (Optional) Upscales to 1080×1920 with SeedVR2 7B. |
| `examples/my_cat_reference_sheet.png` | Sample reference sheet (my cat, real photos). |
| `examples/input_video.mp4` | Sample input video (21 s, 544×960, no sound): my final swap result. |
| `prompts/claude_requests.en.md` | The requests I gave Claude, step by step. |
| `prompts/prompt_template.en.md` | Prompt template: just fill in the brackets. |
| `docs/install.en.md` | Installation and what to prepare. |
| `docs/models.en.md` | Models (official files). |

## Steps

1. Install ComfyUI Desktop and Claude Code (`docs/install.en.md`) and download the models (`docs/models.en.md`).
2. Put these in ComfyUI's `input` folder:
   - `my_cat_reference_sheet.png`: your cat's reference sheet
   - `input_video.mp4`: the video to change
   - To try it right away, copy the two files from `examples/`. Workflow 01 then swaps the long-haired cat in front (first 158 frames) for the cat in the sheet. Put your own cat's sheet in to see it change.
3. Drag a workflow json onto the ComfyUI canvas.
4. Rewrite the cat description in the prompt for your cat (see `prompts/prompt_template.en.md`).
5. Test a short clip first (22–56 frames), then render the full length.

Stuck? Say the requests in `prompts/claude_requests.en.md` to Claude as they are.

## Node packs

- All workflows: [ComfyUI-VideoHelperSuite](https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite) (video loading)
- Workflow 03 only: [h3-relay](https://github.com/akatz-ai/h3-relay) (MiniMax H3 masked edit)
- Everything else is core ComfyUI, including SAM3 and SeedVR2.

## Notes

- Model names and the step count (20) in the workflows follow the **official files**. I rendered with a lighter 8-step merged model that fits 8GB VRAM, so the times above are for that setup; the official files may take longer.
- Use lengths of 17×n + 5 frames (22, 39, 56, 90, 124, 158, 175).
- The three inputs of workflow 03 (`crop_source.mp4`, `crop_mask.mp4`, `crop_reference_gray.mp4`) are crops around the target cat, made from the 02 masks. I made them by asking Claude: "Using the 02 masks, crop so the cat to change fills the frame, and make the three inputs for workflow 03."
- Use a video you filmed or are allowed to use. The demo video from the tutorial is not included.
- Model files are not included. Download them from each model's official page.

This is an independent tutorial and is not affiliated with Anthropic, Comfy, or MiniMax.

## License

MIT. Models, node packs and videos keep their own licenses.
