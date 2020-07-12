1. 브랜치란?

나무가 뿌리에서 줄기, 그리고 여러 개의 가지(branch)로 나뉘어지듯이 git 역시 마찬가지. (그래서 맨 처음 커밋을 root commit 이라고 함.)

우리가 프로젝트를 하다 보면 하나의 가지로만 나아가는 경우는 거의 없음. 예로 들면, 유료 + 무료.

유료는 무료와 크게 다르지 않으므로, 하나의 프로젝트 내에서 두 개의 가지를 뻗어 나갈 수 있음. 유료 버전, 무료 버전으로.

git status 쳐 보면 On branch master 라고 뜸.
마스터 브랜치 - 레포지토리를 만들고 커밋을 하면 자동으로 생기는 브랜치 (기본 브랜치)

commit history를 보면 나오는 흐름이 branch.
HEAD -> master (여기서의 master 가 master branch)

브랜치 만들기 -> git branch [브랜치 이름]

브랜치를 만들면 여기에도 지금까지의 프로젝트가 담긴다.

그다음에 꼭 해야 할 것이 브랜치로의 이동 : git checkout premium
오 그렇게 하니까 원래 git에 맨날 뜨던 줄 (master) 가 (premium) 으로 바뀌네!!

이제 작업을 하고 커밋을 하면 premium branch 에만 반영되는 것. master branch는 그대로야. 그러니까 기존에 있는 것들을 premium을 위해 바꿔도 되는 거지.
