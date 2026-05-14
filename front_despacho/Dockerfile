# Etapa de build
FROM node:20-alpine AS build
WORKDIR /app

# Copiar archivos de dependencias primero (mejor caché)
COPY package*.json ./
RUN npm ci

# Copiar el resto del código
COPY . .

# Ejecutar el build
RUN npm run build

# Etapa de producción
FROM nginx:stable-alpine

COPY --from=build /app/dist /usr/share/nginx/html

# Permisos de seguridad
RUN chown -R nginx:nginx /usr/share/nginx/html && \
    chmod -R 755 /usr/share/nginx/html

EXPOSE 80
USER nginx
CMD ["nginx", "-g", "daemon off;"]
