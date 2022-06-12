# Guía de instalación  Linux 

#
## ¿Cómo puedo descargar Docker?


Docker en Linux es una herramienta nativa pensada tanto para desarrolladores como para ambientes productivos. 

Al instalarlo en nuestra estación de trabajo lo utilizaremos como desarrolladores.

#
### ¿Cómo instalarlo?



1) Desde una terminal ejecutar el siguiente comando: sudo apt-get update 
2) Luego, en la misma terminal, ejecutar el comando: sudo apt-get install docker-ce docker-ce-cli containerd.io
3) Para instalar Docker-Compose, ejecutar el siguiente comando: sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose 
4) Finalmente ejecutar: sudo chmod +x /usr/local/bin/docker-compose


#
### Cómo ejecutarlo


Una vez finalizado el proceso de instalación, desde una consola de bash podemos ejecutar ***docker --version*** para validar la instalación.

#
### Play with Docker, ¿qué es?


En caso de no poder instalar Docker, Play with Docker es una herramienta que nos permite usar Docker de forma temporal en el la nube sin la necesidad de instalarlo
localmente.
Para ello, debemos estar registrados en Docker Hub. Visitando https://labs.play-with-docker.com/, hacemos clic en Login ¡y estamos listos para empezar!
























#
#
#
#
#


See you on [Day 26](day26.md)
