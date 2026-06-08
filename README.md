# Jenkins CI/CD Pipeline Project

End-to-End CI/CD Pipeline using Jenkins, SonarQube, Docker and AWS EC2

## Tools Used
- Jenkins - CI/CD orchestration
- SonarQube - Code quality analysis
- OWASP - Security vulnerability scanning
- Docker - Containerization
- Maven - Java build tool
- AWS EC2 - Cloud deployment

## Pipeline Flow
Git Checkout → Compile → Test → SonarQube Analysis → OWASP Scan → Build → Docker Build and Push → Deploy

## Screenshots

### Jenkins Dashboard
![Jenkins Dashboard](screenshots/Screenshot 2026-06-07 at 12.56.38 AM.png)

### Pipeline Stages
![Pipeline Stages](screenshots/Screenshot 2026-06-07 at 12.56.49 AM.png)

### SonarQube Analysis
![SonarQube](screenshots/Screenshot 2026-06-07 at 1.00.57 AM.png)

### App Running
![App](screenshots/Screenshot 2026-06-07 at 1.01.48 AM.png)

## Access
- Jenkins: http://ec2-ip:8080
- SonarQube: http://ec2-ip:9000
- Application: http://ec2-ip:8070
