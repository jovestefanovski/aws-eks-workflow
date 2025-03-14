# Use a smaller base image (Alpine-based Node image)
FROM node:14-alpine AS builder

# Set the working directory
WORKDIR /usr/src/app

# Copy the application files
COPY . .

# Install dependencies
RUN npm install --only=production

# Remove unnecessary files to reduce size
RUN rm -rf node_modules/.cache

# Use a minimal runtime image
FROM node:14-alpine

# Set the working directory
WORKDIR /usr/src/app

# Copy files from the builder stage
COPY --from=builder /usr/src/app . 

# Expose port 3000
EXPOSE 3000

# Start the application
CMD ["npm", "start"]