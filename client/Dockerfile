FROM node:14.14.0-alpine

WORKDIR "/app"

COPY ./client/package.json .

RUN npm install

COPY ./client/ .

RUN npm run build

FROM nginx:latest

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=0 /app/build /usr/share/nginx/html