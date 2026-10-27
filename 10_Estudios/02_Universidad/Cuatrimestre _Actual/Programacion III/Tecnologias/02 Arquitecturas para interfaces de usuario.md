### Interfaz de usurio GUI

involucra codigo que puede ser extenso, se trata con los mismos estandares que el codigo de negocio, accede desde acciones a funcionalidad de negocio.
Esto ultimo tiene un riesgo de incluir negocio en el codigo de la interfaz,por ello es importante tener ambas secciones de codigo separadas
Seguimos el principio *Separated Presentation* al momento de diseñar el codigo de interfaces, diviendola en dos modulos logicos uno con el codigo logico y otro de presentacion.

### Arquitectura multi-capa
Se divide en niveles los cuales son tres en la mas habitual:
- Nivel presentacion: Contiene la interfaz de usuario y no procesa informacion, solo presenta la informacioin de forma adecuada.
- Nivel de aplicacion o negocio:Contiene la funcionalidad del sistema, por ejemplo incluye las clases y su implementacion
- Nivel de datos: contiene almacenamiento de la informaciony la funcionalidad asociada con el acceso a la informacion.
 

### Opciones de esta Arquitectura
### Forms and control: 
Controles visuales genericos llamados forms los cuales llaman al codigo de negocio, para ejecutar opciones por usuario,actualizar controles visuales. En ningun momento el codigo de negocio llama a la interfaz.
- Ventajas: 
	- Arquitectura sencilla y facil de implementar
	- toda logica de la GUI queda contenida en las clases de la interfaz

- Desventajas:
	- El codigo de interfaz queda demasiado recargado para interfaces complejas
	- La intergfaz debe saber en que momento cambia el estado del sistema,para actualizar controles
### Model-View-Controller
Separamos la logica de visualizacion de la de actualizacion del sistema
- Model: es la clase de negocio, debe representar el dominio del problema en cuestion 
- View: El codigo encargado de mostrar la informacion al usuario y que contiene los controles visuales
- Controller: Codigo encargado de tomar el input del usuario y tomar las acciones necesarias

Utilizamos patron de diseño Observer, para cada evento o grupo de eventos el codigo de negocio establece un observador, esto puede ser interno a la clase negocio o ser una interfaz separada.
Las clases de negocio en las que se producen cambio de estado tienen una lista de observadores. En cada momento que haya un cambio de estado los observadores son notificados.

- El modelo no conoce detalles de la interfaz
- Cuando el modelo cambia, la vista lo hace automaticamente
- Se puede tener mas de un observador


### Model-View-Presenter
 Combina MVC con Forms and Controls dando una capa de presentacion que combina responsabilidades de vista y controlador
 La vista es pasiva y solamente tiene controles visuales para mostrar informacion,no sabe como reaccionar ante las acciones del usuario
 Cuando se genera un evento sobre un control visual, se pasa el evento a un metodoo adecuado del presenter.El presenter decide que hacer y ejecutar los metodos adecuados
 Cuando el modelo se modifica, el presenter actualiza la vista, el presenter puede ser notificado por observadores o consultando metodos del modelo. 