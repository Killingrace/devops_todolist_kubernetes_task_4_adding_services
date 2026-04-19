# Todoapp

simple todo app

## Installation

to install app firstly apply all manifests.

```bash
kubectl apply -f .infrastructure/namespace.yml && \
kubectl apply -f .infrastructure/todoapp-pod.yml && \
kubectl apply -f .infrastructure/clusterIp.yml && \
kubectl apply -f .infrastructure/nodePort.yml && \
kubectl apply -f .infrastructure/busybox.yml
```

## Testing

1. Test ClusterIp with ```port-forward```

    ```bash
    kubectl port-forward svc/todoapp-clusterip -n todoapp 8080:80
    ```

    Now you can access nodes via [this link](http://127.0.0.1:8080/)

1. To test ClusterIp with busybox.

    ```bash
    kubectl exec busybox -n todoapp -- curl http://todoapp-clusterip.todoapp.svc.cluster.local
    ```

1. To test NodePort service follow [app link](http://127.0.0.1:30007/)