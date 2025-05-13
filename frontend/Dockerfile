# Step 1: Build the app using Node
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Step 2: Serve the app using nginx
FROM nginx:stable-alpine

# Copy built frontend files
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80 for nginx
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

