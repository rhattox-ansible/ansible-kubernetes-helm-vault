# ansible-kubernetes-helm-vault

Installs Vault with single-replica Raft storage, initializes it with one unseal
key, saves the initialization JSON locally, and unseals Vault.

## Layout

```text
main.yaml
defaults/main.yaml
meta/main.yml
tasks/main.yaml
tasks/0-install-vault.yaml
```

The root playbook loads defaults and includes the task dispatcher. The dispatcher
reports progress and includes the installation tasks. Galaxy role metadata is in
`meta/main.yml`.

## Usage

Requires Ansible, the `kubernetes.core` collection, Helm, Kubernetes Python
dependencies, and access to a Kubernetes cluster. Initialization expects an
uninitialized Vault instance. Protect `/mnt/vault/vault-init.json`, which contains
the unseal key and root token.

```bash
ansible-playbook main.yaml
```
