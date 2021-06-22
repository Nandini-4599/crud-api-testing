FROM node:16-alpine3.11 as build
LABEL stage=build

WORKDIR /app

COPY . .

RUN apk update && \
    apk add --no-cache python2 && \
    npm install -g @angular/cli && \
    npm install && \
    ng build --prod

FROM nginx:alpine as runtime
COPY --from=build /app/dist/CustomerSeviceApp /usr/share/nginx/html
