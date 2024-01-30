# Generating a GPG key

### Supported GPG key algorithms: 

GitHub supports several GPG key algorithms. If you try to add a key generated with an unsupported algorithm, you may encounter an error.

- RSA
- ElGamal
- DSA
- ECDH
- ECDSA
- EdDSA

### Generating a GPG key: 

**Step 1:** Open Terminal

**Step 2:** Generate a GPG key pair, use the command `gpg --full-generate-key` to generate a GPG key pair.
```nginx
gpg --full-generate-key
```

**Step 3:** At the prompt, specify the kind of key you want, or press Enter to accept the default.

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/ahuav64ql4HQBCTQ-image.png)

**Step 4:** At the prompt, specify the key size you want, or press Enter to accept the default. Maximum bits are recommended. In this case 4096

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/03KToA2VlnrfQPXX-image.png)

**Step 5:** Enter the length of time the key should be valid. Press Enter to specify the default selection, indicating that the key doesn't expire. Unless you require an expiration date.

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/feGSJE4gj08rSXFw-image.png)

After selecting the time, the key should be valid to ‘`0`’, enter ‘`y`’ to continue. We can give the length of time to the number of weeks, months, and years for our gpg.

Here we have given a one-year valid time for our gpg key after confirming with ‘`1y`’ press enter. As shown in the image below, it will display the exact expiry date and time for our newly generated gpg key.

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/3MQKyCPISAAjiJMz-image.png)

 **Step 6:** Enter your user ID information like email and git username to verify your identity.

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/ArFxi0GxJzzRJM45-image.png)

**Note:** Ensure that your email is verified in your GitHub account. Refer to the link [Verifying your email address ](https://docs.github.com/en/get-started/signing-up-for-github/verifying-your-email-address)

**Step 7:** Type a secure passphrase.

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/ffjI5lOqgb9jjIU0-image.png)

If you set a password you need to enter your password whenever you made a commit.
If you do not want to set a password keep it empty and press enter or ok.

**Step 8:** Use the `gpg --list-secret-keys --keyid-format=long` command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.
```nginx
gpg --list-secret-keys --keyid-format=long
```

**Step 9:** From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is `64D884ABBF2C1D27`.

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/NKzYHNOe1FLfqZs0-image.png)

**Step 10:** Paste the text below, substituting the GPG key ID you'd like to use. In this example, the GPG key ID is `64D884ABBF2C1D27`:

```nginx
gpg --armor --export 64D884ABBF2C1D27
```

 The above command will prints the GPG key ID, in ASCII armor format

**Step 11:** Copy your GPG key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK------` and ending with `-----END PGP PUBLIC KEY BLOCK------`.

**Step 12:** Refer the given link to add a GPG key to your GitHub account. [Adding a GPG key to your GitHub account ](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)

# Telling Git about your signing key

**Step 1:** Open Terminal

**Step 2:** Use the `gpg --list-secret-keys --keyid-format=long` command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.

```nginx
gpg --list-secret-keys --keyid-format=long
```

**Step 3:** From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is `64D884ABBF2C1D27`:

![image.png](https://atlas.i.camp/uploads/images/gallery/2023-07/scaled-1680-/MWYiAdItxOjzyaCt-image.png)

  
**Step 4:** To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID `64D884ABBF2C1D27`:  
```nginx
git config --global user.signingkey 64D884ABBF2C1D27
```

**Step 5:** To configure Git to sign all commits by default, enter the following command:

```nginx
git config --global commit.gpgsign true
```
