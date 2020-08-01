---
description: >-
  Para esta app crearemos un servicio donde mostraremos la data en uno de los
  componentes, ademas de usar el enrutamiento
---

# ⌛Hagamos una app en Angular⌛

Para construir nuestra aplicación primero lo haremos de una forma sencilla online haciendo uso de stackblitz:

## Paso 1: **Creemos nuestra App de Angular** ⭐️ <a id="paso-1-creemos-nuestra-app-de-angular"></a>

Primero iremos a el inicio de **Stackbliz** y crearemos una App de Angular.

![](https://gblobscdn.gitbook.com/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-Lfm1buzeVgzyc9sla4K%2F-LfmF2EIn_D3rx1gxAJJ%2FScreen%20Shot%202019-05-25%20at%2010.41.44%20PM.png?alt=media&token=eff358e9-e6bb-4a39-a072-8de632c75ac2)

Vamos al inicio de Stackblitz y damos click en el botón.

![](https://gblobscdn.gitbook.com/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-Lfm1buzeVgzyc9sla4K%2F-LfmFnfwUkx_kYXbVEwL%2FScreen%20Shot%202019-05-25%20at%2010.48.40%20PM.png?alt=media&token=3050fc43-1746-4a98-993d-94c250b1a2a3)

Seleccionamos la opción de Angular

![](https://gblobscdn.gitbook.com/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-Lfm1buzeVgzyc9sla4K%2F-LfmGCMN4j_IokU0vzTP%2FScreen%20Shot%202019-05-25%20at%2010.52.23%20PM.png?alt=media&token=b9630837-c8a0-4388-93a5-0474b2f6f7e5)

Verás algo como esto 👆

Seleccionamos el texto del archivo **app.component.html**, lo borramos \(presionando la tecla delete de tu compu 💻\) y guardamos los cambios, seleccionando en la parte superior la opción de 'Save' 💾

![](https://gblobscdn.gitbook.com/assets%2F-LW1Rd6Lo-WMisT20MSI%2F-Lfm1buzeVgzyc9sla4K%2F-LfmHJVm7_7cFa8fmSA3%2FWebp.net-gifmaker%20%281%29.gif?alt=media&token=8924bfbd-4c41-4857-b397-9e9f32e455de)

## Paso 2: Crearemos varios componentes 💪

Cuando visitas una página web, puedes observar que ella tiene muchas secciones como información de una empresa/producto, detalles de servicios, información de contacto entre otras. En este paso crearemos varios componentes, que serán donde iremos a colocar cada una de las secciones de nuestra página.

Dando clic derecho sobre la carpeta App, se desplegará un menú, en el seleccionaremos la opción **Angular Generator** y luego seleccionamos componente.

Nos aparece un campo de texto donde colocaremos el nombre para nuestro componente.

Le colocaremos el nombre home y presionamos enter y se nos creará nuestro nuevo componente.

Repetiremos el mismo paso para la creación del componente para crear otro componente más, lo llamaremos topmovies.

## Paso 3: Añadiendo un Menu 📋

Añadamos un componente para crear nuestro menú en él.

Dando clic derecho sobre la carpeta App, se desplegará un menú, en el seleccionaremos la opción **Angular Generator** y luego seleccionamos componente.

Nos aparece un campo de texto donde colocaremos el nombre para nuestro componente.

Le colocaremos el nombre "menu" y presionamos enter y se nos creará nuestro nuevo componente.

En el archivo **menu.component.html** vamos a poner la etiqueta &lt;nav&gt; donde pondremos cada uno de los links que nos llevarán a cada componente. Esos links los pondremos en una lista.

Nuestra lista se verá parecida al siguiente código, pero en la vista o **HTML** aún  no veremos nuestra lista hasta que la incluyamos en nuestro componente  App. 

{% tabs %}
{% tab title="menu.component.html" %}
```markup
<nav>
  <ul>
    <li><a>Home</a></li>
    <li><a>Top Movies</a></li>
  </ul>
</nav>
```
{% endtab %}
{% endtabs %}

En el archivo **menu.component.ts** existe una línea donde encuentras el '**selector**' y ese es el que se debe añadir en el **app.component.html**

Copia el selector y añádelo como etiqueta en la vista del componente App, en el archivo app.component.html.

```markup
<app-menu></app-menu>
```

## Paso 4: Uniendo los componentes a sus links 🕹️

Vamos a crear un módulo router, para controlar todas nuestras rutas.

En la carpeta **app**, vamos a dar clic derecho y en la opción Angular Generator, seleccionaremos Module y lo llamaremos routing.

En nuestro nuevo archivo vamos a incluir las rutas y para ello debemos importar Routes y el RouterModule e incluir en los import la colección de nuestras rutas.

* Incluimos el import

```typescript
import { Routes, RouterModule } from '@angular/router';
```

* Debemos también importar los componentes que estamos mencionando en la colección de rutas, para que no salga error en nuestra aplicación.

```typescript
import { HomeComponent } from '../home/home.component';
import { TopmoviesComponent } from '../topmovies/topmovies.component';
```

También podemos crear una constante donde almacenemos la colección de nuestras rutas, la llamaremos "**routes**".

Ademas en los imports icluiremos cada una de las rutas haciendo uso de forRoute\(\) en los imports del decorador del NgModule.

{% tabs %}
{% tab title="routing.module.ts" %}
```typescript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { HomeComponent } from '../home/home.component';
import { TopmoviesComponent } from '../topmovies/topmovies.component';

const routes: Routes = [
  { path: 'home', component: HomeComponent },
  { path: 'topmovies', component: TopMoviesComponent },
  { path: '', redirectTo: '/home', pathMatch: 'full' },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class RoutingModule { }
```
{% endtab %}
{% endtabs %}

* Aún no hemos incluido el archivo routing.module en nuestro app, para esto en el archivo **app.module.ts**, importamos nuestro archivo **routing.module.ts**

{% tabs %}
{% tab title="app.module.ts" %}
```typescript
import { RoutingModule } from './routing/routing.module';
```
{% endtab %}
{% endtabs %}

Incluimos en la colección de imports nuestro '**RoutingModule**'

```typescript
imports:      [ BrowserModule, FormsModule, RoutingModule ],
```

En nuestro **app.module.ts** aparecen importados los componentes que ya incluimos en el **routing.module.ts**, entonces lo que haremos es borrar los que ya están en el routing de nuestro **app.module.ts** y quedará así:

{% tabs %}
{% tab title="app.module.ts" %}
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';

import { AppComponent } from './app.component';
import { MenuComponent } from './menu/menu.component';

import { RoutingModule } from './routing/routing.module';

@NgModule({
  imports:      [ BrowserModule, FormsModule, RoutingModule ],
  declarations: [ AppComponent, MenuComponent ],
  bootstrap:    [ AppComponent ]
})
export class AppModule { }

```
{% endtab %}
{% endtabs %}

* Nos falta incluir estas rutas que creamos de nuestros componentes en el menú que incluimos y usar la etiqueta &lt;router-outlet&gt; que nos ayudará a mostrar el contenido de nuestros componentes

En nuestro **app.component.html** vamos a incluir nuestra etiqueta &lt;router-outlet&gt; &lt;/router-outlet&gt;, dentro de estas etiquetas se va a mostrar todo el contenido de nuestros componentes.

{% tabs %}
{% tab title="app.component.html" %}
```markup
<header class="header">
  <h1>My App 😉</h1>
</header>
<app-menu></app-menu>
<router-outlet></router-outlet>
```
{% endtab %}
{% endtabs %}

Solo falta incluir en nuestros links la ruta de nuestros componentes y para ello vamos a hacer uso de unos atributos que tiene el enrutamiento o Routing, llamados **routerLinkActive** y **routerLink**. En cada uno de nuestros links incluiremos que nuestro link esta activo y le pondremos en el routerLink el path que asignamos en el RouterModule. En el archivo **menu.component.html** añadiremos lo mencionado.

{% tabs %}
{% tab title="menu.component.html" %}
```markup
<nav>
  <ul>
    <li><a routerLinkActive="active" 
      routerLink="/home">Home</a></li>
    <li><a routerLinkActive="active" 
      routerLink="/topmovies">Top Movies</a></li>
  </ul>
</nav>
```
{% endtab %}
{% endtabs %}

Si damos clic en cada uno de los links podremos ver el contenido de cada componente.

Como puedes notar no hay mucho contenido en nuestros componentes, entonces podemos incluir alguno de contenido en ellos. 

## Paso 5: Crearemos un servicio 💆

Crearemos un 'servicio' dando clic sobre la carpeta 'app', seleccionamos 'service', nombramos el servicio como: '**movies**', damos enter y se nos creará un archivo llamado: **movies.service.ts**

{% code title="movies.service.ts" %}
```typescript
import { Injectable } from '@angular/core';

@Injectable()
export class MoviesService {

  constructor() { }

}
```
{% endcode %}

Incluimos el '**HttpClientModule**' en el archivo **app.module.ts**

{% code title="add.module.ts" %}
```typescript
import { HttpClientModule } from '@angular/common/http';
```
{% endcode %}

En los imports incluimos el **HttpClientModule** en el '**app.module.ts'**

{% code title="app.module.ts" %}
```typescript
@NgModule({
  imports:      [ BrowserModule, FormsModule, HttpClientModule ],
  declarations: [ AppComponent, HelloComponent ],
  bootstrap:    [ AppComponent ],
  providers: [LoginService]
})
export class AppModule { }

```
{% endcode %}

Importamos unas dependencias en nuestro nuevo archivo llamado **movies.service.ts**,  y añadimos en el constructor lo siguiente: **http: HttpClient** , haciendo uso de la inyección de dependencias \(Patron de diseño\). Este http, va a ser uso de lo que tenga el HttpClient, que este hace parte del nuevo modulo que incluimos en el app.module.ts

{% code title="movies.service.ts" %}
```typescript
import { Injectable } from '@angular/core';
import { HttpClient} from '@angular/common/http';

@Injectable()
export class MoviesService {

  constructor(private http: HttpClient) { }


}
```
{% endcode %}

En nuestro archivo **movies.service.ts** crearemos una función para obtener la data del API, la llamaremos **getApi**. Crearemos una constante donde incluiremos la url de la API. Adicional a nuestra función le incluiremos un parametro de entrada que será el nombre de usuario del dueño del repositorio.

En nuestra función incluimos un return que hace uso del parametro private del constructor que llama al get propio del http, que hace uso de las funciones del HttpClient, lo que hace este método, es que nos crea un Observable que va a contener la data que se recibe del api. En nuestro caso estamos usando la data del api, entonces en la función getApi, vamos a retornar ese observable que contiene la data que recibimos de la api.

{% code title="movies.service.ts" %}
```typescript
import { Injectable } from '@angular/core';
import { HttpClient} from '@angular/common/http';

@Injectable()
export class MoviesService {
  
  private apiRoot: string = 'https://run.mocky.io/v3/0a045509-f93f-4c8b-b66c-a70f20843c35';
  
  constructor(private http: HttpClient) { }
  
  getApi() {
    return this.http.get(this.apiRoot);
  }

}
```
{% endcode %}


