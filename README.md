# DevOps Engineer Challenge Solution

![pods](https://github.com/m-bassam94/devops-challenge/blob/251deb848db28722e1c09e503b9d42b8c38a9631/pods.JPG)

![services](https://github.com/m-bassam94/devops-challenge/blob/251deb848db28722e1c09e503b9d42b8c38a9631/services.JPG)

![PDB-minAvailable](https://github.com/m-bassam94/devops-challenge/blob/251deb848db28722e1c09e503b9d42b8c38a9631/PDB-minAvailable.JPG)


## Technologies Used

- [Docker 20.10.8](https://docker.com/)
- [Kubernetes 1.21](https://kubernetes.io/)
- [Helm v3.6.3](https://helm.sh/)
- [Kind](https://kind.sigs.k8s.io/)
- [Lens](https://k8slens.dev/)


## Build and deploy
```bash
docker build acceleration-a/ -t acceleration-a
```
```bash
docker build acceleration-dv/ -t acceleration-dv
```
```bash
docker build acceleration-calc/ -t acceleration-calc
```
- push to registry or Load the images to a local registry if using kind or minikube
```bash
helm install join acceleration-full-app
```
```bash
export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services acceleration-full-app)`
```
```bash
export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
```
```bash
curl "http://$NODE_IP:$NODE_PORT/calc?vf=200&vi=5&t=123"
```

