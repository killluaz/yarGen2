------------------------------------------------------------------------
                   _____            ___   ___
    __ _____ _____/ ___/__ ___     |_  | / _ \
   / // / _ `/ __/ (_ / -_) _ \   / __/_/ // /
   \_, /\_,_/_/  \___/\__/_//_/  /____(_)___/ 
  /___/  Yara Rule Generator
         by killuaz Version 2.0
         Based on the original work by Florian Roth
   
  Note: Rules have to be post-processed
  See this post for details: https://www.anubiscybersecurity.xyz/post/yarGen2.0
------------------------------------------------------------------------


###  Que hay de nuevo en yaraGen2.0 ### 

### Optimización de rendimiento:

Implementación de procesamiento paralelo para el análisis de archivos.
Modificación de la función parse_sample_dir para utilizar multiprocesamiento.
Creación de la función process_file para manejar el procesamiento individual de archivos.


###Mejora en la creación de reglas YARA:

Implementación de un sistema de puntuación más sofisticado para las cadenas.
Modificación de la función get_rule_strings para ordenar las cadenas basándose en su puntuación.
Introducción de las funciones score_string y calculate_entropy para evaluar la relevancia de las cadenas.


###Optimización de estructuras de datos:

Uso de defaultdict para simplificar la gestión de estadísticas de cadenas y opcodes.
Mejora en el manejo de cadenas UTF-16 y cadenas codificadas en base64.


###Manejo mejorado de opcodes:

Integración de opcodes en la generación de reglas junto con las cadenas.
Adaptación de la función get_rule_strings para incluir opcodes en las reglas generadas.


###Mejora en la flexibilidad del código:

Implementación de la función is_fullword para determinar dinámicamente si una cadena debe ser tratada como palabra completa.
Adaptación del código para manejar tanto listas como diccionarios de elementos de cadena.


###Optimización de la generación de reglas:

Limitación del número de cadenas por regla basada en la puntuación.
Diferenciación entre cadenas de alta puntuación ($x) y cadenas normales ($s) en las reglas generadas.


###Mejora en el manejo de errores y logging:

Implementación de manejo de excepciones más robusto en funciones críticas.
Adición de mensajes de logging más informativos para facilitar la depuración.



Estas mejoras están diseñadas para aumentar la eficiencia del procesamiento de archivos, mejorar la calidad de las reglas YARA generadas, y hacer que el script sea más robusto y flexible en su manejo de diferentes tipos de datos y escenarios.
