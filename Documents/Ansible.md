# Ansible, Automation platform

## Contenido

* [Introducción](#introducción)
* [¿Qué es Ansible?](#¿qué-es-ansible?)
    * [Historia](#historia)
    * [Definición](#ansible-plataforma-de-automatización)
* [¿Cómo Funciona?](#¿cómo-funciona?)
* [Alternativas](#alternativas)
* [Demo](#demo)

## Introducción

* La **automatización** es el uso de la tecnología para realizar tareas con la menor presencia humana posible.  
* Cualquier industria que conlleve tareas repetitivas puede usar la automatización, y en este caso tareas como el **aprovisionamiento**, **configuración de la red** o la **gestión de la configuración** pueden ser automatizadas.

### Aprovisionamiento

* El **aprovisionamiento** tiene que ver con el trabajo pesado, ya sea en hardware dedicado o en una nube privada, híbrida o pública. Para ejecutar sistemas empresariales, se necesita infraestructura y esa infraestructura debe estar **configurada**.
* Lo que antes se trataba de racks, cajas y cables en un centro de datos, ahora (en su mayoría) se trata de activos virtualizados, desde centros de datos definidos por software, redes y almacenamiento hasta máquinas virtuales y contenedores.

### Gestión de la configuración

* No todas las aplicaciones se crean de la misma manera. Requieren diferentes configuraciones, sistemas de archivos, puertos, usuarios... y la lista continúa. Una vez que haya automatizado el aprovisionamiento, debe poder indicar a esos recursos lo que deben hacer.
* Para ello, necesita una solución de **gestión de la configuración** sólida que permita a los desarrolladores definir simplemente la infraestructura (bare metal, virtualizada, en la nube, contenedores, etc.) de forma que todos los miembros de su equipo de TI puedan entenderla fácilmente. Cuanto más sencillo sea automatizar los scripts y las prácticas ad hoc para la gestión del sistema, más fácil será realizar el trabajo real.

## ¿Qué es Ansible?

### Historia

* El término "ansible" fue acuñado por Ursula K. Le Guin en su novela de 1966 Rocannon's World, y se refiere a los sistemas ficticios de comunicación instantánea.
* La herramienta Ansible fue desarrollada por **Michael DeHaan**, autor de la aplicación de servidor de aprovisionamiento Cobbler (servidor de aprovisionamiento de Linux que facilita y automatiza la instalación de sistemas basados en red de múltiples sistemas operativos informáticos desde un punto central utilizando servicios como DHCP, TFTP y DNS.) y coautor del marco Fedora Unified Network Controller (Func) para la administración remota.
* **Ansible, Inc.** (originalmente AnsibleWorks, Inc.) fue la empresa fundada en 2013 por DeHaan, Timothy Gerla y Saïd Ziouani para apoyar y patrocinar comercialmente a Ansible.  **Red Hat** adquirió Ansible en octubre de 2015.
* Ansible se incluye como parte de la distribución Fedora de Linux, propiedad de Red Hat, y también está disponible para Red Hat Enterprise Linux, CentOS, openSUSE, SUSE Linux Enterprise, Debian, Ubuntu, Scientific Linux y Oracle Linux a través de paquetes adicionales para Enterprise Linux, así como para otros sistemas operativos.

![Timeline](Images/timeline.PNG)

### Ansible, Plataforma de automatización

**Ansible** es una herramienta software de automatización de TI de código abierto que que reduce la complejidad y se ejecuta en todas partes. El uso de Ansible permite automatizar prácticamente cualquier tarea.


### Características

#### Casos de Uso
Con Ansible puedes:
* Eliminar la repetición y simplificar los flujos de trabajo
* Administrar y mantiener la configuración del sistema
* Implementar continuamente software complejo
* Realizar actualizaciones continuas sin tiempo de
inactividad

#### Princípios
* Arquitectura sin agentes
* Simplicidad
* Escalabilidad y flexibilidad
* Idempotencia y previsibilidad

## ¿Cómo funciona?

![Timeline](Images/ansible_inv_start.svg)

Como se muestra en la figura, la mayorıa de los entornos Ansible tienen tres componentes principales:

* **Nodo de control**: Un **sistema** en el que está **instalado Ansible**. Los comandos de Ansible se ejecutan en este nodo.
* **Inventario**: Una **lista de nodos administrados** que están organizados lógicamente. Se crea un inventario en el nodo de control para describir las implementaciones de host en Ansible.
* **Nodo administrado**: Un **sistema remoto**, o **host**, que controla Ansible.

### Playbooks:

Son los **scripts de automatización** para los nodos administrados. Utilizan sintáxis **YAML**.

Ejemplo:

```yml
---
- name: Update web servers
  hosts: webservers
  remote_user: root

  tasks:
  - name: Ensure apache is at the latest version
    ansible.builtin.yum:
      name: httpd
      state: latest

  - name: Write the apache config file
    ansible.builtin.template:
      src: /srv/httpd.j2
      dest: /etc/httpd.conf

- name: Update db servers
  hosts: databases
  remote_user: root

  tasks:
  - name: Ensure postgresql is at the latest version
    ansible.builtin.yum:
      name: postgresql
      state: latest

  - name: Ensure that postgresql is started
    ansible.builtin.service:
      name: postgresql
      state: started
```

```
ansible-playbook -i host playbook
```

## Alternativas

| **Tool**                             | **Ansible**                                                                                                  | **Terraform**                                                                                                          | **Puppet**                                                                                                          | **Chef**                                                                         | **Saltstack**                                                                 |
|:------------------------------------:|:-----------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------:|:--------------------------------------------------------------------:|
| **Supported resources**              | Configuration Management, Orchestration and Provisioning                                              | Provisioning                                                                                                  | Configuration Management                                                                                      | Configuration Management, Orchestration                                      | Configuration Management, Vulnerability Compliance                  |
| **Desired State**                    | Idempotency                                                                                           | Convergence                                                                                                   | Convergence                                                                                                   | Convergence                                                                  | Idempotency                                                          |
| **Infrastructure**                   | Mutable                                                                                               | Immutable                                                                                                     | Mutable                                                                                                       | Mutable                                                                      | Mutable                                                              |
| **Syntax**                           | Declarative                                                                                           | Declarative                                                                                                   | Declarative                                                                                                   | Declarative / Imperative                                                     | Declarative / Imperative                                             |
| **Approach control**                 | Serveless and Agentless                                                                               | Serveless and Agentless                                                                                       | Server and Agent                                                                                              | Server and Agent                                                             | Server and Minion \(Agent)                                          |
| **Configuration Language**           | ✓✓✓✓                                                                                                  | ✓✓✓✓                                                                                                          | ✓✓✓                                                                                                           | ✓✓✓                                                                          | ✓✓✓✓                                                                 |
| **Community and Cost Support**       | ✓✓✓✓                                                                                                  | ✓✓✓✓                                                                                                          | ✓✓✓✓                                                                                                          | ✓✓✓✓                                                                         | ✓✓✓                                                                  |
| **Maturity and Learning Curve**      | ✓✓✓✓                                                                                                  | ✓✓✓✓                                                                                                          | ✓✓✓✓                                                                                                          | ✓✓✓✓                                                                         | ✓✓✓                                                                  |
| **Can it be used with other tools?** | ✓✓✓✓                                                                                                  | ✓✓✓✓                                                                                                          | ✓✓✓✓                                                                                                          | ✓✓✓                                                                          | ✓✓✓✓                                                                 |
| **Best for**                         | The best tool for those beginning with Infrastructure\-as\-code managing heterogeneous environments\. | To simplify the management of environments in the public and private clouds, multi\-cloud and hybrid clouds\. | To orchestrate environments that have rigid compliance requirements, maintaining an immutable configuration\. | Continuous Automation on complex topologies or deployments that need speed\. | To orchestrate and to automate IT tasks with speed and flexibility\. |



## Demo

Toda la información de la demo está en el [guión](Guion.md).
