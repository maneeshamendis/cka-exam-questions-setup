openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout tls.key -out tls.crt \
  -subj "/CN=localhost/O=test"

kubectl create secret tls nginx-ssl \
  --cert=tls.crt \
  --key=tls.key \
  -n nginx-static