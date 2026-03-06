# Stack Skills

<p align="right">
  <a href="README.md">English</a> · <a href="README.ko.md">한국어 (Korean)</a>
</p>

**AI의 사고력을 쌓아올리다.**

당신의 AI는 코드를 빠르게 씁니다. 그런데 *생각*을 잘 하나요?

첫 번째 답을 고르지, 최선의 답을 고르지 않습니다. 반론을 제기해야 할 때 동의합니다. 검증 없이 그럴듯한 답을 지어냅니다. **Stack Skills가 그걸 바꿉니다.**

> AI가 코드를 쓰는 방식이 아니라, *생각하는 방식*을 업그레이드하는 7개 메타-인지 스킬.

```
npx skills add whynowlab/stack-skills --all
```

> [Claude Code](https://claude.com/claude-code) 전용 | 41개 AI 에이전트 호환 via [Agent Skills](https://agentskills.io) 오픈 표준
> Created by [@thestack_ai](https://github.com/whynowlab)

---

## 문제

AI에게 데이터베이스를 고르라고 합니다. "PostgreSQL 쓰세요" — 안전한 기본값.

아키텍처 리뷰를 요청합니다. "괜찮아 보입니다" — 동의하는 게 쉬우니까.

어떤 주장을 조사해달라고 합니다. 그럴듯한 답을 지어냅니다 — 구분도 안 됩니다.

**당신의 AI는 빠르지만 얕습니다. Stack Skills는 속도를 늦추고 진짜 생각하게 만듭니다.**

---

## 설치 전 vs 설치 후

| Stack Skills 없이 | Stack Skills 적용 |
|:---|:---|
| 안전한 답 1개 | 확률 가중치가 붙은 5개 옵션 — AI가 평소 억제하는 아이디어 포함 |
| "괜찮아 보입니다" | 반드시 문제를 찾아야 하는 3벡터 공격. "괜찮다"는 출력 금지. |
| 출처 없는 주장 | 소스 등급(S/A/B/C)이 붙은 4단계 검증 리서치 |
| 표면적 리뷰 | 5개 분석 렌즈를 통한 현미경 해부 |
| 이해했다는 가정 | 실제로 모르는 것을 드러내는 3단계 9문제 |

---

## 스킬 목록

### 리서치 & 의사결정

| 스킬 | 기능 | 트리거 |
|:------|:-----|:--------|
| **cross-verified-research** | 4단계 검증 리서치 파이프라인, 소스 등급제 (S/A/B/C), 반환각 게이트 | `"조사해줘"` `"리서치"` `"검증해줘"` |
| | 사용 예: `/cross-verified-research 모바일 백엔드에 gRPC가 REST보다 나은가?` | |
| **creativity-sampler** | 확률 가중치 기반 5개 옵션 생성, p<10% 비관습적 대안 강제 포함 | `"대안"` `"옵션 뽑아"` `"아이디어"` |
| | 사용 예: `/creativity-sampler 실시간 리더보드에 어떤 데이터베이스?` | |
| **adversarial-review** | 3벡터 악마의 변호인 공격 (논리/엣지케이스/마이크로분해) + 심각도 분류 | `"스트레스 테스트"` `"이거 괜찮아"` `"문제 없을까"` |
| | 사용 예: `/adversarial-review 3인 스타트업에서 Kubernetes를 선택했다` | |

### 워크플로우 & 아키텍처

| 스킬 | 기능 | 트리거 |
|:------|:-----|:--------|
| **skill-composer** | 다중 스킬 파이프라인 구성 (Sequential / Fork-Join / Iterative) | `"워크플로우"` `"파이프라인"` `"스킬 조합"` |
| | 사용 예: `/skill-composer 기술 의사결정을 위한 research + adversarial 파이프라인` | |
| **persona-architect** | 5레이어 AI 페르소나 DNA 설계 (정체성/소통/행동/전문성/경계) | `"페르소나"` `"역할 설정"` `"톤 설정"` |
| | 사용 예: `/persona-architect 시니어 보안 감사관 페르소나 생성` | |

### 분석 & 테스트

| 스킬 | 기능 | 트리거 |
|:------|:-----|:--------|
| **deep-dive-analyzer** | 3모드 마이크로 분석: 코드 / 시스템 / 컨셉 (5부 코덱스 구조) | `"심층 분석"` `"분석해줘"` `"뜯어봐"` |
| | 사용 예: `/deep-dive-analyzer 인증 플로우의 취약점 분석` | |
| **tiered-test-generator** | 3단계 지식 검증 (개념/응용/전문가) + 채점 + 3차원 진단 리포트 | `"문제 만들어"` `"이해도 확인"` `"시험 문제"` |
| | 사용 예: `/tiered-test-generator React hooks 검증 문제 생성` | |

---

## 어떤 스킬을 써야 할까?

| 상황 | 추천 스킬 | 이유 |
|:-----|:---------|:-----|
| 기술을 조사하거나 사실 주장을 검증할 때 | `cross-verified-research` | 다중 소스 검증으로 환각 방지 |
| 여러 옵션 중 선택해야 할 때 (DB, 프레임워크, 아키텍처) | `creativity-sampler` | 비관습적 대안 포함 5개 옵션 강제 생성 |
| 이미 결정을 내렸고, 스트레스 테스트하고 싶을 때 | `adversarial-review` | 3벡터 공격으로 사각지대 발견 |
| 복잡한 시스템을 깊이 이해해야 할 때 | `deep-dive-analyzer` | 레이어별 철저한 분석 |
| 여러 스킬을 파이프라인으로 조합하고 싶을 때 | `skill-composer` | 복잡한 워크플로우를 위한 스킬 체이닝 |
| 특정 도메인의 전문 AI 페르소나가 필요할 때 | `persona-architect` | 맥락 인식 전문가 페르소나 생성 |
| 팀 지식을 검증하거나 학습 자료를 만들 때 | `tiered-test-generator` | 다단계 난이도 평가 생성 |

### 추천 체인
- **기술 의사결정**: `creativity-sampler` → `cross-verified-research` → `adversarial-review`
- **아키텍처 리뷰**: `deep-dive-analyzer` → `adversarial-review`
- **리서치 보고서**: `cross-verified-research` → `deep-dive-analyzer`

---

## 스킬 관계도

```
                        skill-composer
                    (모든 스킬을 파이프라인으로)
                             |
         +-------------------+-------------------+
         |                   |                   |
   cross-verified      creativity          persona
     -research          -sampler           -architect
   "사실을 검증한다"    "선택지를 연다"     "목소리를 만든다"
         |                   |
         v                   v
    deep-dive          adversarial
    -analyzer            -review
   "깊이 이해한다"      "결함을 찾는다"
         |
         v
    tiered-test
    -generator
   "이해를 검증한다"
```

---

## 벤치마크: 기본 응답 vs Stack Skills

Claude Opus를 사용한 비공식 내부 비교입니다. 점수는 저자의 주관적 품질 평가(1-10)이며, 독립적으로 검증되지 않았습니다. 개선의 *유형*을 보여주기 위한 것이지 과학적 주장이 아닙니다. 결과는 작업과 모델에 따라 달라집니다.

### 결과

| 시나리오 | 기본 | Stack Skills | 향상 |
|:---------|:----:|:-----------:|:----:|
| 리서치: "SQLite가 1000 동시 유저에 적합한가?" | 5/10 | 9/10 | **+80%** |
| 의사결정: "React 이커머스 상태관리 선택?" | 5/10 | 9/10 | **+80%** |
| 아키텍처 리뷰: "단일 PostgreSQL로 OLTP+분석?" | 4/10 | 8/10 | **+100%** |
| **평균** | **4.7** | **8.7** | **+85%** |

### 무엇이 달라졌는가?

| 차원 | Stack Skills 없이 | Stack Skills 사용 |
|:-----|:-------------------|:------------------|
| 인용 소스 수 | 0개 | 10개 (공식 문서 포함) |
| 탐색한 옵션 수 | 1-3개 (안전한 디폴트) | 5개 (비관습적 대안 포함) |
| 발견한 이슈 수 | 4개 (표면적) | 12개 (Critical 4건) |
| 노출한 숨겨진 가정 | 0개 | 5개 이상 |
| 실행 가능성 | "X 쓰세요" | SQL 설정, 타임라인, 트레이드오프 |

### 핵심 발견

> **참고**: 이 벤치마크는 저자의 평가를 반영합니다. 커뮤니티 벤치마크를 환영합니다 — 본인의 before/after 비교를 이슈로 공유해주세요.

- **리서치**: 기본 응답은 "PostgreSQL 쓰세요." Stack Skills는 1000 동시 유저 = ~30 동시 쓰기 = **SQLite의 120배 여유**라는 정량적 인사이트 발견. 완전히 다른 결론.
- **의사결정**: 기본 응답은 "Zustand 추천." Stack Skills는 **장바구니 저장 위치(서버 vs 클라이언트)가 라이브러리 선택보다 중요**하다는 상위 질문 발견.
- **리뷰**: 기본 응답은 4개 일반론 나열. Stack Skills는 **멀티테넌트 분석 쿼리의 데이터 유출** Critical 보안 이슈 발견 + RLS SQL 제공.

> 기본 응답은 **답을 준다**. Stack Skills는 **더 나은 질문을 발견하게 한다.**

---

## 설치

### Plugin Marketplace (권장)

```bash
/plugin marketplace add whynowlab/stack-skills
/plugin install stack-skills@whynowlab/stack-skills
```

### 수동 설치

```bash
git clone https://github.com/whynowlab/stack-skills.git
cp -r stack-skills/skills/* ~/.claude/skills/
```

---

---

**Stack Skills** by [@thestack_ai](https://github.com/whynowlab) — AI의 사고력을 쌓아올리다.
