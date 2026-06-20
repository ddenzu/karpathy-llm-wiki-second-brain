# 🧠 karpathy-llm-wiki-second-brain

> An **Obsidian + Claude Code** template that turns an AI agent into the **disciplined maintainer of your second brain**. You drop raw sources into `raw/`; the agent compiles them into a linked, cited wiki. Based on Andrej Karpathy's *LLM Wiki* pattern, organized as a **4-axis second brain** — Work · Learning · Decisions · Thinking.

**English** · [한국어 ↓](#한국어)

You write sources. The LLM does the bookkeeping — summarizing, cross-linking, indexing, and keeping **one fact in one place**.

### Why
- **Beyond RAG.** RAG re-searches raw text on every query. An LLM Wiki *pre-compiles* knowledge into structured pages, so every new source **compounds** — future questions get better automatically.
- **You own it.** Plain Markdown in Obsidian. No lock-in, fully auditable, every claim traces back to a source.
- **The agent is disciplined.** `CLAUDE.md` is a natural-language *schema* that makes Claude Code a rule-following wiki maintainer, not a forgetful chatbot.

### 3 layers
| Layer | Role |
|---|---|
| `raw/` | Immutable source inbox — **you write here** |
| `wiki/` | LLM-generated notes — summaries, links, concept maps |
| `CLAUDE.md` | The schema — rules the agent must follow |

### Quickstart
1. **Use this template** (green button) or clone it.
2. Open the folder in **Obsidian** (read-only frontend: graph + backlinks).
3. Run **Claude Code** in the folder.
4. Drop a source into `raw/` (or paste a URL) and run:
   - `/ingest <source>` — compile a source into the wiki
   - `/query <question>` — answer from the wiki, with citations
   - `/lint` — health-check (orphans, contradictions, un-ingested backlog)

### Structure
```
index.md            # 4-axis MOC — the entry point
CLAUDE.md           # schema (rules)
log.md              # append-only activity ledger
raw/                # immutable source inbox
wiki/               # LLM-compiled knowledge (incl. 유형:결정 decision notes)
assets/             # binaries — created on first file
.claude/commands/   # /ingest /query /lint
```

---

## 한국어

LLM에게 코드만 짜게 하지 말고, **나만의 위키(지식베이스)를 짓고 유지보수하게 하라** — 안드레 카파시의 *LLM Wiki* 패턴을 **4축 세컨드브레인**(업무·학습·결정·사고)으로 구현한 Obsidian + Claude Code 템플릿.

> **핵심:** 사람은 `raw/`에 원본만 던진다. LLM이 요약·연결·인덱싱·정리를 한다.

### 왜?
- **RAG를 넘어서** — RAG는 질문마다 원본을 다시 검색(지식이 안 쌓임). LLM Wiki는 미리 구조화해 두어 **복리**가 붙는다. 원본 하나 넣으면 미래 질문 전체가 개선.
- **내가 소유** — Obsidian의 순수 마크다운. 락인 없음, 모든 주장은 출처로 역추적.
- **규율 있는 에이전트** — `CLAUDE.md`가 자연어 *스키마*. Claude Code를 규칙 따르는 위키 관리자로 만든다.

### 3계층
| 계층 | 역할 |
|---|---|
| `raw/` | 불변 원본 인박스 (사람이 **여기에만** 씀) |
| `wiki/` | LLM이 생성한 노트 — 요약·링크·개념맵 |
| `CLAUDE.md` | 스키마 = 에이전트가 따르는 규칙 |

### 빠른 시작
1. 이 템플릿을 **Use this template** / clone.
2. 폴더를 **Obsidian**으로 연다 (읽기 전용 프론트엔드: 그래프·백링크).
3. 폴더에서 **Claude Code** 실행.
4. `raw/`에 원본을 던지고(또는 URL 붙여넣기):
   - `/ingest <원본>` — 원본을 위키로 컴파일
   - `/query <질문>` — 위키 기반, 출처 단 답
   - `/lint` — 건강검진 (고아·모순·미ingest 백로그)

### 4축 세컨드브레인
폴더가 아니라 `index.md`의 **섹션(MOC)**으로 산다:

| 축 | 무엇 |
|---|---|
| 🗂 업무 | 활성 작업·도메인 지식 |
| 📚 학습 | 개념·레퍼런스·배운 것 |
| 💭 사고 | 내 생각·통찰·열린 질문 |
| ⚖️ 결정 | `유형: 결정` 노트 (ADR식·append-only) |

새 주제가 생기면 해당 섹션에 한 줄. 폴더는 `raw`·`wiki` 최소만 — **폴더보다 링크·MOC.**

### 원칙
- **하나의 사실은 한 곳에** — 위키가 틀리면 고치지 말고 raw에서 재컴파일.
- **미리 채우지 않기** — 지금 필요한 것만 (냉장고 안 채우기).
- **raw는 불변** — 원본은 신성불가침.
- **고아 금지** — 새 노트는 최소 1개 상위(허브/MOC)에 연결.

### 커스터마이즈
- **언어**: `CLAUDE.md` 절대 규칙의 "한국어로 작성" 줄을 바꾸면 됨.
- **외부 소스**: `raw/` 안에 코드프로젝트 메모 등을 **심링크**로 걸어 단일 소스 레이어로 둘 수 있음 (심링크 대상도 읽기 전용).
- **새 노트 위치**: `.obsidian/app.json`에 `newFileLocation: wiki` 설정 포함 — UI로 만든 노트가 루트로 안 샘.

### 크레딧 / 라이선스
- 방법론: **Andrej Karpathy**, *LLM Wiki*.
- License: **MIT**.
