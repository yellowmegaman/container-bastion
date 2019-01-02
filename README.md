# bstn [![Build Status](https://cloud.drone.io/api/badges/yellowmegaman/bstn/status.svg)](https://cloud.drone.io/yellowmegaman/bstn)

Docker image based on alpine with openssh-client and [Glider](https://github.com/nadoo/glider)

Example usage:

##### Start the tunnel
```
 docker run --rm -ti --net=host yellowmegaman/bastion ash -c 'ssh -o StrictHostKeyChecking=no -qTnN -D 0.0.0.0:8888 user@host -p sshport'
```

##### Start glider http->socks5 proxy
```
docker run --rm -ti --net=host yellowmegaman/bastion ash -c 'glider -listen http://:8384 -forward socks5://127.0.0.1:8888 -verbose'
```

##### Test
```
curl -s ifconfig.co
export http_proxy=http://localhost:8384
curl -s ifconfig.co
```
