# 🐳 Docker Containers - Basic Commands Cheat Sheet

## 🔍 View Containers
---
| Command | Description |
|--------|-------------|
| `docker ps` | List running containers |
| `docker ps -a` | List **all** containers (including stopped ones) |

## 🚀 Run a Container
---

| Command | Description |
|--------|-------------|
| `docker run <image>` | Run a container from an image |
| `docker run -it <image> bash` | Run interactively with a shell |
| `docker run -d <image>` | Run in **detached** mode (in background) |
| `docker run -p <host_port>:<container_port> <image>` | Map container port to host |
| `docker run --name <name> <image>` | Run with a specific container name |
| `docker run -v <host_path>:<container_path> <image>` | Mount a volume |

### Example:
```bash
docker run -d -p 8080:80 --name webserver nginx
```

## ⏹️ Stop, Start, Restart Containers

---
| Command                         | Description               |
| ------------------------------- | ------------------------- |
| `docker stop <container_id>`    | Stop a running container  |
| `docker start <container_id>`   | Start a stopped container |
| `docker restart <container_id>` | Restart a container       |

## ❌ Remove Containers
---
| Command                       | Description                   |
| ----------------------------- | ----------------------------- |
| `docker rm <container_id>`    | Remove a container            |
| `docker rm -f <container_id>` | Force remove a container      |
| `docker container prune`      | Remove all stopped containers |
## 📝 Inspect & Logs
---
| Command                         | Description                 |
| ------------------------------- | --------------------------- |
| `docker logs <container_id>`    | View container logs         |
| `docker inspect <container_id>` | Get detailed container info |

## 📌 Notes
- Use docker ps -q to get only container IDs.

- Combine commands: docker stop $(docker ps -q) to stop all running containers.

