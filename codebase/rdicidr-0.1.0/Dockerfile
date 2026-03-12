FROM node:15 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM nginx:alpine

WORKDIR /usr/share/nginx/html

COPY --from=builder /app/build .

RUN chmod -R 755 /usr/share/nginx/html

ENTRYPOINT ["nginx", "-g", "daemon off;"]
