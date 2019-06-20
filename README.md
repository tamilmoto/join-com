# Helm chart for acceleration calculator of an object

This repository contains the Docker file, Code and helm chart file for each micro services.

### Installing the Chart
To install the chart with the release name my-release:

```sh
$ helm install --name my-release-a helm-acceleration-a
$ helm install --name my-release-dv helm-acceleration-dv
$ helm install --name my-release-calc helm-acceleration-calc
```
These commands deploys microservices for acceleration calculator on the Kubernetes cluster in the default namespace.

### Uninstalling the Chart
To uninstall/delete the my-release deployment:

```sh
$ helm delete my-release-a
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

### Services

- acceleration-dv calculates 𝚫v=vf-vi
```sh
curl http://127.0.0.1:3001/dv?vf=200&vi=5
{"dv":195}
```
- acceleration-a calculates a=𝚫v/t
```sh
curl http://127.0.0.1:3002/a?dv=200&t=5
{"a":40}
```
- acceleration-calc coordinates request to acceleration-dv and acceleration-a services
```sh
curl http://127.0.0.1:3000/calc?vf=200&vi=5&t=123
{"a":1.5853658536585367}
```
