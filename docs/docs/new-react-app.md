# Creating a new React App

This assumes you already have node (> v4) installed. The other program you'll need is **create-react-app**
In order to set up the React app environment, you need to have the **create-react-app** installed (please check out the [Install](install) session).
Open the command prompt and type the following command:


    create-react-app <project name>

The corresponding project name can be found in the Project_name field in the Pagedraw dashboard, as described below:

![](https://d2mxuefqeaa7sj.cloudfront.net/s_0D309846360B9C8558544A15DA3255269736A32D754FB67C2E543DF5727437D2_1512433973159_project_name2.png)


This command will create a directory called <**project name**>. Inside the directory, it will generate the initial project structure and install the following transitive dependencies:


    <project name>
    ├── README.md
    ├── node_modules
    ├── package.json
    ├── .gitignore
    ├── public
    │ └── favicon.ico
    │ └── index.html
    │ └── manifest.json
    └── src
    │ └── App.css
    │ └── App.js
    │ └── App.test.js
    │ └── index.css
    │ └── index.js
    │ └── logo.svg
    │ └── registerServiceWorker.js

In the root project directory, create a new file named **pagedraw.json**, containing:


    { “app” : "<project name>" }

The ‘pagedraw.json’ file basically tells Pagedraw CLI which app to fetch from. In this case, the Pagedraw CLI will fetch docs from <project name> and place them in paths relative to the location of your pagedraw.json file.


## Syncing files generated by Pagedraw

First of all, run the following command to enable access to the project:


    pagedraw login

A new window will open, asking for login authentication. Once the authentication is successful, a message will appear in the screen.
There are two main ways of bringing the docs generated by Pagedraw to your computer:


- Pull: lets you pull at once the docs generated by Pagedraw specifically to the paths relative to the location of your pagedraw.json file;
- Sync: lets you sync automatically the docs generated by Pagedraw at the same directory destination as pull does, also letting you real-time follow the development progress in a separate browser window.

In order to pull at once those generated docs to your computer, enter the project folder and type the command:


    `pagedraw pull`

Alternatively, in order to sync them automatically to your computer, enter the project folder and type the command:


    `pagedraw sync`

If you want to read more check out [this section on the Pagedraw CLI](cli).


## Requiring files

The create-react-app environment needs to understand which files to require from Pagedraw.
Right after starting a project, edit the ‘index.js’ file, inside the ‘src’ folder, so it contains the information below:


    import React, {Component} from ‘react’;
    import ReactDOM from ‘react-dom’;
    import App from './pagedraw/<artboard_name>';
    
    Class App2 extends Component {
        render() {
            return <App />;
        }
    }
    ReactDOM.render(<App2 />, document.getElementById(‘root’));


## Running the app in development mode

Once the previous steps are done, open a different command prompt window and run the following command inside the pagedraw project folder:


     npm start 

This command will run the app in development mode.
To follow in real time the project development progress, there is an environment that mirrors exactly what you would see working in a professional setting in a separate browser window. Open this [link](http://localhost:3000) to view this real-time progress in the browser. If you have used the command `pagedraw sync`, the page will automatically reload while you make changes to the code, allowing to see occasional build errors and lint warnings in the console.
