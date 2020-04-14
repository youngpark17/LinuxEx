# 리눅스 연습 구름IDE를 이용한 우분투+생활코딩 참고

## ls
현재 디렉토리의 파일 목록을 출력하는 명령어. 'ls -l'은 자세히 보기 파일의 리스트를 보자
'ls -a'
-rw-rw-r-- 1 root root    0  4월 14 05:37 empty_file.txt
drwxrwxr-x 2 root root 4096  4월 14 05:36 hello_linux
drw의 d는 디렉토리 라는 뜻
d가 안붙어있으면 파일.

## ls
-a 했을때 숨김파일도 나옴. .이 붙어있으면 숨김파일인거
숨김파일은 ls했을때는 안나옴

## pwd
현재 위치하고 있는 디렉토리를 알려주는 명령어

## mkdir
mkdir 새로 생성할 디렉토리명

mkdir -p dir1/dir2/dir3/dir4 (-p --;sparents)
형식으로도 가능.
touch
touch empty_file.txt

## cd
cd 이동할 디렉토리의 경로명

상대경로와 절대경로
상대경로는 현재 디렉토리의 위치를 기준으로 다른 디렉토리의 위치를 표현하는 것으로 ..은 부모 디렉토리를 의미합니다. 'cd ..'은 현재 디렉토리의 부모 디렉토리로 이동하는 명령이 됩니다. 참고로 현재 디렉토리는 '.' 입니다. 

절대경로는 최상위 디렉토리를 기준으로 경로를 표현하는 것을 의미합니다. 최상위 디렉토리는 루트(root) 디렉토리라고 하고 '/' 입니다. 'cd /'는 최상위 디렉토리로 이동한다는 뜻입니다. 'cd /home/egoing'은 현재 디렉토리가 무엇이건 언제나 '/home/egoing'을 의미하는데 이런 식의 경로 표현을 절대경로라고 합니다. 

## rm
rm 파일명
rm -r 디렉토리명

## --help
명령어 뒤에 --help를 붙이면 명령의 사용설명서가 출력됩니다. 

예 

ls --help
rm --help
mkdir --help
pwd --help

## cp
copy의 약자 cp abc.txt def.txt abc를 def로 이름 바꿔서 복사

cp abc.txt xyz
xyz라는 디렉토리가 없다면 abc.txt 파일을 xyz 파일로 복사합니다.
xyz라는 디렉토리가 있다면 xyz 디렉토리 안에 abc.txt 파일을 복사합니다.


## mv
move의 약자

mv abc.txt def.txt
abc.txt 파일을 def.txt로 이름을 바꾸어 이동합니다.
파일 이름을 바꾸는 것과 결과가 같습니다.

mv abc.txt xyz
xyz라는 디렉토리가 없다면 abc.txt 파일을 xyz로 이름을 바꾸어 이동합니다.
xyz라는 디렉토리가 있다면 xyz 디렉토리 안으로 abc.txt 파일을 이동합니다.\

## sudo

super user의 권한으로 활동할 수 있는 사용자라면 sudo 명령어를 붙여서
임시로 그 명령어만 super 유저의 권한으로 실행
관리자 권한 느낌인듯

## nano vi 편집기
^ -> 컨트롤키

## Package Manager(앱스토어 같은거)
### apt
apts-get update
sudo apt-get update 설치할 수 있는 프로그램의 최신 목록 업데이트

sudo apt-cache search htop
sudo apt-get install htop
htop은 작업관리자같은거 ... graphical 하게 보여줌
sudo apt-get upgrade htop
sudo apt-get remove htop