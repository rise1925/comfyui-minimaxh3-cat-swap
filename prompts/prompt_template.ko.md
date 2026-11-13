# 프롬프트 틀

```text
[프롬프트 틀] 영상 속 고양이를 우리 집 고양이로 (MiniMax H3 + 스왑 LoRA)

사용법: 대괄호 [ ] 부분만 우리 고양이에 맞게 영어로 바꿔 쓰세요.
<Picture 1> = 참조 시트(우리 고양이 실제 사진), <Video 1> = 바꿀 영상입니다.

------------------------------------------------------------
A single continuous uninterrupted take. <Picture 1> shows one real [Maine Coon] cat from several angles and poses; every face in <Picture 1> belongs to this same cat.
The cat's face matches <Picture 1> exactly: [눈: small, dark gray-brown eyes with heavy, half-closed upper lids]; [이마·코: a narrow white blaze running from the forehead down to a small pink nose]; [주둥이: a plain, pure white muzzle and chin]; [귀: large, wide ears with pink insides and long white ear tufts].
Its coat is [털색·무늬: mostly pure white, with soft patches of pale ginger-gold on the top of its head, around its ears, and on the upper sides of its back]. Its fur is [털 길이: very long, silky, and wispy].
The [바꿀 대상: cream-colored cat closest to the camera] in <Video 1> is replaced by this cat from <Picture 1>. It keeps exactly the same body, size, position in the frame, pose, and every movement of the [바꿀 대상] in <Video 1>, but it has the face, eyes, fur colors, and markings of <Picture 1>.
Its two front paws perform every gesture of the [바꿀 대상] in <Video 1>, [동작: including raising a paw and holding the sides of its head].
Its jaw opens as wide as the [바꿀 대상]'s mouth in <Video 1> in every frame, with the same opening, timing, and shape.
The [그대로 둘 것: black-and-white cat standing farther back, the wooden fence, the plants, the ground, and the lighting] stay exactly as they are in <Video 1> from the first frame to the last.
Follow the camera movement, framing, timing, and body movements of <Video 1> exactly.
------------------------------------------------------------

쓰는 요령
- 얼굴(눈, 이마, 주둥이, 귀), 털색, 털 길이를 따로따로 적는다. "고양이로 바꿔"만 쓰면 얼굴만 바뀐다.
- 앞발, 입처럼 원본에서 움직이는 부위를 꼭 적는다.
- 그대로 둘 것(다른 동물, 배경, 조명)을 마지막에 적는다.
- 사람 영상을 쓸 때는 "man"을 "cat"으로 바꾸는 대신 입력 영상을 털색으로 칠하는 편이 훨씬 잘 된다.
- 문장으로 세 번 고쳐도 안 되면 프롬프트 대신 참조 시트나 입력 영상을 고친다.

설정 (제가 쓴 값)
- 샘플러 res_multistep, 스케줄러 simple, LoRA 강도 1.0, 시드 고정 (공식 기본 20스텝, 저는 8GB용 가벼운 8스텝 모델 사용)
- 생성 길이는 17의 배수 + 5 프레임 (22, 39, 56, 90, 124, 158, 175)
- 시험은 22~56프레임, 전체는 마지막에 한 번
```
