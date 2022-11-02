# heroku-prep

## 1. Create Procfile

web: node server.js

## 2. Serve frontend 

const path = require('path');

// Serve frontend
if (process.env.NODE_ENV === 'production') {
  app.use(express.static(path.join(__dirname, '../client/build')));

  app.get('*', (req, res) =>
    res.sendFile(
      path.resolve(__dirname, '../', 'client', 'build', 'index.html')
    )
  );
} else {
  app.get('/', (req, res) => res.send('Please set to production'));
}

## 3. Install path and concurrently

## 4. package.json in server folder

"scripts": {
    "start": "node server/server.js",
    "server": "nodemon server/server.js",
    "client": "npm start --prefix client",
    "dev": "concurrently \"npm run server\" \"npm run client\"",
    "heroku-postbuild": "NPM_CONFIG_PRODUCTION=false npm install --prefix client && npm run build --prefix client"
  },
  
  
 "engines": {
    "node": "16.x"
  }
  
 ## 5. Add config vars environments and buildpacks on heroku
 
 ## 6. package.json in client folder
 "proxy": "http://localhost:5000"
 
 ## 7. axios call must include '/api/v1'
