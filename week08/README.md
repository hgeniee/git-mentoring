# 8주차: 협업 시뮬레이션 (push 거절, fetch, pull 충돌 해결)

## 🎯 학습 목표

- 두 사람이 같은 저장소에 push할 때 **push가 거절되는 이유**를 이해한다.
- `git fetch` 와 `git pull` 의 차이를 이해한다.
- `git pull` 중에 생긴 충돌을 해결하고 다시 push할 수 있다.
- git-mentoring PR에 **"This branch has conflicts"** 가 떴을 때 스스로 해결할 수 있다.

> 💡 이번 주에는 **혼자서 두 사람 역할**을 합니다. `~/git-practice`(나)와, 같은 저장소를 하나 더 clone한 `~/git-practice-friend`(친구)를 번갈아 오가며 실습해요.
> 5주차에는 **내 컴퓨터 안의 두 브랜치**가 부딪혔다면, 이번 주에는 **GitHub를 사이에 둔 두 사람**이 부딪힙니다.

---

## 📚 학습 내용

### 1) push가 거절되는 이유

```
            친구가 먼저 push한 커밋
                   v
GitHub:   1---2---F
               \
나:             M        ← 나는 F를 모르는 채로 M을 만듦
```

GitHub는 내 push를 받아 주면 친구의 커밋 `F` 가 사라지기 때문에 **거절**합니다.

```
! [rejected]        main -> main (fetch first)
hint: Updates were rejected because the remote contains work that you do not have locally.
```

**해결:** 먼저 `git pull` 로 친구의 커밋을 받아서 내 커밋과 합친 뒤, 다시 push 합니다.

### 2) `fetch` 와 `pull`

| 명령어 | 하는 일 |
|---|---|
| `git fetch` | GitHub의 새 커밋을 **받아 오기만** 함. 내 파일은 그대로 (`origin/main` 만 업데이트) |
| `git pull` | `git fetch` + `git merge` . 받아 와서 **내 브랜치에 합치기**까지 함 |

> 💡 `fetch` 는 "택배가 왔는지 확인하고 문 앞에 두기", `pull` 은 "택배를 열어서 정리까지 하기"입니다.
> 무슨 변경이 왔는지 먼저 보고 싶을 때 `fetch` → `git log --oneline --graph --all` 로 확인한 뒤 `pull` 하면 안전해요.

### 3) 이번 주 명령어

| 명령어 | 의미 |
|---|---|
| `git clone 주소 폴더이름` | 저장소를 원하는 폴더 이름으로 clone |
| `git fetch` | 원격 저장소의 새 커밋을 받아 오기만 하기 |
| `git status` | `have diverged` = 나와 GitHub 양쪽에 서로 모르는 커밋이 있음 |
| `git pull` | 받아 와서 합치기 (충돌이 나면 5주차처럼 해결) |
| `git log --oneline --graph --all` | 내 `main` 과 `origin/main` 의 위치를 그림으로 확인 |

---

## 🛠️ 실습

### 준비. pull 설정 한 번 해 두기

```bash
git config --global pull.rebase false
```

> 💡 `git pull` 이 합칠 때 **merge 방식**(5주차에 배운 방법)을 쓰라는 설정입니다.
> macOS 등에서 이 설정이 없으면 `fatal: Need to specify how to reconcile divergent branches` 에러가 날 수 있어요. (Windows의 Git for Windows는 보통 이미 설정되어 있음)

### 실습 1. 친구 역할 폴더 만들기

```bash
cd ~
git clone https://github.com/MY-ID/git-practice.git git-practice-friend
cd git-practice-friend
git log --oneline -n 3        # ~/git-practice 와 같은 기록이 보임
```

> ⚠️ `~/git-practice` **안에서** clone하지 마세요. 반드시 `cd ~` 로 나온 뒤 clone합니다.
>
> 💡 지금부터 터미널 창(탭)을 **2개** 열어서, 하나는 `~/git-practice`(나), 하나는 `~/git-practice-friend`(친구)로 쓰면 편합니다.

### 실습 2. 친구가 먼저 push 하기

**친구 창** (`~/git-practice-friend`):

```bash
echo "제목: 친구가 바꾼 제목" > title.md
git add title.md
git commit -m "Fix: 친구가 제목 변경"
git push
```

### 실습 3. 나도 push 하려다 거절당하기

**나 창** (`~/git-practice`):

```bash
cd ~/git-practice
echo "제목: 내가 바꾼 제목" > title.md
git add title.md
git commit -m "Fix: 내가 제목 변경"
git push
# ! [rejected]        main -> main (fetch first)  ← 거절!
```

`fetch` 로 무슨 일이 있었는지 먼저 확인합니다.

```bash
git fetch
git status
# Your branch and 'origin/main' have diverged,
# and have 1 and 1 different commits each, respectively.
git log --oneline --graph --all     # 내 main 과 origin/main 이 갈라진 모습
```

### 실습 4. pull 하고 충돌 해결하기

```bash
git pull
# CONFLICT (content): Merge conflict in title.md
cat title.md
# <<<<<<< HEAD
# 제목: 내가 바꾼 제목
# =======
# 제목: 친구가 바꾼 제목
# >>>>>>> 5a2f7b9...(친구 커밋의 해시)
```

> 💡 5주차와 달리 `>>>>>>>` 뒤에 브랜치 이름 대신 **커밋 해시**가 보입니다. 친구가 GitHub에 올린 커밋이라는 뜻이에요.

`title.md` 를 에디터로 열어 최종 내용 한 줄만 남기고 충돌 표시를 지웁니다. (예: `제목: 친구와 내가 함께 정한 제목`)

```bash
cat title.md                          # 충돌 표시가 하나도 없는지 확인!
git add title.md
git commit -m "Fix: title.md 충돌 해결"
git push                              # 이번에는 성공!
git log --oneline --graph -n 5        # 두 갈래가 합쳐진 모습
```

### 실습 5. 친구도 최신으로 맞추기

**친구 창** (`~/git-practice-friend`):

```bash
git pull                  # "Fast-forward" — 친구는 새 커밋이 없어서 그대로 따라감
cat title.md              # 해결된 제목이 보임
```

> 💡 실습이 끝나면 `~/git-practice-friend` 폴더는 지워도 됩니다. (GitHub와 `~/git-practice` 에는 영향 없음)

### 실습 6. git-mentoring PR에 충돌이 났을 때 (읽어 두기)

PR 화면에 **"This branch has conflicts that must be resolved"** 가 보이면, 원본(upstream)의 `main` 이 바뀌어서 내 브랜치와 부딪힌 것입니다. 지금까지는 튜터가 정리했지만, 이제는 직접 해결할 수 있어요.

```bash
cd ~/git-mentoring
git switch weekXX-이름              # PR을 보낸 브랜치로 이동
git pull upstream main              # 원본의 최신 main을 내 브랜치에 합치기 → 충돌 발생
# 충돌 파일을 열어 표시를 지우고 저장
git add 충돌난파일
git commit -m "Fix: upstream main 충돌 해결"
git push origin weekXX-이름          # PR에 자동 반영 → 충돌 메시지가 사라짐
```

> 💡 각자 **본인 파일만** 만드는 규칙 덕분에 git-mentoring에서는 충돌이 거의 안 납니다. 이 규칙이 왜 있었는지 이제 이해되죠?

---

## ✏️ 과제

`week08/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

````markdown
# 홍길동

- GitHub ID: MY-ID
- 실습 3에서 push가 거절될 때 나온 메시지 (첫 줄):
- 실습 3에서 `git status` 에 나온 메시지:
- 실습 4 이후 `git log --oneline --graph -n 5` 결과:
  ```
  (여기에 결과를 붙여 넣기)
  ```
- push가 거절된 이유를 내 말로 설명하기:
- `git fetch` 와 `git pull` 의 차이:
- git-mentoring에서 "본인 파일만 만들기" 규칙이 있는 이유:
- 이번 주 소감:
````

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week08-이름` (예: `week08-hong`) |
| 파일 경로 | `week08/members/본인이름.md` (예: `week08/members/홍길동.md`) |
| 커밋 메시지 | `Add: 8주차 홍길동 과제` |
| PR 제목 | `[8주차] 홍길동 과제 제출` |

```bash
cd ~/git-mentoring
git switch main
git pull upstream main
git push origin main
git switch -c week08-hong
# week08/members/홍길동.md 작성 후 저장
git add week08/members/홍길동.md
git commit -m "Add: 8주차 홍길동 과제"
git push origin week08-hong
# GitHub에서 Pull Request 생성
```

---

## ❓ 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| `fatal: Need to specify how to reconcile divergent branches` | pull 방식 설정이 없음 | [준비](#준비-pull-설정-한-번-해-두기)의 `git config --global pull.rebase false` 실행 후 다시 `git pull` |
| `fatal: destination path 'git-practice-friend' already exists` | 같은 이름 폴더가 이미 있음 | 다른 이름으로 clone하거나, 예전 폴더를 지우고 다시 |
| 친구 창에서 push하는데 로그인을 다시 물어봄 | 정상. 같은 계정으로 로그인하면 됨 | 2주차 PAT 안내 참고 |
| `git pull` 후 편집기가 열림 | 충돌 없이 자동으로 합쳐져서 merge commit 메시지를 물어봄 | 그대로 저장하고 닫기 (vim이면 `:wq` 입력 후 Enter) |
| `error: Pulling is not possible because you have unmerged files.` | 이전 충돌을 아직 해결하지 않음 | 충돌 파일 수정 → `git add` → `git commit` 으로 먼저 마무리 |
| 충돌 해결 후 push했는데 또 거절됨 | 그 사이 친구 창에서 또 push함 | 다시 `git pull` → (충돌 시 해결) → `git push` |

---

## ✅ 제출 체크리스트

- [ ] `git config --global pull.rebase false` 를 설정했다
- [ ] `~/git-practice-friend` 로 같은 저장소를 하나 더 clone했다 (실습 1)
- [ ] 친구 역할로 먼저 push하고, 내 쪽 push가 거절되는 것을 확인했다 (실습 2, 3)
- [ ] `git fetch` 와 `git status` 로 갈라진 상태를 확인했다 (실습 3)
- [ ] `git pull` 충돌을 해결하고 push에 성공했다 (실습 4)
- [ ] 친구 쪽에서 `git pull` 로 최신 상태를 받았다 (실습 5)
- [ ] `main` 에서 만든 `week08-이름` 브랜치에서 `week08/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
