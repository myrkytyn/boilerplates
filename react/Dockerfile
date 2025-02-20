# Multi-stage Dockerfile for React app
FROM node:22 AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM caddy:2-alpine AS production
COPY --from=build /app/dist /var/www
COPY ./Caddyfile /etc/caddy/Caddyfile 
EXPOSE 80