# 김선형

- GitHub ID: linearmik
- 운영체제: macOS
- `git --version` 결과: git version 2.52.0
- `git config --global --list` 로 확인한 설정:
  - user.name: linearmik
  - user.email 등록 여부: O
  - init.defaultbranch: main
- 실습 폴더에서 `git init` 후 `git status` 첫 줄: 현재 브랜치 main
- `git init` 과 `git clone` 의 차이를 내 말로 설명하기: `git init`은 내 컴퓨터의 폴더에 `.git`을 만들어서 빈 저장소를 새로 시작하는 것이고, `git clone`은 이미 존재하는 원격 저장소를 커밋 기록과 원격(origin) 연결까지 통째로 내 컴퓨터에 복사해 오는 것이다. init은 기록이 없는 상태에서 시작하고 원격도 직접 연결해야 하지만, clone은 받자마자 기존 기록과 origin 설정이 다 들어 있다.
- PAT를 비밀번호처럼 다뤄야 하는 이유: PAT는 비밀번호 대신 내 계정으로 인증해 주는 토큰이라, 유출되면 다른 사람이 내 권한으로 저장소를 읽고 push하거나 삭제할 수 있다. 그래서 코드나 커밋, 채팅에 그대로 올리면 안 되고, 필요한 권한만 주고 만료 기간을 설정해야 하며, 노출되면 바로 폐기하고 새로 발급해야 한다.
- 이번 주 소감: `git config`를 입력하다가 `user`를 `useer`로 오타 냈는데 에러 없이 그대로 저장돼서, `git config --list`로 확인하기 전까지 설정이 안 바뀐 줄 몰랐다. 명령어를 치고 끝내는 게 아니라 결과를 꼭 확인해야 한다는 걸 배웠다. 전역 설정과 저장소별 설정이 따로 있다는 것도 list 출력을 보면서 알게 됐다.