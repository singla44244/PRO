# WIP
WIP

Project Homepage: https://portainer.io

Video: // WIP

---
## Prerequisites

Docker, Kubernetes, Portainer

For further References, how to use **Docker**, **Kubernetes** and **Portainer**, check out my previous videos:
- [How to use Docker and migrate your existing Apps to your Linux Server?](https://youtu.be/y0GGQ2F2tvs)
- [Kubernetes explained simply, and why you should learn it!](https://youtu.be/glFE28QT1HI)
- [Portainer Install Ubuntu tutorial - manage your docker containers](https://youtu.be/ljDI5jykjE8)

---
## Deploy Portainer Agent on Docker

### WIP

```bash
docker run -d \
  -p 9001:9001 \
  --name portainer_agent \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /var/lib/docker/volumes:/var/lib/docker/volumes \
  portainer/agent:2.16.0
```

## Deploy Portainer Agent on Kubernetes

### WIP

```yml
kubectl apply -f https://downloads.portainer.io/ee2-16/portainer-agent-k8s-lb.yaml
```

### WIP

```bash
kubectl delete svc portainer-agent-headless
```

### WIP

```yml
...
spec:
...
  type: ClusterIP
...
``` 

### WIP

```yml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRouteTCP
metadata:
  name: portainer-agnet-ingressroutetcp
  namespace: portainer
spec:
  entryPoints:
  - websecure
  routes:
  - match: HostSNI(`your-hostname-sni`)
    priority: 10
    services:
    - name: portainer-agent
      port: 9001
  tls:
    passthrough: true
```

## Deploy Portainer Edge Agent on Docker

### WIP

open port 8000

```yml
ports:
  ...
  edge:
    expose: true
    exposedPort: 8000
    port: 8800
```

### WIP

portainer ingress needs to be limited to web and websecure

```yml
ingress:
  enabled: true
  annotations:
    traefik.ingress.kubernetes.io/router.entrypoints: web, websecure
  hosts:
  - host: your-hostname-sni
    paths:
    - path: /
  ingressClassName: traefik
  tls:
  - hosts:
    - your-hostname-sni
    secretName: portainer-tls-secret
```

### WIP

add ingress inportainer for edge port

```yml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: portainer-edge-ingress
  namespace: portainer
  annotations:
    traefik.ingress.kubernetes.io/router.entrypoints: edge
spec:
  rules:
  - host: your-hostname-sni
    http:
      paths:
      - backend:
          service:
            name: portainer
            port:
              number: 8000
        path: /
        pathType: Prefix
```

### WIP

- Create new config
- ... WIP
- Copy Command and execute it on the edge server


---
## References

- [WIP](url)
