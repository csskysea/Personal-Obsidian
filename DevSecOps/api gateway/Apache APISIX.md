# Introduction

## Why APISIX?

1. Provide dashboard for configure, it's super easy for route config.
2. rich plugin for kinds of features.
3. hot load.

***



# Installation

- use `helm` to install
```shell
helm repo add apisix https://charts.apiseven.com
helm repo update
helm install apisix apisix/apisix --create-namespace  --namespace apisix
```
