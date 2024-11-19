# Use an official Node.js image as the base image
FROM node:16

# Set the working directory inside the container
WORKDIR /backend

# Copy package files to the container for dependency installation
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application files to the container
COPY . .

# Expose port 3000 for backend service
EXPOSE 3000

# Start the application
CMD ["node", "index.js"]
