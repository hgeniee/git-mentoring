# 김세연

- GitHub ID: gseyeon74
- 실습 4 이후 `git log --oneline --graph --all` 결과:
  ```
  *   b095771 Fix: title.md 충돌 해결
  |\
  | * 4bc12e6 Fix: 브랜치에서 제목 변경
  * | 4e996e4 Fix: main에서 제목 변경
  |/
  * 9cd1255 Add: 제목 파일 추가
  *   f6a04e4 Merge branch 'add-hobby'
  |\
  | * 5a0e46f Add: 자기소개에 취미 추가
  * | ddff3ca Add: 명령어 목록에 git merge 추가
  |/
  * c00b98e Add: 자기소개 파일 추가
  * 661535b Add: 웹에서 hello.md 수정
  * c62b5aa Add: 명령어 목록에 git push 추가
  * b7627da Add: 명령어 목록에 git restore 추가
  * 99ed797 Add: 배운 명령어 목록 추가
  * c5b3d08 Add: hello.md에 실습 기록 추가
  * 968ec03 Add: hello.md 추가
  ```
- 브랜치를 내 말로 설명하기:
  같은 저장소 안에서 기록을 따로 이어 갈 수 있게 해 주는 작업 공간이다. `add-profile` 에서 만든 `profile.md` 가
  `main` 으로 옮기면 폴더에서 안 보이고 다시 돌아오면 보여서, 브랜치를 바꾸면 폴더 내용이 그 브랜치 상태로 바뀐다는 걸 알았다.
- fast-forward 와 merge commit 의 차이 (실습 2, 3 경험으로):
  실습 2는 `main` 이 그대로인 상태에서 합쳐서 `Fast-forward` 라고 나왔고, 새 커밋 없이 `main` 이 `c00b98e` 로 옮겨 가기만 했다.
  실습 3은 `main` 에도 `git merge` 추가 커밋이 있어서 `Merge branch 'add-hobby'` 커밋(`f6a04e4`)이 새로 만들어졌고,
  그래프에서 두 줄로 갈라졌다가 다시 하나로 합쳐졌다.
- 충돌이 났을 때 `title.md` 에 보인 내용과, 어떻게 해결했는지:
  `<<<<<<< HEAD` 와 `=======` 사이에 main의 `제목: Git 놀이터`, `=======` 와 `>>>>>>> change-title` 사이에 브랜치의 `제목: 나의 첫 Git 연습장` 이 있었다.
  두 제목을 합친 한 줄만 남기고 표시 줄을 지운 뒤, `cat` 으로 표시가 없는 걸 확인하고 `git add title.md` → `git commit` 으로 merge를 끝냈다.
- git-mentoring에서 매주 `main` 에서 새 브랜치를 만드는 이유:
  새 브랜치는 지금 있는 브랜치의 커밋을 그대로 가지고 시작한다. 지난주 브랜치에서 만들면 지난주 과제 커밋까지 이번 주 PR에 들어가니까,
  upstream을 받아 둔 최신 `main` 에서 갈라져야 그 주 파일 하나만 PR에 담긴다.
- 이번 주 소감:
  충돌을 일부러 만들어 보니 Git이 망가진 게 아니라 같은 줄을 어느 쪽으로 할지 물어보는 것뿐이었다.
  `git log --oneline --graph --all` 로 갈라지고 합쳐지는 모양을 직접 보니 merge가 어떻게 기록되는지 감이 잡혔다.
