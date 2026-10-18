# 오서진

- GitHub ID: oseoooojin
- git-practice의 `git log --oneline` 결과 (3개 이상):
  ```
 9e8703e (HEAD -> main) Add: 배운 명령어 목록 추가
 6f5d993 Add: hello.md에 실습 기록 추가
 52a020c Add: hello.md 추가
  ```
- working directory / staging area / repository를 내 말로 설명하기:
  Working directory는 내가 직접 파일을 만들거나 수정하는 공간이다.

 Staging area는 수정한 파일 중 다음 커밋에 포함할 내용을 미리 선택해 두는 공간이다.

 Repository는 commit을 통해 저장한 변경 사항과 기록이 보관되는 공간이다.

- `add` 와 `commit` 을 나눠 놓은 이유 (실습 3 경험으로):
  수정한 파일을 모두 한 번에 저장하는 것이 아니라, 필요한 파일만 선택해서 커밋할 수 있기 때문이다. 실습 3에서 commands.md와 memo.md를 만들었지만, git add로 commands.md만 선택해 커밋할 수 있었다. 이를 통해 작업 내용을 구분해서 관리할 수 있다는 것을 알게 되었다.
- `git diff` 와 `git diff --staged` 의 차이:
  git diff는 파일을 수정한 후 아직 add하지 않은 변경 내용을 보여준다. 반면 git diff --staged는 add를 완료했지만 아직 commit하지 않은 변경 내용을 보여준다. 실습에서 hello.md를 add한 후에는 git diff에 아무것도 나오지 않았지만, git diff --staged에서는 추가한 내용을 확인할 수 있었다
- `git restore` 를 써 본 상황:
  hello.md에 실수로 내용을 추가한 후 git diff로 변경 사항을 확인하고 git restore로 수정 내용을 되돌렸다. 또한 commands.md를 add한 뒤 git restore --staged를 사용해 staging만 취소했고, 실제 파일의 수정 내용은 그대로 남아 있는 것을 확인했다.
- 이번 주 소감:
  이번 주에는 파일이 수정되고 커밋되는 과정을 더 자세히 이해할 수 있었다. 특히 git add와 git commit이 나뉘어 있는 이유를 직접 실습하면서 알게 되었고, git diff와 git restore를 활용하면 변경 내용을 확인하고 실수를 되돌릴 수 있다는 점이 유용했다.