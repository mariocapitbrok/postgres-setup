# Postgres Setup

## Project Description

This project sets up a PostgreSQL database using Docker and provides scripts to manage the database lifecycle.

## Prerequisites

- Docker
- Node.js

## Setup

1. Clone the repository:

   ```sh
   git clone <repository_url>
   cd postgres-setup
   ```

2. Install dependencies:

   ```sh
   npm install
   ```

3. Create a `.env` file in the root directory with the following content:

   ```env
   POSTGRES_PORT=5432
   POSTGRES_USER=<your_postgres_user>
   POSTGRES_PASSWORD=<your_postgres_password>
   POSTGRES_DB=<your_postgres_db>
   ```

4. Create an `init.sql` file inside the `db` directory with your initial SQL setup scripts.

## Scripts

- **Start Database:**

  ```sh
  npm run start-db
  ```

- **Stop Database:**

  ```sh
  npm run stop-db
  ```

- **Initialize Database:**
  ```sh
  npm run init-db
  ```

## Docker Compose Configuration

The `docker-compose.yml` file defines the PostgreSQL service.

### Services

- **postgres:**
  - Image: `postgres:latest`
  - Container Name: `my_postgres`
  - Ports: `${POSTGRES_PORT}:5432`
  - Volumes: `./db/init.sql:/docker-entrypoint-initdb.d/init.sql`
  - Networks: `postgres-network`

### Networks

- **postgres-network:**
  - Driver: `bridge`

## Author

mariocapitbrok

## License

ISC
