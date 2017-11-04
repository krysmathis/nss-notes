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
genex() {
    # modify this directory structure to hold the location of your exercises folder
    # $1 is the variable you pass in
    # mkdir -p ~/workspace/javascript/exercises/$1 && cd $_
    mkdir $1 && cd $_
    mkdir scripts
    mkdir styles
    mkdir images
    # create javascript file
    #JS_FILE="scripts/"$1".js"
    JS_FILE="scripts/main.js"
    echo "console.log('connected...')" > $JS_FILE
    echo "/*@import url('https://fonts.googleapis.com/css?family=Roboto');*/\n\n body {\n  background: red;\n  font-family: 'Roboto', sans-serif;\n}\n\n.main-content {\n  margin-left: 20px;\n  margin-right: 20px;\n}\n\n header {\n  font-size: 2em;\n  font-weight: bold;\n  border-bottom: 1px solid rgba(0,0,0,.15);\n   padding: 10px 0px 10px 0px;\n   margin-bottom: 10px;\n}" > "styles/"$1".css"
    # create html file
    echo "<html lang='en'>" > index.html
    echo "<head>" >> index.html
    echo "  <meta charset='utf-8'>" >> index.html
    echo "  <title>"$1"</title>" >> index.html
    echo "  <link rel='stylesheet' href='./styles/"$1".css'>" >> index.html
    echo "</head>" >> index.html
    # -- the ">>" operator appends to a file or creates it
    echo "  <body>" >> index.html
    echo "    <nav></nav>" >> index.html
    echo "    <main class='main-content'>" >> index.html
    echo "      <header></header>  " >> index.html
    echo "      <article></article>" >> index.html
    echo "    </main>" >> index.html
    echo "    <footer></footer>" >> index.html
    echo "  <script src='./"$JS_FILE"'></script>" >> index.html
    echo "</html>" >> index.html
}
```
