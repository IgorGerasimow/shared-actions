# shared-actions

Reusable **GitHub Actions** that cover a basic Kubernetes-style container delivery pipeline: build the image, run tests, and publish the artifact.

## Composite actions

| Action | Path | Summary |
| ------ | ---- | ------- |
| Docker Build | `.github/actions/docker-build` | Build multi-platform Docker images with BuildKit caching. |
| Run Tests | `.github/actions/run-tests` | Install dependencies (optional) and execute project tests. |
| Docker Publish | `.github/actions/docker-publish` | Authenticate, build, and push tagged Docker images. |

### Docker Build
```yaml
- uses: ./.github/actions/docker-build
  with:
    context: .
    file: ./Dockerfile
    build_args: |
      NODE_ENV=production
```

### Run Tests
```yaml
- uses: ./.github/actions/run-tests
  with:
    working-directory: ./app
    install-command: npm ci
    test-command: npm test -- --runInBand
```

### Docker Publish
```yaml
- uses: ./.github/actions/docker-publish
  with:
    image: ghcr.io/example/app
    context: .
    tags: |
      type=raw,value=latest
      type=sha
```

## Reusable workflows

- `.github/workflows/docker-build-push.yml`

Release automation remains powered by **release-please**, and the repository stays secure by default with support for `GITHUB_TOKEN` authentication or custom registry credentials.
