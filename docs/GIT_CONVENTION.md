# 🌿 Gyuniverse Git Convention

이 문서는 Gyuniverse 프로젝트의 공통 Git 협업 기준입니다.

## Branch Strategy

기본 구조는 `main + develop + 작업 Branch`를 사용합니다.

```text
main
└── develop
    ├── feat/{JIRA-KEY}-{summary}
    ├── fix/{JIRA-KEY}-{summary}
    ├── refactor/{JIRA-KEY}-{summary}
    └── docs/{JIRA-KEY}-{summary}
```

### Branch 역할

- `main`: 배포 및 최종 안정본
- `develop`: 개발 통합본
- `feat/*`: 기능 개발
- `fix/*`: 버그 수정
- `refactor/*`: 기능 변경 없는 구조 개선
- `docs/*`: 문서 작업

예시:

```text
feat/JP-16-retriever
fix/JP-23-search-error
refactor/JP-27-rag-pipeline
```

## Commit Message

기본 형식:

```text
<type>: <JIRA-KEY> <summary>
```

예시:

```text
feat: JP-16 hybrid retriever 구현
fix: JP-23 검색 결과 예외 처리
refactor: JP-27 retrieval pipeline 구조 개선
docs: JP-31 README 실행 방법 추가
```

권장 type:

- `feat`: 기능 추가
- `fix`: 버그 수정
- `refactor`: 리팩터링
- `docs`: 문서
- `test`: 테스트
- `chore`: 설정 및 기타 작업

## Pull Request

기본 흐름:

```text
Jira Issue
→ Branch
→ Commit
→ Pull Request
→ CI / Review
→ Merge
→ Jira Done
```

- 기능 Branch는 기본적으로 `develop`을 대상으로 PR을 생성합니다.
- `develop → main`은 릴리즈 또는 안정본 반영 시 별도 PR로 진행합니다.
- 주요 Branch 직접 Push는 제한하는 것을 원칙으로 합니다.
- 최소 1명의 Review 후 Merge합니다.
- CI가 구성된 이후에는 필수 검증 통과 후 Merge합니다.

## Merge Strategy

기본 Merge 방식은 **Squash Merge**를 권장합니다.

이유:

- 하나의 PR을 하나의 의미 있는 변경 단위로 남길 수 있음
- 작업 중 발생한 자잘한 Commit을 최종 History에서 정리 가능
- Jira Issue / PR 단위로 변경 이력을 추적하기 쉬움

팀 상황에 따라 Merge Commit이 더 적합한 경우 Decision Log에 근거를 남기고 변경할 수 있습니다.
