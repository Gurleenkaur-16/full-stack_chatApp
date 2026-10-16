FROM node:20-alpine as builder

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm ci --omit=dev

COPY . .

#stage2
FROM node:20-alpine

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY --from=builder /app ./

ENV NODE_ENV=production

EXPOSE 5001

USER appuser

CMD ["npm","start"]
