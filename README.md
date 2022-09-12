0) зарегать VPS на edgecenter.ru (1680р/год)

1) sudo apt update
2) sudo apt upgrade -y
3) shutdown -r now
4) hostname -I
5) curl -sSL https://get.docker.com | sh
6) sudo usermod -aG docker $(whoami)
7) docker
8) docker images
9) docker run -d \
  --name=wg-easy \
  -e WG_HOST=ВАШ_IP_АДРЕС_СЕРВЕРА \
  -e PASSWORD=ПАРОЛЬ_ДЛЯ_ВХОДА_В_ВЕБ_ИНТЕРФЕЙС \
  -v ~/.wg-easy:/etc/wireguard \
  -p 51820:51820/udp \
  -p 51821:51821/tcp \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_MODULE \
  --sysctl="net.ipv4.conf.all.src_valid_mark=1" \
  --sysctl="net.ipv4.ip_forward=1" \
  --restart unless-stopped \
  weejewel/wg-easy

10) docker images
11) docker ps -a
12) Веб-интерфейс теперь будет доступен на: http://ВАШ_IP_АДРЕС_СЕРВЕРА:51821

Обновление
Чтобы обновиться до последней версии, просто запустите:
1) docker stop wg-easy
2) docker rm wg-easy
3) docker pull weejewel/wg-easy

Разработчик данного WireGuard: https://github.com/weejewel/wg-easy
<>THX<>