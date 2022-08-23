FROM node:14-alpine as node 

RUN npm i -g pnpm

WORKDIR /code

COPY package.json pnpm-lock.yaml /code/

RUN pnpm i --frozen-lockfile

COPY . /code

RUN pnpm build

FROM nginx:alpine

COPY --from=node /code/dist /usr/share/nginx/html