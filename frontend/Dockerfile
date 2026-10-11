# ==========================================================
# ETAPA 1: Builder (Compilación y generación de artefactos)
# ==========================================================
FROM node:24-alpine AS builder

# Habilitar pnpm
RUN npm i -g pnpm@12.6.0

WORKDIR /app

COPY . . 

RUN pnpm install --frozen-lockfile

ARG VITE_API_URL
ENV VITE_API_URL=${VITE_API_URL}


# Compilar TypeScript a JavaScript (/dist)
RUN pnpm build

# ==========================================================
# ETAPA 2: Runner (Entorno de Ejecución Mínimo en Producción)
# ==========================================================
FROM nginx:alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copiar el cliente de Prisma generado y el build
COPY --from=builder /app/dist  /usr/share/nginx/html

EXPOSE 80

# SCRIPT DE ARRANQUE RESILIENTE:
# 1. Nginx sirve los archivos estáticos compilados
CMD ["nginx", "-g", "daemon off;"]
