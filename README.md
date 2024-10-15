# TAREA_02 - DOCKER

### 1. Descarga la imagen "alpine" SIN ARRANCARLA y comprueba que está en tu equipo
Para descargar la imagen de alpine desde el repositorio de **Docker Hub** sin ejecutarlo:
```bash
docker pull alpine
```

Para comprobar si la imagen está instalada se utiliza:
```bash
docker images
```
### 2. Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre
```bash
docker run alpine
```
Si, está arrancado. Para obtener el nombre se utiliza:
```bash
docker ps -a
```
En mi caso se ha creado con el nombre **'optimistic_engelbart'**.
### 3. Crea un contenedor con el nombre 'dam_alp1'. ¿Como puedes acceder a él?
Se crea un contenedor utilizando **--name** seguido del nombre que le queremos poner.
```bash
docker run -it --name=dam_alp1 alpine /bin/sh
```

- **_-i_**: Permite interactuar con el contenedor
- **_-t_**: Asigna una terminal al contenedor (es útil cuando queremos interactuar con la shell del contenedor.

Para acceder a él se utiliza:
```bash
docker start -ai dam_alp1
```
- **_-a_**: Permite ver la salida del contenedor directamente en la terminal.

### 4. Comprueba que ip tiene y si puedes hacer un ping a google.com
Iniciar el contenedor:
```bash
docker start dam_alp1
```
Comprobar la IP del contenedor:
```bash
sudo docker inspect dam_alp1 | grep IPA
```
Se ejecuta el contenedor:
```bash
sudo docker exec -it dam_alp1 sh
```
Se hace la prueba de ping para google.com
```bash
ping google.com
```
### 5. Crea un contenedor con el nombre 'dam_alp2'. ¿Puedes hacer ping entre los contenedores?
Crear el contenedor con nombre **dam_alp2**
```bash
docker run -dit --name dam_alp2 alpine
```
- **_-d_**: Ejecuta el contenedor en segundo plano, lo que significa que no se verá la salida directamente en la terminal

Se inician ambos contenedores y se comprueba sus IPs
Ahora se comprueba el ping entre contenedores utilizando:
```bash
docker exec -it dam_alp1 ping -c 4 172.17.0.2
```
- **_-c 4_**: Envía solo 4 paquetes en lugar de un ping continuo.

Se comprueba utilizando la IP del otro contenedor, es decir, para el caso de dam_alp1 se utilizará la IP de dam_alp2 y viceversa.
### 6. Sal del terminal, ¿que ocurrió con el contenedor?
Se utiliza **exit**, se abre la consola de nuevo, y se comprueban los contenedores.
```bash
exit
docker ps -a
```
En mi caso los contenedores siguen estando Up, según vi lo normal es que se cierren pero por la forma de iniciar los contendores puede ser que no lo hagan.
### 7. ¿Cuanta memoria en el disco duro ocupaste?
Para comprobar la memoria utilizada se utiliza:
```bash
docker system df
```
En mi caso he utilizado **7.811MB** en las imagenes, y **206B** para los contenedores.
### 8. ¿Cuanta RAM ocupan los contenedores? ¿Hay algún comando docker para saber esto?.
Para comprobar la memoria RAM utilizada se utiliza:
```bash
docker stats
```
Aquí se podrá ver más información relevante además del uso de memoria RAM.
En mi caso están utilizando **468KiB** y **476KiB** respectivamente.
