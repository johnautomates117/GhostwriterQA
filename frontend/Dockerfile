# Frontend Dockerfile - Fixed version
FROM node:18-alpine

WORKDIR /app

# Copy package files
COPY package*.json ./

# Clean install dependencies
RUN rm -rf node_modules package-lock.json && \
    npm cache clean --force && \
    npm install

# Copy application files
COPY . .

# Ensure vite config is used
COPY vite.config.docker.ts vite.config.ts

# Expose port
EXPOSE 3000

# Start development server
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]