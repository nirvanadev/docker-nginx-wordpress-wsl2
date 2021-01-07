# docker-nginx-wordpress-wsl2

## Prerequisites
1. Working WSL 2 Ubuntu
2. Docker WSL 2
3. Self-signed SSL certificates for localhost

## Install
1. Open a terminal using your WSL 2 Ubuntu distro and navigate to somewhere like ~/home/sites (make the directory if not present)
2. Run this `git clone https://github.com/nirvanadev/docker-nginx-wordpress-wsl2.git`
3. Then this `cd docker-nginx-wordpress-wsl2 && touch .env`
4. Now, open the .env file and add the following:
    ```MYSQL_ROOT_PASSWORD=your_root_password
    MYSQL_USER=user_name
    MYSQL_PASSWORD=user_password
    ```
    Replace the values after the `=` with some custom ones
5. Copy your self-signed .crt and .key files to `certs/`
5. Finally, launch the container with `docker-compose up -d`

## Notes
- The site will be available at https://localhost
- phpMyAdmin is available at https://localhost:8000 and will use the credentials set in the .env file.
- VSCode now has seamless integration with WSL 2 and docker
