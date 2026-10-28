# 4주차: 원격 저장소 연결 (remote, push, pull)

## 🎯 학습 목표

- **로컬 저장소**(내 컴퓨터)와 **원격 저장소**(GitHub)의 관계를 이해한다.
- `git remote add` 로 내 로컬 저장소를 GitHub 저장소에 연결할 수 있다.
- `git push` 로 커밋을 올리고, `git pull` 로 GitHub의 변경을 받아올 수 있다.
- 1주차부터 써 온 `origin`, `upstream` 이 무엇이었는지 정확히 설명할 수 있다.

> 💡 이번 주 실습은 3주차까지 커밋을 쌓아 온 **`~/git-practice` 폴더**를 GitHub에 올리는 것입니다.
> 3주차 실습을 못 했다면 [3주차 실습](../week03/README.md)부터 진행하세요. (커밋이 1개 이상 있어야 push할 수 있어요.)

---

## 📚 학습 내용

### 1) 로컬 저장소와 원격 저장소

```
[내 컴퓨터: ~/git-practice]  --git push-->  [GitHub: MY-ID/git-practice]
        로컬 저장소           <--git pull--         원격 저장소
```

- **로컬 저장소** : `git init` 으로 만든, 내 컴퓨터 안의 저장소 (`.git` 폴더)
- **원격 저장소(remote)** : GitHub 같은 서버에 있는 저장소. 다른 사람과 공유하거나 백업할 때 사용
- 하나의 로컬 저장소에 원격 저장소를 **여러 개** 연결할 수 있고, 각각 **이름**을 붙여서 구분합니다.

> 💡 git-mentoring에서 써 온 이름을 떠올려 보세요.
>
> | 이름 | git-mentoring에서 가리키는 곳 |
> |---|---|
> | `origin` | Fork한 **내** 저장소 (`MY-ID/git-mentoring`) |
> | `upstream` | 튜터의 원본 저장소 (`hgeniee/git-mentoring`) |
>
> `origin` 은 "내가 주로 push하는 원격 저장소"에 붙이는 **관례적인 이름**일 뿐, 특별한 명령어가 아닙니다.
> `git clone` 하면 자동으로 `origin` 이 만들어졌고, 이번 주에는 `git init` 한 저장소라서 **직접** 연결합니다.

### 2) 이번 주 명령어

| 명령어 | 의미 |
|---|---|
| `git remote -v` | 연결된 원격 저장소 목록과 주소 보기 |
| `git remote add 이름 주소` | 원격 저장소를 이름을 붙여 연결하기 (예: `git remote add origin https://...`) |
| `git push -u origin main` | 내 `main` 브랜치를 `origin` 에 올리고, 둘을 **짝지어 두기** (처음 한 번만) |
| `git push` | 짝지어 둔 원격 브랜치로 올리기 (`-u` 를 한 뒤부터는 이것만 쳐도 됨) |
| `git pull` | 원격 저장소의 새 커밋을 받아와서 내 브랜치에 합치기 |
| `git log --oneline` | 커밋 기록 보기 (`origin/main` 표시로 원격 저장소 위치도 확인 가능) |

> 💡 `-u` 는 `--set-upstream` 의 줄임말입니다. git-mentoring의 `upstream`(원본 저장소 이름)과는 **다른 뜻**이니 헷갈리지 마세요.
> 여기서는 "내 `main` 은 `origin/main` 과 짝"이라고 기억해 두는 설정입니다.

---

## 🛠️ 실습

모든 실습은 `~/git-practice` 에서 진행합니다. 커밋 메시지는 [커밋 메시지 규칙](../README.md#커밋-메시지-규칙)(`타입: 내용`)을 지켜 주세요.

```bash
cd ~/git-practice
git status            # On branch main 확인
git log --oneline     # 3주차에 만든 커밋들이 보이면 준비 완료
git remote -v         # 아직 아무것도 안 나옴 (연결된 원격 저장소가 없음)
```

### 실습 1. GitHub에 빈 저장소 만들기 (GitHub 웹)

1. GitHub 오른쪽 위 **+** → **New repository**
2. Repository name: **`git-practice`**
3. Public / Private 는 자유롭게 선택
4. ⚠️ **Add a README file, .gitignore, license 는 모두 체크하지 않기** (완전히 빈 저장소로 만들기)
5. **Create repository** 클릭 → 화면에 나오는 HTTPS 주소 확인 (`https://github.com/MY-ID/git-practice.git`)

> 💡 README를 체크하면 GitHub 쪽에 커밋이 하나 생겨서, 내 로컬 기록과 달라져 첫 push가 거절됩니다.
> 실수로 체크했다면 [자주 막히는 부분](#-자주-막히는-부분)을 참고하세요.

### 실습 2. 원격 저장소 연결하기

```bash
git remote add origin https://github.com/MY-ID/git-practice.git
git remote -v
# origin  https://github.com/MY-ID/git-practice.git (fetch)
# origin  https://github.com/MY-ID/git-practice.git (push)
```

### 실습 3. 처음 push 하기

```bash
git push -u origin main
```

GitHub의 `MY-ID/git-practice` 페이지를 새로고침해서 `hello.md`, `commands.md` 가 올라왔는지 확인하세요.
(커밋하지 않은 `memo.md` 는 올라가지 않습니다. **커밋한 것만** push 된다는 걸 확인해 보세요!)

```bash
git log --oneline     # 맨 위 커밋에 (HEAD -> main, origin/main) 이 보이면 성공
```

### 실습 4. 로컬에서 커밋하고 다시 push 하기

```bash
echo "- git push" >> commands.md
git add commands.md
git commit -m "Add: 명령어 목록에 git push 추가"
git status            # Your branch is ahead of 'origin/main' by 1 commit.
git push              # -u 를 해 뒀기 때문에 origin main 생략 가능
git status            # Your branch is up to date with 'origin/main'.
```

> 💡 `ahead of 'origin/main' by 1 commit` = "내 컴퓨터에는 있지만 아직 GitHub에 안 올린 커밋이 1개 있다"는 뜻입니다.

### 실습 5. GitHub에서 수정하고 pull 받기

다른 사람(또는 다른 컴퓨터)이 GitHub에 올린 변경을 받아오는 상황을 연습합니다.

1. GitHub의 `MY-ID/git-practice` 페이지에서 `hello.md` 클릭 → 오른쪽 위 ✏️(Edit) 클릭
2. 맨 아래에 `GitHub 웹에서 추가한 줄` 한 줄 추가
3. **Commit changes...** → Commit message에 `Add: 웹에서 hello.md 수정` 입력 → **Commit changes**

```bash
cat hello.md          # 아직 내 컴퓨터에는 그 줄이 없음
git pull              # GitHub의 새 커밋 받아오기
cat hello.md          # 웹에서 추가한 줄이 보임
git log --oneline     # 웹에서 만든 커밋이 맨 위에 보이면 성공!
```

> 💡 git-mentoring에서 매주 하던 `git pull upstream main` 도 같은 원리입니다.
> "upstream이라는 원격 저장소의 main 브랜치를 받아와서 내 브랜치에 합쳐라"라는 뜻이었어요.

---

## ✏️ 과제

`week04/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

````markdown
# 홍길동

- GitHub ID: MY-ID
- 내 git-practice 저장소 주소: https://github.com/MY-ID/git-practice
- `git remote -v` 결과:
  ```
  (여기에 결과를 붙여 넣기)
  ```
- 실습 5 이후 `git log --oneline` 결과:
  ```
  (여기에 결과를 붙여 넣기)
  ```
- 로컬 저장소와 원격 저장소를 내 말로 설명하기:
- git-mentoring의 `origin` 과 `upstream` 은 각각 어디를 가리키는지:
- `git push -u origin main` 에서 `-u` 를 붙이는 이유:
- `git pull` 이 하는 일:
- 이번 주 소감:
````

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.
>
> 💡 git-practice 저장소를 Private으로 만들었다면 주소는 적되, 튜터에게는 안 보여도 괜찮습니다.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week04-이름` (예: `week04-hong`) |
| 파일 경로 | `week04/members/본인이름.md` (예: `week04/members/홍길동.md`) |
| 커밋 메시지 | `Add: 4주차 홍길동 과제` |
| PR 제목 | `[4주차] 홍길동 과제 제출` |

명령어 순서가 기억나지 않으면 [메인 README의 "매주 과제 제출 흐름"](../README.md#매주-과제-제출-흐름)을 참고하세요.

```bash
cd ~/git-mentoring       # git-practice가 아니라 git-mentoring 폴더로 이동
git switch main
git pull upstream main
git push origin main
git switch -c week04-hong
# week04/members/홍길동.md 작성 후 저장
git add week04/members/홍길동.md
git commit -m "Add: 4주차 홍길동 과제"
git push origin week04-hong
# GitHub에서 Pull Request 생성
```

> 💡 `git-mentoring` 을 홈 폴더가 아닌 다른 곳에 clone했다면 그 경로로 `cd` 하세요.
>
> ⚠️ 새 브랜치는 꼭 **`main` 에서** 만드세요. 지난주 브랜치에 있는 상태로 `git switch -c` 하면 지난주 파일까지 PR에 딸려 갑니다.

---

## ❓ 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| `error: remote origin already exists.` | 이미 `origin` 을 연결해 둠 | `git remote -v` 로 주소 확인. 주소가 틀렸다면 `git remote set-url origin 올바른주소` |
| `error: src refspec main does not match any` | 커밋이 하나도 없거나 브랜치 이름이 `main` 이 아님 | `git log --oneline` 으로 커밋 확인, `git status` 첫 줄의 브랜치 이름 확인 (`master` 라면 `git push -u origin master`) |
| `! [rejected] main -> main (fetch first)` | GitHub 저장소를 만들 때 README를 체크해서 GitHub에 다른 커밋이 있음 | 가장 쉬운 방법: GitHub에서 저장소를 지우고(**Settings** → 맨 아래 **Delete this repository**) README 없이 다시 만든 뒤 실습 3부터 |
| `remote: Repository not found.` | 주소 오타, 또는 저장소를 아직 안 만듦 | GitHub에서 저장소 주소를 다시 복사해서 `git remote set-url origin 주소` |
| `git pull` 후 이상한 편집기 화면이 뜸 | 로컬과 GitHub 양쪽에 서로 다른 새 커밋이 있어서 합치는 커밋(merge commit) 메시지를 묻는 화면 | 그대로 저장하고 닫기 (vim이면 `:wq` 입력 후 Enter) |

---

## ✅ 제출 체크리스트

- [ ] GitHub에 README 없이 빈 `git-practice` 저장소를 만들었다
- [ ] `git remote add origin` 으로 연결하고 `git remote -v` 로 확인했다
- [ ] `git push -u origin main` 으로 처음 push 하고 GitHub에서 파일을 확인했다
- [ ] 로컬에서 커밋을 하나 더 만들어 `git push` 했다 (실습 4)
- [ ] GitHub 웹에서 수정한 내용을 `git pull` 로 받아왔다 (실습 5)
- [ ] `main` 에서 만든 `week04-이름` 브랜치에서 `week04/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 커밋 메시지 규칙(`타입: 내용`)을 지켰다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
