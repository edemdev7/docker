# Étape 1 : Utilisation une image Node.js officielle
FROM node:18 AS build

# Créaton d'un répertoire de travail
WORKDIR /app

# Copie du fichier package.json et installation les dépendances
COPY package.json ./
RUN npm install

# Copie du reste de l'application et la construire
COPY . .
RUN npm run build

# Étape 2 : Exécution de  Next.js en mode production
CMD ["npm", "start"]

# Exposition du port 3000 pour accéder à l'application
EXPOSE 3000