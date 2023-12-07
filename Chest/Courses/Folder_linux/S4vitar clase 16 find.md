[[index]]
[[index_linux]]


## FIND
- #Find es un comando en sistemas Unix y Linux utilizado para buscar archivos y directorios en un sistema de archivos, según diversos criterios como nombre, tipo, tamaño y otros atributos.


#### **USUARIO Y GRUPO**
- Los #UsuariosYGrupos dentro de `find` pueden ser combinados con los siguientes comandos.

USUARIO Y GRUPO:
- Busca los archivos/directorios que contengan de grupo/usuario al usuario seleccionado y dirige los errores al tacho.
```bash
	# Grupo
	find / -group havel 
	
	# Usuario
	find / -user havel 

---------------------------------------------------------------------------------
	# Practica1: Archivos root que empiecen con 'python3.9' mas sus permisos.
	find / -group root -type f -name python3.9* -ls 2>/dev/null | awk '{$1=$1}1'
```
PERMISOS DE USUARIO Y GRUPO:
- Busca los archivos/directorios que contengan de grupo/usuario al grupo/usuario seleccionad `PERO` que tenga el permiso de lectura , escritura o ejecucion.
```bash
	# Lectura
	find / -user havel -readable
	# Alterno
	find / -user havel -not -readable

	# Escritura
	find / -user havel -writable 
	# Alterno
	find / -user havel -not -writable 
	
	# Ejecucion
	find / -user havel -executable 
	# Alterno
	find / -user havel -not -executable 
	
---------------------------------------------------------------------------------
	# Practica: Busqueda por usuario/g, tipo y visualizarlo con permisos
	find / -user havel -writable -type f 2>/dev/null | xargs ls -l
	# Practica2: agregando fzf
	find / -user havel -writable -type f 2>/dev/null | xargs ls -l | fzf
```


#### **PERMISO**

STICKY BIT:
```bash
	find / -perm -1000
---------------------------------------------------------------------------------
	# Practica1: A/D con permisos +t 
	find / -perm -1000 -ls 2>/dev/null | awk '{$1=$1}1'
```

SUID Y SGID:
```bash
	find / -perm -4000
---------------------------------------------------------------------------------
	# Practica1:
	find / -user havel -perm -4000 2>/dev/null | xargs ls -l
```
- El doble permiso es posible por medio de los paréntesis que se utilizan para agrupar las expresiones -perm -4000 y -perm -2000 y el operador lógico -o indica que se deben buscar archivos que tengan permisos SUID, SGID o 20002.
```bash
	find / -type f \( -perm -4000 -o -perm -2000 \) 2>/dev/null | xargs ls -l
```

FIND + RECURSIVO:
- El comando `/`
```bash
find / -perm /444
```


#### **ASTERISCO**

En el comando `find`, el #Asterisco (`*`) se utiliza como comodín para representar cualquier cantidad y combinación de caracteres en nombres de archivos o directorios durante una búsqueda.

CONTENCION:
- Busqueda por el nombre incompleto.
```bash
	find / -name *kitt* -type d
---------------------------------------------------------------------------------
	# Practica: Nombre de algo mas fzf
	find / -name *kitt* 2>/dev/null | fzf
```

#### **SIGNO DE PREGUNTA**

VERSION:
```bash
	find / -name python??? -type f 
---------------------------------------------------------------------------------
	find / -group root -type f -name python??? -ls 2>/dev/null | awk '{$1=$1}1'
```




#### EXEC




#### **SIZE**
- El comando #Size busca a/d por su peso y otros parametros.
  En el comando `find`, la opción `-size` se utiliza para buscar archivos según su tamaño. Aquí tienes algunos ejemplos simples de cómo usar `-size`:
1. **Buscar archivos más grandes que un tamaño específico:**
   ```bash
   find / -type f -size +1M
   ```
2. **Buscar archivos más pequeños que un tamaño específico:**
   ```bash
   find / -type f -size -100k
   ```
3. **Buscar archivos de un tamaño específico:**
   ```bash
   find / -type f -size 500c
   ```










________________________________________________________________________


## XARGS
- El comando xargs se utiliza para construir y ejecutar comandos a partir de la entrada estándar. A menudo se usa para tomar la salida de otro comando y pasarla como argumentos a otro comando.

BUSQUEDA CON PERMISOS:
```bash
	find / -name *asd* -type f | xargs ls -l
---------------------------------------------------------------------------------
	find / -name python* -type f 2>/dev/null | xargs ls -l
	# Practica2: Elimina todos los archivos que terminen en '.txt'
	find / -name *.txt -type d | xargs rm
	# Practica3: Permisos
	find /
```

CAT:
- Usando el comando `xargs` es posible abrir un archivo de texto pero antes se debe de usar `grep` para nombrarlo.
```bash
find . -type f | grep 'nombre\del\archivo'| xargs cat
```




ERRORES:
- No puede estar acompañado del comando 'cut'.


#### **AWK**
- #Awk es ideal para trabajar con ``COLUMNA`` de datos y realizar operaciones en base a patrones o campos específicos en líneas de texto. Puede realizar cálculos, filtrar datos, reorganizar la salida, entre otras tareas.

ELIMINAR ESPACIOS INECESARIOS:
```bash
	awk '{$1=$1}1'
	awk '{print $2}'
---------------------------------------------------------------------------------
	find / -group havel -type f -name *python* -ls 2>/dev/null | awk '{$1=$1}1'
	# Practica2: Muestra la segunda columna del archivo de texto
	find / -type f -name pato.txt 2>/dev/null | awk '{print $2}'
```


#### **GREP**
Grep es un comando en sistemas Unix y Linux que se utiliza para buscar patrones de texto en archivos o en la salida de otros comandos.

CARACTER ESPECIAL -r:
1. **`\w`:** Representa cualquier carácter de palabra, incluyendo letras (mayúsculas y minúsculas), números y guiones bajos.
    ```bash
    grep -r '\w' archivo.txt
    ```
2. **`\W`:** Representa cualquier carácter de simbolo.
    ```bash
    grep -r '\W' archivo.txt
    ```
3. **`\d`:** Representa cualquier dígito (equivalente a `[0-9]`). Este comando buscará líneas que contengan al menos un dígito.
    ```bash
    grep -r '\d' archivo.txt
    ```
3. **`\D`:** Representa cualquier carácter que no sea un dígito (equivalente a `[^0-9]`). Este comando buscará líneas que contengan al menos un carácter que no sea un dígito.
    ```bash
    grep -r '\D' archivo.txt
    ```
4. **`\s`:** Representa cualquier carácter de espacio en blanco (espacios, tabulaciones, saltos de línea). Este comando buscará líneas que contengan al menos un carácter de espacio en blanco.
    ```bash
    grep -r '\s' archivo.txt
    ```
5. **`\S`:** Representa cualquier carácter que no sea un espacio en blanco. Este comando buscará líneas que contengan al menos un carácter que no sea un espacio en blanco.
    ```bash
    grep -r '\S' archivo.txt
    ```

IGNORAR:
- Con el comando `-v` puedes resaltar o ignorar archivos o directorios y si se requiere hacerlo con mas de 1 unidad es posible con `-E`.
```
find . -type f | grep -vE "archivo|directorio" 
```


#### **CUT**
- #Cut es especialmente útil cuando trabajas con archivos de texto delimitados por columnas, ya que te permite recortar y mostrar solo las partes específicas de cada línea.

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
cut -d ',' -f2 datos.csv
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