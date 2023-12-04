
# Stage 1: Build the Node.js app
FROM node:16-alpine as build
WORKDIR /app
COPY ./package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve the app with Nginx
FROM nginx:latest

COPY --from=build /app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
EXPOSE 3000
