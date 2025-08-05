# STAGE 1: Сборка статических файлов Angular
FROM node:14-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --prod


# STAGE 2: Создание финального образа с Nginx
FROM nginx:stable-alpine

COPY --from=builder /app/dist/frontend /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]