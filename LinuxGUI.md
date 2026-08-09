sudo apt install xfce4 xfce4-session xrdp
sudo systemctl enable xrdp
sudo adduser xrdp ssl-cert
echo xfce4-session >~/.xsession
sudo systemctl restart xrdp
-> rdp inbound roule
