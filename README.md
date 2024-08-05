```sh
# create network
docker network create goals-node

# build images
docker build ./backend
docker build ./frontend

# run backend
cd backend && docker run --name mongodb --rm -p27017:27017 --network goals-node mongo

# run frontend
cd frontend && docker run --name goals-frontend --rm -p3000:3000 --network goals-node -it goals-node-front
```
