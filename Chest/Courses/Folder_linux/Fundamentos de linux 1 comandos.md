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
cat 'nombre del archivo con espacios'
```

ARCHIVOS CON SIGNOS:
- -: Estos archivos pueden ser abiertos como un ejecutable.
```bash
cat ./-
```

BASE64:
- Un archivo `base64` puede ser codificado por este mismo comando y descodificado:
```bash
	cat archivo | base64 -d
```


#### **GREP + CARACTERES ESPECIALES**

1. **`-w`:** Busca solo palabras completas, no subcadenas.
    ```bash
    grep -w "palabra" archivo.txt
    ```
2. **`-i`:** Busca palabras ingnorando mayusculas y minusculas.
    ```bash
    grep -i "palabra" archivo.txt
    ```
3. **`-r`:** Busca en la carpeta y sub-carpetas.
    ```bash
    grep -r "palabra" archivo.txt
    ```
4. **`-l`:** Muestra los archivos que contienen la palabra clave.
    ```bash
    grep -l 'palabra' archivo.txt 
    ```
5. **`-n`:** Muestra el número de línea junto con el resultado de la búsqueda.
    ```bash
    grep -n "patrón" archivo.txt
    ```
6. **`-c`:** Muestra solo el recuento de líneas que coinciden con el patrón.
    ```bash
    grep -c "patrón" archivo.txt
    ```
7. **`-e`:** Permite especificar múltiples patrones de búsqueda.
    ```bash
    grep -e "patrón1" -e "patrón2" archivo.txt
    ```


#### **FILE**
- **`file`:** El comando `file` en sistemas Unix y Linux se utiliza para determinar el tipo de archivo mediante la inspección de su contenido y otros atributos. Proporciona información sobre el formato y la naturaleza del archivo.




## DIRECTORIO

DEFINICION:
	Comandos solo posibles en un #Directorio.
