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
