FROM node:15.4-slim as build 
ARG REACT_APP_PUBLIC_URL=$REACT_APP_PUBLIC_URL
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN REACT_APP_PUBLIC_URL=$REACT_APP_PUBLIC_URL npm run build

FROM nginx:1.19
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/build /usr/share/nginx/html
