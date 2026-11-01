# 12 · Hands-on labs

The labs emphasize safe observation, design reasoning, and cleanup planning. They do not automatically deploy resources.

## Labs

1. [Read-only IAM and account review](iam-read-only-review.md)
2. [Plan a VPC on paper](vpc-design-exercise.md)
3. [S3 protection and lifecycle design](s3-design-exercise.md)
4. [Resilience tabletop exercise](resilience-tabletop.md)

## Before using an AWS account

- Confirm account ownership, approved Region, and any organizational restrictions.
- Use a sandbox account and least-privilege temporary credentials; never use root credentials for routine work.
- Read the current pricing page before creating anything. “Free tier” is not a guarantee of zero cost.
- Set a budget alert, record what you create, and define cleanup before starting.
- Avoid public access, production data, persistent compute, and resources that can create ongoing charges.
- Verify deletion/termination and check billing after the exercise.

Commands shown in topic notes are read-only unless explicitly stated. No command in this repository is intended to deploy infrastructure.
