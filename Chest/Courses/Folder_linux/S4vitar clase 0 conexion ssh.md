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


#### **CONEXION ESTANDAR**
0. ==Localhost==.
1. Archivo de configuracion.
- Una conexion es posible si el host tiene activa la opcion `PermitRootLogin yes/ PubkeyAuthentication yes/ PasswordAuthentication yes`, la que esta dentro de la siguiente carpeta.
```bash
	vim /etc/ssh/sshd.config
``` 
2. Comanodos de activacion/estado/reinicio. 
```bash
	service ssd status
	service ssd start
	service ssd restart
``` 
3. Generacion de claves.
- En la creacion de una clave ssh te da a elegir a cambiar la ubicacion de la misma y agregar una contraseña. 
- Esta misma creara 2 claves, 1 privada otra 1 publica. Estan ubicadas en la carpeta `.ssh` del usuario.
```bash
	# Generador
	ssh-keygen
	# Ubucacion
	/home/usuario/.ssh/claves
```
4. Archivo de autorizacion.
- Luego de generar las claves se tiene que crear el archivo llamado `authorized_keys` que contiene el contenido del archivo `id_rsa.pub`, este mismo tiene que estar en la carpeta `.ssh` junto con las demas claves del usuario host que es el que abre las puertas para ingresar a su localhost.
5. ==Usuario==.
- Todo usuario que quiera entrar en el localhost debera de tener en su carpete `.ssh` la clave privada `id_rsa` del localhost , para luego colocar el siguiente comando de acceso y la contraseña del la clave privada:
```bash
	# El usuario el 'root' y el nombre del equipo es 'localhost' en este caso.
	ssh -i id_rsa root@localhost -p 22
``` 
- En caso de ser necesario 

#### **CONEXION REGULAR**
0. ==Usuario==



#### **DIAGNOSTICO**

LSOF:
- El comando `lsof` en Linux se utiliza para listar información sobre los archivos abiertos por procesos. La opción `-i` se utiliza para mostrar información sobre los archivos relacionados con conexiones de red. En este contexto, `lsof -i:22` se utiliza para mostrar los procesos que están utilizando el puerto 22 en el sistema.
- Entonces, `lsof -i:22` muestra los procesos que están utilizando o tienen abierta una conexión en el puerto 22. En el contexto de conexiones de red, el puerto 22 generalmente se asocia con el servicio SSH (Secure Shell), que es un protocolo utilizado para acceder de forma segura a sistemas remotos.
1. `lsof`: Este es el comando principal que significa "List Open Files". Proporciona información detallada sobre los archivos que están abiertos por los procesos en el sistema.
2. `-i`: Es la opción que especifica que se debe mostrar información relacionada con conexiones de red.
3. `:22`: Especifica el puerto en el que estamos interesados. En este caso, el puerto 22.







