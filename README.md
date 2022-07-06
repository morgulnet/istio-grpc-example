# istio-grpc-example
Simple grpc app  with istio ingress

```
kubectl get svc -n istio-system
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)                                      AGE
istio-egress    ClusterIP      10.96.190.127   <none>        15021/TCP,80/TCP,443/TCP                     28d
istio-gateway   LoadBalancer   10.96.205.158   10.1.30.36    15021:31903/TCP,80:31853/TCP,443:30667/TCP   33d
istiod          ClusterIP      10.96.224.29    <none>        15010/TCP,15012/TCP,443/TCP,15014/TCP        33d
```

grpcurl -plaintext 10.1.30.36:443 list
```
grpc.reflection.v1alpha.ServerReflection
yages.Echo
```

grpcurl -plaintext 10.1.30.36:443 describe
```
grpc.reflection.v1alpha.ServerReflection is a service:
service ServerReflection {
  rpc ServerReflectionInfo ( stream .grpc.reflection.v1alpha.ServerReflectionRequest ) returns ( stream .grpc.reflection.v1alpha.ServerReflectionResponse );
}
yages.Echo is a service:
service Echo {
  rpc Ping ( .yages.Empty ) returns ( .yages.Content );
  rpc Reverse ( .yages.Content ) returns ( .yages.Content );
}
``` 

## only for tests

```
 Gateway 
 hosts:
      - "*"

grpc uses 443 port
```