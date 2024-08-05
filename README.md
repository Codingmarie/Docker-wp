Docker set up

https://docs.docker.com/compose/install/

[Search docker.com](https://www.docker.com/) click on get started to download

•Create docker Account 

•terminal run `docker version` - can also use docker in terminal

• to test docker if working fine https://hub.docker.com/_/hello-world 

• click copy docker pull hello-world in run on terminal

• run: `docker images`

• run: `docker` +tab

• run: `docker run hello-world`

• output: Hello from Docker! docker working fine.

• `docker ps` to see the running container and `docker ps -a` to see the previous running 

# -**Cleaning workplace** -

•`docker images`  (list images)

•`docker ps`   (list containers)

•`docker image` ls (get all images)

•`docker image ls -q` (images id)

### to remove the images remove the containers first

•`docker container rm -f $(docker container ls -a -q)` —(force remove the container)

•`docker image rm -f $(docker image ls -q)`——(remove the images)

# Use Docker in Project

•Create a file name (docker-compose.yml)

• run the (`docker-compose up`) to download all the dependency needed

-To create your directory file for the WordPress project, follow these steps:

1. Open Terminal:
    - You can find Terminal in Applications > Utilities, or use Spotlight (Cmd + Space) and type "Terminal"
2. Navigate to where you want to create your project:
    - For example, to create it in your Documents folder, type:
    `cd ~/Documents`
3. Create a new directory for your WordPress project:
    - Type the following command and press Enter:
    `mkdir wordpress-project`
4. Move into the new directory:
    - Type:
    `cd wordpress-project`
5. Create the docker-compose.yml file:
    - Type:
    `touch docker-compose.yml`
    
    •yaml
    
    set .yml what you want to run in docker.
    
    ```
    version: '3.8'
    
    services:
      wordpress:
        image: wordpress:latest
        ports:
          - "8000:80"
        volumes:
          - ~/my-wordpress:/var/www/html
        environment:
          WORDPRESS_DB_HOST: db:3306
          WORDPRESS_DB_NAME: wordpress
          WORDPRESS_DB_USER: wordpress
          WORDPRESS_DB_PASSWORD: wordpress
        depends_on:
          - db
    
      db:
        image: mysql:8.0
        volumes:
          - db_data:/var/lib/mysql
        environment:
          MYSQL_ROOT_PASSWORD: root
          MYSQL_DATABASE: wordpress
          MYSQL_USER: wordpress
          MYSQL_PASSWORD: wordpress
    
    volumes:
      db_data:
    
    
    ### •Run: docker compose up -d (to install/pull all the dependency)


# Building Images

`docker-compose build`

**Rebuild and Start Containers**:

```jsx
docker compose up -d --build

```

To see the latest re build

`docker compose build --no-cache`

`docker ps` to map the ports
