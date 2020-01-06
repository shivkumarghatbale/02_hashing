# hashing
Description &amp; implementation of various hashing techniques.

Hashes are often used in password verification, data integrity or computing the index for the string based in key in a table (i.e. from a string first compute it's hash, convert hash string to number and then this number % size of table gives us index into the table.)

A) MD5 hashing:

The MD5 hashing algorithm is a one-way cryptographic function that accepts a message of any length as input and returns as output a fixed-length digest value to be used for authenticating the original message.

The MD5 message digest hashing algorithm processes data in 512-bit blocks, broken down into 16 words composed of 32 bits each. The output from MD5 is a 128-bit message digest value.

Computation of the MD5 digest value is performed in separate stages that process each 512-bit block of data along with the value computed in the preceding stage:

The first stage begins with the message digest values initialized using consecutive hexadecimal numerical values
Each stage includes four message digest passes which manipulate values in the current data block and values processed from the previous block
The final value computed from the last block becomes the MD5 digest for that block.

MD5 is a cryptographic hash function, not to be confused with a computer science hash function.

A cryptographic hash function has 3 properties:

Easy to compute, i.e. generating hash of X is quite fast.
Practically impossible to reverse (one-way), i.e. if hash(X)=Y, no one should be able to find X based on Y alone.
Practically impossible to duplicate, i.e. if hash(X)=Y, nobody should be able to find Z, such that hash(Z)=Y as well. So it should be practically impossible to find 2 things that hash to the same thing.
Point 2 has many uses. For example, systems do not store your actual password. Instead, they store its cryptographic hash. This ensures that if a system gets hacked, your actual password is never leaked, and also that if the system admin peeked into the database, they couldn’t see your password.

Whenever you enter your password to login, again, it is hashed. If the two hashes match, then you have entered the right password. Point 3 becomes important here, only your password will hash to Y, it is practically impossible to find another password that hashes to Y, so no one else can login to your account.

They are also very useful for digest and integrity purposes. If you download a very long file (say, 2 GB) and a hacker modifies it on the fly, so that it has a virus in it, the hash of the entire file will change. So when the download is finished, you can compare the hash of your stored file, with the hash listed on the download page (many open source systems list the hash of their download files for this reason). If even 1 byte of the data is changed, hashes will be different.

Similarly, they are used for digital signatures. Instead of signing an entire long document, digital signatures are usually applied on digests. You first hash the long document into X (hash outputs are usually fixed size, e.g., 160 bit for MD5) and then sign the hash. If the document is modified by 1 byte, the hash will change, and thus the thing you signed is no longer the hash of that document.

These are just examples. Cryptographic hashes have many more uses.
