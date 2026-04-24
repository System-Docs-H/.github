# System-Docs-H

## 프로젝트명
System-Docs-H

## 한 줄 소개
실시간 공동 편집과 문서 중심 협업 경험을 구축하는 팀 프로젝트입니다.

## Overview
System-Docs-H는 collaborative editor frontend와 realtime collaboration backend를 분리해 개발하는 프로젝트입니다. 프런트엔드는 문서 탐색과 편집 경험을 담당하고, 백엔드는 문서 생성·조회, 협업 세션 동기화, snapshot 기반 복원 구조를 담당합니다. 현재 프로젝트는 개발 중이며, 문서화된 규칙과 역할 분담을 바탕으로 단계적으로 통합을 진행하고 있습니다.

## Features
- 문서 목록과 문서별 편집 화면을 중심으로 한 협업 편집 흐름
- Tiptap, Yjs, Yrs 기반의 실시간 공동 편집 구조
- HTTP API와 WebSocket을 통한 프런트엔드-백엔드 연동
- DOCX import utility 기반의 문서 입력 준비
- room registry와 snapshot store를 활용한 저장 및 복원 구조
- 역할 분담, 체크리스트, 규칙 문서를 포함한 협업 중심 개발 환경

## 핵심 기능
- 문서 목록 조회와 문서별 편집 진입 흐름
- collaborative editor shell 기반의 편집 환경 구성
- 문서 생성, 조회, 삭제를 위한 백엔드 API 구조
- 문서별 WebSocket 진입점을 통한 실시간 동기화
- snapshot hydrate와 on-demand restore를 고려한 복구 흐름
- `.docx` 기반 문서 입력 경로와 파일 처리 준비

## Repository Structure
Organization 프로필은 `.github` 저장소의 `profile/README.md`에서 관리하며, 실제 제품 개발은 아래 private 저장소를 중심으로 진행합니다.

| Repository | Description | Visibility |
|---|---|---|
| [Front-End](https://github.com/System-Docs-H/Front-End) | React + TypeScript + Vite 기반 협업 편집 프런트엔드입니다. 문서 목록, 편집 화면, 협업 연결 지점, DOCX import utility를 포함하며 접근 권한이 필요합니다. | Private |
| [Back-End](https://github.com/System-Docs-H/Back-End) | Axum, Tokio, Yrs 기반 협업 백엔드입니다. 문서 API, WebSocket 협업, room registry, snapshot 저장 및 복원 구조를 제공하며 접근 권한이 필요합니다. | Private |

## Tech Stack

### Front-End
- React 19
- TypeScript (strict mode)
- Vite
- React Router
- Tiptap
- Yjs + y-websocket
- Mammoth
- DOMPurify
- Vitest
- Testing Library
- ESLint
- Prettier

### Back-End
- Axum
- Tokio
- tower-http
- Yrs
- yrs-axum
- DashMap
- serde
- serde_json
- uuid
- chrono
- dotenvy
- tracing
- tracing-subscriber
- anyhow
- thiserror
- axum-test

## 모듈 의존성

### Front-End 주요 라이브러리
- 애플리케이션 구성: `React`, `TypeScript`, `Vite`, `React Router`
- 편집 및 협업: `Tiptap`, `Yjs`, `y-websocket`
- 문서 입력 처리: `Mammoth`, `DOMPurify`
- 품질 관리: `Vitest`, `Testing Library`, `ESLint`, `Prettier`

### Back-End 주요 라이브러리
- 웹 서버 및 런타임: `axum`, `tokio`, `tower-http`
- 실시간 협업 및 CRDT: `yrs`, `yrs-axum`
- 상태 관리 및 직렬화: `dashmap`, `serde`, `serde_json`, `uuid`, `chrono`
- 설정 및 로깅: `dotenvy`, `tracing`, `tracing-subscriber`
- 에러 처리 및 테스트: `anyhow`, `thiserror`, `axum-test`

### 구조 요약
- Front-End는 `app`, `pages`, `features`, `lib`, `shared` 중심의 feature-based 구조를 사용합니다.
- Back-End는 `app`, `config`, `state`, `routes`, `collab`, `models`, `storage` 중심으로 서버와 협업 경계를 나눕니다.

## Architecture Summary
프런트엔드는 문서 목록 화면과 문서별 편집 화면을 중심으로 사용자 경험을 구성하고, 백엔드는 문서 단위 API와 협업 세션을 관리합니다. 실시간 편집은 프런트엔드의 협업 연결 지점과 백엔드의 WebSocket/Yrs 기반 동기화 구조가 맞물리는 방식으로 설계되어 있으며, 저장 및 복구는 snapshot 기반 흐름을 중심으로 정리되어 있습니다.

## Collaboration
1. 전체 일정 관리, 기능 우선순위 정리, 구조 설계, 최종 통합 및 데모 준비
2. React 기반 에디터 UI, 편집 기능, 협업 화면, 문서 생성/열기/자동저장 프론트 담당
3. Rust 서버, 실시간 동기화, 동시 편집 충돌 처리, 저장/복구 구조 담당
4. `.docx` import, 파일 처리 검증, 테스트

## Development Plan
프로젝트 진행은 명확한 날짜 대신 3주차까지의 단계 중심으로 관리합니다.

### 1주차
- 프로젝트 문서, 역할 분담, 작업 규칙을 정리합니다.
- 프런트엔드 편집기 구조와 백엔드 API/협업 경계를 맞춥니다.
- 문서 목록, 편집 진입, 협업 연결의 기본 흐름을 정리합니다.

### 2주차
- 프런트엔드와 백엔드의 실시간 협업 연결을 검증합니다.
- 문서 생성·조회 흐름과 저장/복구 흐름을 점검합니다.
- `.docx` import와 파일 처리 검증, 회귀 테스트 보강을 진행합니다.

### 3주차
- 남은 버그를 정리하고 문서를 마감합니다.
- PR 리뷰 반영과 최종 통합을 진행합니다.
- 데모 시나리오와 내부 검토가 가능한 수준으로 마무리합니다.

## Documentation
- Front-End 문서: [Front-End/docs](https://github.com/System-Docs-H/Front-End/tree/main/docs)
- Back-End 문서: [Back-End/docs](https://github.com/System-Docs-H/Back-End/tree/main/docs)

위 문서는 private 저장소에 포함되어 있어 확인하려면 접근 권한이 필요합니다.

## Project Status
현재 프로젝트는 개발 중입니다. Front-End는 collaborative editor frontend의 초기 부트스트랩 단계를, Back-End는 실시간 협업 서버 부트스트랩과 단일 프로세스 기준의 운영 범위를 중심으로 정리한 상태입니다.

## 커밋 규칙
- 커밋 메시지 형식은 `type(scope): subject`를 사용합니다.
- 허용 `type` 예시는 `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `build`, `ci`, `rename`, `remove`입니다.
- 권장 `scope` 예시는 `api`, `sync`, `yrs`, `auth`, `db`, `websocket`, `storage`, `config`, `docs`, `repo`입니다.
- 하나의 커밋에는 하나의 목적만 담고, 리팩토링과 기능 변경을 섞지 않습니다.
- API, WebSocket, 문서 구조와 같은 계약 변경이 있으면 관련 문서와 테스트를 함께 갱신합니다.
- 마무리 전에 각 저장소의 검증 절차를 수행하고, 불확실한 구현은 `TODO` 또는 blocked 상태로 명시합니다.

예시:

```text
feat(websocket): add document room restore on connect
fix(storage): guard corrupt snapshot catalog entries
docs(repo): refresh readme for collaboration workflow
```

## PR 규칙
- `main`에 직접 반영하지 않고 기능 브랜치에서 작업한 뒤 PR로 병합합니다.
- PR은 하나의 목적만 다루며, 리팩토링과 기능 변경을 함께 섞지 않습니다.
- PR 제목은 가능하면 커밋 형식과 같은 `type(scope): subject`를 사용합니다.
- PR 본문에는 변경 배경, 핵심 변경점, 영향 범위, 테스트 결과를 포함합니다.
- API, 협업 흐름, 문서 구조 변경이 있으면 `README.md`와 관련 문서를 함께 갱신합니다.
- 리뷰 포인트는 역할 구분에 맞춰 A, B, C, D 담당과 공유합니다.

## 브랜치 규칙
- 모든 작업 브랜치는 `main`에서 분기합니다.
- 브랜치 하나당 작업 목적 하나만 담당합니다.
- 브랜치 이름은 아래 형식을 권장합니다.

```text
<type>/<scope>-<short-kebab-description>
```

예시:

```text
feat/websocket-document-sync
fix/storage-file-snapshot-catalog
docs/repo-readme-refresh
```

- 장기 브랜치보다 짧고 작은 브랜치를 선호합니다.
- PR 생성 전 최신 `main` 기준으로 충돌을 정리합니다.
- 실험성 작업은 `wip/` 접두사를 사용할 수 있지만, 병합 전에는 목적이 드러나는 이름으로 정리합니다.

## Visibility Notice
Front-End와 Back-End 저장소는 모두 private입니다. 저장소 링크는 포함되어 있지만 외부 사용자는 접근 권한이 있어야 내용을 확인할 수 있습니다. 이 프로필에는 private 저장소의 내부 코드, 세부 실행 방법, 환경 변수, 인증 정보, 서버 주소를 포함하지 않습니다.

---
This organization profile is maintained for project introduction purposes.
