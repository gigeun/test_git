 # test_git
 테스트 기록

----------------------------------------------------------------------------------------------------------------

 # git_bash 사용

 ### git bash 란

 * Git Bash란 컴퓨터 OS와 상관없이 리눅스 베이스 터미널용 Git을 말한다.
 
 <br>
  
 ### https://git-scm.com/downloads 에서 다운로드 및 설치
 
 ### 특정 위치에서 git terminal 호출 
 
 * 저장 할려는 위치에서 git-bash 호출 하거나 cd 명령어로 이동 또는 마우스 우클릭 Git Bash Here

<br>


![](https://kikuen.github.io/pana/img/bash.png)

<br>

 ### Git Bash에서 사용되는 Linux-base 기본 명령어 
 
 * 기본 명령어 설명
 	+ 명령어 --help
 		- $ ls --help
 
 * 파일 브라우징
	+ 파일 목록 ls :  (list) -l(자세히) -a(숨김파일까지)
	 	- $ ls
	 	- $ ls -l
	 	- $ ls -a
	 	- $ ls -l -a
	+ 디렉토리(폴더) 이동 cd :  (change directory)
		- $ cd ../
		- $ cd test_git
		- $ cd ./test_git
	+ 현재 작업중인 디렉토리 pwd :  (print working directory)
		- $ pwd
		
 *  권한 확인
	+ ls -l
	
	+ -|rw-|r--|r-- root(소유자) root(소유그룹) test(파일이름)
	+ 1 234 567 890
	
		- 1 - 파일의 형식 ( l: link, d: directory, - : file ) 
		- 234 - 소유자의 권한
		- 567 - 소유그룹의 권한
		- 890 - 나머지 사용자들의 권한
		
	+ 3가지 권한 - r(read 읽기), w(write 쓰기), x(execute 실행)
		- 숫자로 권한 표시 r: 4, w: 2, x: 1
		- ex) 644 권한
		- ex) 최고권한 = 777
		
 * 파일 조작
	+ 파일 생성 touch 
		- $ touch test.txt
	+ 파일 복사 cp (copy)
		- $ cp test.txt ../copy.txt
		- $ ls -l
		- $ cd ../
	+ 파일 이동 mv (move)
		- $ mv copy.txt ./git_test
		- $ ls -l
	+ 파일 삭제 rm (remove)
		- $ cd ./git_test
		- $ rm copy.txt
		- $ ls -l


 * 디렉토리 조작
	+ 디렉토리 생성 mkdir ( make directory )
		- $ mkdir test
	+ 디렉토리 삭제 rmdir ( remove directory ) - 빈 디렉토리
		- $ rmdir test
	+ 디렉토리에 파일이 존재할 경우 내용까지 삭제 rm -r ( r 옵션으로 내용까지 모두 삭제 )
		- $ rm -r test

* 파일 내용 조회(concatenate:연결하다 또는 catenate:연결하다 암기하다)
	+ 전체 내용 출력 cat ( 터미널 창으로 출력 )
		- $ cat test.txt
	+ 파일의 앞부분 head ( 기본 10줄 )
		- $ head test.txt
		- $ head -n 5 test.txt 
	+ 파일의 뒷부분 tail
		- $ tail test.txt
	
 * 파일 편집기
	+ 파일 편집 호출 **vi** **파일이름**
	+ 명령 모드 / 입력 모드 두가지 모드로 진행
	+ vi 진입 - 명령 모드 
	+ 입력 모드 진입 : a, i  ( --끼워넣기-- )
	+ 명령 모드 진입 : esc
	+ 저장하고 종료 : : wq
	+ 저장하지 않고 종료 : q
		- 편집 사항이 있을 경우 - :q!
	+ 명령 모드
		- 행 번호 표시 : :set number
	  	- 한 줄 삭제 : dd
		- 한 줄 복사 : yy
		- 붙여넣기 : p
		
-----------------------------------------------------------------------------------------

 ### git 원격 명령 실행을 위한 준비
 
 * git_hub Page 에서 등록 한 repositories 이름 등록
	+ $ git config --global user.name "test_git"
	
 * git_hub Page 에서 등록 한 사용자아이디(이메일) 등록
	+ $ git config --global user.email "hap0p9y@nate.com"
	
 * git 초기화 
	+ $ git init
	
 * git_원격지 와 연결 - repository 등록 후 code 탭에서 확인 가능
	+ $ git remote add origin https://github.com/kikuen/test_git.git
	
 * 원격지 연결 후 정보 확인
	+ $ git remote -v

 ## 명령어 

 ### Add
 * 저장소에 파일 추가(staged:무대에 오르다) - 무대에 올리다.
 * (현재 디렉토리 안에 모든 파일 추가) 
 	+ git add .   

 * (특정 파일만 추가)
 	+ git add [경로/파일이름]


 ### commit
 * 무대에 올린(staging한) 파일 커밋
 <br> 커밋시 메세지 추가(추가된 파일에 대해 타인이 알아볼 수 있도록 전달되는 간략한 메세지)
 	+ git commit -m '커밋메세지'


 ### push
 * 원격 저장소로 push
 <br/> git push [원격저장소 이름][원격저장소 브런치 이름]
 	+ git push origin master


 * branch-분점 - 나뉘다
 	+ 로컬 저장소의 변경사항을 원격 저장소(origin)의 브런치(master)에 반영


 ## 실습

 * README.md 파일 생성
 	+ $ echo "# git test reload README.md" >> README.md

 * 상태 확인
	 + $ git status

 * 반영 할 내용을 로컬 무대에 올림
 	+ $ git add README.md

 * 적용 시킬 내용 확인
	 + $ git status

 * 로컬에 적용
 	+ $ git commit -m "first commit"

 * 원격지에 적용
 	+ $ git push -u origin master

 * github repository로 가서 상태 확인

 * 파일 정보 직접 변경 후 반복


## 버전관리하기

 * sample 파일 생성
	+ $ touch sample.txt
	+ $ ls -l

 * sample 파일 수정
	+ $ vim sample.txt
	임의의 값 작성 후
	+ :wq

 * git 상태 정보 확인
	+ $ git status
	+ Untracked files:(use "git add <file>..." to include in what will be committed) sample.txt

 * 작업 트리에서 수정한 파일(sample.txt)을 스테이지에 추가
	+ $ git add sample.txt
	+ $ git status

 * 버전을 만드는 것을 ‘커밋한다’라고 함

 * 버전에 어떤 변경이 있었는지 메시지를 함께 기록해 둠. -m
	+ $ git commit -m "ADD sample.txt"

 * 저장소에 있는 버전(커밋)을 확인

 * 커밋을 만든 사람, 만든 시간, 커밋 메시지 등이 나타남
	+ $ git log

 * 버전을 변경하기 위해 파일 정보를 다시 수정
	+ $ vim sample.txt 

 * 커밋하려면 수정 내용이 있어야 하므로 vi 편집기에서 숫자 ‘2’ 입력 & 저장해서 sample.txt 파일 수정
	+ :wq

 * 스태깅과 동시에 버전 생성 
	+ $ git commit –am “MODIFY SAMPLE”
		- commit 명령에 (add를 의미하는) –a 옵션 추가. 
		- git commit –a –m 처럼 옵션을 따로 써도 됨.
		- 스테이징과 커밋을 한꺼번에 처리하려면 무조건 한번은 커밋했던 파일이어야 함.


 * 저장소에 있는 버전 확인
	+ $ git log

 * 빔 편집기에서 숫자 ‘2’ 를 ‘two’로 변경
	+ $ vim sample.txt

 * 수정한 파일과 저장소에 있는 파일 비교
	+ $ git diff

 * 수정한 내용으로 다시 버전을 만들려면 스테이지에 올린 후 커밋
 * 수정한 내용을 버리려면 git checkout 명령을 사용해 수정 내용 취소
	+ $ git checkout sample.txt

 * 되돌아간 내용 확인
	+ $ vi sample.txt


 * 버전을 만드는 각 단계마다 파일의 상태가 달라짐. 
 * 파일의 상태를 이해하면 현재 어느 단계인지, 그 상태에서 어떤 일을 할 수 있는지 알 수 있음
	
	+ tracked  : 버전을 만든 후에 깃에서 변경 내역을 추적 중인 상태 
	+ untracked  : 한번도 버전을 만들지 않은 상태 
	+ unmodified : 수정되지 않은 상태 (working tree is clean)
	+ modified : 작업 트리에서 수정한 후 아직 스테이지에 저장하지 않은 상태
	+ staged : 스테이지에 있고 아직 커밋하지 않은 상태


 * 스테이징 되돌리기
	+ 파일을 스테이지에 올린 상태에서 되돌리려고 할 때
	+ 파일 수정 후 스테이징 초기화
	+ $ vi sample.txt
	+ $ git add sample.txt
	+ $ git status
	+ $ git reset HEAD sample.txt
	+ $ git commint -m "미변경 확인"
	+ $ git push test_git main
	+ github 원격 저장소에서 확인해보면 스태깅이 취소 되었기 때문에 자료가 변경된게 수정되지 않음 확인

 * 최신 커밋 되돌리기
	+ $ git commit -a -m "최신 커밋 되돌리기"
	+ 커밋 버전 확인
	+ $ git log 
	+ $ git reset HEAD^
	+ 가장 마지막에 했던 커밋을 되돌리려고 할 때
	+ 커밋 취소와 함께 스테이지에서도 내려짐
	+ 사라진 버전 로그 확인
	+ $ git log


 * 작업 트리에서 수정한 파일 되돌리기
	+ github 사이트 history 또는 $git log 를 통해 버전 해쉬 코드 획득한 후 작성

	+ $ git reset --hard 버전해쉬코드
	+ 특정 버전 상태로 되돌리려고 할 때
	+ git log를 사용해 커밋 해시 확인한 후
	+ 해당 커밋 해시를 가진 커밋으로 리셋 & 이후 커밋은 삭제됨

 * 작업 트리에서 수정한 파일 되돌리기
	+ $ git revert  커밋해시
	+ 특정 버전 상태로 되돌리려고 할 때
	+ $ git log를 사용해 커밋 해시 확인한 후
	+ 해당 커밋 해시의 직전 커밋으로 돌아감 & 이후 커밋 그대로 유지


## 브런치
 * main 브랜치 : 깃에서 자동으로 만드는 기본 브랜치
 * 분기(branch) : main 브랜치에서 새 브랜치 만듦
 * 병합(merge) : 새 브랜치에 있던 파일을 main 브랜치에 합침


 * 저장소의 브랜치 확인 
	+ $ git branch

 * apple이라는 새 브랜치 만듦
	+ $ git branch apple

 * 변경 정보 확인
	+ $ git log

 * apple 브랜치로 이동 (apple 브랜치로 체크아웃한다고 함)
	+ $ git checkout apple
	+ main branch 커밋 내용들이 apple로 복사됨 

 * git log 명령어를 활용하여 내용 확인
	+ $ git log --online


 * main 에는 없고 apple에만 있는 버전을 확인
	+ $ git log main..apple


 * main 브런치로 변경 후 apple 에서 변경한 내용을 main 브런치에 병합
	+ $ git checkout main
	+ $ git merge apple

	+ log로 확인 main과 apple이 같은 commit을 가르킴
	+ $ git log --oneline 


