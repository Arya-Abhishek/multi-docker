FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build
# https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/learn/lecture/29431298#questions/18841478 -> Why RUN instead of CMD

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html