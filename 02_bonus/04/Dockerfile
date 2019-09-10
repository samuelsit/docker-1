FROM node:7

WORKDIR /app

COPY app/package.json /app

RUN npm install

COPY app/index.js /app

EXPOSE 8081

CMD node index.js
