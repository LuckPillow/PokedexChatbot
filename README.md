# Pokédex with Chatbot

> This project is an enhanced version of the traditional Pokédex, designed to assist new trainers on their Pokémon journey.

![Bulbasaur](https://raw.githubusercontent.com/LuckPillow/erm-project/refs/heads/main/pokemon/1.png)
![Charmander](https://raw.githubusercontent.com/LuckPillow/erm-project/refs/heads/main/pokemon/4.png)
![Squirtle](https://raw.githubusercontent.com/LuckPillow/erm-project/refs/heads/main/pokemon/7.png)

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
  - [Setting up Visual Studio Code](#setting-up-visual-studio-code)
  - [Setting up MySQL 8.0](#setting-up-mysql-80)
  - [Setting up the AI Chatbot](#setting-up-the-ai-chatbot)
- [Features](#features)
  - [Encyclopedia](#encyclopedia)
  - [LearnSets](#learnsets)
  - [Habitats](#habitats)
  - [Chatbot](#chatbot)
  - [Pokémon Catcher](#pokémon-catcher)

---

### <span style="color: Yellow">Introduction

This project expands upon the classic Pokédex, providing trainers with an interactive and feature-rich tool. It includes a built-in AI chatbot to answer questions, suggest strategies, and offer insights about Pokémon in real time.

![Pikachu](https://raw.githubusercontent.com/LuckPillow/erm-project/refs/heads/main/pokemon/25.png)
---

### <span style="color: Yellow"> Installation

Follow these steps to set up the project:

# Setting up Visual Studio Code

1. Download and install [Visual Studio Code](https://code.visualstudio.com/).
2. Open the project folder in Visual Studio Code.

# Setting up MySQL 8.0

1. Download and install [MySQL 8.0](https://dev.mysql.com/downloads/mysql/).
2. Configure your database by following the setup instructions, creating necessary tables and entries for Pokémon data.

# Setting up Node Js
1. Download and install [NodeJs](https://nodejs.org/en).
2. Open Windows Powershell as admin
3. Enter the command (Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned)
4. Once the prompt to change the execution policy appears Type (A) Yes to all, then Enter.

#### Step 1: Create Your Database

> **Note:** For testing purposes, it's recommended to create a new database.

Run the following commands in your MySQL interface:

```sql
CREATE DATABASE pokemon_app;
USE pokemon_app;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL
);

CREATE TABLE pokemon (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    name VARCHAR(50) NOT NULL,
    type VARCHAR(50),
    level INT,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

#### Step 2: Generate a JWT Secret Key

1. Create a new `.js` file (e.g., `generateKey.js`).
2. Add the following code to generate a secret key:

   ```javascript
   const crypto = require('crypto');
   const jwtSecret = crypto.randomBytes(64).toString('hex');
   console.log(jwtSecret);
   ```
3. Run the file using Node.js:

   ```
   node "placeholdername.js"
   ```



#### Step 4: Update Your Credentials in `app.js`

Edit the `app.js` file to replace placeholders with your own credentials, such as your MySQL password, JWT secret key, and database name (if you're using a test database). Don't forget this is just the snippet.

Here is an example `app.js`:

```javascript
const express = require('express');
const mysql = require('mysql');
const bcrypt = require('bcryptjs');
const jwt = require('jsonwebtoken');
const cors = require('cors'); // Import cors

const app = express();
app.use(express.json());

app.use(cors());

const db = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'YOUR_PASSWORD', // Replace with your MySQL password
    database: 'pokemon_app'// (Replace this if you are testing)
});

db.connect(err => {
    if (err) throw err;
    console.log('Connected to MySQL');
});

// Replace this with your generated JWT secret key
const jwtSecret = 'YOUR_GENERATED_SECRET_KEY';
```
#### Step 5: Run the Application

To start the application, type:

```
node app.js
```

Then, run it on your live server.

Troubleshooting
If you experience issues with MySQL, run the following commands in your MySQL query interface:

```SQL
ALTER USER 'your_username'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';
FLUSH PRIVILEGES;
```
```kotlin
Replace 'your_username' and 'your_password' with your MySQL username and password.
```

# Setting up the AI Chatbot

1. Ensure you have Python installed. If not, download it [here](https://www.python.org/downloads/).

2. Ensure you have Visual Studio Code. If not, download [Visual Studio Code](https://code.visualstudio.com).

---

#### Getting Your Gemini AI API Key

1. Visit [Google AI Studio](https://ai.google.dev) and click **"Get API key in Google AI Studio"**.
2. You will be redirected to [API Key Creation](https://aistudio.google.com/app/apikey).
3. Click **"Create API key"**, and a pop-up will appear to let you select a Google Cloud Project.
4. Choose your desired project, and your key will be generated.

**Note:** Do **NOT** share your API key with anyone.

---

#### Setting Up the AI Chatbot

1. Download all the files and move them to your preferred directory.
2. Open **Visual Studio Code**.
3. Navigate to `backend/.env`.
4. Replace `"your_api_key_here"` with your generated API Key (without quotes).
5. Open the terminal in Visual Studio Code, ensuring the path is set to `/chatbot`.

---

#### Downloading Dependencies

In the `/chatbot` terminal path of Visual Studio Code, enter the following commands to install required dependencies:

```Terminal

npm init -y

npm install express mysql bcryptjs jsonwebtoken

npm install cors

npm install express mysql2

python -m pip install --upgrade pip

pip install flask

pip install python-dotenv

pip install google-generativeai

python -m venv venv

venv\Scripts\activate

```

---

#### Starting up the Webpage

You have three ways to start up the webpage:

1. Right click the `/backend` folder and open in terminal and input the following line in the terminal: `python app.py`
2. Navigate to the path of the `/backend` folder through cd backend and input the following line in the terminal: `python app.py`
3. Input the following line in the terminal `python backend/app.py`

---

![Mew](https://raw.githubusercontent.com/LuckPillow/erm-project/refs/heads/main/pokemon/151.png)
### <span style="color: Yellow"> **Features**

Features included in the project website 

- #### <span style="color: LightGreen"> **Encyclopedia📖**
   - The website's encyclopedia includes an overview of Generation 1 Pokémons that appear within the initial games, *FireRed*🔥 and *LeafGreen*🍃, both releasing in 2004 as remakes of the renowned Generation 1 games

- #### <span style="color: LightGreen">**LearnSets✨**
  - As the website introduces the different Pokémons, it also showcases the possible abilities or movesets that each of them can possess. This also includes a brief description of that ability when clicked on.

- #### <span style="color: LightGreen">**Habitats🌲**
  - This part of the website reveals the location of Pokémons, which can help players in learning how to find and caputure specific Pokémons.

- #### <span style="color: LightGreen">**ChatBot💬**
  - The Chatbot of the website includes an Aritificially Intelligent chatting system that takes the role of Proffesor Oak. This system aims to assist users in answering various questions with real time responses.

- #### <span style="color: LightGreen">**Pokémon Catcher**
  - In this part of the website, the user can take records of their currently captured Pokémons, easing the user experience in keeping track of their Pokémons.




### 🌟 **Embark on Your Pokémon Adventure with Confidence!** 🌟

---

Thank you for exploring the **Pokédex with Chatbot!** 🎉 

This enhanced Pokédex is designed to be more than just your regular Pokédex it’s your **reliable tool** in the world of Pokémon. With **real-time insights**, a **friendly chatbot** to answer your questions, and tools to help you **track and strategize**, this project brings the Pokémon experience to life like never before.


### **Whether you're a seasoned trainer or just starting out,**  
we hope this Pokédex empowers you to dive deeper into the world of Pokémon, catch ‘em all, and become the very best! 🏆


### **Happy training, and may every encounter be extraordinary!** 🎒⚡
