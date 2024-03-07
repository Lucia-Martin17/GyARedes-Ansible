# Demo Ansible

En esta demo, vamos a configurar dos perfiles en máquinas distintas, un perfil por defecto que sería de un oficinista y otro perfil alternativo que sería de desarrollador.

## Escenarion Inicial

Se dispondría de dos máquinas virtuales basadas en Lubuntu 22.04.4 (buscaba un sistema operativo ligero sin muchas cosas instaladas) con las mismas características.

* Procesadores: 1 vCPU
* Memoria base: 2048 MB
* Almacenamiento: 16,00 GB
* Interfaces de red: NAT y sólo anfitrión

Ambas se provisionarán mediante ssh

## Instalación de Ansible en mi máquina

Al tener Windows 11 instalado en mi diso duro, utilizaré una máquina virtual de Ubuntu 22.04.1 configurada de la siguiente manera:

* Procesadores: 1 vCPU
* Memoria base: 2048 MB
* Almacenamiento: 25,00 GB
* Interfaces de red: NAT y sólo anfitrión

Instalación en Ubuntu:

`sudo apt-get update`
`sudo apt-get install ansible`
`ansible --version`