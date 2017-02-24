# Ejercicios-Linux

Ejercicios comandos Linux

Listar todos los archivos del directorio bin.
ls /bin
Listar todos los archivos del directorio tmp.
ls /tmp
Listar todos los archivos del directorio etc que empiecen por t en orden inverso.
ls –r /etc/t*
Listar todos los archivos del directorio dev que empiecen por tty y tengan 5 caracteres.
ls /dev/tty??
Listar todos los archivos del directorio dev que empiecen por tty y acaben en 1,2,3 ó 4.
ls /dev/tty*[1-4]
Listar todos los archivos del directorio dev que empiecen por t y acaben en C1.
ls /dev/t*c1
Listar todos los archivos, incluidos los ocultos, del directorio raíz.
ls –a /
Listar todos los archivos del directorio etc que no empiecen por t.
ls –d /etc/[^t]*
Listar todos los archivos del directorio usr y sus subdirectorios.
ls –R /usr
Cambiarse al directorio tmp, crear directorio PRUEBA.
cd /tmp mkdir PRUEBA
Verificar que el directorio actual ha cambiado.
pwd
Mostrar el día y la hora actual.
date
Con un solo comando posicionarse en el directorio $HOME.
cd /home
Verificar que se está en él.
pwd
Listar todos los ficheros del directorio HOME mostrando su número de inodo.
ls -i
Borrar todos los archivos y directorios visibles de vuestro directorio PRUEBA.
rm -rf PRUEBA/*
Crear los directorios dir1, dir2 y dir3 en el directorio PRUEBA. Dentro de dir1 crear el directorio dir11. Dentro del directorio dir3 crear el directorio dir31. Dentro del directorio dir31, crear los directorios dir311 y dir312.
mkdir PRUEBA/dir1
mkdir PRUEBA/dir1/dir11
mkdir PRUEBA/dir2
mkdir PRUEBA/dir3
mkdir PRUEBA/dir3/dir31
mkdir PRUEBA/dir3/dir31/dir311
mkdir PRUEBA/dir3/dir31/dir312
Copiar el archivo /etc/motd a un archivo llamado mensaje de vuestro directorio PRUEBA.
sudo touch /etc/motd PRUEBA/mensaje
Copiar mensaje en dir1, dir2 y dir3.
cd PRUEBA
cp mensaje dir1/mensaje && cp mensaje dir2/mensaje && cp mensaje dir3/mensaje
Comprobar el ejercicio anterior mediante un solo comando.
ls -R PRUEBA
Copiar los archivos del directorio rc.d que se encuentra en /etc al directorio dir31.
cp -r /etc/rc.d dir31
Copiar en el directorio dir311 los archivos de /bin que tengan una a como segunda letra y su nombre tenga cuatro letras.
cp -r /bin/?a?? PRUEBA/dir3/dir31/dir311
Copiar el directorio de otro usuario y sus subdirectorios debajo de dir11 (incluido el propio directorio).
sudo cp -r ../usuario2 PRUEBA/dir1/dir11
Mover el directorio dir31 y sus subdirectorios debajo de dir2.
mv PRUEBA/dir3/dir31 PRUEBA/dir2
Mostrar por pantalla los archivos ordinarios del directorio HOME y sus subdirectorios.
ls -R $HOME
Ocultar el archivo mensaje del directorio dir3.
mv PRUEBA/dir3/mensaje PRUEBA/dir3/.mensaje
Borrar los archivos y directorios de dir1, incluido el propio directorio.
rm -rf PRUEBA/dir1
Copiar al directorio dir312 los ficheros del directorio /dev que empiecen por t, acaben en una letra que vaya de la a a la b y tengan cinco letras en su nombre.
cp /dev/t???[a*b] /home/ubuntu/PRUEBA/dir3/dir31/dir312
Borrar los archivos de dir312 que no acaben en b y tengan una q como cuarta letra.
rm -r PRUEBA/dir2/dir31/dir312/???q[^b]
Mover el directorio dir312 debajo de dir3.
mv PRUEBA/dir2/dir31/dir312 PRUEBA/dir3
Crear un enlace simbólico al directorio dir1 dentro del directorio dir3 llamado enlacedir1.
ln -s /home/ubuntu/PRUEBA/dir1 PRUEBA/dir3/enlacedir1
Posicionarse en dir3 y, empleando el enlace creado en el ejercicio anterior, crear el directorio nuevo1 dentro de dir1.
cd dir3 mkdir enlacedir1/nuevo1
Utilizando el enlace creado copiar los archivos que empiecen por u del directorio /bin en directorio nuevo1.
cp -r /bin/u* enlacedir1/nuevo1/
Crear dos enlaces duros del fichero fich1, llamarlo enlace, en los directorios dir1 y dir2.
ln fich1 dir1/enlace ln fich1 dir2/enlace
Borrar el archivo fich1 y copiar enlace en dir3.
rm fich1 cp dir1/enlace dir3/
Crear un enlace simbólico (llamado enlafich1) al fichero enlace de dir2 en dir1.
ln -s /home/ubuntu/PRUEBA/dir2 /home/ubuntu/PRUEBA/dir1/enlafich1
Posicionarse en dir1 y, mediante el enlace creado, copiar el archivo fichl dentro de dir311.
cd dir1 cp enlafich1 ../dir2/dir31/dir311/fich1
Seguir en dir1 y, mediante el enlace creado, sacar por pantalla las líneas que tiene el archivo fich1.
cat enlafich1
Borrar el fichero fich1 de dir2.
rm dir2/fich1
Borrar todos los archivos y directorios creados durante los ejercicios. rm -r *
Crear el directorio dir2 y dir3 en el directorio PRUEBA ¿Cuáles son los actuales permisos del directorio dir2?
mkdir dir1 mkdir dir2 ls -l
Utilizando la notación simbólica, eliminar todos los permisos de escritura (propietario, grupo, otros) del directorio dir2.
chmod 555 dir2
Utilizando la notación octal, eliminar el permiso de lectura del directorio dir2, al resto de los usuarios.
chmod 551 dir2
¿Cuáles son ahora los permisos asociados a dir2?
ls -l
Crear bajo dir2, un directorio llamado dir2l.
mkdir dir2/dir21 no se puede crear perniso denegado
Concederse a sí mismo permiso de escritura en el directorio dir2 e intentar de nuevo el paso anterior.
chmod 751 dir2 mkdir dir2/dir21
¿Cuáles son los valores por omisión asignados a los archivos?
ls -l dir2
Cambiar el directorio actual al directorio dir3. Imprimir su trayectoria completa para verificar el cambio.
cd .. cd dir3 ls -lR
¿Cuáles son los permisos asignados en su momento a este directorio?
ls -lR
Reiniciar el ordenador.
reboot
Crear cuatro nuevos directorios llamados dira, dirb, dirc, y dird bajo el directorio actual.
mkdir dira mkdir dirb mkdir dirc mkdir dird
Comprobar los permisos de acceso de los directorios recién creados para comprobar el funcionamiento del comando umask.
ls -l
Crear el fichero uno . Quitarle todos los permisos de lectura. Comprobarlo. Intentar borrar dicho fichero.
touch uno chmod a-r uno ls -l rm uno
Quitarle todos los permisos de paso al directorio dir2 y otorgarle todos los demás.
chmod = dir2 chmod o=rwx dir2
Crear en el directorio propio:
El directorio carpeta1 con los tres permisos para el propietario, dentro de él fich1 con lectura y escritura para todos y fich2 con lectura y escritura para el propietario y solo lectura para el resto.
El directorio carpeta2 con todos los permisos para el propietario y lectura y ejecución para los del mismo grupo. Dentro file1 con lectura y escritura para el propietario y los del grupo y file2 con los mismos para el propietario y solo lectura para el grupo.
mkdir carpeta1 chmod u=rwx,g=,o= carpeta1 touch carpeta1/fich1 touch carpeta1/fich2 chmod = carpeta1/fich1 chmod = carpeta1/fich2 chmod o=rw carpeta1/fich1 ls -l

mkdir carpeta2 chmod u=rwx,g=rx,o= carpeta2 touch carpeta2/file1 touch carpeta2/file2 chmod = carpeta2/file2 chmod = carpeta2/file1 chmod u=rw,g=rw carpeta2/file1 chmod u=rw,g=r carpeta2/file2 ls -l

Desde otro usuario probar todas las operaciones que se pueden hacer en los ficheros y directorios creados.
ls -lR

Visualizar la trayectoria completa del directorio actual. Crear dos directorios llamados correo y fuentes debajo del directorio actual.
mkdir correo mkdir fuentes
Posicionarse en el directorio fuentes y crear los directorios dir1, dir2, dir3.
cd fuentes mkdir dir1 mkdir dir2
Crear el directorio menus bajo correo sin moverse del directorio actual.
mkdir ../correo/menus
Posicionarse en el directorio HOME. Borrar los directorios que cuelgan de fuentes que acaben en un número que no sea el 1.
cd $HOME
Ver si existe el archivo tty2 en el directorio dev. En caso de que exista, ver su fecha de creación o actualización.
find PRUEBA/fuentes -type d -name "tty2" -exec ls -l {} \;
Ver los permisos que tienen los archivos que empiecen por tt del directorio /dev.
ls -l /dev/tt*
Visualizar la lista de los archivos ordinarios que están en el directorio /usr/bin.
find /usr/bin -type d -name "*" -exec ls -l {} \;
Visualizar la lista de todos los directorios que cuelgan del raíz.
find / -type d -name "*" -exec ls {} \;
Visualizar la lista de todos los ficheros que pertenezcan a root.
find / -user root -type f
Visualizar la lista de todos los ficheros .h del directorio /usr/include.
find /usr/include -type f -regex ".*.h"
Ejecutar todos los comandos que empiecen por ls del directorio /bin.
ls /bin/ls*
Visualizar de qué tipo son todos y cada uno de ficheros de todo el árbol del sistema propiedad de un usuario conocido.
find /home/ubuntu -exec file --mime-type -0 '{}' \;
Crear el directorio uno en el directorio HOME con permiso de escritura y paso para el propietario, de lectura y paso para los usuarios de su mismo grupo y ningún permiso para el resto de usuarios.
mkdir uno chmod u=rw,g=rw,o= uno ls -ld uno
Crear el directorio uno1 dentro del directorio creado en el ejercicio anterior con todos lo permisos para el usuario, ninguno para los usuarios del grupo y permiso de escritura para el resto de usuarios.
chmod u=rwx,g=rwx,o= uno mkdir uno/uno1 chmod u=rwx,g=,o=w uno/uno1 ls -ld uno/uno1
Copiar todos los ficheros propiedad de un usuario conocido que acaben en un número en el directorio menus.
find /home/usuario2 -type f -regex ".*[0-9]" -exec cp -r '{}' PRUEBA/correo/menus/ \;
Visualiza con la orden who la relación de usuarios conectados y sus terminales. Mediante la orden cat, crea un pequeño mensaje desde tu consola y redirígelo a uno de los terminales conectados.
sudo -s
Crea un archivo de tamaño 0
touch archivo_tamaño_cero
Visualiza el archivo /etc/motd, que contiene el "mensaje del día".
cat /etc/motd
Utilizando de entrada la información de los usuarios conectados al sistema, guardar, ordenadas por el campo hora, las líneas correspondientes al usuario que se desee en el archivo persona.
who | grep $USER | sort -k 4 > persona
Crear el directorio carpeta debajo del directorio PRUEBA. Quitarle todos los permisos de lectura. A continuación, buscar todos los directorios que cuelguen del directorio propio y guardarlos en el archivo direc.
mkdir carpeta chmod a-r carpeta find ~ -type d > direc
Volver a realizar la segunda parte del ejercicio anterior, pero redireccionando los errores al fichero malos. Comprobar la información del fichero malos.
find ~ -type d 2> malo
Añadir al fichero direc la lista de todos los ficheros ordinarios que cuelguen de /etc.
find /etc -type f >> direc
Añadir al archivo nuevalista el/los nombre/s de el/los fichero/s del directorio PRUEBA que contengan en su nombre la cadena "ai", añadiendo el posible error al fichero malos.
find ./ -type f -not -iname ai 1> nuevalista 2> malos find ./ -type f -iname ai 1> nuevalista 2> malos
Sacar por pantalla únicamente el tiempo (buscar comando time) que tarda en ejecutarse el comando who.
time 'sleep 3' time who -p %e
Sacar por pantalla un listado completo (buscar comando ps) de los procesos que está realizando el usuario root.
ps -U root -u root u
Crear el archivo proceso con los procesos que no tienen ningún terminal asignado.
ps -U root -u root u | grep -v "'ls /dev'"
Añadir al fichero anterior la fecha actual y la trayectoria completa del directorio actual.
echo "'date +"%A %D"' - 'pwd'" >>nuevalista
Sacar por pantalla el listado de todos los usuarios conectados ordenados por número de proceso asignado.
ps axu
Averiguar cuál es la actividad actual del sistema. Para ello visualice un listado completo del estado de todos los procesos que se están ejecutando en el sistema.
top -d 1 -n 10
Obtener un listado con los siguientes datos de los procesos de su shell actual.
ps -e
Mostrar cuantos usuarios tiene registrados el sistema (el registro de usuarios está en el archivo /etc/passwd)
cat /etc/passwd | wc -l
Mostrar cuántos usuarios tiene registrados el sistema y que utilizan el intérprete bash (debe aparecer al final de la línea /bin/bash o similar)
cat /etc/passwd | grep bash
Mostrar cuantos usuarios hay conectados
who -q
Mostrar las líneas, de un archivo de texto, empiecen por L (mayúscula o minúscula)
man gcc > gcc.man_page cat gcc.man_page | sed -e 's/ //g' > file.filled cat file.filled | grep ^[Ll]
Contar las líneas, del ejemplo anterior
cat file.filled | grep ^[Ll] | wc -l
Extraer los nombres de usuario (primer campo) del sistema
cat /etc/passwd | cut -d ':' -f 1
Extraer los nombres de usuario y el shell que utilizan (último campo)
gawk -F: '{print $1, $7}' /etc/passwd
Cambiar la fecha de creación de un archivo ya previamente creado
touch -t 8810011101 good ls -l good
Calcular la firma md5 de un archivo
md5sum good
Modificar la firma md5 y detectar que se ha cambiado (revisión de firma)
md5sum -c good.MD5 md5sum good md5sum -c good.MD5 md5sum good
Monitorear la ocupación de las particiones en los discos
df -lh
¿Cual es el proceso que más carga el procesador?
for x in seq 1 10; do ps -eo pid,pcpu,pmem,user,args | sort -r -k 2 | head -n 2; sleep 3; done
¿Está corriendo el proceso bash?
ps -eo pid,pcpu,pmem,user,args | grep bash ps a | grep bash
¿Cuántos procesos que empiecen por k están corriendo?
ps -eo args | cut -d ' ' -f 1 | grep ^g | wc -l
