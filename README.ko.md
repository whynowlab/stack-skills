# Stack Skills

**AI의 사고력을 쌓아올리다.**

코드를 작성하는 것이 아니라, AI가 *생각하는 방식*을 업그레이드하는 7개 메타-인지 스킬. 더 깊이 조사하고, 더 날카롭게 결정하고, 더 엄격하게 검증하세요.

> [Claude Code](https://claude.com/claude-code) 전용 | [Agent Skills](https://agentskills.io) 오픈 표준 호환
> Created by [@thestack_ai](https://github.com/whynowlab)

---

## Stack Skills가 다른 이유

대부분의 AI 코딩 스킬은 코드를 더 빨리 쓰게 해줍니다. **Stack Skills는 더 잘 생각하게 해줍니다.**

| 기존 스킬 | Stack Skills |
|:---|:---|
| "보일러플레이트 생성" | "이 주장을 3개 이상 소스로 교차검증" |
| "린트 에러 수정" | "이 아키텍처에 반대하는 가장 강력한 논거 3개" |
| "유닛 테스트 작성" | "이해도를 검증하는 3단계 9문제 생성" |
| "코드 포맷팅" | "평소라면 억제될 비관습적 대안 포함 5가지 옵션" |

코딩 단축키가 아닙니다. **사고력 업그레이드**입니다.

---

## 스킬 목록

### 리서치 & 의사결정

| 스킬 | 기능 | 트리거 |
|:------|:-----|:--------|
| **cross-verified-research** | 4단계 검증 리서치 파이프라인, 소스 등급제 (S/A/B/C), 반환각 게이트 | `"조사해줘"` `"리서치"` `"검증해줘"` |
| **creativity-sampler** | 확률 가중치 기반 5개 옵션 생성, p<10% 비관습적 대안 강제 포함 | `"대안"` `"옵션 뽑아"` `"아이디어"` |
| **adversarial-review** | 3벡터 악마의 변호인 공격 (논리/엣지케이스/마이크로분해) + 심각도 분류 | `"스트레스 테스트"` `"이거 괜찮아"` `"문제 없을까"` |

### 워크플로우 & 아키텍처

| 스킬 | 기능 | 트리거 |
|:------|:-----|:--------|
| **skill-composer** | 다중 스킬 파이프라인 구성 (Sequential / Fork-Join / Iterative) | `"워크플로우"` `"파이프라인"` `"스킬 조합"` |
| **persona-architect** | 5레이어 AI 페르소나 DNA 설계 (정체성/소통/행동/전문성/경계) | `"페르소나"` `"역할 설정"` `"톤 설정"` |

### 분석 & 테스트

| 스킬 | 기능 | 트리거 |
|:------|:-----|:--------|
| **deep-dive-analyzer** | 3모드 마이크로 분석: 코드 / 시스템 / 컨셉 (5부 코덱스 구조) | `"심층 분석"` `"분석해줘"` `"뜯어봐"` |
| **tiered-test-generator** | 3단계 지식 검증 (개념/응용/전문가) + 채점 + 3차원 진단 리포트 | `"문제 만들어"` `"이해도 확인"` `"시험 문제"` |

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
