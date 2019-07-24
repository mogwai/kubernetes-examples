# Concepts

#### Pods

A pod is a wrapper for container that will sit in them.

Deployment:

A deployment declaration in kubernetes allows you to do app deployments and updates

Do define a simple pod: 

```
apiVersion: v1
kind: Pod
metadata:
  name: nodehelloworld.example.com
  labels:
    app: helloworld
spec:
  containers:
  - name: k8s-demo
    image: wardviaene/k8s-demo
    ports:
    - name: nodejs-port
      containerPort: 3000
```

Creating a Replication Controll will ensure that there is always a certain number of pods

You can do this though yml:

```
apiVersion: v1
kind: ReplicationController
metadata:
  name: helloworld-controller
spec:
  replicas: 2
  selector:
    app: helloworld
  template:
    metadata:
      labels:
        app: helloworld
    spec:
      containers:
      - name: k8s-demo
        image: wardviaene/k8s-demo
        ports:
        - name: nodejs-port
          containerPort: 3000
```

Or with the command 

`kubectl scale --replicas=4 rc/helloworld-controller`

