# ------------------ Build Stage ------------------
FROM node:20 AS build

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Install Angular CLI globally if not in package.json
RUN npm install -g @angular/cli@15

# Copy all source
COPY . .

# Build Angular app
RUN npm run build --prod

# ------------------ Runtime Stage ------------------
FROM nginx:alpine

# Copy build output to nginx
COPY --from=build /app/dist/web-application /usr/share/nginx/html

# Copy custom Nginx config for Angular routing
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
