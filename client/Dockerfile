# Use an official Node.js 18 image as the build environment
FROM node:16-alpine3.16 AS build

# Set the working directory in the container
WORKDIR /client

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install dependencies without caching
RUN npm ci 

# Copy the rest of the application code to the container
COPY . .

#Run build to output Production files
RUN npm run build

#Add multi-stage build with minimal Alpine
#FROM node:16-alpine3.16
FROM node:16-alpine3.16

WORKDIR /app

# Install only necessary system packages
RUN apk add --no-cache nodejs

#Copy build output from previous stage

COPY --from=build /client/build /app
COPY --from=build /client/public ./public
COPY --from=build /client/src ./src


#Copy package.json and Install production dependencies, removing unnecessary files
COPY --from=build /client/package*.json ./
#RUN apk add npm --no-cache npm
RUN npm install --production && npm cache clean --force

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run your app
CMD ["npm", "start"]

