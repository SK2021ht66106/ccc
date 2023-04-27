FROM node:16-alpine as build
WORKDIR /app
COPY ./package.json ./package.json
COPY ./build /app/build

RUN yarn install --immutable

CMD [ "yarn", "start:webprod"]

# FROM nginx:stable-alpine
# COPY --from=build /app/build /var/www
# CMD ["nginx", "-g", "daemon off;"]
