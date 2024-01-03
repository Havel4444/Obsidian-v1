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
ssh -i id_rsa root@localhost -p 22
# -i: sirve para seleccionar un archivo/clave.
# root: Usuario al que se quiere acceder.
# localhost: Maquina al que se quiere acceder, en este caso tiene ese nombre debido a que ya se esta dentro de la misma.
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
# Verificacion, en caso de ser '0' quiere decir que esta habilitado en caso contrario sera un '1'.
echo $?
```


#### **ENVIO DE DATOS**

TELNET:
- El comando `telnet localhost` se utiliza para iniciar una conexión Telnet a la máquina local (localhost) en el puerto predeterminado, que es el puerto 23. Telnet es un protocolo de red que permite la comunicación bidireccional entre dispositivos a través de una conexión de texto simple.
- Cuando ejecutas `telnet localhost`, estás abriendo una sesión Telnet hacia tu propia máquina en la dirección IP de loopback (`127.0.0.1`). Esto puede tener varios propósitos:
1. **Pruebas de Conectividad:** Puedes usar `telnet localhost` para verificar si el servicio Telnet está en ejecución en tu máquina y si puedes establecer una conexión exitosa. Esto puede ser útil para verificar la disponibilidad del servicio o para diagnosticar problemas de red.
```bash 
telnet localhost 30000
# Telnet es un programa que proporciona una interfaz de terminal para conectarse a servidores utilizando el protocolo Telnet. Se utiliza para establecer conexiones con otros sistemas en la red.

# Localhost Es un nombre que se refiere a la dirección IP de loopback, que es `127.0.0.1`. En este contexto, significa que estás intentando conectarte a un servidor que se ejecuta en tu propia máquina.
```

NC:
- Manera alternativa del comando `telnet`.
```bash
echo "Mensaje a enviar" | nc localhost 30000
# Este comando (`nc` o `netcat`) se utiliza para realizar conexiones de red. En este caso, está intentando establecer una conexión TCP con el servidor en el localhost (127.0.0.1) en el puerto 30000.
```

OPERACION CRIPTOCRAFICO CON OPENSSL:
- `OpenSSL` es una herramienta y biblioteca de código abierto que proporciona implementaciones de los protocolos SSL (Secure Sockets Layer) y TLS (Transport Layer Security), así como de criptografía general. Su propósito principal es brindar funciones criptográficas y herramientas relacionadas para garantizar la seguridad de las comunicaciones en red y la protección de datos.
- Algunos de los usos más comunes de `OpenSSL` incluyen:
- **Cifrado y Descifrado SSL/TLS:** OpenSSL es ampliamente utilizado para cifrar y descifrar las comunicaciones a través de SSL/TLS. Puede ser utilizado tanto como cliente como servidor, permitiendo la comunicación segura entre aplicaciones.
- En este caso existen puerto a los que se puede entrar solo de forma cifrada.
```bash
openssl s_client -connect 127.0.0.1:30001
# openssl s_client: Openssl es el comando principal de la herramienta OpenSSL, y `s_client` es una subcomando específica para actuar como un cliente SSL/TLS. Este subcomando permite realizar conexiones SSL/TLS y mostrar información detallada sobre la conexión.
```


#### **NMAP**
- El comando que proporcionaste utiliza Nmap, una herramienta de escaneo de red, para buscar y mostrar los puertos abiertos en un rango específico en una red. Aquí está el desglose del comando:
```bash
nmap --open -T5 -v -n -p31000-32000
# nmap: El comando principal que inicia la herramienta Nmap.
# --open: Esta opción indica a Nmap que solo muestre los puertos que están abiertos. Esto filtra la salida para mostrar solo los puertos que están actualmente accesibles.
# -T5: Especifica el nivel de agresividad del escaneo. En este caso, se establece en 5, que es el nivel más alto (más rápido y más agresivo). Ten en cuenta que configurar un nivel de agresividad muy alto puede afectar la precisión del escaneo y aumentar la probabilidad de ser detectado.
# -v: Habilita el modo detallado o verboso, proporcionando información más detallada sobre el progreso del escaneo.
# -n: Desactiva la resolución de DNS, lo que significa que Nmap no intentará resolver las direcciones IP a nombres de host. Esto puede acelerar el escaneo y reducir la dependencia de la resolución DNS.
# -p3100-32000: Define el rango de puertos que se escanearán. En este caso, se están escaneando los puertos desde el 3100 hasta el 32000.
```


El comando `nc -nlvp` se utiliza para iniciar un servidor de escucha (listener) en un puerto específico utilizando Netcat (`nc`). Aquí está el desglose del comando:
```bash
# El comando `nc -nlvp 5757` se utiliza para iniciar un servidor de escucha (listener) en un puerto específico utilizando Netcat (`nc`). Aquí está el desglose del comando:
nc -nlvp 5757
# nc: Es el comando principal de Netcat, una utilidad de red que permite la lectura y escritura de datos en conexiones de red.
# -n: No realiza la resolución de DNS para mostrar direcciones IP en lugar de nombres de host en las estadísticas.
# -l: Indica que `nc` debe estar en modo de escucha, esperando conexiones entrantes en lugar de intentar conectarse a otro host.
# -v: Modo verbose o detallado, que proporciona información más detallada sobre la actividad.
# -p 5757: Especifica el número de puerto en el que `nc` escuchará las conexiones entrantes. En este caso, está configurado en el puerto 5757.
```


