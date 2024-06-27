# docker-build-ecr-push-action

Build and push a Docker image to Amazon ECR with Buildx cache.

IAM Role to be authenticated using OIDC must be passed.

See doc [Configuring OpenID Connect in Amazon Web Services - GitHub Docs](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)

## Usage

```yaml
name: Sample Workflow

permissions:
  id-token: write
  contents: read
  pull-requests: read

jobs:
    build:
        name: Build and Push
        runs-on: ubuntu-latest
        steps:
            - uses: YumaFuu/docker-build-ecr-push-action@v1
              with:
                aws_role_arn: arn:aws:iam::YOUR_ACCOUNT:role/YOUR_ROLE
                context: .
                dockerfile: path/to/Dockerfile
                ecr_repo: sample-repo
                tag: ${{ github.sha }}
```
