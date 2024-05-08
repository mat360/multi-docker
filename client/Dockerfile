FROM node:16-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
# construit l'application dans un répertoire nommé par défaut 'build'
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# A partir du stage 'builder', copie du répertoire /app/build vers nginx
COPY --from=builder /app/build /usr/share/nginx/html