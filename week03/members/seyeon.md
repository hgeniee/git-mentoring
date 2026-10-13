# 김세연

- GitHub ID: gseyeon74
- git-practice의 `git log --oneline` 결과 (3개 이상):
  ```
  b7627da Add: 명령어 목록에 git restore 추가
  99ed797 Add: 배운 명령어 목록 추가
  c5b3d08 Add: hello.md에 실습 기록 추가
  968ec03 Add: hello.md 추가
  ```
- working directory / staging area / repository를 내 말로 설명하기:
  working directory는 내가 파일을 만들고 고치는 실제 폴더, staging area는 그중에서 다음 커밋에 넣기로 고른 변경을 올려 두는 곳,
  repository는 커밋한 기록이 쌓여 있는 `.git` 폴더다. 파일은 `add` 로 staging area에, `commit` 으로 repository에 들어간다.
- `add` 와 `commit` 을 나눠 놓은 이유 (실습 3 경험으로):
  `commands.md` 와 `memo.md` 를 같이 만들었는데 `commands.md` 만 add 하니까 커밋에는 그 파일만 들어가고 `memo.md` 는 Untracked로 남았다.
  아직 정리 중인 파일은 빼고 완성된 것만 골라서 커밋할 수 있게 하려고 두 단계로 나눠 둔 것이다.
- `git diff` 와 `git diff --staged` 의 차이:
  `git diff` 는 수정했지만 아직 add 하지 않은 변경을 보여 주고, `git diff --staged` 는 add 해서 커밋을 기다리는 변경을 보여 준다.
  `hello.md` 를 add 한 뒤에는 `git diff` 에 아무것도 안 나오고 `git diff --staged` 에서만 추가한 줄이 보였다.
- `git restore` 를 써 본 상황:
  `hello.md` 에 "실수로 쓴 내용!!!" 을 추가했다가 `git restore hello.md` 로 버려서 마지막 커밋 상태로 되돌렸다.
  `commands.md` 는 add 한 다음 `git restore --staged commands.md` 로 add만 취소했는데, 수정한 내용은 그대로 남아 있어서 다시 add 하고 커밋했다.
- 이번 주 소감:
  명령어를 칠 때마다 `git status` 로 파일이 어느 영역에 있는지 확인하니까 add와 commit이 각각 무슨 일을 하는지 이해가 됐다.
  `git restore` 는 버린 내용을 되살릴 수 없다고 해서, 쓰기 전에 `git diff` 로 먼저 확인하는 습관을 들여야겠다.
