
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

<div style="line-height: 1.3;">

<h1 style="margin-bottom: 10px;">🚀 Novedades en YaraGen 2.0</h1>

<h2 style="margin-top: 20px; margin-bottom: 10px;">🔥 Mejoras Revolucionarias</h2>

<h3 style="margin-top: 15px; margin-bottom: 5px;">🏎️ Optimización de Rendimiento</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🚄 Implementación de <strong>procesamiento paralelo</strong> para análisis de archivos</li>
  <li>🔧 Nueva función <code>parse_sample_dir</code> con multiprocesamiento</li>
  <li>🧰 Función <code>process_file</code> para manejo individual de archivos</li>
</ul>

<h3 style="margin-top: 15px; margin-bottom: 5px;">🎯 Creación de Reglas YARA Mejorada</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🏅 Sistema de puntuación sofisticado para cadenas</li>
  <li>🔢 Función <code>get_rule_strings</code> actualizada con ordenamiento por puntuación</li>
  <li>🧠 Nuevas funciones <code>score_string</code> y <code>calculate_entropy</code> para evaluación de cadenas</li>
</ul>

<h3 style="margin-top: 15px; margin-bottom: 5px;">📊 Estructuras de Datos Optimizadas</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🗃️ Uso de <code>defaultdict</code> para gestión simplificada de estadísticas</li>
  <li>🔡 Mejora en el manejo de cadenas UTF-16 y codificación base64</li>
</ul>

<h3 style="margin-top: 15px; margin-bottom: 5px;">💻 Manejo de Opcodes Potenciado</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🔗 Integración de opcodes en la generación de reglas</li>
  <li>🔄 Adaptación de <code>get_rule_strings</code> para incluir opcodes</li>
</ul>

<h3 style="margin-top: 15px; margin-bottom: 5px;">🛠️ Flexibilidad de Código Mejorada</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🔍 Nueva función <code>is_fullword</code> para detección dinámica de palabras completas</li>
  <li>🔀 Soporte para listas y diccionarios de elementos de cadena</li>
</ul>

<h3 style="margin-top: 15px; margin-bottom: 5px;">⚙️ Generación de Reglas Optimizada</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🎚️ Limitación inteligente del número de cadenas por regla</li>
  <li>🏷️ Diferenciación entre cadenas de alta puntuación ($x) y normales ($s)</li>
</ul>

<h3 style="margin-top: 15px; margin-bottom: 5px;">🛡️ Manejo de Errores y Logging Reforzado</h3>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🚨 Sistema robusto de manejo de excepciones</li>
  <li>📝 Logging detallado para facilitar la depuración</li>
</ul>

<h2 style="margin-top: 20px; margin-bottom: 10px;">💡 Impacto</h2>

<p style="margin-bottom: 5px;">Estas mejoras revolucionarias están diseñadas para:</p>
<ul style="margin-top: 5px; margin-bottom: 10px; padding-left: 20px;">
  <li>🚀 Aumentar drásticamente la eficiencia en el procesamiento de archivos</li>
  <li>🎯 Mejorar significativamente la calidad de las reglas YARA generadas</li>
  <li>🔧 Hacer que YaraGen 2.0 sea más robusto y adaptable a diversos escenarios</li>
</ul>

<h4 style="margin-top: 15px;">¡Descubre el poder de YaraGen 2.0 y lleva tu análisis de malware al siguiente nivel! 🦠🔍</h4>

</div>

<h2>🔧 Parametros de linea de comandos<h2>

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
