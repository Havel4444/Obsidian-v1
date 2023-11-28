[[index]]
[[index_linux]]


# TERMINAL

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

**COPIAR LO SELECCIONADO:**
	xclip -selection clipboard : copia y guarda en el portapapeles la linea selecionada.
```
less .bash_history | no_dup | fzf | xclip -selection clipboard
```

**ARRIBA Y ABAJO SIN FLECHAS:**
	Usando la combinacion de teclas 'ctrl+p' para arriba y 'ctrl+n' para abajo.

**==XARGS==:**
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



## EDICION, CREACION Y ELIMINACION

**ELIMIAR EL CONTENIDO .TXT:**
	El comando #truncate elimina el contenia texto de un archivo .txt.
```
truncate -s 0 libro.txt
``` 
1. -s: Elijir el tamaño.
2. 0: Tamaño a eliminar.




# DESCOMPRECION

Comandos para instalar y #descomprimir. 
**.deb:**
```
# Instalador
sudo dpkg -i nombre-del-archivo.deb
sudo dpkg -i

# Error por falta de dependencias
sudo apt-get install -f
```

**tar.xz:**
```
tar -xJvf nombre-del-archivo.tar.xz
tar -xJvf 
```

**7z:**
```
# Instalador
sudo apt-get install p7zip-full

# Descompresor
7z x archivo.7z
7z x 
```




## EXAMPLE

**BUSQUEDA CON FIND:**
	El comando `find` se usa principalmente para visualizar/buscar todos los archivos y directorios.
```
find ~/ -name '*kitty*' | fzf 
```
1. find : Muestra los archivos y directorios.
2. ~/ : Ubicacion elegida opcional.
3. -name : Busqueda por nombre.
4. '\*kitty*' : Todo que contenga 'kitty'.
5. | : Separador de comandos.
6. fzf : Interfaz interactiva.