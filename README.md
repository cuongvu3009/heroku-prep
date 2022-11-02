# heroku-prep

## 1. Create Procfile

web: node server.js

## 2. Serve frontend 

const path = require('path');

// Serve frontend <br>
if (process.env.NODE_ENV === 'production') { <br>
  app.use(express.static(path.join(__dirname, '../client/build'))); <br>

  app.get('*', (req, res) => <br>
    res.sendFile( <br>
      path.resolve(__dirname, '../', 'client', 'build', 'index.html') <br>
    )<br>
  );<br>
} else {<br>
  app.get('/', (req, res) => res.send('Please set to production'));<br>
}<br>

## 3. Install path and concurrently

## 4. package.json in server folder

"scripts": { <br>
    "start": "node server/server.js", <br>
    "server": "nodemon server/server.js", <br>
    "client": "npm start --prefix client", <br>
    "dev": "concurrently \"npm run server\" \"npm run client\"", <br>
    "heroku-postbuild": "NPM_CONFIG_PRODUCTION=false npm install --prefix client && npm run build --prefix client" <br>
  },
  
  
 "engines": { <br>
    "node": "16.x"
  }
  
 ## 5. Add config vars environments and buildpacks on heroku
 
 ## 6. package.json in client folder
 "proxy": "http://localhost:5000"
 
 ## 7. axios call must include '/api/v1'
