# Practica02SUnix

# Gparted 
GParted (GNOME Partition Editor) es una herramienta de software libre que permite crear, redimensionar, mover, y gestionar particiones en discos duros y otros medios de almacenamiento. Es una aplicación basada en GUI (Interfaz Gráfica de Usuario), desarrollada para el entorno de escritorio GNOME, pero también puede usarse en otros entornos.
Esta herramienta nos sirve para 

* Crear Particiones: Puedes crear nuevas particiones en discos sin particionar o en espacio no asignado.
* Redimensionar Particiones: Permite aumentar o reducir el tamaño de particiones existentes sin perder los datos.
* Mover Particiones: Puedes mover una partición de un lugar a otro en el disco. Eliminar Particiones: Borra particiones existentes

# Pasos
Para esta practica primero descargamos la herramienta Gparted

![image](https://github.com/user-attachments/assets/dfdbbef8-2d22-4fa3-9a68-a59b41ea3992)

Y tenemos que entrar a nuestra maquina virtual sin LVM para ejecutar los comandos "df -h" y "lsblk" para mostrar el uso del espacio en disco de los sistemas de archivos montados

![image](https://github.com/user-attachments/assets/80781807-b784-4223-b6ee-657269b0a1f4)

Podemos ver la siguiente informacion:
Con el comando df -h
* udev: Sistema de archivos virtual que usa 946 MB y está montado en /dev.
* tmpfs: Sistema de archivos temporal, montado en /run con un tamaño de 194 MB.
* /dev/sda1: Partición de 4.0 GB, con 1.4 GB usados y 2.4 GB disponibles, montada en /.
* /dev/sda8: Partición de 13 GB, casi completamente disponible (12 GB), montada en /home.
* /dev/sda7: Partición de 338 MB, con 316 MB disponibles, montada en /tmp.
* /dev/sda5: Partición de 1.7 GB, con 1.3 GB disponibles, montada en /var.

Con el comando lsblk, podemos ver lo siguiente:

* sda: Disco duro principal con un tamaño de 20G.
* sda1: Partición de 4.1G montada en /.
* sda2: Partición de 1K (probablemente una partición extendida).
* sda5: Partición de 1.7G montada en /var.
* sda6: Partición de 976M usada como SWAP.
* sda7: Partición de 371M montada en /tmp.
* sda8: Partición de 12.9G montada en /home.
* sr0: Unidad de CD/DVD con un tamaño de 1024M.

Ahora iniciamos la maquina virtual y vemos lo siegiente:

![image](https://github.com/user-attachments/assets/1ac399d8-19d7-436e-ae38-fbaefaf103b3)

Luego sekleccionamos esta opcion 

![image](https://github.com/user-attachments/assets/0283a5b8-50a6-4373-adfd-691c8156d121)

Y sleccionamos las opciones por defecto, por lo que solo pulsamos enter en la terminal, despues veremos lo siguiente en donde vemos la particion del disco:

![image](https://github.com/user-attachments/assets/73705f17-0316-4a2c-9593-def9ae833d92)

Vemos que tenemos la siguiente informacion

* Disco seleccionado: /dev/sda con una capacidad total de 20.00 GiB.

Particiones existentes:

* /dev/sda1: Partición primaria con sistema de archivos ext4, tamaño de 4.12 GiB, y montada como partición de arranque (boot).
* /dev/sda2: Partición extendida que abarca varias particiones lógicas.
* /dev/sda5: Partición lógica dentro de la extendida, con sistema de archivos ext4, y un tamaño de 1.68 GiB.
* /dev/sda6: Partición lógica usada como linux-swap con un tamaño de 976.00 MiB.
* /dev/sda7: Otra partición lógica con sistema de archivos ext4, y un tamaño de 371.00 MiB.
* /dev/sda8: Partición lógica con sistema de archivos ext4, y un tamaño de 12.88 GiB.
* Espacio sin asignar: Hay un pequeño espacio no asignado de 1.00 MiB al final del disco.
Este esquema de particiones es típico en instalaciones de Linux, con una partición primaria para el arranque, una partición extendida que contiene múltiples particiones lógicas, incluyendo particiones para el sistema de archivos, intercambio (swap), y otros propósitos.











