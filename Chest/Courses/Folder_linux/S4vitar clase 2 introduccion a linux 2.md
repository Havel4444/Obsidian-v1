[[index]]
[[index_linux]]


### ANNOTATIONS
##### COMANDOS:

Muestra la ruta ubicada.
```
pwd
```

**Muestra la ubicacion de un archivo ejecutable**.
```
which ls
```
**Muestra la ubicacion del valor actural**
Que es la ruta completa del shell en uso.
```
echo $SHELL
```

**`SHELLS EXISTENTES`**
```
cat /etc/shells
```
**`COMANDO PARA CAMBIAR DE SHELL`**
bash, zsh, pwsh y mas.
```
chsh -s /bin/bash
chsh -s /bin/zsh
chsh -s /bin/pwsh
```










### EXAMPLES AND MORE
##### TAMANO DE ARCHIVOS:

Muetra el tamano de **`TODOS`** los archivos.
```
ls | du -h
```
Muestra el tamano de los archivos.
Esto solo mostrara los archivos **`NO OCULTOS`** y los ordena de menor a mayor.
```
ls | grep -v / | xargs du -h | sort -h
```

ORDEN FZF:
```
fzf --reverse
fzf --tac
```
### CONCLUSION
