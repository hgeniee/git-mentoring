# 9주차: Markdown과 GitHub 프로필 꾸미기

## 🎯 학습 목표

- 지금까지 매주 써 온 `.md` 파일의 정체, **Markdown 문법**을 제대로 익힌다.
- 나만의 **GitHub 프로필 README** 를 만들어서, 내 GitHub 첫 화면을 꾸민다.
- 지금까지 배운 **clone → 수정 → commit → push** 흐름을 내 저장소에서 혼자 처음부터 끝까지 해 본다.

> 💡 이번 주 결과물(프로필 README)은 **10주차 수료 활동**에서 서로 소개할 때 사용합니다. 정성껏 만들어 주세요!

---

## 📚 학습 내용

### 1) Markdown이란?

`#`, `-`, `**` 같은 간단한 기호로 **제목, 목록, 굵은 글씨** 등을 표현하는 문서 작성 방법입니다.
GitHub의 README, Issue, PR 설명, 리뷰 코멘트가 모두 Markdown으로 보입니다.

### 2) 자주 쓰는 문법

| 표현 | 이렇게 쓰면 | 이렇게 보임 |
|---|---|---|
| 제목 | `# 큰 제목`, `## 중간 제목`, `### 작은 제목` | 크기가 다른 제목 |
| 굵게 / 기울임 | `**굵게**`, `*기울임*` | **굵게**, *기울임* |
| 목록 | `- 항목` 또는 `1. 항목` | • 항목 / 1. 항목 |
| 체크리스트 | `- [ ] 할 일`, `- [x] 한 일` | ☐ 할 일 / ☑ 한 일 |
| 링크 | `[GitHub](https://github.com)` | [GitHub](https://github.com) |
| 이미지 | `![설명](이미지주소)` | 이미지 표시 |
| 코드 (한 줄) | `` `git status` `` | `git status` |
| 코드 (여러 줄) | ` ```bash ` 로 열고 ` ``` ` 로 닫기 | 회색 코드 상자 |
| 인용 | `> 인용문` | 왼쪽에 선이 있는 문단 |
| 구분선 | `---` | 가로 선 |
| 표 | `\| 제목 \| 제목 \|` 다음 줄에 `\|---\|---\|` | 표 |

> 💡 **줄바꿈 주의:** 그냥 Enter 한 번은 같은 문단으로 이어 붙여 보입니다. 문단을 나누려면 **빈 줄**을 한 줄 넣으세요.
>
> 💡 VS Code에서 `.md` 파일을 열고 `Ctrl + Shift + V` (macOS: `Cmd + Shift + V`) 를 누르면 **미리보기**를 볼 수 있어요.

### 3) GitHub 프로필 README

**내 GitHub 아이디와 똑같은 이름**의 저장소를 만들고 그 안에 `README.md` 를 쓰면, 내 프로필 페이지(`https://github.com/MY-ID`) 맨 위에 그 내용이 보입니다.

```
저장소 이름: MY-ID  (예: 내 아이디가 gildong-hong 이면 저장소 이름도 gildong-hong)
       ↓
https://github.com/MY-ID 첫 화면에 README.md 내용이 표시됨
```

---

## 🛠️ 실습

### 실습 1. 프로필 저장소 만들기 (GitHub 웹)

1. GitHub 오른쪽 위 **+** → **New repository**
2. Repository name에 **본인 GitHub 아이디를 정확히** 입력 → "✨ special repository" 안내 문구가 뜨는지 확인
3. **Public** 선택
4. **Add a README file 체크** ✅
5. **Create repository**

> 💡 4주차에는 README를 체크하면 안 됐죠? 그때는 **이미 있던 내 로컬 저장소**를 올렸기 때문이고,
> 이번에는 GitHub에서 **새로 만든 저장소를 clone** 해서 쓰기 때문에 README가 있어도 괜찮습니다.

### 실습 2. clone 해서 프로필 작성하기

```bash
cd ~
git clone https://github.com/MY-ID/MY-ID.git
cd MY-ID
ls                        # README.md 가 보임
```

`README.md` 를 에디터로 열어서 자유롭게 작성하세요. 아래 예시를 복사해서 바꿔 써도 됩니다.
**Markdown 문법을 5가지 이상** 써 보세요.

````markdown
# 안녕하세요, 홍길동입니다 👋

> Git & GitHub 멘토링 수료를 앞둔 개발 입문자입니다.

## 🙋 About me

- 🎓 OO대학교 OO학과
- 🌱 요즘 배우고 있는 것: **Git**, GitHub
- 💬 관심 분야: 웹 개발, 오픈소스

## 🛠️ 이번 멘토링에서 배운 것

| 주차 | 배운 것 |
|---|---|
| 4주차 | `git push`, `git pull` 로 GitHub와 연결하기 |
| 5주차 | 브랜치와 충돌 해결 |

## ✅ 올해 목표

- [x] 첫 Pull Request 보내기
- [ ] 실제 오픈소스 프로젝트에 기여하기

## 📫 Contact

- GitHub: [@MY-ID](https://github.com/MY-ID)
````

> 🔒 전화번호, 개인 이메일, 학번처럼 **공개되면 곤란한 정보는 적지 마세요.** 프로필은 전 세계 누구나 볼 수 있습니다.

### 실습 3. commit, push 하고 확인하기

```bash
git status
git diff                          # 바꾼 내용 확인
git add README.md
git commit -m "Docs: 프로필 README 작성"
git push                          # clone한 저장소라 origin/main 과 이미 짝지어져 있음
```

`https://github.com/MY-ID` 에 들어가서 프로필 첫 화면에 README가 보이는지 확인하세요. 🎉

> 💡 clone한 저장소는 처음부터 `origin` 과 짝지어져 있어서 `-u` 없이 `git push` 만 쳐도 됩니다. (4주차와 비교해 보세요)

### 실습 4. 웹에서 한 번 더 고치고 pull 받기

1. GitHub에서 프로필 저장소의 `README.md` → ✏️(Edit) → 아무 줄이나 수정 → **Preview** 탭으로 미리보기 → **Commit changes**
2. 내 컴퓨터에서 받아오기:

```bash
git pull
git log --oneline -n 3
```

---

## ✏️ 과제

`week09/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
이번 주 과제 파일도 **Markdown 문법을 3가지 이상** 써서 꾸며 보세요. (표, 체크리스트, 링크 등)
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

```markdown
# 홍길동

- GitHub ID: MY-ID
- 내 프로필 주소: https://github.com/MY-ID
- 프로필 README에 쓴 Markdown 문법 (5가지 이상):
  1.
  2.
  3.
  4.
  5.
- 4주차(`git init` 후 연결)와 이번 주(`git clone`)의 차이:
- Markdown을 쓰면서 헷갈렸던 점:
- 다른 멘티에게 추천하고 싶은 프로필 꾸미기 팁:
- 이번 주 소감:
```

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week09-이름` (예: `week09-hong`) |
| 파일 경로 | `week09/members/본인이름.md` (예: `week09/members/홍길동.md`) |
| 커밋 메시지 | `Add: 9주차 홍길동 과제` |
| PR 제목 | `[9주차] 홍길동 과제 제출` |

```bash
cd ~/git-mentoring       # 프로필 저장소(~/MY-ID)가 아니라 git-mentoring 폴더로 이동
git switch main
git pull upstream main
git push origin main
git switch -c week09-hong
# week09/members/홍길동.md 작성 후 저장
git add week09/members/홍길동.md
git commit -m "Add: 9주차 홍길동 과제"
git push origin week09-hong
# GitHub에서 Pull Request 생성
```

> 💡 이제 내 컴퓨터에 저장소가 3개(`git-mentoring`, `git-practice`, `MY-ID`) 있어요. 명령어를 치기 전에 `pwd` 로 **지금 어느 폴더인지** 꼭 확인하세요.

---

## ❓ 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| 프로필에 README가 안 보임 | 저장소 이름이 아이디와 다름(대소문자, 오타), Private 으로 만듦, 또는 push를 안 함 | 저장소 **Settings** 에서 이름 확인 → Public 확인 → `git status` 로 push 여부 확인 |
| 줄을 바꿨는데 한 줄로 이어져 보임 | Markdown은 Enter 한 번을 줄바꿈으로 안 봄 | 문단 사이에 **빈 줄** 넣기 |
| 표가 표로 안 보임 | 표 바로 위에 빈 줄이 없거나 `\|---\|` 줄이 빠짐 | 표 위에 빈 줄 추가, 두 번째 줄에 `\|---\|---\|` 확인 |
| 이미지가 안 보임 | 이미지 주소가 틀림, 또는 내 컴퓨터 경로(`C:\...`)를 씀 | 인터넷 주소를 쓰거나, 이미지를 저장소에 올리고 `![설명](./파일이름.png)` |
| `git push` 에서 `Everything up-to-date` | commit을 안 했음 | `git status` 확인 → `git add` → `git commit` 후 다시 push |

---

## ✅ 제출 체크리스트

- [ ] 아이디와 같은 이름의 Public 저장소를 README 포함해서 만들었다 (실습 1)
- [ ] clone 해서 Markdown 문법 5가지 이상으로 프로필 README를 작성했다 (실습 2)
- [ ] commit, push 하고 내 프로필 페이지에서 확인했다 (실습 3)
- [ ] 웹에서 고친 내용을 `git pull` 로 받아왔다 (실습 4)
- [ ] 개인정보(전화번호, 개인 이메일 등)를 프로필에 적지 않았다
- [ ] `main` 에서 만든 `week09-이름` 브랜치에서 `week09/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
