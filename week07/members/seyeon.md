# 김세연

- GitHub ID: gseyeon74
- 실습 3 이후 `git log --oneline -n 5` 결과:
  ```
  8ab7edc (HEAD -> main, origin/main) Revert "Add: 실수로 추가한 줄"
  ead7ae9 Add: 실수로 추가한 줄
  6a98fd0 Add: 명령어 목록에 git revert 추가
  de4f46f Add: .gitignore 추가
  b095771 Fix: title.md 충돌 해결
  ```
- 내 `.gitignore` 내용:
  ```
  memo.md
  *.log
  ```
- `.gitignore` 에 꼭 넣어야 할 파일의 예와 이유:
  GitHub PAT 같은 토큰이나 비밀번호가 적힌 `.env` 파일. 한 번 커밋해서 올라가면 나중에 지워도 기록에 남아 있기 때문에 처음부터 Git이 추적하지 않게 해야 한다.
  그 밖에 `*.log` 처럼 실행할 때마다 자동으로 생기는 파일도 올릴 필요가 없어서 넣어 두면 `git status` 가 깔끔해진다.
- amend 전후로 바뀐 것과 바뀌지 않은 것:
  커밋 메시지(`revrt` → `revert`)와 해시(`5b1145a` → `6a98fd0`)는 바뀌었고, 커밋 개수와 `commands.md` 에 추가한 내용은 그대로였다.
  해시가 바뀐 걸 보고 amend는 원래 커밋을 고치는 게 아니라 새 커밋으로 바꿔치기한다는 걸 알았다.
- push한 커밋에 amend 대신 revert 를 쓰는 이유:
  amend는 기록 자체를 바꾸기 때문에 GitHub에 이미 올라간 기록과 내 기록이 달라져 push가 거절된다.
  revert는 기존 커밋을 그대로 두고 그걸 거꾸로 되돌리는 새 커밋을 쌓는 거라, 다른 사람이 이미 받아 간 기록과도 충돌하지 않는다.
- 지금까지 배운 되돌리기 방법 중 가장 유용할 것 같은 것:
  `git revert`. 실수는 대부분 push하고 나서야 발견하게 되는데, 기록을 지우지 않고 안전하게 되돌릴 수 있어서 협업할 때 가장 마음이 편할 것 같다.
- 이번 주 소감:
  실습 3에서 `git revert HEAD --no-edit -q` 처럼 옵션을 하나 더 붙였다가 usage 에러가 나서, 명령어마다 쓸 수 있는 옵션이 다르다는 걸 직접 겪었다.
  `git show` 로 `+` 로 추가된 줄과 `-` 로 지워진 줄을 나란히 비교해 보니 revert가 정확히 반대 작업을 한다는 게 눈에 보여서 이해가 잘 됐다.
