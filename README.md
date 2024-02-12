# Development Secrets Management

**Contents:**

- [What are development secrets](#what-are-development-secrets)
- [How to share development secrets](#how-to-share-development-secrets)
  - [Encrypted secret file](#encrypted-secret-file)
    - [Transcrypt](#transcrypt)
    - [Git-crypt](#git-crypt)
    - [Git-secret](#git-secret)
    - [SOPS](#sops)
  - [Secrets management](#secrets-management)
  - [Key management](#key-management)

## What are development secrets
In software projects, you need to secure every type of service you provide and external service you use. 
This is often done with _secrets_.
Secrets can be of several types.
These secrets attempt to provide a layer of security.
In many cases, secrets are needed during development to be able to develop a service locally.
For single developer projects, this may not be a big issue because you can store them locally.
But in a project where multiple people are contributing to the project, these secrets need to be shared.

## How to share development secrets
Sharing development secrets in a secure way can be done through various ways and with varying degrees of complexity.
The following is an uncompleted list of possible solutions, which will be described in more detail below:
- Encrypted secret file
- Secrets manager
- Key management

### Encrypted secret file
This category refers to storing the secrets in a encrypted file in a Git repository.
Even when encrypted the access to the repository should be private and should only be accessed by anyone who needs.
The following list of methods and their pros and cons is adapted from a Medium post by Brian Davis.
> [More details here](https://medium.com/@slimm609/securely-storing-secrets-in-git-542771d3ed8c)

#### Transcrypt
[Transcrypt](https://github.com/elasticdog/transcrypt) is a encryption tool for Git using OpenSSL.
By configuring a ```.gitattributes``` file it determines which files should be encrypted or decrypted.
It automatically detects if a viewer should be able to see the content of a secrets file and masks it for unauthorized viewers. 

| Pros                       | Cons                                             |
|----------------------------|--------------------------------------------------|
| Seamless usage             | Secrets are stored in plain text on each machine |
| Encrypts the file contents | .gitattributes needs to be configured with care  |
|                            | Default cipher is: AES-256-CBC                   |

#### Git-crypt
[Git-crypt](https://github.com/AGWA/git-crypt) is a encryption tool for Git using OpenSSL.
Like transcrypt it also uses a ```.gitattributes``` file in a similar way.

| Pros                                   | Cons                                                       |
|----------------------------------------|------------------------------------------------------------|
| Seamless usage                         | Secrets are stored in plain text on each machine           |
| Encrypts the file contents             | .gitattributes needs to be configured with care            |
| Better default cipher than AES-256-CBC | Uses a fixed key length when generating the encryption key |

#### Git-secret
[Git-secret](https://git-secret.io/)
> Needs description

| Pros                           | Cons                                               |
|--------------------------------|----------------------------------------------------|
| Uses GPG private keys to share | Each secret file must be added to ```.gitignore``` |
|                                | Needs manual commands to encrypt and decrypt       |

#### SOPS
> Needs description

### Secrets management
A secret management is a product built to manage secrets.
Essentially these are installed programs that interact can be accessed to retrieve the secrets.
Here is a list of products for developers:
- [Cyberark Conjur](https://www.conjur.org/)
- [1Password](https://1password.com/de/developers)
- [HashiCorp Vault](https://www.vaultproject.io/)
>Needs contribution

### Key management
- [Azure Key Vault](https://azure.microsoft.com/en-us/products/key-vault)
- [AWS Key Management Service](https://aws.amazon.com/kms)
- [Google Secret Mnaager](https://cloud.google.com/secret-manager)

## Examples
>Needs contribution
