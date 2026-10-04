# Stage 1: Build Angular application
FROM node:22 AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build -- --base-href /


# Stage 2: Serve Angular application
FROM nginx:alpine

COPY --from=build /app/dist/doctor-website/browser /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]