# Peritoneal-Dialysis-and-Home-Dialysis-event-manager
.html tool to register and monitor events in home kidney replacement therapy. Aimed to help Doctors monitor the main outcomes of their home programe.
Manual de Uso: Registro Integral de Diálisis Domiciliaria
Esta aplicación web funciona íntegramente en formato local (sin conexión a internet), lo que garantiza la privacidad de los datos clínicos. Toda la información se almacena en el navegador del equipo desde el que se ejecuta.

1. Estructura Principal y Navegación
La interfaz se divide en tres pestañas principales, seleccionables desde el menú superior:

Registro de Eventos: Gestión cronológica de las incidencias clínicas, entradas y salidas del programa.

Calculadora y Registro Kt/V: Evaluación de adecuación dialítica (modalidad dual DP y HDD).

Calculadora y Registro TEP: Evaluación del transporte peritoneal y ultrafiltración.

2. Pestaña: Registro de Eventos
Esta sección permite documentar el historial clínico y calcula automáticamente las métricas de la unidad (Pacientes activos en DP/HDD y Tasa de Peritonitis por paciente-año).

Ingreso de Datos
Introduce el SIP del paciente.

Selecciona la Categoría del evento. El menú Detalle se adaptará automáticamente.

Campos Condicionales: La interfaz despliega opciones adicionales según el evento seleccionado:

Infecciones (Peritonitis, orificio/túnel, bacteriemia de CVC): Aparecen campos para Patógeno, Antibiótico Empírico y Antibiótico Dirigido.

Fallo de Ultrafiltración: Habilita campos opcionales para registrar los valores de TEP y Kt/V asociados al fallo.

Colocación CVC: Solicita la localización anatómica.

Establece la Fecha del Evento (y la Fecha Fin si el evento ha concluido).

Indica el Desenlace.

Automatización Clínica: Si el desenlace es Fallecimiento o Cambio de técnica permanente, el sistema generará automáticamente un evento secundario de Salida de programa con la misma fecha, ajustando los contadores de pacientes activos al instante.

3. Pestaña: Calculadora y Registro Kt/V
Permite calcular y almacenar los parámetros de adecuación en función de la modalidad dialítica.

Diálisis Peritoneal (DP)
Requiere los datos demográficos (Sexo, Edad, Peso, Altura) para el cálculo automático del Volumen de Distribución (fórmula de Watson ajustada) y Superficie Corporal (fórmula de DuBois).

Se deben introducir los valores de Urea en suero, Urea en efluente y el Volumen Total Drenado en 24h (en litros).

Opcionalmente, se añade la diuresis residual para calcular el Kt/V renal. El sistema devuelve el Kt/V Peritoneal, Renal y Semanal Total.

Hemodiálisis Domiciliaria (HDD)
Se activa mediante el interruptor superior Modo HDD.

Requiere el peso pre y post-diálisis, ureas pre y post, volumen de ultrafiltración y la duración de la sesión en minutos.

Calcula simultáneamente el spKt/V (Daugirdas 2ª gen), eKt/V (ajuste de rebote) y el stdKt/V (estandarizado según frecuencia semanal).

4. Pestaña: Calculadora y Registro TEP
Evalúa las características de la membrana peritoneal.

Calcula automáticamente el cociente D/P de Creatinina y clasifica al paciente (Alto, Promedio Alto, Promedio Bajo, Bajo).

Sodium Sieving: Si se introducen los valores de Sodio D0 y D60, calcula la caída del sodio (Sieving) para evaluar la función de las acuaporinas. Estos campos, junto con la Ultrafiltración total a las 4 horas, son opcionales.

5. Gestión de Registros: Edición y Borrado
En la parte inferior de cada pestaña se encuentra la tabla del historial.

Editar (Icono Lápiz): Carga los datos del evento exacto en el formulario superior. Los botones cambian a color verde (Actualizar Registro). Si el evento tenía campos condicionales (ej. antibióticos en una peritonitis), estos se desplegarán y rellenarán automáticamente.

Borrar (Icono Papelera): Elimina el registro de la base de datos local previa confirmación.

6. Seguridad y Gestión de Datos (Copias y Exportación)
Dado que los datos residen en la memoria local del navegador (localStorage), es imperativo realizar copias de seguridad regulares para evitar pérdidas si se borra el historial o se cambia de ordenador.

Sistema de Backup (JSON)
Exportar Backup: Descarga un único archivo .json que contiene las tres bases de datos (Eventos, Kt/V y TEP).

Importar Backup: Permite restaurar los datos en cualquier equipo. Se puede hacer clic en el botón para buscar el archivo o arrastrar y soltar el archivo .json directamente sobre la pantalla.

Exportación para Análisis Estadístico (CSV)
Cada pestaña dispone de un botón Exportar CSV. La exportación está codificada en UTF-8 con BOM y separador de punto y coma, optimizada para su importación directa y estructurada en R o Excel sin problemas de formato o caracteres especiales.
