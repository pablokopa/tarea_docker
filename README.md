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
```bash
docker run --name dam_alp1 alpine
```
Se crea un contenedor utilizando **--name** seguido del nombre que le queremos poner.

Para acceder a él se utiliza:
```bash
docker start -i dam_alp1
```
