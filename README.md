Este archivo describira como utulizar el Playbook de Ansible descargado el cual permite
instalar y configurar Apache para Loadbalancing en SO Cento&Ubuntu:

Recomendación:
Crear usuario en el Bastion y en los equipos clientes los cuales se utilizaran
para ejecutar el PLaybook y realizar las conexiones SSH, este usuario agregarlo como Sudoer.

Instalar Repositorio epel, con el seguiente comando:

sudo yum install epel-release


Paso 1 - Pre requisitos:

- Instalar Ansible en el equipo Bastion ejecutando el siguiente comando:

sudo yum -y install ansible

Paso 2 - Verificacion de archivos:

- Ingresar a la carpeta donde descargo los archivos, editar el achivo "inventario" y colocar
las direcciones IP de los Hosts donde quiere ejecutar el Playbook.

- En los archivos:

Carpeta_Descargada/lamp.yml
Carpeta_Descargada/roles/apache-centos/tasks/main.yml
Carpeta_Descargada/roles/apache-debian/tasks/main.yml
Carpeta_Descargada/loadbalancer.j2

Verificar que la ruta de los archivos de configuracion sean las correctas, y de no ser asi corregirlos.

Paso 3 - Chequeo y ejecucion:

- ubicarse en la carpeta descargada y ejecutar el siguiente comando para chequear que la sintaxis del PLaybook sea correcta:

ansible-playbook -i inventario --check lamp.yml --ask-become-pass

Si el comando no devulve ningun error de sintaxis continuar con lo siguientes, de lo contrario verificar nuevamente los archivos .yml.

- Si todo lo anterior esta correcto, se puede ejecutar el playbook con el siguiente comando:

ansible-playbook -i inventario lamp.yml --ask-become-pass

Con esto deberia quedar apache instalado y configurado en los equipos indicados en "inventario", en caso que se presente algun error,
verificar los archivos nuevamente.



