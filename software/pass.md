# To Manage Password - pass

- \$ sudo apt-get install pass
- \$ pass
- \$ pass add aws (To add new password for this aws user)
- \$ pass -c aws (Copy the password to clipboard for 45sec)
- \$ pass edit aws/aws-code-commit/devUser1
- \$ pass git add . (To move your password to - Private GIT which is encrypted)
- \$ pass git commit -m "message"
- \$ pass git push

- REF:
  - https://www.passwordstore.org/
  - https://medium.com/@johnnymatthews/terminal-based-password-manager-ab82fd8f856a

---

# Forgot Passpharse to unlock OpenPGP

- Error => gpg: decryption failed: No secret key (Now we cannot get the password, please delete all and re-initialize process)
- Remove all pass
  - $ pass rm -rf aws/ (on parent folder to remove all child)
  - $ pass rm linux/kali
- Should delete GPG a private key
  - $ gpg --list-secret-keys (to know all private keys)
  - $ gpg --delete-secret-keys <User_Name>
  - $ gpg --delete-secret-keys tsabunkar@gmail.com
  - $ gpg --delete-secret-keys "Tejas Sabunkar" (bcoz I had 2 usernames for which gpg keys were generated)
- Should delete GPG a public key
  - $ gpg --list-keys (to know all public keys)
  - $ gpg --delete-key <User_Name>
  - $ gpg --delete-key tsabunkar@gmail.com
  - $ gpg --delete-key "Tejas Sabunkar"
- Restart Key GPG Key generation process from start
  - $ gpg --full-generate-key
  - $ Select RSA and RSA
  - $ keysize is 4096 bits
  - $ valid for? (0) 0 <== Key does not expire at all
  - $ Name - tsabunkar, Email - tsabunkar@gmail.com
  - NOTE: Revocation certificate stored location -> '/home/tejas/.gnupg/openpgp-revocs.d/<file>.rev'
- Initalize Password Store
  - $ pass init tsabunkar
  - $ pass add personal/github
  - $ pass
  - $ pass -c personal/github
  - $ pass edit personal/github
  - $ pass delete personal/github
  - Now save above password to GIT
- To store all the encrupted key-value pairs in GIT remote
  - cd ~/.password-store (Only to be done 1-time at inital)
  - Create remote private repo and link this repo here (Only to be done 1-time at inital)
  - pass git add .
  - pass git commit -m "personal"
  - pass git push
