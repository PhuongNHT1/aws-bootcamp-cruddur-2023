# Week 1 — App Containerization

- [Week 1 — App Containerization](#week-1--app-containerization)
  - [Prerequisite Knowledge](#prerequisite-knowledge)
  - [Materials](#materials)
  - [Required Homeworks](#required-homeworks)
    - [1. Containerize Application (Dockerfiles, Docker Compose)](#1-containerize-application-dockerfiles-docker-compose)
    - [2. Document the Notification Endpoint for the OpenAI Document](#2-document-the-notification-endpoint-for-the-openai-document)
    - [3. Write a Flask Backend Endpoint for Notifications](#3-write-a-flask-backend-endpoint-for-notifications)
    - [4. Write a React Page for Notifications](#4-write-a-react-page-for-notifications)
    - [5. Run DynamoDB Local Container and ensure it works](#5-run-dynamodb-local-container-and-ensure-it-works)
    - [6. Run Postgres Container and ensure it works](#6-run-postgres-container-and-ensure-it-works)
  - [Homework Challenges](#homework-challenges)
    - [1. Learn how to install Docker on your localmachine and get the same containers running outside of Gitpod / Codespaces](#1-learn-how-to-install-docker-on-your-localmachine-and-get-the-same-containers-running-outside-of-gitpod--codespaces)

## Prerequisite Knowledge

- [x] [Docker in 5 minutes](https://www.youtube.com/watch?v=cxCG0cFgsd4): the shortest and easiest way to get to know Docker
- [ ] [Adrian Cantrill – Docker Fundamentals (Free)](https://learn.cantrill.io/p/docker-fundamentals)
- [ ] [Docker Labs for absolute beginner (Free)](https://kodekloud.com/topic/labs-basic-docker-commands-beta/): the playground to play with Docker @ kodekloud


## Materials

- [x] Grading Homework Summaries
- [x] Week 1 - Live Streamed Video
- [x] Chirag's Week 1 - Spending Considerations
- [x] Ashish's Week 1 - Container Security Considerations


## Required Homeworks
- [ ] 1. Containerize Application (Dockerfiles, Docker Compose)
- [ ] 2. Document the Notification Endpoint for the OpenAI Document
- [ ] 3. Write a Flask Backend Endpoint for Notifications
- [ ] 4. Write a React Page for Notifications
- [ ] 5. Run DynamoDB Local Container and ensure it works
- [ ] 6. Run Postgres Container and ensure it works

### 1. Containerize Application (Dockerfiles, Docker Compose)

### 2. Document the Notification Endpoint for the OpenAI Document

### 3. Write a Flask Backend Endpoint for Notifications

### 4. Write a React Page for Notifications

### 5. Run DynamoDB Local Container and ensure it works

### 6. Run Postgres Container and ensure it works

## Homework Challenges
### 1. Learn how to install Docker on your localmachine and get the same containers running outside of Gitpod / Codespaces
My local machine is MacOS. I used homebrew to install docker
```
brew install docker
```
Then, install the Docker extension in VSCode
![](img/week1_20230224003440.png)

After config the links in docker-compose.yml to local links, I got all the containers running like this.
![](img/week1_20230224003212.png)

Here is my configured docker-compose.yml
```yml
version: "3.8"
services:
  backend-flask:
    environment:
      FRONTEND_URL: "https://localhost:3000"
      BACKEND_URL: "https://localhost:4567"
    build: ./backend-flask
    ports:
      - "4567:4567"
    volumes:
      - ./backend-flask:/backend-flask
  frontend-react-js:
    environment:
      REACT_APP_BACKEND_URL: "https://localhost:4567"
    build: ./frontend-react-js
    ports:
      - "3000:3000"
    volumes:
      - ./frontend-react-js:/frontend-react-js

# the name flag is a hack to change the default prepend folder
# name when outputting the image names
networks:
  internal-network:
    driver: bridge
    name: cruddur
```