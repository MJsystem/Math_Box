# 수학 계산을 위한 코드를 제공하는 프로젝트
**1. calculator.py** : `계산기`에 있는 기능들을 제공하는 모듈
- add, substract 등



<커밋 다루기>

1.커밋 히스토리 살펴보기
프로그래밍을 하다 보면 커밋 히스토리를 활용해야 할 일들이 생긴다! 

지금까지의 커밋 = '커밋 히스토리'
커밋 히스토리를 부르는 커맨드 = git log <- 여기서 커밋은 새로운 게 맨 위임.
commit 뒤에 나오는 건 '커밋 아이디' (커밋 해시)

나오는 게 너무 많아 복잡하다면, '커밋 히스토리 깔끔하게 보기' -> git log --pretty=oneline <- 커밋 당 한 줄로 출력해달라는 의미!

*** FUCK! git log 하고 ctrl c 로 나가면 loop에 빠져 문제 발생 - text disappear - 해결 위해서 reset 이용 -> git log 후 나갈 때는 q + enter / :q + enter whatever possible

git log는 commit message와 날짜밖에 모르는 게 아쉬워! 구체적인 변경 사항이 보고 싶다면
-> git show 커밋 아이디
커밋 아이디는 다 칠 필요 없이, 앞의 4자리 정도만 쳐주면 된다. (겹치면 안 되지만 그럴리는 커밋이 정말 많지 않는 이상 없음)


2. m 옵션 없이도 커밋 메시지를 남기는 법!
git commit 만 입력한다. 그러면 commit message 입력하는 창으로 간다. 다 입력한 후, esc 하고 :wq 엔터!

-m 옵션 없이 git commit 만으로 텍스트 에디터에 커밋 메시지를 남기는 것은,
"복잡하고 긴 커밋 메시지를 쉽게 남길 수 있다"는 점에서 유용하다.

3. 최신 커밋 수정하기
만약 최신 커밋에 오류가 있다면, 고치고 커밋하면 되겠지만 그러면 불필요한 커밋 하나가 생기는 것
-> 그래서 git 에는 최신 커밋을 수정하는 기능이 있다!

수정하고,
git add . 하는 것 까지 동일.
*git commit --amend 입력*
그러면 다시 commit message 입력하는 창으로 이동 ->여기서 커밋 메시지 역시 수정할 수 있음

--amend : 최신 커밋 수정하기 기능 커맨드


4. 커밋 생성, 커밋 메시지 작성 가이드라인

>>>> 커밋 메시지 작성 가이드라인
(1) 상세한 설명이 필요할 때는 커밋 메시지에 제목과 상세 내용을 적자. (그러려면 길게 작성하기 좋게 어디로 이동해야겠어?)

제목 하고 한 줄 띄고 상세 내용 쓰는거임. 이렇게 ->
Add one function

calculator.py supports 3 functions now

(2) 제목 뒤에 . 붙이지 말 것

(3) 제목의 첫 번째 알파벳은 대문자로 작성할 것

(4) 제목은 명령조로 작성할 것(Fix it) Not (Fixed it, fixes it)

(5) 커밋의 상세 내용에는 다음과 같은 것을 담아라
> 왜 커밋을 했는지
> 어떤 문제가 있었고
> 적용한 해결책이 어떤 효과를 갖는지

(6) 최대한 친절하게 작성할 것!

>>>> 커밋할 때의 가이드라인

(1) 하나의 커밋에는 하나의 수정사항, 하나의 이슈를 해결한 내용만 남겨라. 다양하게 수정하고 그걸 모두 하나의 커밋으로 남기는 건 좋지 않다. 
즉, 작은 단위의 변화를 기준으로 커밋을 하라는 의미.

(2) 현재 프로젝트 디렉토리 상태가 그 전체 코드를 실행했을 때 에러가 발생하지 않는 경우에만 커밋하기


** 나중에 다시 봤을 때 이해하는 데 어려움이 없도록
** 다른 동료 개발자와 협업하는 데 방해가 되지 않도록


5. 긴 커맨드에 alias 설정하기
git log --pretty=oneline 이게 너무 길어!
git history 만 쳐도 실행되게 하고 싶다면,

aliasing을 하자.

방법) git config alias.history 'log --pretty=oneline'

만약 이 프로젝트뿐만 아니라 이 기기에서 하는 모든 프로젝트에서 쓰고 싶다면, (user.name 이나 user.email config 할 때도 쓸 수 있음. config 할 때는 다 쓸 수 있음)

git config --global alias.history 'log --pretty=oneline'

하면 되겠지!

+ 

https://johngrib.github.io/wiki/git-alias/ 
alias 관련 꿀 설정들이 있다. 학습이 끝난 후 활용하면 좋을 듯 하다.


-- alias 정보 담기는 곳
alias 의 경우 만약 --global 옵션으로 특정 사용자가 생성하는 모든 프로젝트에서 alia 를 적용하는 경우엔 .gifconfig 파일에,
특정 프로젝트에만 alias 를 적용했다면(강의노트 내용대로) 해당 프로젝트의 .git/config 에 alias 설정이 되어 있을 것입니다.
그러므로 이 파일을 백업하거나 파일에서 일부를 따로 저장하셔도 될 것 같아용.
.gitconfig 파일 위치는 
unix 계열에서는 ~/.gitconfig
window 에서는 c:\Users\사용자\.gitconfig
에 파일이 있을 것입니다^^

6. 두 커밋 간의 차이 보기
커밋 히스토리를 보는데 특히 어떤 두 커밋 사이의 변화가 궁금하다면,

git diff 더오래전커밋아이디 비교할커밋아이디
이 순으로 입력해주면 

git show 커밋아이디
한 것처럼 변화를 알려준다.

7. HEAD의 의미
커밋 히스토리를 보니, 맨 위 (가장 최근) 커밋에 HEAD라고 적혀 있음.

HEAD : 가장 최근에 한 커밋을 가리킴

HEAD의 존재 - working directory의 내용을 결정한다.

따라서, 만약 HEAD가 가장 최근의 커밋이 아니라 그 이전의 커밋을 가리킨다면 working directory의 내용물은 그 커밋 기준으로 구성되겠군!

8. 이전 커밋으로 git reset 하기
HEAD의 존재가 working directory를 결정한다면, HEAD를 옮겨서 reset할 수 있겠군! -> git reset

git reset --hard (가고 싶은 커밋의 아이디 - HEAD 옮기고 싶은 커밋 아이디)

--hard는 git reset의 옵션 중 하나.

오 진짜 파일 내용 reset 됐다. 

git reset : 과거 커밋으로 아예 돌아가고 싶을 때 사용한다. 


9. git reset 꼭 알아야 할 2가지
1) git reset을 쓸 때 --hard는 무엇이었을까?
--hard, --soft, --mixed 가 있음. 어떤 옵션을 쓰던 HEAD가 과거의 커밋을 가리키게 되는데 working directory의 내부도 바뀌는 건 --hard 뿐! 다음 시간에 자세히

2) staging area에 있던 것들은 커밋하고 나면 어떻게 될까?
-> 그대로 있지. git add를 할 때마다 새로운 파일이 추가 되거나 원래 있던 파일이 새로운 버전으로 교체되는 것 뿐, 사라지지 않는다.
(당연한 것 아닌가? 그래야 modified도 체크할 수 있고, 애초에 다른 영역이니까!)

staging area에 있던 것들은 커밋을 하더라도 그것과 상관없이 계속 남아 있다!


10. git reset의 3가지 옵션 
표를 생각하자. 
3가지 옵션은 git의 세 가지 작업 영역 중 몇 개의 영역까지 원하는 시점의 커밋 기준으로 reset을 하느냐로 구분된다.
(--soft < --mixed < --hard)

working directory, staging area, repository

이 3가지 옵션 중에서 원하는 방향에 따라 결정하여 사용하면 됨.

실무에서 --hard 옵션 같은 경우는 자주 사용되지 않는데, reset 시점 이후의 모든 자료가 사라져버리기 때문. 따라서, 모든 자료가 사라져도 괜찮은 상황이 아니라면 --soft, --mixed를 쓰는 게 권장 됩니당.

직접 실습해본 바, 

--soft -> git history 에서만 변화가 있다. 

--mixed -> git history, git status 에서 변화가 있다.

--hard -> git history, working directory 에서 변화가 있고, git status를 해도 바뀐 게 없다고 나온다. (그렇지 staging area도 그 커밋 기준으로 바뀌었으니까..)

지워놓고 보니, 커밋 돌려놓고 싶다면? 깃허브 remote repository에서 가져오면 되지! -> git pull

git push 자주자주 하쟈. 이게 백업으로서의 깃헙!

11. HEAD를 기준으로 git reset하기

매번 커밋 아이디로 reset 하기 귀찮은 당신을 위해!
HEAD가 있는 커밋 바로 밑 커밋 지칭 - HEAD^
HEAD가 있는 커밋 밑에서 n번째 지칭 - HEAD~n



