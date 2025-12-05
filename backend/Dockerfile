FROM node:18-alpine3.17

RUN apk add --no-cache python3 py3-pip ffmpeg
RUN pip3 install yt-dlp

WORKDIR /app

COPY backend/package.json ./
COPY package-lock.json ./
RUN npm ci --only=production

COPY backend/ .
COPY frontend/ ./public/
RUN mkdir -p /recordings /app/public

# FORCE PORT 10000 for Render
EXPOSE 10000

CMD ["node", "index.js"]
