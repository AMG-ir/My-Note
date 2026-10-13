# SSH Key Authentication

## Overview

SSH key authentication is a way to authenticate to a remote server using a cryptographic key pair instead of relying only on an account password.

It uses two related keys:

- **Private key:** Kept on the local machine. It must remain private.
- **Public key:** Installed on the server and allowed to be shared with that server.

The private key is used by the SSH client to prove possession of the matching key. The server checks whether the corresponding public key is authorized for the account.

## How It Works

1. Generate a key pair on the local machine.
2. Add the public key to the remote account's `~/.ssh/authorized_keys` file.
3. Connect to the server using SSH.
4. The client proves it has the matching private key, and the server verifies the public key is authorized.
5. If authentication succeeds and other access checks pass, the connection is established.

## Common Commands

Generate an RSA key pair with a 4096-bit key:

```bash
ssh-keygen -t rsa -b 4096
```

Copy the public key to a server account:

```bash
ssh-copy-id user@server_ip
```

Connect to the server:

```bash
ssh user@server_ip
```

These are example commands for learning; they have not been tested as part of this research note. The server must be reachable and configured to accept SSH connections.

## Key Files

Typical default file names for an RSA key pair are:

- `~/.ssh/id_rsa` — private key; keep it secret.
- `~/.ssh/id_rsa.pub` — public key; can be installed on the server.
- `~/.ssh/authorized_keys` — on the server, lists public keys permitted to authenticate to that account.

File names can differ if another key type or custom name is used.

## Benefits

- Can avoid entering the server account password for every connection.
- Can provide stronger authentication than password-only access when configured and managed properly.
- Makes it possible to disable password-based SSH login while retaining key-based access.
- A passphrase can protect the private key if someone obtains its file.

## Security Considerations

- Never share or upload a private key.
- Use a strong passphrase for the private key where appropriate.
- Set correct permissions on SSH files and directories.
- Remove public keys from `authorized_keys` when access is no longer needed.
- Keep a tested alternative administrative access method before changing SSH authentication settings.
- SSH keys do not automatically prevent every brute-force attempt. Disabling password authentication can reduce password-guessing risk, but must be done carefully to avoid locking out administrators.

## Scope

This document summarizes the concept shown in the learning material. It does not claim that SSH key authentication has been configured or tested on a server.

## References

- [OpenSSH Manual Pages](https://www.openssh.com/manual.html)
- [ssh-keygen manual](https://man.openbsd.org/ssh-keygen)
- [ssh-copy-id manual](https://man.openbsd.org/ssh-copy-id)
