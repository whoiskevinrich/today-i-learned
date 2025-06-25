# Updating cache duration for GPG keys

## GnuPG 2.1 and above
In GnuPG 2.1 and above, the maximum-cache-ttl option was renamed to max-cache-ttl without further changes.

```bash
default-cache-ttl 34560000
max-cache-ttl 34560000
```

## GnuPG 2 and below
```bash
default-cache-ttl 34560000
maximum-cache-ttl 34560000
```

## Restart the agent
For changes to take effect, the session must be ended by restarting gpg-agent.

```bash
gpgconf --kill gpg-agent
gpg-agent --daemon --use-standard-socket
```

Source: https://superuser.com/a/624488/462011