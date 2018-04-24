##Postman
https://www.getpostman.com/docs/v6/postman/launching_postman/installation_and_updates
https://app.getpostman.com/app/download/linux64?_ga=2.126085774.208107287.1524496452-1290295698.1524496452
https://blog.bluematador.com/posts/postman-how-to-install-on-ubuntu-1604/?utm_source=hootsuite&utm_medium=twitter&utm_campaign=


wget https://dl.pstmn.io/download/latest/linux64 -O postman.tar.gz
sudo tar -xzf postman.tar.gz -C /opt
rm postman.tar.gz
sudo ln -s /opt/Postman/Postman /usr/bin/postman


cat > ~/.local/share/applications/postman.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=postman
Icon=/opt/Postman/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
EOL

##CapsLock2Esc
https://blog.csdn.net/mzqj_WPF/article/details/41120175
解决方案


1、以下代码保存为 CapsLock2Esc.reg 文件；
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,03,00,00,00,3a,00,01,00,01,00,3a,00,00,00,00,00

2、双击该文件，弹出框，选“是”；

3、重启系统，完成。