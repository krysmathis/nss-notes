# Oh-My-Zsh 

## Syntax How-Tos

This is a function to initiate git and connect to a remote repository

Call it: ```ginit git@github.com:krysmathis/test_setup.git```

Just calling ```ginit``` will initiate a repo without connecting to a remote host


```bash
ginit() {
    git init;
    echo "# Documentation" > README.md;
    echo "node_modules" > .gitignore;
    git add .;
    git commit -m "initial commit";
    if [ -z $1 ]; then echo "no remote given"; else 
        git remote add origin $1
        git push -u origin master
    fi
}
```

## Generating a test site

To call it: ```genex site-name```

```bash
genexCSS() {
    CSS_FILE=$1

    printf '%s\n' '/*@import url("https://fonts.googleapis.com/css?family=Roboto");*/
/*font-family: "Roboto", sans-serif;*/

body {
  background: #D3D3D3;
  font-family: sans-serif;
  text-align: center;
  margin: 0;
  padding: 0;
}


.main-content {
  position: relative;
  background-color: #FAFAFA;
  text-align: left;
  width: 800px;
  margin: 0 auto;
}


.header {
  font-size: 2em;
  font-weight: bold;
  border-bottom: 1px solid rgba(0,0,0,.15);
  padding: 10px 0px 10px 0px;
  margin-left: 20px;
  margin-right:20px;
  margin-bottom: 10px;

}
.article {
  margin: 0 20px;
  padding: 10px 0;
}


.nav {
  color: white;
  background-color: black;
  height: 60px;
  width: 100%;
  font-size: 2em;
  font-weight: bold;
  z-index: 101;
}


.footer {
  background-color: black;
  width: 100%;
  height: 60px;
  position: fixed;
  bottom: 0;
  left: 0;
  display: block;
  margin: 0;
  z-index: 101;
}
' > $CSS_FILE
}

genexHTML() {
    HTML_FILE="index.html"
    CSS_FILE=$2
    JS_FILE=$3
    printf '%s''<html lang="en">
<head>
  <meta charset="utf-8"> 
  <title>'$1'</title> 
  <link rel="stylesheet" href="'$CSS_FILE'"> 
</head> 
  <body> 
    <nav class="nav"></nav> 
    <main class="main-content"> 
      <!-- PLACEHOLDER CONTENT --> 
      <header class="header">'$1'</header> 
      <article class="article"> 
        Start of article content 
      </article> 
      <!-- END OF PLACEHOLDER CONTENT--> 
    </main> 
    <footer class="footer"></footer> 
  <script src="'$JS_FILE'"></script> 
</html>' > $HTML_FILE

}

# Purpose: make a basic site for completing exercises
# Usage in terminal -- mksite boybands
genex() {
    # This function generates a basic set of files to initiate a project
    # $1 is the variable you pass in
    # start it in the directory you want your project directory to be in
    echo "CREATING DIRECTORIES:"
    mkdir $1 && cd $_
    echo "- /"$1
    mkdir scripts
    echo "- scripts"
    mkdir styles
    echo "- styles"
    mkdir images
    echo "- images"
    mkdir build
    echo "- build"
    echo "//placeholder for browserify" > "build/bundle.js"
    echo "DIRECTORY CREATION COMPLETE..."
    echo "..."
    #JS_FILE="scripts/"$1".js"
    JS_FILE="scripts/main.js"
    CSS_FILE="styles/"$1".css"
    HTML_FILE="index.html" 
    # create javascript file
    echo "BUILDING JS FILE"
    echo "console.log('connected...')" > $JS_FILE
    echo $JS_FILE " COMPLETE"
    # create the css file
    echo "BUILDING CSS FILE"
    genexCSS $CSS_FILE
    echo $CSS_FILE " COMPLETE"
    # create the index.html
    echo "BUILDING HTML FILE"
    genexHTML $1 $CSS_FILE $JS_FILE
    echo $HTML_FILE " COMPLETE"
    echo "DIRECTORY STRUCTURE:"
    echo "index.html
    |- styles
    |   |- "$1".css
    |- scripts
    |   |- main.js
    |- images
    |- build
    |   |- bundle.js"
    # open code editor
    # code .
    # open chrome -- this is specific to mac
    # open -a '/Applications/Google Chrome.app' http://localhost:8080
    # launch http-server
    # http-server
}

```

## Grunt Initiation Procedures

To run: ```gruntifyMe``` with the option of ```-a``` to have the program run ```rpm init``` instead of just adding a preconfigured file.

```bash
generatePackageJSON() {
# write a package json file
    JSON="package.json"
    printf '
{
"name": "my_package",
"version": "1.0.0",
"description": "Configure the description",
"repository": {
    "type": "git",
    "url": ""
  },
"keywords": [],
"main": "main.js",
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
},
"author": "Krys Mathis<krysmathis@gmail.com>",
"license": "MIT"
}' > $JSON
}

generateGruntFile() {
    GRUNT="Gruntfile.js"
    printf 'module.exports = function(grunt) {
  
    // Project configuration.
    grunt.initConfig({
        pkg: grunt.file.readJSON("package.json"),
        eslint: {
            src: ["!node_modules/**/*.js","scripts/*.js"]
        },
        browserify: {
            dist: {
                files: {
                    "build/bundle.js": ["scripts/*.js"]
                }
            }
        },
        watch: {
            options: {
                livereload: true
            },
            styles: {
                files: "[styles/**/*.css]"
            },
            scripts: {
                files: ["scripts/*.js"],
                tasks: ["eslint","browserify"],
                options: {
                    spawn: false,
                },
            }
        },
        uglify: {
            options: {
            },
            build: {
                files: [{
                    expand: true,
                    cwd: "build",
                    src: "bundle.js",
                    dest: "build",
                    ext: ".min.js"
                }]
            }
        }
    });
    
    // Load the plugin that provides the "uglify" task.
    grunt.loadNpmTasks("grunt-contrib-uglify");
    grunt.loadNpmTasks("grunt-contrib-watch");
    grunt.loadNpmTasks("gruntify-eslint");
    grunt.loadNpmTasks("grunt-browserify");
        
    
    // Default task(s).
    grunt.registerTask("default", ["uglify", "watch","eslint","browserify"]);
    
};    
' > $GRUNT
}

myLintConfig() {

    LINT_FILE=".eslintrc.js"
printf 'module.exports = {
    "env": {
        "browser": true,
        "commonjs": true,
        "es6": true
    },
    "extends": "eslint:recommended",
    "parserOptions": {
        "sourceType": "module"
    },
    "rules": {
        "indent": [
            "error",
            4
        ],
        "linebreak-style": [
            "error",
            "unix"
        ],
        "quotes": [
            "warn",
            "double"
        ],
        "no-console": [
            "warn"
        ],
        "semi": [
            "error",
            "always"
        ],
        "no-unused-var": 
            "off"
        
    },
    "globals": {
        "moment": true
    }
    
    
};' > $LINT_FILE
}

gruntInstallPackages() {

    echo "npm install grunt --save-dev"
    npm install grunt --save-dev
    echo "******************************"
    echo " Installing uglify"
    echo " - from: 'git://github.com/gruntjs/grunt-contrib-uglify.git#harmony'"
    echo "******************************"
    #npm install grunt-contrib-uglify --save-dev
    npm install 'git://github.com/gruntjs/grunt-contrib-uglify.git#harmony' --save-dev
    echo "******************************"
    echo " Installing watch"
    echo "******************************"
    npm install grunt-contrib-watch --save-dev
    echo "******************************"
    echo " Installing eslint"
    echo "******************************"
    npm install gruntify-eslint --save-dev
    echo "******************************"
    echo " Installing browserify"
    echo "******************************"
    npm install grunt-browserify --save-dev
}



gruntifyMe() {

    # if the user supplies -a then the 
    # program will generate a package.json
    # using npm init instead
    echo "Begin set-up for:"
    echo "Grunt: The Javascript Task Runner"
    echo "---------------------------------"
    echo "Generating package.json"
        if [ $# -eq 0 ]
        then
        echo "...Generating default package.json"
        generatePackageJSON
    else
        case $1 in 
            -a* ) npm init
        esac
    fi
    
    echo "Generating Gruntfile.js"
    generateGruntFile
    
    echo "Begin install of packages and plug-ins"
    gruntInstallPackages
    
    echo "Generating elintrc.js file"
    myLintConfig
    
    echo '***********************************'
    echo '“Ho! Tom Bombadil, Tom Bombadillo!
By water, wood and hill, by reed and willow,
By fire, sun and moon, harken now and hear us!
Come, Tom Bombadil, for our need is near us!” '

    echo '***********************************
    You asked for it and you got it!
    The following actions occurred successfully:
    - package.json
    - Gruntfile.js
    - .eslintrc.js (config as necessary)
    - Grunt Plug-Ins
        - Grunt
        - Browserify
        - Watch
        - Uglify

    * LiveReload is included in the Gruntfile.js,
      if you are not using live reload you many
      need to set the livereload option under watch
      to false.
    The next step is up to you -> run grunt in the command line
    '

}

```
