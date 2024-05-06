# version node and instal him
FROM node:18 AS build

# Install pnpm
RUN npm i -g pnpm

# Directory of dependencies
WORKDIR /usr/src/app

# Copy package.json of project from container
COPY package.json pnpm-lock.yaml ./

# Install dependencies
RUN pnpm i

# Copy all files from container
COPY . .

# Build Project
RUN pnpm build

# Install only production dependencies
RUN pnpm i --filter production

# Second Stage
FROM node:18-alpine3.19

WORKDIR /usr/src/app

COPY --from=build /usr/src/app/package.json ./package.json
COPY --from=build /usr/src/app/dist ./dist
COPY --from=build /usr/src/app/node_modules ./node_modules

# Port in container
EXPOSE 3000

# Command for run application when Container is up
CMD ["pnpm", "run", "start:prod"]

# docker build -t api-test . ## or docker build -t api-test -f name_file

# docker image ls

# docker run --rm -p 3000:3000 -d api-test:v1 .
# The params --rm delete this Container when it is stopped.

# docker ps - See all running container

# docker stop CONTAINER_ID

# docker network ls

# docker network create name_network

# docker run --network=name_network -p 3000:3000 -d api-test:v2

# docker volume create name_volum

# docker -v name_volum:/usr/src/app -p 3000:3000 api-test:v1 