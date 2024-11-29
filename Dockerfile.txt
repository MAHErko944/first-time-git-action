# Stage 1: Build
FROM openjdk:22-jdk-slim AS builder
WORKDIR /app
COPY Main.java .
RUN javac Main.java

# Stage 2: Runtime
FROM openjdk:22-jdk-slim
WORKDIR /app
COPY --from=builder /app/Main.class .
CMD ["java", "Main"]
