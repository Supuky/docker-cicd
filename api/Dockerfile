FROM gradle:7 as base
CMD ["bash"]

# Build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# production
FROM openjdk:17 AS production
COPY --from=build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD ["jave", "-jar", "api.jar"]
