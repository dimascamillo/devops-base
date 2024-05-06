# version node and instal him
FROM node:18-slim

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

# Port in container
EXPOSE 3000

# Command for run application when Container is up
CMD ["pnpm", "run", "start"]

# docker build -t api-test . ## or docker build -t api-test -f name_file

# docker image ls

# docker run --rm -p 3000:3000 -d api-test:v1 .
# The params --rm delete this Container when it is stopped.

# docker ps - See all running container

# docker stop CONTAINER_ID