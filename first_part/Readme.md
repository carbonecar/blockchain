# Blockchain without transaction autentication
Each block has a function hash. This function was made using: shasum -a 256 blockX.txt
Each block contains the shasum of the previous block.

### Block 0:
Contains the balance of the 2 accounts

### Bock 1:
Contains the transaction wich tranfer some amount.


### Questions:
What happens if i try to change the balance on the first block?
Why sould i beleave that Alice realy send 100 to Bob?
