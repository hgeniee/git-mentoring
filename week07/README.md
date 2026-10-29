# 7주차: 되돌리기와 기록 관리 (.gitignore, amend, revert)

## 🎯 학습 목표

- `.gitignore` 로 **Git이 신경 쓰지 않을 파일**을 정할 수 있다.
- 방금 한 커밋의 메시지를 `git commit --amend` 로 고칠 수 있다.
- 이미 push한 커밋을 `git revert` 로 **안전하게** 되돌릴 수 있다.
- 상황에 따라 `restore` / `amend` / `revert` 중 무엇을 쓸지 고를 수 있다.

> 💡 이번 주 실습도 **`~/git-practice` 폴더**에서 진행합니다. (4주차에 GitHub와 연결해 둔 상태)
> 시작하기 전에 `git status` 가 `working tree clean`, `git log --oneline` 에 커밋이 여러 개 보이는지 확인하세요.

---

## 📚 학습 내용

### 1) `.gitignore`

저장소 맨 위 폴더에 `.gitignore` 라는 파일을 만들고, **무시할 파일 이름이나 패턴**을 한 줄에 하나씩 적습니다.

```
# 이 파일 하나 무시
memo.md
# .log 로 끝나는 모든 파일 무시
*.log
# secret 폴더 전체 무시
secret/
```

> 💡 `#` 으로 시작하는 줄은 설명(주석)입니다. 주석은 **반드시 줄 맨 앞**에 써야 해요. `memo.md # 설명` 처럼 뒤에 붙이면 패턴의 일부로 읽힙니다.

- 비밀번호·토큰(PAT)이 든 파일, 자동으로 생기는 파일(`.DS_Store`, `node_modules/` 등), 개인 메모처럼 **올리면 안 되거나 올릴 필요가 없는 파일**을 적습니다.
- `.gitignore` 파일 자체는 **커밋해서 함께 공유**합니다.

> ⚠️ `.gitignore` 는 **아직 커밋하지 않은 파일**에만 효과가 있습니다. 이미 커밋해서 GitHub에 올라간 비밀번호는 `.gitignore` 에 적어도 기록에 남아 있어요.
> 토큰을 실수로 올렸다면 **즉시 GitHub에서 그 토큰을 삭제(revoke)** 하고 새로 발급하세요.

### 2) 되돌리기 도구 비교

| 상황 | 쓰는 명령어 | 결과 |
|---|---|---|
| 수정했는데 아직 add/commit 안 함 | `git restore 파일` (3주차) | 마지막 커밋 상태로 되돌림 |
| add만 취소하고 싶음 | `git restore --staged 파일` (3주차) | 수정 내용은 남고 add만 취소 |
| **방금** 한 커밋의 메시지를 고치고 싶음 (push 전) | `git commit --amend -m "새 메시지"` | 마지막 커밋을 **새 커밋으로 바꿔치기** |
| 이미 **push한** 커밋을 취소하고 싶음 | `git revert 커밋` | 그 커밋을 거꾸로 되돌리는 **새 커밋**을 추가 |

> ⚠️ `amend` 는 커밋을 바꿔치기하기 때문에 **push한 커밋에는 쓰지 마세요.** GitHub의 기록과 내 기록이 달라져 push가 거절됩니다.
> push한 커밋은 기록을 지우지 않고 "취소 커밋"을 쌓는 `revert` 로 되돌립니다.
>
> 💡 인터넷에서 `git reset --hard` 를 보게 되면 조심하세요. 기록과 수정 내용을 **되살릴 수 없게 지울 수 있는** 명령어라 이 멘토링에서는 다루지 않습니다.

### 3) 이번 주 명령어

| 명령어 | 의미 |
|---|---|
| `git status --ignored` | 무시되고 있는 파일까지 보기 |
| `git commit --amend -m "메시지"` | 마지막 커밋 메시지 고치기 (push 전에만!) |
| `git revert HEAD` | 가장 최근 커밋을 되돌리는 새 커밋 만들기 |
| `git revert 커밋해시` | 특정 커밋을 되돌리는 새 커밋 만들기 |
| `git show 커밋해시` | 그 커밋에서 무엇이 바뀌었는지 보기 |
| `git log --oneline -n 5` | 최근 커밋 5개만 보기 |

> 💡 `HEAD` 는 "지금 내가 있는 브랜치의 가장 최근 커밋"을 가리키는 이름입니다.

---

## 🛠️ 실습

모든 실습은 `~/git-practice` 에서 진행합니다.

```bash
cd ~/git-practice
git status            # working tree clean 인지 확인 (memo.md 는 Untracked 로 보여도 OK)
```

### 실습 1. `.gitignore` 만들기

3주차부터 커밋하지 않고 계속 따라다니던 `memo.md`, 이제 Git에게 "신경 쓰지 마"라고 알려 줍니다.

```bash
echo "에러 기록" > debug.log           # 무시할 파일 하나 더 만들기
git status                            # memo.md, debug.log 가 Untracked 로 보임

echo "memo.md" > .gitignore
echo "*.log" >> .gitignore
git status                            # memo.md, debug.log 는 사라지고 .gitignore 만 보임!
git status --ignored                  # 무시되는 파일 목록 확인

git add .gitignore
git commit -m "Add: .gitignore 추가"
```

> 💡 `.gitignore` 처럼 이름이 `.` 으로 시작하는 파일은 숨김 파일이라 `ls` 로는 안 보이고 `ls -a` 로 보입니다.

### 실습 2. 커밋 메시지 고치기 (`--amend`)

일부러 오타가 있는 커밋을 만들고 고쳐 봅니다.

```bash
echo "- git revert" >> commands.md
git add commands.md
git commit -m "Add: 명령어 목록에 git revrt 추가"     # 오타!
git log --oneline -n 3                                # 해시와 메시지를 기억해 두기

git commit --amend -m "Add: 명령어 목록에 git revert 추가"
git log --oneline -n 3                                # 커밋 개수는 그대로, 메시지와 해시가 바뀜
git push                                              # 고친 뒤에 push
```

> 💡 해시가 바뀐 것에 주목하세요. amend는 커밋을 "수정"하는 게 아니라 **새 커밋으로 바꿔치기**하는 것입니다.

### 실습 3. push한 커밋 되돌리기 (`revert`)

```bash
echo "이 줄은 실수로 올린 내용" >> hello.md
git add hello.md
git commit -m "Add: 실수로 추가한 줄"
git push                                  # GitHub에서 hello.md 에 실수한 줄이 보임

git revert HEAD --no-edit                 # 방금 커밋을 되돌리는 새 커밋 만들기
cat hello.md                              # 실수한 줄이 사라짐
git log --oneline -n 3
# 1a2b3c4 Revert "Add: 실수로 추가한 줄"
# 5d6e7f8 Add: 실수로 추가한 줄            ← 기록은 그대로 남아 있음
git push                                  # 되돌린 결과도 GitHub에 올리기
```

> 💡 `Revert "..."` 커밋 메시지는 Git이 자동으로 만들어 주는 형식이라, 이번만 `타입: 내용` 규칙의 예외로 둡니다.
> `--no-edit` 을 빼면 메시지를 고칠 수 있는 편집기가 열립니다. (vim이면 `:wq` 입력 후 Enter)

### 실습 4. 커밋 들여다보기

```bash
git log --oneline -n 5
git show HEAD                 # 가장 최근 커밋(revert)의 변경 내용: - 로 지워진 줄
git show HEAD~1               # 그 전 커밋의 변경 내용: + 로 추가된 줄
```

> 💡 `HEAD~1` 은 "HEAD에서 하나 전 커밋"이라는 뜻입니다. 화면에서 나올 때는 `q`.

---

## ✏️ 과제

`week07/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

````markdown
# 홍길동

- GitHub ID: MY-ID
- 실습 3 이후 `git log --oneline -n 5` 결과:
  ```
  (여기에 결과를 붙여 넣기)
  ```
- 내 `.gitignore` 내용:
  ```
  (여기에 붙여 넣기)
  ```
- `.gitignore` 에 꼭 넣어야 할 파일의 예와 이유:
- amend 전후로 바뀐 것과 바뀌지 않은 것:
- push한 커밋에 amend 대신 revert 를 쓰는 이유:
- 지금까지 배운 되돌리기 방법 중 가장 유용할 것 같은 것:
- 이번 주 소감:
````

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week07-이름` (예: `week07-hong`) |
| 파일 경로 | `week07/members/본인이름.md` (예: `week07/members/홍길동.md`) |
| 커밋 메시지 | `Add: 7주차 홍길동 과제` |
| PR 제목 | `[7주차] 홍길동 과제 제출` |

```bash
cd ~/git-mentoring       # git-practice가 아니라 git-mentoring 폴더로 이동
git switch main
git pull upstream main
git push origin main
git switch -c week07-hong
# week07/members/홍길동.md 작성 후 저장
git add week07/members/홍길동.md
git commit -m "Add: 7주차 홍길동 과제"
git push origin week07-hong
# GitHub에서 Pull Request 생성
```

> 💡 PR을 보낸 뒤 커밋 메시지 오타를 발견했다면? 이미 push했으니 amend 하지 말고 그대로 두세요. 내용 수정은 `Fix:` 커밋으로!

---

## ❓ 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| `.gitignore` 에 적었는데 계속 `modified` 로 보임 | 이미 커밋된 파일이라 `.gitignore` 효과가 없음 | 이번 실습 범위 밖이에요. Issues에 질문 남겨 주세요 |
| `.gitignore` 가 안 먹힘 | 파일 이름 오타(`.gitignore.txt` 등), 또는 저장소 맨 위 폴더가 아닌 곳에 만듦 | `ls -a` 로 이름과 위치 확인 |
| amend 후 push 하니 `! [rejected] ... (non-fast-forward)` | **push한 커밋**을 amend 함 | 실습 2는 push **전에** amend 하는 순서예요. 이미 그렇게 됐다면 Issues에 질문해 주세요 (혼자 `--force` 쓰지 않기) |
| `git revert` 후 편집기가 열림 | `--no-edit` 을 빼고 실행함 | 그대로 저장하고 닫기 (vim이면 `:wq` 입력 후 Enter) |
| `git show` 화면에서 안 나가짐 | 결과가 길어서 페이지 화면이 열림 | `q` 누르기 |

---

## ✅ 제출 체크리스트

- [ ] `.gitignore` 를 만들어 `memo.md`, `*.log` 가 무시되는 것을 확인하고 commit 했다 (실습 1)
- [ ] 오타 커밋을 `--amend` 로 고친 뒤 push 했다 (실습 2)
- [ ] push한 커밋을 `git revert` 로 되돌리고 push 했다 (실습 3)
- [ ] `git show` 로 커밋 내용을 확인했다 (실습 4)
- [ ] `main` 에서 만든 `week07-이름` 브랜치에서 `week07/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 커밋 메시지 규칙(`타입: 내용`)을 지켰다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
