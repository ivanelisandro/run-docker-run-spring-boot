# Stage 1:

In this project, we will create a simple Sprint Boot web application.

It can be created in Java or Kotlin and will be delivered in a container.

Here are the folder structures in each case:

Kotlin version:
```bash
hyper-web-app-Kotlin-main/
├── src/
│   └── main/
│   │   └── kotlin/
│   │       └── com/
│   │           └── example/
│   │               └── hyperwebapp/
│   │                   ├── HyperWebAppApplication.kt
│   │── test/
│       └── kotlin/
│           └── com/
│               └── example/
│                   └── hyperwebapp/
│                       ├── HyperWebAppApplicationTests.kt
├── resources/
│   ├── templates/
│   │   └── index.html
│   ├── static/
│   │   ├── styles.css
├── build.gradle
├── settings.gradle
├── gradlew
├── gradlew.bat
└── README.md
```

Java version:
```bash
hyper-web-app-Java-main/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── example/
│   │               └── hyperwebapp/
│   │                   ├── HyperWebAppApplication.java
│   ├── test/
│   │   └── java/
│   │       └── com/
│   │           └── example/
│   │               └── hyperwebapp/
│   │                   ├── HyperWebAppApplicationTests.java
├── resources/
│   ├── templates/
│   │   └── index.html
│   ├── static/
│   │   └── styles.css
├── build.gradle
├── settings.gradle
├── gradlew
├── gradlew.bat
└── README.md
```

In this stage we create the base `Dockerfile` and `.dockerignore` for the project.

Here are some entry examples for the `.dockerignore`:
```dockerignore
# Gradle build files and directories
.gradle
build/

# IDE-specific files
.idea/
*.iml

# Operating system-specific files
.DS_Store
Thumbs.db

# Logs and temporary files
*.log
tmp/

# The Dockerfile and .dockerignore themselves
Dockerfile
.dockerignore
```

## Objectives

1. Download and extract the project files:

    - Download and extract your preferred Spring Boot project into a separate folder to avoid conflicts with the project files.
    - The project folder contains the necessary application files for a simple Kotlin or Java-based Spring Boot application.

2. Create the `Dockerfile`:

    - In the root directory of the extracted application, create a file named `Dockerfile` (no extension).
    - Add two instructions to the `Dockerfile` that specify the base images required for building and packaging the application:

      - A `build` stage that uses a JVM-based image with the JDK to compile the application, such as `eclipse-temurin:21-jdk`.
      - A run stage that uses a JVM-based image with the JRE to run the application, such as `eclipse-temurin:21-jre`.
      - You can use any JVM-based base image such as `eclipse-temurin` or `amazoncorretto`.

3. Create the `.dockerignore` file:

    - In the root directory of the project, create a file named `.dockerignore` (no extension).
    - Add files to be excluded from the Docker build context.

4. Pull the images:

    - Use the appropriate command to pull the base images from Dockerhub.
    - Verify that the images were downloaded and are available locally.

5. Provide the full path to the `Dockerfile` in the `Main.kt` file.
