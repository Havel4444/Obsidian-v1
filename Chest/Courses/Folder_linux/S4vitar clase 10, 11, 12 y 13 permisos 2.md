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

















## LINK

```
# Notacion octal
https://blog.alcancelibre.org/staticpages/index.php/permisos-sistema-de-archivos

# Permisos especial: sticky bit
https://keepcoding.io/blog/que-es-el-sticky-bit-y-como-configurarlo/
https://www.fpgenred.es/GNU-Linux/el_bit_sticky.html
```
