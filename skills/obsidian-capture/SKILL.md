---
name: obsidian-capture
description: Capture notes, findings, insights, and decisions into the raw/ inbox of the user's Obsidian second-brain vault ({{VAULT_PATH}}), from any project or path. Use it on requests like "save this to my vault", or whenever an insight worth filing into the wiki comes up. Only drops raw files into raw/ — does not compile the wiki (/ingest).
---

# 옵시디언 캡처 (raw 축적)

사용자의 개인 지식 볼트에 **원본을 던져넣는다**(capture-only). 볼트는 이 절대경로:
`{{VAULT_PATH}}`

## 절차
1. **무엇을 캡처할지 정한다** — 사용자가 준 내용 + 지금 대화·코드 맥락에서 핵심만 추린다. 간결하게, 날것 그대로.
   답변·작성 언어는 볼트 `CLAUDE.md`를 따른다.
2. **볼트 raw/에 새 파일을 쓴다**: `{{VAULT_PATH}}/raw/<YYYY-MM-DD>-<짧은-슬러그>.md`
   - 날짜는 환경의 현재 날짜. 슬러그는 kebab-case(공백·특수문자 금지).
   - **같은 이름이 이미 있으면 덮어쓰지 않는다** — `-2`·`-3` … 또는 더 구체적인 슬러그로 **새 파일**을 만든다 (인박스는 추가 전용).
   - 가벼운 출처 헤더를 단다 (나중 `/ingest`가 쓸 provenance):
     ```
     ---
     captured: <YYYY-MM-DD>
     from: <지금 프로젝트명 또는 경로>
     출처: [<관련 코드경로·URL·PR 번호 등>]
     ---
     ```
   - 본문은 정리된 위키 노트가 아니라 **발견/생각 한 덩어리**. 정리는 나중에 볼트에서 한다.
3. **확인해준다** — 저장 경로 + 한 줄 요약.
4. **알린다** — 저장됐고, 위키로 굳히려면 볼트에서 `/ingest` 하면 된다고.

## 하지 말 것
- `wiki/`·`index.md`·`log.md`는 **건드리지 않는다**. 캡처는 `raw/` 인박스에만 — 컴파일·연결은 볼트에서 `/ingest`가 한다.
- `raw/` 안의 **심링크(외부 메모리 연결)는 읽기 전용** — 쓰지 않는다.
- `raw/processed/`는 `/ingest`가 컴파일 끝낸 원본을 옮겨두는 곳 — **건드리지 않는다**. 캡처는 항상 `raw/` 최상위에 새 파일로만 쌓는다.
- 한 파일에 여러 주제 욱여넣지 않는다. 발견이 여러 개면 파일도 여러 개.
- 기존 raw 파일을 **수정·삭제하지 않는다** — 캡처는 오직 새 파일 추가.
- 볼트 repo에 **git 커밋·푸시하지 않는다** — 파일만 쓰고, 커밋·`/ingest`는 사용자가 한다.
