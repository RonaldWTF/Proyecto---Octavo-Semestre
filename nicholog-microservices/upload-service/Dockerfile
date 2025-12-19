FROM node:18-alpine
WORKDIR /app
COPY package*.json ./

# AQUI ESTA EL CAMBIO: --force para evitar el error ERESOLVE
RUN npm install --force

COPY . .
CMD ["npm", "run", "dev"]