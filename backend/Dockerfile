#Build 
FROM node:24-alpine AS builder

RUN npm i -g pnpm@12.3.4

WORKDIR /app

COPY . .

RUN pnpm install --frozen-lockfile

RUN pnpm exec prisma generate 

RUN pnpm build


#RUN 

FROM node:24-alpine AS runner

RUN npm i -g pnpm@12.3.4

WORKDIR /app

COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./
COPY prisma.config.ts ./prisma.config.ts
COPY prisma ./prisma 

RUN pnpm install --frozen-lockfile

COPY --from=builder /app/dist ./dist


EXPOSE 3000

CMD ["sh", "-c", "pnpm exec prisma migrate deploy && node dist/server.js"]


