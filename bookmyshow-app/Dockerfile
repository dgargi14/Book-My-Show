# Start with Node.js 18 (Jenkins can override this if needed)
FROM node:18 AS base

# Define application working directory
WORKDIR /usr/src/app

# Copy dependency files first for better cache
COPY ["package.json", "package-lock.json", "./"]

# Fix PostCSS issue and install dependencies
RUN npm install postcss@8.4.21 postcss-safe-parser@6.0.0 --legacy-peer-deps \
    && npm install --silent

# Copy the full project
COPY . .

# Environment variables
ENV NODE_OPTIONS="--openssl-legacy-provider" \
    PORT=3000

# Expose container port
EXPOSE ${PORT}

# Start the application
CMD ["npm", "start"]
