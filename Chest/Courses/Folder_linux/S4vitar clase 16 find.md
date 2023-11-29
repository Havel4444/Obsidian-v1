[[index]]
[[index_linux]]

## GROUP Y USER

#find 

**GRUPO/USUARIO:**
	Busca los archivos/directorios que contengan de grupo/usuario al usuario seleccionado y dirige los errores al tacho.
```
# Grupo
find / -group havel type f 

# Usuario
find / -user havel type d 

---------------------------------------------------------------------------------
# Practica1: Archivos root que empiecen con 'python3.9' mas sus permisos.
find / -group root -type f -name python3.9* -ls 2>/dev/null | awk '{$1=$1}1'
```

**GRUPO/USUARIO CON PERMISOS:**
	Busca los archivos/directorios que contengan de grupo/usuario al grupo/usuario seleccionad `PERO` que tenga el permiso de lectura , escritura o ejecucion.
```
# Lectura
find / -user havel -readable -type f 2>/dev/null

# Escritura
find / -user havel -writable -type d 2>/dev/null 

# Ejecucion
find / -user havel -executable -type f 2>/dev/null

---------------------------------------------------------------------------------
# Practica: Busqueda por usuario/g, tipo y visualizarlo con permisos
find / -user havel -writable -type f 2>/dev/null | xargs ls -l
# Practica2: agregando fzf
find / -user havel -writable -type f 2>/dev/null | xargs ls -l | fzf
```

## PERMISO

**STICKY BIT:**
```
find / -perm -1000

---------------------------------------------------------------------------------
# Practica1: A/D con permisos +t 
find / -perm -1000 -ls 2>/dev/null | awk '{$1=$1}1'
```

**SUID Y SGID:**
```
find / -perm -4000

---------------------------------------------------------------------------------
Practica1:
find / -user havel -perm -4000 2>/dev/null | xargs ls -l
```

## ASTERISCO

**CONTENCION:**
	Busqueda por el nombre incompleto.
```
find / -name *kitt* -type d

---------------------------------------------------------------------------------
# Practica: Nombre de algo mas fzf
find / -name *kitt* 2>/dev/null | fzf
```

## SIGNO DE PREGUNTA

**VERSION:**
```
find / -name python??? -type f 
---------------------------------------------------------------------------------
find / -group root -type f -name python??? -ls 2>/dev/null | awk '{$1=$1}1'
```

## EXEC




________________________________________________________________________


## XARGS

**DEFINICION:**
	El comando xargs se utiliza para construir y ejecutar comandos a partir de la entrada estándar. A menudo se usa para tomar la salida de otro comando y pasarla como argumentos a otro comando.

**BUSQUEDA CON PERMISOS:**
```
find / -name *asd* -type f | xargs ls -l
---------------------------------------------------------------------------------
find / -name python* -type f 2>/dev/null | xargs ls -l
Practica2: Elimina todos los archivos que terminen en '.txt'
find / -name *.txt -type d | xargs rm
```


## AWK

**DEFINCION:**
	Es ideal para trabajar con columnas de datos y realizar operaciones en base a patrones o campos específicos en líneas de texto. Puede realizar cálculos, filtrar datos, reorganizar la salida, entre otras tareas.

**ELIMINAR ESPACIOS INECESARIOS:**
```
awk '{$1=$1}1'
awk '{print $2}'
---------------------------------------------------------------------------------
find / -group havel -type f -name *python* -ls 2>/dev/null | awk '{$1=$1}1'
# Practica2: Muestra la segunda columna del archivo de texto
find / -type f -name pato.txt 2>/dev/null | awk '{print $2}'
```
