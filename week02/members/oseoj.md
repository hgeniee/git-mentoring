GitHub ID: oseoooojin

운영체제: Windows

git --version 결과: (실제 출력 결과 입력)
git version 2.44.0.windows.1

git config --global --list 로 확인한 설정:

user.name: oseooojin

user.email 등록 여부: O

init.defaultbranch: main

실습 폴더에서 git init 후 git status 첫 줄: On branch main

git init 과 git clone 의 차이를 내 말로 설명하기:

git init은 내가 만든 폴더를 새로운 Git 저장소로 설정하는 것이고, git clone은 GitHub 등에 이미 만들어져 있는 저장소를 내 컴퓨터로 가져오는 것이다. 즉, init은 새로 시작할 때 사용하고 clone은 기존 저장소를 가져올 때 사용한다.

PAT를 비밀번호처럼 다뤄야 하는 이유:

PAT는 GitHub에서 사용자 인증을 할 때 사용하는 토큰이다. 다른 사람에게 노출되면 토큰에 부여된 권한으로 내 저장소에 접근할 수 있기 때문에 비밀번호처럼 안전하게 관리해야 한다.

이번 주 소감:

1주차에는 Git 명령어를 따라 입력하면서 과제를 제출했다면, 이번에는 각 명령어의 역할을 조금 더 이해할 수 있었다. 특히 git init과 git clone의 차이를 직접 실습하면서 알게 되었고, Git의 사용자 정보와 기본 브랜치 설정을 확인하는 방법도 배울 수 있었다.