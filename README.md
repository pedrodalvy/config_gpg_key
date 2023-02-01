# Example with a new GPG key configuration

1 - Generate a new key
```sh
gpg --full-generate-key

# Select the following option:
 (1) RSA e RSA

# Provide a RSA length:
  4096

# Provide a time to live (0 to forever)
  0

# Provide the user name and email address...
```


2 - Show the generated key
```sh
gpg --list-secret-key --keyid-form LONG

# Output:
sec   rsa4096/gpg_key_id 2023-02-01 [SC]
```

3 - Export the public key
```sh
gpg --armor --export gpg_key_id
```

4 - Add the exported public key to GitHub

5 - Configure the git to use the key
```sh
git config --global user.signingkey gpg_key_id
```

6 - Add the following comand to ~/.bash_profile or ~/.zshrc:
```sh
export GPG_TTY=$(tty)
```

7 - Enable GPG signing for all commits and tags
```sh
git config --global commit.gpgsign true
git config --global tag.gpgSign true
```

## Optional configuration
Add a new user to GPG key

1 - Edit the GPG key
```sh
gpg --edit-key gpg_key_id

# A interactive edit mode will open

# Run the adduid command and provide the new Name and new Email to be added:
adduid

# Select the new user
uid 2

# Mark the selected user as trusted
trust

# Save the changes
save
```
