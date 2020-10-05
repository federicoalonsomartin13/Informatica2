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

- __EJERCICIO 35__: 

    Hacer un programa que tome los datos de contacto de una persona (Nombre, Apellido, edad, teléfono, mail) y los cargue, en forma directa, en una pila de memoria dinámica. Imprimir en pantalla y cargar en un archivo llamado "contactos.dat", de organización secuencial, los registros ingresados por el usuario si la persona tiene una edad mayor a 21 años.

- __EJERCICIO 36__:

    Hacer un programa que lea al archivo "contactos.dat" creado en el __Ejercicio 35__ y crear una lista, en memoria dinámica, ordenada alfabéticamente. Una vez creada la lista guardarla en un archivo de organización directa llamado "contactos_ordenados.dat" imprimiendola en pantalla.

- __EJERCICIO 37__:

    Existe un archivo llamado "datos.dat", de tipo binario, cuya organización es secuencial. Los datos están organizados según la siguiente estructura:   
                                                                                 
    ```c
    struct d{                                                                                            
    long clave; //Clave o Id del registro
    
    char d[30]; // Descripcion                                                                                          
    unsigned char tipo; //Tipo de datos como entero sin signo                                                                                                                                            
    char b; //'A':Alta 'B':Baja                                                                                                                                                                          
    }
    ```
                            
    Se Pide:
    Realizar una funciún que pase como parámetro la clave, entre otros parámetros, y apile dos valores, la Clave y su posición física respecto 
    al archivo (registro 1, 2, etc), si es que el campo tipo tiene el bit 4 con valor 1. En caso de no encontrarlo mostrar por pantalla "Registro no encontrado".
    La función debe devolver el puntero de pila.
    Realizar el main con varias llamadas a dicha función y proceder a mostrar las descripciones del archivo, mediante la pila como acceso directo, __NO USAR VARIABLES GLOBALES__.             
- __EJERCICIO 38__:

    Hacer una cola con los valores muestreados de un cuarto de ciclo de una señal sinusoidal, en 8 bits, para luego recorrerla y recomponer la señal completa. Las muetras deberán ir de 127 a -127 utilizando el bit más significativo en 1 para los valores negativos y en 0 para los valores positivos. Imprimir en pantalla los valores.
- __EJERCICIO 39__:

    Hacer un programa que tome los datos de medición de potencia, cargados por el usuario, de un sistema de medición a distancia.

    Los datos que cargará el usuario tienen la siguiente estructura:
    ```c
        char desc[60];
        unsigned char potencia;
        unsigned int estado;
    ```
    Donde estado es la multiplicación del valor ASCII de la primer letra de la descripción por la potencia. 
    Los datos cargados se deberán guardar en una lista ordenada, de mayor a menor, del valor de potencia. Una vez finalizada la carga guardar los datos en un archivo de organización directa llamado "potencia.dat" imprimiendo en pantalla los datos.
   
- __EJERCICIO 40__:

     Utilizando el archivo “potencia.dat” creado en el __Ejercicio 39__, realizar una función que pase como parámetro, entre otros datos, la clave del registro (id). 
     
     La función ubicará el registro correspondiente al id pasado como parámetro, y utilizando punteros imprimirá la primera palabra del campo "desc" en forma inversa, además cambiará el estado del bit 3 para luego actualizar el archivo. Además, se agregará a una pila la potencia cuando los bits 0 y 2, del campo estado, estén encendidos, en caso contrario se agregará el registro al archivo “salida.dat” de organización secuencial.
