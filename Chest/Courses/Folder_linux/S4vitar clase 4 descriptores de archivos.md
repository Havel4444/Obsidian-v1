[[index]]
[[index_linux]]

## REDIRECCION

**SALIDA:**
```
# Enviar la salida stdout a un archivo.
ls 1> datos.txt

# Enviar la salida stderr a un archivo.
ls 2> errores.txt
```

**ENTRADA:**
	Ejecuta el comando _ls_ en modo entra en 'archivo.txt' para visualiar un lista de directorios y archivos en la terminal. Esto solo se aplica si exite vinculacion una vinculacion con el camando y el contenido del archivo.
```
ls < archivo.txt
```




## DESCRIPTOR DE ARCHIVO

**ASIGNACION:**
	Los descriptores son los numero que salen antes de un comando de redireccionamiento, por ejemplo, `1,2,3`.
```
# Descriptor de archivo con lectura(<) y escritura(>).
exec 3<> file
```














### EXAMPLES AND MORE



### CONCLUSION


