# Use a lightweight Node.js runtime
FROM node:22-alpine

# Create application directory
WORKDIR /app

# Copy package files first for better layer caching
COPY package*.json ./

# Install production dependencies
RUN npm ci --omit=dev

# Copy application source
COPY . .

# Create a non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Set ownership
RUN chown -R appuser:appgroup /app

# Run as non-root
USER appuser

# Backend application port
EXPOSE 5000

# Start the application
CMD ["npm", "start"]