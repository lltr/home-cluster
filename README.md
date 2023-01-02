
<div align="center">

  <img src="https://user-images.githubusercontent.com/12874842/209884137-923943a4-16ef-4fe1-ab7f-aaa60e957466.png" width="144px" height="144px"/>

  ### My Talos Kubernetes cluster

  [![External-Status](https://img.shields.io/uptimerobot/status/m793353196-e4e90f5680b8c3200714f8f6?label=EXTERNAL%20STATUS&style=for-the-badge)](https://uptimerobot.com)

</div>

---

## Overview

This is a mono repository for my home Kubernetes cluster. [Flux](https://github.com/fluxcd/flux2) watches the cluster directory and makes changes to the cluster based on the YAML manifests.

This repository is built off the [onedr0p/flux-cluster-template](https://github.com/onedr0p/flux-cluster-template) repository.

---

## 🎨 Cluster components

### Cluster management

- [Talos](https://www.talos.dev): Using bare talosctl
- [fluxcd](https://fluxcd.io/): Sync kubernetes cluster with this repository.
- [SOPS](https://toolkit.fluxcd.io/guides/mozilla-sops/): Encrypts secrets which is safe to store - even to a public repository.
- [yq v4](https://github.com/mikefarah/yq): Command tool
- [go-task](https://github.com/go-task/task): Custom helper commands

### Core components

- [Flannel](https://github.com/flannel-io/flannel): Container Network Interface for networking between pods.
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
├─📁 apps          # Apps deployed after core into the cluster grouped by namespace
└─📁 archive       # Archived applications
```

---

## 🤝 Thanks

[k8s-at-home](https://discord.gg/k8s-at-home), [k8s-at-home-search](https://nanne.dev/k8s-at-home-search/)
