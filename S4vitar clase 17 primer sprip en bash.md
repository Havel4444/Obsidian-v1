[[index]]
[[index_linux]]

## SALTO DE LINEA

**DEFINCION:**
	El #SaltoDeLinea es un comando a compañado de un _-e_ para acomodar un espacio arriba y bajo del comando.
```bash
echo -e "\n(COMANDO)\n"
```


## IF, ELIF, ELSE Y FI

**DEFINICION:**
	Los equivalentes a los comando python.


**TRUE OR FALSE:**
	El comando _-n_ dentro de las llaves _if_ es un equivalente a verdadero o falto.
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


**VARIABLES ESPECIALES:**
	Las variables especiales "$0", "$1", "$2" y etc son los argumentos pasado al script.
	Cuando ejecutas un script de Bash y proporcionas argumentos en la línea de comandos, estos argumentos se numeran desde 1. Por ejemplo, si ejecutas ``./script.sh argumento1 argumento2``, entonces "$1" será igual a "argumento1" y "$2" será igual a "argumento2".
	Mientras que la variable especial "$0" representa el nombre del archivo en ejecucion y su ruta padre(ruta completa).


**IMPUT:**
	La funcion _read -p 'texto' variable(imput)_ al igual que en python es el imput.
```bash
if [ "$variable" == "variable" ]; then
	read -p 'ingrese su edad: ' edad
		if [ "$edad" -gt  ] 
	 
```


**CARACTERES EN LETRAS:**
	En bash, para comparar cadenas, puedes utilizar varios operadores de comparación.
	Recuerda utilizar comillas dobles alrededor de las variables para manejar adecuadamente casos en los que las cadenas puedan contener espacios u otros caracteres especiales. Además, ten en cuenta que las dobles corchetes (`[[ ]]`) proporcionan funcionalidades adicionales y, en general, son preferibles para las expresiones condicionales más complejas.
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


**==CARACTERES EN NUMERO==:**
	Sí, en el contexto de la condición `[ $numero -gt 10 ]` en un script bash, la opción `-gt` se utiliza para comparar si la variable `$numero` es mayor que 10. Aquí hay algunos operadores de comparación comunes en bash:
1. `-eq`: Igual a (equal)
2. `-ne`: No igual a (not equal)
3. `-lt`: Menor que (less than)
4. `-le`: Menor o igual a (less than or equal to)
5. `-gt`: Mayor que (greater than)
6. `-ge`: Mayor o igual a (greater than or equal to)
&&
	En este caso específico, `-gt` se utiliza para evaluar si el valor de `$numero` es mayor que 10. Si es así, la condición se considera verdadera y se ejecutará el bloque de código dentro del `if`; de lo contrario, se ejecutará el bloque dentro del `else`. Estos operadores son comunes en las expresiones condicionales de scripts bash y otros lenguajes de programación.


## VARIABLE

DEFINICION:
	Una #Variable es un valor que puede ser asignado por _export_, que en su mayoria son directorios/archivos y cadenas de texto.
	Este mismo desapare en una nueva terminal y para su permanencia debe ser colocado en _.bashrc_.
```
export RUTA=~/Desktop
``` 






