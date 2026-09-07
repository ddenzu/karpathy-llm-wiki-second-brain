---
name: obsidian-query
description: Read the user's Obsidian second-brain vault ({{VAULT_PATH}}) to answer questions, from any project or path (read-only, cite sources). TRIGGER — before starting any investigation or judgment, read the vault's index.md FIRST — before grepping code, querying a database, or opening files. If a relevant note exists, read it; if not, stop immediately. SKIP (overrides trigger) — the user already gave the answer · a simple edit or finding a file path · already queried the same topic in this session. Never writes to the vault; filing notes back is done inside the vault with /ingest.
---

# 옵시디언 쿼리 (위키 회상, 읽기 전용)

작업 위치와 무관하게 사용자의 개인 지식 볼트를 **읽어서** 답한다. 볼트는 이 절대경로:
`{{VAULT_PATH}}`

벡터 RAG·임베딩을 쓰지 않는다 — **인덱스→드릴다운**으로 충분하다.

## 절차
1. **인덱스 먼저** — `index.md`(전체 MOC)를 읽어 질문과 관련된 허브·노트를 추린다.
   인덱스 줄이 `[[제목]] — 결론 한 줄` 형태라, **그 줄만으로 답이 되는 경우가 많다.**
2. **후보가 없으면 종료** — 추가 grep으로 볼트를 더 뒤지지 않는다. 대신 `ls raw/*.md`로 미처리 인박스를 확인해
   **"위키에 없고 인박스에도 관련 원본 없음"** 과 **"인박스에 아직 안 넣은 원본이 있음"**(= `/ingest`하면 답이 생길 수 있음)을 구분해 말한다.
3. **드릴다운 — 통째로 읽는다** — 관련 `wiki/` 노트를 1~2개 연다. **통독이 기본**이다:
   호출 1회로 끝나고, 답이 어디 있는지 맞힐 필요가 없고, 표 밖 단서 문장을 놓치지 않는다.
   잘라 읽는 건 **아주 큰 허브 노트에서 필요한 주제 외 섹션이 대부분일 때만**.
   토큰을 아끼려고 자르지 않는다. 목표는 절약이 아니라 **빠르고 정확하게 얻는 것**이다.
   필요하면 `raw/`·`raw/processed/`(심링크 포함) 원본까지. **전부 읽기만 한다.**
4. **출처 단 답** — 근거(파일 경로·URL·코드 경로)를 달고, 노트의 `updated`를 보고 **"언제 기준의 지식인지"를 밝힌다.**
   위키에 근거가 없으면 **"위키에 없음"**이라고 명시한다(지어내지 말 것). 답변 언어는 볼트 `CLAUDE.md`를 따른다.
5. **저장 가치가 있으면** — 직접 쓰지 말고 `obsidian-capture`로 `raw/`에 던지라고 제안한다.

## 볼트와 실측이 어긋날 때
- **실측(코드·DB·문서)이 이긴다. 단 이기는 건 "현재 값"까지다.**
- **실측 1건으로 볼트의 대역·분포를 고치지 않는다** (n=1로 분포를 못 고친다).
- 볼트는 **어디를 볼지**와 **과거에 뭘 틀렸는지**를 주지, 현재 값을 확정하지 않는다.
- 어긋남을 발견하면 `raw/`에 남긴다(확정 안 됐으면 **열린 질문**으로).

## 하지 말 것
- 볼트에 **쓰지 않는다** — 노트 생성·수정, `index.md`·`log.md` 갱신 **전부 금지**. 이 스킬은 순수 읽기.
- 근거 없이 답을 **지어내지 않는다** — "위키에 없음"이 정답일 때가 있다.
- 임베딩·벡터 검색으로 빠지지 않는다 — 항상 `index.md`부터.
- `log.md`는 **전문을 읽지 않는다** — 볼트에서 가장 큰 단일 파일인 append-only 원장이다. 필요하면 tail(최근) 또는 grep(특정 주제)으로 필요한 줄만.
- 깊은 정리가 필요하면 볼트에서 `/query`·`/ingest`를 쓰라고 안내한다 (이건 quick recall 레인).
