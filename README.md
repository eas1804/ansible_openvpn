1. Указать IP адрес linux сервера в файле hosts. Белый или серый

2. Укзать логин и путь к ключу. каталог group_vars

3. defaults/main.yml
- openvpn_interface: eth0           сетевой интерфейс, смотрящий в и-нет
- openvpn_addres:  el2.mlp.pp.ua    Белый Ip  или доменное имя VPN сервера
- Указать порт: 1194
- Список пользователей

4. В файле 5-config_server.yaml указать подсеть. Последняя строка
 - push "route 192.168.18.0 255.255.255.0"

Если нужно всеь трафик напрвить через VPN В файле 5-config_server.yaml
- push "redirect-gateway def1 bypass-dhcp"
- push "dhcp-option DNS 208.67.222.222"
- push "dhcp-option DNS 208.67.220.220"

5. Запуск
ansible-playbook  playbook.yaml  -i hosts  -vD