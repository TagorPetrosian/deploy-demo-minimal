# DemoDeployMini

## Deployment To Heroku

1. Install Heroku CLI
2. git init
3. [create heroku app](https://devcenter.heroku.com/articles/git)
4. create server.js in src folder

   - Make it serve proper file from dist

   ```
   //Install express server
   const express = require('express');
   const path = require('path');

   const app = express();

   // Serve only the static files form the dist directory
   app.use(express.static(__dirname + '/dist/demo-deploy-mini'));

   app.get('/*', function (req, res) {
     res.sendFile(path.join(__dirname + '/dist/demo-deploy-mini/index.html'));
   });

   // Start the app by listening on the default Heroku port
   app.listen(process.env.PORT || 8080);
   ```

5. modify package.json

   - add your npm and node version after scripts:

   ```
     "engines": {
     "node": "14.15.1",
     "npm": "6.14.8"
   },
   ```

   - add to scripts:

   ```
    "heroku-postbuild": "ng build --prod"

   ```

6. git push -u origin --all
7. heroku create
8. git push heroku master
