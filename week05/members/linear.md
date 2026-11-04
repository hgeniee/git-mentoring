# 김선형

- GitHub ID: linearmik
- 실습 4 이후 `git log --oneline --graph --all` 결과:
  ```
  *   4f1a8c2 (HEAD -> main) Fix: title.md 충돌 해결
  |\
  | * b72e09d Fix: 브랜치에서 제목 변경
  * | 9d3c5f1 Fix: main에서 제목 변경
  |/
  * e05b7a3 Add: 제목 파일 추가
  *   71c9e4b Merge branch 'add-hobby'
  |\
  | * c8a2f60 Add: 자기소개에 취미 추가
  * | 2e6d1b8 Add: 명령어 목록에 git merge 추가
  |/
  * 5ab403e Add: 자기소개 파일 추가
  * 0f8e2c7 (origin/main) Docs: 웹에서 hello.md 오타 수정
  * a39d6b1 Add: 명령어 목록에 git push 추가
  * 6e7b0f4 Add: 명령어 목록에 git restore 추가
  * d2c58a9 Add: 배운 명령어 목록 추가
  * 18f4e3c Add: hello.md 추가
  ```
- 브랜치를 내 말로 설명하기:
  커밋 기록 위에 붙여 둔 "이름표"이고, 이 이름표를 따라 새 커밋이 쌓인다고 이해했다.
  `git switch` 하면 그 이름표가 가리키는 시점의 파일로 작업 폴더가 바뀌는데, 실습 1에서 `ls` 했을 때 `profile.md` 가 main에서는 안 보이고 `add-profile` 에서만 보여서 확실히 와닿았다.
- fast-forward 와 merge commit 의 차이 (실습 2, 3 경험으로):
  실습 2는 터미널에 `Fast-forward` 만 뜨고 log에 새 커밋이 하나도 안 늘었다. main 뒤에 갈라진 게 없으니 main 이름표만 앞으로 옮긴 것.
  실습 3은 `Merge made by the 'ort' strategy.` 가 뜨면서 커밋이 2개(각 브랜치 1개)가 아니라 merge commit까지 3개가 늘었고, 그래프에 `|\` `|/` 로 갈라졌다 합쳐지는 모양이 생겼다.
- 충돌이 났을 때 `title.md` 에 보인 내용과, 어떻게 해결했는지:
  `git status` 에 `both modified: title.md` 가 떴고, 파일 안에는 `<<<<<<< HEAD` 아래 `제목: Git 놀이터`, `=======` 아래 `제목: 나의 첫 Git 연습장`, 마지막에 `>>>>>>> change-title` 이 있었다.
  VS Code로 열어서 **Accept Incoming** 을 눌러 브랜치 쪽 `제목: 나의 첫 Git 연습장` 을 남겼고, `cat` 으로 표시 줄이 다 지워졌는지 확인한 뒤 `git add` → `git commit` 했다.
- git-mentoring에서 매주 `main` 에서 새 브랜치를 만드는 이유:
  새 브랜치는 "지금 내가 서 있는 커밋"에서 시작한다. week04 브랜치에 있는 채로 `week05-` 를 만들면 4주차 커밋도 같이 들고 가서, PR 하나에 두 주치 파일이 섞인다.
  그래서 `git pull upstream main` 으로 최신 main을 받아 두고 거기서 갈라져야 리뷰하는 사람도 이번 주 변경만 보게 된다.
- 이번 주 소감:
  자율주행 팀에서 여러 명 코드를 합칠 때 충돌 나면 그냥 한쪽 파일을 통째로 덮어쓴 적이 있는데, 이제는 충돌 표시를 보고 줄 단위로 어느 쪽을 남길지 고를 수 있게 됐다. 다음 통합 때 바로 써먹어 볼 생각!
