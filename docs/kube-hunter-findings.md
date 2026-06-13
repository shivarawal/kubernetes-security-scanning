# Kube-Hunter Internal Security Assessment

## Project

Automated Kubernetes Security Scanning with kube-bench and kube-hunter

## Scan Date

13 June 2026

## Scan Mode

Pod Mode (Internal Threat Simulation)

## Objective

Evaluate the Kubernetes cluster from the perspective of a compromised pod and identify potential security weaknesses.

## Findings

### 1. CAP_NET_RAW Enabled

Severity: Medium

Description:
Containers have the NET_RAW capability enabled, allowing raw packet generation and network reconnaissance.

Recommendation:
Drop NET_RAW capability using SecurityContext.

Example:

```yaml
securityContext:
  capabilities:
    drop:
      - NET_RAW
```

---

### 2. Read Access to Service Account Token

Severity: Medium–High

Description:
Pods have access to service account tokens mounted by default.

Risk:
Compromised pods may interact with Kubernetes API depending on RBAC permissions.

Recommendation:

```yaml
automountServiceAccountToken: false
```

---

### 3. Access to Pod Secrets

Severity: Medium–High

Description:
Applications can access mounted Kubernetes Secrets.

Risk:
Exposure of credentials, certificates, and API keys.

Recommendation:

* Use least privilege RBAC
* Avoid mounting unnecessary secrets
* Consider external secret management solutions such as HashiCorp Vault.

## Conclusion

The cluster demonstrated a generally secure posture with no critical externally exploitable vulnerabilities discovered during pod-mode assessment. However, several hardening opportunities exist around capability management, service account usage, and secret handling.

Regular kube-hunter assessments should be incorporated into cluster security operations.

