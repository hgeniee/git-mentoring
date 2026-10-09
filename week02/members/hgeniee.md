# 이현진 (튜터 예시)

- GitHub ID: hgeniee
- 운영체제: Windows
- `git --version` 결과: git version 2.55.0.windows.5
- `git config --global --list` 로 확인한 설정:
  - user.name: hgeniee
  - user.email 등록 여부: O
  - init.defaultbranch: main
- 실습 폴더에서 `git init` 후 `git status` 첫 줄: On branch main
- `git init` 과 `git clone` 의 차이를 내 말로 설명하기:
  `git init` 은 내 컴퓨터의 빈 폴더를 **새 Git 저장소로 만드는 것**이라 기록이 하나도 없는 상태에서 시작하고,
  `git clone` 은 GitHub에 **이미 있는 저장소를 기록째 내려받는 것**이라 원격 저장소(origin) 연결까지 자동으로 된다.
- PAT를 비밀번호처럼 다뤄야 하는 이유:
  PAT만 있으면 누구든 내 계정 권한으로 저장소에 push하거나 삭제할 수 있기 때문이다. 그래서 만료일을 정해 두고, 필요한 권한(scope)만 준다.
- 이번 주 소감:
  1주차에 따라 쳤던 설정 명령어들을 하나씩 다시 짚어 보는 주예요. `git config --list` 로 내 설정을 스스로 확인할 수 있으면 다음부터 막혀도 혼자 원인을 찾을 수 있어요!
