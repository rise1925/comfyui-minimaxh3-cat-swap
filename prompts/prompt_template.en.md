# Prompt template (MiniMax H3 + swap LoRA)

Replace only the [brackets] to match your cat. `<Picture 1>` = your reference sheet (real photos of your cat), `<Video 1>` = the video to change.

```text
A single continuous uninterrupted take. <Picture 1> shows one real [Maine Coon] cat from several angles and poses; every face in <Picture 1> belongs to this same cat.
The cat's face matches <Picture 1> exactly: [eyes: small, dark gray-brown eyes with heavy, half-closed upper lids]; [forehead & nose: a narrow white blaze running from the forehead down to a small pink nose]; [muzzle: a plain, pure white muzzle and chin]; [ears: large, wide ears with pink insides and long white ear tufts].
Its coat is [color & markings: mostly pure white, with soft patches of pale ginger-gold on the top of its head, around its ears, and on the upper sides of its back]. Its fur is [length: very long, silky, and wispy].
The [target: cream-colored cat closest to the camera] in <Video 1> is replaced by this cat from <Picture 1>. It keeps exactly the same body, size, position in the frame, pose, and every movement of the [target] in <Video 1>, but it has the face, eyes, fur colors, and markings of <Picture 1>.
Its two front paws perform every gesture of the [target] in <Video 1>, [moves: including raising a paw and holding the sides of its head].
Its jaw opens as wide as the [target]'s mouth in <Video 1> in every frame, with the same opening, timing, and shape.
The [keep as is: black-and-white cat standing farther back, the wooden fence, the plants, the ground, and the lighting] stay exactly as they are in <Video 1> from the first frame to the last.
Follow the camera movement, framing, timing, and body movements of <Video 1> exactly.
```

## Tips
- Describe the face (eyes, forehead, muzzle, ears), fur color and fur length separately. "Change it to my cat" alone only changes the face.
- Always mention the parts that move in the original, like the front paws and the mouth.
- List what must stay unchanged (other animals, background, lighting) at the end.
- For a video performed by a person, painting the input in fur color works much better than writing "cat" instead of "man".
- If three rewrites don't help, fix the reference sheet or the input video instead of the prompt.

## Settings I used
- Sampler res_multistep, scheduler simple, LoRA strength 1.0, fixed seed (official default 20 steps; I used a lighter 8-step model for 8GB VRAM)
- Length: 17×n + 5 frames (22, 39, 56, 90, 124, 158, 175)
- Test with 22–56 frames; render the full length once at the end
