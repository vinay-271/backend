# Apr 22, 2025

-> Restarted my Backend Project

-> Installed Node.js & NPM on Ububtu using terminal

    sudo apt install nodejs npm


-> Installed curl using 

    sudo apt install curl

-> Installed NVM using curl

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash

alternate,

    wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash

Then, Restart terminal.

-> I can install different Nodejs version using NVM by

    nvm ls-remote                 //it will list all the available nodejs version
    nvm install [version_number]
    nvm use [version_number]      // to switch b/w different Nodejs version

-> Initiated my project using

    npm init 


# Apr 24, 2025

-> .env file contains sensitive data and almost always added to .gitignore file.

-> .gitignore file is ignored while adding, committing and pushing and files to a Repository.

-> STARTING Data Modelling and Data Storing using MongoDB with Mongoose.

-> Data Modelling means the Structure of Data Storing in the Data base and how they're conntected to each other.

-> I'll use earser.io for data modelling diagrams and then code accordingly.

## Data Modelling : 

[Eraser Tool for Data Modelling](eraser.io)

-> Logic of storing data should be clear initially.

-> Slight change in storing data like adding new field to store or removing a field will impact the complete logic of data modelling or data storing.

-> Installed Mongoose on my system

    npm install mongoose
   
-> Practice some schema making related to Todo Lists on [StackBlitz](https://stackblitz.com/edit/stackblitz-starters-kcqu96bx?description=&file=models%2Ftodos%2Fsub_todos.model.js&title=Express%20Starter)
	
### Creating models using Mongoose:

```
import mongoose from 'mongoose'
const userSchema = new mongoose.Schema(
  {
      username: {
        type: string,   //defines type of input
        required: true,	//defines if compulsory to enter data or not
        unique: true,   //check if it pre-exists in the database
        lowercase: true 
      },
      email: {
        type: string,
        required: true,
        //required:[true,""email is required] -> this way we can pass additional comments other than the property.
        unique: true,
      },
      passwd: {
        type: string,
        required: true,
        min:[6,""Atlease 6 Characters should be there."],
        max: [18, "Atmost 18 Characters can be there."]
      }
  },
  {timestamps: true}	//this will introduce time stamps
)
export const User = mongoose.model("User",userSchema)
```
-> Completed 5th video of the Lecture.

# Apr 25, 2025

• Images are not directly saved into the database as it makes our DB heavier. It's possible but not recommended.

• We save images on some 3rd party services or our own server and the public URL of the image/video/PDFs,etc is entered into the database.

# Apr 29, 2025

-> Installed "nodemon" as DevDependency using
```
npm i -D nodemon
```

-> nodemon keeps restarting our server on its own after saving the file.

-> Also, added Prettier as a DevDependency for keeping the format of the page same for all the contributing developers.
```
npm i -D prettier
```
-> After installing Prettier, some new files related to prettier has to be added manually.
 1. .prettierrc : It has the format that we need to keep uniform throughout the project.
  
 2. .prettierignore : It works similar to ".gitignore". Prettier doesn't changes the structure of the mentioned files.

 ### Lecture 7 : Connecting Database

 -> using [MongoDB Atlas]()
 -> Always wrap in try-catch syntax to overcome errors.
 -> DB is always in other Continent therefore using "async - await" is necessary in professional approach.
```
 Step 1 : Login into MongoDB Atlas."
 Step 2 : Choose free server if prompted.
 Step 3 : Create Database
 Step 4 : Create cluster
 Step 5 : Save the connection string in .env file as MONGODB_URI or any other suitable name.
 ```

-> There are 2 approaches to coonect DB.
  1. Connect inside the index.js file
```
import mongoose from "mongoose";
import { DB_NAME } from "./constants";
import connectDB from "./db";

import express from "express";
const app = express();
;(async () => {
    try{
        await mongoose.connect(`${process.env.MONGO_URI}/${DB_NAME}`)
        app.on("error", (err) => {
            console.error("MongoDB connection error:", err);
        });
        app.listen(process.env.PORT, () => {
            console.log(`Server is running on port ${process.env.PORT}`);
        });
    }catch(error){
        console.error("Error connecting to MongoDB:", error);
        throw error;
    }
})()
```
  2. Create another file in src/db/ and write code for connecting DB there.
```
import mongoose from "mongoose";
import { DB_NAME } from "../constants";

const connectDB = async () => {
    try{
        const connectionInstance = await mongoose.connect(`${process.env.MONGO_URI}/${DB_NAME}`);
        console.log("\nMongoDB connected !! DB HOST : ${connectionInstance.connection.host} \n");
    }catch{
        console.log("MONGODB CONNECTION ERROR", error);
        process.exit(1)
    }
}

export default connectDB;
```

-> Name of the DB is mention in src/constansts.js.

-> It is desired to load the environment variable ASAP so that all the files can access them if needed without causing errors and crash. Therefore, configuring is important.

-> There are multiple methods to config the dotenv file
```
import dotenv from "dotenv"

dotenv.config({
  path: './env'
})
```
-> Then, edit the dev command in package.json as follows
```
nodemon -r dotenv/config --experimental-json-modules src/index.js
```

# Apr 30, 2025
[Lecture - 8](https://www.youtube.com/watch?v=S5EpsMjel-M&list=PLu71SKxNbfoBGh_8p_NS-ZAh6v7HhYqHW&index=9&t=1500s&pp=iAQB)

-> Whenever a asynchronous (async) method completes, it returns a promise.

-> Install Cookie-parser and Cors
```
npm i cookie-parser cors
```

-> cookie-parser is a middleware that parses cookies attached to the client request object. It makes it easier to access and manage cookies in your routes.

-> cors is a middleware that allows your server to accept requests from other domains (origins), which is often needed when your frontend and backend are hosted separately.

## NOTE: Starting JavaScript OneShot to have better understanding of NodeJS. [JavaScript One Shot](https://www.youtube.com/watch?v=sscX432bMZo) 


