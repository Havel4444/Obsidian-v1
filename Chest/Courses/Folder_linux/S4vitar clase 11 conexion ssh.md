[[index]]
[[index_linux]]

## SSH
- SSH, que significa "Secure Shell" (Shell Seguro), es un protocolo de red que permite a los usuarios acceder y gestionar de forma segura los sistemas remotos a través de una conexión cifrada. Es ampliamente utilizado en entornos de sistemas Unix y Linux para acceder a servidores de forma remota.


#### **PING**
- El comando `ping` se utiliza para enviar paquetes de solicitud de eco a una dirección IP o a un nombre de dominio y recibir respuestas. En el comando que proporcionaste:
```bash
ping -c 1 bandit.labs.overthewire.org
```
1. **`ping`:** Este es el comando en sí mismo, que se utiliza para enviar paquetes de solicitud de eco a una dirección específica y recibir respuestas. Se utiliza comúnmente para verificar la conectividad de red y la disponibilidad de un host.
2. **`-c 1`:** Esto es una opción de línea de comandos que indica el número de paquetes de solicitud de eco que se deben enviar. En este caso, se está enviando un solo paquete (`-c 1`). Esto significa que el comando enviará un solo paquete de solicitud de eco y luego mostrará estadísticas sobre el tiempo de ida y vuelta de ese paquete.
3. **`bandit.labs.overthewire.org`:** Esta es la dirección a la que se está enviando el ping. En este caso, parece ser un nombre de dominio (`bandit.labs.overthewire.org`). El comando `ping` intentará determinar si puede alcanzar este dominio y cuánto tiempo lleva ida y vuelta el paquete.


#### **CONEXION MEDIANTE CODIGO**
- En este metodo la conexion es atraves de una contraseña, usuario, maquina y puerto. 
```bash
sshpass -p 'contraseña' ssh usuario@maquina -p 'puerto'
```


#### **CONEXION MEDIANTE ARCHIVO**

HOST:
1. Archivo de configuracion.
- Activar la opcion `PermitRootLogin yes` para habilitar la conexion.
```bash
	vim /etc/ssh/sshd.config
``` 
2. Comanodos de activacion, estado y reinicio. 
```bash
	service ssd status
	service ssd start
	service ssd restart
``` 
3. Generacion de claves.
```bash
	# Generador de clave privada(id_rsa) y publica(id_rsa.pub).
	ssh-keygen
	# Ubucacion
	/home/usuario/.ssh/
```
4. Archivo de conexion.
```bash
	# Archivo de conexion ubicada en .ssh
	cp id_rsa.pub authorized_keys
```


USUARIO:
- El usuario debera de tener en su carpeta `.ssh` la clave `id_rsa` del host al que quiera conectarse.
- El archivo `id_rsa` debera de contener al usuario en los permisos de grupo para su acceso al host.
- En caso de ser necesario puede agregarse otro puerto, pero si no, el que viene por preterminado es el `22`.
```bash
	# El usuario el 'root' y el nombre del equipo es 'localhost' en este caso.
	# El comando '-i' sirve para seleccionar un archivo/clave.
	ssh -i id_rsa root@localhost -p 22
	# -i: sirve para seleccionar un archivo/clave.
	# root: Usuario al que se quiere acceder.
	# localhost: Maquina al que se quiere acceder, en este caso tiene ese nombre
	# debido a que ya se esta dentro de la misma.
``` 



#### **DIAGNOSTICO**

LSOF:
- Este es el comando principal que significa "List Open Files". Proporciona información detallada sobre los archivos que están abiertos por los procesos en el sistema.
- El comando `lsof -i:22` muestra los procesos que están utilizando o tienen abierta una conexión en el puerto 22. En el contexto de conexiones de red, el puerto 22 generalmente se asocia con el servicio SSH (Secure Shell), que es un protocolo utilizado para acceder de forma segura a sistemas remotos.

TCP:
- La disponibilidad de un puerto puede ser verificado de la siguiente manera.
```bash
	# Comando. 
	echo '' > /dev/tcp/127.0.0.1/22
	# Verificacion, en caso de ser '0' quiere decir que esta habilitado en caso
	# contrario sera un '1'.
	echo $?
```




