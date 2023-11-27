[[index]]
[[index_linux]]

## NOTACION OCATAL

**VALOR:**
	Cada permiso 'r,w,x' tiene un valor numero #octal.
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
&&
	


**PERMISOS:**
	"e": Indica que el atributo "append-only" está activado. Cuando este atributo está establecido en un archivo, solo se le permite agregar datos al final del archivo. No se pueden modificar ni eliminar datos existentes.
	"c" o "C": Indica que el atributo "no-clobber" está activado. Este atributo también controla la capacidad de agregar datos al archivo, pero de manera más restrictiva que el atributo "append-only". Si el atributo "c" está establecido, solo los usuarios con capacidad de escritura en el directorio pueden agregar datos al archivo. Si el atributo "C" está establecido, incluso el propietario del archivo no puede agregar datos.













## LINK

```
# Notacion octal
https://blog.alcancelibre.org/staticpages/index.php/permisos-sistema-de-archivos

# Permisos especial: sticky bit
https://keepcoding.io/blog/que-es-el-sticky-bit-y-como-configurarlo/
https://www.fpgenred.es/GNU-Linux/el_bit_sticky.html
```
