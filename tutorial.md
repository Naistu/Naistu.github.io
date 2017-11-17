#
ANGULAR 2 INSTALACION

Existen 2 métodos para comenzar a usar Angular. Cualquiera método requiere tener instalado [**NodeJS 4**](https://nodejs.org/es/download/)**, **[**npm 3** ](https://docs.npmjs.com/cli/install)**o superiores **\(**npm se instala en conjunto a NodeJS**\) .

## Metodo 1:Manual

Este método será el más largo.

**PASO 1:**

Creamos una carpeta con cualquier nombre.

**PASO 2:**

Dentro generaremos 3 archivos con los siguientes nombres y contenido.

**package.json:**

Identifica las dependencias de paquetes npm para el proyecto.

```js
{
"name": "angularcli",
"version": "0.0.0",
"license": "MIT",
"scripts": {
"ng": "ng",
"start": "ng serve",
"build": "ng build",
"test": "ng test",
"lint": "ng lint",
"e2e": "ng e2e"
},
"private": true,
"dependencies": {
"@angular/animations": "^5.0.0",
"@angular/common": "^5.0.0",
"@angular/compiler": "^5.0.0",
"@angular/core": "^5.0.0",
"@angular/forms": "^5.0.0",
"@angular/http": "^5.0.0",
"@angular/platform-browser": "^5.0.0",
"@angular/platform-browser-dynamic": "^5.0.0",
"@angular/router": "^5.0.0",
"core-js": "^2.4.1",
"rxjs": "^5.5.2",
"zone.js": "^0.8.14"
},
"devDependencies": {
"@angular/cli": "1.5.0",
"@angular/compiler-cli": "^5.0.0",
"@angular/language-service": "^5.0.0",
"@types/jasmine": "~2.5.53",
"@types/jasminewd2": "~2.0.2",
"@types/node": "~6.0.60",
"codelyzer": "~3.2.0",
"jasmine-core": "~2.6.2",
"jasmine-spec-reporter": "~4.1.0",
"karma": "~1.7.0",
"karma-chrome-launcher": "~2.1.1",
"karma-cli": "~1.0.1",
"karma-coverage-istanbul-reporter": "^1.2.1",
"karma-jasmine": "~1.1.0",
"karma-jasmine-html-reporter": "^0.2.2",
"protractor": "~5.1.2",
"ts-node": "~3.2.0",
"tslint": "~5.7.0",
"typescript": "~2.4.2"
}
}
```

**tsconfig.json:**

Define la configuración de TypeScript y como compilara los archivos JavaScript.

```js
{
"compileOnSave": false,
"compilerOptions": {
"outDir": "./dist/out-tsc",
"sourceMap": true,
"declaration": false,
"moduleResolution": "node",
"emitDecoratorMetadata": true,
"experimentalDecorators": true,
"target": "es5",
"typeRoots": [
"node_modules/@types"
],
"lib": [
"es2017",
"dom"
]
}
}
```

**Systemjs.config.js: **Proporcionará la configuración de cómo serán cargados los módulos del proyecto.

/\*\*

```js
* System configuration for Angular samples
* Adjust as necessary for your application needs.
*/
(function (global) {
System.config({
paths: {
// paths serve as alias
'npm:': 'node_modules/'
},
// map tells the System loader where to look for things
map: {
// our app is within the app folder
app: 'app',
// angular bundles
'@angular/core': 'npm:@angular/core/bundles/core.umd.js',
'@angular/common': 'npm:@angular/common/bundles/common.umd.js',
'@angular/compiler': 'npm:@angular/compiler/bundles/compiler.umd.js',
'@angular/platform-browser': 'npm:@angular/platform-browser/bundles/platform-browser.umd.js',
'@angular/platform-browser-dynamic': 'npm:@angular/platform-browser-dynamic/bundles/platform-browser-dynamic.umd.js',
'@angular/http': 'npm:@angular/http/bundles/http.umd.js',
'@angular/router': 'npm:@angular/router/bundles/router.umd.js',
'@angular/forms': 'npm:@angular/forms/bundles/forms.umd.js',
'@angular/upgrade': 'npm:@angular/upgrade/bundles/upgrade.umd.js',
// other libraries
'rxjs': 'npm:rxjs',
'angular-in-memory-web-api': 'npm:angular-in-memory-web-api/bundles/in-memory-web-api.umd.js'
},
// packages tells the System loader how to load when no filename and/or no extension
packages: {
app: {
main: './main.js',
defaultExtension: 'js'
},
rxjs: {
defaultExtension: 'js'
}
}
});
})(this);
```

Estos son los tres archivos que debemos tener dentro de la carpeta

![](/assets/import.png1)

**PASO 3: Instalación de paquetes**

Para instalar los paquetes necesario ejecutaremos el siguiente comando dentro de la carpeta:

_**npm install**_

Al terminar tendremos una carpeta llamada _**node\_modules **adicional a esta carpeta, crearemos una nueva llamada _**app, **nos quedarán las siguientes carpetas.

![](/assets/i2mport.png)

_**PASO 5: Componentes**_

Dentro de la carpeta _**app **crearemos el archivo llamado _**app.component.ts **con el siguiente contenido.

```
import { Component } from '@angular/core';
```

```js
@Component({
selector: 'my-app',
template: '
<
h1
>
Hello Angular!
<
/h1
>
'
})
export class AppComponent { }
```

**PASO 6: Módulo inicial**

Todas las aplicaciones en Angular 2 requieren **mínimo de un módulo**, dentro de la carpeta _**app **crearemos un archivo llamado _**app.module.ts **con el siguiente contenido.

import { NgModule } from '@angular/core';

```js
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
@NgModule({
imports: [ BrowserModule ],
declarations: [ AppComponent ],
bootstrap: [ AppComponent ]
})
export class AppModule { }
```

_**PASO 7: **_**Main**

Nuevamente dentro de la carpeta _**app **creamos un nuevo archivo llamado _**main.ts **con el siguiente código.

```
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
```

```js
import { AppModule } from './app.module';
const platform = platformBrowserDynamic();
platform.bootstrapModule(AppModule);
```

**PASO 8: Index.html**

Dentro de nuestra carpeta_** **crearemos un archivo llamado _**index.html **donde pondremos el siguiente código.

```
<html>
<head>
<title>Angular QuickStart</title>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- 1. Load libraries -->
<!-- Polyfill for older browsers -->
<script src="node_modules/core-js/client/shim.min.js"></script>
<script src="node_modules/zone.js/dist/zone.js"></script>
<script src="node_modules/reflect-metadata/Reflect.js"></script>
<script src="node_modules/systemjs/dist/system.src.js"></script>
<!-- 2. Configure SystemJS -->
<script src="systemjs.config.js"></script>
<script>
System.import('app').catch(function(err){ console.error(err); });
</script>
</head>
<!-- 3. Display the application -->
<body>
<my-app>Loading...</my-app>
</body>
</html>
```

**PASO 9: Ejecución**

Ahora ejecutaremos nuestro proyecto con el comando _**npm start **_. Inmediatamente de ejecutar el comando _nos abrirá una ventana en el navegador con la dirección _[_**http://localhost:3000/**_](http://localhost:3000/) con el siguiente mensaje:

![](/assets/i1mport.png)

Y listo eso es todo para poder tener nuestra primer aplicación en Angular 2 mediante el método manual.

## Método 2: Angular CLI

Para este método tendremos que seguir los siguientes pasos, **ya debemos tener instalado NodeJS\(Version 4 en adelante\), npm\(Version 3 en adelante\).**

**PASO 1: Angular CLI Global**

Este método requiere instalar **angular cli de forma global **\(por eso se le agrega -g a nuestro comando\) de la siguiente forma:

_**npm install -g @angular/cli**_

Una vez terminado el proceso verificaremos que fue instalado correctamente con el siguiente comando:

_**ng -v**_

que nos mostrará un mensaje similar a este donde nos indica la versión de angular cli que tenemos instalada y la versión de node:

![](/assets/ngv.png)

_**PASO 2: Creación del proyecto**_

Una vez comprobado que tenemos instalado angular-cli de manera correcta, procederemos a crear un proyecto con el siguiente comando: **ng new &lt;nombre-del-proyecto&gt; **en este caso se llamará angularcli y el comando quedaría de la siguiente forma:

_**ng new mis-heroes**_

Esperamos a que terminen de bajar los archivos, paquetes y dependencias.

**PASO 3: Ejecución**

Nos creará una carpeta con el nombre del proyecto que le hayamos puesto y en este caso nuestra aplicación se encontrará en la carpeta _**src **donde encontraremos los archivos necesarios para poder iniciar nuestra aplicación._

La ejecución\(dentro de la carpeta mis-heroes\) será con el comando:

_**ng serve **_

Nos dirigimos a localhost:4200 en nuestro navegador y veremos lo siguente:

![](/assets/ngserve.png)

Y eso será todo para poder tener nuestra aplicación angular-cli instalada y funcionando.

En conclusion les recomiendo instalar el CLI de angular 2 para ahorrarse mucho tiempo que pueden gastar desarollando su app.

Ahora vamos agregar un nuevo componente para ver como funcionan.

## Componente heroes

Usando Angular CLI, creamos un nuevo comoponente llamado heroes.

_**ng generate component heroes**_

La clase`HeroesComponent`contiene:

```typescript
import { Component, OnInit } from '@angular/core';

@Component({
selector: 'app-heroes',
templateUrl: './heroes.component.html',
styleUrls: ['./heroes.component.css']
})
export class HeroesComponent implements OnInit {

constructor() { }

ngOnInit() {
}

}
```

### Agregamos una propiedad a heroes

Dentro de `heroes.component.ts` agregamos la propiedad "Windstorm."

`hero = 'Windstorm';`

Cambiamos dentro de `heroes.component.html`el texto que tiene por defecto, y ponemos lo siguente:

```
{{hero}}
```

Para que `HeroesComponent`se ve en nuestra aplicacion web debemos agregarla al template de la app, debemos agregarlo a `app.component.html:`

`<h1>{{title}}</h1>`

`<app-heroes></app-heroes>`

Como vemos arriba debajo del titulo de la app tenemos el componente de 'heroe' con su propiedad.
De esta forma veremos en pantalla lo siguente:

![](/assets/pantalla.png)

### Creamos la clase Heroe

Creamos la clase heroe dentro de la carpeta `src/app`. Le daremos un id y un nombre.

Dentro del archivo recien creado`src/app/hero.ts` creamos la clase:

```
export class Hero {
id: number;
name: string;
}
```

Volvemos a`src/app/heroes/heroes.component.ts` e importamos la clase `Hero`.

Modificamos la propiedad `hero`para que sea tipo `Hero`. Lo inicializamos con `id=1` y `name=Windstorm`. El codigo nos quedaria algo asi:

```
import { Component, OnInit } from '@angular/core';
import { Hero } from '../hero';

@Component({
selector: 'app-heroes',
templateUrl: './heroes.component.html',
styleUrls: ['./heroes.component.css']
})
export class HeroesComponent implements OnInit {
hero: Hero = {
id: 1,
name: 'Windstorm'
};

constructor() { }

ngOnInit() {
}

}
```

La pagina no cargara mas hero, porque ya no es mas un string sino un objeto. Por lo que ahora devemos llamar al objeto

### Mostrar el objeto 'Hero'

Dentro de `heroes.component.html` actualizamos los datos, colocando el `id` y `name` de `Hero`. Lo que quedaria algo asi:

```
<h2>Mis heroes</h2>
<div><span>id: </span>{{hero.id}}</div>
<br>
<div><span>Nombre:</span>{{hero.name}}</div>
<br>
```

Ahora le daremos al usuario la posibilidadde de modificar el nombre del heroe.

### Editar nombre del heroe

El usuario tendra la posibilidad de editar el nombre con un `<input>`.

Para automatizar ese flujo de datos, configure un enlace de datos bidireccional entre el elemento de formulario `<input>` y la propiedad `hero.name`.

Modificamos `src/app/heroes/heroes.component.html` para que se vea asi:

```
<div>
<label>Nuevo nombre:
<input [(ngModel)]="hero.name" placeholder="nuevo nombre">
</label>
</div>
```

\[\(ngModel\)\] es el sintaxis de datos bidireccional de Angular.

### Importar FormsModule

Para que \[\(ngModel\)\] funcione es necesario importar `FormsModule`, entonces lo impoetamos dentro de `AppModule (app.module.ts)`:

```
import { FormsModule } from '@angular/forms'; // <-- NgModel lives here
```

y tambien lo importamos en `@NgModule imports`:

```
imports: [
BrowserModule,
FormsModule
],
```

Ahora la pagina se nos recargara y veremos como funciona perfectamente, dejandonos editar el nombre de nuestro heroe.

![](/assets/ultima.png)


