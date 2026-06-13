# kube-hunter External Scan Findings

## Target
192.168.56.10

## Open Services Found

- API Server (6443)
- Kubelet API (10250)
- Etcd (2379)

## Vulnerabilities

### KHV002 - Kubernetes Version Disclosure

Description:
The Kubernetes API server exposes version information through the /version endpoint.

Evidence:
v1.29.15

Risk:
Low

Recommendation:
Restrict API server exposure using firewalls and network policies.
