FROM node:24-alpine

WORKDIR /test-app/src/app

COPY . /test-app/src/app

RUN npm install -g @angular/cli

RUN npm install --force

CMD ["ng", "serve", "--host", "0.0.0.0"]
