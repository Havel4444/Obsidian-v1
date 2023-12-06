[[index]]
[[index_linux]]

## SSH

DEFINICION: 
	SSH, que significa "Secure Shell" (Shell Seguro), es un protocolo de red que permite a los usuarios acceder y gestionar de forma segura los sistemas remotos a través de una conexión cifrada. Es ampliamente utilizado en entornos de sistemas Unix y Linux para acceder a servidores de forma remota.

PING:
	El comando `ping` se utiliza para enviar paquetes de solicitud de eco a una dirección IP o a un nombre de dominio y recibir respuestas. En el comando que proporcionaste:
```bash
ping -c 1 bandit.labs.overthewire.org
```
1. **`ping`:** Este es el comando en sí mismo, que se utiliza para enviar paquetes de solicitud de eco a una dirección específica y recibir respuestas. Se utiliza comúnmente para verificar la conectividad de red y la disponibilidad de un host.
2. **`-c 1`:** Esto es una opción de línea de comandos que indica el número de paquetes de solicitud de eco que se deben enviar. En este caso, se está enviando un solo paquete (`-c 1`). Esto significa que el comando enviará un solo paquete de solicitud de eco y luego mostrará estadísticas sobre el tiempo de ida y vuelta de ese paquete.
3. **`bandit.labs.overthewire.org`:** Esta es la dirección a la que se está enviando el ping. En este caso, parece ser un nombre de dominio (`bandit.labs.overthewire.org`). El comando `ping` intentará determinar si puede alcanzar este dominio y cuánto tiempo lleva ida y vuelta el paquete.

**CONEXION:**





 