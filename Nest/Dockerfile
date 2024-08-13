# Utiliser l'image Node.js officielle comme image de base
FROM node:18

# Définir le répertoire de travail dans le conteneur
WORKDIR /app

# Copier les fichiers package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances de l'application
RUN npm install

# Copier le reste des fichiers de l'application dans le conteneur
COPY . .

# Exposer le port que l'application utilise
EXPOSE 3000

# Commande pour démarrer l'application
CMD ["npm", "run", "start:prod"]
