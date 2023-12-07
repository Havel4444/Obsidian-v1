[[index]]
[[index_linux]]

# XARGS

**VISUALIZAR EL PESO DE LOS ARCHIVOS:**
	1. ls
	2. xargs du -h: Muestra el peso de los archivos.
	3. sort -h: ordena de menor a mayor.
```
ls | xargs du -h | sort -h
```

**FZF PARA VISULIZAR:**
	 En caso de usar 'fzf' usar '--tac' para ordernarlo de menor a mayor.
```
ls | xargs du -h | sort -h |fzf --tac
```

**COMANDOS SIGUIENTE:**
	El comando xargs puede ser agregado como conjugacion de ciertos comandos, por ejemplo:
1. Eliminar archivos filtrados por find:
```
# Este comando eliminará todos los archivos con extensión ".txt" 
# en el directorio actual y sus subdirectorios.
find . -name "*.txt" | xargs rm
```
2. Ejecutar un comando en varios archivos: 
```
# Este comando buscará el patrón en todos los archivos listados por ls.
ls | xargs grep "patrón"
```
3. Listar por permisos 
```
find / -type f | xargs ls -l
```




## XCLIP

**COPIAR LO SELECCIONADO:**
	xclip -selection clipboard : copia y guarda en el portapapeles la linea selecionada.
```bash
less .bash_history | no_dup | fzf | xclip -selection clipboard
```

**ARRIBA Y ABAJO SIN FLECHAS:**
	Usando la combinacion de teclas 'ctrl+p' para arriba y 'ctrl+n' para abajo.




## ARCHIVO

DEFINICION:
- Comandos solo posibles en un #Archivo.


#### **MANIPULACION**

ARCHIVOS OCULTOS:
- El archivo #Hidden es un contenedor de texto que puede ocultar a/d solo de manera visual.
```bash
touch .hidden
```

ELIMIAR EL CONTENIDO .TXT:
- El comando #truncate elimina el contenia texto de un archivo .txt.
```bash
truncate -s 0 libro.txt
``` 
1. -s: Elijir el tamaño.
2. 0: Tamaño a eliminar.

ARCHIVOS CON ESPACIO:
- Para crear un de texto que contenga espacios, puedes utilizar la siguiente sintaxis en la terminal y para acceder:
```bash
touch 'nombre del archivo con espacios'
cat 'nombre del archivo con espacios'
```

ARCHIVOS CON SIGNOS:
- -: Estos archivos pueden ser abiertos como un ejecutable.
```bash
cat ./-
```


#### **GREP + CARACTERES ESPECIALES**

CARACTER -r:
- La opción `-r` en `grep` se utiliza para realizar búsquedas de manera recursiva en directorios y subdirectorios.
- Si deseas buscar todas las líneas que contienen la palabra "ejemplo" en todos los archivos bajo el directorio `directorio`, puedes usar `-r`:
```bash
grep -r "ejemplo" directorio/
```

CARACTER -v:
- La opción `-v` en `grep` se utiliza para invertir la búsqueda y mostrar solo las líneas que no coinciden con el patrón especificado.
- Supongamos que tienes un archivo llamado `datos.txt` con el siguiente contenido.
```plaintext
Juan
María
Pedro
Carlos
```
- Si deseas mostrar solo las líneas que no contienen la palabra "María", puedes usar `-v`:
```bash
grep -v "María" datos.txt
```
- La salida mostrará las líneas que no contienen la palabra "María".
```plaintext
Juan
Pedro
Carlos
```

CARACTER -i:
- La opción `-i` en `grep` se utiliza para realizar búsquedas de manera insensible a mayúsculas y minúsculas.
- Por ejemplo, si deseas buscar la palabra "mundo" de manera insensible a mayúsculas y minúsculas, puedes usar `-i`:
```bash
grep -i "mundo" *.txt
```
- Resultado.
```plaintext
Hola Mundo
HOLA MUNDO
```

CARACTER -l:
- La opción `-l` en `grep` se utiliza para mostrar solo los nombres de los archivos que contienen al menos una línea que coincide con el patrón de búsqueda.
- Por ejemplo, supongamos que tienes dos archivos, `archivo1.txt` y `archivo2.txt`, ambos con contenido similar:
```plaintext
archivo1.txt:
Hola, esto es un ejemplo.

archivo2.txt:
Este es otro ejemplo.
```
- Si deseas buscar la palabra "ejemplo" en ambos archivos y solo obtener los nombres de los archivos que contienen la palabra, puedes usar `-l`:
```bash
grep -l "ejemplo" *.txt
```
- La salida mostrará los nombres de los archivos que contienen la palabra "ejemplo".
```plaintext
archivo1.txt
archivo2.txt
```

CARACTER -e:
- La opción `-e` en `grep` permite especificar múltiples patrones de búsqueda en una sola invocación de `grep`.
- Por ejemplo, Supongamos que tienes un archivo llamado `datos.txt` con el siguiente contenido:
```plaintext
Nombre: Juan
Apellido: Pérez
Edad: 25

Nombre: María
Apellido: Gómez
Edad: 30
```
- Si deseas buscar líneas que contienen "Nombre" o "Apellido", puedes usar `-e`:
```bash
grep -e "Nombre" -e "Apellido" datos.txt
```
- La salida mostrará las líneas que contienen "Nombre" o "Apellido".
```plaintext
Nombre: Juan
Apellido: Pérez

Nombre: María
Apellido: Gómez
```


#### **UNIQ**
- Uniq es un comando que se utiliza para eliminar líneas adyacentes duplicadas en un archivo o datos provenientes de la entrada estándar.













#### **SORT**
- Sort es un comando en sistemas Unix y Linux que se utiliza para ordenar líneas de texto en un archivo o datos provenientes de la entrada estándar. 






## DIRECTORIO

DEFINICION:
	Comandos solo posibles en un #Directorio.
