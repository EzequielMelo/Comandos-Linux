# Comandos-Linux

Para comenzar montar dentro de virtualbox un nuevo disco duro

1- Empezar como admin: sudo su -
2- Ver info del Kernel y buscar sdb: dmesg | grep sd
3- Listar todos los dispositivos de bloque y sus particiones: fdisk -l o lsblk o mostrar
solo el disco que quieras (fdisk -l /dev/sdb)-> sdb hace referencia a ese disco duro
5- Comienzo: (fdisk /dev/sdb) o (fdisk -l /dev/sdb)
tree
n crear 
d eliminar 
p imprimir  
t cambiar tipo de particion
w guardar y salir

mkfs -tab-tab (doble tab tecla)
6- hacer un formateo: mkfs.ext4 /dev/sdb1 --> (/dev/sdb1)-->nombre del disco duro "sdb1"
7- Montar el disco con: (mount) o con (mount | grep sda) o (mount /dev/sdb1 /mnt)-->Montar nueva particion
8- Montar: mount | grep sdb1
9- Ir al mount: cd /mnt 
10- Fijarse si se monto correctamente: ls -l y despues echo $?
11- Ver info de lo montado: df -h /mnt

(solo se pueden montar primarias y logicas)

crear directorios- mkdir -p nombredirectorio/subdirectorio/subsbudirectorio{1..3} --> ({1..3} crear 3 subsubdirectorio)

mkdir -p 20220928/mama/{amante,hijo}/perro --> crear carpeta perro tanto en amante como en hijo

Borrar: rm -rf 20220928/

mkdir -p Nacion/{prov{1..3}/ciudad,caba}

mkdir -p Nacion1/{prov{1..3}/{ciudad{1..5},municipalidad},caba,ministerios}

Con History poder visualizar codigo otra vez: luego con el numero al costado y "!" volver a crear lo borrado

apt update: actualiza la base de datos de nuestros equipos NO actualiza nuestros sistemas operativos solo la base de datos
apt upgrade: descargar y pregunta si instala (apt upgrade -y)--> no pregunta solo instala
apt update && apt upgrade -y: actualiza la lista de cosas a actualizar e instala directamente
apt dist-upgrade: subir de version 
do-release-upgrade saltar de version a la ultima puede saltar varias

dpkg -l | more: saber paquetes que tengo instalados
dpkg -L net-tools: saber sobre un paquete especifico en este caso net-tools

/////////////////////////////////////////////////////////////////////////////////////////////
apt install kde-plasma-desktop
ese ya no es un gestior de ventanas livianito.. asique si le dieron poca ram a la vm subanle un poco
upszot19:58
apt install gnome-shell
ese es otro
apt install ubuntu-gnome-desktop
despues de todo eso ponen 

sudo dpkg-reconfigure lightdm
y listo tienen 3 gestores de escritorio..
//////////////////////////////////////////////////////////////////////////////////////////////

which ls: trae directorio
echo $PATH: mustra como busca el directorio

whereis ls: mustra en donde se encuentra el directorio y sus deribados 


/etc/passwd		->Informacion del usuario
				*id
				*nombre de usuario
				*gid
				*gecos (descrip.)
				*home (/home/NOM_USUARIO)
				*shell
				*x (correspondia a la password)

/etc/shadow		->password encriptada
				*usuario
				!

/etc/group		->grupos
/etc/gshadow	->contiene contraseña de grupos
/etc/skel 		->contiene los archivos/directorios que se copian cuando se crea un usuario


Generar usuarios:
1- useradd -m -s /bin/bash -c "usuario de prueba" prueba
(/bin/bash)--> donde se va a localizar
(-c "usuario de prueba")--> "descripcion de usuario"
(prueba)--> nombre de usuario

2- passwd prueba
(prueba)--> usuario

3- login prueba ->loggearse
(prueba)--> usuario

4- useradd -m -s /bin/bash -c "Usuario test" -p '$y$j9T$7lOndW2Ol0cjVmgctJnxa0$JV590/qN9krpZBUnahU4SyA8mSJzhgx1sP2sadjWsrC' test
(-p '$y$j9T$7lOndW2Ol0cjVmgctJnxa0$JV590/qN9krpZBUnahU4SyA8mSJzhgx1sP2sadjWsrC') --> copia de la contraseña de "prueba" encriptada

5- usermod -G sudo,cdrom -a test
(-G)--> grupos secundarios

(añadir al grupo sudo)

6- userdel -r prueba
(-r) --> de forma recursiva
(prueba)--> usuario
(borrar usuario)


grep prueba /etc/shadow --> ver informacion sobre el usuario en este caso "prueba"

ctrl-d -> cerrar sesion

cat /etc/shadow --ver mas info de todos los usuarios

Permisos:
r --> 4
w --> 2
x --> 1

chmod 740 "nombreArchivo.txt"

cat /etc/sudoers
vim /etc/sudoers
ll /etc/sudoers
visudo

rpm -aq |grep vim

ver cosas del disco
lsblk
fdisk -l -h

sistema operativo
uname -a
dmesg | more
dmesg | grep sd


crear carpeta archivo texto: (touch opt.txt)-->opt.txt=nombre del archivo
(ls /opt >> ruta del archivo) --> comando para guardar un ls en un archivo

ls /opt >> desarrollo/imagenes/backup/opt.txt

ls -l /opt >> archivo1.txt
o 
ls -l /opt >> desarrollo/imagenes/backup/archivo1.txt

more mi_archivo.txt --> leer archivo de texto
less mi_archivo.txt --> leer archivo de texto

rm -rf rutaDelARchivo -->borrar archivo segun ruta

mkdir -p carpetas/pandemia/{nacional,provincial}/{informes,fotos}/

mkdir -p {desarrollo,testing}/{fuentes,imagenes,final}/backup/ && rm -r desarrollo/final

ver

1. arch - mostrar la arquitectura de la máquina (1).
2. uname -m - mostrar la arquitectura de la máquina (2).
3. uname -r-mostrar la versión del kernel usado.
4. uname -a - mostrar la información completa.
5. lsb_release -a - mostrar la información completa de la distribución.
6. cat /etc/issue - mostrar el nombre de la distribución
7. dmidecode -q - mostrar los componentes (hardware) del sistema.
8. hdparm -i /dev/hda - mostrar las características de un disco duro.
9. hdparm -tT /dev/sda - realizar prueba de lectura en un disco duro.
10.cat /proc/cpuinfo - mostrar información de la CPU.
11.grep -C ^processor /proc/cpuinfo - mostrar número de procesadores.
12.cat /proc/interrupts-mostrar las interrupciones.
13.cat /proc/meminfo -v verificar el uso
