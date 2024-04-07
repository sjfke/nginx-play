FROM nginx:latest
# COPY ./site-content/index.html /usr/share/nginx/html/index.html
# COPY ./etc/nginx.conf /etc/nginx/
# remove default.conf
# RUN rm -f /etc/nginx/conf.d/default.conf
COPY ./etc/static.conf /etc/nginx/conf.d/default.conf
# COPY ./site-content/* /usr/share/nginx/html/graidememoire/
COPY ./site-content/static/* /usr/share/nginx/html/static/
COPY ./site-content/html/* /usr/share/nginx/html/