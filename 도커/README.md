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