# Docker Compose

## Commands

```bash
# start up containers defined in docker-compose-dev.yml and use 'myproject' as container prefix
docker-compose -p myproject -f docker-compose-dev.yml up
# same as above, but detach from stdin / stdout
docker-compose -p myproject -f docker-compose-dev.yml up -d
```

## docker-compose.yml

```yml
version: "3"

services:
  mysql:
    image: mysql:5
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
    volumes:
      - mysql-data:/var/lib/mysql
    networks:
      net:
        aliases:
          - db

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    ports:
      - 80:80
    networks:
      - net

networks:
  net:

volumes:
  mysql-data:
```
