# 🧩 Docker Compose & Multi-Container Apps (DevOps)

[[Docker Volumes & Storage]] ← Previous

> [!info] Purpose
Docker Compose simplifies **running multi-container applications**.  
DevOps engineers use it to **define services, networks, and volumes** in a single YAML file for reproducible deployments.

---

## 🔹 What is Docker Compose?
- Tool to define **multi-container apps**  
- Uses **docker-compose.yml**  
- Handles **networks, volumes, dependencies** automatically  
- Commands: `docker-compose up`, `docker-compose down`, `docker-compose logs`

---

## 🔹 Basic docker-compose.yml
```yaml
version: "3.9"

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  app:
    build: .
    volumes:
      - .:/app
    ports:
      - "5000:5000"
```

Commands
```
docker-compose up -d        # Start services
docker-compose ps           # List running services
docker-compose logs -f      # Follow logs
docker-compose down         # Stop and remove containers
```

## 🔹 Using Networks & Volumes in Compose

```yaml
version: "3.9"

services:
  db:
    image: postgres:15
    volumes:
      - db_data:/var/lib/postgresql/data
    environment:
      POSTGRES_PASSWORD: example

  app:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db
    networks:
      - app_net

volumes:
  db_data:

networks:
  app_net:
```

## 🔹 Environment Variables

- Store secrets or config in `.env` file

```env
POSTGRES_PASSWORD=supersecret
APP_ENV=development
```

Use in docker-compose.yml

```yaml
environment:
  POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
  APP_ENV: ${APP_ENV}
```

## 🔹 Scaling Services

```bash
# Scale web service to 3 instances
docker-compose up -d --scale web=3
```

Stop Compose from Python

```python
subprocess.run(["docker-compose", "down"])
```

Monitor logs

```python
subprocess.run(["docker-compose", "logs", "-f"])
```

---

## 🔹 Best Practices

- Use **named volumes** for databases
    
- Use **networks** to isolate app components
    
- Keep `.env` files **outside version control**
    
- Use **depends_on** carefully; consider health checks
    
- Automate Compose in **CI/CD pipelines**

> [!tip]  
> Docker Compose is essential for **multi-container DevOps environments**:

- Combine services, networks, and volumes in one file
    
- Use `.env` for configuration
    
- Automate builds and deployments with Python or CI/CD