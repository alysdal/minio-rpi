# Todo
* Do SSL of remote server and not in minio, as it is already in an ssh tunnel.
* nginx proxy manager docker container on remote server with a proxy to the ssh tunnel port of minio.
  * Minio (Exposed): 9000->443 minio.docker01.letsmakeit.dk
  * Admin (via SSH tunnel): 9001->9001 via ssh local tunnel from client

# Tunnel
Location machine
ssh -N -R \*:443:127.0.0.1:8001 root@207.154.249.247

openssl req -new -x509 -nodes -days 730 -keyout ./certs/private.key -out ./certs/public.crt -config openssl.conf

Relay machine

Make sure firewall is open 

ufw allow 443

sshd config must allow: GatewayPorts clientspecified

