# 🖼️ Docker Image Commands - Cheat Sheet
---
| Command | Description |
|---------|-------------|
| `docker images` | List all local Docker images |
| `docker pull <image>` | Download an image from Docker Hub |
| `docker build -t <name>:<tag> .` | Build an image from a Dockerfile |
| `docker tag <image> <new_name>:<tag>` | Tag an image with a new name or version |
| `docker push <name>:<tag>` | Push an image to a remote registry (e.g., Docker Hub) |
| `docker rmi <image>` | Remove one or more images |
| `docker image inspect <image>` | View detailed information about an image |
| `docker image history <image>` | Show history of image layers |
| `docker save -o <file>.tar <image>` | Save image to a tar archive |
| `docker load -i <file>.tar` | Load image from a tar archive |
| `docker image prune` | Remove all unused images |
| `docker system prune --all` | Remove unused containers, images, volumes, and networks |

---

## 🔖 Example: Build and Push a Custom Image

```bash
docker build -t myapp:latest .
docker tag myapp:latest mydockerhubuser/myapp:latest
docker push mydockerhubuser/myapp:latest
