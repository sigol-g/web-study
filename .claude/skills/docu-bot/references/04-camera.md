# 4단계 · 촬영팀 — AI 영상 제작 (Kling · Seedance)

목표: 3단계에서 만든 정지 이미지에 움직임을 더해 컷을 영상으로 만든다.

| 도구 | 언제 | 길이 |
|---|---|---|
| **Kling** (촬영 감독) | 한 동작·한 카메라 무빙의 기본 컷, 자료 INS | 5~10초 |
| **Seedance** (연출 감독) | 여러 동작·카메라 변화가 이어지는 복합 장면, 원테이크 | 10~15초 |

---
## A. Kling — 생성한 이미지 영상화

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

---
## B. Seedance — 복잡한 장면 연출
여러 비트를 **초 단위 타임라인**으로 나눠 한 번에 연출한다. 컷 편집 없이 원테이크처럼 이어지는 장면에 쓴다.

규칙:
- 맨 앞에 **시대·장소·소리 조건**을 고정한다: `1950, night, no dialogue, room tone only.`
- 그 다음 구간별로: `0-3s: … 3-8s: … 8-12s: …` 각 구간에 **동작 하나 + 카메라 하나**.
- 첫 구간은 `hold the starting frame`으로 시작 이미지를 지키게 한다.
- 시작/끝 프레임(레퍼런스 이미지 2장)을 넣으면 끝 장면이 고정된다. 끝 프레임에 텍스트가 있으면 마지막 1초를 편집에서 정지 프레임으로 늘리는 방법을 함께 안내한다.
- 마지막에 룩 고정: `photographic realism, restrained saturation, soft open shadows, no music.`

틀:
```
One continuous camera move. [연도], [시간대], [대사 유무], [소리 조건].
0-3s: hold the starting frame, [샷 크기] of [인물], [작은 동작].
3-8s: the camera [무빙], revealing [공간/정보].
8-12s: [핵심 동작/전환].
12-15s: the camera stops on [마지막 이미지].
[룩 고정 문구]
```

예 (S#2 방 셋 — 이미테이션 게임 규칙 설명):
```
One continuous camera move. 1950, night, no dialogue, room tone only.
0-3s: hold the starting frame, medium shot of the man seated at a desk under a single lamp, he blinks slowly.
3-8s: the camera pulls straight back and rises, revealing three bare rooms seen from above like a floor plan.
8-12s: in the left room a woman writes an answer with a fountain pen; in the right room a teleprinter types by itself, no hands.
12-15s: the camera stops above the middle room, the man glowing faintly beneath the lamp.
Photographic realism, restrained saturation, soft open shadows, no music.
```
한국어: 한 사람 → 위로 빠지며 방 세 개(질문자·사람·기계)가 드러나는 원테이크.

---
## 샷리스트 출력 형식
| 컷 | 도구 | 원본 이미지 | 동작 | 카메라 | 길이 | 프롬프트 | 체크 |
|---|---|---|---|---|---|---|---|
| S2-C1 | Kling | S2-C1.png | 펜을 내려놓는다 | static | 5초 | (코드블록) | 얼굴 왜곡 / 손가락 |
| S2-C2 | Seedance | S2-C2.png + 끝프레임 | 방 셋 공개 | pull back + rise | 15초 | (코드블록) | 방 구조 / 텍스트 |

## 검수 체크
얼굴·손·텍스트 왜곡, 시대에 맞지 않는 물건, 컷 간 의상·조명 연속성. 실패한 컷은 원인(동작 과다, 무빙 과다, 묘사 충돌)을 짚고 프롬프트를 한 가지만 바꿔 재생성한다.
