FROM node:14-alpine as build
WORKDIR /usr/src/frontend
COPY package*.json ./
RUN npm install
COPY . ./
RUN npm run build


FROM nginx:1.12.0-alpine
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY --from=build /usr/src/frontend/build /usr/share/nginx/html/bookstore
EXPOSE 80
