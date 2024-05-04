# GyARedes-Ansible
Trabajo + demo sobre la herramienta Ansible

## Categoría:

Configuration management/provisioning

## Demo:

* Cómo construir dos perfiles distintos (defecto y alternativo)
* Contruir nodo con perfil por defecto
* Indicar cómo establecer qué perfil debe aplicarse a un nodo
* Construir nodo con perfil alternativo según MAC/IP

## Entregables

Presentación:

`Documents/LaTeX/Ansible/template.pdf`

Guión demo:

`Documents/Guion.md`

## Eventos:

|**Evento**                   |**Información del evento**|
|:---------------------------:|:------------------------:|
|Finaliza un aprovisionamiento|IP del nodo aprovisionado |

Se añade lo siguiente para recibir una notificación de un bot de Telegram:

```yaml
- name: notificar por Telegram
      telegram:
        token: "token_del_bot"
        chat_id: "id_chat_del_bot"
        msg: "Aprovisionamiento oficinista finalizado. IP del nodo aprovisionado: {{ ansible_host }}"
      when: ansible_host is defined and ansible_host != ""
```
