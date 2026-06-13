# kube-bench Findings

Date: 13 June 2026

## Compliance Score

85%

## Summary

PASS: 62
FAIL: 11
WARN: 51

## Critical Findings

- Audit logging not configured
- Kubelet certificate authority missing
- protect-kernel-defaults disabled
- Profiling enabled on control plane components

## Recommendations

1. Enable Kubernetes audit logging
2. Disable profiling endpoints
3. Configure kubelet CA validation
4. Harden kubelet configuration
