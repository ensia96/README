[comment]: <> (TODO: 주석 관련 내용 추가)

# Git

## Overview

- 환경 단위로 [stage](#stage) 운영
- 주제 단위로 [issue](#issue) 생성
- 변경 단위로 [pull request](#pull-request) 생성
- 작업 단위로 [branch](#branch) 생성
- 파일 단위로 [commit](#commit) 생성

## Stage

### Dev (develop)

- 개발 환경
- 운영 환경의 레플리카
- 개발 완료된 코드만 [개발 PR](#for-develop) 을 통해 merge
- 수정이 필요한 경우에만 fix 커밋을 통해 수정

### Main (release)

- 실제로 운영되는 환경
- 사용자에게 전달되는 서비스
- 배포 가능한 코드만 [배포 PR](#for-release) 을 통해 merge
- 긴급 수정이 필요한 경우에만 hotfix 커밋을 통해 수정

## Issue

```
{type}: {title}
```

- 작업의 방향성을 제시
- 제목, 내용, 댓글을 통해 상세하게 설명/토의

### Types

```
report
- 외부 사용자의 제보/문의/요청
- 구체화 후 task 로 전환

story
- 내부 개발자의 아이디어/예상 요구
- 구체화 후 task 로 전환

task
- 기술 작업 (버그 수정, 기능 구현 등)
- report/story 에 의해 생성
```

### Examples

```
report: 로그인 버튼을 눌렀는데 아무런 반응이 없다.
task: 로그인 버튼 클릭 이벤트 핸들러 버그 수정

story: 사용자는 서비스를 이용하기 위해 로그인을 해야 한다.
task: 로그인 페이지 컴포넌트 구현
```

## Pull request

### For develop

```
[#{issue number}] {worker} ({date})
```

- 작업 내용 검토, 반영

### For release

```
[배포] {...PR number} ({date})
```

- 변경 내용 검토, 배포

### Examples

```
[#1] test (1111-11-11)
[#1] new-test (1111-11-12)
[#2] new-test (1111-11-13)
[#3] test (1111-11-14)
```

## Branch

```
{issue number}/{worker}/{date}
```

- issue 에 의해 생성
- pull request 를 통해 반영

### Examples

```
1/test/1111-11-11
1/new-test/1111-11-12
2/new-test/1111-11-13
3/test/1111-11-14
```

## Commit

```
{type}: {한글 메시지}
```

- commit title 만으로 변경 내용을 파악할 수 있도록 작성
- 메시지는 한글로 작성
- 저장소 관례가 있는 경우 해당 관례 우선

### Types

```
feat
- 기능 추가/수정
- 새로운 기능을 추가하거나 기존 기능을 수정할 때

fix
- 버그 해결
- 예상과 다른 동작을 하는 코드를 수정할 때

docs
- 문서 작성
- README 혹은 주석을 추가/수정/제거할 때

chore
- 단순 수정
- 코드 동작에 영향을 주지 않는 수정을 할 때
```

### Examples

```
feat: 페이지 컴포넌트 추가
feat: 테스트 요청 기능 수정
fix: 핸들러가 정상적으로 동작하지 않는 문제 해결
docs: TODO 주석 추가
chore: 코드 포매팅 적용
```
