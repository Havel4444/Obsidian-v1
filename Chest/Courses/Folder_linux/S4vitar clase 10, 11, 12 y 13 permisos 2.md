[[index]]
[[index_linux]]

## NOTACION OCATAL

**VALOR:**
	Cada permiso 'r,w,x' tiene un valor numero #Octal.
1. r: 4
2. w: 2
3. x: 1
&&
	La enumeracion octal te permite agregar permisos de manera mas rapida y limpia. Por ejemplo.
```
# Agregar todos los permisos al usuario, permisos de lectura y ejecucion al
# grupo y sin permisos para otro.
chmod 750 archivo
```



## PERMISO ESPECIAL: STICKY BIT

**DEFINICION:**
	El permiso #StickyBit deniega los permisos '777 y 666' a archivo y directorios de cualquier usuario pero `SOLO A GRUPOS Y A OTROS`.
**ASIGNACION:**
	Puede ser asignado con el siguiente comando:
```
# Modo normal
chmod +t archivo/directorio

# Modo octal
chmod 1777 archivo/directorio
```


## CONTROL DE ATRIBUTOS DE FICHERO

**COMANDOS:**
	El #Lsattr visualiza los atributos de fichero.
&&
	El #Chattr hace in-borrable un archivo/directori incluso para el usuario root.
```
# Agregar
chattr +i -V archivo/directorio
# Quitar
chattr -i -V archivo/directorio
```

**PERMISOS:**
	"e": Indica que el atributo "append-only" está activado. Cuando este atributo está establecido en un archivo, solo se le permite agregar datos al final del archivo. No se pueden modificar ni eliminar datos existentes.
	"c" o "C": Indica que el atributo "no-clobber" está activado. Este atributo también controla la capacidad de agregar datos al archivo, pero de manera más restrictiva que el atributo "append-only". Si el atributo "c" está establecido, solo los usuarios con capacidad de escritura en el directorio pueden agregar datos al archivo. Si el atributo "C" está establecido, incluso el propietario del archivo no puede agregar datos.


## PERMISO ESPECIAL: SUID Y SGID

**DEFINICION:**
	Los permisos #SUID y #SGID activan la funcion root de forma pasiva.
**COMANDO:**
```
# Para usuario con y sin numeracion octal
chmod 4755(4000) directorio
chmod 4644(4000) archivo

# Para grupo con y sin numeracion octal
chmod 2755(2000) directorio
chmod 2644(2000) archivo
```

**EJEMPLO DE USO:**
	En el siguiente ejemplo se vera el paso a paso de como acceder al usiario root de otro linux mediante un _suid_/_sgid_.
	Estando en modo no root.
1. Buscar archivos/directorios con estas funciones activadas y luego filtralas con un redireccionamiento.
```
# Usuario
find / -type f -perm -4000 2>/dev/null

# Grupo
```
2. Elegir una de la lista, en caso de no tener se puede agregar esta funcion especial.
```
# Usuario
chmod u+s archivo/directorio

# Grupo
chmod g+s archiv
```



## LINK

```
# Notacion octal
https://blog.alcancelibre.org/staticpages/index.php/permisos-sistema-de-archivos

# Permisos especial: sticky bit
https://keepcoding.io/blog/que-es-el-sticky-bit-y-como-configurarlo/
https://www.fpgenred.es/GNU-Linux/el_bit_sticky.html

# Permisos especiales: chattr
https://rm-rf.es/chattr-y-lsattr-visualizar-y-modificar-atributos-en-sistemas-de-ficheros-linux/#:~:text=El%20primer%20comando%2C%20lsattr%20permite,chmod%2C%20chown%2Csetfacl%E2%80%A6)
https://programmerclick.com/article/5604675172/

# Permisos especiales: SUID Y SGID


```






