# 📦 Docker Volumes - Command Table

| Command | Description |
|--------|-------------|
| `docker volume create <volume_name>` | Create a new volume named volume_name |
| `docker volume ls` | List all Docker volumes |
| `docker volume inspect <volume_name>` | Show detailed info about a volume |
| `docker volume rm <volume_name>` | Remove a specific volume |
| `docker volume prune` | Remove all **unused** volumes |
| `docker run -v <volume_name>:<container_path> <image>` | Mount a named volume into a container |
| `docker run -v /host/path:/container/path <image>` | Bind mount: map host directory into container |
| `docker volume ls -f dangling=true` | List **dangling (unused)** volumes |
| `docker system prune --volumes` | Remove **all unused data**, including volumes |

---

## 🔖 Example: Run a Container with Volume

```bash
docker volume create myvolume
docker run -d -v myvolume:/usr/share/nginx/html nginx
