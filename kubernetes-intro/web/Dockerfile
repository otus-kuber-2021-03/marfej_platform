FROM nginx:latest
WORKDIR /app
COPY /nginx.conf /etc/nginx/nginx.conf
COPY /app /app
EXPOSE 8000
RUN useradd -r -u 1001 webapp && \
    chown -R webapp /app


