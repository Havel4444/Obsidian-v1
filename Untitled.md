# Ruta predeterminada de la configuracion de kitty
include /usr/share/doc/kitty/examples/kitty.conf

# kk

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
active_border_color #FE8019
# Distancia del margen
window_margin_width 2.7
# Ancho de bordes
window_border_width 1.8pt
# Margen
window_padding_width 0
single_window_margin_width 0
#window_margin_width 0
#single_window_padding_width 0





# Cambio de fechas en la terminal
# Mover a la izquierda
#map alt+h send_text all \x02
# Mover a la derecha
#map alt+l send_text all \x06
# Mover hacia arriba
#map alt+k send_text all \x10
# Mover hacia abajo
#map alt+j send_text all \x0e
# Mover hacia el final
#map alt+, send_text all \x05
# Mover hacia el principio
#map alt+m send_text all \x01


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
