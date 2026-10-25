# 🐳 Docker Masterclass: From Zero to Production

> **A Comprehensive Curriculum and Plain-English Command Reference**

Welcome to the **Docker Masterclass** repository! This repository contains a structured, progressive 10-module curriculum, cheat sheet, security checklist, and a 4-week hands-on action plan designed to take you from container fundamentals to multi-container production orchestration.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Course Architecture & 10 Modules](#-course-architecture--10-modules)
  - [Module 1: Core Concepts & Architecture](#module-1-core-concepts--architecture)
  - [Module 2: Working with Docker Images](#module-2-working-with-docker-images)
  - [Module 3: Running & Managing Containers](#module-3-running--managing-containers)
  - [Module 4: Debugging, Logs & Live Inspection](#module-4-debugging-logs--live-inspection)
  - [Module 5: Persistent Storage (Volumes & Bind Mounts)](#module-5-persistent-storage-volumes--bind-mounts)
  - [Module 6: Docker Networking](#module-6-docker-networking)
  - [Module 7: Writing Dockerfiles & Custom Images](#module-7-writing-dockerfiles--custom-images)
  - [Module 8: Docker Compose Orchestration](#module-8-docker-compose-orchestration)
  - [Module 9: System Maintenance & Production Security](#module-9-system-maintenance--production-security)
  - [Module 10: 4-Week Hands-On Action Plan](#module-10-4-week-hands-on-action-plan)
- [⚡ Quick Command Reference](#-quick-command-reference)
- [🔒 Production Security Checklist](#-production-security-checklist)
- [🗓️ 4-Week Action Plan Milestones](#️-4-week-action-plan-milestones)
- [🚀 How to Get Started](#-how-to-get-started)
- [📄 License](#-license)

---

## 📖 Overview

Docker packages applications and their dependencies into isolated units called **containers**. Containers share the host OS kernel, making them lightweight, fast, and portable across any environment—eliminating the 'it works on my machine' problem.

This curriculum covers everything from fundamental container concepts to building multi-container microservices using Docker Compose, optimizing multi-stage Dockerfiles, securing images, and creating multi-architecture builds.

---

## 🎓 Course Architecture & 10 Modules

### Module 1: Core Concepts & Architecture
- **Learning Objective:** Understand container architecture vs. traditional Virtual Machines (VMs) and master the three core building blocks.
- **Key Concepts:**
  - **Dockerfile:** The recipe listing step-by-step instructions.
  - **Image:** The read-only immutable blueprint / snapshot.
  - **Container:** The running isolated process instantiated from an image.
  - **Docker Engine Architecture:** CLI client sending instructions to `dockerd` daemon.

### Module 2: Working with Docker Images
- **Learning Objective:** Search, pull, inspect, tag, export, and manage Docker image layers.
- **Key Concepts:**
  - **Docker Hub & Tags:** Understanding version tags (`:3.12-slim`, `:20-alpine`) vs `:latest`.
  - **Union File System:** Read-only layered storage sharing base layers across images.
  - **Image Operations:** Exporting `.tar` archives (`docker save`/`load`) and cleaning dangling images (`docker image prune`).

### Module 3: Running & Managing Containers
- **Learning Objective:** Master container lifecycles, background execution, port forwarding, and restart policies.
- **Key Concepts:**
  - **Detached (`-d`) vs. Interactive (`-it`) Mode:** Running background daemons vs. terminal shells.
  - **Port Mapping (`-p HOST:CONTAINER`):** Bridging network ports between host and container.
  - **Environment Variables (`-e` / `--env-file`):** Passing secrets and configuration at launch time.
  - **Restart Policies:** Using `--restart unless-stopped` for self-healing services.

### Module 4: Debugging, Logs & Live Inspection
- **Learning Objective:** Diagnose crashes, stream live logs, execute commands in running containers, and monitor resource consumption.
- **Key Concepts:**
  - **Process Lifecycle (PID 1):** Why containers stop when their primary process exits.
  - **`docker run` vs `docker exec`:** Creating a new container vs. stepping into a live container.
  - **Resource Limits:** Setting `--memory` caps and `--cpus` limits to prevent host freezing.

### Module 5: Persistent Storage (Volumes & Bind Mounts)
- **Learning Objective:** Store persistent data outside container ephemeral writable layers.
- **Key Concepts:**
  - **Named Volumes:** Docker-managed persistent storage buckets (ideal for databases like PostgreSQL/MySQL).
  - **Bind Mounts:** Mapping local host source directories (`$(pwd):/app`) for live code reloading during development.
  - **Read-Only Mounts:** Protecting code using `:ro` flags.

### Module 6: Docker Networking
- **Learning Objective:** Connect containers over isolated private virtual bridge networks using container names as DNS hostnames.
- **Key Concepts:**
  - **Network Drivers:** Bridge (default private network), Host (shared stack), and None (isolated).
  - **Internal DNS:** Automatic name resolution allowing services (e.g. `api` -> `db`) to communicate without hardcoded IP addresses.

### Module 7: Writing Dockerfiles & Custom Images
- **Learning Objective:** Write production-grade Dockerfile recipes with caching optimizations and multi-stage builds.
- **Key Concepts:**
  - **Layer Caching:** Structuring `COPY package.json` before `COPY . .` to maximize build speeds.
  - **Multi-Stage Builds:** Compiling binaries in heavyweight builder images and copying outputs to lightweight runtime images (`alpine`/`distroless`).
  - **Essential Directives:** `FROM`, `WORKDIR`, `COPY`, `RUN`, `ENV`, `ARG`, `EXPOSE`, `USER`, `HEALTHCHECK`, `ENTRYPOINT`, `CMD`.

### Module 8: Docker Compose Orchestration
- **Learning Objective:** Replace single-container scripts with multi-service `compose.yaml` orchestration files.
- **Key Concepts:**
  - **Multi-Container Stacks:** Defining frontend, API, database, and cache in unified YAML files.
  - **Service Dependencies (`depends_on` + healthchecks):** Managing startup sequences cleanly.
  - **Lifecycle Management:** `docker compose up -d`, `docker compose down -v`, `docker compose logs -f`.

### Module 9: System Maintenance & Production Security
- **Learning Objective:** Reclaim disk space, harden containers against security vulnerabilities, and build multi-arch images.
- **Key Concepts:**
  - **Production Security:** Running as non-root `USER`, minimal base images, avoiding hardcoded secrets.
  - **System Maintenance:** `docker system prune -a --volumes` and `docker builder prune`.
  - **Multi-Arch Builds:** Building universal images (`linux/amd64`, `linux/arm64`) with `docker buildx`.

### Module 10: 4-Week Hands-On Action Plan
- **Learning Objective:** Transition theoretical knowledge into muscle memory via 4 practical milestones.

---

## ⚡ Quick Command Reference

| Command | Category | Description |
| :--- | :--- | :--- |
| `docker version` / `docker info` | **Core** | Display system version and full Docker engine resource overview |
| `docker run hello-world` | **Core** | Run initial test container from Docker Hub |
| `docker pull <image>:<tag>` | **Images** | Download image without starting a container |
| `docker images` | **Images** | List locally stored Docker images |
| `docker rmi <image>` | **Images** | Remove local Docker image |
| `docker image prune -a` | **Images** | Delete all unused images |
| `docker run -d -p 8080:80 --name web <image>` | **Containers** | Run background container with port mapping and custom name |
| `docker run -it <image> sh` | **Containers** | Launch container into interactive terminal shell |
| `docker run --rm <image>` | **Containers** | Run container and automatically remove it upon exit |
| `docker ps` / `docker ps -a` | **Containers** | List active / all containers |
| `docker stop <cont>` / `docker start <cont>` | **Containers** | Gracefully stop / restart container |
| `docker rm <cont>` / `docker container prune` | **Containers** | Remove specific / all stopped containers |
| `docker logs -f --tail 100 <cont>` | **Debugging** | Tail and live-stream container console logs |
| `docker exec -it <cont> bash` | **Debugging** | Open interactive terminal inside a running container |
| `docker cp <src> <cont>:<dest>` | **Debugging** | Copy files between host computer and container |
| `docker stats` | **Debugging** | Live task manager dashboard for CPU, RAM, & Network |
| `docker volume create <name>` | **Volumes** | Create a Docker-managed persistent volume |
| `docker run -v <vol>:/path <image>` | **Volumes** | Mount named persistent volume |
| `docker run -v $(pwd):/app <image>` | **Volumes** | Bind mount current working directory into container |
| `docker network create <net>` | **Networking** | Create custom private virtual bridge network |
| `docker run --network <net> <image>` | **Networking** | Attach container to custom virtual network |
| `docker build -t <name>:<tag> .` | **Dockerfiles** | Build Docker image from Dockerfile in current directory |
| `docker compose up -d` | **Compose** | Build and start multi-container stack in detached mode |
| `docker compose down -v` | **Compose** | Stop stack and purge named volumes |
| `docker system prune -a --volumes` | **Maintenance** | Full system cleanup of unused images, containers, & volumes |

---

## 🔒 Production Security Checklist

- [ ] **Non-Root Execution:** Always define a non-privileged user using `USER <username>` in Dockerfile.
- [ ] **Minimal Base Images:** Use `-alpine`, `-slim`, or `distroless` images to reduce vulnerability surface area.
- [ ] **No Hardcoded Secrets:** Never bake credentials, tokens, or `.env` files into Dockerfiles or images; inject via environment variables or secrets management at runtime.
- [ ] **Use `.dockerignore`:** Exclude `node_modules`, `.git`, `.env`, and temporary files from image context.
- [ ] **Read-Only Filesystem:** Mount code directories as read-only (`:ro`) where application writes are not required.
- [ ] **Resource Limits:** Constrain container RAM and CPU allocation using `--memory` and `--cpus`.

---

## 🗓️ 4-Week Action Plan Milestones

1. **Milestone 1 (Days 1–5): Tame Pre-Built Containers**
   - Run `nginx:alpine` on port 8080.
   - Use `docker exec -it` to modify `/usr/share/nginx/html/index.html` live.
   - Practice stopping and removing containers (`docker stop`, `docker rm`, `docker rmi`).

2. **Milestone 2 (Days 6–12): Prove Data Persistence & Networking**
   - Create custom network `lab-net` and volume `db-data`.
   - Launch PostgreSQL attached to both, seed data, force-kill container (`docker rm -f`), and recreate container to verify data survives.

3. **Milestone 3 (Days 13–20): Containerize Your Own App**
   - Write a Web API (Node.js / Python / Go).
   - Write optimized Dockerfile with layer caching, non-root user, and `HEALTHCHECK`.
   - Build image and push to Docker Hub registry.

4. **Milestone 4 (Days 21–28): Full-Stack Orchestration with Docker Compose**
   - Combine Web API, PostgreSQL, and Redis into `compose.yaml`.
   - Configure bind mount for live-reload development.
   - Test full orchestration lifecycle (`docker compose up -d` & `docker compose down`).

---

## 🚀 How to Get Started

1. **Prerequisites:** Install Docker Desktop or Docker Engine (v20+).
2. **Verify Installation:**
   ```bash
   docker --version
   docker run hello-world
   ```
3. **Explore the Syllabus:** Follow the 10 modules sequentially to build your container skills!

---

## 📄 License

This repository and curriculum reference are open source under the MIT License.
