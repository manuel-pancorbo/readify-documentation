## Summary
 * Qué es un event Storming
 * Pará que sirve
 * Bounded contexts?
 * Cómo encaja DDD con esto?
 * Cuál ha sido el resultado?
 * Cuáles son los bounded contexts de readify?
 * Cómo ayuda al desarrollo de la aplicación?


## Una breve introducción a DDD

Domain Driven Design es un enfoque de desarrollo de software ideado por Eric Evans en su libro “Domain-Driven Design — Tackling Complexity in the Heart of Software, 2004”. Eric Evans identifica lo que él llama el espacio del problema, en el cuál se encuentra el dominio de nuestra aplicación (qué problemas resuelve y cómo lo hace nuestra aplicación desde un punto de vista de negocio y agnóstico a la tecnología). A su vez Eric Evans nos propone lo siguiente:

 * Transformar un dominio grande en pequeños (y manejables) subdominios
 * Identificar los subdominios **core** para que nos ayuden a identificar qué es lo realmente **importante** de nuestro dominio (el core domain es aquel que nos diferencia de nuestra competencia y en el que nos interesará invertir más en términos de tiempo, económicos... etc)
 * Colaborar con los expertos de dominio para encontrar las mejores soluciones a los problemas de cada subdominio o para revelar nuevas oportunidades de negocio.
 * Hacer que todos los equipos involucrados (técnicos, negocio, marketing... etc) hablen utilizando la misma terminología y sean capaces de construir un **lenguaje ubicuo**

Una vez identificados los subdominios del problema, estaremos capacitados para acercarnos a lo que Eric Evans denomina el espacio de la solución, dónde habita el concepto de **bounded context** que no es más que cada una de las divisiones del modelado del dominio en límites conceptuales (casi semánticos), lógicos y tangibles que protejan la integridad de los mismos.

Un bounded context es una solución específica, una solución que ha de guiar y materializar el desarrollo poniendo en un primer plano el lenguaje ubicuo previamente desarrollado. Por ejemplo, el lenguaje ubicuo que nos ocupa en el problema de Readify es un lenguaje que no habla de usuarios y productos, habla de lectores, de autores (escritores) y de libros. Y esa terminología es la que habrá de usarse tanto en conversaciones de negocio como en la implementación de los bounded contexts.

También hay que destacar que DDD no impone una arquitectura software o una forma de implementar la solución. DDD nos da un conjunto de herramientas (lenguaje ubicuo, subdominios, bounded contexts) que ha de guiarnos en la realización de una solución abstraída de la tecnología que finalmente se use.

## ¿Qué es un Event Storming?

Ya hemos introducido brevemente lo que nos aporta DDD, ¿pero cómo identificamos esos conceptos que nos propone? Aquí es dónde entra en juego el **Event Storming**.

Event Stroming es un talller con un formato flexible que permite la exploración colaborativa de un determinado dominio concreto. Se suele usar para diferentes fines:

* Validar la salud de un modelo de dominio ya existente y descubrir areas de mejora.
* Explorar la viabilidad de una nueva línea de negocio
* Y la más importante, explorar y descubrir un dominio que a priori se desconoce y sentar las bases para diseñar un sistema mantenible y que pueda evolucionar rapidamente con el negocio. Esta práctica también es conocida como Big Picture Event Storming

Es este último escenario el que motiva que lo realice para este proyecto. En esencia el taller consistirá en identificar ciertos elementos típicos de DDD (eventos de dominio, entidades, actores...) y de agruparlos para conseguir identificar subdominios y posteriormente los bounded contexts y la relación entre ellos.

## Subdominios

Tras realizar el ejercicio de Event Storming, a primera vista podemos identificar los siguientes subdominios:

* Publicación de libros/capítulos: se compone de la publicación del libros/capítulos de la gestión de los precios por parte del autor y de las reglas de negocio derivadas de este proceso de publicación y del mantenimiento del catálogo
* Biblioteca del lector: compra por parte del lector del material elegido y mantenimiento de la biblioteca del lector
* Reseñas de libros: se compone de las posibles revisiones que un lector puede hacer a los libros que ha leído así como la posible moderación que puedan tener (para evitar contenido inapropiado o spoilers).
* Registro de usuario: se compone del proceso de registro y de las reglas asociadas al mismo (como validación de email... etc)

## Bounded contexts

Una vez el espacio del problema se ha diseñado, podemos centrarnos en traducirlo al espacio de la solución mediante bounded contexts que nos delimiten la solución en piezas más manejables.

* Publicación de libros: aquí se contendrá el catalogo de libros disponibles y de los distintos mecanismos de publicación de los mismos.
* Biblioteca del lector: aquí se implementará el proceso de compra y el mantenimiento de la biblioteca del lector.
* Search and discovery: contexto secundario que servirá de soporte a los contextos de Publicación de libros y Biblioteca del lector para que el lector encuentre de forma fácil contenido afín y relevante para él.
* Reseñas de libros: en este contexto se imlementarán las reseñas que el lector podrá emitir del contenido que ha comprado
* Engadgement: este será un contexto secundario que servirá de soporte al resto de contextos para enviar notificaciones (push, email) a los distintos tipos de usuario para fomentar el engadgement con la aplicación
* Registro de usuario / Autenticación: este será un contexto secundario en el que se implementará el registro de usuario así como el inicio/cierre de sesión.



## Bibliografía
“Domain-Driven Design — Tackling Complexity in the Heart of Software" - Eric Evans - 2004
"DDD the first 15 years" - The DDD Community - 2019
https://robertbasic.com/blog/bounded-contexts-and-subdomains/
https://martinfowler.com/bliki/BoundedContext.html
Implementing Domain-Driven Design - Vaughn Vernon
