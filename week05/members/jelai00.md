\# 제혜린



\- GitHub ID: MY-ID

\- 실습 4 이후 `git log --oneline --graph --all` 결과:

&#x20; ```

&#x20; $ git log --oneline --graph --all

\*   bee6587 (HEAD -> main) Fix: title.md 충돌 해결

|\\

| \* d8eebb6 (change-title) Fix: 브랜치에서 제목 젼경

\* | e232d87 Fix: main에서 제목 변경

|/

\* 0ed9b67 Add: 제목 파일 추가

\*   4c9535f Merge branch 'add-hobby'

|\\

| \* 18e40f1 Add: 자기소개에 취미 추가

\* | a436bef Add: 명령어 목록에 git merge 추가

|/

\* cac2caa Add: 자기소개 파일 추가

\* a7631cb (origin/main, origin/HEAD) Add: 웹에서 hello.md 수정

\* 0ca4b5e Remove extra line from hello.md

\* 87d7243 Update hello.md

\* a96c4ab Add:명령어 목록에 push 추가

\* 2367ed6 Add: 배운 명령어 목록 추가

\* ae79e98 Add: hello.md에 실습 기록 추가

\* 0942675 Ass: hello.md추가



&#x20; ```

\- 브랜치를 내 말로 설명하기: 브랜치는 main에서 갈라져 나온 나만의 작업 공간이다. 여기서 파일을 마음대로 고치고 커밋해도 main에는 영향이 없고. 작업이 끝나면 합쳐서 main에 반영한다.

\- fast-forward 와 merge commit 의 차이 (실습 2, 3 경험으로): fast-forward는 main에 새 커밋이 없을 때 일어난다. 브랜치가 일직선 위에 있어서 main의 포인터만 앞으로 옮기면 끝나고, 합치기용 커밋은 생기지 않는다. merge commit은 main과 브랜치에 각각 새 커밋이 있어 히스토리가 갈라졌을 때 생긴다. 두 갈래를 이어 주는 합치기 전용 커밋이 하나 생기고, git log --graph로 보면 갈라졌다 합쳐지는 모양이 보인다.

\- 충돌이 났을 때 `title.md` 에 보인 내용과, 어떻게 해결했는지: main에서는 "제목: Git 놀이터"로, 브랜치에서는 "제목: 나의 첫 Git 연습장"으로 같은 줄을 서로 다르게 바꿨다. 합치자 Git이 어느 쪽을 쓸지 몰라서 <<<<<<< HEAD, =======, >>>>>>> change-title 표시를 파일에 남겼다. 에디터로 파일을 열어 이 표시 줄을 모두 지우고 원하는 제목 한 줄만 남겨 저장했다. 그 뒤 git add title.md로 해결했다고 알리고 git commit으로 합치기를 마무리했다.

\- git-mentoring에서 매주 `main` 에서 새 브랜치를 만드는 이유: 주차마다 작업을 분리하기 위해서다. 한 주 작업이 다른 주 작업과 섞이지 않고, PR을 주차별로 따로 보낼 수 있다. 항상 최신 main에서 시작하면 다른 사람이 머지한 내용을 포함한 채로 작업해서 충돌도 줄어든다.

\- 이번 주 소감: 오타 때문에 의도하지 않은 충돌이 나서 당황했지만, merge --abort와 reset으로 되돌려 보면서 Git이 생각보다 안전하다는 것을 느꼈다. 충돌 표시를 직접 지워 가며 해결해 보니 충돌이 무서운 게 아니라 Git이 사람에게 선택을 맡기는 과정이라는 걸 이해했다.

