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

## CI Pipeline Stages
| Stage | Description |
|-------|-------------|
| Git Checkout | Pull code from GitHub |
| Compile | Maven compile |
| Test | Maven test |
| SonarQube Analysis | Code quality check |
| OWASP Scan | Security vulnerability scan |
| Build | Maven clean install |
| Docker Build and Push | Build image and push to DockerHub |

## CD Pipeline Stages
| Stage | Description |
|-------|-------------|
| Docker Deploy | Pull image and run container |

## Access
- Jenkins: http://ec2-ip:8080
- SonarQube: http://ec2-ip:9000
- Application: http://ec2-ip:8070
