## git은 버전관리시스템이다.
>*SVN 과 GIT 의 차이점은 SVN은 중앙집중식 버전관리 라면  GIT은 분산 버전관리 시스템이다.*

#### 오늘 공부한 명령어
*git --version : git 버전 확인

*git init : git 저장소 생성

*git status : 현재 변경사항을 조회

*git add file : 로컬디렉토리에서 파일을 스테이징 영역에 올려 놓는다.

*git commit -m "message" : 스테이징에 올라간 파일을들 커밋한다.
즉 로컬 저장소에만 반영을 한다는것을 말한다. 원격서버에는 아직 올라가지 않은 상태이다.

*git diff : 작업트리와 스테이징영역에 대한 차이점을 보여줍니다.
--cached 옵션을 추가하면 스테이징 영역과 저장소의 차이점을 보여준다.
```
$ git diff --cached
diff --git a/GITHUB/diff_Test.txt.txt b/GITHUB/diff_Test.txt.txt
new file mode 100644
index 0000000..e69de29
```
ex) 테스트용으로 파일을 만들고 해당파일을 add 한 상태이다.
git diff HEAD를 입력하면 작업트리, 스테이징 영역, 저장소의 차이점을 모두 보여준다.

// git change
git add / git commit 의 상태확인 과 취소방법

git add 한 파일들 확인방법 : git status

git add 취소하는 방법 : git reset HEAD 파일명
git add 전제 취소하는방법 : git reset HEAD

git commit 한 파일들 확인방법 : git log를 치면 commit한 기록들이 전부 나오게 된다.(해당 레파지토리 내용만)

git reset --soft HEAD^ : commit 한 파일들을 전부 staged 상태로 이동시킨다.
git reset --soft HEAD~1 : 마지막으로한 commit 1개의 파일을 staged 상태로 이동시킨다.
git reset --mixed HEAD^ : commit한 파일을 취소하고 unstaged 상태로 이동시킨다. (unstaged 상태는 add 를 하기 전의 상태이다)
git reset HEAD^ : 위의 기능과 같다.
git reset HEAD~2 : 마지막 두개의 commit을 unstaged상태로 이동시킨다.

git reset --hard HEAD^ : commit을 취소하고 해당파일을 unstaged상태로 워킹 디렉토리에서 파일을 삭제한다.

git reset --hard HEAD : 마지막 commit이후의 워킹 디렉토리와 add 했던 파일들이 모두 사라진다. (즉 commit 과 add 했던게 다 사라진다. 마지막 commit 기준으로)


// git stash
git stash 란 현재 작업하고 있던일을 잠시 임시저장 하는 느낌의 명령어이다.

git stash명령을 사용하면 기존에 작업하던일을 저장한다.

기존 작업파일을 임시로 저장 : git stash

임시 저장 파일 확인 : git stash list

임시 파일 가져오기 : git stash apply

임시파일 일부만 가져오기 : git stash apply [stash 이름]

임시파일 가져올시 staged 상태로 가져오기 : git stash apply --index

임시파일 삭제 : git stash drop / git stash drop [stash 이름]
