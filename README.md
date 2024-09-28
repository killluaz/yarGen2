
# yarGen2.0
<pre>
------------------------------------------------------------------------
 __   __          _____            ___   ___
 \ \ / /__ _ _ __/ ____|__ _ __   |_  | / _ \
  \ V / _ \ '__| |  _| _ \ '_ \   / __/_/ // /
   | |  __/ |  | |_| |  __/ | | | /____(_)___/ 
   |_|\___|_|   \____|\___|_| |_|
         Yara Rule Generator
         by killuaz , Version 2.0
        Based on the original work by Florian Roth

  Note: Rules have to be post-processed
  See this post for details: anubiscybersecurity.xyz/blog/yarGen2.0)
------------------------------------------------------------------------
<pre>


🚀 Novedades en YaraGen 2.0
🔥 Mejoras Revolucionarias
🏎️ Optimización de Rendimiento

🚄 Implementación de procesamiento paralelo para análisis de archivos
🔧 Nueva función parse_sample_dir con multiprocesamiento
🧰 Función process_file para manejo individual de archivos

🎯 Creación de Reglas YARA Mejorada

🏅 Sistema de puntuación sofisticado para cadenas
🔢 Función get_rule_strings actualizada con ordenamiento por puntuación
🧠 Nuevas funciones score_string y calculate_entropy para evaluación de cadenas

📊 Estructuras de Datos Optimizadas

🗃️ Uso de defaultdict para gestión simplificada de estadísticas
🔡 Mejora en el manejo de cadenas UTF-16 y codificación base64

💻 Manejo de Opcodes Potenciado

🔗 Integración de opcodes en la generación de reglas
🔄 Adaptación de get_rule_strings para incluir opcodes

🛠️ Flexibilidad de Código Mejorada

🔍 Nueva función is_fullword para detección dinámica de palabras completas
🔀 Soporte para listas y diccionarios de elementos de cadena

⚙️ Generación de Reglas Optimizada

🎚️ Limitación inteligente del número de cadenas por regla
🏷️ Diferenciación entre cadenas de alta puntuación ($x) y normales ($s)

🛡️ Manejo de Errores y Logging Reforzado

🚨 Sistema robusto de manejo de excepciones
📝 Logging detallado para facilitar la depuración

💡 Impacto
Estas mejoras revolucionarias están diseñadas para:

🚀 Aumentar drásticamente la eficiencia en el procesamiento de archivos
🎯 Mejorar significativamente la calidad de las reglas YARA generadas
🔧 Hacer que YaraGen 2.0 sea más robusto y adaptable a diversos escenarios

¡Descubre el poder de YaraGen 2.0 y lleva tu análisis de malware al siguiente nivel! 🦠🔍


🔧 Parametros de linea de comandos

```
uso: yarGen.py [-h] [-m M] [-y min-size] [-z min-score] [-x high-scoring]
                 [-w superrule-overlap] [-s max-size] [-rc maxstrings]
                 [--excludegood] [-o output_rule_file] [-e output_dir_strings]
                 [-a author] [-r ref] [-l lic] [-p prefix] [-b identifier]
                 [--score] [--strings] [--nosimple] [--nomagic] [--nofilesize]
                 [-fm FM] [--globalrule] [--nosuper] [--update] [-g G] [-u]
                 [-c] [-i I] [--dropzone] [--nr] [--oe] [-fs size-in-MB]
                 [--noextras] [--debug] [--trace] [--opcodes] [-n opcode-num]

yarGen

optional arguments:
  -h, --help            show this help message and exit

Rule Creation:
  -m M                  Path to scan for malware
  -y min-size           Minimum string length to consider (default=8)
  -z min-score          Minimum score to consider (default=0)
  -x high-scoring       Score required to set string as 'highly specific
                        string' (default: 30)
  -w superrule-overlap  Minimum number of strings that overlap to create a
                        super rule (default: 5)
  -s max-size           Maximum length to consider (default=128)
  -rc maxstrings        Maximum number of strings per rule (default=20,
                        intelligent filtering will be applied)
  --excludegood         Force the exclude all goodware strings

Rule Output:
  -o output_rule_file   Output rule file
  -e output_dir_strings
                        Output directory for string exports
  -a author             Author Name
  -r ref                Reference (can be string or text file)
  -l lic                License
  -p prefix             Prefix for the rule description
  -b identifier         Text file from which the identifier is read (default:
                        last folder name in the full path, e.g. "myRAT" if -m
                        points to /mnt/mal/myRAT)
  --score               Show the string scores as comments in the rules
  --strings             Show the string scores as comments in the rules
  --nosimple            Skip simple rule creation for files included in super
                        rules
  --nomagic             Don't include the magic header condition statement
  --nofilesize          Don't include the filesize condition statement
  -fm FM                Multiplier for the maximum 'filesize' condition value
                        (default: 3)
  --globalrule          Create global rules (improved rule set speed)
  --nosuper             Don't try to create super rules that match against
                        various files

Database Operations:
  --update              Update the local strings and opcodes dbs from the
                        online repository
  -g G                  Path to scan for goodware (dont use the database
                        shipped with yaraGen)
  -u                    Update local standard goodware database with a new
                        analysis result (used with -g)
  -c                    Create new local goodware database (use with -g and
                        optionally -i "identifier")
  -i I                  Specify an identifier for the newly created databases
                        (good-strings-identifier.db, good-opcodes-
                        identifier.db)

General Options:
  --dropzone            Dropzone mode - monitors a directory [-m] for new
                        samples to processWARNING: Processed files will be
                        deleted!
  --nr                  Do not recursively scan directories
  --oe                  Only scan executable extensions EXE, DLL, ASP, JSP,
                        PHP, BIN, INFECTED
  -fs size-in-MB        Max file size in MB to analyze (default=10)
  --noextras            Don't use extras like Imphash or PE header specifics
  --debug               Debug output
  --trace               Trace output

Other Features:
  --opcodes             Do use the OpCode feature (use this if not enough high
                        scoring strings can be found)
  -n opcode-num         Number of opcodes to add if not enough high scoring
                        string could be found (default=3)
