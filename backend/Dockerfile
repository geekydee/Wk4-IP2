# Use an official Node runtime as a parent image
FROM node:16-alpine3.16 AS build

# Set the working directory in the container
WORKDIR /backend

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm ci 

# Copy the rest of the application code to the container
COPY . .

#A new stage from a minimal image 
FROM alpine:3.19

WORKDIR /app

RUN apk add --no-cache nodejs

COPY --from=build /backend /app

# Expose the port the app runs on
EXPOSE 5000

# Define the command to run your app
CMD ["node", "server.js"]
