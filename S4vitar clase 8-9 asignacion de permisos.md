[[index]]
[[index_linux]]

## PERMISOS Y GRUPOS

**GREAGAR Y QUITAR:**
	Los #permisos pueden ser agregados con el siguiente comando.
```
# agregar permisos en todos los grupos.
chmod u+w,g+w,o-r
```

**AÑADIR GRUPOS:**
	Dentro de lo permitido donde estan los grupos y otros pueden agregarse con el siguiente comando:
```
chgrp havel archivo
``` 



## USUARIO

**Ubicacion:**
	El archivo que contiene a todos los usuarios
```
/etc/passwd
```
&&
	Cada campo esta separado por un ':' y cada uno contiene:
1. Nombre de usuario.
2. Contraseña.
3. ID del usuario.
4. ID del grupo principal.
5. Informacion del usuario.
6. Ubicacion.
7. Shell utilizado.










## LINK

```
# permisos
https://www.hostinger.es/tutoriales/cambiar-permisos-y-propietarios-linux-linea-de-comandos/
https://www.softzone.es/linux/tutoriales/permisos-archivos-directorios-linux/

# propietario y permisos
https://atareao.es/tutorial/terminal/propietarios-y-permisos/

```
