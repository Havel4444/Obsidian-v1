[[index]]
[[index_linux]]

# SCRIPT

#### **VARIABLE**
- La #Variable es un valor que puede ser asignado por _export_, que en su mayoria son directorios/archivos y cadenas de texto.
- Este mismo desapare en una nueva terminal y para su permanencia debe ser colocado en _.bashrc_.

Ejemplo:
```
export RUTA=~/Desktop
``` 


#### ACELERACION
- Comandos `&` y `wait` para una aceleracion mediante hilos.

Ejemplo: 
```sh
# Colocacion de "&" al final del comando y "wait" al final de una secuencia despues de ";"
for port in $(seq 31000 32000); do
        (echo '' > /dev/tcp/127.0.0.1/$port) 2>/dev/null && echo "[+] Puerto $port abierto" &
done; wait
```


#### **IF, ELIF, ELSE Y FI**
- El #IfElifElseFi de bash es el equivalente a los comando python.

True or false:
- El comando `-n` dentro de las llaves `if` es un equivalente a verdadero o falto.
```bash
if [ -n "$1"]; then
	valor="$1"
else
	valor="$( shuf -i 1-100 -n 1)"
fi 

echo "$valor"
```
1. shuf: Generador de permutaciones aleatorias.
2. -i: Rango de entrada.
3. -n: Especifica el numero de entrada(digito) de _shuf_.

Variables especiales:
- Las variables especiales "$0", "$1", "$2" y etc son los argumentos pasado al script.
- Cuando ejecutas un script de Bash y proporcionas argumentos en la línea de comandos, estos argumentos se numeran desde 1. Por ejemplo, si ejecutas ``./script.sh argumento1 argumento2``, entonces "$1" será igual a "argumento1" y "$2" será igual a "argumento2".
- Mientras que la variable especial "$0" representa el nombre del archivo en ejecucion y su ruta padre(ruta completa).

Input:
- La funcion _read -p 'texto' variable(imput)_ al igual que en python es el imput.
```bash
if [ "$variable" == "variable" ]; then
	read -p 'ingrese su edad: ' edad
		if [ "$edad" -gt  ] 
	 
```

Caracteres en letras:
- En bash, para comparar cadenas, puedes utilizar varios operadores de comparación.
- Recuerda utilizar comillas dobles alrededor de las variables para manejar adecuadamente casos en los que las cadenas puedan contener espacios u otros caracteres especiales. Además, ten en cuenta que las dobles corchetes (`[[ ]]`) proporcionan funcionalidades adicionales y, en general, son preferibles para las expresiones condicionales más complejas.
1. Igualdad (`==`):
   ```bash
   if [ "$cadena1" == "$cadena2" ]; then
       # código si las cadenas son iguales
   fi
   ```
2. No igualdad (`!=`):
   ```bash
   if [ "$cadena1" != "$cadena2" ]; then
       # código si las cadenas no son iguales
   fi
   ```
3. Cadena vacía:
   ```bash
   if [ -z "$cadena" ]; then
       # código si la cadena es vacía
   fi
   ```
4. Cadena no vacía:
   ```bash
   if [ -n "$cadena" ]; then
       # código si la cadena no es vacía
   fi
   ```
5. Comparación lexicográfica:
   ```bash
   if [[ "$cadena1" < "$cadena2" ]]; then
       # código si cadena1 es lexicográficamente menor que cadena2
   fi
   ```
6. Comparación lexicográfica (mayor o igual):
   ```bash
   if [[ "$cadena1" >= "$cadena2" ]]; then
       # código si cadena1 es lexicográficamente mayor o igual que cadena2
   fi
   ```


Caracteres en numeros:
- Sí, en el contexto de la condición `[ $numero -gt 10 ]` en un script bash, la opción `-gt` se utiliza para comparar si la variable `$numero` es mayor que 10. Aquí hay algunos operadores de comparación comunes en bash:
1. `-eq`: Igual a (equal)
2. `-ne`: No igual a (not equal)
3. `-lt`: Menor que (less than)
4. `-le`: Menor o igual a (less than or equal to)
5. `-gt`: Mayor que (greater than)
6. `-ge`: Mayor o igual a (greater than or equal to)


String:
- El comando `if` puede ser usado con asteriscos para buscar catacteres pero solo cuando este acompañado de doble corchete. 
```bash
	if [[ "$valor" == *palabra* ]]; then
```


#### **SALTO DE LINEA**
- El #SaltoDeLinea es un comando a compañado de un _-e_ para acomodar un espacio arriba y bajo del comando.

Ejemplo:
```bash
echo -e "\n(COMANDO)\n"
```


#### **DESCOMPRESOR**
- El #Descompresor es un codigo que descomprime reiteradamente un archivo muy comprimido.

Archivo:
- El contenido que debe de contener lo siguiente `xxd -r archivo`:
```bash
�hUedata2.bin =��BZh91AY&SYH2  ������������������9���1����������;,� 
� hh
  i�
@h �
�� �� F�d424a4
��Q�P ��   ���hhh
```

- El contenido no debe de contener lo siguiente `xxd archivo`:
```bash
00000210: 4d87 30ce b8a3 946e 72c1 a643 1db7 a060  M.0....nr..C...`
00000220: 6524 629c 0c7e 8e7b e0f8 820c d5cb 60a0  e$b..~.{......`.
00000230: 003c a584 d4c1 61ef eb02 3f65 3a54 a3a2  .<....a...?e:T..
00000240: a565 c154 34c2 b162 d206 1ff8 bb92 29c2  .e.T4..b......).
00000250: 8482 40d9 9010 b3a9 e478 3d02 0000       ..@......x=...
```

- Codigo pra descomprimir un archivo repetidamente comprimido.
```bash
#!/bin/bash
# Archivo a descomprimir.
file_A="$1"

# Bucle descompresor.
while [ -e "$file_A" ] 
do
	
	# Codigo descompresor
	file_B="$(7z l "$file_A" | grep -wi 'name' -A 2 | tail -n 1 | awk '{print $NF}')"
	7z x "$file_A" &>/dev/null
	echo "Archivo descomprimido: $file_B"

	# Comando if para salir del bucle.
	category="$(file "$file_B")"
	if [[ "$category" == *ASCII* ]]; then 
		echo -e "\nArchivo ASCII: $file_B\n"
		cat "$file_B"
		exit
	fi
	
	# Valor principal de bucle.
	file_A="$file_B" 

done
```


#### **DIFF**
- El #Diff en una variables es la diferencia entre estos mismos.
```bash
proceso_viejo="$(ps -eo command)"

while true; do
    proceso_nuevo="$(ps -eo command)"
    diff <(echo "$proceso_viejo") <(echo "$proceso_nuevo")
    proceso_viejo="$proceso_nuevo"
done
```


# CRON

#### DEFINICION
- El #Cron es un sistema de programación de tareas en sistemas operativos tipo Unix. Permite programar comandos o scripts para ejecutarse automáticamente en momentos específicos y de manera recurrente. Aquí tienes algunos ejemplos de tareas que puedes programar con cron:
- El formato de configuración de cron es el siguiente: **Minuto Hora Dia-del-Mes Mes Dia-de-la-Semana Comando-a-Ejecutar**

- El intervalo de tiempo se especifica mediante 5 campos que representan, de izquierda a derecha:
- **Minutos**: de 0 a 59.
- **Horas**: de 0 a 23.
- **Día del mes**: de 1 a 31.
- **Mes**: de 1 a 12.
- **Día de la semana**: de 1 a 6 lunes a sábado (1=lunes, 2=martes, etc.) y 0 o 7 el domingo.

Resumen n1:
- Si quisiéramos especificar todos los valores posibles de un parámetro (minutos, horas, etc.) podemos hacer uso del asterisco (*****). Esto implica que si en lugar de un número utilizamos un asterisco, el comando indicado se ejecutará cada minuto, hora, día de mes, mes o día de la semana, como en el siguiente ejemplo: `* * * * * /home/user/script.sh`.


Ejemplos:
0. Ejecutar un comando 1 ves cada minuto:
```sh
* * * * * /ruta/al/script.sh
```
1. Ejecutar un script todos los días a medianoche:
```bash
0 0 * * * /ruta/al/script.sh
```
Este cronjob ejecutará el script.sh todos los días a la medianoche.
2. Hacer una copia de seguridad diaria a las 3 AM:
```bash
0 3 * * * /ruta/al/script_de_copia_de_seguridad.sh
```
Este cronjob ejecutará el script_de_copia_de_seguridad.sh a las 3 AM todos los días.
3. Actualizar la base de datos cada hora:
```bash
0 * * * * /ruta/al/script_de_actualizacion_de_base_de_datos.sh
```
Este cronjob ejecutará el script_de_actualizacion_de_base_de_datos.sh cada hora en punto.
4. Ejecutar un comando cada lunes a las 8 AM:
```bash
0 8 * * 1 /ruta/al/comando.sh
```
Este cronjob ejecutará el comando.sh todos los lunes a las 8 AM.
5. Enviar un recordatorio cada día laborable a las 9 AM:
```bash
0 9 * * 1-5 /ruta/al/script_de_recordatorio.sh
```
Este cronjob ejecutará el script_de_recordatorio.sh a las 9 AM de lunes a viernes.
6. Limpiar archivos temporales cada fin de semana:
```bash
0 0 * * 6 /ruta/al/script_de_limpieza.sh
```
   Este cronjob ejecutará el script_de_limpieza.sh cada sábado a la medianoche.

Resumen n2:
- Estos son solo ejemplos y puedes ajustar la programación según tus necesidades específicas. La estructura del formato de tiempo en un cronjob es: minuto hora díaDelMes mes díaDeLaSemana comando. Puedes utilizar asteriscos (`*`) para indicar "cualquier" valor en un campo.


# LINK

```sh
Cron=
https://blog.desdelinux.net/cron-crontab-explicados/
https://www.site24x7.com/es/tools/crontab/cron-generator.html


```