# TFTP Server running in docker

docker run -p 0.0.0.0:69:69/udp -v /var/tftpboot:/var/tftpboot -i -t pghalliday/tftp
