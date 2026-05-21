### Hi, I'm Pin-Feng (Bin) Hsu

**Hands-on Platform Engineer** with **15 years** spanning two domains:
**C++ systems** (10 yrs — embedded Linux, CMake, ARM/MIPS/x86, deployed across 120+ countries)
and **platform infrastructure** (5 yrs — 155 CI/CD pipelines, Kubernetes, 5 AWS accounts, 4-5M req/day, end-to-end ownership with full system context).

**AWS Certified Solutions Architect — Professional** (2026) · 3 consecutive years owning ISO 27001/27701 audits

---

#### V1 — Aegis Prompter (LAN)

| Repo | Status | Stack |
|---|---|---|
| [**Aegis-Prompter**](https://github.com/BinHsu/Aegis-Prompter) | Shipped | Python · MLX-Whisper · Sentence Transformers · Streamlit · Apple NPU |

A proof-of-concept teleprompter built in 2 days — Apple Silicon NPU transcription, vector-semantic RAG (pure numpy, no external DB), and a multi-role web UI where staff inject tactical cues into the speaker's display in under 0.5s.

---

#### V2 — Four-Tier Multi-Repo GitOps

Industry-aligned split across four tiers, each with its own repo and ownership boundary:

| Tier | Industry name | Stack | Repo |
|---|---|---|---|
| Account fabric | **Landing Zone** (AWS Control Tower) | Organizations · OUs · SCPs · Identity Center · GitHub OIDC · security baseline | [aegis-aws-landing-zone](https://github.com/BinHsu/aegis-aws-landing-zone) |
| Platform | **Platform engineering** / paved road / IDP | EKS + Karpenter · ArgoCD · observability *(extracted from landing-zone per ADR-033)* | [aegis-platform](https://github.com/BinHsu/aegis-platform) |
| Workload — app | **Application repo** | C++ + whisper.cpp (gRPC) · Go BFF gateway · TypeScript React; dual-mode LAN/Cloud | [aegis-core](https://github.com/BinHsu/aegis-core) |
| Workload — deploy | **Config repo** (two-repo GitOps, Weaveworks) | K8s manifests for the application | [aegis-core-deploy](https://github.com/BinHsu/aegis-core-deploy) |

**End-to-end GitOps loop:** CI in the app repo builds + pushes the image to ECR, commits the new tag cross-repo into the deploy repo, ArgoCD in the platform tier reconciles. Every trade-off documented in **Architecture Decision Records** across both V2 repos — see also the running [incident postmortem log](https://github.com/BinHsu/aegis-aws-landing-zone/blob/main/docs/incidents.md) and [recruiter-oriented competency notes](https://github.com/BinHsu/aegis-aws-landing-zone/blob/main/docs/interview-notes.md).

**DevSecOps** lives on the account fabric (SCPs, zero static credentials, OIDC federation, gitleaks/push-protection); **GitOps** moves with the platform tier; **FinOps** spans both (budget alerts, teardown automation, spot-first compute, ~$5/month baseline).

---

Based in **Berlin** · **Chancenkarte** — in-country Blue Card conversion upon contract · Open to relocate across Germany

[binhsu.org](https://binhsu.org) · [LinkedIn](https://www.linkedin.com/in/bin-hsu-taiwan/) · [YouTube](https://www.youtube.com/@BHDailyPov)

---

#### License & Attribution

All portfolio repositories are published under the **MIT License**. Fork freely — attribution to [BinHsu](https://github.com/BinHsu) is appreciated.
