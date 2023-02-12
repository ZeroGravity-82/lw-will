
# Last Wishes - 'Will' bounded context 

An example of a hexagonal architecture project. It implements the 'Will' bounded context of the Last Wishes application. 


Quickstart
----------
To configure PhpStorm + Docker + Xdebug, please see this article: <https://blog.denisbondar.com/post/phpstorm_docker_xdebug/>

This project requires the Docker Compose plugin to be installed: <https://docs.docker.com/compose/install/linux/>

Run the following console commands before starting local development:
```bash
export HOST_USER_UID=$(id -u) && export HOST_USER_GID=$(id -g);
make init
```
