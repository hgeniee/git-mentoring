# 6주차: GitHub 협업 (Issue, 코드 리뷰, 리뷰 반영)

## 🎯 학습 목표

- **Issue** 로 할 일이나 질문을 남기고, PR과 연결할 수 있다.
- 다른 사람의 PR을 읽고 **리뷰 코멘트**를 남길 수 있다.
- 내 PR에 달린 리뷰를 **같은 브랜치에 커밋을 추가**해서 반영할 수 있다.
- 오픈소스 프로젝트가 **Issue → PR → 리뷰 → 반영 → Merge** 순서로 돌아간다는 것을 이해한다.

> 💡 지금까지는 튜터만 리뷰를 했다면, 이번 주에는 **멘티끼리 서로 리뷰**합니다.
> 이번 주 실습은 `git-practice` 가 아니라 **`git-mentoring`** 저장소와 GitHub 웹에서 진행합니다.

---

## 📚 학습 내용

### 1) 오픈소스 협업 흐름

```
① Issue 만들기        "이런 걸 하려고 해요 / 이런 문제가 있어요"
        |
② PR 보내기           PR 설명에 "Closes #이슈번호" 를 적어 Issue와 연결
        |
③ 리뷰 받기           다른 사람이 Files changed 에서 코멘트를 남김
        |
④ 리뷰 반영           같은 브랜치에 커밋 추가 → push → PR에 자동 반영
        |
⑤ Merge              Merge 되면 연결된 Issue도 자동으로 닫힘 🎉
```

### 2) Issue

- 저장소의 **Issues** 탭에서 만드는 "게시글"입니다. 버그 신고, 기능 제안, 질문, 할 일 등을 남깁니다.
- Issue마다 **번호**(`#21` 등)가 붙습니다. PR도 같은 번호 체계를 씁니다.
- PR 설명에 **`Closes #21`** 이라고 적으면, PR이 Merge될 때 21번 Issue가 **자동으로 닫힙니다.**

### 3) 코드 리뷰

PR 화면의 **Files changed** 탭에서 바뀐 내용을 보고 코멘트를 남깁니다.

| 리뷰 방법 | 하는 법 |
|---|---|
| 특정 줄에 코멘트 | 줄 번호에 마우스를 올리면 나오는 파란 **+** 버튼 클릭 → 코멘트 작성 → **Start a review** |
| 리뷰 제출 | 오른쪽 위 **Review changes** → 전체 의견 작성 → **Comment** 선택 → **Submit review** |
| PR 전체에 짧은 의견 | **Conversation** 탭 맨 아래 댓글 창에 작성 |

> 💡 좋은 리뷰 코멘트는 **무엇을, 왜** 바꾸면 좋을지 구체적으로 말하고, 잘한 점도 함께 말해 줍니다.
>
> | 😕 아쉬운 코멘트 | 🙂 좋은 코멘트 |
> |---|---|
> | "이상해요" | "`-u` 설명에 '짝지어 둔다'는 표현이 이해하기 쉬워요! 다만 `git pull` 설명에 실습 5 경험도 넣으면 더 좋을 것 같아요." |
> | "틀렸어요" | "`git diff --staged` 는 add 한 변경을 보여 주는 거라, 설명이 반대로 적힌 것 같아요." |

### 4) 리뷰 반영

리뷰를 받으면 **새 PR을 만들지 않고**, 같은 브랜치에서 고친 뒤 다시 push 합니다. (1주차 [7. 리뷰 반영하기](../README.md#7-리뷰-반영하기)와 같은 방법)

```bash
git switch week06-hong                 # PR을 보낸 그 브랜치인지 확인
# 파일 수정 후 저장
git add week06/members/홍길동.md
git commit -m "Fix: 6주차 리뷰 반영"
git push origin week06-hong            # 기존 PR에 커밋이 자동으로 추가됨
```

반영했다면 리뷰 코멘트에 **답글**("반영했습니다!")을 달고 **Resolve conversation** 을 눌러 정리합니다.

---

## 👥 리뷰 짝꿍

아래 표의 **리뷰할 사람**의 6주차 PR을 리뷰해 주세요. (A → B → C → D → E → A 순서로 돌아가며 리뷰)

| 나 | 리뷰할 사람 |
|---|---|
| @jelai00 | @linearmik |
| @linearmik | @gseyeon74 |
| @gseyeon74 | @seeunparkdev |
| @seeunparkdev | @oseoooojin |
| @oseoooojin | @jelai00 |

> 💡 짝꿍의 PR이 아직 안 올라왔다면 먼저 내 PR부터 보내 두고, 짝꿍 PR이 올라오면 리뷰하세요.
> 짝꿍이 늦어진다면 **Issues** 탭에 남겨 주세요. 튜터가 다른 짝꿍을 연결해 드립니다.

---

## ✏️ 과제

### 1단계. Issue 만들기

1. `hgeniee/git-mentoring` → **Issues** 탭 → **New issue**
2. 제목: `[6주차] 홍길동 과제` / 내용: 지금까지 Git을 배우면서 **가장 헷갈렸던 것 한 가지**
3. **Create** 클릭 → 만들어진 Issue 번호(`#번호`)를 기억해 두기

### 2단계. 과제 파일 작성하고 PR 보내기

`week06/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

```markdown
# 홍길동

- GitHub ID: MY-ID
- 내가 만든 Issue: #번호
- Issue와 PR을 연결하면 좋은 점:
- 좋은 리뷰 코멘트란 무엇일까 (내 생각):
- 내가 리뷰한 PR: #번호
- 내가 남긴 리뷰 코멘트 요약:
- 내가 받은 리뷰와 반영한 내용:
- 이번 주 소감:
```

> 💡 "내가 리뷰한 PR", "받은 리뷰" 칸은 PR을 처음 보낼 때 **비워 둬도 됩니다.** 3·4단계를 하면서 채워서 다시 push 하세요.
> 이렇게 PR을 보낸 뒤에 내용을 보충하는 것 자체가 이번 주 실습입니다.

PR을 만들 때 **설명란에 반드시** 아래처럼 적어 주세요.

```
week06/members/홍길동.md 파일을 추가했습니다.

Closes #번호
```

### 3단계. 짝꿍 PR 리뷰하기

1. [리뷰 짝꿍](#-리뷰-짝꿍) 표에서 내가 리뷰할 사람의 `[6주차]` PR을 엽니다. (**Pull requests** 탭)
2. **Files changed** 탭 → 특정 줄에 **+** 버튼으로 코멘트 **1개 이상** 작성
3. **Review changes** → 전체 의견(잘한 점 포함) 작성 → **Comment** → **Submit review**

> ⚠️ 리뷰는 **코멘트만** 남기고, 다른 사람의 파일을 직접 수정하거나 커밋하지 마세요.

### 4단계. 받은 리뷰 반영하기

1. 내 PR에 달린 리뷰를 확인합니다.
2. [4) 리뷰 반영](#4-리뷰-반영) 방법으로 파일을 고치고, "내가 리뷰한 PR / 받은 리뷰" 칸도 채워서 push 합니다.
3. 리뷰 코멘트에 답글을 달고 **Resolve conversation** 을 누릅니다.
4. 튜터가 Merge하면 1단계에서 만든 Issue가 **자동으로 닫혔는지** 확인합니다.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| Issue 제목 | `[6주차] 홍길동 과제` |
| 브랜치 이름 | `week06-이름` (예: `week06-hong`) |
| 파일 경로 | `week06/members/본인이름.md` (예: `week06/members/홍길동.md`) |
| 커밋 메시지 | 처음: `Add: 6주차 홍길동 과제` / 리뷰 반영: `Fix: 6주차 리뷰 반영` |
| PR 제목 | `[6주차] 홍길동 과제 제출` |
| PR 설명 | `Closes #내Issue번호` 포함 |

```bash
cd ~/git-mentoring
git switch main
git pull upstream main
git push origin main
git switch -c week06-hong              # 꼭 main에서 만들기!
# week06/members/홍길동.md 작성 후 저장
git add week06/members/홍길동.md
git commit -m "Add: 6주차 홍길동 과제"
git push origin week06-hong
# GitHub에서 Pull Request 생성 (설명에 Closes #번호)

# --- 리뷰를 받은 뒤 ---
# week06/members/홍길동.md 수정 후 저장
git add week06/members/홍길동.md
git commit -m "Fix: 6주차 리뷰 반영"
git push origin week06-hong
```

> 💡 `git-mentoring` 을 홈 폴더가 아닌 다른 곳에 clone했다면 그 경로로 `cd` 하세요.

---

## ❓ 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| Merge됐는데 Issue가 안 닫힘 | PR 설명에 `Closes #번호` 가 없거나 번호가 틀림 | 튜터에게 알려 주세요. 직접 Issue의 **Close issue** 를 눌러도 됩니다 |
| 리뷰 반영 push를 했는데 PR에 안 보임 | PR과 **다른 브랜치**에 커밋함 | `git branch` 로 지금 브랜치 확인 → `git switch week06-이름` 후 다시 commit, push |
| 리뷰 반영하려고 새 PR을 또 만듦 | 같은 브랜치에 push하면 기존 PR에 반영된다는 걸 놓침 | 새 PR은 **Close pull request** 로 닫고, 기존 PR에서 계속 진행 |
| Files changed 에서 **+** 버튼이 안 보임 | 마우스를 코드 줄이 아닌 곳에 올림 | 바뀐 줄의 **줄 번호** 위에 마우스를 올려 보세요 |
| **Resolve conversation** 버튼이 없음 | 리뷰가 줄 코멘트가 아닌 일반 댓글로 달림 | 답글만 달면 됩니다 |

---

## ✅ 제출 체크리스트

- [ ] `[6주차] 이름 과제` Issue를 만들었다
- [ ] `main` 에서 만든 `week06-이름` 브랜치에서 `week06/members/본인이름.md` 를 작성하고 commit 했다
- [ ] PR 설명에 `Closes #내Issue번호` 를 적어 PR을 보냈다
- [ ] 짝꿍 PR의 **Files changed** 에 줄 코멘트를 1개 이상 남기고 리뷰를 제출했다
- [ ] 받은 리뷰를 같은 브랜치에 `Fix: 6주차 리뷰 반영` 커밋으로 반영하고 push 했다
- [ ] 리뷰 코멘트에 답글을 달고 Resolve 했다
- [ ] Merge 후 내 Issue가 자동으로 닫힌 것을 확인했다
