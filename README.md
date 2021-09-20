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

Una vez dentro de los contenedores respectivos, debemos configurar el lado del servidor. Para ello ejecutamos:
```diff
vim config/smtp.ini
```
Donde se debe establecer las lineas "listed" y "nodes" como a continuación:
```diff
- listen=[::0]:25,[::0]:2555
- nodes=0
```
Luego, se debe utilizar el siguiente comando:
```diff
vim config/host_list
```
Donde se añaden los dominios de correo de preferencia, ejemplo: gmail.com, hotmail.com, etc.
Y finalmente, se utiliza:
```diff
vim config/smtp_forward.ini
```

Y se añade las siguientes dos lineas
```diff
- host=8.8.8.8 (o alguna otra ip que deseen probar)
- port=25
```


<h1> Uso </h1>
