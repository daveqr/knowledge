# GPG

gpg --list-keys

gpg --import private-key.asc
gpg --import public-key.asc


git log --show-signature
git config user.signingkey
git config --global user.signingkey YOUR_GPG_KEY_ID

enable signing by default
git config --global commit.gpgsign true

to revoke
gpg --gen-revoke "Your Name" > revocation-certificate.asc
gs