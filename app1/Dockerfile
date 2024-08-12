FROM node:lts-alpine

# Instalar http-server para servir contenido estático
RUN npm install -g http-server

# Establecer el directorio de trabajo
WORKDIR /app

# Copiar los archivos de dependencias
COPY app/package*.json ./

# Instalar las dependencias del proyecto
RUN npm install

# Copiar todos los archivos de la aplicación al directorio de trabajo
COPY app/ .

# Construir la aplicación para producción con minificación
RUN npm run build

# Exponer el puerto 8000
EXPOSE 8000

# Comando para ejecutar el servidor en el contenedor
CMD [ "http-server", "dist", "-p", "8000" ]