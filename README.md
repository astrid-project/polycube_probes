# NTP Probe artifacts

These artifacts can be used to create the nine nodes (POD) for NTP probing.


## Description

For every node there are three files:
* pod: create the pod and its containers (polycube, lcp, logstash and scheduler). For example "node-0.yaml"
* configmap: load configmap of the pod. For example "node-0-configmap.yaml"
* service: description of service for specific pod. For example "node-0-service.yaml"


## How to configure

It is possible to configure each node modifying environment variables in artifact file of the specific pod, for example for "node 0", change the file "node-0.yaml".

An important value is the "POLLING_TIME", that is the value used by the "scheduler" to launch the reading act on the probe.

By default this value is set to 3 seconds ("3s").


## How to use

Warning: always load configmap before launch the pod creation

Launch the commands:
```
kubectl apply -f <ARTIFACT-FILE>.yaml
```

For example if you wanto to load the configmap of the "node 0":
```
kubectl apply -f node-0-configmap.yaml
```

To create the "node 0" pod:
```
kubectl apply -f node-0.yaml
```

To create the service of the "pod 0":
```
kubectl apply -f node-0-service.yaml
```

