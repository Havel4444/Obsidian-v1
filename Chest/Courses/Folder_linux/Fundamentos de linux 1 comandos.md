[[index]]
[[index_linux]]

# XARGS

#### **ORDEN**

VISUALIZAR EL PESO DE LOS ARCHIVOS:
```
ls | xargs du -h | sort -h
```

FZF PARA VISULIZAR:
- En caso de usar 'fzf' usar '--tac' para ordernarlo de menor a mayor.
```
ls | xargs du -h | sort -h |fzf --tac
```




## XCLIP

COPIAR LO SELECCIONADO:
- xclip -selection clipboard : copia y guarda en el portapapeles la linea selecionada.
```bash
less .bash_history | no_dup | fzf | xclip -selection clipboard
```

ARRIBA Y ABAJO SIN FLECHAS:
- Usando la combinacion de teclas 'ctrl+p' para arriba y 'ctrl+n' para abajo.




## ARCHIVO
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


#### **FILE**
- **`file`:** El comando `file` en sistemas Unix y Linux se utiliza para determinar el tipo de archivo mediante la inspección de su contenido y otros atributos. Proporciona información sobre el formato y la naturaleza del archivo.




## DIRECTORIO
- Comandos solo posibles en un #Directorio.
