# 설치와 재료 준비

```text
[처음 한 번만] 설치와 재료 준비

필요한 컴퓨터
- NVIDIA 그래픽카드 8GB 이상 (제 것은 RTX 4060 노트북 8GB)
- 메모리 32GB, 디스크 여유 50GB 이상

1. ComfyUI 데스크톱 설치
   - comfy.org 에서 데스크톱 앱을 받아 설치 (그래픽카드: NVIDIA)
   - 템플릿에서 MiniMax H3 워크플로를 열어 둔다
   - 스왑 LoRA 안내: https://huggingface.co/akatz-ai/MiniMax-H3-Character-Swap-LoRA
   - MiniMax H3 공식 모델: https://huggingface.co/Comfy-Org/MiniMax-H3
     영상 minimax_h3_ref2va_pruned_int8_convrot / 텍스트 인코더 qwen3vl_32b_minimax_h3_nvfp4_awq / VAE minimax_h3_video_vae_int8_convrot
   - 8GB에서 느리면 Claude에게 가벼운 버전을 찾아 달라고 요청

2. Claude Code 설치
   - ComfyUI와 같은 컴퓨터에 설치하고 Claude 유료 요금제로 로그인

3. 둘을 잇기
   - ComfyUI 연결 도구(comfy-mcp)를 Claude Code에 등록한다
   - Claude에게 "내 ComfyUI(127.0.0.1:8188)에 연결해서 작업할 수 있게 설정해 줘"라고 요청하면 필요한 명령을 알려 준다
   - 설치 명령은 Claude가 알려 주면 직접 실행·승인한다

4. 빠진 노드 설치
   - 워크플로를 열었을 때 빨간 노드가 있으면 ComfyUI Manager > Install Missing Custom Nodes
   - 필요한 노드 팩: ComfyUI-VideoHelperSuite (03번 워크플로는 h3-relay도 필요)
   - h3-relay: https://github.com/akatz-ai/h3-relay

5. 연결한 뒤 첫 요청
   "내 ComfyUI로 MiniMax H3 캐릭터 스왑을 하고 싶어. 필요한 노드와 모델이 다 있는지 확인하고, 빠진 건 어떻게 설치하는지 알려 줘."

재료 넣는 곳 (ComfyUI 폴더 안)
- input/   : 바꿀 영상(mp4), 우리 고양이 사진
- models/  : diffusion_models / text_encoders / vae / loras  (모델 파일)
- output/  : 결과가 여기로 나온다
- 데스크톱 앱은 설정에서 폴더 위치를 볼 수 있다

바꿀 영상 고르기
- 직접 찍었거나 사용해도 되는 영상
- 5~10초, 끊기지 않는 한 장면
- 고양이가 같은 동작을 하는 영상이 가장 쉽다
- 24fps가 아니면 Claude에게 24fps로 바꿔 달라고 한다

우리 고양이 사진
- 10~20장, 밝은 곳에서
- 얼굴 정면, 옆얼굴, 전신, 털색이 잘 보이게
- 보정·필터 없는 원본
```
