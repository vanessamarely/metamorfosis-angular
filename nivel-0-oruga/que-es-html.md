---
description: >-
  Es la forma en la que escribimos nuestros documentos y en esta sección
  aprenderemos a crearlos.
---

# 📄 ¿Qué es HTML? 📄

## 💡Introducción al HTML💡

![](../.gitbook/assets/html2.png)

Las siglas de HTML en ingles significan: **HyperText Markup Language** o lenguaje de marcado de Hipertexto en nuestro idioma.

El HTML, es el lenguaje base con el que se hacen las páginas web.

No es un lenguaje de programación, sino un lenguaje descriptivo, una serie de etiquetas 🏷️ que el navegador reconoce para mostrar el contenido en la pantalla 💻.

### Estructura básica de una página Web

Una página o documento HTML contiene unas etiquetas que son indispensables:

**\<!doctype>** es el tipo de documento, desde la versiòn de html5 el tipo de documento se colocala con la siguiente etiqueta: _**\<!doctype html>**_&#x20;

**\<html>** Aquí irá todo el contenido de nuestra página, esta etiqueta puede tener el atributo _**lang**_, que especifica el lenguaje de la página **\</html>**&#x20;

Dentro de las etiquetas anteriores (_**\<html>\</html>**_) van dos pares de etiquetas muy importantes:

**\<head>** Son etiquetas cabecera del documento, contienen información sobre la página, estas contienen unos meta tag que brindan información adicional del documento, ademas en estas pueden ser incluidos alguos tags como: \<title>\</title>, \<link>, \<script>**\</head>**

**\<body>** Estas etiquetas son el cuerpo del documento, aquí es donde incluimos todas las etiquetas para nuestro contenido, como: **\<div>\</div>\<p>\</p>**, entre otras**\</body>**

![](../.gitbook/assets/html.png)

****

![](https://lh5.googleusercontent.com/KY5iylncV2ihtT-7\_lNGp\_4riqyU-Fj\_Qb5oKYCLCBsvra7qREmv5Tvn6nDLUVyASEm3qKp2xv\_4LcW\_fc1l2sVGj5usTImEwmQmJsXiCgiIrn-MUJOG-Qcj3oHiREpDfEzrrByItog)

{% hint style="info" %}
Todas las etiquetas deben cerrarse. Hay etiquetas que tienen una que abre y cierra como esta: **\<p>\</p>**

y hay otras etiquetas que no requieren un par, se puede hacer el cierre en una sola, como: **\<img />**
{% endhint %}

### Sintaxis de un elemento

Un elemento de un documento HTML, tiene una representaciòn o significado semántico. El _**\<title>\</title>**_ representa el titulo del documento y solo se incluye en el _**\<head\</\<head>**_ del documento.

La mayoria de etiquetas tienen un tag o etiqueta de inicio y de cierre, y pueden contener atributos, que definen unas propiedades adicionales. Por ejemplo:

![](../.gitbook/assets/textos.png)

### Anidamiento (Nesting)

Las etiquetas pueden contener en su interior otras etiquetas. Si creamos dos etiquetas tipo parrafo, y dentro de cada una de ellas incluimos mas etiquetas, las dos etiquetas \<p>\</p>, estarian al mismo nivel y serian hermanas (siblings) y las etiquetas internas dentro de cada una, se convertirian en etiquetas padres que anidan otras etiquetas o tienen etiquetas hijas.

![](../.gitbook/assets/anidamiento.png)

### Comentarios

Los comentarios se incluyen en el marcado para hacer las etiquetas faciles de entender. Puede ser de ayuda para quien este leyendo tu documento HTML, para entender que estas haciendo Estos no se visualizan en el documento. Los comentarios inician con _**\<!--**_ y terminan con _**-->**_.

![](../.gitbook/assets/comentario.png)

### **Tipos de elementos del HTML**

Los elementos del HTML se pueden colocar en dos grupos, los elementos de **bloque** (**block**) y los elementos en **línea** (**inline**). Los de bloque ocupan el 100% del ancho disponible para este y hacen un salto de línea. Los elementos en línea, se colocan en la misma línea uno seguido del otro, ocupan el ancho de su contenido.

En bloque: **\<div>\</div>**, **\<p>\</p>**, **\<h1>\</h1>** hasta **\<h6>\</h6>**, **\<form>\</form>**, **\<ol>\</ol>**, **\<ul>\</ul>**, **\<li>\</li>**, **\<section>\</section>**, **\<article>\</article>**, entre otras.

En línea: **\<img />**, **\<a>\</a>**, **\<span>\</span>**, **\<strong>\</strong>**, **\<i>\</i>**, **\<input />**, **\<button>\</button>**

Es recomendable por semántica no colocar elementos en bloque dentro de los inline.

Existen muchas etiquetas, las cuales puedes ampliar la información en el siguiente link, en él puedes encontrar atributos de estas etiquetas, más etiquetas de acuerdo a su significado, con sus respectivos ejemplos: [mdn](https://developer.mozilla.org/es/docs/Web/HTML).

&#x20;
