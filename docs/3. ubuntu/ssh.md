# SSH 

## Create rsa key

```bash
ssh-keygen -o -t rsa -C "#comment"
```

## Remove password from ssh sessions

```bash
ssh-copy-id username@remote_host
```