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


