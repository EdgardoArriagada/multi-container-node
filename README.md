```sh
# create network
docker network create goals-node

# build images
docker build -t goals-node ./backend
docker build -t goals-node-front ./frontend

# run db
docker run --name mongodb --rm --network goals-node mongo

# run backend
cd backend && docker run --name goals-backend --rm --network goals-node -p80:80 goals-node

# run frontend
cd frontend && docker run --name goals-frontend --rm -p3000:3000 -it goals-node-front
```
