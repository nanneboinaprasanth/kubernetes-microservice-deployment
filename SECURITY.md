# Security Policy

## Reporting Security Issues

Please do not open public issues for sensitive security reports.

Email: `nprasanth1014@gmail.com`

Include a short description, affected files or configuration, and steps to reproduce if possible.

## Secret Handling

- Do not commit real passwords, tokens, kubeconfigs, or cloud credentials.
- Keep Kubernetes `Secret` examples as placeholders only.
- Store production secrets in a secret manager or inject them through CI/CD.
- Rotate any secret immediately if it is accidentally committed.

## Recommended GitHub Settings

Enable these in repository settings:

- Secret scanning
- Dependabot alerts
- Dependabot security updates
- Branch protection for `main`
- Required status checks for pull requests
