# 3단계 · 미술팀 — AI로 이미지와 무드 제작

## 3-1. 미술 감독: 무드보드 (Midjourney)
목표: 작품만의 룩을 정하고, 이후 모든 이미지가 같은 세계에 있도록 고정한다.

1. **톤 & 룩 키워드 5~8개**를 바이블에서 뽑는다. (예: 1950s British, low-key lighting, teal-green shadows, tungsten practicals, film grain, muted palette)
2. 무드보드용 이미지 프롬프트 6~12개: 인물 / 공간 / 소품 / 자료 클로즈업 / 빛의 질감으로 고르게 나눈다.
3. 사용자가 Midjourney 무드보드(Personalize → Moodboard)를 만들면 받은 코드(`--p 코드`)를 바이블의 톤 & 룩에 기록하고 이후 모든 프롬프트에 붙인다.

프롬프트 틀:
```
[피사체와 행동], [시대·장소], [조명], [색감], [렌즈·질감], cinematic still --ar 16:9 --style raw --p [무드보드코드]
```

## 3-2. 캐릭터·공간 시트 (일관성 고정)
- **캐릭터 시트**: 같은 인물을 정면 / 3/4 측면 / 측면 / 전신으로. 외형 고정 문구를 매번 그대로 반복한다.
  ```
  character sheet of a 38-year-old British mathematician, 1950, slightly wavy dark brown hair parted to the side,
  tweed jacket over a rumpled white shirt and knit tie, 178cm slim build, front view, three-quarter view, side view,
  neutral grey background, soft even light --ar 16:9 --style raw
  ```
- **공간 시트**: 스튜디오 공간을 와이드 1장으로 확정하고, 이후 컷은 그 이미지를 레퍼런스로 쓴다.
- 실존 인물이면 사진 기록에 근거한 외형만 묘사한다. **배우 이름·영화 제목은 프롬프트에 넣지 않는다.**

## 3-3. 조명 감독: 조명과 앵글 (Higgsfield 등)
캐릭터 레퍼런스로 일관성을 유지하면서 컷별로 빛과 앵글을 설계한다.

컷마다 이 표를 채운다:
| 컷 | 샷 크기 | 앵글 | 키라이트 | 보조광/역광 | 실내 광원(practical) | 감정 |
|---|---|---|---|---|---|---|
| S1-C1 | MCU | 눈높이, 측면 프로필 | 창문 쪽 차가운 달빛, 하드 | 약한 림라이트 | 책상 백열 스탠드 | 고독, 숙고 |

조명 어휘(프롬프트용):
- 분위기: `low-key`, `chiaroscuro`, `single motivated source`, `pool of light`
- 방향: `side light`, `rim light`, `top light`, `backlit silhouette`
- 색: `warm tungsten practical vs cool moonlight`, `teal shadows`
- 앵글: `eye-level`, `low angle (권위)`, `high angle (고립)`, `over-the-shoulder`, `dutch angle (불안, 아껴 쓰기)`

## 출력
1) 무드보드 프롬프트 세트 2) 캐릭터·공간 시트 프롬프트 3) 대본의 컷별 이미지 프롬프트 + 조명/앵글 표.
컷 번호는 대본의 S#-C#와 맞춘다.
