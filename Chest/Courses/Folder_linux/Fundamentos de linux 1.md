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




## EDICION, CREACION Y ELIMINACION

**ELIMIAR EL CONTENIDO .TXT:**
	El comando #truncate elimina el contenia texto de un archivo .txt.
```
truncate -s 0 libro.txt
``` 
1. -s: Elijir el tamaño.
2. 0: Tamaño a eliminar.


## INSTALACION y DESCOMPRECION

**.deb:**
	Instalar un archivo #deb desde la terminal.
```
# Instalador
sudo dpkg -i nombre-del-archivo.deb

# Error por falta de dependencias
sudo apt-get install -f
```

**tar.xz:**
	Descomprimir un archivo #tar desde la terminal.
```
tar -xJvf nombre-del-archivo.tar.xz
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