# simplebank
This repository is based on [Tech School's](https://github.com/techschool/simplebank) development of a backend web service for a simple bank. 

The purpose of this exercise is for me to better understand the processes involved in developing backend services from scratch. This documentation records my learning process.

## Technologies Used
### Environment
- Windows 11 with WSL2
- Golang

### Platforms/Services
- DBDiagram
- Docker
- AWS
- Kubernetes
- PostgreSQL
- Postman
- TablePlus

### Packages/Libraries
- sqlc
- golang-migrate
- Viper
- GoMock
- bcrypt
- jwt-go
- go paseto
- GIN

## Building the Application
### Database Design
- Used DBDiagram to plot database schema
- Exported diagram into PostgreSQL queries

### CRUD Statements
- Used sqlc to generate SQL queries into go code

### RESTful HTTP JSON APIs
- Used GIN framework to receive and handle requests
- Hashed passwords using Bcrypt
- Implemented both JWT and PASETO usage, switchable through use of go interface type

### Unit Testing
- Wrote simple unit tests for the code
- Used GoMock for more robust testing

### GitHub Actions
- Automated testing after every git push

## Preparing for Deployment
### Docker
- Used multi-stage docker file to build application as a light-weight docker image
- Used docker network to connect 2 stand-alone containers
- Used docker compose to start multiple services at once, in a specific order

### AWS
- Made a private Amazon ECR repo where docker image can be pushed to
- Using GitHub Actions, automated building of docker image to Amazon ECR whenever there is a new push on GitHub master branch
- Created Postgres database on Amazon RDS (using free tier, so it might be taken down eventually) that can be remotely accessed from local machine
- Used Amazon EKS to create node group and manage containers
