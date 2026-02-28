# GitHub SSH Setup Guide

If you see this error when trying to push:

```
remote: Invalid username or token. Password authentication is not supported for Git operations.
fatal: Authentication failed for 'https://github.com/...'
```

it means your repository is using **HTTPS authentication**, which GitHub no longer supports with passwords.

The solution is to use **SSH authentication** instead.

---

## 1. Generate an SSH Key (if you don't have one)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Press Enter to accept the default file location.

Your public key will be located at:

```
~/.ssh/id_ed25519.pub
```

---

## 2. Add the SSH Key to GitHub

Copy your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Then go to:

GitHub → Settings → SSH and GPG Keys  
https://github.com/settings/keys  

Click **"New SSH Key"** and paste your key.

---

## 3. Test SSH Authentication

```bash
ssh -T git@github.com
```

You should see:

```
Hi <your-username>! You've successfully authenticated, but GitHub does not provide shell access.
```

This confirms SSH is working correctly.

---

## 4. Check Your Remote URL

Run:

```bash
git remote -v
```

If you see something like:

```
https://github.com/username/repository.git
```

then your repository is using HTTPS and must be switched to SSH.

---

## 5. Switch Remote to SSH

```bash
git remote set-url origin git@github.com:username/repository.git
```

Verify the change:

```bash
git remote -v
```

You should now see:

```
git@github.com:username/repository.git
```

---

## 6. Push Your Code

```bash
git push
```

Your push should now succeed without authentication errors.

---

## Why This Happens

GitHub no longer supports password authentication for Git operations over HTTPS.  
SSH authentication is the recommended secure method.

---

## If Authentication Still Fails

Make sure the SSH agent is running and your key is added:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

## Done 🎉

You can now safely push, pull, and clone repositories using SSH.

