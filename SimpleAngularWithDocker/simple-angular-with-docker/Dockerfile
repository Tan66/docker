# with context path

# build stage

FROM node:alpine AS app-build
WORKDIR /app
COPY . .
RUN npm ci && \
    npm run build --base-href=/ui/

# for nx
# RUN npm install -g nx && nx run app:build:development --base-href=/path/ --deploy-url=/ui/

# run server stage
FROM nginx
COPY --from=app-build /app/dist/simple-angular-with-docker /usr/share/nginx/html/ui
COPY nginx2.conf /etc/nginx/nginx.conf
EXPOSE 4200
