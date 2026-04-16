FROM node:20-bullseye

WORKDIR /app

COPY package*.json ./

RUN npm config set fetch-timeout 600000 \
 && npm config set fetch-retries 5 \
 && npm ci

COPY . .

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]