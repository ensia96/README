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
story
- 사용자 스토리
- 예상 요구사항

voc
- 사용자 피드백
- 실제 요구사항

report
- 버그 리포트
- 발생한 문제
```

### Examples

```
story: 사용자는 서비스를 이용하기 위해 로그인을 해야 한다.
voc: 로그인을 하는데, 비밀번호를 입력하는 화면이 너무 작아서 불편하다.
voc: 로그인 버튼을 눌렀는데 아무런 반응이 없다.
```

## Pull request

### For develop

```
[{issue number}] {worker} ({date})
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
[배포] #1, #2, #3, #4 (3333-33-33)
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
{type}: {message} ({target})
```

- commit title 만으로 변경 내용을 파악할 수 있도록 작성

### Types

```
init
- 기능 추가
- 프로젝트에 새로운 코드를 추가할 때

test
- 동작 시험
- 버그가 있을 수 있는 코드를 시험할 때

feat
- 동작 수정
- 특정 기능에 대한 코드 동작을 수정할 때

refactor
- 코드 개선
- 동작 방식은 유지하면서 코드를 개선할 때

fix
- 버그 해결
- 예상과 다른 동작을 하는 코드를 수정할 때

hotfix
- 긴급 수정
- 브랜치를 생성하지 않고 바로 수정해야 할 때

docs
- 주석 작성
- README 혹은 주석을 추가/수정/제거할 때

chore
- 단순 수정
- 코드 동작에 영향을 주지 않는 수정을 할 때
```

### Examples

#### for frontend

```
init: 페이지 컴포넌트 추가 (TestPage)
test: 변경된 핸들러 동작 테스트 (TestPage)
feat: 테스트 요청 기능 수정 (TestPage)
refactor: 테스트 기능이 test 메서드를 활용하도록 개선 (TestPage)
fix: 테스트 요청 시, 핸들러가 정상적으로 동작하지 않는 문제 해결 (TestPage)
hotfix: 핸들러가 동작하지 않는 현상 해결 (TestPage)
docs: TODO 주석, ref 주석 추가 (TestPage)
chore: 레이아웃 스타일 수정 (TestPage)
```

#### for backend

```
init: 컨트롤러 추가 (TestController)
test: 변경된 서비스 동작 테스트 (TestService)
feat: test 메서드의 조건 처리 방식 변경 (TestController)
refactor: test 메서드의 조건 처리 방식을 switch/case 문으로 변경 (TestService)
fix: TestService 에서 반환된 응답을 처리하지 못하는 문제 해결 (TestController)
hotfix: TestError: this is test 해결 (TestService)
docs: TODO 주석 내용 수정 (TestService)
chore: 코드 포매팅 적용 (TestService)
```
