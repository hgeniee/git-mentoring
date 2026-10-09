# 2주차: Git 설치 및 실습 환경 구성

## 🎯 학습 목표

- 내 PC에 Git이 설치되어 있고, 터미널에서 Git을 사용할 수 있는 상태를 **직접 확인**한다.
- 사용자 정보와 기본 브랜치 이름을 설정하고, 설정 내용을 스스로 확인할 수 있다.
- GitHub **Personal Access Token(PAT)** 이 무엇이고 언제 필요한지 이해한다.
- `git init` 으로 **처음부터** 저장소를 만들어 보고, `git clone` 과의 차이를 이해한다.

> 💡 1주차에 이미 Git을 설치하고 push까지 해 봤다면, 이번 주는 **"그때 따라 친 명령어가 무슨 뜻이었는지"** 정리하고
> 빠진 설정(기본 브랜치 이름 등)을 채우는 시간입니다. 설치 단계는 확인만 하고 넘어가도 됩니다.

---

## 📚 학습 내용

### 1) Git 설치 (이미 설치했다면 확인만)

| 운영체제 | 설치 방법 |
|---|---|
| Windows | [Git for Windows](https://git-scm.com/download/win) 설치 → **Git Bash** 와 Git Credential Manager가 함께 설치됨 |
| macOS | 터미널에서 `xcode-select --install` (Xcode Command Line Tools) 또는 `brew install git` (Homebrew) |

설치 확인:

```bash
git --version     # 예: git version 2.45.1
```

> ⚠️ `command not found` 가 나오면 설치가 안 된 것이고, Windows에서 Git Bash 대신 PowerShell/cmd를 열었을 수도 있습니다.

### 2) 터미널 기본 사용법

Windows는 **Git Bash**, macOS는 **터미널** 앱을 엽니다.

| 명령어 | 의미 | 예시 |
|---|---|---|
| `pwd` | 지금 내가 있는 위치(폴더) 출력 | `pwd` |
| `ls` | 현재 폴더의 파일 목록 보기 (`-a` : 숨김 파일까지) | `ls -a` |
| `cd` | 폴더 이동 (`~` : 홈 폴더, `..` : 상위 폴더) | `cd ~`, `cd ..` |
| `mkdir` | 새 폴더 만들기 | `mkdir git-practice` |

### 3) 사용자 정보 등록

커밋할 때마다 **누가** 만든 커밋인지 기록되기 때문에, 처음 한 번 등록해 둡니다.

```bash
git config --global user.name "내 이름"
git config --global user.email "GitHub에 가입한 이메일"
```

> 💡 `user.email` 은 GitHub 계정 이메일과 같아야 커밋이 내 프로필(잔디)에 연결됩니다.
> 이메일을 공개하고 싶지 않다면 GitHub → **Settings** → **Emails** 에 있는 `...@users.noreply.github.com` 주소를 써도 됩니다.

### 4) 기본 브랜치 이름 설정

`git init` 으로 새 저장소를 만들 때 첫 브랜치 이름을 `main` 으로 정합니다.
(설정하지 않으면 Git 버전에 따라 `master` 로 만들어질 수 있습니다.)

```bash
git config --global init.defaultBranch main
```

### 5) 설정 내용 확인

```bash
git config --list                  # 적용 중인 모든 설정 보기
git config --global --list         # 내가 --global 로 등록한 설정만 보기
git config user.name               # 특정 값 하나만 보기
```

> 💡 목록이 길어서 화면이 멈춘 것처럼 보이면 `q` 를 눌러 빠져나오세요.
> 잘못 입력했다면 같은 명령어로 다시 입력하면 덮어써집니다.

### 6) GitHub 계정과 Personal Access Token(PAT)

터미널에서 GitHub로 push할 때는 **GitHub 비밀번호를 사용할 수 없고**, 대신 PAT를 입력합니다.

발급 방법:

1. GitHub 오른쪽 위 프로필 → **Settings** → **Developer settings** → **Personal access tokens**
2. **Tokens (classic)** → **Generate new token (classic)**
3. Note(용도)에 `git-mentoring` 입력, Expiration(만료일) 설정, Scope는 **`repo`** 체크
4. **Generate token** → 화면에 나온 토큰을 바로 복사 (다시 볼 수 없습니다)

> 🔑 Windows의 Git for Windows는 push할 때 **브라우저 로그인 창**(Git Credential Manager)이 떠서 PAT 없이 로그인되는 경우가 많습니다.
> 터미널이 `Password:` 를 물어볼 때만 PAT를 붙여 넣으면 됩니다.
>
> ⚠️ 토큰은 비밀번호와 같습니다. **과제 파일, 스크린샷, 카톡 어디에도 적지 마세요.**

### 7) 실습 폴더에서 첫 저장소 만들기 (`git init`)

1주차에는 GitHub에 있는 저장소를 **내려받았다면(clone)**, 이번에는 빈 폴더를 **직접 Git 저장소로** 만들어 봅니다.

```bash
cd ~                     # 홈 폴더로 이동
mkdir git-practice       # 실습용 폴더 만들기
cd git-practice
pwd                      # 위치 확인
git init                 # 이 폴더를 Git 저장소로 만들기
ls -a                    # 숨김 폴더 .git 이 생겼는지 확인
git status               # On branch main 이 보이면 기본 브랜치 설정 성공
```

> ⚠️ `git-mentoring` 폴더 **안에서** `git init` 하지 마세요. 저장소 안에 저장소가 생겨 꼬입니다.
> 반드시 `cd ~` 로 빠져나온 뒤 별도 폴더에서 실습하세요.
>
> 💡 `.git` 폴더가 바로 Git이 모든 기록을 저장하는 곳입니다. 이 폴더를 지우면 일반 폴더로 돌아갑니다.

---

## ✏️ 과제

`week02/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

```markdown
# 홍길동

- GitHub ID: MY-ID
- 운영체제: (Windows / macOS)
- `git --version` 결과:
- `git config --global --list` 로 확인한 설정:
  - user.name:
  - user.email 등록 여부: (O / X)
  - init.defaultbranch:
- 실습 폴더에서 `git init` 후 `git status` 첫 줄:
- `git init` 과 `git clone` 의 차이를 내 말로 설명하기:
- PAT를 비밀번호처럼 다뤄야 하는 이유:
- 이번 주 소감:
```

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.
>
> 🔒 이메일 주소와 PAT 값은 적지 마세요. 이메일은 등록 여부만 O / X 로 표시합니다.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week02-이름` (예: `week02-hong`) |
| 파일 경로 | `week02/members/본인이름.md` (예: `week02/members/홍길동.md`) |
| 커밋 메시지 | `Add: 2주차 홍길동 과제` |
| PR 제목 | `[2주차] 홍길동 과제 제출` |

명령어 순서가 기억나지 않으면 [메인 README의 "매주 과제 제출 흐름"](../README.md#매주-과제-제출-흐름)을 참고하세요.

```bash
cd ~/git-mentoring       # 실습 폴더가 아니라 git-mentoring 폴더로 돌아오기
git switch main
git pull upstream main
git push origin main
git switch -c week02-hong
# week02/members/홍길동.md 작성 후 저장
git add week02/members/홍길동.md
git commit -m "Add: 2주차 홍길동 과제"
git push origin week02-hong
# GitHub에서 Pull Request 생성
```

> 💡 `git-mentoring` 을 홈 폴더가 아닌 다른 곳에 clone했다면 그 경로로 `cd` 하세요.

---

## ✅ 제출 체크리스트

- [ ] `git --version` 으로 설치를 확인했다
- [ ] `user.name`, `user.email` 을 등록하고 `git config --list` 로 확인했다
- [ ] `init.defaultBranch` 를 `main` 으로 설정했다
- [ ] PAT 발급 위치를 확인했다 (필요하면 발급했다)
- [ ] 별도 실습 폴더에서 `git init` 하고 `.git` 폴더를 확인했다
- [ ] `week02-이름` 브랜치에서 `week02/members/본인이름.md` 를 작성하고(이번 주 소감 포함) commit 했다
- [ ] 커밋 메시지 규칙(`타입: 내용`)을 지켰다
- [ ] 내 저장소(origin)로 push 하고 원본 저장소로 Pull Request를 생성했다
