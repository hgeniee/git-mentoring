# 이현진 (튜터 예시)

- GitHub ID: hgeniee
- git-practice의 `git log --oneline` 결과 (3개 이상):
  ```
  ea7b454 Add: 명령어 목록에 git restore 추가
  6860bb1 Add: 배운 명령어 목록 추가
  e4a88c5 Add: hello.md에 실습 기록 추가
  d17efaf Add: hello.md 추가
  ```
- working directory / staging area / repository를 내 말로 설명하기:
  working directory는 내가 실제로 파일을 고치는 작업 공간, staging area는 "이번 커밋에 넣을 것"을 골라 담아 두는 대기 공간,
  repository는 커밋이 차곡차곡 저장되는 기록 보관소(`.git`)다.
- `add` 와 `commit` 을 나눠 놓은 이유 (실습 3 경험으로):
  `commands.md` 와 `memo.md` 를 동시에 만들었지만, 완성된 `commands.md` 만 add 해서 커밋했다.
  이렇게 여러 파일을 고쳐도 **관련 있는 변경만 골라** 하나의 커밋으로 묶을 수 있도록 단계를 나눠 둔 것이다.
- `git diff` 와 `git diff --staged` 의 차이:
  `git diff` 는 아직 add 하지 않은 변경을, `git diff --staged` 는 add 해서 커밋을 기다리는 변경을 보여 준다.
  add 직후 `git diff` 에 아무것도 안 나와서 처음엔 변경이 사라진 줄 알았다.
- `git restore` 를 써 본 상황:
  `hello.md` 에 실수로 쓴 줄을 `git restore hello.md` 로 버렸고, `commands.md` 를 add 한 뒤 `git restore --staged` 로 add만 취소했다.
- 이번 주 소감:
  `git status` 를 습관처럼 치면서 파일이 어느 영역에 있는지 확인하는 게 이번 주의 핵심이에요. 다음 주에는 오늘 만든 커밋들을 GitHub에 올려 봅니다!
