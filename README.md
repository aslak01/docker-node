### Commands

Naming (and tagging (-t)) the image "node app image" for reference in list of docker images
```bash
docker build -t node-app-image .
```
Running the container in detached mode and naming it "node-app" in list of containers, sending traffic to port 3000 in container from localhost:3000, linking PWD to /app in container (read only), making a volume for the container's node_modules to prevent it being overwritten by the missing node_modules folder locally.
```bash
docker run -v $(PWD):/app:ro -v /app/node_modules -p 3000:3000 --env-file ./.env -d --name node-app node-app-image
```
Mega long command replaced with docker compose
```bash
docker-compose up -d
```
Docker compose with dev and prod

dev
```bash
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d
```
prod
```bash
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build
```
Enter container
```bash
docker exec -it node-app bash
```

Bringing the container down, removing anonymous volumes
```bash
docker-compose down -v
```