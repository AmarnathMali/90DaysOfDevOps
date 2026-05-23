

SSH authentication is how a server checks that you’re really the person trying to connect. You can log in with a password, or more securely with a key pair: a private key on your computer and a public key saved on the server. When you connect, the server uses the public key to test you, and your private key proves your identity.







🔑 SSH Authentication Methods

Password authentication



You type a password to log in.



Simple but less secure (susceptible to brute force attacks).



Public key authentication



Uses a key pair:



Private key: stays on your computer, must be kept secret.



Public key: stored on the server in \~/.ssh/authorized\_keys.





\----------------------------------------------------------------

ssh connection between two server



server-a                     server-b



to connect server-b, server-a should have private-key of server-b, and server-b should have public-key

\----------------------------

0\. ssh-keygen used in server b to generate key-pair.

1. in server-a created .pem file
2. paste private-key of the server-b in this newly created .pem file
3. then try establishing connection  **ssh -i server-b-key.pem ubuntu@18.60.107.155**
4. got error: permission denied(public key)
5. did this only read permission for this file: chmod 400 server-b-key.pem
6. still got error:  Permission denied (publickey).
7. due to authorized key , authorized-key contains key which try to match private key
8. pasted the public key into authorized-key
9. after connection got succeeded.
10. Asymmetric Encryption: initial key exchange
11. Symmetric Encryption: it is uses 2nd time onwards to connect .



