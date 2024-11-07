FROM node:18 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html

# Копируем пользовательскую конфигурацию Nginx, если это необходимо
# COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 3000

# Запуск Nginx
CMD ["nginx", "-g", "daemon off;"]
