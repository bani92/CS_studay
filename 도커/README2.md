### 엔드리 포인트(Entry Point)

FROM openjdk:11-jdk-slim

WORKDIR /app

COPY build/aws-v3-0.0.3.jar ./application.jar

ENTRYPOINT ["java", "-jar", "-Dspring.profiles.active=dev", "application.jar"]

실행하면 8081로 구동됨

docker run -dit -p 8080:8081 java-server --server.port=5000 \
'--server.port=5000'를 붙이면 구동시 스프링 포트 5000번으로 실행(CMD)

### 엔트리 포인트와 CMD 차이

엔트리포인트 - 무조건 실행할 실행 명령어를 넣는것(디폴트 값) \
CMD - 옵션(변수)

-Dspring.profiles.active=dev 옵션을 주면 5000번 포트로 돌아감
하지만 CMD ["--server.port=3000"] 으로 인해 3000번 포트로 구동됨

### 구동되고있는 컨테이너 로그보기
docker logs 컨테이너ID