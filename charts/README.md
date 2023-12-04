 
# Create Namespace and Install:


```
kubectl create namespace emissary && \
kubectl apply -f ./emissary-crds.yaml
 
kubectl wait --timeout=90s --for=condition=available deployment emissary-apiext -n emissary-system

cd ./emissary-ingress
helm install emissary-ingress --namespace emissary . && \
kubectl -n emissary wait --for condition=available --timeout=90s deploy -lapp.kubernetes.io/instance=emissary-ingress
```
