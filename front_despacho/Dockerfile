# Etapa de build
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build

# Etapa de producción
FROM nginx:stable-alpine
COPY --from=build /app/dist /usr/share/nginx/html

# Mejoras de seguridad y permisos
RUN chown -R nginx:nginx /usr/share/nginx/html && \
    chmod -R 755 /usr/share/nginx/html

EXPOSE 80
USER nginx
CMD ["nginx", "-g", "daemon off;"]
