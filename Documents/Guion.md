# Demo Ansible

En esta demo, vamos a configurar dos perfiles en máquinas distintas, un perfil por defecto que sería de un oficinista y otro perfil alternativo que sería de desarrollador.

## Escenarion Inicial

### Nodos Administrados

Se dispondría de dos máquinas virtuales basadas en Lubuntu 22.04.4 (buscaba un sistema operativo ligero sin muchas cosas instaladas) con las mismas características.

* Procesadores: 1 vCPU
* Memoria base: 2048 MB
* Almacenamiento: 16,00 GB
* Interfaces de red: NAT y sólo anfitrión

Ambas se provisionarán mediante *ssh*, por lo que en la máquina administrada habrá que instalar `openssh`:

`sudo apt-get update`
`sudo apt-get install openssh-server`

Comprobar que está activado:

`sudo systemctl status ssh`

Abrir puerto:

`sudo ufw allow ssh`

### Nodo de control

Al tener Windows 11 instalado en mi disco duro, utilizaré una máquina virtual de Ubuntu 22.04.1 configurada de la siguiente manera:

* Procesadores: 1 vCPU
* Memoria base: 2048 MB
* Almacenamiento: 25,00 GB
* Interfaces de red: NAT y sólo anfitrión

### Conexión ssh

En este nodo también hay que tener instalado `ssh` para poder hacer la conexión remota, además para poder autenticarnos remotamente necesitamos este paquete:

`sshpass - Non-interactive ssh password authentication`

Instalación:

`sudo apt-get install sshpass`

### Instalación de Ansible en el nodo de control

Instalación en Ubuntu:

`sudo apt-get update`
`sudo apt-get install ansible`

Comprobar que se ha instalado:

`ansible --version`

*Nota: Puede que para instalar ansible además deberás de instalar python3*

## Comprobar conexión ssh con los nodos administrados

Como el provisionamiento va a ser por *ssh* antes tendremos que conectarnos para comprobar la conexión con los nodos y para crear el *key fingerprint*:

`ssh usuario-1@<ip-nodo-administrado>`

La dirección ip del nodo administrado se puede mirar con:

`ip addr`

## Cambiar inventario

## Comprobar playbook

## Ejecutar Ansible

`ansible-playbook -i <inventory> <playbook>`

La opción `-i` es para indicar el archivo de inventario, puedes cambiar el inventario que viene por defecto.

---

## Tabla resumen

|Variable|Valor por defecto|Significado|
|:------:|:---------------:|:---------:|
|`<ip-nodo-administrado>`|`<ninguno>`|Dirección IP del nodo adminstrado|
|`ansible_ssh_user`|`usuario-1`|Nombre del nodo administrado|
|`ansible_ssh_pass`|`usuario-1`|Contraseña para poder conectarse mediante *ssh*|
|`<inventory>`|`hosts.ini`|Inventario|
|`<playbook>`|`playbook.yml`|Script de automatización|

## Crear bot de Telegram:

1. Buscar el chat de BotFather de Telegram
2. Enviarle `\start`
3. Seguir las instrucciones:
    * `\newbot`
    * `nombre_del_bot`
    * `nombre_usuario_del_bot`
    * Recibiras un token
4. Mandar `/start` a tu bot para iniciarlo
5. Para obtener el `chat_id` mandar mensaje a tu bot y acceder a [https://api.telegram.org/bot<token\>/getUpdates]()
