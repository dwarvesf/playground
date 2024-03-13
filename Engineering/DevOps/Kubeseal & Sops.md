---
tags: engineering/devops, secret, kubeseal, sops
author: Nguyen Huu Nguyen
github_id: nguyennh4522
date: 2022-09-28
---

- `Kubeseal`: Encrypt your Secret into a SealedSecret, which is safe to store - even to a public repository. The SealedSecret can be decrypted only by the controller running in the target cluster and nobody else (not even the original author) is able to obtain the original Secret from the SealedSecret. SealedSecret is composed of two parts:
  - Cluster-side controller: `sealed-secrets-controller` - generate keypair and decrypt secrect.
  - Client-side utility: `kubeseal` - uses asymmetric crypto to encrypt secrets that only the controller can decrypt.

- `Sops`: Sops is a binary able to encrypt configuration files. But rather than encrypting the whole file Sops understands format (JSON, YAML, INI, etc) and will only encrypt the values of each line (with AWS KMS, GCP KMS, Azure Key Vault, age, and PGP).

## How it works
![[_assets/kubeseal_&_sops.png]]

- Source code repo: contains secret was encrypted by `sops`
- Github action: use `sops` to decrypt secret and `kubeseal` to seal secret and push it to infrastructure repo
- Infrastructure repo: save all Kubernetes config
- Cluster: use `sealed-secrets-controller` to decrypt sealedsecret to secret and apply it

## Core benefits
- **Easy management**: Developers can update secret without devops.
- **Security**: The secret will be encrypted and cannot be decrypted without the key provided by devops.

## Reference
- https://github.com/bitnami-labs/sealed-secrets
- https://github.com/mozilla/sops

---
<!-- cta -->

### Contributing
At Dwarves, we encourage our people to read, write, share what we learn with others, and [[CONTRIBUTING|contributing to the Brainery]] is an important part of our learning culture. For visitors, you are welcome to read them, contribute to them, and suggest additions. We maintain a monthly pool of $1500 to reward contributors who support our journey of lifelong growth in knowledge and network.

### Love what we are doing?
- Check out our [products](https://superbits.co)
- Hire us to [build your software](https://d.foundation)
- Join us, [we are also hiring](https://github.com/dwarvesf/WeAreHiring)
- Visit our [Discord Learning Site](https://discord.gg/dzNBpNTVEZ)
- Visit our [GitHub](https://github.com/dwarvesf)