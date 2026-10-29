# 10주차: 수료 활동 — 우리들의 Git 졸업 앨범 만들기 🎓

10주차는 과제 대신 **다 같이 모여서** 지난 9주 동안 배운 것을 총동원해 하나의 결과물을 만듭니다.

> **오늘의 결과물:** 누구나 접속할 수 있는 **멘토링 수료 웹사이트**
> 👉 `https://hgeniee.github.io/git-mentoring/`
>
> 각자 만든 **수료 페이지**와, 모두의 이름이 담긴 **졸업 앨범**이 GitHub Pages로 실제 인터넷에 공개됩니다.
> 수료 후에도 링크를 이력서나 프로필에 걸어 둘 수 있어요.

---

## 🗓️ 진행 순서 (약 2시간)

| 시간 | 활동 | 사용하는 기술 |
|---|---|---|
| 0:00 – 0:15 | 체크인 & 10주 돌아보기 | `git log`, `git shortlog` |
| 0:15 – 0:55 | **미션 1.** 내 수료 페이지 만들기 | Fork → branch → commit → PR → 리뷰 (1·5·6주차) |
| 0:55 – 1:05 | 쉬는 시간 · 사이트에 내 페이지가 떴는지 확인 | GitHub Pages |
| 1:05 – 1:30 | **미션 2.** 충돌 릴레이로 졸업 앨범 완성하기 | 충돌 해결 (5·8주차) |
| 1:30 – 1:45 | **미션 3.** 프로필 쇼케이스 | 프로필 README (9주차) |
| 1:45 – 2:00 | 단체 사진 · 다음 단계 안내 · 마무리 | |

---

## 🎒 준비물

**멘티**
- [ ] 노트북 (Git 설치, GitHub 로그인 된 상태)
- [ ] `~/git-mentoring` 이 최신 상태 (`git switch main` → `git pull upstream main`)
- [ ] 9주차에 만든 프로필 README

**튜터 (하루 전까지)**
- [ ] GitHub Pages 켜기: 저장소 **Settings** → **Pages** → Build and deployment의 Source를 **Deploy from a branch**, Branch를 **`main`** / **`/ (root)`** 로 선택 → **Save**
- [ ] 몇 분 뒤 `https://hgeniee.github.io/git-mentoring/` 에 메인 README가 보이는지 확인
- [ ] 미션 1에서 Merge를 빨리 해 줄 수 있도록 PR 알림 켜 두기

> 💡 사이트 제목과 테마는 저장소 맨 위의 `_config.yml` 에서 바꿀 수 있습니다.

---

## 0. 체크인 & 10주 돌아보기 (15분)

`git-mentoring` 에서 지금까지 쌓인 기록을 함께 봅니다.

```bash
cd ~/git-mentoring
git switch main
git pull upstream main
git log --oneline | wc -l          # 이 저장소에 쌓인 전체 커밋 수
git shortlog -sn --no-merges       # 사람별 커밋 수 순위 🏆
git log --oneline --graph -n 20    # 최근 기록을 그림으로
```

> 💡 한 사람씩 "**10주 동안 가장 당황했던 에러**"를 하나씩 이야기해 봐요. 지금은 다 해결할 수 있는 것들일 거예요.

---

## 1. 미션 1 — 내 수료 페이지 만들기 (40분)

`week10/members/본인이름.md` 에 나만의 수료 페이지를 만듭니다. Merge되면 **웹사이트의 한 페이지**가 됩니다.
작성 예시: [튜터의 수료 페이지](./members/hgeniee.md)

```markdown
# 홍길동

> 한 줄 소개를 여기에 적어 주세요.

- GitHub: [@MY-ID](https://github.com/MY-ID)

## 🧰 10주 동안 배운 것 중 가장 쓸모 있는 명령어 3가지

1. `명령어` — 이유
2. `명령어` — 이유
3. `명령어` — 이유

## 💥 가장 기억에 남는 에러와 해결 방법

## 🌱 앞으로 Git으로 해 보고 싶은 것

## 💌 함께한 사람들에게 한마디
```

**진행 방법**

```bash
git switch main
git pull upstream main
git switch -c week10-hong
# week10/members/홍길동.md 작성 후 저장
git add week10/members/홍길동.md
git commit -m "Add: 10주차 홍길동 수료 페이지"
git push origin week10-hong
```

1. PR 제목 `[10주차] 홍길동 수료 페이지` 로 PR 보내기
2. [6주차 리뷰 짝꿍](../week06/README.md#-리뷰-짝꿍)의 PR에 **칭찬 코멘트 1개 이상** 남기기
3. 튜터가 Merge하면 1~2분 뒤 사이트에서 확인: `https://hgeniee.github.io/git-mentoring/week10/members/본인이름.html`

> 💡 Markdown 파일(`.md`)이 사이트에서는 `.html` 페이지로 바뀌어서 보입니다. 9주차에 배운 Markdown이 그대로 웹페이지가 되는 거예요.
>
> 💡 페이지 반영 상황은 저장소의 **Actions** 탭(pages build and deployment)에서 볼 수 있어요. 초록 체크가 뜨면 반영 완료!

---

## 2. 미션 2 — 충돌 릴레이로 졸업 앨범 완성하기 (25분)

[`week10/album.md`](./album.md) 의 **수료생 목록 맨 아래**에 모두가 **동시에** 한 줄씩 추가합니다.
같은 위치를 동시에 고치니까 **일부러 충돌이 납니다.** 이번에는 튜터가 아니라 **각자 직접** 해결해요!

**규칙**

1. 다 같이 "시작!" 하면 동시에 아래 한 줄을 `album.md` 맨 아래에 추가하고 PR을 보냅니다.

   ```markdown
   - [홍길동](./members/홍길동.md) · [@MY-ID](https://github.com/MY-ID) · 오늘의 한 단어: **충돌**
   ```

   ```bash
   git switch main
   git pull upstream main             # 미션 1에서 Merge된 내용까지 받기
   git switch -c week10-album-hong
   # week10/album.md 맨 아래에 내 줄 추가 후 저장
   git add week10/album.md
   git commit -m "Add: 졸업 앨범에 홍길동 추가"
   git push origin week10-album-hong
   ```

2. 튜터는 **가장 먼저 도착한 PR**을 Merge합니다.
3. 나머지 PR에는 "This branch has conflicts" 가 뜹니다. [8주차 실습 6](../week08/README.md#실습-6-git-mentoring-pr에-충돌이-났을-때-읽어-두기) 방법으로 해결하고 다시 push!

   ```bash
   git switch week10-album-hong
   git pull upstream main             # 충돌 발생
   # album.md 를 열어 충돌 표시를 지우고, 다른 사람 줄과 내 줄을 **모두** 남기기
   git add week10/album.md
   git commit -m "Fix: 졸업 앨범 충돌 해결"
   git push origin week10-album-hong
   ```

4. 충돌을 해결한 사람부터 다시 Merge → 또 다른 사람에게 충돌 → 해결 … 을 **모두의 이름이 앨범에 들어갈 때까지** 반복합니다.

| 항목 | 값 |
|---|---|
| 브랜치 이름 | `week10-album-이름` (미션 1과 다른 브랜치! `main` 에서 새로 만들기) |
| 커밋 메시지 | `Add: 졸업 앨범에 홍길동 추가` / 충돌 해결: `Fix: 졸업 앨범 충돌 해결` |
| PR 제목 | `[10주차] 홍길동 졸업 앨범 추가` |

> ⚠️ 충돌을 해결할 때 **다른 사람의 줄을 지우지 마세요.** "내 것만 남기기"가 아니라 "**둘 다 남기기**"가 정답입니다.
>
> 💡 터미널이 어렵다면 PR 화면의 **Resolve conflicts** 버튼으로 웹에서 고쳐도 됩니다. 단, 한 번은 터미널로 해 보기를 추천해요!

---

## 3. 미션 3 — 프로필 쇼케이스 (15분)

1. 한 사람씩 9주차에 만든 **프로필 README**를 화면에 띄우고 1분 동안 소개합니다.
2. 서로 **Follow** 하고, 이 저장소(`hgeniee/git-mentoring`)에 **Star ⭐** 를 눌러 주세요.
3. 마음에 드는 프로필 꾸미기 아이디어가 있다면 그 자리에서 내 프로필에 적용하고 push 해 봐요.

---

## 4. 마무리 (15분)

- 📸 **단체 사진:** 튜터가 사진을 `week10/photo.jpg` 로 push하면, 졸업 앨범 맨 위에 표시됩니다.
- 🌍 **다음 단계 — 진짜 오픈소스에 첫 기여하기**

  | 어디서? | 무엇을? |
  |---|---|
  | [first-contributions](https://github.com/firstcontributions/first-contributions) | 전 세계 입문자들이 Fork → PR을 연습하는 저장소. 이 멘토링에서 한 것과 똑같은 흐름이라 바로 해 볼 수 있어요 |
  | [good first issue 토픽](https://github.com/topics/good-first-issue) | 입문자에게 맡기기 좋은 Issue를 모아 둔 프로젝트들 |
  | 평소 쓰는 라이브러리·문서 | 오타, 깨진 링크, 번역 등 작은 것부터 Issue → PR |

- 💬 마지막 소감은 미션 1의 수료 페이지 "함께한 사람들에게 한마디"에 남겨 주세요.

---

## ✅ 오늘의 체크리스트

- [ ] `git shortlog` 로 10주간의 기록을 확인했다
- [ ] 내 수료 페이지 PR을 보내고, 짝꿍 PR에 칭찬 코멘트를 남겼다
- [ ] 사이트에서 내 수료 페이지를 확인했다
- [ ] 졸업 앨범 충돌을 **직접** 해결하고, 내 이름이 앨범에 들어갔다
- [ ] 서로 Follow 하고 저장소에 Star 를 눌렀다

**10주 동안 수고 많았습니다. 수료를 축하해요! 🎉**
