# Git & GitHub 오픈소스 협업 실습 매뉴얼

이 저장소는 **오픈소스 기여 흐름(Fork → Pull Request)** 을 직접 체험하기 위한 실습 공간입니다.
아래 순서대로 따라 하면 실제 오픈소스 프로젝트에 기여하는 것과 동일한 과정을 경험할 수 있습니다.

> 📌 아래 명령어의 `MY-ID`(본인 GitHub 아이디), `이름`은 각자 상황에 맞게 바꿔서 입력하세요.

---

## 전체 흐름 한눈에 보기

```
[원본 저장소(upstream)] --① Fork--> [내 저장소(origin)]
                                          |  ② Clone
                                          v
                                   [내 컴퓨터(로컬)]
                                   ③ branch → 수정 → commit
                                          |  ④ Push
                                          v
[원본 저장소(upstream)] <--⑤ Pull Request-- [내 저장소(origin)]
        ⑥ 리뷰 → Merge
```

---

## 0. 사전 준비

1. [GitHub](https://github.com) 계정 만들기
2. [Git](https://git-scm.com/downloads) 설치하기
3. 터미널(Windows는 Git Bash)에서 설치 확인 및 사용자 정보 등록

```bash
git --version
git config --global user.name "내 이름"
git config --global user.email "GitHub에 가입한 이메일"
```

---

## 1. Fork 하기 (GitHub 웹)

1. 이 저장소 페이지 오른쪽 상단의 **Fork** 버튼 클릭
2. **Create fork** 클릭
3. `https://github.com/MY-ID/git-mentoring` 이 생성되었는지 확인

> 💡 Fork = 원본 저장소를 **내 GitHub 계정으로 복사**하는 것. 원본에는 직접 수정 권한이 없기 때문에 내 사본에서 작업합니다.

---

## 2. Clone 하기 (내 컴퓨터로 내려받기)

**내 저장소(Fork한 것)** 의 초록색 **Code** 버튼 → HTTPS 주소 복사 후:

```bash
git clone https://github.com/MY-ID/git-mentoring.git
cd git-mentoring
```

원본 저장소도 `upstream`이라는 이름으로 연결해 둡니다. (나중에 최신 내용 받아올 때 사용)

```bash
git remote add upstream https://github.com/hgeniee/git-mentoring.git
git remote -v    # origin(내 저장소), upstream(원본) 두 개가 보이면 성공
```

---

## 3. 브랜치 만들기

`main`에서 바로 작업하지 않고, 작업용 브랜치를 만듭니다.

```bash
git switch -c add-이름      # 예: git switch -c add-hong
```

---

## 4. 과제 수행

`members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 내용을 작성하세요.
(다른 사람과 같은 파일을 수정하지 않도록 반드시 **본인 파일만** 만듭니다.)

```markdown
# 홍길동

- GitHub ID: MY-ID
- 한 줄 자기소개:
- 오늘 배운 Git 명령어 3가지와 의미:
  1.
  2.
  3.
- Fork와 Clone의 차이를 내 말로 설명하기:
```

---

## 5. Commit 하기

```bash
git status                      # 변경된 파일 확인
git add members/홍길동.md        # 스테이징
git commit -m "Add: 홍길동 자기소개"   # 커밋
git log --oneline               # 커밋 기록 확인
```

> 💡 커밋 메시지는 **무엇을 했는지** 알 수 있게 작성합니다.

---

## 6. Push 하기 (내 저장소로 올리기)

```bash
git push origin add-이름
```

> 처음 push할 때 로그인 창이 뜨면 GitHub 계정으로 로그인하세요.
> 비밀번호 입력을 요구하면 GitHub 비밀번호가 아닌 **Personal Access Token**이 필요합니다.
> (GitHub → Settings → Developer settings → Personal access tokens에서 발급)

---

## 7. Pull Request(PR) 보내기

1. 내 저장소 페이지에 뜨는 **Compare & pull request** 버튼 클릭
2. 방향 확인: `hgeniee/git-mentoring : main` ← `MY-ID/git-mentoring : add-이름`
3. 제목과 설명 작성 후 **Create pull request** 클릭

```
제목: [과제] 홍길동 자기소개 추가
내용: members/홍길동.md 파일을 추가했습니다.
```

---

## 8. 리뷰 반영하기

튜터가 PR에 코멘트를 남기면, 로컬에서 수정 후 **같은 브랜치에 다시 push** 합니다.
새 PR을 만들 필요 없이 기존 PR에 자동으로 반영됩니다.

```bash
git add members/홍길동.md
git commit -m "Fix: 리뷰 반영"
git push origin add-이름
```

튜터가 승인하면 원본 저장소에 **Merge** 되고 과제가 완료됩니다. 🎉

---

## 9. (Merge 이후) 최신 내용 동기화

다른 사람들의 작업까지 내 컴퓨터와 내 저장소에 반영합니다.

```bash
git switch main
git pull upstream main
git push origin main
```

---

## ✅ 제출 체크리스트

- [ ] Fork 완료
- [ ] Clone 및 upstream 등록 완료
- [ ] `add-이름` 브랜치에서 작업
- [ ] `members/본인이름.md` 작성 및 commit
- [ ] 내 저장소로 push
- [ ] 원본 저장소로 Pull Request 생성
- [ ] 리뷰 반영 후 Merge 확인

---

## ❓ 자주 막히는 부분

| 상황 | 해결 방법 |
|---|---|
| `permission denied` / 403 에러 | 원본(hgeniee) 주소로 clone했는지 확인 → 반드시 **내 저장소(MY-ID)** 를 clone |
| push할 때 비밀번호 오류 | GitHub 비밀번호 대신 Personal Access Token 입력 |
| `nothing to commit` | `git add`를 했는지, 파일을 저장했는지 확인 |
| PR 버튼이 안 보임 | 내 저장소 → **Pull requests** 탭 → **New pull request** 클릭 |
| 브랜치를 안 만들고 main에서 작업함 | `git switch -c add-이름` 실행 후 이어서 commit (변경 내용은 그대로 옮겨짐) |

궁금한 점은 이 저장소의 **Issues** 탭에 질문을 남겨 주세요.
