\# 제혜린



\- GitHub ID: MY-ID

\- git-practice의 `git log --oneline` 결과 (3개 이상):

&#x20; ```

2367ed6 (HEAD -> main) Add: 배운 명령어 목록 추가

ae79e98 Add: hello.md에 실습 기록 추가

0942675 Ass: hello.md추가



&#x20; ```

\- working directory / staging area / repository를 내 말로 설명하기: working derectory는 파일을 직접 만들고 수정하는 공간이다. staging area는 다음 커밋에 넣을 변ㄱㅕㅇ ㄴ용을 골랃ㅜ는 곤간이다. repository는 커밋한 기록이 저장되는 곳이다.

\- `add` 와 `commit` 을 나눠 놓은 이유 (실습 3 경험으로):

여러 파일을 수정해도 원하는 변경내용만 골라 기록하기 위해서이다. 실습 3에서 commands.md만 add하고 commit해서, 아직 정리 중인 memo.md는 커밋에 포함하지 않을 수 있었다.

\- `git diff` 와 `git diff --staged` 의 차이: git diff는 수정한 내용 중 아직 add하지 않은 변경을 보여주고, git diff --staged는 add는 했지만 아직 commit하지않은 변경을 보여줌

\- `git restore` 를 써 본 상황: hello.md에 실수로 추가한 내용을 지울 때 사용했다. commands.md에서는 git restore --staged로 add를 취소한 뒤, got restore로 남은수정내용을 버렸다.

\- 이번 주 소감: 처음에는 add를 하면 왜 파일이 초록색으로 표시되는지 헷갈렸는데, 커밋할 내용을 선택한 상태라는 것을 알게 되었다. 

