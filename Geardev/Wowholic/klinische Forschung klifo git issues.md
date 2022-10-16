```swift
ssh -l opusmarketing -p 22008 151.106.72.108

cd /data/klinischeforschung/production

sudo -u apache git fetch --all

sudo -u apache git stash --include-untracked

# sudo -u apache git checkout v.1.1.400
sudo -u apache git checkout master

sudo -u apache git stash apply

sudo -u apache git add .
sudo -u apache git commit -m "Update internal files"
```

```swift
git reflog
fef9300 HEAD@{0}: commit: Update Wordpress internal files
1b2a972 HEAD@{1}: rebase finished: returning to refs/heads/master
1b2a972 HEAD@{2}: checkout: moving from master to 1b2a972b167f0ed18f5ba4976232c9c7bcfa5fce^0
f867226 HEAD@{3}: commit: Update Wordpress internal files
6cdad1c HEAD@{4}: checkout: moving from 1b2a972b167f0ed18f5ba4976232c9c7bcfa5fce to master
1b2a972 HEAD@{5}: checkout: moving from master to v.1.1.400
6cdad1c HEAD@{6}: checkout: moving from master to master
```

Where are the keys?

```swift
ls /usr/share/httpd/.ssh
sudo -u apache cp /data/klinischeforschung/production/id_rsa /usr/share/httpd/.ssh/id_rsa
sudo -u apache chmod 600 /usr/share/httpd/.ssh/id_rsa

git config core.sshCommand 'ssh -i /data/home/opusmarketing/.ssh/id_rsa -o IdentitiesOnly=yes'

/data/home/opusmarketing
GIT_SSH_COMMAND='ssh -i private_key_file -o IdentitiesOnly=yes' git

~/.ssh/id_rsa.pub

sudo -u apache GIT_SSH_COMMAND='ssh -i /data/home/opusmarketing/.ssh/id_rsa -o IdentitiesOnly=yes' git fetch --all
GIT_SSH_COMMAND='ssh -i /data/home/opusmarketing/.ssh/id_rsa -o IdentitiesOnly=yes' sudo -u apache git fetch --all
```

## Redirect

Tobi has weird SSL cert revoked error message?

Novartis uses load balancer

Alle Subdomains umleiten auf /shortlink/whatever

shortlink is handled in



