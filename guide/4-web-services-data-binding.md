# Usando WebServices y DataBinding

En el ejercicio anterior creamos el componente `<task-card>`. Lo que vamos a hacer ahora es obtener una lista de tareas de una API y usar one-way data binding para mostrarlas (en el ejercicio que viene vamos a ver two-way data binding).

El servicio ya esta creado de antemano y se llama `<task-service>` (lo pueden encontrar en `/task-service/task-service.html`). Este servicio se conecta a una API fake para hacer el request de todas las tareas a realizar. Vamos a usar este servicio desde el element `<task-list>` el cual se encargara de mostrar la lista de tareas.

## Agregando el servicio

#### Tarea 1: Importar el servicio `<task-service>` en el componente `task-list`

#### Tarea 2: Instanciar el servicio `<task-service>`

````html
<task-service id="service" tasks="{{allTasks}}"></task-service>
<!-- Insertar el resto del contenido desde aqui -->
````

Con el `{{}}` estamos creando un DataBinding entre la lista de tareas devueltas por el servicio y una variable de instancia de nuestro WebComponent. Esto quiere decir que ni bien lleguen las listas de tareas del servidor, nosotros vamos a poder acceder a las tareas via `this.allTasks` desde la `<task-list>`.

> Nota: si se fijan en `task-service.html` van a ver que se crea un array de `tasks`. Lo que estamos haciendo al instanciar el template es crear una variable `allTasks` y asignarle el valor del array de `tasks`. Para generalizarlo: `variable-del-service={{variable-para-binding}}`

## Mostrando el listado en la home

El `<task-list>` lo vamos a estar mostrando en nuestro `home-page.html`. Entonces, las tareas a realizar son las siguientes:

#### Tarea 3: Importar el `<task-list>` en nuestro home

#### Tarea 4: Usarlo dentro del `<div class="container">`. Pongamosle de `id` `list` al `<task-list>`

> **Tip:** Para ver que se haya importado el `<task-list>` correctamente, pueden poner en el contenido de la `<task-list>` un `<p>Hola</p>` y luego chequear que se haya mostrado en el home.

## Creando el listado de tareas

Ahora que ya obtenemos las tareas del servicio, lo que nos resta hacer es iterar sobre las mismas y mostrarlas en nuestro `<task-list>`.

#### Tarea 5: Mostrar por cada tarea una `<task-card>` con la informacion de su nombre y descripcion. Las propiedas a mostrar de la task son `task.name` y `task.description`. Usar el siguiente template como referencia:

````html
<div layout vertical center>

  <template repeat="{{task in allTasks}}">
    <!-- Insertar aqui una task card por cada task -->
  </template>

</div>
````

El `repeat` es una instruccion que itera por la lista de tareas. Cada tarea dentro de la lista es asignada a una variable temporal `task`, la cual puede ser usada dentro del `<template>`. En este caso, debemos mostrar los datos de la variable `task` en una `<task-card>`.

> **Tip:** Es necesario primero importar la `<task-card>` y luego usaremos bindings con `{{}}` para mostrar las propiedades de la tarea.

Ahora, deberiamos ver el siguiente listado de tareas

![result](https://cloudup.com/cG15DAWYgXr+)

[Continuemos agregando una forma de poder procastinar las tareas](5-procastinating-tasks.md).
