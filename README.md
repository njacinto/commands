## Command line encrypt/decrypt with public/private keys:

- create private key:
```
openssl genrsa -out priv-key.pem 1024
```
- create public key:
```
openssl rsa -in priv-key.pem -out pub-key.pem -outform PEM -pubout
```
- encrypt with public key:
```
openssl rsautl -encrypt -inkey pub-key.pem -pubin -in file.txt -out file.dat
```
- decrypt with private key:
```
openssl rsautl -decrypt -inkey priv-key.pem -in file.dat -out file.txt
```


## Git ssh key:

- create key pair private/public:
```
ssh-keygen -t rsa -b 4096 -C "name@domain"
```
- start ssh agent:
```
eval "$(ssh-agent -s)"
```
- add key to agent:
```
ssh-add ~/.ssh/git_id_rsa
```
- ssh config (~/.ssh/git_id_rsa):
```
Host github.com
  IdentityFile ~/.ssh/git_id_rsa
```
