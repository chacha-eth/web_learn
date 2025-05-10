# Setting Up SSH for GitHub

## **Step 1: Check for Existing SSH Keys**
Run the following command to see if you already have an SSH key:

```bash
ls -al ~/.ssh
```

If you see files like `id_rsa.pub` or `id_ed25519.pub`, you already have an SSH key. If not, proceed to **Step 2**.

---

## **Step 2: Generate a New SSH Key**
If you don’t have an SSH key, create one:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

- Replace **your_email@example.com** with your GitHub email.
- Press **Enter** to accept the default save location (`~/.ssh/id_ed25519`).
- If prompted, enter a passphrase (optional but recommended).

Verify that the key was created:

```bash
ls -al ~/.ssh
```

You should see files like `id_ed25519` and `id_ed25519.pub`.

---

## **Step 3: Add SSH Key to GitHub**
Copy the **public key**:

```bash
cat ~/.ssh/id_ed25519.pub
```

1. Copy the entire output.
2. Go to **GitHub** → [SSH Keys Settings](https://github.com/settings/keys).
3. Click **"New SSH Key"**.
4. **Title**: Give it a recognizable name (e.g., "My Laptop SSH Key").
5. **Key**: Paste the copied public key.
6. Click **"Add SSH Key"**.

---

## **Step 4: Add SSH Key to ssh-agent**
Run:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Now, test the SSH connection:

```bash
ssh -T git@github.com
```

If successful, you should see:

```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## **Step 5: Try Cloning or Pushing Again**
Now, try cloning or pushing to your repository:

```bash
git clone git@github.com:your-username/repository.git
```

If you still face issues, double-check your SSH key setup and GitHub settings!

---

## **Bonus: Check Your Git Email and Username**
Check your configured Git email:

```bash
git config --global user.email
```

Set a new email if needed:

```bash
git config --global user.email "your_email@example.com"
```

Check your Git username:

```bash
git config --global user.name
```

Set a new username if needed:

```bash
git config --global user.name "Your Name"
```

