FROM node:18 AS build
WORKDIR /app
COPY . .
ARG REACT_APP_API_URL
ENV REACT_APP_API_URL=$REACT_APP_API_URL
RUN npm install && NODE_OPTIONS=--openssl-legacy-provider npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80