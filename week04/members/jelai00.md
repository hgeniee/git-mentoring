# 제혜린

- GitHub ID: MY-ID
- 내 git-practice 저장소 주소: https://github.com/jelai00/git-practice
- `git remote -v` 결과:
  ```
origin  https://github.com/jelai00/git-practice.git (fetch)
origin  https://github.com/jelai00/git-practice.git (push)

  ```
- 실습 5 이후 `git log --oneline` 결과:
  ```
a7631cb (HEAD -> main, origin/main, origin/HEAD) Add: 웹에서 hello.md 수정
0ca4b5e Remove extra line from hello.md
87d7243 Update hello.md
a96c4ab Add:명령어 목록에 push 추가
2367ed6 Add: 배운 명령어 목록 추가
ae79e98 Add: hello.md에 실습 기록 추가
0942675 Ass: hello.md추가


  ```
- 로컬 저장소와 원격 저장소를 내 말로 설명하기:
- git-mentoring의 `origin` 과 `upstream` 은 각각 어디를 가리키는지: origin은 내가 fork한 내 레포(jelai00/git-mentoring)이고, upstream은 fork의 원본 레포(hgeniee/git-mentoring). 나는 origin에만 push할 수 있고, upstream에는 PR로 반영을 요청함.
- `git push -u origin main` 에서 `-u` 를 붙이는 이유:로컬 main과 원격 origin/main을 연결(추적 브랜치 설정)해 두기 위해서이다. 한 번 설정해 두면 그다음부터는 git push나 git pull만 쳐도 어디로 보낼지, 어디서 받을지 Git이 알아서 처리해요.
- `git pull` 이 하는 일: 원격에서 내 레포로 가져오기
- 이번 주 소감:로컬에는 있는데 원격에는 없는 상태를 git remote -v로 확인하였다. 