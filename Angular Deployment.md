# Angular Deployment

## Get Ready for Deployment
### Optimize the Application
> Minification  
> Uglification  
> Bundling  
> Dead code elimination

> **Using Angular CLI:** Since we are using Angular CLI for our project, so we can use the command below to build and Bundle.

>ng build --prod

I have a project from the learning journey on Angular material.

```
Date: 2018-06-19T04:28:45.579Z
Hash: 64b4d3fc34504c87c7d0
Time: 66420ms
chunk {0} runtime.a66f828dca56eeb90e02.js (runtime) 1.05 kB [entry] [rendered]
chunk {1} styles.120dd010beed940b5c52.css (styles) 56.4 kB [initial] [rendered]
chunk {2} polyfills.7a0e6866a34e280f48e7.js (polyfills) 59.6 kB [initial] [rendered]
chunk {3} main.8db0f8891cb38e5b9b45.js (main) 596 kB [initial] [rendered]

```

```

```


## Deploy Application to Github
- Create and make sure the app run with ng serve.  (here we use our material-app for Angular 6)

1. create a new repository in github (e.g. ng6-material-app-deploy)

2. if you have not add remote git to the project:  
git remote add origin https://github.com/YourGitName/PROJECT_NAME.git

3. $ git remote -v  
origin  https://github.com/mgolladaywork1/ng6-material-app.git (fetch)
origin  https://github.com/mgolladaywork1/ng6-material-app.git (push)

4. install angular-cli-ghpages globally  
$ npm install -g angular-cli-ghpages

**Note**:  If something mess up, may have to run   
$ npm install -g @angular/cli

to get ng serve working again.

As of 06/20/2018, the angular-cli-ghpages may have a problem with Angular 6.  I will need to do more research on deploy to github.

```
better use npm install -g ngh

ng build --prod --base-href https://debugmodedotnet.github.io/demo9/ 

then ngh...

ngh --dir dist/material-app

angular.json's "outputPath": "dist/" into "outputPath": "dist/[PROJECTNAME]", which placed everything in the dist folder in a subfolder

ngh --dir dist/[PROJECTNAME]

There is someone:  my github pages deploy branch to the gh-pages one that was created by the ngh --dir dist/[PROJECTNAME] command.

ng build --prod --base-href "http://[username].github.io/[projectname]"

set a custom base href in development index.html to fix them and just used a relative path to assets/image.jpg

```

https://github.com/mgolladaywork1/ng6-material-app.git


ng build --prod --base-href https://github.com/mgolladaywork1/ng6-material-app/ 

ngh --dir dist/material-app

https://mgolladaywork1.github.io/ng6-material-app/




## Deploy Application to Netlify

## Deploy Angular Application to IIS

> try IIS, not working yet (able to run app on 'http-server')

Make sure we have:  
Install Internet Information Services.  
Install the URL Rewrite Module


[Deploy an Angular Application to IIS ](https://blog.angularindepth.com/deploy-an-angular-application-to-iis-60a0897742e7)


for my [material-app], in material-app\src, create web.config
```
<?xml version="1.0" encoding="utf-8"?>
<configuration>

<system.webServer>
  <rewrite>
    <rules>
      <rule name="Angular Routes" stopProcessing="true">
        <match url=".*" />
        <conditions logicalGrouping="MatchAll">
          <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
          <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
        </conditions>
        <action type="Rewrite" url="./index.html" />
      </rule>
    </rules>
  </rewrite>
</system.webServer>

</configuration>
```

In the project .angular.-cli.json.  Add web.config to assets
```
"assets": [
    "assets",
    "favicon.ico",
    "web.config"
],
```

After I ran   
ng build --base-href "/material-app/" --prod 

copy material-app\dist folder to
wwwroot\material-app

Go to Browser and run
http://localhost/material-app/index.html




## Deploy Angular Application to Java War

