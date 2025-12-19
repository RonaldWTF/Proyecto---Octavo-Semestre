# Usamos una imagen ligera de Node
FROM node:18-alpine

# Directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiamos package.json primero (para aprovechar caché de Docker)
COPY package*.json ./

# Instalamos dependencias
RUN npm install

# Copiamos el resto del código
COPY . .

# Comando para iniciar (asegúrate que en tu package.json exista "start" o "dev")
CMD ["npm", "run", "dev"]