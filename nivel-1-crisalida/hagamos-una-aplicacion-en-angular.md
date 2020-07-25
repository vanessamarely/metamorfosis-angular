---
description: >-
  En esta aplicación haremos uso de varios conceptos de Angular, para crear un
  formulario que nos permita autenticarnos,  y a la vez usaremos un servicio que
  consuma una API.
---

# ⌛Hagamos una aplicación en Angular⌛

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

## Paso 2: Crearemos un formulario ✍️

Vamos a crear un formulario con un campo de texto, donde pondremos el nombre de usuario con el que nos vamos a autenticar en nuestra App. Adicionalmente tendrá un botón para enviar el texto que ingresaremos en el formulario.

Para el formulario añadiremos en la vista en el **app.component.html**, algunas etiquetas, como estas: 

{% code title="app.component.html" %}
```markup
<section id="authentication">
  <h1>Autentiquemonos en Github 😉</h1>
  <form class="form">
    <div>
      <label for="username">Añade un nombre: 
        <input class="form__field"
          id="username"
          type="text"
          placeholder="Añade el nombre de usuario ..."
          required
          name="username"
        />
      </label>
    </div>
    <button type='submit'>Enviar!!</button>
  </form>
  <p class="label">Form: </p>
</section>
```
{% endcode %}

## Paso 3: Creemos la función que se encargará de la autenticación 🏭

En el archivo **app.component.ts** vamos a crear el objeto model, que es donde almacenaremos el modelo de nuestro formulario y crearemos una función login que se encargará de la lógica de nuestra App.

{% code title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';


@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  model = {};

  login(): void {
  
  }
}
```
{% endcode %}

En nuestra función llamada **login**, que será accionada cuando el usuario de click en el botón **Enviar**, le añadiremos un parámetro que va a recibir la función que se lo asignaremos a nuestra variable model.

{% code title="app.component.ts" %}
```typescript
login(form: any): void{
  this.model = form;
}
```
{% endcode %}

En el html vamos a hacer el binding, para enlazar la data que será diligenciada con el modelo del formulario. En  el campo de texto añadiremos el banana-box.

```markup
<input class="form__field"
    id="username"
    type="text"
    placeholder="Añade el nombre de usuario ..."
    required
    name="username"
    [(ngModel)]="model.username"
/>
```

En el **ngModel** \(binding\), asignaremos el objeto que creamos en el componente model, con la propiedad **model.username**.

Como el botón en nuestras etiquetas es de tipo submit, en la etiqueta form añadiremos un evento, que llamará a la función que creamos. Ademas crearemos una referencia al formulario: _**\#form**_ \(esta referencia nos permite acceder al DOM\).

```markup
<form #form="ngForm" (ngSubmit)="login(form.value)">
    ...
</form>
```

## Paso 4: Crearemos un servicio 💆

Crearemos un 'servicio' dando clic sobre la carpeta 'app', seleccionamos 'service', nombramos el servicio como: '**login**', damos enter y se nos creará un archivo llamado: **login.service.ts**

{% code title="login.service.ts" %}
```typescript
import { Injectable } from '@angular/core';

@Injectable()
export class LoginService {

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

Importamos unas dependencias en nuestro nuevo archivo llamado **login.service.ts**,  y añadimos en el constructor lo siguiente: **http: HttpClient** , haciendo uso de la inyección de dependencias \(Patron de diseño\)

{% code title="login.service.ts" %}
```typescript
import { Injectable } from '@angular/core';
import { HttpClient} from '@angular/common/http';

@Injectable()
export class LoginService {

  constructor(private http: HttpClient) { }


}
```
{% endcode %}

En nuestro archivo **login.service.ts** crearemos una función para obtener la data del API, la llamaremos **getApi**. Crearemos una constante donde incluiremos la url de la API.

{% code title="login.service.ts" %}
```typescript
import { Injectable } from '@angular/core';
import { HttpClient} from '@angular/common/http';

@Injectable()
export class LoginService {
  
  private apiRoot: string = 'https://api.github.com/users/';
  
  constructor(private http: HttpClient) { }
  
  getApi(username: string) {
    return this.http.get(`${this.apiRoot}${username}/repos`);
  }

}
```
{% endcode %}

## Paso 5: Hagamos la lógica que llama a nuestro servicio  🍭

En nuestro archivo **app.component.ts**, en nuestra función **login**, crearemos un 'Observable' que nos permitirá subscribirnos a la petición que hacemos de los datos, usando la variable que definimos con la ruta del API de **Github**.

También importaremos en nuestro **app.component.ts** el servicio que creamos, **LoginService,** y crearemos una función **constructor** donde declararemos una función privada del servicio. ****

{% code title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';
import { LoginService } from './login.service';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  model = {};
  
  constructor(
    private loginService: LoginService
  ){}

  login(form: any): void {
    this.model = form;
    console.log(this.model);
  }
}
```
{% endcode %}

En la función login\(\), vamos a  crear una constante donde asignamos la propiedad del username. 

En el servicio login, como notaste retornamos una función, que trae la respuesta de nuestra API. En esa función hacemos uso del  [HttpClient](https://angular.io/api/common/http/HttpClient), que es un observable, entonces en nuestro componente para obtener la data necesitamos subscribirnos.

{% code title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';
import { LoginService } from './login.service';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  model = {};
  
  constructor(
    private loginService: LoginService
  ){}

  login(form: any): void {
    this.model = form;
    const username = this.model['username'];
    console.log(this.model);
    this.loginService.getApi(username)
      .subscribe(
        response => (console.log(response)),
        error => (console.log('Ups! we have an error: ', error))
      );
  }
}
```
{% endcode %}

Ahora podemos probar el llamado de nuestra API colocando en el campo de texto el nombre de un usuario de **Github**. Si abres la consola de **Stackblitz** podrás ver el resultado de nuestro **console.log\(response\)**.

## Paso 5: Mostremos el resultado del API 📰

Crearemos una variable llamada **responseList**, donde almacenaremos el resultado del llamado de nuestra API. 

Si observas la url de nuestra API, al final tiene '/**repos**', con esta palabra traeremos la lista de todos los repositorios del usuario que estamos consultando, puedes probar quitándole esta palabra y observarás que traerás la información de usuario \(la imagen de perfil, su id en Github, entre otros datos\) .

{% code title="app.component.ts" %}
```typescript
import { Component } from '@angular/core';
import { LoginService } from './login.service';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  model = {
    username: ''
  };
  responseList;
  
  constructor(
    private loginService: LoginService
  ){}

  login(form: any): void {
    this.model = form;
    const username = this.model['username'];
    console.log(this.model);
    this.loginService.getApi(username)
      .subscribe(
        response => (console.log(response)),
        error => (console.log('Ups! we have an error: ', error))
      );
  }
}
```
{% endcode %}

Para mostrar esta data en nuestro HTML y ocultarla y mostrarla cuando lo necesitemos haremos uso de la interpolación y las directivas.

{% hint style="info" %}
La interpolación nos permite mostrar la data que almacenan las variables en la vista.
{% endhint %}

Teniamos un parrafo, cuando creamos nuestro HTML, allí mostraremos el modelo de nuestro formulario, para saber que va digitando el usuario:

```markup
<p class="label">Form: {{ model | json}} </p>
```

{% hint style="info" %}
Despues de model notasrás que hay un pipe, en angular nos pipes nos permiten dar formato a la data en la vista.
{% endhint %}

Ahora para mostrar nuestra data, te invito a crees una etiqueta section y apliques la interpolación, ademas hagamos uso de las directivas \*ngIf, para que se oculte esta sección y que solo aparezca cuando haya data, como respuesta al llamado de nuestra API.

```markup
<section id="display-data" *ngIf="responseList">
  <h2>la respuesta es: </h2>
  {{ responseList | json}}
</section>
```

Puedes ver lo que hemos hecho aquí: [https://angular-ivy-o2htnx.stackblitz.io](https://angular-ivy-o2htnx.stackblitz.io)

La data se va a mostrar muy desordenada, así que nuestra tarea es ordenarla, en una tabla. Usa una directiva llamada \*ngFor para recorrer la respuesta de nuestra API en la vista. Aquí encontrarás una guía sobre [directivas](https://ngchallenges.gitbook.io/project/directivas), para que conozcas el uso del \*ngFor.

## Crea tu  App usando el angular-cli

Para crear esta misma aplicación localmente debes tener instalado node.js y un IDE \(Visual Studio Code es una buena opcion\). Una vez lo instales debemos en tu terminal preferida, instalar Angular usando el siguiente comando:

```bash
npm install -g @angular/cli
```

Para verificar que tienes instalado node.js antes del anterior comando, solo colocas en la terminar

```bash
node -v
npm -v
```

* Vamos a crear el workspace o ambiente de trabajo. Cuando haya terminado de instalar el angular/cli, debes ejecutar el siguiente comando:

```bash
ng new my-app
```

Con ese comando indicamos que queremos crear una nueva aplicación. Cuando estes instalando te va a preguntar si deseas añadir el routing, le escribes  "Y" \(seria yes\), te mostrá algo similar a esto:  'Would you like to add Angular Routing?'. Eso es lo unico que necesitamos decirle Y.  
Cuando te pregunte por el stylescheet selecciona CSS.

Para ejecutar nuestra aplicación debemos ir a la carpeta que se genero, ejecutamos lo siguiente en la terminal:

```text
cd my-app
ng serve --open
```

![](../.gitbook/assets/image%20%282%29.png)

Una vez ejecutado nuestro proyecto, podremos ver el hola por defecto de Angular, similar al de stackblitz.

El archivo de routing es para crear una SPA, para darle más complejidad a nuestra App y te puedes basar en el nivel 0 para hacerlo.

Angular tiene algo que se llama schematics, que te permite ejecutar pequeñas instrucciones para generar los archivos y añadir las rutas respectivas donde se necesitan. Para crear los componentes, lo haremos así:

```text
ng generate component <nameComponent>
```

Se puede usar la forma abreviada:

```text
ng g c <nameComponent>
```

Para crear un servicio, lo haremos así:

```text
ng generate service <nameService>
```

Se puede usar la forma abreviada:

```text
ng g s <nameService>
```

Puedes basarte en el ejercicio que hiciste en Stackblitz para hacer este y una vez lo termines, subes a Github tu ejercicio.

