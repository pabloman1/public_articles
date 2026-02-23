# Entornos virtuales de python

## Introducción

Cuando creas un entorno virtual, suceden tres cosas clave:

* Copia de ejecutables: Se crea una carpeta que contiene una copia (o un enlace simbólico) del ejecutable de Python.
* Aislamiento de librerías: Se crea una carpeta site-packages vacía dentro del entorno. Todo lo que instales con pip se guardará ahí, no en la carpeta raíz del sistema.
* Redirección de rutas (PATH): Al "activar" el entorno, se modifica temporalmente la variable de entorno PATH de tu terminal. Esto le dice a tu computadora: "Oye, cuando escribas 'python', usa el que está en esta carpeta específica, no el general".

Paso,Comando (Windows),Comando (Mac/Linux)

1. Crear,python -m venv venv,python3 -m venv venv
2. Activar,.\venv\Scripts\activate,source venv/bin/activate
3. Instalar,pip install requests,pip install requests
4. Desactivar,deactivate,deactivate

Conviene generar un archivo **requirements.txt** que enumera exactamente lo que tu proyecto necesita para que otra persona lo replique fácilmente.
Cuando se hace backup del proyecto, no se incluye el conjunto de ejecutables y librerías, por eso es necesario este fichero de requerimientos.

```graph
mi_proyecto_datos/          <-- Carpeta raíz (el nombre de tu proyecto)
├── venv/                   <-- Entorno Virtual (HERRAMIENTAS)
│   ├── Lib/                <-- Aquí viven pandas, numpy, etc.
│   └── Scripts/            <-- Aquí vive el ejecutable python.exe
├── src/                    <-- Tus FUENTES (Tu código)
│   ├── __init__.py         <-- Indica que es un paquete
│   ├── procesador.py       <-- Tu lógica de datos
│   └── visualizador.py     <-- Tu lógica de gráficos
├── main.py                 <-- Punto de entrada de tu programa
├── .gitignore              <-- Aquí escribes "venv/" para no subirlo
└── requirements.txt        <-- La lista de lo que hay en venv/
```

El archivo .gitignore es un simple archivo de texto plano que le dice a Git: "Por favor, ignora estas carpetas y archivos; no los subas al repositorio".

Es fundamental en Python porque, como vimos, la carpeta del entorno virtual (venv/) puede contener miles de archivos que no son código tuyo, sino librerías de terceros que cualquiera puede reinstalar.

Ejemplo de fichero gitignore

```text
# Entornos virtuales (el más importante)
venv/
.venv/
env/
ENV/

# Archivos de caché de Python (se generan al ejecutar código)
__pycache__/
*.py[cod]
*$py.class

# Distribución / Empaquetado
bin/
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/

# Variables de entorno (¡Seguridad! No subir contraseñas)
.env
.venv
```

## Creación del entorno

Se debe crear el entorno siempre desde la raíz de la carpeta de tu proyecto.
El escenario ideal paso a paso

Imagina que quieres crear un proyecto llamado mi_proyecto. Este sería el orden lógico en tu terminal:

1. Creas la carpeta del proyecto: mkdir mi_proyecto
2. Entras en ella (esto es clave): cd mi_proyecto
3. Creas el entorno virtual estando ahí dentro: ```python -m venv venv```

Resultado: La carpeta venv/ aparecerá justo dentro de mi_web, al mismo nivel donde luego crearás tu main.py y tu carpeta de fuentes src/.

## Activación del entorno

En Windows (PowerShell o CMD)
PowerShell: .\venv\Scripts\activate

En Mac o Linux (Terminal)
Bash: source venv/bin/activate

## Configuración de VS Code

1. Seleccionar el Intérprete

a. Abrir carpeta de proyecto en VS Code.
b. Presiona **Ctrl + Shift + P (Windows/Linux) o Cmd + Shift + P (Mac) para abrir la Paleta de Comandos.**
c. Escribe "Python: Select Interpreter" y selecciónalo.

d. Sale una lista. Busca la opción que diga algo como:

* Python 3.x.x ('venv': venv)
* O que muestre la ruta: ```./venv/Scripts/python.exe (Windows) o ./venv/bin/python (Mac/Linux).```

Si no aparece en la lista, dale a "Enter interpreter path..." y busca manualmente el archivo python.exe (en Scripts) o python (en bin).
