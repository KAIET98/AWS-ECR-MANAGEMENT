# AWS-ECR-MANAGEMENT
Creación de un repositorio donde podremos hostear nuestras imagenes de Docker en un entorno de AWS

# ECR

Nos posicionamos en el servicio de ECR y creamos nuestro primer repositorio. 

## General Settings: 

Visibilidad: Privada

Repository name: 

```
demostephane
```
Se pueden ver diferentes opciones: 
1. Tag inmmutability: que te evita que pushees dos imagenes con el mismo tag
2. Scan on push: que te mire que lo que pushee no tenga un fallo de seguridad
3. Encryption: encriptear con KMS. 

## Subida de docker: 

Si entramos en el repositorio no tendremos ninguna imagen construida; Vamso a ver los 'Push commands' para ver como podemos subir una imagen.
Yo lo voy  a hacer en Windows desde la consola de GIT, ojo esto es improtante: 

### Operaciones en el ordenador: 

Miramos si tenemos docker instalado y que version tiene, es decir, en la termina del ordenador laznamos: 

```
docker --version
```

Luego vamos a instalar el CLI: 

```
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin <TU_ACCOUNT_ID>.dkr.ecr.eu-west-1.amazonaws.com
```

Nos bajamos la imagen (https://hub.docker.com/r/nginxdemos/hello/), abrimos Docker de paso...


```
docker pull nginxdemos/hello
```
Cambiamos de nombre, partimos de: 

```
docker tag demostephane:latest<TU_ID_ACCOUNT>.dkr.ecr.eu-west-1.amazonaws.com/demostephane:latest
```

Quitamos la parte de docker tag... y le ponemos el nombre de la imagen de docker qu eacabamos de bajar: 

```
docker tag nginxdemos/hello<TU_ID_ACCOUNT>.dkr.ecr.eu-west-1.amazonaws.com/demostephane:latest
```
Entonces, la imagen tambien se ha cambido de nombre; como lo podemos comprobar esto? pues haciendo lo sigueinte: 

```
docker push 070307590085.dkr.ecr.eu-west-1.amazonaws.com/demostephane:latest

```
Es suficientemente inteligente como para subir lo úlitmo


Entonces, si vamos al repositorio de Amazon ECR y refrescamos la página; tendremos la imagen ya en nuestro repositorio privado. 
