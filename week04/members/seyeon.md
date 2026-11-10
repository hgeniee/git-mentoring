# 김세연

- GitHub ID: gseyeon74
- 내 git-practice 저장소 주소: https://github.com/gseyeon74/git-practice (Private)
- `git remote -v` 결과:
  ```
  origin	https://github.com/gseyeon74/git-practice.git (fetch)
  origin	https://github.com/gseyeon74/git-practice.git (push)
  ```
- 실습 5 이후 `git log --oneline` 결과:
  ```
  661535b Add: 웹에서 hello.md 수정
  c62b5aa Add: 명령어 목록에 git push 추가
  b7627da Add: 명령어 목록에 git restore 추가
  99ed797 Add: 배운 명령어 목록 추가
  c5b3d08 Add: hello.md에 실습 기록 추가
  968ec03 Add: hello.md 추가
  ```
- 로컬 저장소와 원격 저장소를 내 말로 설명하기:
  로컬 저장소는 내 컴퓨터의 `git-practice` 폴더 안 `.git` 에 쌓인 기록이고, 원격 저장소는 같은 기록을 GitHub에 올려 둔 사본이다.
  둘은 자동으로 맞춰지지 않아서, 내가 push 해야 GitHub에 올라가고 pull 해야 내 컴퓨터로 내려온다.
- git-mentoring의 `origin` 과 `upstream` 은 각각 어디를 가리키는지:
  `origin` 은 Fork한 내 저장소(`gseyeon74/git-mentoring`), `upstream` 은 튜터의 원본 저장소(`hgeniee/git-mentoring`)다.
  나는 `origin` 에만 push 할 수 있고, `upstream` 에서는 새 과제를 pull로 받아오기만 한다.
- `git push -u origin main` 에서 `-u` 를 붙이는 이유:
  내 `main` 이 `origin/main` 과 짝이라고 한 번 등록해 두는 것이다. 그래서 실습 4에서는 `git push` 만 쳐도 올라갔고,
  `git status` 에 `ahead of 'origin/main' by 1 commit` 처럼 GitHub보다 몇 커밋 앞서 있는지도 보여 줬다.
- `git pull` 이 하는 일:
  GitHub에 생긴 새 커밋을 받아와서 내 브랜치에 합친다. GitHub에서 `hello.md` 에 한 줄을 추가한 뒤 `git pull` 하니
  내 컴퓨터의 `hello.md` 에도 그 줄이 생기고, log 맨 위에 `Add: 웹에서 hello.md 수정` 커밋이 보였다.
- 이번 주 소감:
  커밋하지 않은 `memo.md` 는 push 해도 GitHub에 안 올라가는 걸 보고, 결국 원격 저장소와 주고받는 단위는 커밋이라는 걸 알았다.
  매주 하던 `git pull upstream main` 이 무슨 뜻이었는지 이제야 제대로 이해됐다.
