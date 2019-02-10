_Angular 7 - Spring_
====================
caracter multilinea:  `  `   //*para template:  `  ` 
### parte Angular 7 ### 
###### descargamos utilitarios: Atom, Angular CLI, typescript, nodeJS.
- apm install angular-2-typescript-snippets
- apm install atom-typescript
- apm install atom-bootstrap3
- apm install atom-bootstrap4
- apm install v-bootstrap4
- apm install platformio-ide-terminal
- apm install file-icons
- cd ~/.atom/packages /*despues*/ git clone https://github.com/emmetio/emmet-atom /*despues*/ cd emmet-atom /*despues*/ npm install
- apm install minimap
- ide-typescript ///*para dar formato*
- npm install --save @angular/material @angular/cdk @angular/animations  //*para mi*
###### descargamos utilitarios: Atom, Angular CLI, typescript, nodeJS.  
- npm install bootstrap --save
- npm install jquery --save
- npm install popper.js --save

###### Comenzando Angular7 ###### 
- ng new clientes-app  		// *creando un proyecto angular*
- ng serve -o   		// *levantamos el proyecto*
- ng g service cliente  	// *creando un servicio
- ng g class footer.component   // generando un clase
###### Hacer la aplicaccion reactivo - se actualice en tiempo real , stream I/O
- angular 5: import {Observable} from 'rxjs/Observable'; import {of} from 'rxjs/Observable/of'; 
- angular 6: import {of,Observable} from 'rxjs';

- *directiva para saber redireccionar*
```xml
<router-outlet></router-outlet>  
```
###### Opcionales
- Desde la versión 6 y 7 de angular se pasó a llamar angular.json, pero en versiones anteriores de angular se llamaba angular.cli.json
### FRONTED & BACKEND ### 
Envia URI Http al servidor. 

|     Verbos       |     URI          |   Action o Handler  |		
| ------------- | ------------- | ------------- |
|GET| /clientes		|index()	|
|GET| /clientes/create	|create()	|
|POST| /clientes		|store()	|
|GET| /clientes/{id}	|show()	|
|GET| /clientes/{id}/edit|edit()	|
|PUT| /clientes/{id}	|update()	|
|DELETE| /clientes/{id}	|destroy()	|
## Anotaciones: 
```java
- @SpringBootConfiguration : configuracion automatica, application.properties
- @EnableAutoConfiguration : habilitar la configuracion
- @ComponentScan		 : busca y registra en el contenedor de Spring todas las clases anotadas con @RestControler, @Controller, @Component, @Repository, @Service.
```
## Properties
```properties
spring.datasource.url=jdbc:mysql://localhost/db_spring_boot_backend
spring.datasource.username=root
spring.datasource.password=sasa
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.jpa.database-platform=org.hibernate.dialect.MySQL5InnoDBDialect
spring.jpa.hibernate.ddl-auto=create-drop  
/** 
- create: se crea cuando se levanta la App, si se baja, no se elimina.
- create-drop: se crea cuando se levanta la App, si se baja,se elimina.
- none: no hace nada, asume que tiene las tablas creadas.
- update: crea todo el sistema lka primera vez, luego va actualizando**
```






_Docker_ :pensive:
========
https://onedrive.live.com/?authkey=%21ANAqKS_syP3u2Os&id=2F5823B4594339C3%2116706&cid=2F5823B4594339C3 - virtual ubuntu con docker
user: docker   clave: lepanto | sudo: docker   clave: lepanto | 
#### Arrancar Docker: 
- systemctl status docker 
- systemctl stop docker 
- systemctl start docker 
- systemctl enable docker  // cuando el sistema arranque, lo permita autenticar
#### CentOs version <= 6
- service docker status  
- service docker start
#### Comando Basicos
- docker images  // ver las imagenes
- docker ps  	 // ver los contenedores prendidos
- docker ps  	 // ver los contenedores prendidos y apagados
- docker ps -l 	 // ver el ultimo contenedor que se modifico
- docker ps -n 4 // ver el ultimo 4 contenedor que se modificaron
- docker ps -a -n 3 -s// ver el ultimo 3 contenedor que se modificaron con la oclumna SIZE(tamaño)
- docker ps -a -q // mostrar los ID's
- docker ps -a -f "name=amazing_dirac"  // filtrar por nombre generado
- docker start -i e57354da7acf // e57354da7acf: es el CONTAINER_ID del contenedor
- docker run -d nginx  	       // -d: descarga y lo deja corriendo en modo background
- docker pull ubuntu:trusty    // descarga con la version trusty
- docker rm  deef7bbf4093      // remover un contenedor por CONTAINER_ID ó NAMES
- docker rmi -f fce289e99eb9   //Eliminar Imagen  -f: forzar
- docker run -it --name mi_ubuntu_ctm ubuntu bash   // NAME: mi_ubuntu_ctm, ya no sera aleatorio
- docker pull python   // descargo python, pro defecto latest la ultima version
- docker run -it --name mi_python python 	// le pongo un alias y se define com NAME y ya no se genera aleatorio y comienza correr
- docker exec -it mi_python bash		// ejecutar python con el nombre que le di
- docker run -d ubuntu sh -c "while true; do date; done"   // subo imagen, como background y comando linux ".."
- docker logs 206c --tail 5 	// mostrar los ultimo 5 lineas del log 206c: 4primeros digitos del CONTAINER_ID
- docker kill 206c   // matar un contenedor
- docker top 0a2  // para ver lso recursos del contenedor, que esta consumiendo mas
- docker stats // se vee lso recursos que esta consumiendo los contenedores que estan prendidos.
- while true; do date; done // coamndos linos, para realizar un bucle y asi ver el recurso que consume ese contenedor
- docker inspect 39ca > container1.txt   // inspect: detalle del contenedor y generar txt en la ruta.
- docker run -d -P nginx  // lo hacemos publico, por defecto nginx es http://localhost:32768/
- docker run -d --name nginx2 -p 8080:80 nginx  // le damos nombre al contenedor y mapeamos el puerto http://localhost:8080/
- docker network // red
- docker network inspect bridge  // ver detalle de la red "bridge"
- docker stop nginx2  // parar contenedor activo
- docker network create red1  // crear red , default:bridge
- docker network create --subnet=192.168.0.0/16 red2  // crear red, con ip 
- docker run -it --name ubuntua --network red1 ubuntu   // corro imagen con red que cree
- docker network connect red2 ubuntua // ubuntua puede trabajar con contenedores de la red1 y la red2
- docker network disconnect red2 ubuntua  //desconectar a la red
- docker run -it --rm  --name b1 busybox   // se coloca --rm para que lo elimine el contenedor despues de salir.
- docker run -it --rm  --name b2 busybox   // se coloca --rm para que lo elimine el contenedor despues de salir.
- docker run -it --rm --name b3 --link b1:maquina1 busybox  // enlace a la ip de la maquina b1 y le pones un alias y despues de salir del contenedor, que lo remueva.
- docker rm $(docker ps -a -q)  //borrar todos los contenededores apagados -f: forzar
##### docker mySQL
- docker run -d --name mysql_server --rm --network red1 -e MYSQL_ROOT_PASSWORD=secret mysql  //  -d: modod background, se pasa variable de entorno con valor "secret"
- docker exec -it mysql_server bash  // inicio el mysqlServer, con el nombre que le coloque "mysql_server"
- mysql -u root -p  // entrar al servidor y escribir la clave "secret"
###### me conecto de un cliente al servidorMysql
-  docker run -it --name mysql_client --rm --network red1 mysql bash //" "
-  mysql -h mysql_server -u root -p    // poner la clave "secret"
###### conectamos wordpress y mysql
- docker run -d --name mysql_wp --rm --network red1 -e MYSQL_ROOT_PASSWORD=secret mysql:5.7  //iniciamos mysql , la 5.7 aguanta wordpress
- docker run -d --name wp --rm --network red1 -e WORDPRESS_DB_HOST=mysql_wp -e WORDPRESS_DB_PASSWORD=secret -p 8080:80 wordpress // corremos wordpress, con los parametros, poniendo los datos del mysql que levantamos. 
- docker  network rm red1 // no funciona, hay que para los contenedores asociados, viendo "docker network inspect red1"
- docker stop mysql_wp  // parar el contenedor de mysql, no saldra en "docker ps -a" ya que lo iniciamos con --rm
- docker stop ws  // parar el contenedor de worpress, no saldra en "docker ps -a" ya que lo iniciamos con --rm
- docker network rm red1 // ya se puede borrar la red1, ya que paramos los contenededores asociados
###### volumenes
- docker volume ls  // vemos lso volumenes que tenemos, es para alojar todo lo que se edita o se guarda en el contenedor que se tiene levantado
- docker volume prune  // borra los volumenes que tenemos en el listado. 
- docker rm `docker ps -qa`
- docker volume prune
###### volumenes en linux 
- linux> cd /var/lib/docker/volumes/
- linux> ls -l
- linux> docker run -d --rm -p 80:80 --name cloud1 owncloud
- linux> ls -l
- linux> #cd
- linux> ls -l  // hacer cambio en la pagina localhost, y ver nuevamente la lista.
- linux> docker volume ls // se encunetra levantado, que se hicieron cambios ahi.
- linux> docker volume inspect 8900e560bd60b64da85cc2700c5d8ec8a670cd05c0dfb4fdfa827e0e99
fa0eb5 > v1.txt  // el codigo es el id
- linux> docker inspect cloud1 > cloud1.json
- linux> docker stop cloud1  // paramo el contenedor
- linux> docker volume ls // no esta
###### modificaciones en contenedores
- docker run -it --name ubuntu1 bash
- apt-get update  // ya que no podemos usar el comando "wget http://www.google.com
- apt-get install wget
- wget http://www.google.com // ya se puede ejecutar el siguiente comando.le damos exit, lo tenemos almacenado en "docker ps -a"
- docker start -i ubuntu1 //solo aqui tenemos la actualizacion con wget, "ubuntu1" si creas otros contenedores de la imagen1, no tendra la actualizacion que tiene el contenedor ubuntu1
- docker diff ubuntu1  //vemos los cambios que ha tenido el contenedor
- docker commit ubuntu1 mi_ubuntu_deyviz  // hicimos que copie una imagen de nombre "mi_ubuntu_deyviz" con los cambios y actualizaciones que se hizo en el contenedor "ubuntu1".
####### si queremos usar docker en LINUX: ubuntu
- sudo apt update 
- sudo apt upgrade
- sudo apt-get install apt-transport-https ca-certificates curl gnupg software-properties-common
- sudo apt-get install docker-ce
- // si sale error. =>
- curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –
- sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu cosmic nightly "
- sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
- sudo apt install docker-ce
- sudo systemctl enable docker
- sudo systemctl start docker
- sudo systemctl status docker
- docker -v
utilitarios:
- apt-get install systemd



Microservicios - _SpringBoot_ :sunglasses: 
=============================
https://github.com/dperezg2017/in28minutes.com/blob/master/_posts/2017-10-16-spring-micro-services.md

### Actuator ##
###### Paso1: en el properties => management.endpoints.web.exposure.include=*
###### Paso2: pom.xml: 
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.data</groupId>
			<artifactId>spring-data-rest-hal-browser</artifactId>
		</dependency>
###### Paso3: 
- Si se usa SprinbBoot 2.0.0 a (+) =>  POST: http://localhost:8080/actuator/refresh 
- Si se usa SprinbBoot 1.x a (+) =>  POST: http://localhost:8080/refresh ó http://localhost:8080/application/refresh
##### Opcionales
Si en caso se muestra problema de authorizacion, agregar en el properties => management.security.enabled=false.

### Spring Cloud Bus ##
Se debe implementar con MQRabbit - 
###### Paso1: Iniciar MQRabbit (Revisar procedimiento lineas mas abajo)
###### Paso2: Agregar la dependecia en "Limits-Service" y "Spring-cloud-config-server"
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-bus-amqp</artifactId>
		</dependency>
###### Paso3: 
- Si se usa SprinbBoot 2.0.0 a (+) =>  POST: http://localhost:8080/actuator/bus-refresh
- Si se usa SprinbBoot 1.x a (+) =>  POST: http://localhost:8080/bus/refresh
##### Opcionales
###### El Bus, esta estable en la version de SpringBoot => "2.0.2.RELEASE"
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.0.2.RELEASE</version>
		<relativePath /> <!-- lookup parent from repository -->
	</parent>
	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
		<!-- for 2.1.0 <spring-cloud.version>Greenwich.M1</spring-cloud.version> -->
		<spring-cloud.version>Finchley.SR1</spring-cloud.version>
	</properties>
	
### Hystrix ###
###### Paso1: Agregar la dependencia: 
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
<!-- 			<artifactId>spring-cloud-starter-hystrix</artifactId> -->
		</dependency>
###### Paso2: Agregar la anotacion "@EnableHystrix" en la clase Main del servicio "limits-service"
###### Paso3 Agregar en el Controller, una excepcion.
  @GetMapping("/fault-tolerance-example")
  @HystrixCommand(fallbackMethod="fallbackRetrieveConfiguration")
  public LimitConfiguration retrieveConfiguration() {
    throw new RuntimeException("Not available");
  }

  public LimitConfiguration fallbackRetrieveConfiguration() {
    return new LimitConfiguration(999, 9);
  }
######  Explicacion: Si no se agrega la linea:  @HystrixCommand(fallbackMethod="fallbackRetrieveConfiguration"), se mostrara la excepcion, pero le estamos diciendo, que si ocurre excepcion, vaya al metodo X. para abstener a una excepcion en ejecucion.

_GIT HUB_ - deben estar en la ruta del proyecto
===============================================
###### Subir Proyecto de cero: 
- git init
- git add *
- git status 
- git commit -m 'Subo la estructura del proyecto al repositorio de GitHub'
- git remote add origin https://github.com/dperezg2017/Help_Dev.git
- git push -u origin master
###### Subir cambios de Proyecto : 
- git add *
- git status 
- git commit -m 'Subo la estructura del proyecto al repositorio de GitHub'
- git push
###### Actualizar Proyecto:
- git pull
###### Descargar proyecto de gitHub:
- git clone https://github.com/dperezg2017/Help_Dev.git


VM _Argumentos_ 
===============
-Dserver.port=8001 

RabbitMQ _Colas_ 
================
 - Instalar RabbitMQ
 - Instalar 1: http://www.erlang.org/downloads
 - Instalar 2: https://www.rabbitmq.com/install-windows.html
 - Video: https://www.youtube.com/watch?v=gKzKUmtOwR4


###### paso1: https://zipkin.io/pages/quickstart.html  
###### paso2: click ultima version para descargar "zipkin-server-2.12.0-exec.jar" ,varia la version
###### paso3: abrir el CMD, ubicarte donde se encuentra el .Jar y escribir lo siguiente:
 - set RABBIT_URI=amqp://localhost
 - java -jar zipkin-server-2.12.0-exec.jar
###### paso4: ingresar: http://localhost:9411/zipkin/   
##### Recomendacion: Para ver que los servicios esten en el zipkin, debera agregar las dependencias:
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-zipkin</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.amqp</groupId>
			<artifactId>spring-rabbit</artifactId>
		</dependency>
##### Opcionales:
Para ver la interfaz: 
###### Paso1: en el CMD, escribir => rabbitmq-plugins enable rabbitmq_management
###### Paso2: ir a = > http://localhost:15672/#/queues
###### Paso3: registrarse con usuario y clave => guest

### Rabbit Simulador  - http://tryrabbitmq.com/?queue_id=cola2&queue_name=cola3

Se realizaron las pruebas para ver la diferencia de Exchange: topic,fanout,direct 
##### direct: tienes que enviarle exactamente como se llame el "routing key" para que pueda pasar por dicha cola. 
	example: Binding1 { "routing key": orange }    Binding2 { "routing key": orange.big }
		 Producer {"routing key": orange }
##### fanout: ovbia el nombre de los "routing key". igual se lleva enviar los mensaje a los consumers
	example: Binding1 { "routing key": orange }    Binding2 { "routing key": orange.big }
		 Producer {"routing key":  }
##### topic: tiene el #: remplasa 0 o letras, *:remplaza letras, en el ejemplo pasa por los dos binding: une el exchange con la cola. es lo diferente al topic.
	example: Binding1 { "routing key": orange.* }    Binding2 { "routing key": orange.big }
		 Producer {"routing key": orange.big }		 

Angular _version6_ 
==================
http://www.tic2.org/WebTecnica/Programas/SOperativos/Linux/Comandos/LinuxComandosEquivalencias.htm

- Instalar NodeJS
- npm install -g @angular/cli
- ng new my-dream-app
- cd my-dream-app
- ng serve

Si te falta librerias: npm update   ó  (dependiendo)   npm install --save-dev @angular-devkit/build-angular
## Proyecto
Para crear nuevo proyecto :  "ng new SPA" y levantarlo => "ng serve -o" en el CMD
Para generar nuevo componentes : "ng g c navbar"  ,donde g:generate y c:component
Para agregar Boostrap: "npm install bootstrap --save" , "npm install jquery --save" y "npm install popper,js --save"
###### Modificar file: "angular.json"
            "styles": [
              "src/styles.css",
              "node_modules/bootstrap/dist/css/bootstrap.min.css"
            ],
            "scripts": [
              "node_modules/jquery/dist/jquery.slim.min.js",
              "node_modules/popper.js/dist/umd/popper.min.js",
              "node_modules/bootstrap/dist/js/bootstrap.min.js"
            ]
Para no agrega Styles en mi componente: "ng g c heroes -is" se agrega la palabra "-is"








