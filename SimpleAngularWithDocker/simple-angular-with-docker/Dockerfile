# build stage

FROM node:alpine AS app-build
WORKDIR /app
COPY . .
RUN npm ci && \
    npm run build

# run server stage
FROM nginx:alpine
COPY --from=app-build /app/dist/simple-angular-with-docker /usr/share/nginx/html
EXPOSE 80
