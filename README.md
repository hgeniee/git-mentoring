# Git & GitHub 오픈소스 협업 실습

이 저장소는 Git & GitHub 멘토링에서 **오픈소스 기여 방식(Fork → Pull Request)** 으로 매주 과제를 제출하는 실습 공간입니다.
원본 저장소에 쓰기 권한이 없는 "외부 기여자" 입장에서, 실제 오픈소스 프로젝트에 기여하는 과정을 그대로 경험해 봅니다.

> 📌 아래 명령어에 나오는 값은 각자 상황에 맞게 바꿔서 입력하세요.
>
> | 표시 | 바꿔 넣을 값 | 예시 |
> |---|---|---|
> | `MY-ID` | 본인 GitHub 아이디 | `gildong-hong` |
> | `이름` | 본인 이름 (브랜치는 영문, 파일은 한글도 OK) | `hong`, `홍길동` |
> | `XX` | 주차 번호 (두 자리) | `01`, `02` |

---

## 주차별 과제

| 주차 | 주제 | 링크 |
|---|---|---|
| 1주차 | Git & GitHub 개념, 오픈소스 협업 구조 | [week01](./week01/README.md) |

> 새 주차 과제가 올라오면 이 표에 추가됩니다. 내 컴퓨터에 새 폴더가 안 보이면 [최신 내용 받기](#1-최신-내용-받기)를 먼저 하세요.

---

## 전체 흐름 한눈에 보기

```
[원본 저장소 upstream]  hgeniee/git-mentoring
        |
        |  ① Fork (GitHub 웹에서 내 계정으로 복사)
        v
[내 저장소 origin]      MY-ID/git-mentoring
        |
        |  ② Clone (내 컴퓨터로 내려받기)
        v
[내 컴퓨터 (로컬)]
   ③ branch 만들기 → 파일 작성 → commit
        |
        |  ④ Push (내 저장소로 올리기)
        v
[내 저장소 origin]      MY-ID/git-mentoring
        |
        |  ⑤ Pull Request (원본에 반영해 달라고 요청)
        v
[원본 저장소 upstream]  hgeniee/git-mentoring
   ⑥ 튜터 리뷰 → Merge 🎉
```

- **upstream** : 튜터의 원본 저장소. 멘티는 직접 수정할 수 없습니다.
- **origin** : Fork로 만든 **내** 저장소. 마음껏 push할 수 있습니다.

---

## 처음 한 번만 하는 준비

### 1) Git 설치 및 사용자 정보 등록

1. [GitHub](https://github.com) 계정 만들기
2. [Git](https://git-scm.com/downloads) 설치하기
3. 터미널(Windows는 **Git Bash**)을 열고 설치 확인 및 사용자 정보 등록

```bash
git --version
git config --global user.name "내 이름"
git config --global user.email "GitHub에 가입한 이메일"
```

### 2) Fork 하기 (GitHub 웹)

1. 이 저장소(`hgeniee/git-mentoring`) 페이지 오른쪽 위의 **Fork** 버튼 클릭
2. **Create fork** 클릭
3. `https://github.com/MY-ID/git-mentoring` 이 생성되었는지 확인

> 💡 **Fork** = 남의 저장소를 **내 GitHub 계정으로 복사**하는 것.
> 원본에는 쓰기 권한이 없기 때문에, 내 사본에서 작업한 뒤 PR로 반영을 요청합니다.

### 3) Clone 하고 upstream 등록하기

**내 저장소(MY-ID/git-mentoring)** 페이지의 초록색 **Code** 버튼 → HTTPS 주소 복사 후:

```bash
git clone https://github.com/MY-ID/git-mentoring.git
cd git-mentoring
```

> ⚠️ `hgeniee/git-mentoring` 이 아니라 **`MY-ID/git-mentoring`** 을 clone해야 합니다.

원본 저장소를 `upstream` 이라는 이름으로 연결해 둡니다. (매주 새 과제를 받아올 때 사용)

```bash
git remote add upstream https://github.com/hgeniee/git-mentoring.git
git remote -v    # origin(내 저장소), upstream(원본) 두 개가 보이면 성공
```

---

## 매주 과제 제출 흐름

### 1. 최신 내용 받기

새 주차 과제와 다른 사람들의 작업을 내 컴퓨터와 내 저장소에 반영합니다.

```bash
git switch main
git pull upstream main     # 원본 → 내 컴퓨터
git push origin main       # 내 컴퓨터 → 내 저장소
```

### 2. 브랜치 만들기

`main`에서 바로 작업하지 않고, 주차별 작업 브랜치를 만듭니다.

```bash
git switch -c weekXX-이름     # 예: git switch -c week01-hong
```

### 3. 과제 수행

해당 주차 폴더의 `README.md` 안내대로 과제를 수행합니다.
다른 사람과 충돌하지 않도록 **본인 파일만** 만들거나 수정하세요.

### 4. Commit 하기

```bash
git status                                  # 변경된 파일 확인
git add weekXX/members/홍길동.md             # 스테이징 (예: week01/members/홍길동.md)
git commit -m "Add: 1주차 홍길동 과제"        # 커밋
git log --oneline                           # 커밋 기록 확인
```

### 5. Push 하기 (내 저장소로 올리기)

```bash
git push origin weekXX-이름     # 예: git push origin week01-hong
```

> 🔑 처음 push할 때 로그인 창이 뜨면 GitHub 계정으로 로그인하세요.
> 터미널에서 비밀번호를 요구하면 GitHub 비밀번호가 아니라 **Personal Access Token(PAT)** 을 입력해야 합니다.
> 발급 위치: GitHub → 오른쪽 위 프로필 → **Settings** → **Developer settings** → **Personal access tokens**
> (토큰은 비밀번호처럼 다루고, 다른 사람에게 보여 주거나 파일에 적지 마세요.)

### 6. Pull Request(PR) 보내기

1. 내 저장소 페이지에 뜨는 **Compare & pull request** 버튼 클릭
2. 방향 확인: `hgeniee/git-mentoring : main` ← `MY-ID/git-mentoring : weekXX-이름`
3. 제목과 설명 작성 후 **Create pull request** 클릭

```
제목: [1주차] 홍길동 과제 제출
내용: week01/members/홍길동.md 파일을 추가했습니다.
```

### 7. 리뷰 반영하기

튜터가 PR에 코멘트를 남기면, 로컬에서 수정한 뒤 **같은 브랜치에 다시 push** 합니다.
새 PR을 만들 필요 없이 기존 PR에 자동으로 반영됩니다.

```bash
git add weekXX/members/홍길동.md
git commit -m "Fix: 1주차 리뷰 반영"
git push origin weekXX-이름
```

튜터가 승인하면 원본 저장소에 **Merge** 되고 그 주 과제가 완료됩니다. 🎉
다음 주에는 다시 [1. 최신 내용 받기](#1-최신-내용-받기)부터 시작하세요.

---

## 커밋 메시지 규칙

커밋 메시지는 아래 형식을 지켜 주세요. 리뷰할 때 규칙도 함께 확인합니다.

```
형식: 타입: 내용
```

| 타입 | 언제 사용? | 예시 |
|---|---|---|
| `Add` | 새 파일이나 내용을 추가할 때 | `Add: 1주차 홍길동 과제` |
| `Fix` | 리뷰 반영이나 오류를 고칠 때 | `Fix: 1주차 리뷰 반영` |
| `Docs` | 문서 내용을 수정할 때 | `Docs: README 설명 보완` |

---

## 자주 막히는 부분

| 상황 | 원인 | 해결 방법 |
|---|---|---|
| push할 때 `403` / `permission denied` 에러 | 원본(`hgeniee`) 저장소를 clone함 | 내 저장소(**MY-ID**)를 다시 clone하거나, `git remote set-url origin https://github.com/MY-ID/git-mentoring.git` |
| push할 때 비밀번호 오류 | GitHub 비밀번호는 터미널에서 사용 불가 | 비밀번호 대신 **Personal Access Token** 입력 |
| `nothing to commit` | 파일을 저장하지 않았거나 `git add`를 안 함 | 파일 저장 → `git status` 확인 → `git add` |
| PR 버튼(Compare & pull request)이 안 보임 | 버튼은 push 직후에만 잠깐 표시됨 | 내 저장소 → **Pull requests** 탭 → **New pull request** 클릭 |
| 새 주차 폴더가 안 보임 | 내 Fork/컴퓨터가 원본보다 예전 상태 | `git switch main` → `git pull upstream main` → `git push origin main` |
| 브랜치를 안 만들고 main에서 작업함 | — | commit 전이라면 `git switch -c weekXX-이름` 실행 후 이어서 commit (변경 내용은 그대로 옮겨짐) |

---

## 질문하기

궁금한 점이나 막히는 부분은 이 저장소의 **[Issues](https://github.com/hgeniee/git-mentoring/issues)** 탭에 남겨 주세요.
에러 메시지와 실행한 명령어를 함께 적어 주면 더 빨리 도와드릴 수 있습니다.
