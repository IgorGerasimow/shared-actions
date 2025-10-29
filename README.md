# shared-actions

Reusable **GitHub Actions** for Docker image builds & pushes, plus a **composite action** for step‑level reuse.

- Reusable workflow: `.github/workflows/docker-build-push.yml`
- Composite action: `.github/actions/docker-build`
- Release automation via **release‑please**
- Secure by default: **GHCR** login with `GITHUB_TOKEN`, optional OIDC for cloud registries
