FROM node:16-bullseye as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN #!/bin/sh npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html 