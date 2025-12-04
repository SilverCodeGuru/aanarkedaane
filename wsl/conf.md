# conf file

windows drives are automounted.

you can add an automount section and set enabled to false and then your wsl will not have /mnt/c directory

```text
[automount]
enabled = false
```
