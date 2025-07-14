# Stage 2:

In this stage, we will start organizing the `Dockerfile` with the multiple-stage build.

## Objectives

To create the multiple-stage `Dockerfile` we will need the following:

- Stage 1 (Build):
  - Use any valid JVM-based base image with a JDK to build your application (e.g., `eclipse-temurin:21-jdk`)
  - Set the working directory inside the container to `/app`.
  - Use the appropriate instruction to:
    - Transfer the Gradle Wrapper files (`gradlew`, `gradlew.bat`);
    - Transfer the `gradle` folder into the `gradle` folder in the working directory;
    - Transfer the Gradle project files (`build.gradle`, `settings.gradle`) into the working directory;
    - Transfer the `src` folder containing your application source code into the `src` folder in the working directory.
  - Ensure the Gradle Wrapper has executable permissions using the `chmod +x gradlew` command.
  - Build the application with the command: `./gradlew bootJar --no-daemon`.

- Stage 2 (Package):
  - Use any valid JVM-based base image with a JRE to create a lightweight runtime environment for your application (e.g., `eclipse-temurin:21-jre`);
  - Set the working directory inside the container to `/app`;
  - Use the appropriate instruction to copy the JAR file generated in the build stage (`/app/build/libs/hyper-web-app-0.0.1-SNAPSHOT.jar`) into the runtime stage directory as `app.jar`;
  - Expose port `8080`, which is the default port for Spring Boot applications;
  - Set the entry point to run the application using the command: `["java", "-jar", "app.jar"]`.

You may use any valid tag or version for the images (e.g., `latest`, `21-jre`, `17`).