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
4. Drop a source into `raw/` (or paste a URL), then run a command:

### Commands
| Command | What it does | Benefit |
|---|---|---|
| `/ingest <source>` | Compile a source into the wiki | Summarize → format, citations, ≥2 links, index, log — integrated every time |
| `/query <question>` | Cited answer from the wiki | Index→drill-down + citations + no-hallucination + compounding |
| `/lint` | Wiki health-check | Catches orphans, contradictions, stale claims, un-ingested backlog |

### Structure
```
index.md            # 4-axis MOC — the entry point
CLAUDE.md           # schema (rules)
log.md              # append-only activity ledger
raw/                # source inbox (un-ingested)
raw/processed/      # ingested originals — moved here, never edited
wiki/               # LLM-compiled knowledge (incl. 유형:결정 decision notes)
assets/             # binaries — created on first file
.claude/commands/   # /ingest /query /lint
```

### 4-axis second brain
The axes don't live as folders — they exist as **sections (MOCs) in `index.md`**:

| Axis | What it holds |
|---|---|
| 🗂 Work | Active tasks · domain knowledge |
| 📚 Learning | Concepts · references · things learned |
| 💭 Thinking | Ideas · insights · open questions |
| ⚖️ Decisions | `유형: 결정` notes (ADR-style · append-only) |

New topic → one line under its axis. Folders stay minimal (`raw`·`wiki`) — **links & MOCs over folders.**

### 🧭 What's improved
Faithful to the standard Karpathy LLM Wiki pattern, with **one key difference**:

- **Decisions & Thinking as first-class axes** — most LLM wikis are concept/entity knowledge wikis; this adds Work · Learning · Decisions · Thinking, with **Decisions kept as append-only notes**.

> Everything else follows the pattern faithfully (links over folders, immutable sources moved to `raw/processed/` once ingested, citation back-tracing).

### 🔌 Use it from anywhere (while coding, in meetings)
Despite the name, a vault is just a folder — capture anywhere, organize in the vault.

- **In the vault**: run Claude Code → `/ingest` · `/query` · `/lint`
- **From any project (work, coding, meetings)**: don't stop working — drop the finding into `<vault>/raw/`, then `/ingest` it in the vault later to accumulate into the wiki
  - Simple: save a `raw/YYYY-MM-DD-title.md` note
  - Smooth: a global capture skill saves it to `raw/` with one line — "save this to my vault"
- **Right before ending a session or switching context**: save the key points to `raw/` — a good habit for catching context that's easy to lose
- **Auto-feed**: symlink an agent's memory (e.g. your global Claude memory) or a code project's memory into `raw/`, and that growing memory becomes a source (read-only)

Knowledge built up this way is visible to the agents you work with in other sessions, so they catch what you miss and give more complete answers.

### Customize
- **Language**: change the "write in Korean" line in `CLAUDE.md`'s absolute rules.

### Credits / License
- Methodology: **Andrej Karpathy**, *LLM Wiki*.
- License: **MIT**.

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
4. `raw/`에 원본을 던지고(또는 URL 붙여넣기), 커맨드 실행:

### 명령
| 커맨드 | 하는 일 | 이점 |
|---|---|---|
| `/ingest <원본>` | 원본 → 위키 컴파일 | 요약·합의 → 형식·출처·링크(2+)·인덱스·로그까지 자동 통합 |
| `/query <질문>` | 위키 기반, 출처 단 답 | 인덱스→드릴다운 + 출처 + 환각금지 + 복리 |
| `/lint` | 위키 건강검진 | 고아·모순·낡은 주장·미ingest 정기 점검 |

### 구조
```
index.md            # 4축 MOC — 진입점
CLAUDE.md           # 스키마 (규칙)
log.md              # append-only 활동 로그
raw/                # 원본 인박스 (미처리)
raw/processed/      # ingest된 원본 — 여기로 이동, 내용 편집 안 함
wiki/               # LLM이 컴파일한 지식 (유형:결정 노트 포함)
assets/             # 바이너리 — 첫 파일 때 생성
.claude/commands/   # /ingest /query /lint
```

### 4축 세컨드브레인
폴더가 아니라 `index.md`의 **섹션(MOC)**으로 존재함:

| 축 | 무엇 |
|---|---|
| 🗂 업무 | 활성 작업·도메인 지식 |
| 📚 학습 | 개념·레퍼런스·배운 것 |
| 💭 사고 | 내 생각·통찰·열린 질문 |
| ⚖️ 결정 | `유형: 결정` 노트 (ADR식·append-only) |

새 주제가 생기면 해당 섹션에 한 줄. 폴더는 `raw`·`wiki` 최소만 — **폴더보다 링크·MOC.**

### 🧭 무엇이 개선됐나
표준 카파시 LLM Wiki 패턴을 충실히 따르되, **핵심 차이는 하나**.

- **결정·사고도 1급 축** — 대부분 LLM 위키는 개념·엔티티 중심 지식 위키. 여기선 **업무·학습·결정·사고** 4축으로 나누고, 특히 **결정은 append-only 노트**로 쌓임.

> 나머지는 카파시 패턴 정통을 따름 (링크 > 폴더, 원본 불변·ingest 후 `raw/processed/`로 이동, 출처로 역추적).

### 🔌 어디서나 쓰기 (개발·회의 중에도)
볼트는 금고, 즉 그냥 폴더입니다 — 수집은 어디서나, 정리는 볼트에서.

- **볼트 안**: Claude Code 실행 → `/ingest` · `/query` · `/lint`
- **다른 프로젝트(업무·개발·회의 중)**: 일 멈추지 말고 발견을 `<볼트>/raw/`에 던져둠 → 나중에 볼트에서 `/ingest`로 정리해 wiki로 축적
  - 간단: `raw/YYYY-MM-DD-제목.md` 파일로 저장
  - 매끄럽게: 전역 캡처 스킬을 두면 어디서든 "이거 볼트에 저장해" 한 마디로 `raw/`에 저장됨
- **세션을 끝내거나 맥락을 바꾸기 직전**: 그 대화의 핵심을 `raw/`에 저장 — 흩어지기 쉬운 맥락을 붙잡는 좋은 습관
- **자동 연결**: 에이전트 메모리(예: 전역 Claude 메모리)나 코드 프로젝트의 메모리를 `raw/`에 심볼릭 링크로 걸면, 쌓이는 메모리가 그대로 소스가 됨 (링크 대상도 읽기 전용)

이렇게 쌓인 위키 지식은 다른 세션에서 대화하는 에이전트도 인지할 수 있어, 내가 놓친 부분까지 짚고 더 완성도 높은 답을 줌.

### 커스터마이즈
- **언어**: `CLAUDE.md` 절대 규칙의 "한국어로 작성" 줄을 바꾸면 됨.

### 크레딧 / 라이선스
- 방법론: **Andrej Karpathy**, *LLM Wiki*.
- License: **MIT**.
