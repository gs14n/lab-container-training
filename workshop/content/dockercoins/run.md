Now we have a good idea of what the application looks like we can run it on Kubernetes.

1. Deploy `redis`:

```execute
kubectl create deployment redis --image=redis
```

2. Deploy everything else:

```execute
kubectl create deployment hasher --image=dockercoins/hasher:v0.1
kubectl create deployment rng --image=dockercoins/rng:v0.1
kubectl create deployment webui --image=dockercoins/webui:v0.1
kubectl create deployment worker --image=dockercoins/worker:v0.1
```

3. Check if `rng` is working:

```execute
kubectl logs deploy/rng
```

4. Check if `worker` is working:

```execute
kubectl logs deploy/webui
```

It appears that `rng` is working but `webui` is not.
