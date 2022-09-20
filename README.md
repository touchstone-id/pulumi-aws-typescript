# pulumi-aws-typescript reusable workflow

This workflow will install npm dependancies, create a cache, and preview or deploy to an AWS account.
## Getting Started

### Prerequisites

You must have a pulumi team or org setup.

You must have an AWS account and cli configured user provisioned.

Your project must by node or typescript.

This assumes you also have a github deploy environment setup for 'dev' and 'prod'.

Configured secrets:
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION
PULUMI_ACCESS_TOKEN

### Setup

1. create an action yaml file in your project

i.e: `.github/workflows/pulumi.yaml`

2. configure the job in your yaml file
```yaml
name: Preview Infrastructure
on:
  pull_request:
    branches:
      - develop
jobs:
  preview:
    uses: touchstone-id/pulumi-aws-typescript/.github/workflows/pulumi.yml@v1.0.0
    with:
      environment: dev
      aws-profile: qa
      pulumi-action: up
      pulumi-org-id: <your-pulumi-namespace>
    secrets: inherit
```

### Workflow

This workflow uses the following dependencies:

actions/checkout
actions/setup-node
aws-actions/configure-aws-credentials
actions/cache
pulumi/actions