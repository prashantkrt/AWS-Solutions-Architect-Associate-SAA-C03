# IAM policy evaluation

IAM evaluates whether a request is permitted by combining applicable policies and organizational controls. For an SAA-C03 scenario, start with the request's principal, action, resource, and context.

## Reasoning sequence

1. Is there an applicable explicit **Deny**? If yes, access is denied.
2. Is there an applicable **Allow** from an identity-based or resource-based policy?
3. Do permissions boundaries, session policies, SCPs, or resource controls limit that permission?
4. Do trust policies permit the principal to assume the role, if role assumption is involved?
5. Are conditions such as source IP, MFA, tags, or encryption context satisfied?

An SCP sets the maximum permissions available to accounts in an organization; it does not grant a permission. A permissions boundary similarly limits an identity's maximum permissions without granting them. A role trust policy controls who can assume that role; its permissions policy controls what the assumed role can do.

## Least-privilege review

- Replace broad actions/resources with only required operations and resource ARNs.
- Avoid wildcard principals in resource policies unless the access is intentionally public and tightly controlled.
- Prefer roles and temporary credentials to embedded long-lived keys.
- Test policy changes in a non-production account and use IAM Access Analyzer and policy simulation as aids—not as substitutes for review.
