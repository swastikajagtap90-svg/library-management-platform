# Chapter 2.4 — Verification Checklist and Troubleshooting

## Toolchain verification matrix

Run these commands on the workstation where you performed installation and record the real output.

| Component | Verification command | What to check |
|---|---|---|
| AWS CLI v2 | `aws --version` | Output identifies AWS CLI version 2 |
| AWS authentication | `aws sts get-caller-identity` | Command succeeds and shows the intended AWS identity |
| Terraform | `terraform -version` | Version is consistent with the assignment target (v1.7+) |
| Ansible Core | `ansible --version` | Version is consistent with the assignment target (v2.16+) |
| EC2 key pair | `aws ec2 describe-key-pairs --key-names library-aws-key --region us-east-1` | Key pair exists in the intended account and region |

**Status note:** Nothing in this repository should be marked “VERIFIED” until the corresponding command has actually been run and checked. This ZIP contains documentation only.

## Common troubleshooting cases

| Symptom | Possible cause | Suggested check |
|---|---|---|
| `aws: command not found` | AWS CLI is not installed or its binary directory is not on `PATH` | Check installation and `PATH`; reopen the terminal after changes |
| HashiCorp repository/GPG error | Signing key, repository setup, certificate, or network issue | Follow current official HashiCorp installation instructions and verify system certificates |
| SSH says private key permissions are too open | Private key permissions are too permissive | Run `chmod 400 ~/.ssh/library-aws-key` on Linux/macOS |
| `InvalidAccessKeyId` | Incorrect, inactive, or deleted access key | Verify the selected AWS profile and create credentials through the authorised AWS process if needed |
| STS access denied | Active identity lacks required permission or credentials are for a different account/profile | Check the identity, profile, and IAM permissions with your administrator |
| EC2 key pair not found | Wrong key name, region, or AWS account | Check the active identity and region, then list key pairs |

## Final checklist

- [ ] Baseline utilities installed (if performing the lab)
- [ ] AWS CLI v2 installed and version recorded
- [ ] Terraform installed and version recorded
- [ ] Ansible installed and version recorded
- [ ] AWS identity checked using STS (if using AWS)
- [ ] SSH key pair created and public key imported (if required)
- [ ] Secrets and private keys excluded from Git
- [ ] Actual evidence captured without exposing secrets

## Scope

This chapter prepares the workstation for the next stage, Terraform Infrastructure as Code provisioning. It does not provision a VPC, EC2 instance, or S3 bucket by itself.
