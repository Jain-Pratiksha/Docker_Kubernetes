# Dockerfile
FROM debian:bullseye

# Install Kerberos KDC, Admin server, and useful tools
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    krb5-kdc \
    krb5-admin-server \
    procps \
    net-tools \
    vim && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy configuration files
COPY krb5.conf /etc/krb5.conf
COPY kdc.conf /etc/krb5kdc/kdc.conf
COPY kadm5.acl /etc/krb5kdc/kadm5.acl

# Initialize Kerberos database (skip if already created)
RUN mkdir -p /var/lib/krb5kdc && \
    echo "admin/admin@EXAMPLE.COM" | kdb5_util create -s -P adminpassword

# Expose KDC and admin ports
EXPOSE 88/udp 749

# Start the KDC and Admin server
# CMD ["/bin/bash", "-c", "krb5kdc && kadmind -nofork"]
CMD ["/bin/bash", "-c", "test -f /var/lib/krb5kdc/principal || echo 'admin/admin@EXAMPLE.COM' | kdb5_util create -s -P adminpassword; krb5kdc && kadmind -nofork"]
