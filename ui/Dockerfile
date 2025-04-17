FROM nginx
COPY ./dynamic-survey-ui/browser/ /usr/share/nginx/html
COPY wait-for-it.sh /usr/local/bin/wait-for-it.sh
RUN chmod +x /usr/local/bin/wait-for-it.sh

RUN echo "server { \
    listen 80; \
    server_name localhost; \
    root /usr/share/nginx/html; \
    index index.html index.htm; \
    location / { \
        try_files \$uri \$uri/ /index.html; \
    } \
    location /api/ { \
        proxy_pass http://java-app:8080/; \
        proxy_set_header Host \$host; \
        proxy_set_header X-Real-IP \$remote_addr; \
        proxy_set_header X-Forwarded-For \$proxy_add_x_forwarded_for; \
        proxy_set_header X-Forwarded-Proto \$scheme; \
    } \
    error_page 404 /index.html; \
    location = /index.html { \
        root /usr/share/nginx/html; \
    } \
}" > /etc/nginx/conf.d/default.conf

EXPOSE 80
ENTRYPOINT ["/bin/sh", "-c", "/usr/local/bin/wait-for-it.sh -t 900 java-app:8080 && nginx -g 'daemon off;'"]