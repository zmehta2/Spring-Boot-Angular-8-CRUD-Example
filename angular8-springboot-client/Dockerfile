# Use Node.js as base image
FROM node:16-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json package-lock.json ./
RUN npm install --legacy-peer-deps

# Copy the rest of the application files
COPY . .

# Build the Angular app
RUN npm run build --prod

# Use Nginx for serving Angular
FROM nginx:alpine

# Copy built files from previous stage
COPY --from=build /app/dist/angular8-springboot-client /usr/share/nginx/html

# Expose the application port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
