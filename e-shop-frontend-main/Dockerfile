# Build stage
FROM node:18-alpine AS build

WORKDIR /app

# Копирај само package.json и package-lock.json (или yarn.lock) за побрзо кеширање
COPY package*.json ./
RUN npm install

# Копирај целиот код и билдни
COPY . .
RUN npm run build

# Production stage
FROM nginx:alpine

# Копирај билднатиот фронтенд во Nginx
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80
