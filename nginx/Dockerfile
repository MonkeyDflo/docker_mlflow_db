FROM nginx:1.17.6
# Remove default Nginx config
RUN rm /etc/nginx/nginx.conf

#Install apache2-utils
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      apache2-utils \
 && rm -rf /var/lib/apt/lists/* \
 && htpasswd -c /etc/nginx/.htpasswd admin
RUN htpasswd -b /etc/nginx/.htpasswd admin ${MLFLOW_ADMIN_PASSWORD}

# Copy the modified Nginx conf
COPY nginx.conf /etc/nginx
# Copy proxy config
COPY mlflow.conf /etc/nginx/sites-enabled/
