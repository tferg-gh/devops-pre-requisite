#### Generate a private key
```
openssl genrsa -out my-bank.key 2048
```

#### Generate a public key
```
openssl rsa -in my-bank.key -pubout > my-bank.pem
```
Uses the private key generated above

#### Generate a CSR
```
openssl req -new -newkey rsa:2048 -nodes -keyout app01.key -out app01.csr
```
The -new argument generates a new key and -keyout is the private key / new key name

#### Sign a certificate
```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout app01.key -out app01.crt
```

Note: you will be asked for further information E.g.

a. Country Name = `SG`

b. State or Province Name = `Capital Tower`

c. Locality Name = `CT`

d. Organization Name = `KodeKloud`

e. Organizational Unit Name = `Education`

f. Common Name = `app01.com`

g. Email Address = `admin@kodekloud.com`