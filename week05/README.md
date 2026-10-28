# 5주차: 브랜치와 병합 (branch, switch, merge, 충돌 해결)

## 🎯 학습 목표

- **브랜치**가 무엇이고 왜 쓰는지 이해한다.
- `git branch`, `git switch` 로 브랜치를 만들고 오갈 수 있다.
- `git merge` 로 브랜치를 합치고, **fast-forward** 와 **merge commit** 의 차이를 이해한다.
- **충돌(conflict)** 이 왜 생기는지 이해하고, 직접 해결할 수 있다.

> 💡 이번 주 실습도 **`~/git-practice` 폴더**에서 진행합니다. 4주차에 GitHub와 연결해 뒀다면 마지막에 push까지 해 봅니다.
> 4주차 실습을 못 했다면 [4주차](../week04/README.md)부터 진행하세요. (push 단계만 빼면 이번 주 실습은 GitHub 연결 없이도 할 수 있어요.)

---

## 📚 학습 내용

### 1) 브랜치란?

브랜치는 **원래 작업(main)에 영향을 주지 않고 따로 작업할 수 있는 갈래**입니다.

```
           A---B   ← add-profile 브랜치 (새 기능 작업)
          /
  1---2---3        ← main 브랜치 (안정된 버전)
```

- 새 기능이나 실험은 브랜치에서 하고, 완성되면 `main` 에 **합칩니다(merge)**.
- 잘 안 되면 브랜치만 버리면 되니까 `main` 은 안전합니다.

> 💡 사실 1주차부터 매주 브랜치를 쓰고 있었어요!
> git-mentoring에서 `git switch -c week04-hong` 으로 만든 것이 브랜치이고,
> PR을 **Merge** 하는 것은 "내 브랜치를 원본의 `main` 에 합쳐 주세요"라는 뜻이었습니다.

### 2) 이번 주 명령어

| 명령어 | 의미 |
|---|---|
| `git branch` | 브랜치 목록 보기 (`*` 표시가 지금 있는 브랜치) |
| `git switch -c 이름` | 새 브랜치를 만들고 그 브랜치로 이동 |
| `git switch 이름` | 다른 브랜치로 이동 |
| `git merge 이름` | **지금 있는 브랜치**에 `이름` 브랜치를 합치기 |
| `git merge --abort` | 충돌이 나서 merge가 멈췄을 때, merge 전 상태로 되돌리기 |
| `git branch -d 이름` | 다 합친 브랜치 지우기 |
| `git log --oneline --graph --all` | 모든 브랜치의 기록을 그림으로 보기 |

> ⚠️ `git merge` 는 "**지금 있는 브랜치**로 가져와서 합친다"입니다. `main` 에 합치고 싶다면 **먼저 `git switch main`** 하세요.

### 3) 병합의 두 가지 모양

| 종류 | 언제? | 결과 |
|---|---|---|
| **Fast-forward** | `main` 에 새 커밋이 없고, 브랜치에만 커밋이 있을 때 | `main` 이 브랜치 끝으로 **앞으로 쭉 이동**만 함 (새 커밋 없음) |
| **Merge commit** | `main` 과 브랜치 **둘 다** 새 커밋이 있을 때 | 두 갈래를 합치는 **새 커밋**이 하나 생김 |

### 4) 충돌(conflict)이란?

두 브랜치가 **같은 파일의 같은 줄**을 서로 다르게 고친 뒤 합치면, Git은 어느 쪽이 맞는지 알 수 없어서 사람에게 물어봅니다.
그러면 파일 안에 아래와 같은 **충돌 표시**가 생깁니다.

```
<<<<<<< HEAD
지금 있는 브랜치(main)의 내용
=======
합치려는 브랜치의 내용
>>>>>>> change-title
```

**해결 방법:** 원하는 최종 내용만 남기고 `<<<<<<<`, `=======`, `>>>>>>>` 표시 줄을 모두 지운 뒤 → `git add` → `git commit`

> 💡 VS Code로 파일을 열면 충돌 부분 위에 **Accept Current / Accept Incoming / Accept Both** 버튼이 보입니다. 눌러서 골라도 됩니다.
>
> 💡 충돌은 에러가 아니라 **"어느 쪽으로 할지 정해 주세요"라는 질문**입니다. 실제 협업에서도 자주 생기니 겁먹지 마세요!

---

## 🛠️ 실습

모든 실습은 `~/git-practice` 에서 진행합니다. 커밋 메시지는 [커밋 메시지 규칙](../README.md#커밋-메시지-규칙)(`타입: 내용`)을 지켜 주세요.

```bash
cd ~/git-practice
git status            # On branch main, working tree clean 확인
git branch            # * main 하나만 보이면 준비 완료
```

> ⚠️ 브랜치를 옮기기 전에는 **항상 `git status` 로 커밋 안 한 수정이 없는지** 확인하세요.
> (3주차에 커밋하지 않고 둔 `memo.md` 처럼 Git이 모르는 Untracked 파일은 그대로 있어도 괜찮습니다.)

### 실습 1. 브랜치 만들고 오가기

```bash
git switch -c add-profile          # 새 브랜치 만들고 이동
git branch                         # * add-profile 로 바뀜

echo "# 자기소개" > profile.md
echo "- 이름: 홍길동" >> profile.md
git add profile.md
git commit -m "Add: 자기소개 파일 추가"
ls                                 # profile.md 있음

git switch main
ls                                 # profile.md 가 사라짐! (main에는 아직 없는 파일)
git switch add-profile
ls                                 # 다시 나타남
```

> 💡 파일이 사라진 게 아니라, **브랜치마다 다른 상태**를 보여 주는 것입니다.

### 실습 2. Fast-forward 병합

```bash
git switch main
git merge add-profile              # "Fast-forward" 라고 나옴
ls                                 # 이제 main에도 profile.md 가 있음
git log --oneline --graph --all
git branch -d add-profile          # 다 합쳤으니 브랜치 정리
```

### 실습 3. 갈라진 두 브랜치 합치기 (merge commit)

이번에는 `main` 과 브랜치 **양쪽에** 커밋을 만들어서, 두 갈래가 합쳐지는 모습을 봅니다.

```bash
git switch -c add-hobby
echo "- 취미: 산책" >> profile.md
git add profile.md
git commit -m "Add: 자기소개에 취미 추가"

git switch main
echo "- git merge" >> commands.md
git add commands.md
git commit -m "Add: 명령어 목록에 git merge 추가"

git merge add-hobby --no-edit      # "Merge made by the 'ort' strategy." 라고 나옴
git log --oneline --graph --all    # 갈라졌다가 다시 합쳐지는 그림 확인
git branch -d add-hobby
```

> 💡 `--no-edit` 은 merge commit 메시지를 기본값(`Merge branch 'add-hobby'`)으로 쓰겠다는 뜻입니다.
> 빼고 실행하면 메시지를 입력하는 편집기가 열립니다. (vim이 열렸다면 `:wq` 입력 후 Enter)

### 실습 4. 충돌 만들고 해결하기

같은 파일의 같은 줄을 두 브랜치에서 다르게 고쳐서, **일부러** 충돌을 만들어 봅니다.

```bash
# 1) main에 제목 파일 만들기
echo "제목: Git 연습장" > title.md
git add title.md
git commit -m "Add: 제목 파일 추가"

# 2) 브랜치에서 제목 바꾸기
git switch -c change-title
echo "제목: 나의 첫 Git 연습장" > title.md
git add title.md
git commit -m "Fix: 브랜치에서 제목 변경"

# 3) main에서도 같은 줄을 다르게 바꾸기
git switch main
echo "제목: Git 놀이터" > title.md
git add title.md
git commit -m "Fix: main에서 제목 변경"

# 4) 합치기 → 충돌 발생!
git merge change-title
# CONFLICT (content): Merge conflict in title.md
# Automatic merge failed; fix conflicts and then commit the result.
```

충돌 상태를 확인합니다.

```bash
git status            # both modified: title.md
cat title.md
# <<<<<<< HEAD
# 제목: Git 놀이터
# =======
# 제목: 나의 첫 Git 연습장
# >>>>>>> change-title
```

`title.md` 를 에디터로 열어서 **원하는 최종 내용 한 줄만** 남기고 충돌 표시를 모두 지운 뒤 저장합니다.
(어느 쪽을 골라도, 둘을 섞어도 됩니다. 예: `제목: 나의 첫 Git 놀이터`)

```bash
cat title.md          # 충돌 표시(<<<, ===, >>>)가 하나도 없는지 확인!
git add title.md      # "충돌 해결 완료"라고 Git에 알리기
git commit -m "Fix: title.md 충돌 해결"
git log --oneline --graph --all
git branch -d change-title
```

> 💡 해결하다가 꼬였다면 `git merge --abort` 로 merge 전 상태로 돌아가서 4)부터 다시 해 보세요.

### 실습 5. GitHub에 올리기

```bash
git push              # 4주차에 -u 로 짝지어 뒀기 때문에 이것만 쳐도 됨
```

GitHub의 `MY-ID/git-practice` 에서 `profile.md`, `title.md` 가 올라왔는지, **Commits** 에 merge commit이 보이는지 확인하세요.

---

## ✏️ 과제

`week05/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

````markdown
# 홍길동

- GitHub ID: MY-ID
- 실습 4 이후 `git log --oneline --graph --all` 결과:
  ```
  (여기에 결과를 붙여 넣기)
  ```
- 브랜치를 내 말로 설명하기:
- fast-forward 와 merge commit 의 차이 (실습 2, 3 경험으로):
- 충돌이 났을 때 `title.md` 에 보인 내용과, 어떻게 해결했는지:
- git-mentoring에서 매주 `main` 에서 새 브랜치를 만드는 이유:
- 이번 주 소감:
````

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week05-이름` (예: `week05-hong`) |
| 파일 경로 | `week05/members/본인이름.md` (예: `week05/members/홍길동.md`) |
| 커밋 메시지 | `Add: 5주차 홍길동 과제` |
| PR 제목 | `[5주차] 홍길동 과제 제출` |

명령어 순서가 기억나지 않으면 [메인 README의 "매주 과제 제출 흐름"](../README.md#매주-과제-제출-흐름)을 참고하세요.

```bash
cd ~/git-mentoring       # git-practice가 아니라 git-mentoring 폴더로 이동
git switch main
git pull upstream main
git push origin main
git switch -c week05-hong
# week05/members/홍길동.md 작성 후 저장
git add week05/members/홍길동.md
git commit -m "Add: 5주차 홍길동 과제"
git push origin week05-hong
# GitHub에서 Pull Request 생성
```

> 💡 `git-mentoring` 을 홈 폴더가 아닌 다른 곳에 clone했다면 그 경로로 `cd` 하세요.
>
> ⚠️ 새 브랜치는 꼭 **`main` 에서** 만드세요. 지난주 브랜치에 있는 상태로 `git switch -c` 하면 지난주 파일까지 PR에 딸려 갑니다.
> 이번 주에 배운 대로, `git switch -c` 는 **지금 있는 브랜치에서 갈라져 나오기** 때문이에요.

---

## ❓ 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| `error: Your local changes to the following files would be overwritten by checkout` | 커밋하지 않은 수정이 있는 채로 브랜치를 옮기려 함 | 수정을 commit 하거나, 필요 없으면 `git restore 파일` 후 다시 `git switch` |
| `Already up to date.` | 합치려는 브랜치에 새 커밋이 없음 | 브랜치에서 commit 했는지 `git log --oneline --graph --all` 로 확인 |
| `CONFLICT (content): Merge conflict in ...` | 같은 줄을 양쪽에서 다르게 고침 | [충돌 해결 방법](#4-충돌conflict이란) 참고. 꼬이면 `git merge --abort` |
| `You have not concluded your merge (MERGE_HEAD exists).` | 충돌을 해결하고 commit 하지 않은 채로 다른 작업을 함 | 충돌 파일 수정 → `git add` → `git commit` 으로 merge 마무리 |
| `error: The branch '...' is not fully merged.` | 아직 합치지 않은 브랜치를 `-d` 로 지우려 함 | `git switch main` → `git merge 브랜치` 를 먼저 했는지 확인 |
| merge 후 이상한 편집기 화면이 뜸 | merge commit 메시지를 입력하는 화면 | 그대로 저장하고 닫기 (vim이면 `:wq` 입력 후 Enter) |

---

## ✅ 제출 체크리스트

- [ ] 브랜치를 만들고 `git switch` 로 오가며 파일이 바뀌는 것을 확인했다 (실습 1)
- [ ] fast-forward 병합을 해 봤다 (실습 2)
- [ ] 양쪽에 커밋이 있는 브랜치를 merge commit으로 합쳐 봤다 (실습 3)
- [ ] 충돌을 만들고, 충돌 표시를 지워 직접 해결했다 (실습 4)
- [ ] 다 합친 브랜치를 `git branch -d` 로 정리했다
- [ ] `git push` 로 GitHub에 올렸다 (실습 5)
- [ ] `main` 에서 만든 `week05-이름` 브랜치에서 `week05/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 커밋 메시지 규칙(`타입: 내용`)을 지켰다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
