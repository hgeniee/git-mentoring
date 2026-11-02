# 김선형

- GitHub ID: linearmik
- 내 git-practice 저장소 주소: https://github.com/linearmik/git-practice
- git remote -v 결과: 
  origin  https://github.com/linearmik/git-practice.git (fetch)
  origin  https://github.com/linearmik/git-practice.git (push)
- 실습 5 이후 git log --oneline 결과: 
  91a21c6 (HEAD -> main, origin/main, origin/HEAD) "Add: 명령어 목록에 git push 추가"
  73689f2 Add: 명령어 목록에 git push 추가
  9dc7905 Add: 명령어 목록에 git push 추가
  8c7466a Add: 배운 명령어 목록 추가
  f39e5c2 Add: hello.md에 실습 기록 추가
  5ab7f3c Add: hello.md 추가
- 로컬 저장소와 원격 저장소를 내 말로 설명하기: 로컬 저장소는 내 컴퓨터의 .git 폴더에 있는 기록이고, 원격 저장소는 GitHub처럼 인터넷에 있는 기록이다. 둘은 자동으로 맞춰지지 않아서, 내가 push 로 올리고 pull 로 받아와야 같아진다.
- git-mentoring의 origin 과 upstream 은 각각 어디를 가리키는지: origin 은 내가 Fork한 내 저장소(linearmik/git-mentoring), upstream 은 튜터의 원본 저장소(hgeniee/git-mentoring)를 가리킨다. 나는 원본에 직접 push할 수 없어서 origin 에 push하고, 최신 과제는 upstream 에서 pull 받는다.
- git push -u origin main 에서 -u 를 붙이는 이유: 내 main 과 origin/main 을 짝지어 두려고. 한 번 해 두면 다음부터는 git push, git pull 만 쳐도 되고, git status 가 "GitHub보다 커밋이 몇 개 앞서 있는지"도 알려 준다.
- git pull 이 하는 일: 원격 저장소의 새 커밋을 받아와서 내 브랜치에 합친다. 실습 5에서 웹으로 고친 줄이 git pull 후에 내 hello.md 에 생겼다.
- 이번 주 소감: 터미널에서 `code` 명령어가 안 먹혀서 살짝 식겁했지만 결국 꿋꿋이 헤쳐나갔다! 3주 동안 로컬에만 꽁꽁 숨어 있던 커밋들을 드디어 GitHub 원격 저장소로 시원하게 날려 보내고 sync를 맞추니까 속이 다 시원하다. 앞으로 push랑 pull은 절대 안 까먹을 것 같다.
