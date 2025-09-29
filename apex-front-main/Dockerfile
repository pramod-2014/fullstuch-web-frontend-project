FROM node:18 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Nginx to serve frontend
FROM nginx:alpine

RUN apk update && apk upgrade

# Create non-root user and group for running nginx
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY --from=build /app/dist /usr/share/nginx/html

# Change ownership so appuser can serve files
RUN chown -R appuser:appgroup /usr/share/nginx/html

# Switch to non-root user
USER appuser

# Add HEALTHCHECK
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD wget --no-verbose --spider http://localhost || exit 1

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
