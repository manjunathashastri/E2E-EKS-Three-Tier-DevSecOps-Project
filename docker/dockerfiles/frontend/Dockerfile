FROM node:14 AS frontend
WORKDIR /usr/src/app
COPY app/frontend/. .
RUN npm install

FROM node:14.0.0-alpine
WORKDIR /app
COPY --from=frontend /usr/src/app/package*.json ./
COPY --from=frontend /usr/src/app/node_modules ./node_modules
COPY --from=frontend /usr/src/app/public ./public
COPY --from=frontend /usr/src/app/src ./src

# Debugging line: list files to verify they exist in final image
RUN ls -l /app/public
RUN ls -l /app/src

CMD ["npm", "start"]
