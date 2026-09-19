# 바이러스 대시 (Virus Dash)

코딩 세상을 달리는 3레인 러너 게임입니다. 바이러스를 피하고, 백신을 먹어 목숨을 채우세요.

![AI 곰 에셋](assets/grids/bear_asset_grid.png)

## 플레이 방법

`index.html`을 브라우저로 열면 바로 실행됩니다. 설치할 것은 없습니다.

| 조작 | 키보드 | 모바일 |
|---|---|---|
| 레인 이동 | ← → 또는 A · D | 좌우 스와이프 / ◀ ▶ 버튼 |
| 점프 | ↑ · W · 스페이스 | 위로 스와이프, 탭 / 점프 버튼 |
| 일시정지 | P · Esc | 일시정지 버튼 |

## 규칙

- 목숨 3개로 시작, 최대 5개
- 작은 바이러스(분홍): 점프로 넘기
- 큰 바이러스(진홍): 점프 불가, 레인을 바꿔 피하기
- 백신: 목숨 +1 (가득 차 있으면 보너스 150점)
- 데이터 비트: 점수 +15

## 캐릭터

| | AI 곰 | AI 오리 |
|---|---|---|
| 특징 | 점프가 길고 높음 | 레인 이동이 빠름 |

## 폴더 구조

```
index.html              게임 본체 (HTML + CSS + JS 한 파일)
assets/sprites/         게임용 스프라이트 시트 (300px 칸 × 8)
                        0 정면 · 1~5 달리기 · 6 기쁨 · 7 아픔
assets/grids/           확인용 에셋 그리드, 달리기 GIF
assets/source/          원본 캐릭터 시트
tools/build_assets.py   원본 → 스프라이트 시트 자동 생성 스크립트
```

## 에셋 다시 만들기

원본 이미지를 바꿨을 때만 필요합니다.

```bash
pip install -r tools/requirements.txt
python tools/build_assets.py
```

Windows에서는 한글 폰트 경로를 지정하세요: `set KR_FONT=C:/Windows/Fonts/malgunbd.ttf`

## 자주 바꾸는 값 (index.html)

| 원하는 것 | 찾을 코드 |
|---|---|
| 캐릭터별 점프 길이·높이, 이동 속도 | `const CHARS` |
| 게임 속도 | `g.speed=Math.min(34,15+g.dist/140)` |
| 시작 목숨 | `lives:3` |
| 백신 등장 간격 | `g.nextVax=` |
