In the `kube-system` namespace, there should be a service named `kube-dns`

This is the internal DNS server that can resolve service names

The default domain name for the service we created is `<namespace>.svc.cluster.local` (unless you deployed to a namespace other than default)

1. Get the IP address of the internal DNS server:

```execute
IP=$(kubectl -n kube-system get svc kube-dns -o json | jq -r ".spec.clusterIP")
```

2. Resolve the cluster IP for the httpenv service:

```execute
kubectl exec shpod -- nslookup httpenv $IP
```

When accessing `httpenv` from another Pod you can use DNS: `httpenv`, `httpenv.<namespace>` or `httpenv.<namespace>.svc.cluster.local`

3. curl the service from its name:

```execute
kubectl exec shpod -- curl -s http://httpenv:8888/ | jq -r .HOSTNAME
```

4. curl the service from its fqdn:

```execute
NS=$(kubectl get svc httpenv -o json | jq -r  '.metadata.namespace')
kubectl exec shpod -- curl -s http://httpenv.$NS.svc.cluster.local:8888/ | \
  jq -r .HOSTNAME
```