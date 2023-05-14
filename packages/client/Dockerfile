# FROM node:16-alpine as build
# WORKDIR /app
# COPY ./package.json ./package.json
# COPY ./build /app/build

# RUN yarn install --immutable

# FROM nginx:stable-alpine
# COPY --from=build /app/build /var/www
# CMD ["nginx", "-g", "daemon off;"]


FROM node:16-alpine as build
WORKDIR /app
COPY ./package.json ./package.json
COPY ./build /app/build

RUN yarn install --immutable

FROM node:16-alpine as server
WORKDIR /app
COPY --from=build /app .
EXPOSE 3000
CMD ["yarn", "start"]

FROM nginx:stable-alpine
COPY --from=build /app/build /var/www
COPY nginx.conf /etc/nginx/nginx.conf
CMD ["nginx", "-g", "daemon off;"]






# FROM node:16-alpine
# WORKDIR /app
# #COPY ./package.json ./package.json
# COPY . ./
# #COPY serve.json ./
# RUN yarn install serve --immutable
# #COPY ./build /app/build
# CMD serve


# FROM node:16-alpine
# # set the working direction
# WORKDIR /app
# # add `/app/node_modules/.bin` to $PATH
# ENV PATH /app/node_modules/.bin:$PATH
# # install app dependencies
# COPY package.json ./
# #COPY yarn.lock ./
# # rebuild node-sass
# RUN yarn add node-sass
# RUN yarn install --immutable
# # add app
# COPY . ./
# # start app
# CMD ["yarn", "start"]
