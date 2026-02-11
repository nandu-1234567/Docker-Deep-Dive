<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Docker Deep Dive</title>
  
  
</head>
<body>
  <h1>Docker Deep Dive</h1>

  <h2>1. Problem Docker Solves</h2>
  <p>Docker helps developers package applications and all their dependencies into lightweight containers. This solves issues like:</p>
  <ul>
    <li>"It works on my machine" problem</li>
    <li>Dependency conflicts</li>
    <li>Environment inconsistencies between dev, staging, and production</li>
    <li>Scaling and isolation of applications</li>
  </ul>

  <h2>2. Virtual Machines vs Docker</h2>
  <table border="1" cellpadding="8" cellspacing="0">
    <tr>
      <th>Feature</th>
      <th>Virtual Machine</th>
      <th>Docker Container</th>
    </tr>
    <tr>
      <td>Isolation</td>
      <td>Full OS per VM</td>
      <td>Shared OS kernel</td>
    </tr>
    <tr>
      <td>Resource Usage</td>
      <td>Heavy</td>
      <td>Lightweight</td>
    </tr>
    <tr>
      <td>Startup Time</td>
      <td>Minutes</td>
      <td>Seconds</td>
    </tr>
    <tr>
      <td>Portability</td>
      <td>Less portable</td>
      <td>Highly portable</td>
    </tr>
  </table>

  <h2>3. Docker Architecture - What Gets Installed</h2>
  <p>When Docker is installed, it includes:</p>
  <ul>
    <li><strong>Docker Engine:</strong> Core service to run containers</li>
    <li><strong>Docker CLI:</strong> Command-line interface for interaction</li>
    <li><strong>Container Runtime:</strong> Runs containers (like containerd)</li>
    <li><strong>Docker Daemon:</strong> Background service managing images, containers, networks, volumes</li>
    <li><strong>Optional GUI Tools:</strong> Docker Desktop Dashboard (on Windows/macOS)</li>
  </ul>

  <h2>4. Dockerfile Deep Dive</h2>
  <pre>
# Use an official Node.js runtime as a parent image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app
COPY . .

# Expose the port
EXPOSE 1337

# Start the application
CMD ["npm", "start"]
  </pre>

  <h2>5. Key Docker Commands</h2>
  <ul>
    <li><code>docker build -t my-app .</code> - Build an image</li>
    <li><code>docker run -p 80:80 my-app</code> - Run a container</li>
    <li><code>docker ps</code> - List running containers</li>
    <li><code>docker stop container_id</code> - Stop a container</li>
    <li><code>docker rm container_id</code> - Remove a container</li>
    <li><code>docker images</code> - List images</li>
  </ul>

  <h2>6. Docker Networking</h2>
  <p>Docker automatically creates networks for containers. Key points:</p>
  <ul>
    <li>Containers can communicate within the same network using service names</li>
    <li>User-defined networks allow better control and isolation</li>
    <li>Port mapping exposes container services to host machine</li>
  </ul>

  <h2>7. Volumes & Persistence</h2>
  <p>Containers are ephemeral; volumes allow persistent storage:</p>
  <pre>
docker volume create my-data
docker run -v my-data:/var/lib/postgresql/data postgres
  </pre>

  <h2>8. Docker Compose</h2>
  <p>Docker Compose allows running multi-container apps easily:</p>
 p
</body>
</html>
