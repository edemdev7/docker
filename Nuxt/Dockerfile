# Étape 1 : Utiliser une image Node.js officielle
FROM node:18 AS build

# Créer un répertoire de travail
WORKDIR /app

# Copier le fichier package.json et installer les dépendances
COPY package.json ./
RUN npm install

# Copier le reste de l'application et la construire
COPY . .
RUN npm run build

# Étape 2 : Exécuter Nuxt.js en mode production
CMD ["npm", "run", "start"]

# Exposer le port 3000 pour accéder à l'application
EXPOSE 3000