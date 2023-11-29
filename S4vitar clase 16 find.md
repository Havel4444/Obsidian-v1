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
**ATTR:**
**SUID Y SGID:**

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

## XARGS

**BUSQUEDA CON PERMISOS:**
```
find / -name *asd* -type f | xargs ls -l
---------------------------------------------------------------------------------
find / -name python* -type f 2>/dev/null | xargs ls -l
```


## AWK

**ELIMINAR ESPACIOS INECESARIOS:**
```
awk '{$1=$1}1'
---------------------------------------------------------------------------------
find / -group havel -type f -name *python* -ls 2>/dev/null | awk '{$1=$1}1'
```














