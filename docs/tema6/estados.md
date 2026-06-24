<a id="estados"></a>

# 5. Diagrama de estados

---

## ¿Para qué sirve?

Un diagrama de estados muestra los **distintos estados por los que puede pasar un objeto** a lo largo de su vida y qué eventos provocan el cambio de un estado a otro.

Es útil cuando un objeto tiene un comportamiento que varía según en qué situación se encuentre. Por ejemplo, un pedido no se comporta igual si está "pendiente" que si está "enviado" o "cancelado".

!!! info "Idea clave"
    No todos los objetos necesitan un diagrama de estados, solo aquellos cuyo comportamiento cambia significativamente según su estado interno.

---

## Elementos del diagrama

### Estado inicial

Círculo negro sólido, igual que en el diagrama de actividades. Marca el punto de partida.

### Estado

Rectángulo con esquinas redondeadas que contiene el **nombre del estado**. Opcionalmente puede incluir acciones internas con las etiquetas `entry` (al entrar), `do` (mientras dura) y `exit` (al salir).

### Transición

Flecha que une dos estados. Indica el **cambio de estado**. Se etiqueta con:

- El **evento** que la dispara
- Una **condición de guarda** opcional entre corchetes: `[saldo > 0]`
- Una **acción** opcional tras la barra: `/ cobrar()`

Formato: `evento [condición] / acción`

??? note "Para saber más — no entra en examen ni actividades"

    **Acciones internas de un estado**

    Dentro de un estado puedes describir qué hace el sistema mientras está en él:

    | Etiqueta | Cuándo se ejecuta |
    |---|---|
    | `entry` | Al **entrar** en el estado |
    | `do` | **Mientras** el sistema permanece en el estado |
    | `exit` | Al **salir** del estado |

    **Detalle del formato de transición**

    | Parte | Obligatorio | Descripción |
    |---|---|---|
    | `estímulo` | Sí | El evento que dispara el cambio |
    | `[condición]` | No | Expresión booleana; si es falsa, no se cambia de estado |
    | `/ efecto` | No | Acción que se ejecuta antes de cambiar de estado |

    Las **transiciones reflexivas** apuntan al mismo estado de origen: sirven para ejecutar un efecto sin cambiar de estado.

    **Submáquinas de estado**

    Un estado puede contener una máquina de estados completa. Sirve para reutilizar un patrón que aparece en varios sitios del diagrama (p.ej. "introducir PIN" en apertura de puerta y en cambio de configuración).

    **Pseudo-estado de elección**

    Un rombo al que llega una sola transición y del que salen dos o más con condiciones de guarda:

    ```
    [Estado A] → ◇ → [condición verdadera] → [Estado B]
                  └→ [condición falsa]    → [Estado C]
    ```

### Estado final

Círculo con borde grueso. Marca el fin del ciclo de vida del objeto.

---

## Ejemplo: pedido en una tienda online

```
● → [Pendiente] → pagar() → [Pagado] → enviar() → [Enviado] → entregar() → [Entregado] → ⊙
         ↓                     ↓
      cancelar()            cancelar()
         ↓                     ↓
    [Cancelado] ←────────────────
```

Estados posibles de un pedido:
- **Pendiente**: el pedido existe pero aún no se ha pagado
- **Pagado**: se ha confirmado el pago
- **Enviado**: el paquete está en camino
- **Entregado**: el cliente ha recibido el pedido
- **Cancelado**: el pedido se ha anulado (desde pendiente o pagado)

---

## Ejemplo: semáforo

```
● → [Rojo] → temporizador() → [Verde] → temporizador() → [Ámbar] → temporizador() → [Rojo]
```

El semáforo solo tiene tres estados y siempre sigue el mismo ciclo. No hay condiciones de guarda: la única cosa que dispara la transición es el temporizador.

---

## Diferencia con el diagrama de actividades

| Diagrama de actividades | Diagrama de estados |
|---|---|
| Describe el flujo de **un proceso** | Describe el ciclo de vida de **un objeto** |
| Las cajas son acciones (verbos) | Las cajas son estados (sustantivos o adjetivos) |
| Las flechas son el orden de pasos | Las flechas son eventos que cambian el estado |
