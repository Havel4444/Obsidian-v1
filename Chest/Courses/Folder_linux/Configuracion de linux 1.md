[[index]]
[[index_linux]]

# VIM

**==VIMRC:==**
```
syntax on
set tabstop=4
filetype on
set ruler

command Cp :'<,'>w !xclip -selection clipboard

set list
set nu
set relativenumber

set noruler
set nolist
```
Ruta:
	Ubicado en ~/.vimrc.


**==VIMRC-ROOT:==**
```
syntax on
set tabstop=4
filetype on
set ruler
set list
```
Ruta:
	Ubicacion base del la configuracion de _vimrc_. Eliminar _set nu_ y _set list_. Este archivo solo podra ser modificado en modo ROOT.
	//usr/share/vim/vimrc y //root/.vimrc


**==BASHRC:==**
```
# alias
alias nodu="awk '!x[\$0]++'"
alias es='trans -b :es'
alias en='trans -b :en'
alias open='xdg-open'
alias cphi='less .bash_history | nodu | fzf --tac | xclip -selection clipboard'
alias er='vim ~/error.txt'
alias sa='vim ~/salida.txt'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias ping='ping 8.8.8.8'

# zoxide para arrancar el sistema
#. "$(dirname "$BASH_SOURCE")/init.sh"

# activaion de la funcion zi
. ~/z/z.sh
export PATH=~/z:$PATH

# activacion de la funcion fzf
[ -f ~/.fzf.bash ] && source ~/.fzf.bash
```
Ruta:
	Ubicado en ~/.bashrc.




## INSTALL

**TRANSLATE**
```
sudo apt install translate-shell -y
```


==**ZOXIDE**==
1. instalar git.
```
sudo apt install curl git
```
2. Descargar la #zoxide.
```
curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/ajeetdsouza/zoxide/master/install.sh | bash
```
3. Instalar #fzf y #z, se configuran automaticamente en .bashrc
```
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```
4. Ejecutar source.
```
source ~/.bashrc
```


**BACKGROUND:**
	El cambio de un #fondo-de-pantalla en linux tiene que ver principalmente con el gesto de ventas que en el caso de debian es #MATE, asi que `primero se tiene que averiguar este mismo`.

1. Descarga desde web.
```
wget http://urlimagen.png
```
2. Instalar #gsettings.
```
sudo apt-get install gsettings-desktop-schemas
```
3. Cambiar el fondo.
```
gsettings set org.mate.background picture-filename '/home/havel/Pictures/
```

**TEMA:**
	Los #temas de en este caso Debian 11 con gestor de ventanas MATE y un GNOME2 puedes ser descargados de la siguiente pagina.
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
	Configuracion e instalacion de #grub.
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



## KITTY

**KITTY.CONF HIJO:**
```
# Ruta predeterminada de la configuracion de kitty
include /usr/share/doc/kitty/examples/kitty.conf

# Ruta de themes de kitty
include ./theme.conf

nable_audio_bell no

include color.ini

font_family      HackNerdFont
font_size 13

disable_ligatures never
# url_color #42214b

url_style curly

# WINDOW
map ctrl+w close_window


# Border
active_border_color #086A87
# Distancia del margen
window_margin_width 1.5
# Ancho de bordes
window_border_width 1.2pt




# MOVE AND TAB
#map ctrl+left neighboring_window left
#map ctrl+right neighboring_window right
#map ctrl+down neighboring_window down
#map ctrl+up neighboring_window up

cursor_shape beam
cursor_beam_thickness 1.9

# Crear subventas y ventanas internas
tab_bar_style powerline
map ctrl+shift+alt+enter new_window_with_cwd
map ctrl+shift+alt+t new_tab_with_cwd
# Orrden de las ventanas internas
map ctrl+shift+alt+p next_layout


# opacity
background_opacity 0.67

# MOVE AND TAB
map ctrl+shift+alt+h neighboring_window left
map ctrl+shift+alt+l neighboring_window right
map ctrl+shift+alt+j neighboring_window down
map ctrl+shift+alt+k neighboring_window up

# MOUSE
mouse_hide_wait 3.0
detect_urls yes
repaint_delay 10
input_delay 3
sync_to_monitor yes

# zoom
map ctrl+shift+z toggle_layout stack

# SHORTCUT
alias las_mi "ls -lha"

# Moverme ventanas internas
#map ctrl+shift+h move_window left
#map ctrl+shift+l move_window right
#map ctrl+shift+j move_window down
#map ctrl+shift+k move_window up

# Desctivar ctrl+shift+u signos
map ctrl+shift+u none

# Archivo: kitty.conf
#[keymap]
#ctrl+shift+p set_layout columns
#ctrl+shift+r set_layout rows
#ctrl+shift+g set_layout grid


# shell zsh 

# BEGIN_KITTY_THEME
# Kurayami
include current-theme.conf
# END_KITTY_THEME
```
Ruta:
	~/.config/kitty/kitty.conf

**KITTY.CONF PADRE:**
Ruta:
	/usr/share/doc/kitty/kitty.conf








## THEME

Instalar #ohmybash y juntarlo con #kittytheme mas zoxide principalmente mejora en su totalidad el aspecto y las funciones de `ZOXIDE`.

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

Configuracion mediante #keyboard-shortcuts.

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
	La conexion de internet me diante clable al router en parrot trae, en algunos cosos, un error en la configuracion de #controladores-de-red, para solucionarlos en `PARROT SECURITY OS` con `DEBIAN 11` estan estos siguientes pasos:
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
**ALIAS**
	Un #alias es una cadena de caracteres que se define y que se utiliza para ejecutar un comando determinado.	
```
# no duplicar
alias no_dup="awk '!x[\$0]++'"

# traductor
alias es='trans -b :es'
alias en='trans -b :en'

# abrir programas y carpetas
alias open='xdg-open'

# copiar el historias
alias cphi='less .bash_history | nodu | fzf --tac | xclip -selection clipboard'
```




## END

**FUNCION SHELL EN BASHRC:**
	El uso del #alias-con-comando redirigir la salida de error estándar a un archivo, es mejor utilizar una función de shell en lugar de un alias. Puedes agregar la siguiente función a tu archivo .bashrc:
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




# LINKS
Comandos basicos de linux:
https://www.fing.edu.uy/inco/cursos/sistoper/recursosLaboratorio/tutorial0.pdf





