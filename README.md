# Sistema de Gestión de Turnos

## ¿De qué trata el proyecto?
Este proyecto es un sistema para administrar turnos en Java. Lo importante es que los datos se guardan automáticamente en un archivo de texto, así que cuando cierras el programa, los turnos no se pierden y siguen ahí al volver a abrirlo[cite: 1, 2].

## ¿Cómo está organizado el código?
El proyecto está dividido en cuatro paquetes para mantener todo ordenado y separar las tareas[cite: 2, 23]:

* **`turnos.modelo`**: Contiene lo básico del sistema, como la clase `Turno` y sus estados (`PENDIENTE`, `LLAMADO`, `ATENDIDO`)[cite: 5, 6].
* **`turnos.persistencia`**: Se encarga exclusivamente de leer y escribir en los archivos (`data/turnos.txt` y el historial)[cite: 2, 8]. Usa una interfaz llamada `TurnoRepository` para ocultar los detalles de los archivos al resto del programa[cite: 7, 8].
* **`turnos.servicio`**: Aquí están las reglas del programa (crear turnos en orden, evitar que se dupliquen y controlar cuándo se llama o se atiende a alguien)[cite: 12, 13].
* **`turnos.app`**: Tiene la clase `Main` para poner a prueba el sistema y ver cómo interactúan todas las piezas[cite: 14].

## Ideas clave del diseño
* **Independencia:** Gracias a usar una interfaz en la persistencia, la lógica del negocio no sabe de archivos[cite: 1, 7]. Si en el futuro nos toca cambiar los archivos por una base de datos (como Oracle o JDBC), solo agregamos una clase nueva sin romper el servicio[cite: 17, 18].
* **Portabilidad:** Usamos rutas relativas (`data/turnos.txt`) para que el proyecto funcione sin problemas en cualquier computadora[cite: 3, 14].
* **Manejo de errores:** El programa está preparado para arrancar limpio si el archivo aún no existe y maneja los errores de lectura de forma segura[cite: 11].
