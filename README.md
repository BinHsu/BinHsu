<!--
  Repo role (BinHsu/BinHsu — special GitHub profile repo):
  - README.md  -> renders as the GitHub profile page (github.com/BinHsu)
  - index.html -> reference copy for the personal homepage (binhsu.org);
                  NOT served from this repo (no Pages here — binhsu.org is
                  served by BinHsu/BinHsu.github.io)
  The job-application resume is a SEPARATE artifact with a different purpose:
  2026Job/templates/resume.html — do not sync the two.
-->
### Hi, I'm Pin-Feng (Bin) Hsu

**Hands-on Engineer** with **15 years** spanning two domains:
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
| [**aegis-platform-aws**](https://github.com/BinHsu/aegis-platform-aws) | EKS + Karpenter · ArgoCD · observability *(extracted from landing-zone per ADR-017)* | **Platform engineering** / paved road / IDP | Platform |
| [**aegis-core**](https://github.com/BinHsu/aegis-core) | C++ + whisper.cpp (gRPC) · Go BFF gateway · TypeScript React; dual-mode LAN/Cloud | **Application repo** | Workload — app |
| [**aegis-core-deploy**](https://github.com/BinHsu/aegis-core-deploy) | K8s manifests for the application | **Config repo** (two-repo GitOps, Weaveworks) | Workload — deploy |

**End-to-end GitOps loop:** CI in the app repo builds + pushes the image to ECR, commits the new tag cross-repo into the deploy repo, ArgoCD in the platform tier reconciles. Every trade-off documented in **Architecture Decision Records** across both V2 repos — see also the running [incident postmortem log](https://github.com/BinHsu/aegis-landing-zone-aws/blob/main/docs/incidents.md) and [recruiter-oriented competency notes](https://github.com/BinHsu/aegis-landing-zone-aws/blob/main/docs/interview-notes.md).

**DevSecOps** lives on the account fabric (SCPs, zero static credentials, OIDC federation, gitleaks/push-protection); **GitOps** moves with the platform tier; **FinOps** spans both (budget alerts, destroy automation, spot-first compute, ~$5/month baseline).

---

#### Foundation — Secure-by-Default Templates

Reusable template repositories that wire a hardened default — security harness, agent rules, CI gates — into a new project from commit zero.

| Repo | Stack | Description |
|---|---|---|
| [**aegis-template**](https://github.com/BinHsu/aegis-template) | CLAUDE.md / AGENTS.md agent rules · pre-commit secret hooks · semgrep · GitHub Actions · tool registry | A GitHub **template repository** implementing the [Harness Engineering 7 security practices](https://github.com/BinHsu/aegis-template/blob/main/docs/SECURITY_PRACTICES.md) (Rule → Execution → Verification): least-privilege agent tool access, secrets-residue scanning, a destructive-action red line (preview → confirm → log), and a tool registry. "Use this template" wires the full DevSecOps harness into any new repo — the friction differential does the work, not a checklist nobody reads. |

---

#### Tools — Small, Sharp Utilities

Single-purpose command-line utilities, built when an existing tool didn't fit — cross-platform, run locally, tested.

| Repo | Stack | Description |
|---|---|---|
| [**aegis-yt-transcriber**](https://github.com/BinHsu/aegis-yt-transcriber) | Python · yt-dlp · faster-whisper / mlx-whisper · uv · pytest (BVA) · GitHub Actions (3-OS matrix) | Turn a YouTube URL into a transcript locally — even when captions are disabled. Cross-platform (macOS / Linux / Windows); the audio never leaves your machine. |

---

#### Spike — Research & Field Experiments

Time-boxed spikes that take one hard question to a verified answer, then ship the findings as a field report — proof over polish.

| Repo | Stack | Description |
|---|---|---|
| [**aegis-talos-apple-container-provisioner**](https://github.com/BinHsu/aegis-talos-apple-container-provisioner) | Go · Talos `pkg/provision` · Apple `container` (OCI micro-VMs) · DHCP reconciliation · GitHub Actions | A local Talos cluster on Apple's `container` runtime — no Docker daemon, one micro-VM per node. Verified end to end (`talosctl cluster create apple-container` → nginx HTTP 200 → clean teardown). The crux is networking: apple/container assigns IPs by DHCP, breaking Talos's static-IP-at-create contract, so the provider owns `Create` and reconciles the address after boot. Pitched upstream, declined on principled grounds — [discussion #13587](https://github.com/siderolabs/talos/discussions/13587). Write-up: [Bin's Lab](https://binhsu.github.io/a-native-talos-provider-for-apple-container/). |

---

Based in **Berlin** · **Chancenkarte** — in-country Blue Card conversion upon contract · Open to relocate across Germany

[binhsu.org](https://binhsu.org) · [Bin's Lab](https://binhsu.github.io) · [LinkedIn](https://www.linkedin.com/in/bin-hsu-taiwan/) · [YouTube](https://www.youtube.com/@BHDailyPov)

---

#### License & Attribution

All portfolio repositories are published under the **MIT License**. Fork freely — attribution to [BinHsu](https://github.com/BinHsu) is appreciated.
