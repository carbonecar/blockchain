# Blockchain with transaction autentication
Each block has a function hash. This function was made with:<br>
<li> shasum -a 256 blockX.txt <br>
Each block contains the shasum of the previous block.
Each transaction is signed by the owner of the account

RSA pair was generated using:
  ssh-keygen -b 2048 -t rsa


Since we are goin to use openssl to encrypt and decript we'll need to make some transformation for the public keygen

openssl rsa -in ~/.ssh/id_rsa -pubout > ~/.ssh/id_rsa.pub.pem

#### using openssl
For simplicity we use openssl but, as show above, you can use another tool
##### private key
openssl genrsa -out bob_privkey.pem 2048 <br>
openssl genrsa -out alice _privkey.pem 2048 <br>


Also can use -des3 param for encrypt the private key <br>

openssl genrsa -des3 -out bob_privkey.pem 2048 <br>


##### public key
Once the private key was generated we should export the public key. <br>

openssl rsa -in bob_privkey.pem -pubout -out bob_pubkey.pem <br>
openssl rsa -in alice_privkey.pem -pubout -out alice_pubkey.pem <br>


<b>Encript</b>:
cat plain.txt  | openssl rsautl -encrypt -pubin -in ~/.ssh/id_rsa.pub.pem cipher.txt

<b>Decrypt</b>:
cat cipher.txt | openssl rsautl -decrypt -inkey ~/.ssh/id_rsa

### Block 0:
Contains the balance of the 2 accounts

### Bock 1:
Contains the transaction wich tranfer some amount.
To sign the transaction we will use the PRIVATE KEY from the owner of the transaction, so anyone can verify using de his PUBLIC key.
Every transaction are sown in plain text folowed by the crypto transaction.

### Questions:
What happens if i try to change the balance on the first block?
Why sould i beleave that Alice realy send 100 to Bob?
