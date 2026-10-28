# 김선형

- GitHub ID: linearmik
- git-practice의 `git log --oneline` 결과 (3개 이상):
  ```
  8c7466a Add: 배운 명령어 목록 추가
  f39e5c2 Add: hello.md에 실습 기록 추가
  5ab7f3c Add: hello.md 추가
  ```
- working directory / staging area / repository를 내 말로 설명하기: working directory는 내가 파일을 직접 만들고 고치는 작업 공간, staging area는 "이번 커밋에 넣을 것"만 골라 담아 두는 대기 공간, repository는 커밋 기록이 쌓이는 저장소(`.git`)다.
- `add` 와 `commit` 을 나눠 놓은 이유 (실습 3 경험으로): `commands.md` 와 `memo.md` 를 같이 만들었지만, 완성된 `commands.md` 만 add 해서 커밋하고 정리 중인 `memo.md` 는 뺐다. 여러 파일을 고쳐도 관련 있는 변경만 골라 하나의 커밋으로 묶을 수 있도록 단계를 나눠 둔 것이다.
- `git diff` 와 `git diff --staged` 의 차이: `git diff` 는 아직 add 하지 않은 변경을, `git diff --staged` 는 add 해서 커밋을 기다리는 변경을 보여 준다. add 직후 `git diff` 에는 아무것도 안 나오고 `--staged` 에서만 변경이 보였다.
- `git restore` 를 써 본 상황: `hello.md` 에 실수로 쓴 줄을 `git restore hello.md` 로 버렸고, `commands.md` 를 add 한 뒤 `git restore --staged` 로 add만 취소했다.
- 이번 주 소감: 실습 4에서 `echo "실수로 쓴 내용!!!"` 를 쳤더니 zsh가 `!!` 를 직전 명령어로 바꿔 버려서 `dquote>` 에 갇혔다. 작은따옴표로 바꾸니 해결됐다. 다음 주에 이 커밋들을 GitHub에 올리는 게 기대된다!
