FROM node:alpine as builder

WORKDIR /app

COPY ./package.json ./
RUN npm install

COPY ./ ./
RUN npm run build


FROM nginx:alpine
EXPOSE 3000
COPY --from=builder /app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf