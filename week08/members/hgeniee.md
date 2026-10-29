# 이현진 (튜터 예시)

- GitHub ID: hgeniee
- 실습 3에서 push가 거절될 때 나온 메시지 (첫 줄):
  `! [rejected]        main -> main (fetch first)`
- 실습 3에서 `git status` 에 나온 메시지:
  `Your branch and 'origin/main' have diverged, and have 1 and 1 different commits each, respectively.`
- 실습 4 이후 `git log --oneline --graph -n 5` 결과:
  ```
  *   f9f8d5b (HEAD -> main, origin/main) Fix: title.md 충돌 해결
  |\
  | * be1a2a8 Fix: 친구가 제목 변경
  * | 351a568 Fix: 내가 제목 변경
  |/
  * f57f3e0 Revert "Add: 실수로 추가한 줄"
  ```
- push가 거절된 이유를 내 말로 설명하기:
  친구가 먼저 올린 커밋을 나는 모르는 상태였다. GitHub가 내 push를 그대로 받아 주면 친구의 커밋이 사라지니까,
  "먼저 친구 것을 받아서 합친 다음 다시 올려라"라고 거절한 것이다.
- `git fetch` 와 `git pull` 의 차이:
  `fetch` 는 GitHub의 새 커밋을 받아서 `origin/main` 만 옮겨 두고 내 파일은 건드리지 않는다.
  `pull` 은 fetch 후 내 브랜치에 merge까지 한다. 그래서 충돌은 `pull` 할 때 난다.
- git-mentoring에서 "본인 파일만 만들기" 규칙이 있는 이유:
  여러 명이 같은 파일의 같은 줄을 고치면 오늘처럼 충돌이 난다. 각자 다른 파일을 만들면 Git이 알아서 합쳐 주니까 매주 PR이 충돌 없이 Merge될 수 있었다.
- 이번 주 소감:
  혼자 두 사람 역할을 해 보면 "협업에서 왜 pull을 자주 하라는지" 몸으로 느낄 수 있어요. 이제 진짜 팀 프로젝트도 할 수 있습니다!
