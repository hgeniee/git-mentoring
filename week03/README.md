# 3주차: Git 기본 명령어 (init, add, commit)

## 🎯 학습 목표

- Git의 세 영역 **working directory → staging area → repository** 를 이해한다.
- `git status` 와 `git diff` 로 **지금 무엇이 바뀌었는지** 스스로 확인할 수 있다.
- `add` 와 `commit` 이 왜 두 단계로 나뉘어 있는지 직접 경험한다.
- 실수한 변경을 `git restore` 로 되돌릴 수 있다.

> 💡 이번 주 실습은 2주차에 `git init` 으로 만든 **`~/git-practice` 폴더**에서 진행합니다.
> 여기서 쌓은 커밋 기록은 다음 주에 GitHub에 올릴 예정이니 폴더를 지우지 마세요!
> 2주차 실습을 못 했다면 [2주차 7) 실습](../week02/README.md#7-실습-폴더에서-첫-저장소-만들기-git-init)부터 진행하세요.

---

## 📚 학습 내용

### 1) Git의 세 영역

```
[working directory]  --git add-->  [staging area]  --git commit-->  [repository]
   내가 파일을 수정하는 곳          다음 커밋에 넣을 것을 모아 두는 곳      커밋(기록)이 저장되는 곳 (.git)
```

> 💡 택배로 비유하면: 물건을 고르고(수정) → 상자에 담고(`add`) → 송장을 붙여 보내기(`commit`).
> 상자에 담기 전까지는 얼마든지 넣고 뺄 수 있습니다.

### 2) 이번 주 명령어

| 명령어 | 의미 |
|---|---|
| `git status` | 파일들이 지금 어느 영역에 있는지 확인 (가장 자주 쓰는 명령어!) |
| `git add 파일` | 파일을 staging area에 올리기 |
| `git commit -m "메시지"` | staging area에 있는 내용을 하나의 기록으로 저장 |
| `git diff` | 수정했지만 **아직 add 하지 않은** 변경 내용 보기 |
| `git diff --staged` | **add 했지만 아직 commit 하지 않은** 변경 내용 보기 |
| `git log --oneline` | 커밋 기록을 한 줄씩 보기 |
| `git restore 파일` | 수정한 내용을 버리고 마지막 커밋 상태로 되돌리기 |
| `git restore --staged 파일` | add를 취소하기 (수정 내용은 그대로 남음) |

> ⚠️ `git restore 파일` 로 버린 수정 내용은 **되살릴 수 없습니다.** 실행 전에 `git diff` 로 꼭 확인하세요.
>
> 💡 `git diff`, `git log` 화면에서 빠져나올 때는 `q` 를 누르세요.

---

## 🛠️ 실습

모든 실습은 `~/git-practice` 에서 진행합니다. 커밋 메시지도 [커밋 메시지 규칙](../README.md#커밋-메시지-규칙)(`타입: 내용`)을 지켜 주세요.

```bash
cd ~/git-practice
git status          # On branch main / No commits yet 이 보이면 준비 완료
```

> 💡 파일은 VS Code, 메모장 등 편한 에디터로 만들고 수정해도 됩니다. 아래의 `echo` 명령어는 터미널에서 바로 파일에 한 줄을 쓰는 방법입니다.
>
> 💡 Windows에서 `warning: ... LF will be replaced by CRLF` 가 보여도 에러가 아니니 무시하고 진행하세요. (운영체제마다 줄바꿈 문자가 달라서 Git이 알려 주는 안내입니다.)

### 실습 1. 첫 커밋 — 파일이 영역을 이동하는 모습 보기

```bash
echo "# Git 연습장" > hello.md
git status                    # Untracked files: hello.md (Git이 아직 모르는 파일)
git add hello.md
git status                    # Changes to be committed: (staging area에 올라감)
git commit -m "Add: hello.md 추가"
git status                    # nothing to commit, working tree clean
```

### 실습 2. 수정하고 차이 확인하기

```bash
echo "오늘은 3주차 실습을 했다." >> hello.md
git status                    # Changes not staged for commit: modified: hello.md
git diff                      # + 로 표시된 줄이 추가된 내용
git add hello.md
git diff                      # 아무것도 안 나옴 (이미 add 했으니까)
git diff --staged             # 여기서 보임
git commit -m "Add: hello.md에 실습 기록 추가"
```

### 실습 3. 두 파일 중 하나만 커밋하기 — staging이 필요한 이유

```bash
echo "- git status" > commands.md
echo "아직 정리 중인 메모" > memo.md
git status                    # 두 파일 모두 Untracked
git add commands.md           # 하나만 add
git status                    # commands.md 는 staged, memo.md 는 여전히 untracked
git commit -m "Add: 배운 명령어 목록 추가"
```

> 💡 수정한 파일이 여러 개여도 **완성된 것만 골라서** 하나의 커밋으로 묶을 수 있습니다.
> 이것이 `add` 와 `commit` 이 나뉘어 있는 이유입니다. `memo.md` 는 커밋하지 않은 채로 둬도 됩니다.

### 실습 4. 실수 되돌리기

```bash
echo "실수로 쓴 내용!!!" >> hello.md
git diff                      # 실수한 내용 확인
git restore hello.md          # 수정 내용 버리기
git diff                      # 아무것도 안 나옴 → 마지막 커밋 상태로 돌아옴

echo "- git restore" >> commands.md
git add commands.md
git restore --staged commands.md   # add 취소
git status                    # 다시 Changes not staged (수정 내용은 남아 있음)
```

마지막에 남은 `commands.md` 수정 내용은 자유롭게 커밋하거나 `git restore` 로 버리세요.

### 실습 5. 기록 확인하기

```bash
git log --oneline             # 커밋이 3개 이상 보이면 성공!
```

---

## ✏️ 과제

`week03/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

````markdown
# 홍길동

- GitHub ID: MY-ID
- git-practice의 `git log --oneline` 결과 (3개 이상):
  ```
  (여기에 결과를 붙여 넣기)
  ```
- working directory / staging area / repository를 내 말로 설명하기:
- `add` 와 `commit` 을 나눠 놓은 이유 (실습 3 경험으로):
- `git diff` 와 `git diff --staged` 의 차이:
- `git restore` 를 써 본 상황:
- 이번 주 소감:
````

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.
>
> 💡 `git-practice` 는 git-mentoring과 **별개의 저장소**입니다. 과제 파일에는 `git log` 결과만 복사해서 붙여 넣으세요.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week03-이름` (예: `week03-hong`) |
| 파일 경로 | `week03/members/본인이름.md` (예: `week03/members/홍길동.md`) |
| 커밋 메시지 | `Add: 3주차 홍길동 과제` |
| PR 제목 | `[3주차] 홍길동 과제 제출` |

명령어 순서가 기억나지 않으면 [메인 README의 "매주 과제 제출 흐름"](../README.md#매주-과제-제출-흐름)을 참고하세요.

```bash
cd ~/git-mentoring       # git-practice가 아니라 git-mentoring 폴더로 이동
git switch main
git pull upstream main
git push origin main
git switch -c week03-hong
# week03/members/홍길동.md 작성 후 저장
git add week03/members/홍길동.md
git commit -m "Add: 3주차 홍길동 과제"
git push origin week03-hong
# GitHub에서 Pull Request 생성
```

> 💡 `git-mentoring` 을 홈 폴더가 아닌 다른 곳에 clone했다면 그 경로로 `cd` 하세요.

---

## ✅ 제출 체크리스트

- [ ] `~/git-practice` 에서 실습 1~5를 진행했다
- [ ] `git log --oneline` 에 커밋이 3개 이상 있고, 모두 `타입: 내용` 규칙을 지켰다
- [ ] 두 파일 중 하나만 골라 커밋해 봤다 (실습 3)
- [ ] `git restore` 와 `git restore --staged` 를 써 봤다 (실습 4)
- [ ] `week03-이름` 브랜치에서 `week03/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
