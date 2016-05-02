### How to Deploy app strongloop on azure !!!

Como distribuir el backend desarrollado en Strongloop para que funcione correctamente en Azure.

#### 1
Partimos de crear un proyecto con:
##### slc loopback

#### 2
Modificamos en package.json:

Modificamos las líneas, “main” y “start”, luego agregamos “engines”, con la versión de node y npm que azure debe utilizar.

```sh
“main”: “./server/server.js”,
“start”: “node ./app.js”,
```

```sh
“engines”: {
“node”: “5.3.0”,
“npm” : “3.3.12”
},
```

#### 3
agregamos app.js

```sh
var app = require(‘./server/server.js’)
app.start();
```

#### 4
Cuando subimos la app con git, vamos a poder ver como va generando y bajando los paquetes que se encuentran en el package.json:

```sh
remote: Copying file: ‘server\server.js’
remote: Copying file: ‘server\boot\root.js’
remote: Using start-up script app.js from package.json.
remote: Generated web.config.
remote: Node.js versions available on the platform are: 0.6.20, 0.8.2, 0.8.19, 0.8.26, 0.8.27, 0.8.28, 0.10.5, 0.10.18, 0.10.21, 0.10.24, 0.10.26, 0.10.28, 0.10.29, 0.10.31, 0.10.32, 0.10.40, 0.12.0, 0.12.2, 0.12.3, 0.12.6, 4.0.0, 4.1.0, 4.1.2, 4.2.1, 4.2.2, 4.2.3, 4.2.4, 4.3.0, 4.3.2, 4.4.0, 4.4.1, 5.0.0, 5.1.1, 5.3.0, 5.4.0, 5.5.0, 5.6.0, 5.7.0, 5.7.1, 5.8.0, 5.9.1, 6.0.0.
remote: Selected node.js version 5.3.0. Use package.json file to choose a different version.
remote: Selected npm version 3.3.12
remote: Updating iisnode.yml at D:\home\site\wwwroot\iisnode.yml
remote: ………………………………………………………………………………………………………………………………………………………………………….
remote: backend@1.0.0 D:\home\site\wwwroot
remote: +– compression@1.6.1
remote: ¦ +– accepts@1.3.2
remote: ¦ ¦ +– mime-types@2.1.10
remote: ¦ ¦ +– negotiator@0.6.0
remote: ¦ +– bytes@2.2.0
remote: ¦ +– compressible@2.0.7
remote: ¦ ¦ +– mime-db@1.22.0
remote: ¦ +– debug@2.2.0
remote: ¦ +– on-headers@1.0.1
remote: ¦ +– vary@1.1.0
remote: +– cors@2.7.1
remote: +– helmet@1.3.0
remote: ¦ +– connect@3.4.1
remote: ¦ ¦ +– finalhandler@0.4.1
remote: ¦ ¦ ¦ +– unpipe@1.0.0
remote: ¦ ¦ +– utils-merge@1.0.0
remote: ¦ +– dns-prefetch-control@0.1.0

remote: Finished successfully.
remote: Running post deployment command(s)…
remote: Deployment successful.
To https://dsinfo@dsinfo-back-end.scm.azurewebsites.net:443/dsinfo-back-end.git
* [new branch] master -> master
```

#### 5
Chequear del mismo modo que lo hacemos local:

```sh
http://localhost/explorer
```
