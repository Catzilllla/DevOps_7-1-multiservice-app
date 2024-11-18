FROM openjdk:8-jdk-alpine

WORKDIR /dockerapp

# копируем maven и заливаем зависимости в кэш
COPY .mvn /dockerapp/.mvn
COPY mvnw /dockerapp/mvnw
COPY pom.xml /dockerapp/pom.xml

RUN chmod +x /dockerapp/mvnw
RUN ./mvnw dependency:go-offline

# копируем исходники приложения
COPY src ./
RUN mvn -B package -DskipTests
# RUN .dockerapp/mvnw spring-boot:run

CMD ["java", "-jar", "dockerapp/*.jar"]
