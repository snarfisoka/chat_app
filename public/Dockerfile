FROM node:18 AS BUILD

WORKDIR /app

COPY package.json yarn.lock ./
RUN yarn install

COPY . .
RUN yarn build

FROM node:18

WORKDIR /app

RUN yarn global add serve

COPY --from=build /app/build ./build

CMD ["serve", "-s", "build", "-l", "3000"]