FROM node:12-alpine as builder
USER node
RUN mkdir /home/node/app/
WORKDIR /home/node/app/
COPY ./package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx:stable
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /home/node/app/build/ /usr/share/nginx/html/
