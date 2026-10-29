# 이현진 (튜터 예시)

- GitHub ID: hgeniee
- 실습 3 이후 `git log --oneline -n 5` 결과:
  ```
  f57f3e0 (HEAD -> main, origin/main) Revert "Add: 실수로 추가한 줄"
  83f43c7 Add: 실수로 추가한 줄
  bd1120a Add: 명령어 목록에 git revert 추가
  e79d83f Add: .gitignore 추가
  e81c4d0 Fix: title.md 충돌 해결
  ```
- 내 `.gitignore` 내용:
  ```
  memo.md
  *.log
  ```
- `.gitignore` 에 꼭 넣어야 할 파일의 예와 이유:
  API 키나 토큰이 들어 있는 `.env` 파일. 한 번 GitHub에 올라가면 기록에 남아서 누구나 볼 수 있기 때문에, 처음부터 Git이 모르게 해야 한다.
- amend 전후로 바뀐 것과 바뀌지 않은 것:
  커밋 메시지(`revrt` → `revert`)와 해시(`dca080c` → `bd1120a`)가 바뀌었고, 커밋 개수와 파일 내용은 그대로였다.
  해시가 바뀐 걸 보고 amend가 "고치기"가 아니라 "바꿔치기"라는 걸 알았다.
- push한 커밋에 amend 대신 revert 를 쓰는 이유:
  amend는 기록을 바꿔서 GitHub에 있는 기록과 내 기록이 달라지지만, revert는 "취소 커밋"을 하나 더 쌓을 뿐이라 기록이 그대로 이어진다.
  다른 사람이 이미 그 커밋을 받아 갔어도 문제가 생기지 않는다.
- 지금까지 배운 되돌리기 방법 중 가장 유용할 것 같은 것:
  `git restore`. 커밋하기 전에 "아 이거 아닌데" 싶을 때가 제일 많아서. 단, 실행 전에 `git diff` 로 꼭 확인!
- 이번 주 소감:
  Git의 좋은 점은 "되돌릴 수 있다"는 안심이에요. 이제 실수해도 고칠 방법을 알았으니 더 과감하게 실험해 봐요!
