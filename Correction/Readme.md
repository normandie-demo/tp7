# Correction TP 7


## Se connecter sur *server-1.scc-edu* et arrêter le service *nginx*


```
ssh server-1.scc-edu
sudo systemctl stop nginx
```

## Modifier le playbook *nginx.yaml*

Editer le fichier *nginx.yaml*

```
  - name: Count nginx process
    ansible.builtin.shell: ps -ef | grep {{ main_service }} | grep -v grep | wc -l
    register: result

  - name: Display count
    ansible.builtin.debug:
      msg: "There is {{ result.stdout }} nginx process up"

  - name: Start Service
    ansible.builtin.systemd:
      name: "{{ main_service }}"
      state: started
    when: result.stdout == "0"

```

## Exécuter ce playbook sur l’inventaire *inventory*

```Shell
ansible-playbook -i inventory nginx.yaml
```
