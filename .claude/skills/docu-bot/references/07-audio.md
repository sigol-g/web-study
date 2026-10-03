# 7단계 · 음향팀 — 오디오 완성

세 갈래: **목소리(AI 성우) · 효과음(AI 음향감독) · 음악(AI 음악감독)**. 끝에 큐시트로 묶는다.

## 7-1. AI 성우 — ElevenLabs
두 방법:
- **보이스 클론**: 내 목소리(본인 또는 동의받은 목소리만)를 학습시켜 템플릿으로 만든다. 조용한 방에서 녹음한 깨끗한 음성을 쓴다.
- **보이스 디자인**: 프롬프트로 새 목소리를 만든다. 3개 후보 중 고른다.

보이스 디자인 프롬프트 틀 (영어):
```
A [나이]-year-old [국적/억양] man, [음색: soft-spoken, slightly hoarse…], speaking [속도] with
controlled breath and long considered pauses, as if reading a private journal aloud by candlelight.
The emotion stays beneath the surface: [감정 키워드]. No theatricality, no bright smiling warmth,
no modern conversational lilt. Clean intimate studio recording, close-miked, no background noise, no reverb.
```
대사 생성 규칙:
- 대본 AUDIO 칸을 클립 단위(5단계 L01, L02…)로 나눠 생성. 파일명 `S##-C##-L##.mp3`.
- 쉼표·마침표·줄바꿈으로 호흡을 조절한다. 한 번에 길게 생성하지 않는다.
- 숫자·연도는 읽을 방식대로 풀어 쓴다(1950년 → 천구백오십 년).
- 같은 클립을 2~3개 뽑아 고른다.

## 7-2. AI 음향감독 — 효과음
씬마다 필요한 소리를 **앰비언스(바탕) / 하드 이펙트(동작) / 폴리(작은 손동작)**로 나눠 목록을 만든다.

프롬프트 규칙 (영어가 결과가 좋다):
- 소리 요소를 구체적으로 + 감정 톤 + 공간 환경 + 길이.
```
late-night 1950s office room tone, low electrical hum of a valve machine, distant rain on the window, intimate and lonely, small room, 10 seconds
mechanical teleprinter typing a short line then stopping, metallic clatter, close-miked, dry room, 4 seconds
fountain pen nib scratching on thick paper, very close, quiet room, 3 seconds
```
- 앰비언스는 길게(10초 이상) 뽑아 루프용으로, 하드 이펙트는 영상 길이에 맞춰 짧게.

## 7-3. AI 음악감독 — Suno
작품 전체 테마 1곡 + 필요한 씬별 변주. 대사가 있는 다큐는 **보컬 없는 연주곡**이 기본.

스타일 프롬프트 틀:
```
[장르: documentary score, chamber music], [악기: solo piano, string quartet, soft cello], [템포: slow, 60 bpm],
[분위기: introspective, melancholic, restrained], [질감: intimate, sparse, warm room], instrumental, no vocals
```
- 가사 칸에 `[Instrumental]`. 구조 태그로 길이 조절: `[Intro] [Theme] [Build] [Outro]`.
- 제목에 작품과 씬을 담는다 (예: Teleprinter After Midnight).
- 대사 밑에 깔 곡은 **중음역이 비어 있는** 편성(피아노 저음·현 지속음)을 고른다.
- 상업적 사용 시 해당 서비스 요금제의 사용권을 확인하라고 안내한다.

## 7-4. 큐시트
| 씬 | 시간 | 대사 파일 | 효과음 | 음악(구간) | 비고 |
|---|---|---|---|---|---|
| S1 | 00:00–00:12 | S01-C01-L01 | 방 앰비언스, 시계 | 메인 테마 Intro (페이드 인) | 대사 시작 시 음악 -6dB |
