# T2-Taller-de-Redes-y-Servicios
Tarea 2: Instalación de servicios 

<h1> Configuración previa </h1>
Para hacer uso de este sistema, se deben ubicar en la en la raíz del server y del cliente (terminal diferentes).

En la consola del server correr:
```diff
sudo docker build -t "server_v:dockerfile" .
```
y luego: 
```diff
sudo docker run -it "server_v:dockerfile"
```

Esto nos dejara el contenedor del server listo para usar.

Por otro lado, en la consola del cliente correr:
```diff
sudo docker build -t "cliente_v:dockerfile" .
```
y luego:
```diff
sudo docker run -it "cliente_v:dockerfile"
```

Esto nos dejara el contenedor del cliente listo para usar.

<h1> Configuración archivos servidor. </h1> 


Una vez que estamos dentro del container correspondiente al servidor Haraka, configuramos los siguientes ficheros existentes:

```diff
vim config/smtp.ini
```
listen=[::0]:25,[::0]:2555
nodes=cpus

------------------
Para recibir por ejemplo, un correo dirigido a usuario@dominio.com, se tiene que añadir dominio.com al archivo config/host_list. En esta actividad, se utiliza un correo personal de dominio gmail.com
```diff
vim config/host_list
```
gmail.com

------------------
Solo se aceptarán los mensajes a los dominios señalados en el archivo config/host_list y luego se entregarán a través del complemento smtp-forward. Por lo tanto, es necesario configurar el destino en config/smtp_forward.ini

```diff
vim config/smtp_forward.ini
```

host=smtp-relay.sendinblue.com
port=587
auth_type=plain
auth_user= XXXXXXXXXXXX             
auth_pass= XXXXXXXXXXXX            
check_recipient=false
check_sender=false


** Para guardar cambios en los archivos, ESC + :wq 

Una vez finalizada la configuración inicial, se ejecuta el servidor con el comando:
```diff
> haraka -c .
```

<h1> Cliente </h1> 

Una vez que estamos dentro del container  correspondiente al cliente SMTPc se realiza lo siguiente:
```diff
smtpc profiles add USER --host IP --port 25
```

Para conocer la IP del Server Haraka, se deben ejecutar los siguientes comandos (en un bash independiente a donde se están ejecutando el servidor y cliente):
      > docker container ls
    Se obtiene el CONTAINERID del Server
      > docker inspect <container id> | grep "IPAddress"

Luego, se configura el mail
```diff
smtpc messages add Prueba --subject 'Prueba' --body 'MensajePrueba' --from correopersonal@gmail.com --to correopersonal@gmail.com
```

Finalmente, se envia el mail
```diff
smtpc send --profile USER --message Prueba
```
  
Repositorios de los softwares ocupados:

- <a href= https://github.com/haraka/Haraka> Haraka </a>
- <a href= https://github.com/msztolcman/smtpc> SMTPC </a>
    
Video explicativo:

<a href="https://drive.google.com/file/d/1h-sSpOX3kXSaAaL8q6oVSn6nBXaUMWhz/view?usp=sharing" target="_blank">
<img src="" alt="LINK" width="240" height="180" border="10" />
</a>
