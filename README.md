# Storage Drive

#### Table of Contents:

- [Overview](#overview)

  - [Pre-Requisite](#pre-requisite)

- [Build Setup](#build-setup)

  - [Setup Environment Variables](#setup-environment-variables)
  - [Build App](#build-app)
  - [Build Dockerfile](#build-dockerfile)

- [ECS Configuration](#ECS-configuration)

  - [Environment Variables](#environment-variables)
  - [Database Migrations](#database-migration)

---

## Overview

### Pre-Requisite

1. Make sure you have [Node.js v20](https://nodejs.org/en) installed.
2. Clone this repository.
3. Enter the repository and install the dependencies via `npm` or `yarn`:

   ```sh
   npm install
   ```

   or

   ```sh
   yarn
   ```

---

## Build Setup

### Setup Environment Variables

The application require some environment variables to run properly. Create `.env` file in root directory. Template for environment variables available at [.env.example](./.env.example).

### Build App

To build application you can use the following command:

```sh
npm run build
```

or

```sh
yarn run build
```

The code that has been built will be available in the `dist/` directory.

### Build Dockerfile

Build Dockerfile by using the following command

```bash
docker build -t citrus-file:latest .
```

Upload the Docker Image to ECR to be used by Kubernetes Deployments

### Start application locally

1. Start the server:

   ```sh
    npm run start
   ```

   or

   ```sh
   yarn start
   ```

2. application should now be up and running at `http://<host>:<port>`. E.g [http://localhost:3000](http://localhost:3000)

---

## ECS Configuration


### Environment Variables

Since the application will be deploy using AWS ECS, you need to set all configuration options to AWS Parameter store and store all confidential environment as Secrets

### Database Migrations

> **Note** </br>
> The command must be executed before deploying to EKS Cluster

Perform migration to create required tables in database with following command:

```
npm run db:migrate
```

or

```
yarn run db:migrate
```

The migration script depends on the following environment variables:

```
DB_TYPE=
DB_HOST=
DB_PORT=
DB_NAME=
DB_USERNAME=
DB_PASSWORD=
```


