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

Entonces primero vamos a modificar /dev/sda8

![image](https://github.com/user-attachments/assets/45594306-e151-4554-9282-5daddafee81a)

![image](https://github.com/user-attachments/assets/da2ecb14-4af6-4e25-a244-216be791de38)

Configuramos 5987 MiB de espacio libre antes de la partición /dev/sda8. Esto implica que la partición se moverá hacia la derecha, dejando espacio no asignado delante de ella.
El nuevo tamaño de la partición se ha establecido en 7201 MiB. Esto indica que la partición se reducirá de su tamaño original para liberar espacio adicional.

![image](https://github.com/user-attachments/assets/700f3d8a-b5a1-4277-bf69-e81c78026b78)

La particion sda8  ha sido movida hacia la derecha, liberando 5.85 GiB de espacio no asignado (unallocated) entre las particiones lógicas dentro de la extendida Además, el tamaño de la partición /dev/sda8 se ha reducido de 12.88 GiB a 7.03 GiB.Espacio no asignado ,se ha creado un nuevo espacio no asignado de 5.85 GiB, que antes formaba parte de la partición /dev/sda8.

Ahora modificaremos las particiones /dev/sda5, /dev/sda6, /dev/sda7.

![image](https://github.com/user-attachments/assets/bebbaef0-a0d2-4193-bdd0-455c451ba177)

![image](https://github.com/user-attachments/assets/f188ca2b-7425-46da-9e53-2f578d800d4f)

![image](https://github.com/user-attachments/assets/8281114d-648b-454b-83f2-83378873c560)

Repetimos este paso con /dev/sda5 y /dev/sda6. Esto con la intención de mover el nuevo espacio al lado de /dev/sda1.

![image](https://github.com/user-attachments/assets/5234852c-2731-4b37-8020-92866929d60f)

Por ultimo, modificaremos /dev/sda2

![image](https://github.com/user-attachments/assets/4d8f4573-ce14-4a6f-b558-4841f3e3afc2)

![image](https://github.com/user-attachments/assets/44ccf906-c912-45c9-881d-dbab9141fd46)

Luego asiganamos el espacio a /dev/sda1

![image](https://github.com/user-attachments/assets/74da8d65-1123-4b52-a032-e50b392a51aa)


![image](https://github.com/user-attachments/assets/6ac7c9fe-3a7f-4ea0-9d5f-008b35b64e7f)


![image](https://github.com/user-attachments/assets/9cc50f53-7dce-466e-9d48-8667bf9efebf)


![image](https://github.com/user-attachments/assets/886e447d-93a7-456d-b1fa-51165ca24a4f)

Despues de esto guardamos los cambios


![image](https://github.com/user-attachments/assets/f1fa488e-aa4d-4edb-8bad-5fd491ff3536)

Y salimos de la herramienta


![image](https://github.com/user-attachments/assets/ba8dbdb6-6e5d-4082-97dd-8336b7cb8037)

Volvemos a las settings de la máquina virtual y en la parte de CD/DVD, seleccionamos la opción "Use physical drive" para volver a iniciar el sistema de debian con la terminal.


![image](https://github.com/user-attachments/assets/128de650-fd6d-4dd5-aed3-7b17f9e817a4)

Para comprobar los cambios realizados en GParted, volvemos a ejecutar los comandos "df -h" y "lsblk"

![image](https://github.com/user-attachments/assets/935f5450-c209-4a9a-916e-f194f9ff0e71)
































