# Pull base image.
FROM centos

# Install Nginx.
RUN \
  yum install readline-devel pcre-devel openssl-devel gcc -y
RUN \
  echo "[openresty]" > /etc/yum.repos.d/OpenResty.repo && \
  echo "name=Official OpenResty Repository" >> /etc/yum.repos.d/OpenResty.repo && \
  echo "baseurl=https://copr-be.cloud.fedoraproject.org/results/openresty/openresty/epel-7-x86_64/" >> /etc/yum.repos.d/OpenResty.repo && \
  echo "skip_if_unavailable=True" >> /etc/yum.repos.d/OpenResty.repo && \
  echo "gpgcheck=1" >> /etc/yum.repos.d/OpenResty.repo && \
  echo "gpgkey=https://copr-be.cloud.fedoraproject.org/results/openresty/openresty/pubkey.gpg" >> /etc/yum.repos.d/OpenResty.repo && \
  echo "enabled=1" >> /etc/yum.repos.d/OpenResty.repo && \
  echo "enabled_metadata=1" >> /etc/yum.repos.d/OpenResty.repo && \
  cat /etc/yum.repos.d/OpenResty.repo && \
  yum install openresty -y

# Define mountable directories.
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Define working directory.
WORKDIR /etc/nginx

# Define default command.
CMD ["openresty"]

# Expose ports.
EXPOSE 80
EXPOSE 443
