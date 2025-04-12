## 🏥 Spring PetClinic — DevOps Pro Edition

![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7.13-brightgreen.svg)
![Java](https://img.shields.io/badge/Java-17-orange.svg)
![Build](https://img.shields.io/badge/Build-Maven-blue)
![License](https://img.shields.io/badge/license-Apache%202.0-lightgrey.svg)

### ✨ Demo URL
👉 [`http://localhost:9966/petclinic`](http://localhost:9966/petclinic)

---

## 📌 Table of Contents
- [About](#about)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Screenshots](#screenshots)
- [Getting Started](#getting-started)
- [Database Configuration](#database-configuration)
- [Run with Docker](#run-with-docker)
- [CI/CD Pipeline](#cicd-pipeline)
- [Project Structure](#project-structure)
- [Branches](#branches)
- [Contributors](#contributors)
- [License](#license)

---

## 🧾p About

**Spring PetClinic** is a sample **Spring Boot** web application built for learning the **Spring ecosystem** and showcasing real-world DevOps workflows.

This version is DevOps-optimized for CI/CD pipelines, Docker deployment, and infrastructure-as-code practices.

---

## 🛠 Tech Stack

| Layer         | Technology                      |
|--------------|----------------------------------|
| Language      | Java 17                          |
| Framework     | Spring Boot 2.7.13               |
| Web           | Spring MVC, JSP                  |
| Persistence   | Spring Data JPA, Hibernate       |
| Database      | HSQLDB / MySQL                   |
| Build Tool    | Maven                            |
| DevOps Tools  | Docker, Jenkins, GitHub Actions  |
| Testing       | JUnit, Mockito                   |

---

## 🏗 Architecture

```text
Browser
   ↓
Spring MVC (Controller)
   ↓
Service Layer (ClinicService)
   ↓
Repository Layer (Spring Data JPA)
   ↓
Database (HSQLDB / MySQL)
```

---

## 🗼 Screenshots

> Add your own screenshots later

![Home Page](https://github.com/spring-projects/spring-petclinic/blob/main/docs/images/petclinic-home.png)
![Owners List](https://github.com/spring-projects/spring-petclinic/blob/main/docs/images/petclinic-owners.png)

---

## 🚀 Getting Started

### 📦 Clone & Build

```bash
git clone https://github.com/DevOpsLearrnn/PetMate
cd spring-petclinic
./mvnw clean install
```

### ▶️ Run the App

```bash
./mvnw spring-boot:run
```

Access: `http://localhost:9966/petclinic`

---

## 💢 Database Configuration

### 🧠 In-Memory HSQLDB (Default)
- Automatically runs on app startup.
- No configuration needed.

### 🐬 MySQL (Optional)

```bash
docker run -e MYSQL_ROOT_PASSWORD=petclinic \
           -e MYSQL_DATABASE=petclinic \
           -p 3306:3306 mysql:5.7
```

#### Update `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/petclinic
spring.datasource.username=root
spring.datasource.password=petclinic
spring.jpa.hibernate.ddl-auto=update
```

---

## 🐳 Run with Docker

### Step 1: Build the Image

```bash
docker build -t spring-petclinic .
```

### Step 2: Run the Container

```bash
docker run -d -p 8080:8080 spring-petclinic
```

Visit: `http://localhost:8080`

---

## 🔄 CI/CD Pipeline

### ✅ GitHub Actions

```yaml
name: CI Build

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Java
        uses: actions/setup-java@v3
        with:
          java-version: '17'
      - name: Build with Maven
        run: ./mvnw clean install
```

### ✅ Jenkins Pipeline

```groovy
pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/DevOpsLearrnn/PetMate'
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t spring-petclinic .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8080:8080 spring-petclinic'
            }
        }
    }
}
```

---

## 📂 Project Structure

```text
📀 src
🕛   🕛 main
🕛   ├🕛 java/org/springframework/samples/petclinic
🕛   ├🕛 resources
🕛   └🕛 webapp/WEB-INF/jsp
🕛   test
pom.xml
Dockerfile
```

---

## 🌿 Branches

| Branch         | Description                        |
|----------------|------------------------------------|
| `main`         | JSP + Spring Boot default version  |
| `thymeleaf`    | Using Thymeleaf templates          |
| `spring-jdbc`  | Using Spring JDBC instead of JPA   |
| `react`        | React frontend version             |

---

## 👥 Contributors

Made with ❤️ by:

- [Your Name](https://github.com/DevOpsLearrnn/PetMate)
- [Spring Team](https://github.com/spring-projects)

Want to contribute? [Raise a PR](https://github.com/DevOpsLearrnn/PetMate)

---

## 📄 License

This project is licensed under the **Apache License 2.0**.  
See [LICENSE](LICENSE) for details.

---

## 🧑‍🤖 FAQ

**Q: Can I deploy this on AWS/GCP/Azure?**  
Yes, use Docker, ECS, EKS, or App Engine.

**Q: Can I switch to PostgreSQL?**  
Yes, just change the JDBC URL and dependency.

**Q: Does it support REST APIs?**  
Yes, with a bit of customization you can expose REST endpoints.

---

## 🧠 Want DevOps Magic?

Need CI/CD, monitoring, or cloud infra setup?  
> Fork the repo, and start building your DevOps skills now! 🚀


