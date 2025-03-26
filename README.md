# Prometheus Security

## Project Description

Prometheus Security is a Node.js application that provides various endpoints and metrics for monitoring and alerting using Prometheus. The application includes authentication for the `/metrics` endpoint and is configured for deployment using Netlify.

## Setup Instructions

1. Clone the repository:
   ```sh
   git clone https://github.com/ipso-oop/Prometheus_Security.git
   cd Prometheus_Security
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

3. Start the application:
   ```sh
   node app.js
   ```

4. Configure Prometheus to scrape metrics from the application by adding the following job to your `prometheus.yml`:
   ```yaml
   scrape_configs:
     - job_name: "Demo App 1"
       static_configs:
         - targets: ["localhost:3000"]
   ```

## Usage Instructions

### Endpoints

- `/`: Returns a simple "Hello, Prometheus!" message.
- `/login`: Simulates a login endpoint with a 50% chance of success or failure.
- `/metrics`: Exposes Prometheus metrics.

### Metrics

- `http_requests_total`: Counter for the total number of HTTP requests.
- `http_request_duration_seconds`: Histogram for the duration of HTTP requests in seconds.
- `failed_login_attempts_total`: Counter for the total number of failed login attempts.
- `http_errors_total`: Counter for the total number of HTTP error responses.

## Authentication Setup

The `/metrics` endpoint is protected with basic authentication. The default credentials are:
- Username: `admin`
- Password: `admin123`

## Deployment Configuration

The application is configured for deployment using Netlify. The `netlify.toml` file includes the necessary settings for deploying the application and redirecting requests to the appropriate endpoints.

## Dependencies

The application has the following dependencies listed in `package.json`:
- `express`: "^4.21.2"
- `express-basic-auth`: "^1.2.1"
- `prom-client`: "^15.1.3"
- `serverless-http`: "^3.2.0"

## Alert Rules

The alert rules are defined in the `alerts.yml` file. The following alert is configured:
- `HighRequestCount`: Triggers when the total number of HTTP requests exceeds 10.

## Prometheus Configuration

The Prometheus configuration is defined in the `prometheus_local.yml` file. The configuration includes global settings, alertmanager configuration, rule files, and scrape configurations for Prometheus and the application.
