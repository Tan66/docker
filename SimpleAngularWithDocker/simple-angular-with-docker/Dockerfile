# build stage

FROM node:alpine AS app-build
WORKDIR /app
COPY . .
RUN npm ci && \
    npm run build

# run server stage
FROM nginx:alpine
COPY --from=app-build /app/dist/simple-angular-with-docker /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 4000
