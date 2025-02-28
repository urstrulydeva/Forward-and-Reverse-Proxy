# Forward and Reverse Proxy Implementation using Docker

## Overview
This repository contains configurations for setting up both a **Forward Proxy (using Squid)** and a **Reverse Proxy (using Nginx)** using Docker. These proxies help in routing, filtering, and securing network traffic efficiently.

## Features
- **Forward Proxy** using Squid for filtering and caching outgoing requests.
- **Reverse Proxy** using Nginx for load balancing and security.
- **HTTPS Support** with SSL/TLS configuration.
- **Dockerized Implementation** for easy deployment and management.

## Prerequisites
- Docker & Docker Compose installed.
- Basic networking and proxy knowledge.

## Setup Instructions
### Forward Proxy (Squid)
1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo.git
   cd your-repo/squid_forward_proxy
   ```
2. Modify `squid.conf` as needed.
3. Start the Squid proxy:
   ```sh
   docker-compose up -d
   ```
4. Test using:
   ```sh
   curl -x http://localhost:3128 -I https://www.google.com
   ```

### Reverse Proxy (Nginx)
1. Navigate to the Nginx directory:
   ```sh
   cd ../nginx_reverse_proxy
   ```
2. Modify `nginx.conf` as needed.
3. Start the Nginx reverse proxy:
   ```sh
   docker-compose up -d
   ```
4. Access the reverse proxy via:
   ```
   http://localhost
   ```

### Enabling HTTPS
1. Generate SSL certificates:
   ```sh
   openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout certs/nginx.key -out certs/nginx.crt
   ```
2. Update `nginx.conf` to use HTTPS.
3. Restart the proxy:
   ```sh
   docker-compose down && docker-compose up -d
   ```
4. Test with:
   ```sh
   curl -k https://localhost
   ```

## Troubleshooting
- **Container name conflicts:** Remove existing containers before restarting:
  ```sh
  docker ps -a
  docker stop <container_id>
  docker rm <container_id>
  ```
- **Mounting errors:** Ensure configuration files exist and paths are correct.

## Contributing
Feel free to fork the repository and submit pull requests for enhancements or bug fixes.

## License
This project is licensed under the MIT License.

---

