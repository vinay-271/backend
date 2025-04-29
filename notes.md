Apr 22, 2025

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
    nvm ls-remote       //it will list all the available nodejs version
    nvm install [version_number]
    nvm use [version_number]  // to switch b/w different Nodejs version

-> Initiated my project using
    npm init 


Apr 24, 2025

-> .env file contains sensitive data and almost always added to .gitignore file.

-> .gitignore file is ignored while adding, committing and pushing and files to a Repository.

-> STARTING Data Modelling and Data Storing using MongoDB with Mongoose.

-> Data Modelling means the Structure of Data Storing in the Data base and how they're conntected to each other.

-> I'll use earser.io for data modelling diagrams and then code accordingly.

#Data Modelling : using eraser.io

-> Logic of storing data should be clear initially.

-> Slight change in storing data like adding new field to store or removing a field will impact the complete logic of data modelling or data storing.

->Installed Mongoose on my system
   npm install mongoose
   
-> Practice some schema making related to Todo Lists on stackblitz.com

	https://stackblitz.com/edit/stackblitz-starters-kcqu96bx?description=&file=models%2Ftodos%2Fsub_todos.model.js&title=Express%20Starter
	
# Creating models using Mongoose

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

-> Completed 5th video of the Lecture.

# Apr 25, 2025

-> Images are not directly saved into the database as it makes our DB heavier. It's possible but not recommended.

-> We save images on some 3rd party services or our own server and the public URL of the image/video/PDFs,etc is entered into the database.

->
