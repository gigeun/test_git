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







