[[index]]
[[index_linux]]

## SALTO DE LINEA

**DEFINCION:**
	El #SaltoDeLinea es un comando a compañado de un _-e_ para acomodar un espacio arriba y bajo del comando.
```
echo -e "\n(COMANDO)\n"
```

## IF, ELIF, ELSE Y FI

**DEFINICION:**
	Los equivalentes a los comando python.

**TRUE OR FALSE:**
	El comando _-n_ dentro de las llaves _if_ es un equivalente a verdadero o falto.
```
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
```
if [ "$variable" == "variable" ]; then
	read -p 'ingrese su edad: ' edad
		if [ "$edad" -gt ] 
	 
```










