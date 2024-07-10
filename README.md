<a name="readme-top"></a>

# 6G-Sandbox-Sites <!-- omit in toc -->

Particular information of each site for the deployment of components of the [6G-Library](https://github.com/6G-SANDBOX/6G-Library).

<details>
<summary>Table of Contents</summary>

- [Site Directory Structure](#site-directory-structure)
- [Getting started](#getting-started)
  - [Install ansible-core](#install-ansible-core)
  - [Password Encrypt/Decrypt](#password-encryptdecrypt)
  - [Encrypt Site File](#encrypt-site-file)
  - [Edit Encrypted Site File](#edit-encrypted-site-file)
  - [Decrypt Site File](#decrypt-site-file)

</details>

## Site Directory Structure

```
site_name/       # Folder with the site name
└── core.yaml    # File containing the encrypted site information
```

The [`.dummy_site/core.yaml`](.dummy_site/core.yaml) file is a template with the information that has to be indicated for each platform.

## Getting started

> [!NOTE]
> This process has been tested on Ubuntu version 22.04.3 LTS.

### Install ansible-core

- Linux

  ```sh
  apt install ansible-core
  ```

### Password Encrypt/Decrypt

The password is a random string of characters that has to be stored in a file (recommended with extension .txt).

> [!CAUTION]
> Try to avoid scapable special characters as ", ', `, ´, #, $...
> 
> Unpredictable errors might happen.

> [!TIP]
> Typical recommendations are:
>
> - String size: 20
> - Uppercase letters (A-Z)
> - Lower case letters (a-z)
> - Numbers (0-9)
> - Special characters (excluding scapable special characters)
>
> Can use [online random string](https://www.random.org/strings/).

### Encrypt Site File

```sh
ansible-vault encrypt path/file_name_content.yaml --vault-password-file=path/file_name.txt
```

where:

- `path/file_name_content.yaml` is the path to the file with the content to be encrypted.
- `--vault-password-file=path/file_name.txt` is the path to the file containing the password.

example:

```sh
ansible-vault encrypt test/core.yaml --vault-password-file=test/pass.txt
```

This will **replace** the file test/core.yaml with the encrypted content.

### Edit Encrypted Site File

```sh
ansible-vault edit test/file_name_encrypted.yaml --vault-password-file=path/file_name.txt
```

where:

- `test/file_name_encrypted.yaml` is the path to the file with encrypted content.
- `--vault-password-file=path/file_name.txt` is the path to the file containing the password.

example:

```sh
ansible-vault edit test/core.yaml --vault-password-file=test/pass.txt
```

This will return the updated and encrypted file with the new changes.

### Decrypt Site File

```sh
ansible-vault decrypt test/file_name_encrypted.yaml --vault-password-file=path/file_name.txt
```

where:

- `test/file_name_encrypted.yaml` is the path to the file with encrypted content.
- `--vault-password-file=path/file_name.txt` is the path to the file containing the password.

example:

```sh
ansible-vault decrypt test/core.yaml --vault-password-file=test/pass.txt
```

This will replace the file test/core.yaml with the raw content.

<p align="right"><a href="#readme-top">Back to top&#x1F53C;</a></p>