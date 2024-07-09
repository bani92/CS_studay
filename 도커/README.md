### Git Bash에서 명령어

docker stop $(docker ps -q) - 여러 컨테이너를 한꺼번에 STOP\
docker rm $(docker ps -a -q) - 여러 컨테이너를 한꺼번에 삭제\
docker rmi -f $(docker ps -a -q) - 여러 이미지를 한꺼번에 삭제 

### 우분투 구동방법

아파치는 서버 프로세스이기때문에 컨테이너에서 계속적으로 돌고 있음 \
하지만 우분투는 **서버프로세스**가 아니기때문에 컨테이너를 run 하면 **/bin/bash**를 실행하고 종료되어버린다.

**d - 백그라운드 , i - 인터랙티브 , t - 터미널** \
detached : 컨테이너를 백그라운드에서 실행하여 터미널을 반환 \
interactive : 표준 입력을 열어둠, 컨테이너와의 상호작용을 유지합니다. \
tty : 가성 터미널을 할당하여 'bash'와 같은 셸 프로그램이 실행될 수 있도록합니다. \

docker run dit --name myubuntu ubuntu

### 데몬 프로세스

소위 서버라고 불림 \
백그라운드에서 실행되는 프로그램 , 메모리에 상주하면서 특정 요청이 오면 \
즉시 대응할수 있도록 대기중인 프로세스

### docker exec 명령어

1. OS (ubuntu) \
docker run dit ubuntu bash \
docker attach 컨테이너 ID
2. Daemon (Httpd) \
docker run -d -p 8080:80 httpd \
docker exec -it 컨테이너ID bash

### docker volume (-v)

컨테이너와 호스트 운영체제 간에 데이터를 공유하거나 저장하기 위한 기능

1. docker run -d -p 8080:80 -v c:\users\PC2303\webapp:/usr/local/apache2/htdocs httpd
2. docker exec -it 컨테이너명 bash \
위와 같이 구동시 vscode를 통하여 webapp에 index.html 을 생성한 후 \
localhost:8080 에 접근하면 해당 index.html이 출력된다.

### docker hub 업로드

1. Create repository
2. docker run -dit ubuntu
3. vi는 불가능 
4. apt update
5. apt install vim
6. exit
7. 도커 컨테이너를 다시 실행
8. docker attach 컨테이너ID
9. docker commit 컨테이너ID 아이디/리파지토리에 적어준 이름:1.0
10. docker push 아이디/리파지토리 적어준 이름:1.0

위와 같이 진행하면 깃처럼 pull을 받을 수 있음

### docker 삭제방법(윈도우)

for /f "delims=" %A in ('docker ps -q') do (set rm1=%A) 
for /f "delims=" %A in ('docker ps -a -q') do (set rm2=%A) 
for /f "delims=" %A in ('docker images -q') do (set rm3=%A)
docker stop %rm1%
docker rm %rm2%
docker rmi -f %rm3%

### docker file

1. 윈도우에 Dockerfile 이라고 생성 (.txt 삭제, Dockerfile이 키워드임)
2. FROM httpd
   COPY ./webapp /usr/local/apache2/htdocs
   CMD ["httpd-foreground"]
3. 폴더 안에 webapp 이라는 폴더 생성
4. index.html 생성 (기본값 적기)
5. docker build -t webserver ./ (이미지 생성완료, ./ <- 현재 폴더)
6. docker run -dit -p 8080:80 컨테이너이름
7. localhost:8080 확인 or docker exec -it 컨테이너이름 bash 진입 후 htdocs 경로 확인





