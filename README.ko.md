# 우리 고양이를 아무 영상에나 넣기 (ComfyUI + MiniMax H3)

[English](README.md)

영상 속 고양이를 우리 집 고양이로 바꾸는 방법입니다. 코딩 없이 Claude에게 말로 요청해서 만들었고, 그 과정에서 쓴 워크플로와 요청문을 그대로 올려 둡니다.

- 강좌 영상: https://youtu.be/dXoand05TnI
- 제 노트북: RTX 4060 노트북 GPU (VRAM 8GB), RAM 32GB. 7초 영상 1번에 약 1시간.

## 들어 있는 것

| 파일 | 하는 일 |
|---|---|
| `workflows/01_swap_basic_api.json` | 기본 스왑. 영상 속 고양이를 참조 시트의 고양이로 바꿉니다. |
| `workflows/02_sam3_masks_api.json` | (고급) 여러 마리 중 바꿀 고양이와 그대로 둘 고양이의 마스크 영상을 만듭니다. |
| `workflows/03_one_cat_masked_edit_api.json` | (고급) 마스크 안의 고양이만 바꿉니다. h3-relay 노드가 필요합니다. |
| `workflows/04_seedvr2_7b_upscale_api.json` | (선택) SeedVR2 7B로 1080×1920 업스케일. |
| `prompts/claude_requests.ko.md` | 단계별로 Claude에게 한 요청문. |
| `prompts/prompt_template.ko.md` | 대괄호만 바꿔 쓰는 프롬프트 틀. |
| `docs/install.ko.md` | 설치와 재료 준비. |
| `docs/models.ko.md` | 사용 모델 (공식 파일 기준). |

## 순서

1. `docs/install.ko.md`대로 ComfyUI Desktop과 Claude Code를 설치하고, `docs/models.ko.md`의 모델을 받습니다.
2. ComfyUI `input` 폴더에 넣습니다.
   - `my_cat_reference_sheet.png`: 우리 고양이 참조 시트
   - `input_video.mp4`: 바꿀 영상
3. 워크플로 json을 ComfyUI 화면에 끌어다 놓습니다.
4. 프롬프트의 고양이 설명을 `prompts/prompt_template.ko.md`를 보고 우리 고양이에 맞게 고칩니다.
5. 먼저 짧게(22~56프레임) 시험하고, 괜찮으면 전체를 만듭니다.

막히면 `prompts/claude_requests.ko.md`의 요청문을 Claude에게 그대로 말하면 됩니다.

## 필요한 노드 팩

- 모든 워크플로: [ComfyUI-VideoHelperSuite](https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite) (영상 불러오기)
- 03번만: [h3-relay](https://github.com/akatz-ai/h3-relay) (MiniMax H3 마스크 편집 노드)
- 나머지는 모두 ComfyUI 기본 노드입니다. SAM3와 SeedVR2도 기본 노드로 돌아갑니다.

## 알아 둘 점

- 워크플로의 모델 이름과 스텝 수(20)는 **공식 파일 기준**입니다. 저는 VRAM 8GB에 맞춘 가벼운 8스텝 합본 모델로 만들었기 때문에, 강좌의 시간(7초 약 1시간)은 그 기준입니다. 공식 파일은 더 오래 걸릴 수 있습니다.
- 생성 길이는 17의 배수 + 5 프레임(22, 39, 56, 90, 124, 158, 175)으로 맞춥니다.
- 03번의 입력 영상 3개(`crop_source.mp4`, `crop_mask.mp4`, `crop_reference_gray.mp4`)는 02번 마스크로 바꿀 고양이 주변을 잘라 만든 것입니다. 이 준비 단계는 Claude에게 "02번 마스크로 바꿀 고양이만 화면 가득 잘라서, 03번 워크플로 입력 3개를 만들어 줘"라고 요청해서 만들었습니다.
- 입력 영상은 직접 찍었거나 사용해도 되는 영상을 쓰세요. 강좌의 데모 영상은 이 저장소에 들어 있지 않습니다.
- 모델 파일은 여기 없습니다. 각 모델의 공식 페이지에서 받으세요.

이 저장소는 개인 튜토리얼이며 Anthropic, Comfy, MiniMax와 관련이 없습니다.

## 라이선스

MIT. 모델, 노드 팩, 영상은 각자의 라이선스를 따릅니다.
