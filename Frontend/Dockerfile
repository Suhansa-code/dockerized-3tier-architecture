# Use an official Node.js image as the base image for the build stage
FROM node:16 AS builder

# Set the working directory inside the container
WORKDIR /frontend

# Copy package files to the container to install dependencies
COPY frontend/package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application files to the container
COPY . .

# Build the application for production
RUN npm run build

# Use a lightweight Nginx image for serving the application
FROM nginx:alpine

# Copy the build output from the builder stage to the Nginx HTML directory
COPY --from=builder /frontend/dist /usr/share/nginx/html

# Expose port 80 for HTTP traffic
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
