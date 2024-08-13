# Étape 1 : Utiliser une image Node.js officielle pour la construction
FROM node:18 AS build

# Créer un répertoire de travail
WORKDIR /app

# Copier le fichier package.json et installer les dépendances
COPY package.json ./
RUN npm install

# Copier le reste de l'application et la construire
COPY . .
RUN npm run build

# Étape 2 : Utiliser une image Nginx officielle pour servir l'application
FROM nginx:alpine

# Copier les fichiers construits dans le répertoire Nginx
COPY --from=build /app/build /usr/share/nginx/html

# Exposer le port 80 pour accéder à l'application
EXPOSE 80

# Démarrer Nginx
CMD ["nginx", "-g", "daemon off;"]
