# History for solving Angular installation in a rootless container

```
    #=========== front

    2  npm init
    8  npm install @angular/animations @angular/common @angular/compiler @angular/core @angular/fire @angular/forms @angular/platform-browser @angular/platform-browser-dynamic @angular/router firebase  rxjs tslib yarn zone.js  --legacy-peer-deps
    9  npm install @angular-devkit/build-angular @angular/cli @angular/compiler-cli @types/jasmine @types/node jasmine-core karma karma-chrome-launcher  karma-coverage karma-jasmine karma-jasmine-html-reporter typescript --save-dev  --legacy-peer-deps
   13  export PATH="$PATH:~/.config/yarn/global/node_modules/.bin"
   18  yarn global add @angular-devkit/build-angular --dev
   22  yarn add  typescript@4.9.3 --dev
   23  npm run build
   24  yarn add @angular-devkit/build-angular --dev
   25  npm run build
   
   12  yarn global bin
       > /home/user/.yarn/bin
   14  /home/user/.yarn/bin/ng version
   15  export PATH=$PATH:/home/user/.yarn/bin:/usr/local/bin
   21  npx yarn config set prefix /home/user/.yarn/
   22  npx yarn global bin
   23  npx yarn global add @angular/cli --dev
   24  ng version
   28  npx yarn add @angular-devkit/build-angular --dev
   29  ng version

"presets": ["@babel/preset-flow"]
npx yarn add @babel/preset-flow --save-dev
babel-node -x .ts test.ts
     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/
    

#  Angular CLI: 16.2.0
#  Node: 16.20.1
#  Package Manager: npm 8.19.4
#  OS: linux x64
#  
#  Angular: 16.2.2
#  ... animations, common, compiler, compiler-cli, core, forms
#  ... platform-browser, platform-browser-dynamic, router
#  
#  Package                         Version
#  ---------------------------------------------------------
#  @angular-devkit/architect       0.1602.0
#  @angular-devkit/build-angular   16.2.0
#  @angular-devkit/core            16.2.0
#  @angular-devkit/schematics      16.2.0
#  @angular/cli                    16.2.0 (cli-only)
#  @angular/fire                   7.6.1
#  @schematics/angular             16.2.0
#  rxjs                            7.8.1
#  typescript                      4.9.5
#  zone.js                         0.13.1


   #============== back
   back-end (main) $ npx yarn global add @babel/core @babel/node @babel/preset-env nodemon
   # yarn global v1.22.19
   # back-end (main) $ npm run start
   
   # > fsa-meal-tracker-server@1.0.0 start
   # > nodemon --exec 'babel-node ./src/server.js'

   # [nodemon] 3.0.1
   # [nodemon] to restart at any time, enter `rs`
   # [nodemon] watching path(s): *.*
   # [nodemon] watching extensions: js,mjs,cjs,json
   # [nodemon] starting `babel-node ./src/server.js`
   # Listening on port 8080


     

```