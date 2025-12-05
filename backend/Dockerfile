FROM node:18-alpine3.17

# Install python3, pip, ffmpeg (required dependencies)
RUN apk add --no-cache python3 py3-pip ffmpeg

# Install yt-dlp via pip
RUN pip3 install yt-dlp

# Set working directory
WORKDIR /

# Copy package.json and package-lock.json
COPY package*.json ./

# Install node dependencies
RUN npm install

# Copy rest of backend source code
COPY . .

# Copy nginx config from parent directory
COPY ../nginx.conf /etc/nginx/nginx.conf

# Create necessary directories
RUN mkdir -p /var/run/nginx

# Expose rtmp ports
EXPOSE 1935

# Start nginx and Node.js
CMD ["sh", "-c", "nginx && npm start"]
# Expose backend port
EXPOSE 3000

# Start backend server
CMD ["node", "index.js"]





