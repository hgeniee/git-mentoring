# 1주차: Git & GitHub 개념, 오픈소스 협업 구조

## 🎯 학습 목표

- 버전 관리가 왜 필요한지 이해한다.
- **Git**(내 컴퓨터에서 쓰는 버전 관리 도구)과 **GitHub**(Git 저장소를 온라인에 올려 함께 쓰는 서비스)의 차이를 이해한다.
- **Fork → Clone → branch → commit → push → Pull Request** 로 이어지는 오픈소스 기여 흐름을 직접 해 본다.

> 🚀 처음이라면 [메인 README의 "처음 한 번만 하는 준비"](../README.md#처음-한-번만-하는-준비)부터 진행하세요.
> (Git 설치 → Fork → Clone → upstream 등록)

---

## ✏️ 과제

`week01/members/` 폴더 안에 **`본인이름.md`** 파일을 만들고 아래 양식을 채워 주세요.
작성 예시: [튜터 예시 보기](./members/hgeniee.md)

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

> ⚠️ 다른 사람의 파일은 수정하지 말고 **본인 파일만** 새로 만드세요.

---

## 📮 제출 정보

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week01-이름` (예: `week01-hong`) |
| 파일 경로 | `week01/members/본인이름.md` (예: `week01/members/홍길동.md`) |
| 커밋 메시지 | `Add: 1주차 홍길동 과제` |
| PR 제목 | `[1주차] 홍길동 과제 제출` |

명령어 순서가 기억나지 않으면 [메인 README의 "매주 과제 제출 흐름"](../README.md#매주-과제-제출-흐름)을 참고하세요.

```bash
git switch main
git pull upstream main
git push origin main
git switch -c week01-hong
# week01/members/홍길동.md 작성 후 저장
git add week01/members/홍길동.md
git commit -m "Add: 1주차 홍길동 과제"
git push origin week01-hong
# GitHub에서 Pull Request 생성
```

---

## ✅ 제출 체크리스트

- [ ] `hgeniee/git-mentoring` 저장소를 Fork 했다
- [ ] 내 저장소(`MY-ID/git-mentoring`)를 Clone 하고 upstream을 등록했다
- [ ] `week01-이름` 브랜치에서 작업했다
- [ ] `week01/members/본인이름.md` 를 작성하고 commit 했다
- [ ] 커밋 메시지 규칙(`타입: 내용`)을 지켰다
- [ ] 내 저장소(origin)로 push 했다
- [ ] 원본 저장소로 Pull Request를 생성했다
- [ ] 리뷰를 반영하고 Merge 된 것을 확인했다
