Ansible Role: kube-lego for Kubernetes
======================================

Ansible role to install [kube-lego](https://github.com/jetstack/kube-lego) on
Kubernetes, allowing to automatically request certificates for Kubernetes
Ingress resources from Let's Encrypt.

Role Variables
--------------

```yaml
# Namespace
kubernetes_kube_lego_namespace: "kube-lego"
# App name (used as selector)
kubernetes_kube_lego_app: "kube-lego"
# Deployment name
kubernetes_kube_lego_deployment: "kube-lego-deployment"
# Configmap name
kubernetes_kube_lego_configmap: "kube-lego"
# Service account
kubernetes_kube_lego_service_account: "kube-lego"

# Number of replicas
kubernetes_kube_lego_replicas: 1
kubernetes_kube_lego_revision_history: 1

# Node selector
kubernetes_kube_lego_node_selector: {}

kubernetes_kube_lego_resources:
  limits:
    cpu: "10m"
    memory: "20Mi"
  requests:
    cpu: "10m"
    memory: "20Mi"

### kube-lego options ###

# Register email
kubernetes_kube_lego_email: "cert@example.com"

# Acme API URL
kubernetes_kube_lego_api_url: "https://acme-v01.api.letsencrypt.org/directory"

# Default ingress class to use
kubernetes_kube_lego_default_ingress_class: "nginx"
```

Dependencies
------------

Kubectl needs to be installed on the host targeted by the role.


Example Playbook
----------------

```yaml

- hosts: kube-master
  run_once: true
  vars:
    kubernetes_kube_lego_email: "mail@example.com"
  roles:
    - role: Anthony25.kubernetes-kube-lego
```

Use `run_once` to run the role on only one available master in the cluster.

License
-------

Tool under the BSD license. Do not hesitate to report bugs, ask me some
questions or do some pull request if you want to!
