# Baobab

Baobab is a tree based planning tool. The purpose of Baobab is to simplify and combine long term and short term planning. Our team overcame the drawbacks of currently available planning tools by creating a coherent product that allows users to effectively visualise their long term goal planning, whilst encouraging the management of low level tasks that are required to achieve the larger goals. Baobab is designed with usability, customisations and integrations in mind to provide a streamlined user experience.
Baobab was created as a capstone project by UNSW students (Nanway Chen, Thomas Ho, Harry Brink, Alexander Jones, Conrad Martin)

# Usage
You can create sections of a tree to match the sections of your life. For example, University could be your root node and the main branches could be subjects and societies. 

put a gif

You can then connect these branches to queue nodes where you can create Kanban boards or nested trees.

put a gif

This is a Kanban board, here you're limited to only having one task in your doing row to maximise focus! 

put a gif

# Additional Features
- Baobot (Chatbot).
You can ask for help here ... or try and find the easter eggs (bugs = easter eggs) and ask for motivation.

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gifs/chatBot.gif">
</p>

- Creating multiple trees.

- Gamification of Kanban Tasks.
As you complete tasks in your kanban boards, the progress bar increases and you are encouraged by an extremely supportive message! Below is the progression as you complete a greater percentage of your tasks.

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/a%20while%20to%20go.png">
</p>

<p align="center">
  <img width="500" height="280" src=https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/getting%20there.png">
</p>

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/half%20way.png">
</p>

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/half%20way.png">
</p>

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/ramp%20it%20up.png">
</p>

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/finish%20it.png">
</p>

<p align="center">
  <img width="500" height="280" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/gamification/great%20finish.png">
</p>

- User customistation.
Add your own unique flair! 

- Sexify Tree button.
Sometimes when you're in the thick of organising your life, your tree can get a little messy. 

- Onboarding.
Everyone needs help learning something new!

# Contribution history

<p align="center">
  <img width="500" height="530" src="https://github.com/MajesticMullet/Baobab/blob/readmeGIF/img/contributionHist.png">
</p>
Special thanks to Fora.digital 

# Developer Documentation

First of all, make sure you have Node.js installed. You can install it from from https://nodejs.org/en/. This installation includes npm.

## Running the webapp locally

### Running the frontend

1. Clone the repository from https://github.com/MajesticMullet/Baobab 
2. Make sure you are in the project directory.
3. Run the following commands:
- `cd baobab/frontend`
- `npm install` (if you are running for the first time).
- `npm start`
4. Go to http://localhost:3000/ (if this port is taken then you will be asked by terminal if you want to use a different port automatically).

Note, the backend is already deployed on the cloud so the frontend will be communicating with Cloud Functions in `asia-northeast-1`. There is no need to run the backend.

If you get any backend errors then please comment out lines 40, 41, 42 of code in `baobab/frontend/src/firebase.js`

```javascript
if (window.location.hostname === "localhost") {
    this.functions.useFunctionsEmulator("http://localhost:5001");
}
```

We will make sure we comment them out in final submission so it is most likely you won't have to do this.

Onc you comment out those lines, stop the program from running and run it again.

### Running the backend

Assuming you have installed Node.js from the first step.
Only do this if you need to do local development. This is a little complicated.

Run: `npm install -g firebase-tools`

First, uncomment lines 40, 41, 42 of code in `baobab/frontend/src/firebase.js`:

```javascript
// if (window.location.hostname === "localhost") {
//     this.functions.useFunctionsEmulator("http://localhost:5001");
// }
```

After this run:
- `cd baobab/backend`
- `export GOOGLE_APPLICATION_CREDENTIALS="path_to_here/baobab-82803-8b5b63bcf616.json"` Replace `path_to_here` with full path from root e.g. `/Users/username/3900/project/baobab/backend`. You can get this value by running the command pwd in terminal on linux or mac. On windows follow these instructions: https://stackoverflow.com/questions/607670/windows-shell-command-to-get-the-full-path-to-the-current-directory

Once you do this, please do the following:

Now install npm modules in the functions folder:
- `cd functions`
- `npm install`

Now go back to the backend folder:
- `cd ..`

Run the following to start the backend locally on localhost:
- `firebase emulators:start`

## Deploying the Webapp
You only need to do this if you want to develop the app further and re-deploy your code changes.
WARNING: this requires Firebase login because you will be making changes to the deployed webapp.

### Deploying the frontend
Ok so now you've made new code changes and you want to deploy them to updated the deployed webapp (the changes will show up here after this step: https://baobab-82803.firebaseapp.com/)

First make sure you are in the project root directory.

First you need to login (you must be a firebase admin, to request admin access email Alexander on z5114400@student.unsw.edu.au to request access, please provide your gmail)

To log into firebase run: `firebase login` (will ask you for gmail and password)

Make sure you are in the project root folder then go to the frontend folder:
- `cd baobab/frontend`
- `npm install` (if you haven't done so already)
- `sh deploy.sh`

Now the frontend should have any new changes you added.

### Deploying the backend

Run:
- `npm install -g firebase-tools` if you haven't done so already

Doing this will make changes to the Cloud Functions (if you did change the code)

First you need to login (you must be a firebase admin, to request admin access email Alexander on z5114400@student.unsw.edu.au to request access, please provide your gmail)

Make sure you are in the project root folder then go to the backend folder:

To log into firebase if you are not login: `firebase login`

- Go to the backend folder: `cd baobab/backend`
- Go to the functions folder: `cd functions`
- Run: `npm install` (if you haven't done so already)
- Go back to backend folder:cd `cd ..`
- Deploy functions: `firebase deploy`

if not all functions are deployed successfully in one go (happens because of slow internet) firebase will ask you to run another command to deploy only the functions that failed to deploy.

Now the Cloud Functions should have any new code you added.
