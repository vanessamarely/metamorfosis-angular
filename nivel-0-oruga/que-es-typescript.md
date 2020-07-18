---
description: Typescript es un superset de JavaScript
---

# 🤓 ¿Qué es TypeScript? 🤓

## 🤓Introducción a TypeScript🤓

![](../.gitbook/assets/estructurado.png)

TypeScript es un lenguaje de programación, se puede decir que es un super JavaScript tipado. Fue creado para hacer código JavaScript mucho más escalable.

TypeScript soluciona muchos de los problemas que presenta JavaScript:

* Falta de un tipado fuerte y estático.
* Falta de «Syntactic Sugar o Azucar sintáctico» para la creación de clases.
* Falta de interfaces
* Falta de Modulos \(aunque se usa el require.js\)

## Tipos de Datos

En typescript se puede hacer uso de los tipos de datos de JavaScript, pero tambien tiene sus tipos de datos. Los básicos son:

* **Booleans**: tipo de dato lógico
* **Number**: tipo de dato númerico.
* **String**: tipo de dato de cadena de caracteres.
* **Any**: se usa cuando no queremos declarar un tipo de dato, quiere decir que su contenido puede ser algun tipo de dato. Se puede usar cuando tenemos arrays que tienen varios tipos de datos.
* **Void**: se usa para declarar funciones que no retornan nada.

```typescript
const esVisible: boolean = false;
const tamaño: number = 6;
const nombre: string = "Vane";
const list:number[] = [1, 2, 3];
const nose: any = 4;
function saludo(): void {
    console.log("Este es un saludo!!");
}
```







