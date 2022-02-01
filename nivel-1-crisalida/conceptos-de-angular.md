---
description: >-
  Angular es un Framework que esta compuesto de componentes, los cuales definen
  las vistas, ademas de servicios que proveen una funcionalidad especifica.
---

# ✨ Conceptos de Angular ✨

Se puede decir que **Angular** esta compuesto de componentes, modulos y servicios. Estos tres son clases que usan decoradores, los cuales marcan su tipo y poseen una metadata que especifica a **Angular**, como usarlos.

La metadata para un componente nos permite conocer detalles sobre el template, que define la vista, y los estilos que esta puede tener. En un template podemos encontrar el lenguaje de marcado o **HTML**, ademas de las directivas y el binding, que permiten a **Angular** editar el **HTML** antes de que sea renderizado.

La metadata de los servicios proveen información, que puede ser compartida en los diferentes componentes, usando el patron de diseño de **DI - Dependency Injection** o **Inyección de Dependencias**.

Una aplicación de componente, define muchas vistas que estan organizados jerarquicamente.

**Angular** posee un servicio de Enrutamiento o **Router**, que nos permite crear una **SPA** (**Single Page Aplication**), que nos ayuda a manejar la navegación de nuestra aplicación entre las vistas.&#x20;



## 🏺 Módulos 🏺

Los módulos como mencione, son contenedores, en donde se hace referencia a los componentes, a otros módulos que pueden contener otros componentes, a los servicios y otros archivos que necesitemos para la construcción de diferentes elementos de Angular o uso de otras librerías. Se encuentra normalmente el archivo como: 'nombrearchivo.module.ts'.

La estructura del module es como la siguiente:

```typescript
@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, AppRoutingModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

## 📦 Componente 📦

Los componentes de Angular son donde vamos a estructurar nuestra aplicación. Cuando construimos una aplicación analizamos cual va a ser le contenedor de la página, y que elementos internamente vamos a separar el componentes que nos van a ayudar con la lógica de negocio de la página o solo a mostrar un componente visual (sea solo un boton, o un menu, un header, etc.)



![](https://gblobscdn.gitbook.com/assets%2F-LbFy569GFu09bPpzMDJ%2F-LohnhqdNnTTn0E2cbaM%2F-LohnuU0Lxpfjv8oRCmr%2Faplicaicon.png?alt=media\&token=9c03512f-810e-46c6-9d1e-7ea96c1a12b6)

Un componente en Angular es un elemento que está compuesto por:

* Un archivo que será nuestro Template (app.component.html), el cual es nuestro HTML, que es el que se va a visualizar en la interfaz de usuario, la vista o en términos más simples lo que vas a ver en la página.
* Un archivo de lógica, la cual es la que pondremos en un archivo .ts (como por ejemplo app.component.ts), ese archivo debe incluir una clase y esta es la que va a contener las propiedades que se van a usar en la vista (HTML) y los métodos que será las acciones que se ejecutarán en la vista. En este archivo de lógica también se incluye una metadata, que es definida con un decorador, que identifica a Angular como un componente.
* Un archivo para el CSS (podemos usar un preprocesador como SASS o LESS), donde incluiremos los estilos, lo que nos ayuda a hacer bonita nuestra aplicación.

![](https://gblobscdn.gitbook.com/assets%2F-LbFy569GFu09bPpzMDJ%2F-LohnhqdNnTTn0E2cbaM%2F-Loho4STfHppM5gvSYpc%2Fcomponente.png?alt=media\&token=0200ce92-2830-49e4-936c-f45c5cab9683)

La estructura de un componente es así:

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styles: []
})
export class AppComponent {}
```

Adicional a los archivos que mencione, CSS, HTML que son los principales en nuestro componente, e incluso podrían no estar, ya que podemos colocar nuestro HTML usando el selector 'template' y el CSS, el selector styles. Podemos ir añadiendo más archivos de acuerdo a la necesidad que tengamos en nuestro proyecto.

Como por ejemplo:

* Un archivo para el test, donde podemos incluir nuestras pruebas unitarias.

Y podemos incluir muchos archivos más.

Cuando creamos un componente o estamos usando el base de app, para incluir nuestro componente en otros componentes debemos usar la propiedad 'selector' que se encuentra en el decorador, en otro html asi:

```markup
<my-app></my-app>
```

Puedes ampliar la informacion de los componentes en el siguiente link: [componentes](https://medium.com/@vanessamarely/componentes-en-angular-f25138b00c83).

## 🧑‍🎨 Directivas 🧑‍🎨

Las Directivas extienden la funcionalidad del HTML usando para ello una nueva sintaxis. Con ella podemos usar lógica que será ejecutada en el DOM (Document Object Model).

Cada Directiva que usamos tiene un nombre, y determina donde puede ser usada, sea en un elemento, atributo, componente o clase.

Se dividen en tres tipos diferentes:

* Directivas de Atributo: Alteran la apariencia o comportamiento de un elemento del DOM. Son usados como atributos de los elementos.
* Directivas estructurales: Nos permite añadir, manipular o eliminar  elementos del DOM.
* Componentes: Las Directivas de Componente son directivas con un Template.

Para ampliar un poco más la información de Directivas y como usarla, puedes leer este artículo: [Directivas](https://medium.com/@vanessamarely/directivas-en-angular-efb8a8cf78e0)

## Data Binding

Se le llama Data Binding o enlace de Datos, a la técnica que nos sirve de puente de comunicación entre una vista HTML y una fuente de datos, nuestro modelo; y los sincroniza, permitiendonos una actualización casi que en tiempo real de nuestra data a nuestra vista.

Tipos Binding de datos

* One Way (una sola vía) . Los cambios solo se reflejan en la vista o modelo, pero no hay sincronia entre ambos frente a una actualización de la data.
* Two Way (dos vias). Se usa generalmente en los formularios, ya que se desea que el usuario ingrese la información, esta se actualice correctamente.

## Router

El enrutamiento o Router es la navegación entre las diferentes páginas. Nos permite crear SPAs.

Los elementos principales del Router son:

* **RouterModule:** Contiene toda la lógica necesaria para enrutar en el navegador.
* **Router outlet:** Este se encarga de la carga dinámica. Se encarga de saber qué componente cargar y dónde mostrarlo.

```markup
<router-outlet></router-outlet>
```

* **Router Link:** Son los hipervinculos o enlaces donde especificaremos donde navegará nuestra página.\
  Los hipervinculos o enlaces tradicionales normalmente son asi:&#x20;

```markup
<a href=""></a>
```

Donde en el href se incluía la dirección donde el usuario iba a navegar.

En Angular los enlaces se manejan con el atributo routerLink, donde especificamos la ruta.\


```markup
<a routerLink="/">Go home</a>
```

### 🎈¿Qué es una SPA - Single Page Aplication?🎈

Una SPA es una aplicación Web donde todas las pantallas con las que vaya a interactuar el usuario las muestra en una misma página.

Antiguamente cuando se iniciaron a crear páginas Web, el contenido de ellas era estatico y teniamos que crear un documento por página y algunos elementos no se reutilizaban; hablando de un header o un menu. Cuando se empezaron a crear las páginas dinamicas, que el contenido venia desde una petición a una base de datos, se empezaron a crear páginas más robustas que terminarón en aplicaciones Web; y para reutilizar componentes y evitar crear multiples documentos HTML, conceptos como las SPA fueron introducidos para facilitarnos el trabajo.\


## Formularios

Un formulario nos permite recolectar datos, sea información personal del usuario, comentarios, sugerencias, autenticarnos a una página, entre otros usos.

La librería@angular/forms, nos permite hacer uso de los formularios en Angular.

Hay tres tipos de formularios en Angular:

* Formularios de Plantillas - Template Driven

Estos formularios nos permiten enlazar los datos hacer el data binding, desde el componente a la vista (plantilla, HTML), usando la sintaxis del banana box: \[(nombreDeVariable)]. Este tipo de formularios son muy buenos para hacer cosas sencillas y nos permite usar el principio KISS (acrónimo de Keep It Simple Stupid).

* Formularios Reactivos - Reactive Forms

Los formularios reactivos tienen la particularidad que la manipulación de los datos,  los elementos del HTML y sus validaciones, se hacen principalmente en el componente.

* Formularios Dinámicos - Dynamic Forms

Los formularios dinámicos, usan un patron usando una meta descripción para construirlos. Usan la API de los formularios reactivos en su construcción.&#x20;



## Servicios

Un servicio nos permite compartir funcionalidades y la data que solicitamos al servidor, para poderla compartir sin problema entre componentes.

{% hint style="info" %}
Un servicio sigue el patrón _**Singletón**_, sirve como un recurso compartido el cual aisla la implementación de un contexto global, es decir, puedo referenciarlo en varios lugares y llamar sus funciones.

Un _**patrón de diseño**_, es una forma reutilizable de resolver un problema común.

[https://devexperto.com/patrones-de-diseno-software/](https://devexperto.com/patrones-de-diseno-software/)
{% endhint %}

Un servicio de Angular usa  el decorador `@Injectable()` que le indica a Angular que este servicio puede tener dependencias inyectadas.

```typescript
import { Injectable } from '@angular/core';

@Injectable()
export class HeroService {

  constructor() { }

}
```



