Skills Used - Python, Bash, HTML, CSS, JavaScript, Django, Mysql and JQuery

Features of the Project:

1) Basic Work:
We created a web-client which supports signup and login for users. It also displays all the
files uploaded by the user and allow them to download. We implemented upload through
linux client and web client, and implemented copying of the directory structure to the
database on the server.

2) Sync and Version Control:
We implemented this as a part of linux client. First, we implemented a bash function for
version control and then used it for implementation of sync. In the case of files with same
name but different content our function takes the opinion of the client whether to trust
the server’s files or his folder’s files and works accordingly. Our sync function takes care of
version control along with the syncing.

3) Encryption on linux client end:
We provide the users with 3 different options of encryption schemas(AES, DES3, and Blow-
fish). While uploading a file through the linux client, the file first gets encrypted according
to the choice of key and encryption schema and then is saved to the database on the server.
We give the user liberty to shift to a different encryption schema at any point of time
through the linux client. If this is done then the files on the server database would get
updated according to the new encryption schema.

4) Web-end Decryption and File Rendering:
On the web-end, after logging in the user has to fill the private-key and encryption schema
through an input stream. The fields entered are then stored in session storage(user has to
input key each time the webpage is opened) and are used to decrypt the file on clicking.
Clicking also leads to the file being displayed in a new window. This is done through the
post() and get() methods in jQuery.

5) File Sharing:
We have worked a lot on file sharing. We designed a new algorithm using ideas of AES and
RSA that is quite secure and compatible for large file uploads. We made some assumptions
regarding this algorithm. We gave every user 6 keys named as private key , shared key ,
schema , n, e, d where only n and e are public keys. Now lets say A wants to send a file to
B then B will upload it’s shared key to the database after encrypting it with the n and e
of A (RSA). Then A will decrypt the shared key of B using it’s d and upload the file while
encrypting it with shared key of B. B then downloads the files, decrypts them and encryptthem again with it’s private key. Here note that the private key d used for RSA of A is
known to just A as it has been encrypted and then stored. Also the shared key of B is only
passed on to A and not known by server or anyone else, hence protecting A’s data while
sharing. The major one of them being that if we want to share file between A and B then
both A and B should be online at that instance.
