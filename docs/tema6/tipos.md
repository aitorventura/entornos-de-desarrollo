<a id="tipos"></a>

# 1. Tipos de diagramas de comportamiento

![Diagramas de comportamiento](diapositivas/tipos.pdf){ type=application/pdf style="width:100%;min-height:80vh" }

---

## ¿Qué son los diagramas de comportamiento?

En UML los diagramas se dividen en dos grandes grupos:

- **Estructurales**: muestran cómo está organizado el sistema (clases, objetos, componentes…). El diagrama de clases del tema anterior es uno de ellos.
- **De comportamiento**: muestran **qué hace el sistema** y **cómo lo hace**. Describen flujos, interacciones y estados.

Los diagramas de comportamiento son especialmente útiles al principio del proyecto, cuando hay que entender cómo debe funcionar el sistema antes de empezar a programar.

---

## Tipos de diagramas de comportamiento

| Diagrama | Para qué sirve |
|---|---|
| **Casos de uso** | Describir qué puede hacer el sistema desde el punto de vista del usuario |
| **Secuencia** | Mostrar el orden cronológico en que los objetos se envían mensajes |
| **Comunicación** | Mostrar las relaciones entre objetos al intercambiar mensajes |
| **Actividad** | Representar el flujo de un proceso o algoritmo paso a paso |
| **Estados** | Mostrar cómo cambia el estado de un objeto a lo largo del tiempo |

!!! info "Idea clave"
    Ningún diagrama lo explica todo. En la práctica se combinan: un diagrama de casos de uso para entender los requisitos, uno de secuencia para diseñar cómo se comunican los objetos, y uno de actividad para aclarar un flujo complejo.

---

## Campo de aplicación

- **Análisis de requisitos**: los casos de uso ayudan a definir qué debe hacer el sistema con los clientes o usuarios finales.
- **Diseño**: los diagramas de secuencia y comunicación detallan cómo interactúan los objetos.
- **Documentación de lógica**: los diagramas de actividad y de estados explican procesos internos complejos.
