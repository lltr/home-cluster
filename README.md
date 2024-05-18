
<div align="center">

  <img src="https://user-images.githubusercontent.com/12874842/209884137-923943a4-16ef-4fe1-ab7f-aaa60e957466.png" width="144px" height="144px"/>

  ### My Talos Kubernetes cluster

</div>

<div align="center">

  [![External-Status-Page](https://img.shields.io/uptimerobot/status/m793353196-e4e90f5680b8c3200714f8f6?style=for-the-badge&label=EXTERNAL%20STATUS)](https://uptimerobot.com)

</div>

<div align="center">

  [![Talos](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.securetunnel.link%2Fquery%3Fformat%3Dendpoint%26metric%3Dtalos_version&style=for-the-badge&logo=talos&logoColor=white&label=%20&color=blue)](https://talos.dev)
  [![Kubernetes](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.securetunnel.link%2Fquery%3Fformat%3Dendpoint%26metric%3Dkubernetes_version&style=for-the-badge&logo=kubernetes&logoColor=white&label=%20&color=blue)](https://talos.dev)

</div>

<div align="center">

  [![Age-Days](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.securetunnel.link%2Fquery%3Fformat%3Dendpoint%26metric%3Dcluster_age_days&style=flat-square&logoColor=white&label=Age)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
  [![Uptime-Days](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.securetunnel.link%2Fquery%3Fformat%3Dendpoint%26metric%3Dcluster_uptime_days&style=flat-square&logoColor=white&label=Uptime)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
  [![Node-Count](https://img.shields.io/endpoint?url=https%3A%2F%2Fkromgo.securetunnel.link%2Fquery%3Fformat%3Dendpoint%26metric%3Dcluster_node_count&style=flat-square&logoColor=white&label=Nodes)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;

</div>

---

## Overview

This is a mono repository for my home Kubernetes cluster. [Flux](https://github.com/fluxcd/flux2) watches the cluster directory and makes changes to the cluster based on the YAML manifests.

---

## 🎨 Cluster components

### Cluster management

- [Talos](https://www.talos.dev): Using bare talosctl
- [fluxcd](https://fluxcd.io/): Sync kubernetes cluster with this repository.
- [SOPS](https://toolkit.fluxcd.io/guides/mozilla-sops/): Encrypts secrets which is safe to store - even to a public repository.
- [go-task](https://github.com/go-task/task): Custom helper commands

### Core components

- [flannel](https://github.com/flannel-io/flannel): Container Network Interface for networking between pods.
- [metallb](https://github.com/metallb/metallb): Bare-metal load balancer.
- [cert-manager](https://cert-manager.io/docs/): Configured to create TLS certs for all ingress services automatically using LetsEncrypt.
- [ingress-nginx](https://kubernetes.github.io/ingress-nginx/): Ingress controller for services.
- [external-dns](https://github.com/kubernetes-sigs/external-dns): External DNS manager for all ingress.
- [rook-ceph](https://rook.io): Cloud native distributed block storage for Kubernetes
- [kube-prometheus-stack](https://prometheus.io/): Scraping metrics from the entire cluster
- [grafana](https://grafana.com): Visualization for the metrics from Prometheus and other datasources
- [external-secrets](https://external-secrets.io/): Integrates external secrets management with OnePassword Connect
- [local-path-provisioner](https://github.com/rancher/local-path-provisioner) - Provision persistent local storage with Kubernetes to avoid write amplification for default soft replicated applications

---

## 📂 Repository structure

The Git repository contains the following directories under `kubernetes` and are ordered below by how Flux will apply them.

```sh
📁 kubernetes      # Kubernetes cluster defined as code
├─📁 bootstrap     # Flux installation
├─📁 flux          # Main Flux configuration of repository
├─📁 core          # Core applications deployed into the cluster grouped by namespace
├─📁 apps          # Apps deployed after core into the cluster grouped by namespace
📁 archive       # Archived Kubernetes application manifests
```

---

## 🤝 Thanks

[k8s-at-home](https://discord.gg/k8s-at-home), [k8s-at-home-search](https://nanne.dev/k8s-at-home-search/)
