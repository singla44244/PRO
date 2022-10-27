

1. sudo snap install microk8s --classic
2. sudo usermod -a -G microk8s xcad
3. microk8s enable dns  (always recommended)
4. microk8s enable community  (allows community addons)

https://microk8s.io/docs/addons

https://microk8s.io/docs/addon-portainer


Testing:
1. microk8s enable portainer
2. microk8s enable traefik
3. microk8s enable cert-manager



microk8s kubectl get all --all-namespaces

