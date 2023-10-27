# Use Node image as the base image
FROM node:latest as builder

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the entire source code to the working directory
COPY . .

# Build the Angular application
RUN npm run build

# Use Nginx as the base image to serve the Angular application
FROM nginx:latest

# Copy the compiled Angular app to the default Nginx public folder
COPY --from=builder /app/dist/your-angular-app /usr/share/nginx/html

# Expose port 80 for the web server
EXPOSE 80
