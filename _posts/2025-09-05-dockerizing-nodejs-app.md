---
layout: post
title: Dockerizing NodeJS Application
tags: [container, docker, nodejs, javascript]
cover-img: /assets/img/docker-nodejs-cover.png
comments: true
---

Deploying a Node.js application often comes with the challenge of environment differences. Docker helps solve this by providing a consistent environment across development, testing, and production. In this tutorial, we’ll containerize a simple Node.js application and run it seamlessly on any platform—whether on a local machine, server, or the cloud.

### Prerequisites

Before getting started, make sure you have the following installed on your machine:

- **Node.js** – Installed locally (this guide uses Node.js v22, but any recent LTS version works).
- **Docker Desktop** – Ensure Docker Engine is running properly.
- **VS Code or any code editor of your choice** – For writing and editing the application code.

---

### Step 1: Create the Project Folder

Let’s start by creating a dedicated folder for our application. Open your terminal and run:

```bash
mkdir dockerize-node-app
cd dockerize-node-app
```

This will create a new directory named **dockerize-node-app** and navigate into it, where we’ll build our Node.js application.

---

### Step 2: Initialize the Node.js Application

Inside the **dockerize-node-app** folder, initialize a new Node.js project by running:

```bash
npm init -y
```

This will create a package.json file with default settings.

---

### Step 3: Install Express

We’ll use Express to create a simple web server. Install it with:

```bash
npm install express
```

---

### Step 4: Create the Application File

Create a file named index.js in the project folder and add the following code:

```javascript
const express = require("express");
const app = express();
const PORT = 3000;

app.get("/", (req, res) => {
  res.send("Hello, Dockerized Node.js App!");
});

app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```

---

### Step 5: Run the Application Locally

Start the application by running:

```bash
node index.js
```

Now open your browser and visit:

👉 <http://localhost:3000>

You should see:

```
Hello, Dockerized Node.js App!
```

---

> 🔹 Note: At this point, the application is running only on your local Node.js environment. We haven’t Dockerized it yet — that’s what we’ll do in the next steps.

---

### Step 6: Create a Dockerfile

In the root of your dockerize-node-app folder, create a file named Dockerfile (no extension).
This file will define how our Node.js application will be built and run inside a container.

Add the following content:

```dockerfile
# Use official Node.js LTS image as base
FROM node:22-alpine

# Set working directory inside container
WORKDIR /app

# Copy package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Expose the application port
EXPOSE 3000

# Command to run the app
CMD ["node", "index.js"]
```

---

### Step 7: Create a .dockerignore File

Just like .gitignore, a .dockerignore file tells Docker which files and folders to exclude when building the image.

Create a file named .dockerignore in the root folder and add:

```
node_modules
npm-debug.log
Dockerfile
.dockerignore
.git
.gitignore
```

This prevents unnecessary files (like node_modules) from being copied into the image, keeping it clean and lightweight.

---

### Step 8: Build the Docker Image

With the Dockerfile and .dockerignore in place, you can now build your Docker image.
Run the following command in the root of your project:

```
docker build -t dockerize-node-app .
```

- **-t dockerize-node-app** gives your image a name (or “tag”).
- (**.**) tells Docker to use the current directory as the build context.

Once the build is complete, verify the image exists by running:

```
docker images
```

You should see **dockerize-node-app** in the list.

---

### Step 9: Run the Docker Container

Now let’s run the app inside a container:

```
docker run -p 3000:3000 dockerize-node-app
```

- **-p 3000:3000** maps container port 3000 to host port 3000, so you can access the app from your browser.
- **dockerize-node-app** is the name of the image you built.

---

<div style="position: relative; width: 100%; padding-bottom: 56.25%">
<iframe src="https://www.youtube.com/embed/Dj71VBlgU74?si=iJOzm7dcPwqG5fNA" 
        title="Dockerize NodeJS App Demo" frameborder="0" allowfullscreen
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
        style="position: absolute; width: 100%; height: 100%;">
</iframe>
</div>

You can find the full source code for this tutorial on GitHub:
👉 [dockerize-node-app](https://github.com/EstopaceMA/dockerize-node-app)

---

In this guide, we built a simple Node.js application and learned how to containerize it using Docker.
We went through the process of:

- Creating a Node.js app and running it locally.
- Writing a Dockerfile and .dockerignore to define the container setup.
- Building and running the app inside a Docker container.

By Dockerizing your Node.js application, you now have a portable and consistent environment that can run anywhere—on your machine, a server, or the cloud.

🚀 Next Steps: The next stage of this journey is deploying the containerized Node.js application to **Azure Container Apps**, where it can scale automatically and integrate with other Azure services.
