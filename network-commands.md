# 🌐 Docker Network Commands - Cheat Sheet
---

| Command | Description |
|---------|-------------|
| `docker network ls` | List all Docker networks |
| `docker network create <network_name>` | Create a custom network |
| `docker network inspect <network_name>` | View detailed information about a network |
| `docker network rm <network_name>` | Remove a Docker network |
| `docker network connect <network_name> <container>` | Connect a container to a network |
| `docker network disconnect <network_name> <container>` | Disconnect a container from a network |
| `docker run --network <network_name> <image>` | Run a container on a specific network |
| `docker network prune` | Remove all **unused** networks |

---

## 🔖 Example: Create and Use a Custom Network

```bash
docker network create mynet
docker run -d --name container1 --network mynet nginx
docker run -d --name container2 --network mynet alpine sleep 1000
```
- 🔁 These containers can now communicate using container names (e.g., ping container1 from container2).

## 🧠 Default Docker Networks

| Network Name | Type   | Description                             |
| ------------ | ------ | --------------------------------------- |
| `bridge`     | Bridge | Default for containers on a single host |
| `host`       | Host   | Shares host network stack (Linux-only)  |
| `none`       | Null   | No networking                           |
