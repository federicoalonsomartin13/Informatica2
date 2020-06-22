# Práctica con Archivos

En la Práctica de esta clase, planteamos el ABM en archivos Secuenciales.
Se tiene un programa que guarda en un archivo a la estructura de caracteres 8x5 formada por 5 variables de 8 bits, es decir, utilizando manejo de bits para almacenar cada uno de los caracteres.

La estructura de los caracteres es:
```c
typedef struct {
  char ascii;
  char draw[5];
  char flag;
}letra;

```
El programa tiene un control de usuarios con contraseña, con su ABM, para usarlo de ejemplo.

Ejemplo: [Acceder al código de Ejemplo](https://github.com/DamRCorba/Informatica2/tree/master/Clase10/Ejemplos/usuarios)


## Práctica Propuesta

__Ejericio 28__: Ampliar el código de ejemplo con el alta de un caracter.

__Ejericio 29__: Ampliar el código de ejemplo con la modificación de un caracter.

__Ejericio 30__: Ampliar el código de ejemplo con la baja de un caracter.

__Ejericio 31__: Hacer un programa que emule al comando copy de Windows. __copy archivo_original nuevo_arhivo_copiado__
