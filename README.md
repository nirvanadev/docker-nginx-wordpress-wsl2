# docker-nginx-wordpress-wsl2

## Prerequisites
1. Working WSL 2 Ubuntu
2. Docker WSL 2
3. Self-signed SSL certificate and key for localhost

## Install
1. Open a terminal using your WSL 2 Ubuntu distro and navigate to somewhere like ~/home/sites (make the directory if not present)
2. Run this `git clone https://github.com/nirvanadev/docker-nginx-wordpress-wsl2.git`
3. Then this `cd docker-nginx-wordpress-wsl2 && touch .env`
4. Now, open the .env file and add the following. Replace the values after the `=` with your own.
    ```
    MYSQL_ROOT_PASSWORD=your_root_password
    MYSQL_USER=user_name
    MYSQL_PASSWORD=user_password
    ```
5. Generate a self-signed SSL certificate
	```
	openssl req -x509 -days 365 -out localhost.crt -keyout localhost.key   -newkey rsa:2048 -nodes -sha256   -subj '/CN=localhost' -extensions EXT -config <( \
	   printf "[dn]\nCN=localhost\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:localhost\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")
	```
NOTE: Steps 5,6,7 only need to be done once and whenever the certificate expires. You can copy the certificates into other clones of this repo after completing step 7 and it should work.
6. Copy your self-signed .crt and .key files to `certs/`
7. Use IIS to add the certificate to the trusted authority
8. Finally, launch the container with `docker-compose up -d`

## Notes
- The site will be available at https://localhost
- phpMyAdmin is available at https://localhost:8000 and will use the credentials set in the .env file.
- VSCode now has seamless integration with WSL 2 and docker
