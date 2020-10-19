## Lab 11. Create a two container pod using YAML
___

* create a pod with two containers via the following code
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: podwith2containers
spec:
      containers:
      - name: busyboxcontainer
        image: busybox
        command: ['sh', '-c', 'echo "Hello, Kubernetes!" && sleep 3600']

      - name: redis
        image: redis
```

* run some pod related command to inspect pod information

```
kubectl get pod
```
```
kubectl describe pod podwith2containers
```
```
kubectl exec -it podwith2containers sh
```
did you get an error message trying to run the interactive with a pod? what was the issue?

it is because, when there are more than one container in a pod, you need -c to specify which container you want to run into, or you will run into the default (first) container in the pod.
```
kubectl exec -it podwith2containers -c redis sh
```