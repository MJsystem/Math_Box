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

License 파일 바꾸고 commit 해준 다음
git checkout master 로 해서 다시 마스터 브랜치로 갔더니,
원래의 License 그대로. 이게 브랜치구나 같은 프로젝트에서 다른 방향으로 만들어 나가는. (유료 버전, 무료 버전으로 나뭇가지 2개로 갈라진 것)

2. 브랜치 다뤄보기
   git branch -> 존재하는 브랜치 목록

브랜치를 만들고 지워 보자.

git branch test <- 이건 저번에 했었지>

git branch -d test <- 옵션 d는 delete의 약자>

test 사라짐 ㅅㄱ링

Tip) 우리는 브랜치를 만들면 그 브랜치로 바로 이동하는 경우가 많은데, 이를 한 번에 하는 방법은 바로
git checkout -b test
-b 옵션은 branch의 약자. branch 하고 바로 checkout 하라는 의미가 된다.

3. 브랜치 merge 하기

무료 버전에 기능을 추가했더니, 회사에서 무료 버전에 있는 기능은 무조건 유료 버전에 있어야 한다고 했다고 생각해보자.

직접 무료 버전에 쓴 거 복사해서 유료 버전에 넣고 커밋해도 되겠지만, 깃에서는 한 브랜치에서 한 커밋을 그대로 다른 브랜치에 적용하는 기능이 있음 - branch merge

master 브랜치에 있는 걸 premium 브랜치로 가져와야 겠군! -> git checkout premium -> git merge master
: 현재 내가 있는 premium branch에 master branch를 합치겠다는 의미.

이렇게 merge는 다른 브랜치에서 한 커밋을 이 브랜치로 가져오고 싶을 때 활용하는 것 -> 나도 이 강의 들으면서 필기한 md 파일들마다 매번 merge 조져야겠다.

4. merge할 때 conflict가 날 수도 있어요!

master branch 에서는 divide_free 로
premium branch 에서는 divide_premium 으로 바꾸고 git merge master 했더니,
conflict 발생! -> 그 파일로 가보면, current change 가 현재 있는 branch(이 상황에선 premium branch)에서 수정한 바이고, 밑에 있는 change가 merge 하려는 branch에서의 변동 사항

git에서 이렇게 각기 다른 변화를 만나면 conflict. 어떤 변화를 반영할 것인지 사용자가 직접 정해주어야 함.

둘 중에 하나를 정해도 되지만, 아예 다 지우고 새롭게 정보를 줘도 됨. Conflict는 그저 양쪽에 모두 변동 사항이 있어서 발생하는 것이기에.

Conflict가 났다고 당황하지 말자. 자주 일어나는 일이니까

-1 컨플릭트가 발생한 파일을 연다
-2 merge의 결과가 되었으면 하는 모습대로 코드를 수정
-3 커밋

5. conflict가 났을 때, 일단 merge 취소할 수 있다!

git merge --abort
abort 옵션은 중단한다는 의미. git 사용하다보면 이 단어 자주 보이던데, 중단한다는 의미임.

6. 용어 설명

== git remote add origin https://github.com/kyuri-dev/Math_Box.git

remote 레포지토리를 add (등록) 하겠다. origin이란 이름으로, 주소에 있는 리모트 레포지토리를.

origin 이라고 하는 건 국룰. 이걸 나중에 clone해가고 쓰고 할 때 가장 근원이 되는 레포지토리라는 의미인 듯하다.

== git push -u origin master

push 하겠다. -u (set upstream) 옵션을 주어서 origin 이라는 이름의 remote 레포지토리에 master 라는 로컬 레포지토리의 커밋을!

upstream 이란, track 하겠다는 의미임. >> git push 만 해도 알아서 로컬 master 브랜치에서 리모트 master 브랜치로 가는 거야. 브랜치끼리 추적을 하는 거지.

== origin/master의 의미
로컬 레포지토리의 master 브랜치 , 리모트 레포지토리의 master 브랜치
이걸 구분해주는 건 이름

로컬에서는 굳이 다른 게 필요 없이 그냥 master,
리모트 거는 로컬에서 볼 때 이게 origin의 master 브랜치니까, origin/master

git history 해보면 알 수 있다!
