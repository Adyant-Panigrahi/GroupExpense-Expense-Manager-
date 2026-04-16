FROM node:18-bullseye

WORKDIR /app

COPY package*.json ./
RUN npm install

RUN apt-get update && apt-get install -y openssl

COPY . .

RUN npx prisma generate

CMD ["npm", "run", "dev"]
