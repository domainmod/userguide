Encrypted Database Connections
------------------------------
DomainMOD can encrypt its connection to your database with TLS, and check the database server's certificate so that nobody on the network can read or change your data along the way.

If your database runs on the same server as DomainMOD (for example, `$dbhostname` is `localhost`), the connection never crosses the network and you don't need to change anything. If your database is on a different server, or is reached over a network you don't fully trust, you should use the `verify` setting below.

<a name="modes"></a>Settings
--------
The connection is controlled by two optional settings in `_includes/config.inc.php`.

**$dbsslmode**

`'auto'` (the default)  
DomainMOD connects the same way it always has, and only uses an encrypted connection if the database server requires one. This encrypted connection doesn't check the server's certificate, so it **doesn't** protect you from an attacker on the network.

`'verify'`  
DomainMOD always encrypts the connection and checks the server's certificate. If the certificate can't be checked, DomainMOD won't connect. Use this whenever your database is on a different server than DomainMOD, or is reached over an untrusted network.

`'off'`  
DomainMOD never encrypts the connection.

**$dbsslca**

For `'verify'` only, the path to the file containing the certificate of the Certificate Authority (CA) that signed your database server's certificate. If you leave it out, DomainMOD uses your system's trusted CA file: the one set by `openssl.cafile` in php.ini, then the `SSL_CERT_FILE` environment variable, then OpenSSL's default CA file. CA directories (such as `openssl.capath`) aren't used, so if your trusted CAs are only in a directory, point `$dbsslca` at a CA file instead.

Database providers that sign their certificates with their own CA, such as Amazon RDS, need their CA bundle saved on your server and `$dbsslca` pointed at it. For Amazon RDS, see [Using SSL/TLS to encrypt a connection to a DB instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.SSL.html).

<a name="setup"></a>Turning On Certificate Checking
-------------------------------
1. Make sure your database server has TLS enabled with a certificate.

2. Make sure `$dbhostname` in `_includes/config.inc.php` matches the name on the database server's certificate.

3. Add the following line to `_includes/config.inc.php`:

        $dbsslmode = 'verify';

4. If your database server's certificate is signed by its own CA rather than one in your system's trusted CA file, save the CA file on your server and add a line pointing at it:

        $dbsslca = '/path/to/ca.pem';

5. Load DomainMOD in your browser. If it can't connect, the error message will tell you that the certificate couldn't be checked. Check the two settings above, and that the CA file can be read by your web server.

<a name="status"></a>Checking the Connection
-----------------------
You can see how DomainMOD is connected to your database by going to *Administration -> System Information* and looking at **Database Connection**. It will show one of the following:

**Encrypted (certificate checked)**  
The connection is encrypted and the server's certificate was checked. This is what you want to see if your database is on a different server.

**Encrypted (certificate not checked)**  
The connection is encrypted, but the server's certificate wasn't checked, so it isn't protected from an attacker on the network.

**Not encrypted**  
The connection isn't encrypted.
