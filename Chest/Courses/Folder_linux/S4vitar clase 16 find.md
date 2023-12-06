[[index]]
[[index_linux]]

## GROUP Y USER

#find 

**GRUPO/USUARIO:**
	Busca los archivos/directorios que contengan de grupo/usuario al usuario seleccionado y dirige los errores al tacho.
```bash
# Grupo
find / -group havel type f 

# Usuario
find / -user havel type d 

---------------------------------------------------------------------------------
# Practica1: Archivos root que empiecen con 'python3.9' mas sus permisos.
find / -group root -type f -name python3.9* -ls 2>/dev/null | awk '{$1=$1}1'
```

**GRUPO/USUARIO CON PERMISOS:**
	Busca los archivos/directorios que contengan de grupo/usuario al grupo/usuario seleccionad `PERO` que tenga el permiso de lectura , escritura o ejecucion.
```bash
# Lectura
find / -user havel -readable -type f 2>/dev/null

# Escritura
find / -user havel -writable -type d 2>/dev/null 

# Ejecucion
find / -user havel -executable -type f 2>/dev/null

---------------------------------------------------------------------------------
# Practica: Busqueda por usuario/g, tipo y visualizarlo con permisos
find / -user havel -writable -type f 2>/dev/null | xargs ls -l
# Practica2: agregando fzf
find / -user havel -writable -type f 2>/dev/null | xargs ls -l | fzf
```

## PERMISO

**STICKY BIT:**
```bash
find / -perm -1000

---------------------------------------------------------------------------------
# Practica1: A/D con permisos +t 
find / -perm -1000 -ls 2>/dev/null | awk '{$1=$1}1'
```

**SUID Y SGID:**
```bash
find / -perm -4000

---------------------------------------------------------------------------------
Practica1:
find / -user havel -perm -4000 2>/dev/null | xargs ls -l
```
**DOBLE PERMISO:"**
	Los paréntesis se utilizan para agrupar las expresiones -perm -4000 y -perm -2000 y el operador lógico -o indica que se deben buscar archivos que tengan permisos SUID, SGID o 20002.
```bash
find / -type f \( -perm -4000 -o -perm -2000 \) 2>/dev/null | xargs ls -l
```
&&
	El backslash (\) se utiliza para escapar caracteres especiales en Bash. Por ejemplo, si desea buscar archivos que tengan un espacio en el nombre, puede utilizar el backslash para escapar el espacio:
```bash
find / -name "file\ name.txt"
```

## ASTERISCO

**CONTENCION:**
	Busqueda por el nombre incompleto.
```bash
find / -name *kitt* -type d

---------------------------------------------------------------------------------
# Practica: Nombre de algo mas fzf
find / -name *kitt* 2>/dev/null | fzf
```

## SIGNO DE PREGUNTA

**VERSION:**
```bash
find / -name python??? -type f 
---------------------------------------------------------------------------------
find / -group root -type f -name python??? -ls 2>/dev/null | awk '{$1=$1}1'
```

## EXEC




________________________________________________________________________


## XARGS

DEFINICION:
	El comando xargs se utiliza para construir y ejecutar comandos a partir de la entrada estándar. A menudo se usa para tomar la salida de otro comando y pasarla como argumentos a otro comando.

**BUSQUEDA CON PERMISOS:**
```bash
find / -name *asd* -type f | xargs ls -l
---------------------------------------------------------------------------------
find / -name python* -type f 2>/dev/null | xargs ls -l
# Practica2: Elimina todos los archivos que terminen en '.txt'
find / -name *.txt -type d | xargs rm
# Practica3: Permisos
find /
```

ERRORES:
	No puede estar acompañado del comando 'cut'.

## AWK

DEFINCION:
	#Awk es ideal para trabajar con ``COLUMNA`` de datos y realizar operaciones en base a patrones o campos específicos en líneas de texto. Puede realizar cálculos, filtrar datos, reorganizar la salida, entre otras tareas.

**ELIMINAR ESPACIOS INECESARIOS:**
```bash
awk '{$1=$1}1'
awk '{print $2}'
---------------------------------------------------------------------------------
find / -group havel -type f -name *python* -ls 2>/dev/null | awk '{$1=$1}1'
# Practica2: Muestra la segunda columna del archivo de texto
find / -type f -name pato.txt 2>/dev/null | awk '{print $2}'
```


## GREP

DEFINICION:
#Grep es un comando en sistemas Unix y Linux que se utiliza para buscar patrones de texto en archivos o en la salida de otros comandos.

**CARACTERES ESPECIALES:**
0. **`\w`:** Representa cualquier carácter de palabra, incluyendo letras (mayúsculas y minúsculas), números y guiones bajos (`_`). Es equivalente a la clase de caracteres `[a-zA-Z0-9_]`.
    ```bash
    grep -r '\w' archivo.txt
    ```
1. **`\d`:** Representa cualquier dígito (equivalente a `[0-9]`). Este comando buscará líneas que contengan al menos un dígito.
    ```bash
    grep -r '\d' archivo.txt
    ```
2. **`\D`:** Representa cualquier carácter que no sea un dígito (equivalente a `[^0-9]`). Este comando buscará líneas que contengan al menos un carácter que no sea un dígito.
    ```bash
    grep -r '\D' archivo.txt
    ```
3. **`\s`:** Representa cualquier carácter de espacio en blanco (espacios, tabulaciones, saltos de línea). Este comando buscará líneas que contengan al menos un carácter de espacio en blanco.
    ```bash
    grep -r '\s' archivo.txt
    ```
4. **`\S`:** Representa cualquier carácter que no sea un espacio en blanco. Este comando buscará líneas que contengan al menos un carácter que no sea un espacio en blanco.
    ```bash
    grep -r '\S' archivo.txt
    ```


## CUT

DEFINICION:
	#Cut es especialmente útil cuando trabajas con archivos de texto delimitados por columnas, ya que te permite recortar y mostrar solo las partes específicas de cada línea.

**EJEMPLO 1:**
1. Supongamos que tienes un archivo CSV (valores separados por comas) llamado `datos.csv` con el siguiente contenido:
```plaintext
Nombre,Apellido,Edad
Juan,Pérez,25
María,Gómez,30
Carlos,Ruiz,28
```
2. Para extraer solo la columna de "Apellido", puedes usar `cut` de la siguiente manera:
```bash
cut -d',' -f2 datos.csv
```
- `-d','`: Especifica que el delimitador es la coma.
- `-f2`: Indica que quieres extraer el segundo campo.
3. La salida será:
```plaintext
Apellido
Pérez
Gómez
Ruiz
```

**EJEMPLO 2:**
1. Supongamos que tienes un archivo de texto llamado `texto.txt` con el siguiente contenido:
```plaintext
abcdefgh
ijklmnop
qrstuvwx
yz
```
2. Para extraer solo los primeros tres caracteres de cada línea, puedes usar:
```bash
cut -c1-3 texto.txt
```
- `-c1-3`: Indica que quieres extraer los caracteres de la columna 1 a la 3.
3. La salida será:
```plaintext
abc
ijk
qrs
yz
```


## TR