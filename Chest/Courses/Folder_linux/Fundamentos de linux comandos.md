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




# ARCHIVO

#### DESCRIPCION
- Los #Archivos tienen diversos comandos aplicados en estos mismos.

Archivos ocultos:
- Un contenedor de texto que puede ocultar a/d solo de manera visual.
```bash
touch .hidden
```

Eliminar el contenido de un texto:
- El comando de eliminacion del contenido de texto de un archivo .txt.
```bash
truncate -s 0 libro.txt
# -s: Selector de lineas a eliminar.
``` 

Archivos con espacios:
- Para crear un de texto que contenga espacios, puedes utilizar la siguiente sintaxis en la terminal y para acceder:
```bash
cat 'nombre del archivo con espacios'
```

Archivos con signos:
- Estos archivos pueden ser abiertos como un ejecutable.
```bash
cat ./-
```

Base64:
- Un archivo `base64` puede ser codificado por este mismo comando y descodificado:
```bash
	cat archivo | base64 -d
```

Diff: 
- Diferencia entre el archivo nuevo y viejo.
```bash
diff new_file old_file
```

Conteo de lineas:
```bash
cat file.txt | wc -l
```

File:
- El comando `file` en sistemas Unix y Linux se utiliza para determinar el tipo de archivo mediante la inspección de su contenido y otros atributos. Proporciona información sobre el formato y la naturaleza del archivo.
```bash
	file archivo.txt
```

Descompresor universal:
- Comando `7z` para descomprimir.
```bash
	# Descomprimir
	7z x archivo_comprimido
	# Visualizar
	7z l archivo_comprimido
```




# TERMINAL
#### DESCRIPCION
- La #terminal tiene comando disponibles 

Forzar:
- Mediante el comando `bash -c` y `()` es posible forzar a realizar un comando.
```bash
# Comando 1
bash -c "comando" "comando utilzado para forzar"

# Comando 2
(find -type f) 2>/dev/null 

# Ejemplo.
bash -c "echo '' > /dev/tcp/127.0.0.1/22" 2>/dev/null
```




# DESCOMPRECION

#### DEFINICION
- El #Descomprimir es posible mediante diferentes metodos.

Descompresor universal:
- Comando `7z` para descomprimir.
```bash
	# Descomprimir
	7z x archivo_comprimido
	# Visualizar
	7z l archivo_comprimido
```

Dpkg:
```
# Instalador
sudo dpkg -i nombre-del-archivo.deb
sudo dpkg -i

# Error por falta de dependencias
sudo apt-get install -f
```

Tar.xz:
```
tar -xJvf nombre-del-archivo.tar.xz
tar -xJvf 
```