FROM node:23.9-alpine

WORKDIR /app

# Copy package files first for caching
COPY ./frontend/package.json ./frontend/package-lock.json* ./

# Install dependencies (including Vite)
RUN npm install

# Copy the rest of the app
COPY ./frontend .

# Start the dev server
CMD ["npm", "run", "dev", "--", "--host"]