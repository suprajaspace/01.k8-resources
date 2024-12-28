
pod to pod communication possible

here pod-config pod IP address accessed into annotations pod

so pod to pod communication possible


54.152.103.126 | 172.31.88.42 | t3.micro | https://github.com/suprajaspace/01.k8-resources.git
[ ec2-user@ip-172-31-88-42 ~/01.k8-resources ]$ kubectl get pods
NAME              READY   STATUS    RESTARTS      AGE
annotations       1/1     Running   0             68m
environment       1/1     Running   0             65m
labels            1/1     Running   0             71m
limits            1/1     Running   0             62m
multi-container   2/2     Running   4 (10m ago)   76m
nginx             1/1     Running   0             89m
pod-config        1/1     Running   0             24m
pod-secret        1/1     Running   0             14m

54.152.103.126 | 172.31.88.42 | t3.micro | https://github.com/suprajaspace/01.k8-resources.git
[ ec2-user@ip-172-31-88-42 ~/01.k8-resources ]$ kubectl describe pod pod-config
Name:             pod-config
Namespace:        default
Priority:         0
Service Account:  default
Node:             ip-192-168-48-125.ec2.internal/192.168.48.125
Start Time:       Sat, 28 Dec 2024 04:54:14 +0000
Labels:           <none>
Annotations:      <none>
Status:           Running
IP:               192.168.55.23
IPs:
  IP:  192.168.55.23
Containers:
  nginx:
    Container ID:   containerd://5e698a8e379b02895c89fc3bc75454d760e83d83678ab08e6ee02e9d9f4df97c
    Image:          nginx
    Image ID:       docker.io/library/nginx@sha256:42e917aaa1b5bb40dd0f6f7f4f857490ac7747d7ef73b391c774a41a8b994f15
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Sat, 28 Dec 2024 04:54:15 +0000
    Ready:          True
    Restart Count:  0
    Environment Variables from:
      nginx-config  ConfigMap  Optional: false
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-hqp76 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       True
  ContainersReady             True
  PodScheduled                True
Volumes:
  kube-api-access-hqp76:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  24m   default-scheduler  Successfully assigned default/pod-config to ip-192-168-48-125.ec2.internal
  Normal  Pulling    24m   kubelet            Pulling image "nginx"
  Normal  Pulled     24m   kubelet            Successfully pulled image "nginx" in 114ms (114ms including waiting). Image size: 72099410 bytes.
  Normal  Created    24m   kubelet            Created container nginx
  Normal  Started    24m   kubelet            Started container nginx


54.152.103.126 | 172.31.88.42 | t3.micro | https://github.com/suprajaspace/01.k8-resources.git
[ ec2-user@ip-172-31-88-42 ~/01.k8-resources ]$ kubectl exec -it annotations -- bash
root@annotations:/# curl 192.168.55.23
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@annotations:/#
