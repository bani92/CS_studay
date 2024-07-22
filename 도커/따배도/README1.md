docker pull nginx:1.14

docker images\
다운로드 이미지 확인

docker images --no-trunc\
이미지ID를 풀네임으로 표시

docker ps -a\
현재 동작중인 컨테이너 확인

docker create --name webserver nginx\
컨테이너 생성

docker start webserver\
컨테이너 실행

docker inspect webserver\
컨테이너 세부정보 확인

docker inspect --format '{{.NetworkSettings.IPAddress}}' webserver\
필요한 정보만 보고싶을때 '{{ }}'

docker stop 컨테이너ID\
컨테이너 중지

docker rm 컨테이너ID\
컨테이너 삭제