# GitHub Repo Cloning and Build System

This project is a scalable deployment architecture designed to clone GitHub repositories, build executables, and store the results in AWS S3. The system is capable of running up to 5,000 Docker containers concurrently using AWS ECS/ECR. Real-time build logs are displayed on a NextJS client using a Redis-based publish-subscribe model.

## Technologies

- **Frontend:** NextJS
- **Backend:** Node.js, Express.js
- **Database:** Redis (Pub/Sub)
- **Containerization:** Docker
- **Cloud:** AWS ECS, AWS ECR, AWS S3
- **Version Control:** GitHub

## Features

- Scalable deployment with support for up to 5,000 concurrent Docker containers.
- Real-time build logs using Redis Pub/Sub, displayed via a NextJS client.
- Storage of build executables in AWS S3.
- Reverse proxy server for hosting build artifacts.

## Architecture

- **Frontend:** The frontend is built using NextJS and interacts with the backend via a socket connection to fetch real-time build logs.
- **Backend:** A Node.js/Express server handles GitHub repository cloning, builds executables, and interacts with Redis for real-time updates.
- **Containers:** Docker containers are spun up by AWS ECS/ECR to execute builds. The containers pull the source code from GitHub and store the build artifacts in S3.
- **Real-Time Logging:** Redis Pub/Sub provides real-time logging capabilities, where the logs are streamed to the client via WebSockets.

## Prerequisites

- **Node.js**: v16 or later
- **Docker**: Latest version
- **AWS CLI**: Configured with ECS, ECR, and S3 permissions
- **Redis**: Installed and running (local or cloud-based)
- **GitHub OAuth Token**: For accessing private repositories

