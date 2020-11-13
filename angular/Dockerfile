# building app
FROM node:12.13.0 as build

WORKDIR /app

COPY . .

RUN npm ci --silent
RUN npm run build -- --deployUrl /angular/

# starting nginx
FROM nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /app/dist/angular /usr/share/nginx/html

