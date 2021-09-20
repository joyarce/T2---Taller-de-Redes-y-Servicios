# T2-Taller-de-Redes-y-Servicios
Tarea 2: Instalación de servicios 


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
