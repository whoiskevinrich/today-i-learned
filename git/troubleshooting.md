# Troubleshooting

## Couldn't load public key
If you encounter an error stating that GPG couldn't load a public key, it may be due to the key not being present in your keyring or an issue with the key file. Here are steps to troubleshoot:

```bash
> git commit ....

error: Couldn't load public key <OMITTED>: No such file or directory?

fatal: failed to write commit object

> git config --global gpg.format openpgp
> git commit ....

```

