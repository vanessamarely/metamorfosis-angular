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

## Paso 2: Crearemos un servicio 💆

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



