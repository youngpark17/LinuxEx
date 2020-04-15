# 리눅스 연습 구름IDE를 이용한 우분투+생활코딩 참고


## 왜 CLI 인가?
1. GUI는 에너지를 많이 먹는다. 따라서 서버컴퓨터나 데이터 관련 컴퓨터는 CLI 사용
2. GUI 방식은 쉽지만 순차적으로 진행되는 일을 자동화 하기는 힘들다. CLI의 강력한 효과는 순차적으로 실행
mkdir why; cd why; 즉 디렉토리를 만들고 들어가는게 아니고 미리 이렇게 지정해놓을 수 있다.
즉 중간과정에 컴퓨터를 지켜보고 있을 필요가 없다.
mkdir이 매우 시간이 오래걸리는 명령이라면... 2번이 아주 효과적
3. 파이프라인
ls --help | grep sort
| 파이프
grep은 필요한거 찾는 명령어
| 파이프를 통해 프로그램과 프로그램을 연결.
ps aux | grep apache



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

## 파일 다운로드(wget)
url 을 통해 다운 url을 알아야 함
wget url
wget -O (파일명) (url)

## IO Redirection

### standard output과 error
ls -l > result.txt
cat result.txt

unix Process(mkdir ls-l ps) 모니터로 출력되는 결과(standard output)을 redirection 시켜서 >(redirect기호)로 통해 방향을 바꿔서 저장 가능.
unix process는 standard output과 standard error로 구분 >(1>)는 standard output만 redirection standard error의 redirection은 (2>) 사용해야함.

하이브리드 rm rename2.txt 1> result.txt 2> error.log

### standard input
cat 엔터를 누르고 입력하면 계속 input으로 받아들임
cat종료하고싶으면 control+d
cat < result.txt 는 standard input으로 받은거 
cat hi 는 인자로 받은 것
![unix process](./unixprocess.png)
IO스트림

>> 는 redirection한 결과를 뒤에 append
ls -l > /dev/null 결과를 쓰레기통으로


## SHELL vs KERNEL
쉘 : 사용자의 명령 해석해서 커널로 보냄
커널 : 하드웨어 동작시킴.

## bash vs zshell
echo $0 을 통해 지금 사용중인 shell 파악.
bash 와 zshell 은 부모가 같지만 zshell은 bash에 비해 추가가능
zshell이 더 유연한 듯?

## 쉘스크립트 실습
touch a.log b.log c.log 빈 파일 생성

#!/bin/bash
if ! [ -d bak ]; then
	midir bak
fi
*.log bak

backup에 대한 권한
chmod +x backup
-rw-rw-r-- 이
-rwxrwxr-x 로
x는 exacutable

## 디렉토리 구조
/bin - user binarines (실행 가능한 프로그램, 사용자들이 사용하는 명령)
/sbin - System binaries(reboot, shutdown... 시스템 관리자가 사용)
/etc - configuration file, 설정 파일
/dev - device files
/proc - process information
/var - variable files 내용이 바뀔수 있는 파일 ex log파일
/tmp - temporary files 임시로 저장.
/home - cd ~ home디렉토리로감.
/boot
/lib bin과 sbin에서 사용하는 라이브러리가 보관되어있는 파일
/opt
/usr bin, sbin 있음.. 우리가 따로 다운받은건 user/bin or sbin 등에 저장

## 프로세스 모니터링
ps
ps aux 백드그라운드까지 보여줌
ps aux | grep apache 아파치를 포함하는 프로세스만 보여줌
말썽 부리면 sudo kill PID
sudo top
sudo htop 없으면 sudo apt-get install htop
load average는 프로세스의 점유율
첫번쨰는 1분 두번쨰는 5분 세번째자리는 15분의 평균
load average 8 5 3
인데 1분기준 코어가 4개면 부하가 많이 걸려있고 
1 3 2 면 코어가 4갠데 하나만 쓰는거

## 파일을 찾는 법

### locate 
*.log
확장자가 log인 모든 파일을 찾음
locate는 디렉터리가 아닌 데이터베이스를 찾음
mlocate를 뒤짐
### find
는 디렉터리를 뒤짐
성능은 좀 떨어지나 기능이 많다?
sudo find / -name *.log
find --help | head

### whereis
whereis ls
/bin/ls

$PATH 값을 통해 가져옴

echo $PATH 환경변수

## 백그라운드 실행
### 컨트롤+z 백그라운드로 넘기고
### fg(foreground)
fg %2

### kill %4
kll -9 %4
### &
백그라운드에서 실행시키는 명령어 ?

## CRON (정기적으로 실행)
### crontab
-e 수정
crontab expression 으로 검색
m h dom mon dow command
*/1 (1분에 한번) *(시간과는 상관x) * * * date >> date.log 2>&1

## 쉘을 시작할 때 실행
alias l='ls-al'^C
alias ..='cd..'

## 다중 사용자

### id
### who
이 컴퓨터에는 누구누구가 접속해있는가

## 관리자와 일반 사용자
슈퍼유저의 이름은 root
~#은 슈퍼유저
~$ 일반유저
### su
user ID를 바꾸거나 superUser가 됨

## 사용자 추가

## 권한
acess mode

-rw-/rw-/r--
오너의 권한/그룹의 권한/Other의 권한(운영체제의 등록되어있는 모든 사용자)
r : read
w : write
x : excute


### 권한을 변경
chmode o-r perm.txt(other의 read권한 뺸다 perm.txt파일에 대해)
chmode u+r perm.txt
chmod g+rwx file.txt

chmod go+r file.txt
그룹과 다른 사용자에게 읽기 권한을 준다

chmod 000 test.c

사용자, 그룹, 다른사용자의 모든 권한을 제거한다.

chmod 777 test.c

사용자, 그룹, 다른사용자의 모든 권한을 추가한다.

chmode 111 perm.txt도가능(0부터 7까지)

### 실행의 개념과 권한 설정
디렉토리의 실행권한이 cd명령어를 통해 못들어감


## 그룹

groupadd developer (그룹 생성)
!! 두번은 직전에 입력했던 명령어
sudo !!

## vi에디터 종료
esc 누르고 :wq는 저장하고 종료
:!q는 저장 안하고 종료
:w test.txt 파일명 없는 파일 이라면


## linux 인터넷
ping google.com
우분트 ping 안될때 apt-get install iputils-ping
윈도우는 4번보내지만 리눅스는 컨트롤c누를때까지 계속보낸다
DNS는 거대한 전화번호부
ip확인은 ifconfig
또는 ip addr inet이 ip주소 왜 도커우분투는 ip addr 안먹는가?
### public address vs private address

1. public address 확인 방법(온라인 서비스 입장)
: curl ipinfo.io/ip 라우터의 주소

2. private address 확인 방법(실제 ip)
: 라우터에서 보는 ip주소

1,2는 같을수도 , 다를 수도 있다.

한 집에 통신사로부터 211.46.24.37 이라는 ip를 할당 받는다면 공유기(라우터)를 통해 tv,컴퓨터, 전화기 등의 ip를 나눔. 즉 하나의 회선만 계약해서 사용료 절감. 통신사가 제공한 ip는 라우터가 갖고 private ip(사설 ip)로 집 내부 기기 구분
public address와 private address가 다르다면 그 컴퓨터는 서버로 바로 쓸수 없다. 같은 wifi. 즉 같은 라우터를 사용하고 있어야 그 서버컴퓨터에 접속 가능.
또는 라우터의 기능 잘 이용하면 가능함.

## 웹서버(아파치)
apt-cache search apache 설치가능한 패키지
sudo apt update
sudo apt install apache2
sudo service apache2 start
sudo service apache2 stop
sudo service apache2 restart

셸에서 웹브라우징을 할 수 있는 프로그램
ex 이링크스
elinks 실행하고 브라우징하면댐
q키 누르면 빠져나옴
localhost(자기 자신 도메인 네임) = 127.0.0.1 (자기 자신)
프로그래밍의 동작 방법 설정은 /./etc에 있다.(일단 도커는)
/etc/apache2 의 설정파일을 통해 ...
웹페이지의 최상위 디렉터리 document root
### tail -f /var/log/apache2/access.log
누가 들어왔을때 실시간으로 보내줌.
error.log와
access.log를.... 확인

## 원격제어(SSH)
제어하려는 서버컴퓨터에는 ssh server를 설치
우리의 컴퓨터에는 ssh client 설치
apt-get install openssh-server openssh-client
ssh start

## 포트(port)
:80(포트)
web은 80포트
ssh 는 20번 포트
65000여개중에 1024개까지는 well known 포트
포트번호 고정
1024~65~~ 나머지는 우리가 만들어서 알아서 사용
/etc/ssh/sshd_config

### 포트 포워딩
외부포트번호를 통해 내부 포트번호설정

private ip를 외부에 있는 사용자에게 접근하게 하는 것
라우터에 포트 설정. 
라우터의 9000번 포트는 192.168.04:80 번으로 가라!
공유기의 안쪽에서만 통용되는 ip -> default gateway

apt install iproute2 ip명령어 사용하기위해 다운
ip route default via -> default gateway의 ip

## 도메인
DNS domain name system
dns 전에는 hosts file로...
host file에 없으면 dns서버에 접속해서 알아냄.
임시로 도메인을 바꿔야 할 경우에 host파일을 이용
해커들이 host파일을 공격해서 naver에 매칭된 ip를 바꾼다!

### 도메인 구입
cat /./etc/resolv.conf 를 통해 nameserver 확인(dns server ip)
freedomain도 있다
freenom에서

host google.com 구글의 ip확인

### subDomain

### DNS principal
egoing.ga(.) (.)은 root
도메인은 여러 컴퓨터가 계층적으로 분산해서 저장

root dns list는 알고있다
.(root) root domainsystem에게 ga를 관장하는 dns 물어봄
ga관장하는 도메인시스템에게 egoing이 있는 dns ip 물어봄
그다음 egoing.ga의 ip 획득
ga이라는 도메인을 구입한다는 것은 ga관장하는 서버회사에게 돈을 내는거


## 인터넷을 통한 서버간 동기환(rsync)
r = remote
touch test{1..10} 테스트 1부터 9까지 파일 생성
rsync -a src/ dest 밑에 있는 dest파일이 동기화
rsync -a == 아카이브 파일 권한이나 내용 까지 다 전송
rsync -av src dest
이렇게 하면 dest라는 디렉토리 안에 src라는 디렉토리가 생성됨
a는 아카이브 모드, v는 진행상태 출력

dest라는 디렉토리 안에 src 안에 있는 내용을 동기화하고자 한다면
rsync -a src/ dest
여기에서 src/는 src 디렉토리 안에 있는 파일들이라는 뜻
rsync -azP (z=압축 P=접송되는 상황을 progressbar)
rsync의 가장 큰 장점은 증분백업 기능


## 로그인 없이 로그인하기(ssh key)
ssh-keygen하면
ssh 폴더안에 id_rsa랑 id_rsa.pub가 만드렁진다
id_rsa는 private key .pub는 public key
id_rsa는 절대 노출x
ssh-copy-id egoing@192.168.0.67 이런식을 통해 authorized_keys에 덧붙임
로그인 시 ID/PW 를 입력하지 않지만, 보다 안전하게 자동으로 로그인하는 방법

SSH 공개키, 비공개키를 이용한 로그인 방식

SSH 키 생성 명령어
ssh-keygen
.ssh/id_rsa
숨겨진 디렉토리 ssh/id_rsa 에 공개키와 비공개키 파일이 생성된다.
이 키 파일은 랜덤하게 생성된 매우 강력한 비밀번호 파일이다.
id_rsa 파일과 id_rsa.pub 파일이 생성된 보안 키 파일
id_rsa.pub 파일명 중 pub는 public을 의미하며, 공개키(ssh public key)
id_rsa 파일은 비공개키, 사설키(ssh private key)
ssh private key vs ssh public key
이중 비공개키인 id_rsa 파일은 어느 누구에게도, 절대로 노출되면 안 되는 키이다.

공개키 파일 안에 있는 내용을 로그인하고자 하는 컴퓨터의.ssh/authorized_keys 파일에 추가.
명령어는
ssh-copy-id egoing@192.168.0.67
(위 명령어에서 egoing@192.168.0.67은 로그인하고자 하는 컴퓨터)

로그인하고자 하는 컴퓨터에 id_rsa_pub 공개키 파일을 저장하면, 비공개키를 가진 컴퓨터에서 공개키를 가진 로그인하고자 하는 컴퓨터에 ID/PW 입력 없이 자동으로 로그인 가능하다.
접속 명령어는
ssh egoing@192.168.0.67


그렇다면, 언제 이러한 자동 로그인 기능이 필요할까?
동기화를 할 때, 정기적으로 작업을 실행시킬 때
가령 정기적으로 동기화를 하고자 한다면 유용... (crone)
암호화 기술에는 대칭방식과 비대칭방식, 두 가지로 구분된다.
대칭방식의 예로, 데이터를 암호화할 때 비밀번호를 입력했다면 이를 다시 복호화할 때 암호화할 때 입력한 비밀번호와 동일한 비밀번호를 입력해야 하는 경우이다.
반면에,
비대칭방식의 예로는
암호화할 때에는 비공개키로 암호화하고, 복호화할 때는 공개키로만 복호화할 수 있는 경우이다.
이러한 비대칭방식의 대표적인 기술이 RSA 기술이다.
이런 RSA 기술을 응용함으로써 정보기술이 빠르게 발전할 수 있었다.


SSH의 RSA 보안 기술
1. SSH Client(이하 클라이언트)가 SSH Server(이하 서버)에 접속허락을 요청한다.
2. 서버는 랜덤 키를 클라이언트에 보낸다.
3. 클라이언트는 받은 랜덤 키를 비공개키를 이용해 암호화한 후, 암호화한 파일을 서버에 보낸다.
4. 서버는 받은 암호화 파일을 공개키로 복호화한 후, 복호화한 파일이 클라이언트에게 보냈던 랜덤 키와 일치하면 접속을 허락한다.



