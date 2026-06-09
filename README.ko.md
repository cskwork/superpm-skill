# /superpm

[English](README.md) | **한국어**

**PM 요청 하나를 넣으면 검증된 산출물 하나가 나온다 - 가장 작은 유용한 산출물을, 독립
critic이 프레임워크와 실제 의사결정에 대조해 점검한 결과.**

PM 도구 전체를 하나의 워크플로로 접은 단일 에이전트 스킬이다. 요청에서 의도를 캡처하고,
**PM 도메인으로 분기**해 알맞은 프레임워크를 적용하고, 가장 작은 유용한 산출물을 만든 뒤,
전달 전에 독립 critic을 돌린다 - 그리고 멈춘다.

추가 설치 없음: 레포를 클론해 스킬 디렉터리에 심링크하고 `/superpm <요청>`.

## 무엇인가

`phuryn/pm-skills`는 9개 플러그인에 걸친 68개 PM 스킬 마켓플레이스로, 각 스킬이 이름으로
불러오는 별도 파일이다. `superpm`은 이 카탈로그를 **단일 스킬, 단일 레포**로 접는다. 스킬을
고르지 않는다 - PM 요청만 말하면 워크플로가 알아서 라우팅한다:

```
/superpm 인앱 추천 기능 PRD 써줘
/superpm 한국 SMB 급여 시장 TAM/SAM/SOM 뽑아줘
/superpm 활성화(activation) 기회 솔루션 트리 만들어줘
/superpm 프로 티어 가격 전략 초안
/superpm 이 A/B 테스트 읽고 출시할지 죽일지 판단해줘
/superpm EU 출시 GTM 플랜
/superpm 이 JD에 맞춰 내 PM 이력서 리뷰해줘
```

## 작동 방식

모든 도메인에서 같은 루프가 돈다. 바뀌는 건 어떤 프레임워크가 로드되느냐뿐이다.

1. **Capture** - 요청을 PM 도메인 + 목표 산출물로 분류. 진짜 모호하면 ≤5질문 interview
   게이트가 작동. 문서/데이터로 답할 수 있는 건 묻지 않고 읽는다.
2. **Frame** - 산출물이 답해야 할 실제 의사결정과 완결 기준을 한 줄로 고정.
3. **Draft** - 도메인 프레임워크 적용. 가장 작은 유용한 산출물, 실제 입력값, 가정은 가정으로 표기.
4. **Critic** - 독립 패스가 초안을 red-team: 누락 섹션·근거 없는 주장·검증 안 된 가정·회피한
   결정을 각각 risk로 적발.
5. **Deliver** - risk를 반영하고 멈춤. 무엇을 근거로 점검했는지 보고.

## 도메인 (pm-skills 9개 플러그인 = 9개 라우트)

| 도메인 | 범위 |
|---|---|
| **DISCOVER** | 아이디에이션, 리스크 가정, 기회 솔루션 트리, 기능 우선순위, 고객 인터뷰, 메트릭 |
| **STRATEGY** | 전략 캔버스, 비전, 밸류 프로프, Lean/Business 모델, 수익화, 가격, SWOT/PESTLE/Porter/Ansoff |
| **EXECUTE** | PRD, OKR, 아웃컴 로드맵, 스프린트, 레트로, pre-mortem, 스토리, 이해관계자 맵, 우선순위 프레임워크, red-team |
| **RESEARCH** | 페르소나, 세그먼트, 고객 여정, 시장 규모(TAM/SAM/SOM), 경쟁 분석, 감성 분석 |
| **ANALYTICS** | 자연어→SQL, 코호트 분석, A/B 테스트 판독 |
| **GTM** | 고투마켓, beachhead, ICP, 그로스 루프, motion, 배틀카드 |
| **GROWTH** | 마케팅 아이디어, 포지셔닝, 밸류프롭 문구, 네이밍, North Star 메트릭 |
| **TOOLKIT** | 이력서 리뷰/맞춤, NDA, 개인정보처리방침, 교정 |
| **AI-SHIP** | shipping artifacts, intended-vs-implemented 갭(근거 인용) |

## critic이 필요한 이유

PM 산출물엔 유닛 테스트가 없어서 그럴듯한 초안도 틀릴 수 있다. `superpm`은 `supergoal`의 규율을
빌려온다: 독립 리더가 산출물을 세 가지 근거 - **프레임워크 완결성, 실제 의사결정, 모든 주장의
근거** - 에 대조하고, 각 빈틈을 전달 전 risk로 적발한다. 출처 없는 숫자와 회피한 결정은 blocker다.

## 설치

이 레포가 **곧 스킬**이다. 에이전트 CLI가 스킬을 찾는 위치에 둔다:

```bash
git clone <repo-url> superpm-skill
ln -s "$(pwd)/superpm-skill" <your-agent-skills-dir>/superpm
# 예: ~/.claude/skills/superpm, ~/.codex/skills/superpm
```

이후 에이전트 CLI에서 `/superpm <PM 요청>`.

## 구조

```
SKILL.md      얇은 스파인: 원칙 · intent-capture 테이블 · 루프 · reference map
reference/    intent · critic · discover · strategy · execute · research · analytics · gtm · growth · toolkit · ai-ship
templates/    PRD · 전략 캔버스 · 기회 솔루션 트리 · 배틀카드
docs/         DESIGN.md
```

## 크레딧

- PM 프레임워크 카탈로그: **[phuryn/pm-skills](https://github.com/phuryn/pm-skills)** (MIT),
  Paweł Huryn 큐레이션 - 여기서 단일 스킬로 병합.
- 워크플로 + 검증 규율: **[cskwork/supergoal-skill](https://github.com/cskwork/supergoal-skill)** (MIT)에서 이식.

## 라이선스

MIT. [`LICENSE`](LICENSE) 참고.
