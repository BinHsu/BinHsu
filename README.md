### Hi, I'm Pin-Feng (Bin) Hsu

**Hands-on Platform Engineer** with **15 years** spanning two domains:
**C++ systems** (10 yrs — embedded Linux, CMake, ARM/MIPS/x86, deployed across 120+ countries)
and **platform infrastructure** (5 yrs — 155 CI/CD pipelines, Kubernetes, 5 AWS accounts, 4-5M req/day, end-to-end ownership with full system context).

**AWS Certified Solutions Architect — Professional** (2026) · 3 consecutive years owning ISO 27001/27701 audits

---

#### V1 — Aegis Prompter (LAN) `[Shipped]`

| Repo | Stack |
|---|---|
| [**Aegis-Prompter**](https://github.com/BinHsu/Aegis-Prompter) | Python · MLX-Whisper · Sentence Transformers · Streamlit · Apple NPU |

A proof-of-concept teleprompter built in 2 days — Apple Silicon NPU transcription, vector-semantic RAG (pure numpy, no external DB), and a multi-role web UI where staff inject tactical cues into the speaker's display in under 0.5s.

---

#### V2 — Four-Tier Multi-Repo GitOps `[Near Production]`

Industry-aligned split across four tiers, each with its own repo and ownership boundary:

| Repo | Stack | Industry name | Tier |
|---|---|---|---|
| [**aegis-landing-zone-aws**](https://github.com/BinHsu/aegis-landing-zone-aws) | Organizations · OUs · SCPs · Identity Center · GitHub OIDC · security baseline | **Landing Zone** (AWS Control Tower) | Account fabric |
| [**aegis-platform-aws**](https://github.com/BinHsu/aegis-platform-aws) | EKS + Karpenter · ArgoCD · observability *(extracted from landing-zone per ADR-033)* | **Platform engineering** / paved road / IDP | Platform |
| [**aegis-core**](https://github.com/BinHsu/aegis-core) | C++ + whisper.cpp (gRPC) · Go BFF gateway · TypeScript React; dual-mode LAN/Cloud | **Application repo** | Workload — app |
| [**aegis-core-deploy**](https://github.com/BinHsu/aegis-core-deploy) | K8s manifests for the application | **Config repo** (two-repo GitOps, Weaveworks) | Workload — deploy |

**End-to-end GitOps loop:** CI in the app repo builds + pushes the image to ECR, commits the new tag cross-repo into the deploy repo, ArgoCD in the platform tier reconciles. Every trade-off documented in **Architecture Decision Records** across both V2 repos — see also the running [incident postmortem log](https://github.com/BinHsu/aegis-landing-zone-aws/blob/main/docs/incidents.md) and [recruiter-oriented competency notes](https://github.com/BinHsu/aegis-landing-zone-aws/blob/main/docs/interview-notes.md).

**DevSecOps** lives on the account fabric (SCPs, zero static credentials, OIDC federation, gitleaks/push-protection); **GitOps** moves with the platform tier; **FinOps** spans both (budget alerts, destroy automation, spot-first compute, ~$5/month baseline).

---

#### Foundation — Aegis-Template `[GitHub Template]`

| Repo | Stack |
|---|---|
| [**aegis-template**](https://github.com/BinHsu/aegis-template) | CLAUDE.md / AGENTS.md agent rules · pre-commit secret hooks · semgrep · GitHub Actions · tool registry |

A reusable GitHub **template repository** implementing the [**Harness Engineering 7 security practices**](https://github.com/BinHsu/aegis-template/blob/main/docs/SECURITY_PRACTICES.md) (Rule → Execution → Verification): least-privilege agent tool access, secrets-residue scanning, a destructive-action red line (preview → confirm → log), and a production-grade tool registry. "Use this template" starts any new repo with the full DevSecOps harness already wired — the friction differential does the work, not a checklist nobody reads.

---

Based in **Berlin** · **Chancenkarte** — in-country Blue Card conversion upon contract · Open to relocate across Germany

[binhsu.org](https://binhsu.org) · [LinkedIn](https://www.linkedin.com/in/bin-hsu-taiwan/) · [YouTube](https://www.youtube.com/@BHDailyPov)

---

#### License & Attribution

All portfolio repositories are published under the **MIT License**. Fork freely — attribution to [BinHsu](https://github.com/BinHsu) is appreciated.
