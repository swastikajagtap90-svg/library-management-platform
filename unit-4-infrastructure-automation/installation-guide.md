# Chapter 2.1 — Installing AWS CLI, Terraform, and Ansible

## 1. Workstation baseline utilities

On an Ubuntu/Debian-based system, update package indexes and install common utilities:

```bash
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y curl wget unzip jq git software-properties-common ca-certificates gnupg apt-transport-https python3 python3-pip python3-venv
```

> Review package changes before confirming them on a machine you rely on. These commands are instructions; they have not been executed as part of this documentation package.

## 2. Install AWS CLI v2 on Linux x86_64

Download and install the official AWS CLI v2 bundle:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip -q awscliv2.zip
sudo ./aws/install --update
rm -rf aws awscliv2.zip
aws --version
```

The final command should print an AWS CLI version string. Record the actual output if you perform the installation.

**Platform note:** The Linux x86_64 installer is intended for compatible Linux x86_64 systems. For macOS, use the official macOS installer or a package manager. For Windows, use the official Windows installer or run Linux instructions inside Ubuntu on WSL2.

## 3. Install Terraform

The source assignment describes registering HashiCorp's official signing key and APT repository, then installing Terraform. Follow HashiCorp's current official installation instructions for your exact OS and distribution before running repository setup commands.

After installation, verify the binary:

```bash
terraform -version
```

The assignment targets Terraform v1.7 or later. The displayed version is the evidence to record; do not assume the target version was installed without checking.

## 4. Install Ansible Core

On Ubuntu, the assignment describes adding the Ansible PPA and installing Ansible:

```bash
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt-get install -y ansible
ansible-galaxy collection install amazon.aws community.general
ansible --version
```

The assignment targets Ansible Core v2.16 or later. Check the version output on the machine where you perform the setup.

## 5. macOS note

The source guide suggests using Homebrew:

```bash
brew install awscli terraform ansible
```

Confirm the current package names and installation guidance with the official tool documentation for your platform.

## Completion record

Use `docs/verification-and-troubleshooting.md` to record the actual outputs and status after you perform the steps.
