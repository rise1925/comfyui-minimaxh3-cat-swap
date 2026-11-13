# What I asked Claude

Change only the parts in [brackets]. I connected Claude Code to ComfyUI (MiniMax H3 + swap LoRA).
When Claude asks to download a model or install a node, you approve it or run the command yourself.

## Setup
- "On my computer (graphics card [RTX 4060, 8GB VRAM]), I want to replace the cat in a video with my cat using MiniMax H3 and the swap LoRA in ComfyUI. Check that all needed models are there and tell me what's missing."

## Step 1 · Reference photos
- "My cat's photos are in [folder]. Make a reference sheet from them. Use only the real photos, and show the front of the face, the profile and the full body."
- Your job: collect photos / check that no other cat's face slipped into the sheet.

## Step 2 · Input video
- "In this video, I want to replace [the cream cat dancing in the back] with my cat. First check whether the video can be used as is."
- If a person performed it: "Make an input video with the person's body painted in fur color."
- Your job: pick the video / say exactly which cat to change.

## Step 3 · Prompt
- "Look at the reference sheet and write a prompt describing the face, eyes, fur color and ears part by part. Keep the original movements and mouth shapes."
- After a result: "The eyes are bigger and brighter than my cat's. There's an orange mark on the muzzle, but the real one is white."
- Your job: say specifically how the result differs from your cat.

## Step 4 · Generate
- "First make a 1-second test and show it side by side with the original. Keep the seed fixed and change only one thing at a time."
- "If it looks good, render the whole thing. Make a status page so I can check progress on my phone."
- Your job: watch the comparison and decide what to change next.

## Step 5 · Advanced · Only one of several cats
- "Keep the front cat as it is and change only the cream cat in the back."
- "If I fix it by hand every time, nobody else can use this. Find a fundamental fix that other people can use the same way."
- Your job: run/approve node installs yourself / point out edges and ghosting.

## Step 6 · Optional · Upscaling
- "Upscale to 1080p with SeedVR2. Do 2 seconds first and compare it side by side with a simple resize."
- "I see some wobbling. Can you reduce it?"
- Your job: approve the download / judge at normal size whether it's worth it.

## When it doesn't work
- "The result still has [human hands]. List possible causes and check them one by one with short tests."
- If three prompt rewrites don't fix it: "Instead of the prompt, find a way to fix the reference photos or the input video."
