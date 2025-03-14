# Use a smaller base image (Alpine-based Node image)
FROM node:14-alpine AS builder

# Set the working directory
WORKDIR /usr/src/app

# Copy the application files
COPY . .

# Install dependencies
RUN npm install

# Remove unnecessary files to reduce size
RUN rm -rf node_modules/.cache

# Use a minimal runtime image
FROM node:14-alpine

# Set the working directory
WORKDIR /usr/src/app

# Copy files from the builder stage
COPY --from=builder /usr/src/app .

# Start the application
CMD ["node", "index.js"]