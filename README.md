# Awesome-Cloud-Policy-Management

## Top Cloud Policy Management Platforms Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Policy-as-Code, Cloud Guardrails, IaC Security & Runtime Enforcement*

**Last updated: September 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Cloud Policy Management**. These tools help platform and security teams define, enforce, and audit policies across cloud accounts, Kubernetes clusters, and Infrastructure as Code (IaC)—replacing ad-hoc scripts and manual reviews with declarative, version-controlled governance.



**Examples** include Cloud Custodian, Stacklet, CloudQuery, Fugue (Snyk), Snyk IaC, HashiCorp Sentinel, Styra DAS, OPA Gatekeeper, Prisma Cloud Policies, and Azure Policy (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom policy authoring, and transparent enforcement—ideal for platform teams that need full control over their guardrails without per-resource SaaS fees or vendor lock-in.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents



- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Stacklet](https://stacklet.ai/)**

  Commercial platform built by the core creators of Cloud Custodian. Provides fully automated cloud governance with a policy engine spanning **IaC and runtime** in a single language . Features **Terraform Provider for Stacklet** ("Stacklet as Code") enabling declarative management of policy repositories, collections, bindings, and SSO groups . Jun0 AI agent accelerates policy creation and queries. Over **1,500 policies** and **500+ cloud resource types** out of the box . Survey found 62% of organizations report cloud waste mistakes costing **$25,000+/month** .



- **[Fugue (Snyk)](https://www.snyk.io/)**

  Cloud security posture management platform acquired by Snyk (2022). Features a **unified policy engine** that connects cloud posture back to configuration code—**one policy engine for IaC AND runtime** . Security checks embedded in git workflows and CI/CD with automated developer feedback. Goal: "complete journey from code to cloud" .



- **[Snyk IaC](https://snyk.io/product/infrastructure-as-code-security/)**

  IaC security scanning within the Snyk platform. Detects misconfigurations in **Terraform, Kubernetes, CloudFormation, and Azure Resource Manager** templates . Available via **JetBrains IDE plugin** (in-line issue highlighting, severity categorization, free tier) and CLI. Part of Snyk's broader developer-focused security platform covering open source, code, containers, and IaC .



- **[HashiCorp Sentinel](https://www.hashicorp.com/sentinel)**

  Policy-as-code framework embedded in **HCP Terraform and Terraform Enterprise** (paid tiers) . Policy language: **Sentinel** (HashiCorp-proprietary). Enforcement point: **plan-apply gate**. Best for organizations standardized on Terraform . **Important note**: Paid HCP Terraform/Terraform Enterprise tiers also support **OPA**, so being a Terraform shop does not lock you into Sentinel . Sentinel policy sets can be applied at **project level** for app team-level governance .



- **[Styra DAS](https://www.styra.com/)**

  Enterprise-grade **control plane built on top of open-source OPA**, created by Styra . Provides authorization through **policy lifecycle management** across cloud-native ecosystem. Centralized application for managing policy across **Kubernetes, Terraform, microservices, gateways, meshes, and Application Entitlements**. Single policy language: **Rego** . **Self-hosted Styra DAS** available (v0.17.0, June 2025) with OPA upgraded to v1.4.2 . Custom System type works with any OPA-compatible integration point .



- **[Prisma Cloud Policies](https://www.paloaltonetworks.com/prisma/cloud)**

  Policy management within Palo Alto's CNAPP. Provides cloud security posture policies across AWS, Azure, GCP, and Kubernetes with policy-as-code capabilities.



- **[Azure Policy](https://azure.microsoft.com/en-us/products/azure-policy)**

  Native Azure policy service enforcing effects like **audit, deny, deployIfNotExists, and modify** at the resource provider level . Part of the "outer wall" of cloud account controls that "keeps working when the pipeline is skipped" . AWS equivalent: **Service Control Policies (SCPs)** and IAM permission boundaries. GCP equivalent: **Organization Policy Service** .



## Open-Source GitHub Projects



### Cloud Account Governance



- **[Cloud Custodian](https://github.com/cloud-custodian/cloud-custodian)**

  **The foundational open-source cloud governance engine.** CNCF Incubating Project under **Apache 2.0** license . **YAML-based DSL** for defining rules that filter, tag, and apply actions to cloud resources. Supports **AWS, Azure, and GCP** (Kubernetes, Tencent Cloud, OpenStack in beta) . **Real-time compliance**: natively integrates with cloud provider control planes and remediates in real-time . **Cost management**: off-hours scheduling, garbage collection of unused resources, utilization-based tagging . **Terraform integration** (Alpha) for "Governance as Code" from the start . Runs locally, on instance, or **serverless in AWS Lambda** . Powers Stacklet's commercial platform .



### Kubernetes Admission Control



- **[Open Policy Agent (OPA)](https://github.com/open-policy-agent/opa)**

  **CNCF graduated (January 2021) general-purpose policy engine** . **Rego** policy language for reasoning about structured documents. Can be embedded anywhere—Kubernetes admission, CI/CD, APIs, gateways, and more . **OPA Gatekeeper** wraps OPA in a Kubernetes webhook, reusing Rego skills . One policy language across everything: IaC, Kubernetes, APIs, CI .



- **[Kyverno](https://github.com/kyverno/kyverno)**

  **CNCF graduated Kubernetes-native policy engine** . Uses **YAML** policies (no Rego required). Enforcement: **validate, mutate, generate, delete, image-validate**. **Kyverno 1.16** (November 2025) introduces **CEL policy types** (beta) with namespaced variants for multi-tenancy, fine-grained **image-based exceptions**, and comprehensive **native observability** with Prometheus histograms and Kubernetes events . **Kyverno SDK** debuting for ecosystem integrations . Best for Kubernetes teams who don't want to learn Rego .



- **[Kubewarden](https://github.com/kubewarden)**

  **CNCF project** using **WebAssembly (WASM)** for Kubernetes admission policies . Policies can be written in **Rego, Rust, Go, and more**, compiled to portable WASM modules. Unique for policy portability across environments .



- **[Kubernetes ValidatingAdmissionPolicy](https://kubernetes.io/docs/reference/access-authn-authz/validating-admission-policy/)**

  **In-tree Kubernetes admission policy using CEL**, GA since **v1.30** . Runs in-process in the API server—**no external webhook dependency** and no failure point . Best for simple field-level rules where installing an external engine is unnecessary .



### IaC & Configuration Policy



- **[Conftest](https://github.com/open-policy-agent/conftest)**

  Open-source tool for testing **configuration files (YAML/JSON/HCL) against Rego policies** . Enforcement point: **PR / CI**. Ideal for pre-commit and CI pipeline policy testing .



- **[Checkov](https://github.com/bridgecrewio/checkov)**

  **Open-source static analysis tool for Infrastructure as Code** with **750+ built-in policies** . Language: **Python / YAML checks**. Scope: **Terraform, CloudFormation, Kubernetes, Helm, ARM** . **Deeper Terraform graph analysis** than alternatives. Available as **JetBrains IDE plugin** with real-time scan results and inline fix suggestions . **AWS CDK validator plugin** available .



- **[Trivy](https://github.com/aquasecurity/trivy)**

  **Open-source (Aqua-backed) comprehensive scanner** . Language: **Rego (built-in checks)**. Scope: **Images, IaC, secrets, SBOM**. Enforcement: **PR / CI / registry** . Adds container image, filesystem, secret, license, and SBOM scanning in one binary . Many teams run **Checkov for Terraform depth** and **Trivy for images** .



- **[Pulumi CrossGuard](https://github.com/pulumi/crossguard)**

  **Open-source (Pulumi) policy-as-code framework** . Languages: **TypeScript, JavaScript, Python, Rego**. Scope: **Pulumi programs**. Enforcement: **preview and up** . Best for teams using Pulumi .



### Cloud Asset Inventory & Posture



- **[CloudQuery](https://github.com/cloudquery/cloudquery)**

  **Open-source data movement framework** for cloud asset inventory and CSPM . Syncs data from any source to any destination. **First-class support for AWS, GCP, and Azure** . Open source framework with SDK for Go, Python, Java, JavaScript integrations . Use as CSPM to monitor and enforce security policies across cloud infrastructure .



- **[Prowler](https://github.com/prowler-cloud/prowler)**

  **Open-source scanning to validate and extend Microsoft Defender for Cloud** (and standalone) . Supports **Azure, AWS, GCP, and Kubernetes**. Custom policy creation, CLI-first scriptable, exportable detections (JSON, CSV, JUnit, HTML) . **No vendor lock-in**—checks are inspectable, modifiable, and versionable .



- **[Kubescape](https://github.com/kubescape/kubescape)**

  **CNCF project for Kubernetes security posture** . **Kubescape 4.0** (March 2026) GA's **Runtime Threat Detection** with **CEL-based rules** and Kubernetes CRDs for rules/bindings . **Kubescape Storage** GA using Kubernetes Aggregated API for SBOMs and vulnerability manifests . **AI-era security**: KAgent-native plug-in for AI agents to scan clusters; security posture scanning for KAgent itself (42 config points, 15 Rego controls) .



### Additional Strong Open-Source Options



- **Cloud Governance**: **Cloud Custodian** (CNCF Incubating, YAML DSL, 500+ resource types) .

- **Kubernetes Admission**: **OPA/Gatekeeper** (Rego, CNCF graduated), **Kyverno** (YAML, CEL, CNCF graduated), **Kubewarden** (WASM portable), **ValidatingAdmissionPolicy** (in-tree CEL) .

- **IaC Security**: **Checkov** (750+ policies, Terraform depth), **Trivy** (multi-scanner), **Conftest** (Rego config testing), **Pulumi CrossGuard** (Pulumi-native) .

- **CSPM/Inventory**: **CloudQuery** (asset inventory), **Prowler** (multi-cloud posture), **Kubescape** (K8s posture + runtime) .



**Frameworks for building custom systems**: Combine **Cloud Custodian** for cloud account governance and remediation, **OPA/Gatekeeper** or **Kyverno** for Kubernetes admission control, **Checkov** for IaC scanning in CI, and **Prowler** or **CloudQuery** for multi-cloud posture visibility. Add **Prometheus + Grafana** for policy execution observability.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Cloud policy management platforms handle sensitive infrastructure and compliance data; ensure proper access controls and adherence to organizational governance requirements.

- **Open-source reality**: The open-source ecosystem for cloud policy management is **mature and production-ready**. **Cloud Custodian** is the foundational cloud governance engine (CNCF Incubating, powers Stacklet) . **OPA** and **Kyverno** are both **CNCF graduated** for Kubernetes admission control . **Checkov** provides 750+ IaC policies with Terraform graph depth . **Kubescape 4.0** brings GA runtime threat detection with CEL rules . For **fully managed cloud governance** with AI acceleration and enterprise support, Stacklet remains the commercial option built by Cloud Custodian's creators .



---



**Made for platform engineers, cloud security architects, DevOps leads, and governance teams.**

Let's make cloud policy management more open, transparent, and enforceable.
