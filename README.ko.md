# Stack Skills

<p align="right">
  <a href="README.md">English</a> · <a href="README.ko.md">한국어 (Korean)</a>
</p>

**AI 코딩 에이전트를 위한 5개 인지 방화벽.**

환각, 고착 편향, 확증 편향, 블랙박스 사고, 낙관 편향 — 5가지 추론 실패에 각각 대응합니다.

```
npx skills add whynowlab/stack-skills --all
```

> [Claude Code](https://claude.com/claude-code) 전용 | [Agent Skills](https://agentskills.io) 오픈 표준으로 다른 AI 에이전트 호환
> Created by [@thestack_ai](https://github.com/whynowlab)

---

## 문제

AI가 코드는 빠르게 씁니다. 하지만 추론은 허술합니다.

데이터베이스를 고르라고 하면 — "PostgreSQL 쓰세요." 매번 같은 안전한 기본값.

아키텍처 리뷰를 요청하면 — "괜찮아 보입니다." 동의가 생각보다 쉬우니까.

어떤 주장을 조사해달라고 하면 — 사실과 구분 안 되는 그럴듯한 답을 지어냅니다.

왜 이걸 추천하냐고 물으면 — 결론만 주고 추론 과정은 보이지 않습니다.

뭐가 잘못될 수 있냐고 물으면 — 아무 데나 적용되는 일반론을 나열합니다.

**5가지 추론 실패, 5개 방화벽으로 방어합니다.**

---

## 5가지 실패, 5개 방화벽

| 인지 실패 | 증상 | 방화벽 | 강제하는 것 |
|:---|:---|:---|:---|
| **환각** | 검증 없이 주장 | `cross-verified-research` | 출처 추적, 교차 검증, S/A/B/C 소스 등급제 |
| **고착 편향** | 첫 번째 "뻔한" 답에 고정 | `creativity-sampler` | 확률 가중치 5개 옵션 + 비관습적 대안 강제 |
| **확증 편향** | 반론 대신 동의 | `adversarial-review` | Steel-man 후 3벡터 공격. "괜찮다"는 구조적으로 불가 |
| **블랙박스 사고** | 근거 없이 결론만 제시 | `reasoning-tracer` | 가정 목록, 신뢰도 분해, 최약점 분석 |
| **낙관 편향** | 계획이 성공할 거라 가정 | `pre-mortem` | 실패 가정 후 역추적, 5개 시나리오 + 회로 차단기 |

---

## 스킬

### cross-verified-research

4단계 검증 리서치 파이프라인. 반환각 방어.

- 모든 주장은 인용 가능한 출처에 추적 가능해야 함 — 아니면 `Unverified` 표시
- 소스 등급: S(학술/스펙), A(공식 문서), B(커뮤니티 — 경고 표시), C(일반)
- 교차 검증: 핵심 주장은 2개 이상 *독립* 출처 필요
- 적응적 깊이: 좁은 질문 2-3쿼리, 넓은 조사 8+쿼리

### creativity-sampler

고착 편향 방어. 확률 가중치 옵션 생성기.

- 기본 5개 옵션, 각각 전형성 존 배정 (Conventional → Wild card)
- 최소 1개는 비관습적/와일드카드 존에서 — AI가 평소 억제하는 아이디어
- **Hidden Assumptions** 섹션: "뻔한" 답이 뻔해 보이는 이유를 명시적으로 해부
- 제약 조건 기반 의사결정 매트릭스 + 사용자가 놓친 1개 숨겨진 기준

### adversarial-review

확증 편향 방어. 구조화된 악마의 변호인.

- **Steel-man 우선**: 공격 전에 현재 접근법의 최강 정당화를 먼저 명시
- **3개 독립 벡터**: 논리적 건전성 / 엣지 케이스 공격 / 구조적 무결성
- 심각도 분류: Critical / Major / Minor / Note
- Critical/Major는 반드시 트레이드오프 분석 포함 대안 제시
- 명시적 판정 기준: 완화 불가 Critical = FAIL

### reasoning-tracer

블랙박스 방어. AI 추론을 투명하게.

- **가정 목록**: 모든 가정 번호 매기기, 중요도/검증가능성 평가
- **결정 트리**: 각 분기에서 어떤 대안을 고려했고 왜 기각했는지
- **신뢰도 분해**: 전체 신뢰도를 하위 구성요소로 분해 + 근거
- **최약점**: 하나의 가정이 틀리면 결론이 가장 크게 바뀌는 지점
- **대안 결론**: "만약 [최약 가정]이 틀리면, 결론은 [X]로 바뀐다"

### pre-mortem

낙관 편향 방어. 전향적 실패 분석.

- "6개월 후, 이 계획은 완전히 실패했다. 무엇이 잘못됐는가?"
- 5개 카테고리별 실패 시나리오: 기술/조직/외부/시간/가정
- 가능성 x 영향도 매트릭스 → 상위 3개 집중 분석
- **선행 지표**: 각 상위 리스크의 측정 가능한 조기 경보 신호
- **회로 차단기**: 멈추고 방향을 바꿔야 할 구체적 트리거 조건

---

## 어떤 스킬을 써야 할까?

| 상황 | 스킬 | 이유 |
|:-----|:-----|:-----|
| 기술 조사 또는 사실 검증 | `cross-verified-research` | 출처 기반 검증으로 환각 방지 |
| 옵션 선택 (DB, 프레임워크, 아키텍처) | `creativity-sampler` | 고착 탈피, 비관습적 대안 발굴 |
| 결정을 내렸고, 스트레스 테스트 필요 | `adversarial-review` | 구조적 적대 분석으로 진짜 결함 발견 |
| AI의 추천 근거를 알고 싶을 때 | `reasoning-tracer` | 가정과 추론 체인을 감사 가능하게 |
| 프로젝트 착수 전 리스크 분석 | `pre-mortem` | 실패 모드를 미리 식별 |

### 추천 체인

- **기술 의사결정**: `creativity-sampler` → `cross-verified-research` → `adversarial-review`
- **아키텍처 리뷰**: `reasoning-tracer` → `adversarial-review`
- **프로젝트 킥오프**: `pre-mortem` → `creativity-sampler` (완화책용)
- **풀 리거**: `creativity-sampler` → `cross-verified-research` → `adversarial-review` → `pre-mortem`

---

## 작동 구조

```
AI의 기본 추론:

  [질문] ──→ [첫 번째 그럴듯한 답] ──→ [그대로 사용]


Stack Skills 적용 시:

  [질문]
       │
       ├──→ creativity-sampler ──→ "선택지가 전부 뭐야?"  (고착 방어)
       │
       ├──→ cross-verified-research ──→ "이거 진짜야?"  (환각 차단)
       │
       ├──→ reasoning-tracer ──→ "왜 이걸 믿어?"  (가정 노출)
       │
       ├──→ adversarial-review ──→ "뭐가 잘못됐어?"  (확증 편향 제거)
       │
       └──→ pre-mortem ──→ "어떻게 실패해?"  (낙관 편향 방어)
```

각 방화벽은 독립적 — 하나만 쓰거나, 체이닝 가능.

---

## 벤치마크: 기본 응답 vs Stack Skills

Claude Opus 기준 비공식 비교. 저자의 주관적 평가(1-10). 개선의 유형을 보여주기 위한 것이며, 결과는 달라질 수 있습니다.

| 시나리오 | 기본 | Stack Skills | 변화 |
|:---------|:----:|:-----------:|:----:|
| 리서치: "SQLite가 1000 동시 유저에 적합한가?" | 5/10 | 9/10 | **+80%** |
| 의사결정: "React 이커머스 상태관리 선택?" | 5/10 | 9/10 | **+80%** |
| 리뷰: "단일 PostgreSQL로 OLTP+분석?" | 4/10 | 8/10 | **+100%** |

**무엇이 달라졌나:**
- **리서치**: 기본은 "PostgreSQL 쓰세요." cross-verified-research 적용 시, 1000 동시 유저 = ~30 동시 쓰기 = SQLite 120배 여유 발견. 인용된 벤치마크 기반 완전히 다른 결론.
- **의사결정**: 기본은 "Zustand 추천." creativity-sampler 적용 시, 장바구니를 *어디에* 저장하느냐가 *어떤* 라이브러리를 쓰느냐보다 중요하다는 상위 질문 발견.
- **리뷰**: 기본은 4개 일반론. adversarial-review 적용 시, 멀티테넌트 분석 쿼리의 데이터 유출 Critical 보안 이슈 발견 + RLS SQL 제공.

> 커뮤니티 벤치마크를 환영합니다 — 본인의 before/after 비교를 이슈로 공유해주세요.

---

## 설치

### 빠른 설치 (npx)

```bash
npx skills add whynowlab/stack-skills --all
```

### 개별 설치

```bash
npx skills add whynowlab/stack-skills/cross-verified-research
npx skills add whynowlab/stack-skills/adversarial-review
npx skills add whynowlab/stack-skills/creativity-sampler
npx skills add whynowlab/stack-skills/reasoning-tracer
npx skills add whynowlab/stack-skills/pre-mortem
```

### 수동 설치

```bash
git clone https://github.com/whynowlab/stack-skills.git
cp -r stack-skills/skills/* ~/.claude/skills/
```

---

## 호환성

| 플랫폼 | 상태 |
|:--------|:-----|
| Claude Code | 완전 지원 |
| Cursor | 호환 (Agent Skills 표준) |
| GitHub Copilot | 호환 (Agent Skills 표준) |
| Codex CLI | 호환 (Agent Skills 표준) |

---

## 라이선스

MIT License. [LICENSE](LICENSE) 참조.

---

**Stack Skills** by [@thestack_ai](https://github.com/whynowlab) — AI를 위한 5개 인지 방화벽.
