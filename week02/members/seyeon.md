# 김세연

- GitHub ID: gseyeon74
- 운영체제: Windows
- `git --version` 결과: git version 2.46.0.windows.1
- `git config --global --list` 로 확인한 설정:
  - user.name: seyeon
  - user.email 등록 여부: O
  - init.defaultbranch: main
- 실습 폴더에서 `git init` 후 `git status` 첫 줄: On branch main
- `git init` 과 `git clone` 의 차이를 내 말로 설명하기:
  `git init` 은 내 컴퓨터에 있는 폴더를 그 자리에서 새 Git 저장소로 만드는 것이라 커밋 기록도, 연결된 원격 저장소도 없는 빈 상태에서 시작한다.
  `git clone` 은 GitHub에 이미 있는 저장소를 커밋 기록까지 통째로 내려받는 것이라 받자마자 origin이 연결되어 있다.
  1주차에는 clone으로 받아서 바로 push가 됐는데, init으로 만든 `git-practice` 는 `.git` 폴더만 생기고 아직 올릴 곳이 없다는 게 차이였다.
- PAT를 비밀번호처럼 다뤄야 하는 이유:
  PAT는 비밀번호 대신 쓰는 값이라 이것만 있으면 다른 사람도 내 계정 권한으로 저장소에 push하거나 지울 수 있다.
  그래서 과제 파일이나 스크린샷에 남기면 안 되고, 만료일을 정하고 필요한 권한(repo)만 주는 게 안전하다.
- 이번 주 소감:
  `git config --global --list` 로 확인해 보니 user.name, user.email은 있었는데 init.defaultBranch는 설정이 안 되어 있어서 이번에 main으로 추가했다.
  그리고 내 PC는 `~` 가 `C:\Users\내이름` 이 아니라 다른 폴더로 잡혀 있어서 `pwd` 로 위치를 확인하는 게 왜 중요한지 알게 됐다.
