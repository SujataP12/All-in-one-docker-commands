# 🧩 Docker Compose Commands - Cheat Sheet

| Command | Description |
|---------|-------------|
| `docker-compose up` | Start all services defined in `docker-compose.yml` |
| `docker-compose up -d` | Start services in **detached** mode (background) |
| `docker-compose down` | Stop and remove all services, networks, and volumes created by `up` |
| `docker-compose build` | Build or rebuild services |
| `docker-compose pull` | Pull service images from the registry |
| `docker-compose push` | Push service images to the registry |
| `docker-compose stop` | Stop running containers without removing them |
| `docker-compose start` | Start existing containers that were stopped |
| `docker-compose restart` | Restart all services |
| `docker-compose ps` | List containers managed by Docker Compose |
| `docker-compose logs` | View logs from services |
| `docker-compose logs -f` | View logs and follow output (live updates) |
| `docker-compose exec <service> <command>` | Execute a command in a running container (like `docker exec`) |
| `docker-compose run <service> <command>` | Run a one-time command in a new container |
| `docker-compose config` | Validate and view the final Compose configuration |
| `docker-compose down -v` | Remove volumes along with containers and networks |

---

## 🔖 Example: Typical Workflow

```bash
docker-compose up -d        # Start services in background
docker-compose logs -f      # Follow logs
docker-compose exec app sh  # Access container shell
docker-compose down         # Stop and clean up
```

#### Here's a docker-compose.yml file that sets up a simple web application with **Node.js** and a **MongoDB database**.

```sh
# docker-compose.yml

version: '3.8'

services:
  app:
    build: .
    container_name: node-app
    ports:
      - "3000:3000"
    environment:
      - MONGO_URL=mongodb://db:27017/mydb
    depends_on:
      - db
    volumes:
      - .:/app
    networks:
      - app-network

  db:
    image: mongo:6
    container_name: mongo-db
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db
    networks:
      - app-network

volumes:
  mongo-data:

networks:
  app-network:

```
### 📝 Explanation
| Section                 | Purpose                                                         |
| ----------------------- | --------------------------------------------------------------- |
| `version: '3.8'`        | Docker Compose file format version.                             |
| `services:`             | Defines all containerized services.                             |
| `app:`                  | The Node.js application container.                              |
| `build: .`              | Builds the image from the Dockerfile in the current directory.  |
| `ports:`                | Maps port 3000 from container to host.                          |
| `environment:`          | Passes environment variables (e.g., MongoDB connection string). |
| `depends_on:`           | Ensures the MongoDB service starts before the app.              |
| `volumes:`              | Mounts current directory into the container.                    |
| `db:`                   | MongoDB service using the official image.                       |
| `volumes:` (under `db`) | Persistent storage for MongoDB data.                            |
| `networks:`             | Creates an isolated network for service communication.          |

### ▶️ Run the App
```sh
docker-compose up --build
```
To stop and clean up:
```sh
docker-compose down -v
```
