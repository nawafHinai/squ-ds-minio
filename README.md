# Setting Up a 4-Node Highly Available Minio Cluster

## Prerequisites
- Docker and Docker Compose installed.
- Basic understanding of Docker and Docker Compose.
- NGINX installed.

## Step-by-Step Guide

### Step 1: Prepare Docker Compose File

Create a `docker-compose.yml` file to define the Minio services. This file will specify four Minio instances, each running on a different port, and configured to form a cluster.

**Key elements in `docker-compose.yml`:**
- Define four Minio services (`minio1`, `minio2`, `minio3`, `minio4`).
- Assign unique ports for each service.
- Set environment variables for Minio root user and password.
- Use the `command` directive to configure clustering.

### Step 2: Prepare NGINX Configuration File

Create an `nginx.conf` file to configure NGINX as a reverse proxy to balance the load across the Minio instances.

**Key elements in `nginx.conf`:**
- Define an upstream block with all Minio instances.
- Configure the server block to proxy requests to the Minio cluster.

### Step 3: Start Minio Cluster

Navigate to the directory containing the `docker-compose.yml` file and run:

```sh
docker-compose up -d
