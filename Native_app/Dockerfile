# Use the official Node.js image as the base image
FROM node:18

# Install Android SDK and other necessary tools
RUN apt-get update && \
    apt-get install -y openjdk-11-jdk curl unzip && \
    curl -sSL https://dl.google.com/android/repository/commandlinetools-linux-7583922_latest.zip -o android-sdk.zip && \
    unzip android-sdk.zip -d /sdk && \
    rm android-sdk.zip && \
    yes | /sdk/cmdline-tools/bin/sdkmanager --licenses && \
    /sdk/cmdline-tools/bin/sdkmanager "platform-tools" "platforms;android-30" "build-tools;30.0.3"

# Set environment variables for Android SDK
ENV ANDROID_HOME=/sdk
ENV PATH=$PATH:/sdk/platform-tools

# Set the working directory
WORKDIR /app

# Copy package.json and yarn.lock/npm package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port for the React Native Metro bundler
EXPOSE 8081

# Start the Metro Bundler
CMD ["npm", "start"]
