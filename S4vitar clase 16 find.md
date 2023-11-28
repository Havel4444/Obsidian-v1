[[index]]
[[index_linux]]

## FIND

#find 

**BUSQUEDA POR GRUPO/USUARIO:**
	Busca los archivos/directorios que contengan de grupo/usuario al usuario seleccionado y dirige los errores al tacho.
```
# Grupo
find / -group havel type f 2>/dev/null

# Usuario
find / -user havel type d 2>/dev/null
```

**BUSQUEDA POR GRUPO/USUARIO CON PERMISOS:**
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

**BUSQUEDA POR SIMILITUD:**
	Busqueda por el nombre incompleto.
```
find / -name kitt\* 2>/dev/null

---------------------------------------------------------------------------------
# Practica: Busqueda por el nombre de algo, mas fzf
find / -name kitt\* 2>/dev/null | fzf
```



## XARGS

**BUSQUEDA CON PERMISOS:**
3. Listar por permisos 
```
find / -type f | xargs ls -l
```
