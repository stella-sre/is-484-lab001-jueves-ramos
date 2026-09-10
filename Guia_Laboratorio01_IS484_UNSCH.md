ffi a Ayee UNIVERSIDAD NACIONAL DE SAN CRISTOBAL DE HUAMANGA Real, es pron Nacional 

## 3.2. Esquema PEAS del agente inteligente 

Un agente percibe su entorno mediante sensores y actúa sobre él mediante actuadores. Es racional cuando, dada su secuencia de percepciones, elige la acción que maximiza su medida de desempeño esperada. El esquema PEAS describe cualquier agente mediante estos cuatro elementos: 

-  P: Performance (Desempeño): ¾cómo se mide si el agente lo está haciendo bien? 

-  E: Environment (Entorno): ¾en qué contexto opera? 

-  A: Actuators (Actuadores): ¾qué acciones puede ejecutar el agente? 

-  S: Sensors (Sensores): ¾qué percibe el agente del entorno? 

## 3.3. Tipos de agente 

-  Reactivo simple: actúa solo según la percepción actual, sin ningún tipo de memoria del pasado. Por ejemplo, un termostato enciende o apaga la calefacción únicamente según la temperatura que mide en ese instante, sin recordar mediciones anteriores. 

-  Basado en modelos: mantiene un estado interno que representa aspectos del entorno que no puede observar directamente en el momento. Un robot aspirador que recuerda qué zonas de la casa ya limpió, aunque no las esté viendo, es un ejemplo de este tipo. 

-  Basado en objetivos: evalúa distintas secuencias de acciones posibles y elige la que lo acerca a una meta explícita. Un sistema de navegación GPS que planica una ruta completa hacia un destino, en lugar de decidir cuadra por cuadra, actúa con esta lógica. 

-  Basado en utilidad: en lugar de un objetivo binario (lo logra o no lo logra), compara varias acciones posibles según qué tan buenas son, no solo si funcionan. Un sistema de recomendación de rutas que no solo busca llegar, sino la opción más rápida, económica y segura al mismo tiempo, usa una función de utilidad. 

-  De aprendizaje: mejora su regla de decisión con la experiencia, ajustando su comportamiento a partir de datos en lugar de seguir reglas jas escritas de antemano. Un ltro de spam que se vuelve más preciso mientras más correos marca el usuario como spam o no spam es un agente de este tipo. 

## 3.4. Áreas de aplicación de la IA (taxonomía ocial) 

Las áreas de aplicación de la Inteligencia Articial son las siguientes: 

|Área|Qué resuelve|Ejemplo cotidiano|
|---|---|---|
|Visión articial|Que una máquina<br>reconozca objetos, rostros<br>o escenas en imágenes o<br>video|Cámaras de seguridad que<br>detectan personas,<br>reconocimiento facial de un<br>celular|
|Procesamiento de<br>lenguaje natural<br>(NLP)|Que una máquina entienda<br>o genere texto o habla<br>humana|Traductores automáticos,<br>chatbots, corrección<br>ortográca|
|Sistemas de|Predecir qué le gustaría a|Porque viste esto en|
|recomendación|un usuario según su<br>comportamiento previo|Netix, productos<br>relacionados en una tienda<br>en línea|



2 

|Área|Qué resuelve|Ejemplo cotidiano|
|---|---|---|
|Robótica|Que un sistema físico<br>perciba su entorno y actúe<br>sobre él en el mundo real|Aspiradoras robot, brazos<br>robóticos de ensamblaje,<br>drones autónomos|
|Sistemas expertos|Reglas de conocimiento<br>codicadas de un experto<br>humano para diagnosticar<br>o decidir|Sistemas de diagnóstico<br>médico basados en reglas|
|Reconocimiento de<br>patrones|Identicar regularidades o<br>similitudes en datos|Detección de huellas<br>dactilares, identicación de<br>anomalías en señales|
|Análisis predictivo|Estimar valores o eventos<br>futuros a partir de datos<br>históricos|Predicción de tráco,<br>pronóstico de demanda|



Nota: Estas áreas no son excluyentes entre sí: un mismo sistema puede tocar varias a la vez (ej. un asistente de voz usa NLP y análisis predictivo). Para la Actividad 4.3, identicar el área predominante: la que mejor describe el problema central que resuelve el sistema. 

# 4. Actividades de Laboratorio 

## 4.1. Instalación y vericación del entorno de trabajo 

## Parte A: Diagnóstico rápido 

Indicar si ya se cuenta con Python instalado y funcional en el equipo. Si es así, continuar directamente en la Parte D. 

Parte B: Vericar la instalación de Python 

<mark>python --version</mark> 

Si el comando no es reconocido, descargar e instalar Python desde https://www.python.org/ downloads/. 

**_⊗_** Atención: En Windows, durante la instalación es obligatorio marcar la casilla Add Python to PATH en la primera pantalla del instalador. Omitir este paso es la causa más frecuente de que el comando python no sea reconocido después en la terminal. 

Parte C: Crear un entorno virtual e instalar Jupyter 

<mark>python -m venv venv_ia1 .\venv_ia1\Scripts\Activate.ps1</mark> 

<mark>pip install numpy pandas matplotlib scikit-learn scipy jupyter</mark> 

Nota: Si PowerShell muestra un error de ejecución de scripts deshabilitada (PSSecurityException) al activar el entorno, ejecutar una sola vez Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned y conrmar con S. No requiere permisos de administrador. 

Parte D: Vericar que Jupyter se ejecuta correctamente 

3 

<mark>jupyter notebook</mark> 

Debe abrirse una pestaña del navegador con el panel de Jupyter. Crear un nuevo notebook (New _→_ Python 3) y renombrarlo como IS484_Lab01_Apellido.ipynb. 

Nota: Si el equipo del laboratorio no permite instalar software (sin permisos de administrador), usar Google Colab (https://colab.research.google.com) como alternativa temporal. 

## 4.2. Vericación de las bibliotecas del curso 

Parte A: Vericar versiones 

<mark>import numpy as np import pandas as pd import matplotlib import sklearn import scipy print("NumPy:", np.__version__) print("Pandas:", pd.__version__) print("Matplotlib:", matplotlib.__version__) print("Scikit-learn:", sklearn.__version__) print("SciPy:", scipy.__version__)</mark> 

Parte B: Vericación funcional (ejemplo: un sistema anti-fraude) 

Se genera un conjunto simulado de 300 transacciones (con más probabilidad de fraude en horario de madrugada y en montos altos) y se visualiza, para observar el patrón antes de aplicar cualquier algoritmo (lo que se hará desde la Semana 5): 

<mark>import numpy as np import pandas as pd import matplotlib.pyplot as plt np.random.seed(42) n = 300</mark> 

<mark>hora = np.random.randint(0, 24, n) monto = np.random.exponential(scale=150, size=n) + 10</mark> 

<mark># Fraude mas probable de madrugada (0-5h, 23h) y en montos altos prob_fraude = 0.03 + 0.35 * ((hora <= 5) | (hora >= 23)) + 0.25 * (monto > 400) prob_fraude = np.clip(prob_fraude, 0, 0.9) es_fraude = (np.random.rand(n) < prob_fraude).astype(int)</mark> 

<mark>transacciones = pd.DataFrame({"hora": hora, "monto": monto, "es_fraude": es_fraude})</mark> 

<mark>colores = {0: "#0ca30c", 1: "#d03b3b"} # verde = legitima, rojo = fraude etiquetas = {0: "Legitima", 1: "Fraude"}</mark> 

<mark>fig, ax = plt.subplots(figsize=(10, 6), facecolor="#fcfcfb") ax.set_facecolor("#fcfcfb")</mark> 

<mark>for valor in [0, 1]: subset = transacciones[transacciones["es_fraude"] == valor] ax.scatter( subset["hora"], subset["monto"],</mark> 

4 

<mark>s=70, alpha=0.75, c=colores[valor], edgecolors="white", linewidths=0.6, label=etiquetas[valor], )</mark> 

<mark>ax.set_title("Transacciones por hora y monto", fontsize=15, color="#0b0b0b", pad=14) ax.set_xlabel("Hora del dia", fontsize=11, color="#52514e") ax.set_ylabel("Monto (S/)", fontsize=11, color="#52514e") ax.set_xticks(range(0, 24, 2)) ax.grid(True, color="#e1e0d9", linewidth=0.8) ax.spines[["top", "right"]].set_visible(False) ax.legend(title="Tipo de transaccion", frameon=False, loc="upper right")</mark> 

<mark>plt.tight_layout() plt.show()</mark> 

<mark>print("Total transacciones:", len(transacciones), "| Fraudes:", transacciones["es_fraude"].sum())</mark> 

Nota: Si alguna importación falla, revisar la instalación con pip list dentro del entorno virtual activo. No avanzar a la Sección 4.3 con un entorno incompleto. 

## 4.3. Clasicación de sistemas con Inteligencia Articial 

Parte A: Elegir dos sistemas de la siguiente lista (o proponer uno propio): 

-  Recomendador de Netix/Spotify, ltro anti-spam de Gmail, asistente de voz (Siri/Alexa) 

-  Sistema de reconocimiento facial, chatbot de atención al cliente, predicción de tráco 

-  Sistema anti-fraude bancario en tiempo real, balanceador de carga inteligente, sistema de autenticación biométrica 

Parte B: Completar, para cada sistema elegido, entrada, salida, tipo de problema (clasicación/regresión/clustering/generación) y área de IA, usando únicamente las siete categorías ociales listadas en la Sección 3.4. 

## 4.4. Representación de un agente inteligente (PEAS) 

Parte A: Retomar uno de los sistemas técnicos analizados en la Sección 4.3 (fraude, balanceo de carga, biometría), para exigir mayor rigor que con un ejemplo de consumo masivo. 

Parte B: Completar la cha PEAS del agente: 

-  Percepción (S), Acciones (A), Entorno (E), Objetivo, Medida de desempeño (P) 

-  Tipo de agente (reactivo, basado en modelos, en objetivos, en utilidad, de aprendizaje) 

-  ¾Es racional? Justicar en 1 a 2 líneas 

-  ¾Corresponde a IA estrecha o IA General? Justicar 

## 4.5. Entregable del Trabajo en Clase 

-  Tabla de clasicación de sistemas (Sección 4.3, Parte B). 

5 

-  Ficha PEAS del sistema técnico elegido (Sección 4.4, Parte B), incluyendo racionalidad e IA estrecha/General. 

Nota: Entregar ambas chas (foto legible o documento escaneado) en la tarea Trabajo en Clase del aula virtual, antes de nalizar la sesión. 

# 5. Ejercicio Práctico de Laboratorio 

## 5.1. Planteamiento del problema 

Se quiere automatizar el control de temperatura de un ambiente mediante un sensor y un sistema de climatización (aire acondicionado y calefacción). El sistema debe decidir, en cada momento, qué acción tomar según la temperatura medida. 

## 5.2. Diseño del agente (cha PEAS) 

Completar, antes de escribir código, la cha PEAS de este problema: 

Percepción (S) Acciones (A) Entorno (E) Objetivo Medida de desempeño (P) 

## 5.3. De PEAS a reglas de decisión 

Traducir el objetivo anterior en reglas concretas, completando la tabla: 

|Condición|Acción a tomar|
|---|---|
|Si la temperatura está muy por encima de la||
|deseada||
|Si la temperatura está muy por debajo de la||
|deseada||
|Si la temperatura está cerca de la deseada||



## 5.4. Implementación 

Completar el código a partir de sus propias reglas de la tabla anterior (reemplazar cada # COMPLETAR): 

6 

<mark>def agente_termostato(temperatura_actual, temperatura_objetivo=22, margen=1.0): """ Agente reactivo simple (sin memoria, sin modelo del entorno). Completar el docstring con el propio analisis PEAS de la Seccion 5.2. """ diferencia = temperatura_actual - temperatura_objetivo if diferencia > margen: return # COMPLETAR: accion si hace mucho calor elif diferencia < -margen: return # COMPLETAR: accion si hace mucho frio else: return # COMPLETAR: accion si la temperatura esta bien</mark> 

**_⊗_** Atención: Al escribir el código a mano (en vez de copiar y pegar), Python no perdona la sangría: cada línea dentro de def, if, elif o else debe llevar 4 espacios más que la línea anterior que termina en dos puntos (:). Jupyter agrega la sangría automáticamente al presionar Enter después de una línea con :. 

## 5.5. Simulación 

Probar el agente con la siguiente secuencia de percepciones, y agregar dos valores propios, incluyendo al menos un caso límite (una temperatura justo en el borde del margen): 

<mark>percepciones = [18.0, 19.5, 21.8, 24.3, 26.0, 23.0, 20.5]</mark> 

<mark>for t in percepciones: accion = agente_termostato(t) print(f"Percepcion: {t} C -> Accion del agente: {accion}")</mark> 

## 5.6. Reexión 

Responder en una celda markdown o comentario: ¾este agente termostato es racional? ¾Bajo qué condiciones del entorno dejaría de serlo (por ejemplo, si el sensor de temperatura falla o si el margen es demasiado amplio)? 

## 5.7. Entrega mediante GitHub Classroom 

-  Aceptar la asignación del laboratorio ingresando al enlace proporcionado por el docente en GitHub Classroom. Esto genera automáticamente un repositorio individual para el estudiante. 

-  Clonar el repositorio dentro de la terminal: 

<mark>git clone URL_DEL_REPOSITORIO cd nombre_del_repositorio</mark> 

-  Ubicar el notebook o script del ejercicio (Secciones 5.2 a 5.6) dentro del repositorio clonado. 

-  Registrar y subir los cambios: 

<mark>git add . git commit -m "Laboratorio 01: fundamentos de IA y agente reactivo" git push origin main</mark> 

7 

Nota: Si Git no está instalado, descargar el instalador desde https://git-scm.com/downloads y ejecutarlo con las opciones por defecto. 

Si es la primera vez que se emplea Git en el equipo, congurar la identidad con git config --global user.name "Nombre Apellido" y git config --global user.email "correo@ejemplo.com". 

## 5.8. Entregable del Ejercicio de Laboratorio 

-  Repositorio de GitHub Classroom actualizado, con al menos un commit que evidencie el avance del laboratorio. 

-  Notebook (.ipynb) con las celdas de vericación, la prueba funcional y el agente reactivo completado, ejecutadas sin errores. 

-  Ficha PEAS del agente termostato (Sección 5.2) y tabla de reglas (Sección 5.3), completadas antes del código. 

## 5.9. Extensión para la casa 

El agente termostato decide en función de una sola percepción (la temperatura). Esta extensión pide diseñar un agente que decida en función de dos percepciones a la vez, combinándolas. 

Problema: un sistema de riego automático de jardín debe decidir si regar o no, considerando: 

-  humedad_suelo: un número de 0 (seco) a 100 (saturado) 

-  lloverá_hoy: True o False, según el pronóstico 

Parte A: Completar una cha PEAS propia para este problema (Percepción, Acciones, Entorno, Objetivo, Medida de desempeño), siguiendo el mismo formato de la Sección 5.2. 

Parte B: Proponer las reglas de decisión, considerando que ahora deben combinar dos condiciones con and / or. Por ejemplo: si el suelo está seco Y no lloverá hoy, entonces regar. 

Parte C: Escribir la función completa desde cero (sin plantilla esta vez, ya que el proceso se practicó en la Sección 5.4): 

<mark>def agente_riego(humedad_suelo, llovera_hoy): # Escribir aqui la logica completa, basada en las reglas de la Parte B pass</mark> 

Parte D: Probar el agente con al menos 5 combinaciones distintas de humedad_suelo y llovera_hoy, incluyendo un caso donde ambas condiciones compitan entre sí (por ejemplo, suelo muy seco pero con lluvia pronosticada). 

Parte E: Responder: ¾qué tan distinto fue diseñar este agente respecto al termostato? ¾A qué tipo de agente de la Sección 3.3 corresponde? 

Nota: Subir esta extensión como un segundo commit al mismo repositorio de GitHub Classroom, antes de la Semana 2. 

6. Anexo: Solución de Errores Frecuentes 

8 

Error / síntoma Causa Solución 'python' no se reconoce Python no fue Reinstalar Python marcando la como un comando agregado al PATH casilla Add Python to PATH, o durante la ejecutar el instalador nuevamente y instalación elegir Modify ModuleNotFoundError: La biblioteca no se Ejecutar pip install scikit-learn No module named instaló en el entorno dentro del mismo entorno virtual 'sklearn' activo que se está usando 'jupyter' no se Jupyter no se instaló Vericar que el venv esté activado reconoce como un en el entorno activo, (el nombre debe aparecer entre comando o el entorno virtual paréntesis en la terminal) y ejecutar no está activado pip install jupyter nuevamente pip install falla por Intento de Usar un entorno virtual (venv) en permisos instalación global sin lugar de instalar de forma global, o privilegios de agregar --user al comando administrador no se reconoce como Falta la extensión Ejecutar nombre de un cmdlet... .ps1: activate (sin .\venv_ia1\Scripts\Activate.ps1 al activar el venv extensión) es el (con Activate.ps1, no solo script para Bash, no activate) para PowerShell ...no se puede cargar La política de Ejecutar una sola vez porque la ejecución de ejecución de Set-ExecutionPolicy -Scope scripts está PowerShell bloquea CurrentUser -ExecutionPolicy deshabilitada... scripts .ps1 por RemoteSigned y conrmar con S; no (PSSecurityException) defecto requiere permisos de administrador El gráco de Matplotlib Falta plt.show() al Agregar plt.show() después de no aparece nal de la celda construir el gráco fatal: not a git El comando git se Vericar con cd que se está dentro repository ejecutó fuera de la del repositorio antes de usar git carpeta clonada add/commit/push fatal: repository not URL incorrecta o Vericar el enlace y conrmar que found asignación de se aceptó la asignación en GitHub Classroom no Classroom antes de clonar aceptada Please tell me who you Identidad de Git no Ejecutar git config --global are congurada en el user.name y user.email equipo 

9 

