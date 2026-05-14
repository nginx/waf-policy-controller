
[![Project Status: Concept – Minimal or no implementation has been done yet, or the repository is only intended to be a limited example, demo, or proof-of-concept.](https://www.repostatus.org/badges/latest/concept.svg)](https://www.repostatus.org/#concept)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/nginx/waf-policy-controller/badge)](https://securityscorecards.dev/viewer/?uri=github.com/nginx/waf-policy-controller)
[![Community Support](https://badgen.net/badge/support/community/cyan?icon=awesome)](/SUPPORT.md) <!-- [![Commercial Support](https://badgen.net/badge/support/commercial/cyan?icon=awesome)](<Insert URL>) -->
[![Community Forum](https://img.shields.io/badge/community-forum-009639?logo=discourse&link=https%3A%2F%2Fcommunity.nginx.org)](https://community.nginx.org)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/license/apache-2-0)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](/CODE_OF_CONDUCT.md)

# WAF Policy Controller

This repository contains deployment artifacts for the F5 WAF Policy Lifecycle Management system.

## Repository Structure

```
├── manifests/          # Kubernetes deployment manifests
│   ├── 1-deploy-crds.yaml
│   ├── 2-deploy-rbac-services.yaml
│   ├── 3-deploy-seaweedfs-operator.yaml
│   ├── 4-deploy-seaweedfs.yaml
│   └── 5-deploy-main.yaml
├── api/                # API type reference documentation
│   └── f5-waf-policy-lifecycle-management-api.md
└── crds/               # Custom Resource Definitions
    ├── appprotect.f5.com_aplogconfs.yaml
    ├── appprotect.f5.com_appolicies.yaml
    ├── appprotect.f5.com_apsignatures.yaml
    ├── appprotect.f5.com_apusersigs.yaml
    └── seaweed.seaweedfs.com_seaweeds.yaml
```

## Manifests

Kubernetes manifests for deploying the WAF Policy Controller stack. Apply them in order:

1. **1-deploy-crds.yaml** — Custom Resource Definitions
2. **2-deploy-rbac-services.yaml** — RBAC roles, bindings, and services
3. **3-deploy-seaweedfs-operator.yaml** — SeaweedFS operator deployment
4. **4-deploy-seaweedfs.yaml** — SeaweedFS storage deployment
5. **5-deploy-main.yaml** — Main policy controller deployment

## CRDs

Custom Resource Definitions for:

- **APLogConf** (`appprotect.f5.com`) — WAF logging configuration
- **APPolicy** (`appprotect.f5.com`) — WAF security policy
- **APSignatures** (`appprotect.f5.com`) — WAF attack signatures
- **APUserSig** (`appprotect.f5.com`) — WAF user-defined signatures
- **Seaweed** (`seaweed.seaweedfs.com`) — SeaweedFS cluster resource

## API Reference

The API type definitions for the `appprotect.f5.com/v1` group are documented in [`api/f5-waf-policy-lifecycle-management-api.md`](api/f5-waf-policy-lifecycle-management-api.md).

## Contributing

Please see the [contributing guide](/CONTRIBUTING.md) for guidelines on how to best contribute to this project.

## License

[Apache License, Version 2.0](/LICENSE)

&copy; [F5, Inc.](https://www.f5.com/) 2026
