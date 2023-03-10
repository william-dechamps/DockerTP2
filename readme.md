### Exercice 1

Compléter le Dockerfile afin de builder correctement l’application contenu dans src/

```
FROM node:12-alpine3.9

COPY ./src ./src
COPY ./package.json .

RUN npm install --omit=dev

CMD ["node", "src/index.js"]
```

**a**. Une option de npm vous permet de n’installer que ce qui est nécessaire. Quelle est cette option ?

```
Il est possible d'utiliser l'otion "--omit" pour éviter d'installer les packages qui ne sont pas nécessaires pour l'exécution de l'application (devDependencies).
```

Quelle bonne pratique Docker permet t-elle de
respecter ?

```
Construire une image la plus allégée possible.
```

### Exercice 2

A l’aide de la commande docker build, créer l’image ma_super_app  
`docker build -t ma_super_app .`

### Exercice 3

Compléter le fichier docker-compose.yml afin d’éxécuter ma_super_app avec sa
base de données.

```
version: "3.9"

services:
  node:
    container_name: node
    build:
      context: .
      dockerfile: ./Dockerfile
      tags:
        - my_super_app:1.0.0
    depends_on:
      - mysql
    ports:
      - 3000:3000
    env_file:
      - .env

  mysql:
    container_name: mysql
    image: mysql:5.7
    ports:
      - 3306:3306
    environment:
      MYSQL_DATABASE: ${DATABASE_NAME}
      MYSQL_USER: ${DATABASE_USERNAME}
      MYSQL_PASSWORD: ${DATABASE_PASSWORD}
      MYSQL_ROOT_PASSWORD: ${DATABASE_PASSWORD}
```
