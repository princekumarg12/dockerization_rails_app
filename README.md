
# Dockerization Rails App

This is a sample Ruby on Rails application configured with Docker. The app uses PostgreSQL as the database and Puma as the web server, with Hotwire (Turbo + Stimulus) for modern JavaScript functionality. It is designed to work in both Docker and local environments.

## Table of Contents
- [Project Setup](#project-setup)
- [Running in Docker](#running-in-docker)
- [Running Locally](#running-locally)
- [Environment Variables](#environment-variables)
- [Dependencies](#dependencies)
- [Notes](#notes)

## Project Setup

To set up the project, follow the instructions for either the Dockerized environment or local environment setup.

### Running in Docker

1. **Clone the Repository**:
   ```bash
   git clone git@github.com:princekumarg12/dockerization_rails_app.git
   cd dockerization_rails_app
   ```

2. **Build and Start Docker Containers**:
   In the project root directory, run:
   ```bash
   docker compose up --build
   ```

3. **Access the App**:
   The Rails application will be available at `http://localhost:3000` (or `http://127.0.0.1:3000`).

4. **Access PostgreSQL**:
   The PostgreSQL database will be available at port `5433`. The connection details are as follows:
   - `host`: `localhost`
   - `port`: `5433`
   - `username`: `postgres`
   - `password`: `password`
   - `database`: `test_user_development`

5. **Stopping the App**:
   To stop the app, use the following command:
   ```bash
   docker compose down
   ```

### Running Locally

1. **Clone the Repository**:
   ```bash
   git clone git@github.com:princekumarg12/dockerization_rails_app.git
   cd dockerization_rails_app
   ```

2. **Install Dependencies**:
   Make sure you have `ruby`, `rails`, and `postgresql` installed locally. Then run:
   ```bash
   bundle install
   ```

3. **Set Up the Database**:
   Ensure PostgreSQL is running on your local machine, then create and migrate the database:
   ```bash
   rails db:create
   rails db:migrate
   ```

4. **Start the Rails Server**:
   Run the following to start the Rails server locally:
   ```bash
   rails server
   ```

   The app will be available at `http://localhost:3000`.

### Environment Variables

The following environment variables need to be set:

```bash
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password
POSTGRES_DB=test_user_development
DB_HOST=localhost
RAILS_ENV=development
RAILS_MASTER_KEY=*********************
```

For Docker, the `DB_HOST` should be set to `db` since that’s the service name defined in the Docker Compose file.

#### Local Setup:
Ensure the `DB_HOST` is set to `localhost`.

#### Docker Setup:
For Docker, the `DB_HOST` should be set to `db`.

### Dependencies

- **Ruby**: ~3.0.0
- **Rails**: ~8.0.0
- **PostgreSQL**: ~14.0
- **Puma**: ~5.0
- **Hotwire**: turbo-rails, stimulus-rails
- **dotenv-rails**: for managing environment variables

### Notes

- Ensure that Docker is running when you use the Docker environment setup.
- For local development, make sure PostgreSQL is installed and running.
- You can switch between Docker and local environments by updating the `DB_HOST` variable in your `.env` file.