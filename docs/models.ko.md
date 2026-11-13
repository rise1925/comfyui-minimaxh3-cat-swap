# 사용 모델

```text
사용 모델과 설정 (공식 모델 기준)

[영상 변환 - MiniMax H3 공식 파일]  https://huggingface.co/Comfy-Org/MiniMax-H3
- 영상 모델: minimax_h3_ref2va_pruned_int8_convrot.safetensors  -> models/diffusion_models
- 텍스트 인코더: qwen3vl_32b_minimax_h3_nvfp4_awq.safetensors  -> models/text_encoders
- VAE: minimax_h3_video_vae_int8_convrot.safetensors  -> models/vae
- (선택) 4스텝 터보 LoRA: minimax_h3_ref2v_turbo_4step_v0.1_comfyui_bf16.safetensors  -> models/loras

[캐릭터 스왑 LoRA]  https://huggingface.co/akatz-ai/MiniMax-H3-Character-Swap-LoRA
- h3_character_swap_pro4500_1000.safetensors (V1, 공식 안내) 또는 h3_character_swap_v1.5.safetensors  -> models/loras
- 제가 비교해 보니 V1과 V1.5의 바꾸는 능력은 같았습니다.

[설정]
- 샘플러 res_multistep, 스케줄러 simple, LoRA 강도 1.0
- 공식 안내 기본값은 20스텝 (터보 LoRA를 켜면 4스텝)
- 시드는 하나로 고정
- 비교용으로 er_sde + 시그마 시프트 12를 써 보니 털에 줄무늬가 생겼다

[여러 마리 중 하나만 (고급)]
- SAM3: sam3.1_multiplex_fp16.safetensors -> models/checkpoints
- 커스텀 노드 h3-relay (마스크 안만 다시 그리기)

[화질 올리기 (선택), ComfyUI 기본 노드]
- seedvr2_7b_int8_convrot.safetensors -> models/diffusion_models
- seedvr2_ema_vae_fp16.safetensors -> models/vae

[참고: 제 노트북에서 실제로 쓴 것]
- 그래픽카드 8GB에 맞춘 가벼운 버전(8스텝 합친 모델, GGUF 텍스트 인코더)을 썼습니다.
- 강좌의 시간(7초 약 70분, 1초 시험 7~15분)은 이 가벼운 버전 기준입니다. 공식 20스텝은 더 오래 걸릴 수 있습니다.
- 8GB에서 공식 파일이 느리거나 메모리가 부족하면 Claude에게 "8GB에서 돌아가는 가벼운 버전을 찾아 줘"라고 요청하세요.
```
