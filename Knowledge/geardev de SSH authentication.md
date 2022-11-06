- Grab id_rsa from 1Password
- Copy to .ssh/geardev_rsa
- Adjust `.ssh/config`

```sql
Host geardev.de
    User rudolf
    IdentityFile ~/.ssh/geardev_rsa
```

Connect!

```sql
ssh geardev.de
sudo -i
```



