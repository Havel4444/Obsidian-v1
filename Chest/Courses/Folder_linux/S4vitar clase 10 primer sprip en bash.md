[[index]]
[[index_linux]]

## SCRIP
#Scrip

#### **VARIABLE**
- Una #Variable es un valor que puede ser asignado por _export_, que en su mayoria son directorios/archivos y cadenas de texto.
- Este mismo desapare en una nueva terminal y para su permanencia debe ser colocado en _.bashrc_.

EJEMPLO:
```
export RUTA=~/Desktop
``` 


#### **IF, ELIF, ELSE Y FI**
- Los equivalentes a los comando python.

TRUE OR FALSE:
- El comando _-n_ dentro de las llaves _if_ es un equivalente a verdadero o falto.
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

VARIABLES ESPECIALES:
- Las variables especiales "$0", "$1", "$2" y etc son los argumentos pasado al script.
- Cuando ejecutas un script de Bash y proporcionas argumentos en la línea de comandos, estos argumentos se numeran desde 1. Por ejemplo, si ejecutas ``./script.sh argumento1 argumento2``, entonces "$1" será igual a "argumento1" y "$2" será igual a "argumento2".
- Mientras que la variable especial "$0" representa el nombre del archivo en ejecucion y su ruta padre(ruta completa).

IMPUT:
- La funcion _read -p 'texto' variable(imput)_ al igual que en python es el imput.
```bash
if [ "$variable" == "variable" ]; then
	read -p 'ingrese su edad: ' edad
		if [ "$edad" -gt  ] 
	 
```

CARACTERES EN LETRAS:
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


CARACTERES EN NUMERO:
- Sí, en el contexto de la condición `[ $numero -gt 10 ]` en un script bash, la opción `-gt` se utiliza para comparar si la variable `$numero` es mayor que 10. Aquí hay algunos operadores de comparación comunes en bash:
1. `-eq`: Igual a (equal)
2. `-ne`: No igual a (not equal)
3. `-lt`: Menor que (less than)
4. `-le`: Menor o igual a (less than or equal to)
5. `-gt`: Mayor que (greater than)
6. `-ge`: Mayor o igual a (greater than or equal to)


STRING:
- El comando `if` puede ser usado con asteriscos para buscar catacteres pero solo cuando este acompañado de doble corchete. 
```bash
	if [[ "$valor" == *palabra* ]]; then
```


#### **SALTO DE LINEA**
- El #SaltoDeLinea es un comando a compañado de un _-e_ para acomodar un espacio arriba y bajo del comando.

EJEMPLO:
```bash
echo -e "\n(COMANDO)\n"
```


#### **DESCOMPRESOR**

ARCHIVO:
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
- Cuando se utiliza el comando #Diff en variables estos mismos tiene que estar acompañados de `<()`.
```bash
proceso_viejo="$(ps -eo command)"

while true; do
    proceso_nuevo="$(ps -eo command)"
    diff <(echo "$proceso_viejo") <(echo "$proceso_nuevo")
    proceso_viejo="$proceso_nuevo"
done
```









