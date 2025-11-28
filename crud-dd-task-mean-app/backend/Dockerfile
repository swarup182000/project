# Stage 1: Build dependencies
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Stage 2: Production minimal image
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app /app
EXPOSE 8080
CMD ["node", "server.js"]

