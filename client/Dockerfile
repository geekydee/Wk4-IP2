# Use an official Node.js 18 image as the build environment
FROM node:16-slim AS build

# Set the working directory in the container
WORKDIR /client

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install dependencies without caching
RUN npm ci --no-cache

# Copy the rest of the application code to the container
COPY . .

#Add multi-stage build with minimal Alpine
FROM alpine:3.17.9

WORKDIR /app

# Install npm and remove unnecessary files to keep the image small
RUN apk add --no-cache npm

COPY --from=build /client /app

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run your app
CMD ["npm", "start"]

