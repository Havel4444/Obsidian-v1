[[index]]
[[index_linux]]

## DEBIAN

**COMANDOS:**
	Descativar la funcion de bloqueo de pantalla para la combinacion de taclas al movimiento en una terminal.
```
gsettings set org.gnome.desktop.screensaver lock-enabled false
```
Si esto no funciona, también puedes intentar desactivar la opción de bloqueo de pantalla a través de la configuración del sistema.
1. Haz clic en el menú de aplicaciones en la esquina superior izquierda de la pantalla.
2. Busca y abre la aplicación “Configuración”.
3. Haz clic en “Privacidad” en la barra lateral izquierda.
4. Desplázate hacia abajo hasta “Bloqueo de pantalla” y haz clic en él.
5. Desactiva la opción “Bloquear” para desactivar la función de bloqueo de pantalla.




## GIT

**COMANDOS:**
Crear un #Repositorio y configurar #Git.
1. git init: Dentro de la carpeta elegida, en el momento se creara una rama fantasma.
2. git commit -m 'f1'.
3. git branch -M main: Elegir como tronco a la rama fantasma. 
4. git remote add origin git\@github.com :Havel4444/asd.git: Vincular github.com con la carpeta local.
5. git push -u origin main: Enviar el contenido de la carpeta local a github.com\/repositorio

6. git branch _Tronco_: En caso de querer crear un tronco principal.
7. git branch -d o -D: Eliminar una rama.
8. git log: Commits.
9. git reset --hard _18df14jl144_: Volver a un commit antiguo borrando los commits creados despues de este mismo.
10. git checkout _rama01_: Cambiar de rama.




# VIM

**VIMRC ROOT:**
	Archivo padre de _.vimrc_, Ubicado en /usr/share/vim/vimrc.
```
syntax on
set tabstop=4
filetype on
set ruler
set list
```




## INSTALL

Programas a #Instalar.

**TRANSLATE**
```
sudo apt install translate-shell -y
```

==**ZOXIDE**==
1. instalar git.
```
sudo apt install curl git
```
2. Descargar la #Zoxide.
```
curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/ajeetdsouza/zoxide/master/install.sh | bash
```
3. Instalar #Fzf y #Z, se configuran automaticamente en .bashrc
```
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```
4. Ejecutar source.
```
source ~/.bashrc
```

**BACKGROUND:**
	El cambio de un #FondoDePantalla en linux tiene que ver principalmente con el gesto de ventas que en el caso de debian es #Mate, asi que `primero se tiene que averiguar este mismo`.

1. Descarga desde web.
```
wget http://urlimagen.png
```
2. Instalar #Gsettings.
```
sudo apt-get install gsettings-desktop-schemas
```
3. Cambiar el fondo.
```
gsettings set org.mate.background picture-filename '/home/havel/Pictures/
```

**TEMA:**
	Los #Temas de en este caso Debian 11 con gestor de ventanas MATE y un GNOME2 puedes ser descargados de la siguiente pagina.
```
https://www.mate-look.org/browse?cat=135&ord=rating
```
**INSTALACION:**
1. Descargar y descomprimir el archivo
2. Copiar y pegar en la siguiente ruta.
```
# Ruta del tema
cd /usr/share/themes/
# Ruta del icono
cd /usr/share/icons/

# Comando para copiar y pegar en la ruta themes
sudo cp -r ~/downloads/tema ./
```

**TEMA INICIO:**
	Configuracion e instalacion de #Grub.
```
# Ubicacion 1
/usr/share/grub/themes
# Ubicacion 2
/boot/grub/themes/

# pagina de instalacion
https://github.com/vinceliuice/grub2-themes

sudo ./uninstall.sh
sudo rm -rf grub2-themes
```

**REDSHIFT:**
```
sudo apt install redshift
```




## THEME

Instalar #OhMyBash y juntarlo con #KyttyTheme mas zoxide principalmente mejora en su totalidad el aspecto y las funciones de `ZOXIDE`.

**KITTY-THEMES:**
	El siguiente link explica como cambiar el especto de la terminal kitty. Theme elejido: Brogrammer. Eliminar el archivo _theme.conf_ para cambiar a otro tema y ejecutar el siguiete comando con el tema elegido.
```
https://github.com/dexpota/kitty-themes

# Comando a ejecutar en la carpeta kitty
ln -s ./kitty-themes/themes/TEMA.conf ~/.config/kitty/theme.conf
```
Tema elegido Earthsong.


**OH MY BASH:**
	En el siguiente video explicara como instalar oh my bash, esto solo cambiara lo relacionado a la `FUENTE`. `GUARDAR LA CONFIGURACION .BASHRC` porque sera borrado luego de instalar esto.
```
https://www.youtube.com/watch?v=qi5Vzw5AU9M&ab_channel=ContandoBits

# Pagina de temas
https://github.com/ohmybash/oh-my-bash/wiki/Themes
```
Tema elegido mairan.




## TECLADO KEYBOARD SHORTCUTS

Configuracion mediante #KeyboardShortcuts.

**VENTANA:**
	Cambio del movimiento de ventana `MOD4+LEFT` y `MOD4+RIGHT`. 
```
# Mover ventana a la izquierda.
Tile window to east(right) side of screen = Mod4+,
# Mover ventana a la derecha.
Tile window to west(left) side of screen = Mod4+.
```


**ESCRITORIO:**
1. Mover las ventanas entre los workspaces 1,2,3 o 4.
```
Move window to workspace 1 = Alt+Mod4+H
Move window to workspace 2 = Alt+Mod4+J
Move window to workspace 3 = Alt+Mod4+K
Move window to workspace 4 = Alt+Mod4+L
```
2. Moverte entre workspaces.
```
Switch to workspace 1 = Shift+Alt+!
Switch to workspace 2 = Shift+Alt+@
Switch to workspace 3 = Shift+Alt+#
Switch to workspace 4 = Shift+Alt+$
```


**SONIDO:**
	Subir,bajar,mutear y pausar.
```
Volume up = Shift+Ctrl+I
Volume down = Shift+Ctrl+U
Volume mute = Shift+Ctrl+O
Volume play = Shift+Ctrl+Y
```




## ETHERNET

**ERROR DE CONEXION**
	La conexion de internet me diante clable al router en parrot trae, en algunos cosos, un error en la configuracion de #ControladoreDeRed, para solucionarlos en `PARROT SECURITY OS` con `DEBIAN 11` estan estos siguientes pasos:
1. Verificar si el controlador esta cargado.
```
# Modo automatico
lsmod | grep r8169
# Modo manual
sudo modprobe r8169
```
2. Revisar la configuracion de red. Confirma que la configuracion de red en el archivo "/etc/network/interfaces" sea correcta para tu tarjeta. Podria verse algo asi:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
3. Guarga los cambios.
```
# Aveces no funciona
sudo /etc/init.d/networking restart
```
4. Reinicia el NetworkManager.
```
sudo systemctl restart NetworkManager
```
5. En caso de seguir el error agregar el modulo 'modprobe r8169' al archivo '/etc/modules' en `MODO ROOT` al final.
```
r816
```
6. Actualizar la configuracion de #Kernel.
```
sudo update-initramfs -u
```




## ALIAS

**BASHRC**
	El #Bashrc es un archivo que no aparece junto a la instalacion de linux, una de sus funciones es `crear alias` y su comando de creacion es el siguiente:
```
touch .bashrc
```

**FUNCION SHELL EN BASHRC:**
	El uso del #AliasConComandos redirigir la salida de error estándar a un archivo, es mejor utilizar una función de shell en lugar de un alias. Puedes agregar la siguiente función a tu archivo .bashrc:
```
# En este ejemplo, reemplaza "comando_a_ejecutar" con el comando real que deseas ejecutar. Luego, cuando ejecutes iner, se ejecutará el comando especificado y cualquier mensaje de error se redirigirá al archivo "error.txt" en el escritorio.
ALIAS() {
    comando_a_ejecutar "$@" 2> /home/havel/Desktop/error.txt
}

# Ejemplo 2
cphi2() {
	grep -v '^#' .bash_history "$@" > ~/.bash_history_filtered | less .bash_history_filtered | fzf --tac | xclip -selection clipboard
}
```




# DESCOMPRECION

Comandos para instalar y #descomprimir. 
**.deb:**
```
# Instalador
sudo dpkg -i nombre-del-archivo.deb
sudo dpkg -i

# Error por falta de dependencias
sudo apt-get install -f
```

**tar.xz:**
```
tar -xJvf nombre-del-archivo.tar.xz
tar -xJvf 
```

**7z:**
```
# Instalador
sudo apt-get install p7zip-full

# Descompresor
7z x archivo.7z
7z x 
```


## YOUTUBE

**SURFINGKEYS:**
```bash
api.unmap('j');
api.unmap('k');
api.unmap('l');
api.unmap('i');
api.unmap('t');
api.unmap('f');
api.unmap('h');
api.unmap('1');
api.unmap('2');
api.unmap('3');
api.unmap('4');
api.unmap('5');
api.unmap('6');
api.unmap('7');
api.unmap('8');
api.unmap('9');
api.unmap('0');
```



## CTRL + J

**DEFINICION:**
	Combinacion de teclas para ejecutar enter, en todo el sistema.

**PASO A PASO:**

1. Puedes usar `xdotool` directamente en lugar de `xbindkeys` para manejar la combinación de teclas "Ctrl + J". Primero, asegurémonos de que `xdotool` esté instalado:
```bash
sudo apt-get install xdotool
```
2. Luego, crea un script Bash, por ejemplo, `simulate_ctrl_j_enter.sh`:
```bash
#!/bin/bash

# Espera un breve momento para liberar las teclas si se presionaron rápidamente
sleep 0.2

# Utiliza xdotool para simular la pulsación de "Enter"
xdotool key Return
```
3. Guarda el script y dale permisos de ejecución:
```bash
chmod +x simulate_ctrl_j_enter.sh
```
4. Ahora, configura tu sistema para que ejecute este script cuando presiones "Ctrl + J". Puedes hacer esto utilizando `xbindkeys`. Crea un archivo de configuración, por ejemplo, `~/.xbindkeysrc`:
```bash
nano ~/.xbindkeysrc
```
5. Agrega la siguiente línea:
```bash
"ruta_completa_del_script/simulate_ctrl_j_enter.sh"
  Control + j
```
6. Reemplaza "ruta_completa_del_script" con la ubicación real del script que acabas de crear. Guarda el archivo y reinicia `xbindkeys`:
```bash
killall xbindkeys
xbindkeys
```
7. Ahora, cuando presiones "Ctrl + J", debería ejecutarse el script y simular la pulsación de "Enter". Asegúrate de que no haya otras configuraciones de teclas conflictivas en tu sistema.





























# LINKS
Comandos basicos de linux:
https://www.fing.edu.uy/inco/cursos/sistoper/recursosLaboratorio/tutorial0.pdf
