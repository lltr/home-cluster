
<div align="center">

  <img src="https://camo.githubusercontent.com/5b298bf6b0596795602bd771c5bddbb963e83e0f/68747470733a2f2f692e696d6775722e636f6d2f7031527a586a512e706e67" align="center" width="144px" height="144px"/>

  ### My Talos cluster

</div>

---

## Overview

This repository *is* my home Kubernetes cluster in a declarative state. [Flux](https://github.com/fluxcd/flux2) watches my [cluster](https://github.com/lltr/home-cluster) directory and makes the changes to my cluster based on the YAML manifests.

Feel free to open a [Github issue](https://github.com/lltr/home-cluster/issues/new/choose) if you have any questions.

This repository is built off the [onedr0p/flux-cluster-template](https://github.com/onedr0p/flux-cluster-template) repository.

---

## 🎨 Cluster components

### Cluster management

- [Talos](https://www.talos.dev): Using bare talosctl, talhelper * *soon*!
- [fluxcd](https://fluxcd.io/): Sync kubernetes cluster with this repository.
- [SOPS](https://toolkit.fluxcd.io/guides/mozilla-sops/): Encrypts secrets which is safe to store - even to a public repository.
- [yq v4](https://github.com/mikefarah/yq): Command tool
- [go-task](https://github.com/go-task/task): Custom helper commands

### Networking

- [metallb](https://github.com/metallb/metallb): Bare-metal load balancer.
- [cert-manager](https://cert-manager.io/docs/): Configured to create TLS certs for all ingress services automatically using LetsEncrypt.
- [ingress-nginx](https://kubernetes.github.io/ingress-nginx/): Ingress controller for services.
- [external-dns](https://github.com/kubernetes-sigs/external-dns): External DNS manager for all ingress.

### Storage

- [rook-ceph](https://rook.io): Cloud native distributed block storage for Kubernetes
- [nfs-subdir-external-provisioner](https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner): Provides persistent volumes from NFS server. * *soon*

### Metrics

- [Prometheus](https://prometheus.io/): Scraping metrics from the entire cluster
- [Grafana](https://grafana.com): Visualization for the metrics from Prometheus

---

## 💻 Systems

| System              | RAM  | OS Disk         | Storage                      |
| ------------------- | ---- | --------------- | ---------------------------- |
| 3x Intel 12NUCWSHi5 | 64GB | 500GB 870EVO    | 2TB 970EVO+ NVMe (rook-ceph) |
| 1x Intel 11NUCPAHi3 | 32GB | 2TB 980PRO NVMe |                              |

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

