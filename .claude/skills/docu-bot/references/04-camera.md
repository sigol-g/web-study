# 4단계 · 촬영팀 — AI 영상 제작 (Kling AI 등 image-to-video)

목표: 3단계에서 만든 정지 이미지에 움직임을 더해 컷을 영상으로 만든다.

## 원칙
- **한 컷 = 한 동작 + 한 카메라 무빙.** 여러 행동을 넣으면 형태가 무너진다.
- 길이는 5초 기본, 롱테이크가 필요할 때만 10초. 대본의 컷 길이(초)와 맞춘다.
- 이미지에 이미 있는 것(인물 외형, 공간)은 다시 길게 묘사하지 않는다. **움직임만** 묘사한다.
- 느린 움직임이 다큐 톤에 맞고 왜곡도 적다: `slowly`, `subtle`, `gently`.
- 시작/끝 프레임 기능이 있으면 두 이미지로 동작의 시작과 끝을 고정한다.

## 프롬프트 틀
```
[피사체의 동작], [카메라 무빙], [환경의 움직임(연기·먼지·종이)], [분위기], cinematic, 24fps film look
Negative: morphing face, extra fingers, warped text, flicker, fast motion, modern objects
```

카메라 무빙 어휘:
| 무빙 | 쓰임 |
|---|---|
| `static shot` | 독백, 대사 집중 |
| `slow push in` | 생각이 깊어질 때, 감정 고조 |
| `slow pull out` | 고립, 장면 마무리 |
| `slow pan left/right` | 공간·기계 훑기 |
| `macro tracking along` | 자료 INS, 텍스트·기계 디테일 |
| `rack focus from A to B` | 시선 이동, 의미 연결 |

예 (자료 INS — 텔레프린터):
```
paper tape slowly feeds through a vintage teleprinter, printed numbers "105621" pass by,
macro shot, slow tracking along the tape, drifting dust in warm light, cinematic, 24fps film look
Negative: warped numbers, fast motion, morphing machinery
```
한국어: 텔레프린터 종이 테이프가 천천히 지나가며 숫자가 보이는 매크로 컷.

> 숫자·글자는 AI 영상에서 자주 깨진다. 중요한 텍스트는 편집에서 자막/합성으로 넣는 것을 권한다.

## 샷리스트 출력 형식
| 컷 | 원본 이미지 | 동작 | 카메라 | 길이 | 프롬프트 | 체크 |
|---|---|---|---|---|---|---|
| S2-C1 | S2-C1.png | 펜을 내려놓는다 | static | 5초 | (코드블록) | 얼굴 왜곡 / 손가락 |

## 후반 안내 (요청 시)
- 생성 영상 검수: 얼굴·손·텍스트 왜곡, 시대에 맞지 않는 물건, 컷 간 의상·조명 연속성.
- 내레이션: 대본 AUDIO 칸을 그대로 TTS/녹음 대본으로 추출해 준다.
- 편집 순서: 대본 S# 순서대로 컷 배치 → 내레이션 → 효과음·음악 → 자막(고증 자료 출처 표기 포함).
