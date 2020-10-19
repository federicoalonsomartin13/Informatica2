# Pilas, Colas y Listas

## Introducción Teórica
### Pilas

Las pilas son estructuras de datos del tipo FILO, First In Last Out, o en español primero en entrar último en salir.

Una estructura de pila tiene la siguiente forma:

```c
typedef struct {
    datos_t misDatos;
    void *pila;
} pila_t;
```

En el ejemplo el puntero de pila es del tipo __void__ esto es porque al ser una definición de tipo, los compiladores no pueden utilizar un tipo de datos desconocido como el de *pila_t* que hasta ese momento no fue declarado.

> Recordemos que los punteros ocupan siempre el mismo tamaño de datos, y en la práctica no hay diferencia en el tipo de datos que se utilice para armar la estructura de pila. Una estructura de pila no usa a su puntero anterior para operar algebraicamente por lo que el tipo de datos del puntero queda en segundo lugar. 

El puntero "pila", apunta a la siguiente posición de la pila, o sea, al elemento de abajo. El primer elemento ingresado apunta a null.
En nuestro código tenemos un puntero que apunta siempre al último elemento, el más "nuevo", y este tiene en sus datos la información del elemento de abajo de él.

Entonces las pilas solo pueden recorrerse en un sentido para la carga y en sentido inverso para la lectura.

### Colas

Las colas son estructuras de datos reversibles, las cuales pueden ser recorridas de igual modo que las pilas o en sentido inverso, permitiendo así un flujo del tipo FIFO, First In First Out, primero en entrar primero en salir.

La estructura de cola es:

```c
typedef struct {
    datos_t misDatos;
    void *sig;
    void *ant;
} cola_t;
```
> Recordemos que los punteros ocupan siempre el mismo tamaño de datos, y en la práctica, no hay diferencia en el tipo de datos que se utilice para armar la estructura de cola. Una estructura de cola no usa a su puntero para operar algebraicamente por lo que el tipo de datos del puntero queda en segundo lugar. 

Los punteros "sig" y "ant" apuntan al elemento siguiente y anterior de la cola respectivamente. Esto nos permite que un elemento de la cola sepa cuales son los elementos en ambos lados. El primer elemento ingresado siempre tendrá a su puntero "ant" apuntando a null. El último elemento de la cola siempre tendrá a su puntero "sig" apuntando a null. Esto es porque si es el primero no puede haber anterior y si es el último no puede conecer al siguiente. 
Sabiendo esto se puede recorrer la cola de extremo a extremo desde cualquier elemento perteneciente a ella.

### Listas

Las listas son colas ordenadas, además de la estructura de datos tradicional tienen una clave la cual se utiliza para ordenarla y ubicar los registros según la necesidad del programa. 

## TRABAJO PRÁCTICO

- __EJERCICIO 41__: 

    El depósito de la empresa __*CosmeFulanito*__ necesita cargar su stock de repuestos en forma ordenada. Para dicha tarea se solicitó categorizar a los respuestos bajo la siguiente estructura de datos:
     ```c
    typedef struct{
        long partNumber;
        long serialNumber;
        char descripcion[40];       
        chat ubicacion[100];        
    }repuestos_t;
    ```
    Los repuestos no están ordenados, se solicita cargarlos en una lista, la cual ordene por descripción a los repuestos para luego guardarlos en un archivo de *stock* con organización secuencial.
    
    > - Imprimir en pantalla la lista con cada inserción. 
    > - El archivo se generará cuando el usuario decide no cargar mas productos.
- __EJERCICIO 42__:

     El proveedor de repuestos de __*CosmeFulanito*__ informó que una partida de repuestos salió con falla y debe ser devuelta. Para identificar la partida, el proveedor indicó que la falla fue en el partNumber: 1234 que tiene números de serie con el bit 3 y 5 en 1.

    Para estas tareas se solicita:
    - Hacer una cola con todos los registros fallados
    - Realizar la baja física a todos los repuestos fallados 
    - Crear un archivo donde se vuelque el contenido de la cola en orden inverso.

- __EJERCICIO 43__:

    El servicio técnico de __*CosmeFulanito*__ recibe órdenes de trabajo diarias. Las mismas son cargadas en un archivo secuencial por el personal de recepción bajo la siguiente estructura de datos:
     ```c
    typedef struct{
        long numeroDeOrden;
        char cliente[40];       
        char descripciondeFalla[200];        
        char modelo[65];
        char fecha[10];
        char hora[10];
    }repuestos_t;
    ```
    Se pide:
    - Hacer una pila con las órdenes de trabajo de forma tal que la más vieja sea la última en cargarse.

- __EJERCICIO 44__:

    El servicio técnico utiliza la pila generada en el ejercicio 43 en su labor diaria. Cada técnico toma una tarea de la pila y genera un orden de extracción de repuestos al depósito. Para optimizar los viajes al depósito se arma una lista con los repuestos que cada orden necesita utilizando la siguiente estructura:

    ```c
    typedef struct{
        repuestos_t repuesto;        
        int cantidad;
    }extraccionRepuestos_t;
    ```

    Se pide cargar la lista de repuestos solicitados por los técnicos. Tener en cuenta que varios técnicos pueden necesitar la misma parte, y en esos casos se debe incrementar la cantidad pedida en la lista. 
 

- __EJERCICIO 45__:
    
    La lista creada en el ejercicio 44 es procesada por el depósito. 
    Para dicha tarea se pide hacer un programa que:
    - Descuente las cantidades solicitadas del archivo de stock, creado en el __Ejercicio 41__.
    - Hacer una cola con los repuestos en los que no se encontró stock suficiente para poder notificar a los clientes la demora de la reparación. 

