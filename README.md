
<div align="center">

  <img src="https://camo.githubusercontent.com/5b298bf6b0596795602bd771c5bddbb963e83e0f/68747470733a2f2f692e696d6775722e636f6d2f7031527a586a512e706e67" align="center" width="144px" height="144px"/>

  ### My Talos Kubernetes cluster

</div>

---

## Overview

This is a mono repository for my home infrastructure and Kubernetes cluster. [Flux](https://github.com/fluxcd/flux2) watches my [cluster](https://github.com/lltr/home-cluster) directory and makes the changes to my cluster based on the YAML manifests.

This repository is built off the [onedr0p/flux-cluster-template](https://github.com/onedr0p/flux-cluster-template) repository.

---

## 🎨 Cluster components

### Cluster management

- [Talos](https://www.talos.dev): Using bare talosctl, talhelper * *soon*!
- [fluxcd](https://fluxcd.io/): Sync kubernetes cluster with this repository.
- [SOPS](https://toolkit.fluxcd.io/guides/mozilla-sops/): Encrypts secrets which is safe to store - even to a public repository.
- [yq v4](https://github.com/mikefarah/yq): Command tool
- [go-task](https://github.com/go-task/task): Custom helper commands

### Core components

- [metallb](https://github.com/metallb/metallb): Bare-metal load balancer.
- [cert-manager](https://cert-manager.io/docs/): Configured to create TLS certs for all ingress services automatically using LetsEncrypt.
- [ingress-nginx](https://kubernetes.github.io/ingress-nginx/): Ingress controller for services.
- [external-dns](https://github.com/kubernetes-sigs/external-dns): External DNS manager for all ingress.
- [rook-ceph](https://rook.io): Cloud native distributed block storage for Kubernetes
- [Prometheus](https://prometheus.io/): Scraping metrics from the entire cluster
- [Grafana](https://grafana.com): Visualization for the metrics from Prometheus

---

## 📂 Repository structure

The Git repository contains the following directories under `kubernetes` and are ordered below by how Flux will apply them.

```sh
📁 kubernetes      # Kubernetes cluster defined as code
├─📁 bootstrap     # Flux installation
├─📁 flux          # Main Flux configuration of repository
├─📁 core          # Core applications deployed into the cluster grouped by namespace
└─📁 apps          # Apps deployed after core into the cluster grouped by namespace
```

---

## 🤝 Thanks

* [k8s-at-home Discord](https://discord.gg/k8s-at-home)
* [k8s-at-home-search](https://nanne.dev/k8s-at-home-search/)
