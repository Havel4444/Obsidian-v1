[[index]]
[[index_linux]]

## FIND

**BUSQUEDA POR GRUPO:**
	Busca los archivos/directorios que contengan de grupo/usuario al usuario seleccionado y dirige los errores al tacho.
```
find / -group havel type f 2>/dev/null
```




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
```
less .bash_history | no_dup | fzf | xclip -selection clipboard
```

**ARRIBA Y ABAJO SIN FLECHAS:**
	Usando la combinacion de teclas 'ctrl+p' para arriba y 'ctrl+n' para abajo.



## ARCHIVO

**ELIMIAR EL CONTENIDO .TXT:**
	El comando #truncate elimina el contenia texto de un archivo .txt.
```
truncate -s 0 libro.txt
``` 
1. -s: Elijir el tamaño.
2. 0: Tamaño a eliminar.
