# Contenedor base con root activado

## Notas

1. Los paquetes dan problema con la última versión de node y npm así que hay que actualizarlos y dejar typescript@4.9.3
   [enlace stackoverflow](https://stackoverflow.com/questions/16073603/how-can-i-update-each-dependency-in-package-json-to-the-latest-version) 

> npm-check-updates is a utility that automatically adjusts a package.json with the latest version of all dependencies
> 
> see https://www.npmjs.org/package/npm-check-updates
> ```
> $ npm install -g npm-check-updates
> $ ncu -u
> $ npm install
> ```
> [EDIT] A slightly less intrusive (avoids a global install) way of doing this if you have a modern version of npm is:
> ```
> $ npx npm-check-updates -u
> $ npm install
> ```
