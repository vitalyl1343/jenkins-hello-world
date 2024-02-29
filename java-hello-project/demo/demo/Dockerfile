FROM eclipse-temurin:17-jdk-alpine as build
WORKDIR /workspace/app

COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .
COPY src src

RUN ./mvnw install -DskipTests
RUN mkdir -p target/dependency && (cd target/dependency; jar -xf ../*.jar)

FROM eclipse-temurin:17-jdk-alpine as runtime
WORKDIR /app

ARG DEPENDENCY=/workspace/app/target/
COPY --from=build ${DEPENDENCY}/demo-0.0.1-SNAPSHOT.jar .

ENTRYPOINT ["java","-jar","demo-0.0.1-SNAPSHOT.jar"]