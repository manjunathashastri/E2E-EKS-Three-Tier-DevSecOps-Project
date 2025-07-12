# Stage 1 - Build
FROM node:14 AS backend
WORKDIR /usr/src/app

# Copy backend code relative to project root (build context = '.')
COPY app/backend/. .

RUN npm install

# Stage 2 - Runtime
FROM node:14.0.0-alpine
WORKDIR /app

COPY --from=backend /usr/src/app/node_modules ./node_modules
COPY --from=backend /usr/src/app/modules ./modules
COPY --from=backend /usr/src/app/routes ./routes
COPY --from=backend /usr/src/app/db.js .
COPY --from=backend /usr/src/app/index.js .

CMD ["node", "index.js"]
