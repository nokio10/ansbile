# ansbile

## Задание 

Подготовить стенд на Vagrant как минимум с одним сервером. На этом сервере используя Ansible необходимо развернуть nginx со следующими условиями:

необходимо использовать модуль yum/apt;
конфигурационные файлы должны быть взяты из шаблона jinja2 с перемененными;
после установки nginx должен быть в режиме enabled в systemd;
должен быть использован notify для старта nginx после установки;
сайт должен слушать на нестандартном порту - 8080, для этого использовать переменные в Ansible.

## Решение 

Запустить vagrant командой "vagrant up"
После запуска машины запустить плейбук 
```
ansible-playbook -i inventory/hosts.ini -l cluster load.yaml --key-file=./id_rsa -u root
```

Стартовая страница nginx будет доступна на порту 8081 гостевой машины. 
```
box.vm.network "forwarded_port", guest: 8080, host: 8080
```


![image](https://user-images.githubusercontent.com/98832702/165351621-6fcba5f7-23e5-417d-b1b6-a396b1c9f76a.png)


