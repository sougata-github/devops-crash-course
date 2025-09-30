# Base image with Node.js 22 on Alpine Linux
FROM node:22-alpine

# Set the working directory
WORKDIR /app

# Copy files from current directory to Docker image
COPY . .

# Install dependencies
RUN npm install

# Run the app by specifying command
CMD ["npm", "run", "dev"]

