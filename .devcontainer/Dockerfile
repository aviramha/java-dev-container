FROM ghcr.io/aviramha/java-dev-container:07c91a1018f4e7c99f5561988912712ed51ac33d

COPY netskope.crt /netskope.crt

USER root
# Fix root CA
RUN openssl x509 -inform der -in /netskope.crt -out /usr/local/share/ca-certificates/netskope.pem
RUN update-ca-certificates
RUN echo '\n' >> /opt/az/lib/python3.11/site-packages/certifi/cacert.pem && cat /usr/local/share/ca-certificates/netskope.pem >> /opt/az/lib/python3.11/site-packages/certifi/cacert.pem

USER vscode

