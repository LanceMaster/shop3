FROM open:17-jdk-slim as builder
WORKDIR /app
#현재 shop3 전체를 app으로 복사
COPY . .
# mvnw 파일에 실행 권한 부여
RUN chmod +x mvnw
# mvnw : 필드 수행 기능 . 빌드 수행.
# 테스트 파일은 빌드에서 제외 시킴
RUN ./mvnw clean package -Dmaven.test.skip = true

#2단계 : 실제 런타이 환경
FROM openjdk:17-jdk-slim
WORKDIR /app
#shop3 별도로 생선된 jar 파일 
#app.jar dnfl rk qnfemehlsdlfmadml jar파이ㅏㄹ 
COPY --from=builder /app/target/shop3-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]