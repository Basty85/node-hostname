# Node.js Hostname App - Docker Setup

This Node.js Express application has been containerized with Docker for easy deployment.

## Prerequisites

- Docker
- Docker Compose (optional, but recommended)

## Building and Running

### Option 1: Using Docker Compose (Recommended)

```bash
# Build and start the application
docker-compose up -d

# View logs
docker-compose logs -f

# Stop the application
docker-compose down
```

### Option 2: Using Docker directly

```bash
# Build the image
docker build -t node-hostname:latest .

# Run the container
docker run -d -p 3000:3000 --name node-hostname-app node-hostname:latest

# Stop and remove the container
docker stop node-hostname-app
docker rm node-hostname-app
```

## Accessing the Application

Once running, the application will be available at:
- http://localhost:3000

The app returns a JSON response with the hostname and version:
```json
{"hostname":"container_id","version":"0.0.1"}
```

## Container Features

- **Base Image**: Node.js 18 Alpine (lightweight)
- **Security**: Runs as non-root user
- **Health Check**: Included in docker-compose.yml
- **Port**: Exposes port 3000
- **Environment**: Production-ready configuration

## Development

For development, you can mount your local code:

```bash
docker run -d -p 3000:3000 -v $(pwd):/usr/src/app node-hostname:latest
```

## Troubleshooting

Check container logs:
```bash
# With docker-compose
docker-compose logs

# With docker
docker logs node-hostname-app
```

Check container status:
```bash
docker ps
```