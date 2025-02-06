# 🐳 Docker Compose - Running Multiple Docker Containers

### 🛠️ Technologies Used:
1. Docker
2. MongoDB
3. MongoExpress

## ✅ Prerequisites:
1. Docker installed on your local computer to download images and run containers.
2. This guide continues from another [repository](https://github.com/Allon-chauhan/docker-js-node-mongo.git). Make sure to review it for the initial setup.
3. Download the sample Node.js code from [here](https://gitlab.com/twn-devops-bootcamp/latest/07-docker/js-app.git).

### 📝 Creating a Docker Compose File
1. In any directory, create a YAML file - I named it `docker-mongo.yaml`.
2. Enter the following in the YAML file:
   ```yaml
   version: '3'
   services:
     mongodb:
       image: mongo:latest
       ports:
         - 27017:27017
       environment:
         - MONGO_INITDB_ROOT_USERNAME=admin
         - MONGO_INITDB_ROOT_PASSWORD=password
     mongoexpress:
       image: mongo-express:latest
       ports:
         - 8081:8081
       restart: always
       environment:
         - ME_CONFIG_MONGODB_ADMINUSERNAME=admin
         - ME_CONFIG_MONGODB_ADMINPASSWORD=password
         - ME_CONFIG_MONGODB_SERVER=mongodb
   ```

### 🚀 Initiating Docker Compose File
1. After creating and saving the `docker-mongo.yaml` file,
2. Open the terminal and navigate to the directory where `docker-mongo.yaml` is saved.
3. Run the following command:
   ```bash
   docker compose -f docker-mongo.yaml up
   ```

⚠️ **IMPORTANT:** 🚨 Ensure you are in the correct directory before running the command. 🚨

### 🟢 Starting the Node.js Server
1. On your local computer, make sure you're in the app directory. Use this command to confirm:
   ```bash
   pwd
   ```
2. Set up npm:
   ```bash
   npm install
   ```
3. Start the server:
   ```bash
   node server.js
   ```
4. Open your browser and navigate to:
   ```
   http://localhost:3000
   
