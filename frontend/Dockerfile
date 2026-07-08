FROM node:22-alpine AS builder

WORKDIR /app

ARG REACT_APP_API_URL="http://backend:8765/api"
ENV REACT_APP_API_URL=$REACT_APP_API_URL

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

FROM nginx:stable-alpine

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 7896

CMD ["nginx", "-g", "daemon off;"]