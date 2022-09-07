## Kubernetes Dashboard

Update:
 dashboard url: ocalhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

 To install k8 dashboard use this command:

  ```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.2.0/aio/deploy/recommended.yaml


```
Verification

```
kubectl get all -n kubernetes-dashboard
```



### create an admin user account
```
kubectl apply -f admin-service-account.yaml
```

### access the dashboard
* get a security token
```kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep eks-course-admin | awk '{print $1}')
```
record the output of ```token:```

* start kube proxy via ```kubectl proxy```

* open browser at `http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#!/login`

and choose _token_ as login method, where you have to provide the token you recorded two steps before

