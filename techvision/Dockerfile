FROM nginx:latest

# Remove config padrão
RUN rm /etc/nginx/conf.d/default.conf

# Copia configuração personalizada
COPY nginx/default.conf /etc/nginx/conf.d/

# Copia os sites
COPY blog/ /usr/share/nginx/html/blog/
COPY docs/ /usr/share/nginx/html/docs/