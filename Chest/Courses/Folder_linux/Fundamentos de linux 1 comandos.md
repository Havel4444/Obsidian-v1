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
	Comandos solo posibles en un #Archivo.

ARCHIVOS OCULTOS:
	El archivo #Hidden es un contenedor de texto que puede ocultar a/d solo de manera visual.
```bash
touch .hidden
```

**ELIMIAR EL CONTENIDO .TXT:**
	El comando #truncate elimina el contenia texto de un archivo .txt.
```bash
truncate -s 0 libro.txt
``` 
1. -s: Elijir el tamaño.
2. 0: Tamaño a eliminar.

ARCHIVOS CON ESPACIO:
	Para crear un #de texto que contenga espacios, puedes utilizar la siguiente sintaxis en la terminal y para acceder:
```bash
touch 'nombre del archivo con espacios'
cat 'nombre del archivo con espacios'
```

ARCHIVOS CON SIGNOS:
1. -: Estos archivos pueden ser abiertos como un ejecutable.
```bash
cat ./-
```


**CARACTER ESPECIAL -v:**
**CARACTER ESPECIAL -i:**
**CARACTER ESPECIAL -e:**
**CARACTER ESPECIAL -l:**

1. **`-v`:** Representa cualquier carácter que no sea un espacio en blanco. Este comando buscará líneas que contengan al menos un carácter que no sea un espacio en blanco.
    ```bash
    grep -r '\S' archivo.txt
    ```





## DIRECTORIO

DEFINICION:
	Comandos solo posibles en un #Directorio.














