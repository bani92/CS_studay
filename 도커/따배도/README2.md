### 메모리 리소스 제한
제한단위 b, k, m, g로 할당

docker run -d -m 512m nginx:1.14 -> 512MB \
docker run -d -m 1g --memory-reservation 500m nginx:1.14 \
최소 500메가 ~ 최대 1기가 \
docker run -d -m 200m --oom-kill-disable nginx:1.14 \
oom(Out of Memory) killer가 프로세스 kill 하지 못하도록 보호 \

### CPU 리소스 제한

docker run -d --cpu-shares 2048 ubuntu:1.14 \
컨테이너가 사용하는 CPU 비중을 1024 값을 기반으로 설정 \
기본값보다 두배 많은 CPU 자원을 할당

### 컨테이너 볼륨
컨테이너 이미지는 readonly \
컨테이너에 추가되는 데이터들은 별도의 RW(Read Write) 레이어에 저장 \
RO 레이어에 RW 레이어를 하나인것처럼 동작 **Union File System = Overlay** 


rm으로 컨테이너를 삭제시 고객 데이터가 같이 날아가기때문에 데이터를 보존해야함\
### 예제
docker run -d --name db \
-v /dbdata:/var/lib/mysql \
-e MYSQL_ALLOW_EMPTY_PASSWORD=pass mysql:latest

-v /dbdata:/var/lib/mysql \
-v host path : container mount path \
호스트 path에 있는 db데이터를 컨테이너 path에 볼륨마운트

-v /dbdata:/var/lib/mysql:ro \
데이터가 공격자에 의해 컨테이너에 데이터를 저장하면 도커 호스트에도 저장되기때문에
:ro(Read Only) 를 붙여준다 , 생략시 rw(Read Write)



