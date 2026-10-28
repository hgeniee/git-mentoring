# 이현진 (튜터 예시)

- GitHub ID: hgeniee
- 실습 4 이후 `git log --oneline --graph --all` 결과:
  ```
  *   e81c4d0 (HEAD -> main) Fix: title.md 충돌 해결
  |\
  | * 5a2f7b9 Fix: 브랜치에서 제목 변경
  * | c94e1a3 Fix: main에서 제목 변경
  |/
  * 0d6b8f2 Add: 제목 파일 추가
  *   9f3a215 Merge branch 'add-hobby'
  |\
  | * 4b7e6c1 Add: 자기소개에 취미 추가
  * | 2c8d9e4 Add: 명령어 목록에 git merge 추가
  |/
  * 81e5f3a Add: 자기소개 파일 추가
  * b3f91c2 (origin/main) Add: 웹에서 hello.md 수정
  * 7a0d5e1 Add: 명령어 목록에 git push 추가
  * ea7b454 Add: 명령어 목록에 git restore 추가
  * 6860bb1 Add: 배운 명령어 목록 추가
  * e4a88c5 Add: hello.md에 실습 기록 추가
  * d17efaf Add: hello.md 추가
  ```
- 브랜치를 내 말로 설명하기:
  `main` 을 건드리지 않고 따로 작업하는 갈래다. 실습 1에서 `main` 으로 옮기니 `profile.md` 가 사라졌다가,
  `add-profile` 로 돌아오니 다시 생겨서 "브랜치마다 다른 상태를 갖고 있다"는 게 실감 났다.
- fast-forward 와 merge commit 의 차이 (실습 2, 3 경험으로):
  실습 2에서는 `main` 에 새 커밋이 없어서 `main` 이 브랜치 끝으로 그냥 이동했고(fast-forward), 새 커밋이 생기지 않았다.
  실습 3에서는 `main` 과 `add-hobby` 양쪽에 커밋이 있어서 둘을 합치는 `Merge branch 'add-hobby'` 커밋이 새로 생겼고, 그래프도 갈라졌다가 합쳐졌다.
- 충돌이 났을 때 `title.md` 에 보인 내용과, 어떻게 해결했는지:
  `<<<<<<< HEAD` 아래에 main의 `제목: Git 놀이터`, `=======` 아래에 브랜치의 `제목: 나의 첫 Git 연습장` 이 보였다.
  둘을 섞어서 `제목: 나의 첫 Git 놀이터` 한 줄만 남기고 표시 줄을 모두 지운 뒤 `git add title.md` → `git commit` 했다.
- git-mentoring에서 매주 `main` 에서 새 브랜치를 만드는 이유:
  `git switch -c` 는 지금 있는 브랜치에서 갈라져 나오기 때문에, 지난주 브랜치에서 만들면 지난주 커밋까지 따라와서 PR에 섞인다.
  매주 최신 `main` 에서 시작해야 그 주 과제만 깔끔하게 PR로 보낼 수 있다.
- 이번 주 소감:
  충돌은 무서운 에러가 아니라 "어느 쪽으로 할까요?"라는 질문이에요. 오늘 일부러 한 번 겪어 봤으니, 실제 PR에서 충돌이 나도 당황하지 않을 거예요!
