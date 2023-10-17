# Tarea: Configuración cliente + servidor DNS 
## 1. Utilizamos como base la práctica anterior
[Tarea: DNS - Docker Compose](https://github.com/ddasilvam/Tarea-DNS---Docker-Compose)
## 2. Añadimos un cliente al fichero de configuración de Docker Compose
```console
  asir_cliente:
    container_name: asir_cliente
    image: ubuntu:latest
    tty: true
    stdin_open: true
    networks:
      - dns_subnet
	dns:
      - 172.28.5.1
```
## 3. Levantamos los servicios e instalamos la herramienta "dig" en el cliente
```console
docker compose up
```
Una vez arrancado el servidor DNS y el cliente, abrimos una shell en el cliente e instalamos el paquete "bind-tools"
```console
apk add --no-cache bind-tools
```
## 4. Añadimos por cuestiones de retrocompatibilidad el servidor DNS en el fichero /etc/resolv.conf
Introducimos el siguiente comando en una shell del cliente:
```console
echo "nameserver 172.28.5.1" > /etc/resolv.conf
```