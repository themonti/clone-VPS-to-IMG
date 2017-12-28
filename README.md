# clone-VPS-to-IMG

Script para *clonar un VPS* por _ssh_ desde Digital Ocean, Alibaba Cloud, Vultr, Linode, Scaleway, etc. y generar imagen para Virtualbox, VMWare, etc.

## Getting Started

Este script es una modificación del Script creado por Radovan Brezula (http://brezular.com/2015/06/04/cloning-remote-linux-machines/) para poder clonar un VPS desde Digital Ocean, Alibaba Cloud, Vultr, Linode, Scaleway, etc.


Se ha modificado el script para permitir la extracción desde discos ```/dev/*v*da```.



### Prerequisites

En linux:
```
apt-get install sshpass pidof gawk qemu"
```
En MacOS
```
brew install https://raw.githubusercontent.com/kadwanev/bigboybrew/master/Library/Formula/sshpass.rb
brew install gawk
brew install pidof
brew install qemu
```

O bien, para convertir las imagenes es requerido VirtualBox.



## Running 

* Clona el respositorio
* Edita el fichero de texto ```iplist```y añade las IP de los VPS que deseas clonar. _(Nota: Una IP por fila.)_
* Ejecutar: 

Para conversión desde el script de la imagen.
```
sh backup-images-1.0.sh -c *vmdk* -d */dev/vda* -f iplist -u ssh_username -p ssh_password -t 1

- *vmdk*: puedes reemplazar por *vdi*, *vhd*., etc. 
- */dev/vda*: Para saber el nombre del disco de tu VPS puedes ejecutar: _fdisk -l_
```

Para conversión Con VirtualBox de la imagen.
```
sh backup-images-1.0.sh  -d */dev/vda* -f iplist -u ssh_username -p ssh_password -t 1

- */dev/vda*: Para saber el nombre del disco de tu VPS puedes ejecutar: _fdisk -l_
```
A continuación se descomrpime la imagen y se convierte con VirtualBox
```
gunzip <ip_server>.raw.gz
VBoxManage convertfromraw <ip_server>.raw new_name.vdi
```




## Versioning

1.1 - 28/12/2017

## Authors
* Antonio Monteagudo 

## Acknowledgments

Mis garadecimiento a Radovan Brezula, creador de este script: http://brezular.com/2015/06/04/cloning-remote-linux-machines/

