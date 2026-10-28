# Chapter 2.2–2.3 — AWS Authentication and SSH Key Setup

## 1. Configure AWS CLI credentials

When you are ready to access your own AWS account, run:

```bash
aws configure
```

Enter your own credentials interactively. Use the region required by your assignment; the source guide uses `us-east-1` as an example and `json` as the output format.

**Never paste real access keys or secret keys into this repository, a chat, a screenshot, or a `.tf` file.** Any credentials shown in training material should be treated as examples only. Do not use example credentials as if they were valid.

The AWS CLI stores configuration in local files under `~/.aws/`. Keep these local files private and out of Git.

## 2. Verify the authenticated identity

Run:

```bash
aws sts get-caller-identity
```

A successful response returns an account identifier, user ID, and ARN for the active identity. The values depend on the credentials you configured. Do not copy sample account IDs or ARNs into your own evidence.

If the command fails, confirm that the credentials are valid, the intended profile/region is selected, and the IAM principal has permission to call STS.

## 3. Generate an SSH key pair

The source guide demonstrates a 4096-bit RSA key. Generate it on your own machine:

```bash
mkdir -p ~/.ssh
ssh-keygen -t rsa -b 4096 -f ~/.ssh/library-aws-key -N "" -C "devops@careertiq-library"
chmod 400 ~/.ssh/library-aws-key
chmod 644 ~/.ssh/library-aws-key.pub
ls -la ~/.ssh/library-aws-key*
```

This example uses an empty passphrase for automation, which has security trade-offs. If you use a passphrase or a different key type, follow your institution's requirements and AWS guidance.

- `library-aws-key` is the **private key**. Never upload or commit it.
- `library-aws-key.pub` is the **public key**. Only the public key is used for import.

## 4. Import the public key to EC2

Only perform this step if you have an AWS account and permission to import EC2 key pairs. Example command for the region used in the source guide:

```bash
aws ec2 import-key-pair \
  --key-name "library-aws-key" \
  --public-key-material fileb://~/.ssh/library-aws-key.pub \
  --region us-east-1
```

If your shell does not expand `~` correctly after `fileb://`, use the absolute path to the `.pub` file. Do not upload the private key.

Verify key-pair registration with:

```bash
aws ec2 describe-key-pairs --key-names library-aws-key --region us-east-1
```

A successful result should list the key pair if it exists in that account and region. Your actual output will differ from training examples.

## Security checklist

- [ ] No AWS credentials committed to Git.
- [ ] No private SSH key committed to Git.
- [ ] Real account identifiers are redacted from public screenshots where appropriate.
- [ ] AWS commands were run only in an account you are authorized to use.
