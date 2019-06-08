_Angular 7 - Jhipster
====================
######para tener un gestor de dependencias:###### npm install -g yarn
######para agregar yeoman con yarn:###### yarn global add yo
######para agregar el generadot jhipster de yeoman:###### yarn global add generator-jhipster

_Angular 7 - Spring_
====================
caracter multilinea:  `  `   //*para template:  `  ` 
### FRONTED ### 
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
- npm install weetaler2 --save     //*si sucede error* npm install --save sweetalert2@7.26.9
###### descargamos utilitarios: Atom, Angular CLI, typescript, nodeJS.  
- npm install bootstrap --save
- npm install jquery --save
- npm install popper.js --save
###### Angular Material, similar al Bootstrap
- ng add @angular/material
- npm install --save @angular/material-moment-adapter
- npm install --save moment

###### Comenzando Angular7 ###### 
- ng new clientes-app  		// *creando un proyecto angular*
- ng serve -o   		// *levantamos el proyecto*
- ng g service cliente  	// *creando un servicio
- ng g class footer.component   // generando un clase
- ng g c usuarios/login --flat=true  // dentro de la carpeta usuarios se genera login
- ng g class usuarios/usuario  // crea usuario.ts dentro de la carpeta usuarios.
- ng g g usuarios/guards/auth // dentro de la carpeta usuarios, crear otra carpeta guardas y ahi los TS. 
- ng g c facturas/detalleFactura --flat  // --flat: para que no me cree un directorio estra, simplemente dentro de factura
###### Hacer la aplicaccion reactivo - se actualice en tiempo real , stream I/O
- angular 5: import {Observable} from 'rxjs/Observable'; import {of} from 'rxjs/Observable/of'; 
- angular 6: import {of,Observable} from 'rxjs';

- *directiva para saber redireccionar*
```xml
<router-outlet></router-outlet>  
```
-*casteo Observable*
```xml
return this.http.get<Cliente[]>(this.urlEndPoint);
```
###### Opcionales
- Desde la versión 6 y 7 de angular se pasó a llamar angular.json, pero en versiones anteriores de angular se llamaba angular.cli.json
- Binding: Poblar y enlazar

### BACKEND ### 
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
@Bean: se le asigna, a metodos que retorna otro metodo (return new BCryptPasswordEncoder()), y despues en otra clase solo se le asigna la anotacion @Autowired, si en caso hay varios @Bean("authenticationManager"), indicar @Qualifier("authenticationManager") para apuntar al correcto
@SpringBootConfiguration : configuracion automatica, application.properties.
@EnableAutoConfiguration : habilitar la configuracion.
@ComponentScan	   	 : busca y registra en el contenedor de Spring todas las clases anotadas con @RestControler, @Controller, @Component, @Repository, @Service.
@ManyToMany(fetch = FetchType.LAZY, cascade = CascadeType.ALL): relacion de * a * y crea la tabla de la relacion, y cascade para que realice todo lo que con lleva auna funcion GUARDAR(guarda informacion, fotos si es que tenia, etc.)
@ManyToOne(fetch=FetchType.LAZY) : LAzy, solo realizara la carga, cuando se le llame con el GET generado, y genera un proxy con la variable, para ello se puede omitir con @JsonIgnoreProperties({"hibernateLazyInitializer","handler"}), asi solo hara caso a las variables que estan en la clase entity.
y si se tiene problemas de recursividad, agregar lo siguiente: 
@JsonIgnoreProperties(value={"facturas","hibernateLazyInitializer","handler"},allowSetters=true)
@JoinTable(name="users_authorities",joinColumns=@JoinColumn(name="user_id"),inverseJoinColumns=@JoinColumn(name="role_id")	,uniqueConstraints= {@UniqueConstraint(columnNames= {"usuario_id","role_id"})})): sirve para darle nombre a la tabla que se crea de la relacion de * a *, y ponerle nombre a la llave foranea, de las 2 tablas. y que la llaves foraneas sean UNICAS. 
@JoinColumn(name="region_id") : nombre que le das a la llave foranea
@GeneratedValue(strategy=GenerationType.IDENTITY)
- AUTO		: genera de forma automatica, es como un "default"
- IDENTITY	: mySQL, mySQLServer, las llavesy ID se geenran de forma incremental, BD en memoria, embebida, H2.
- SEQUENCE	: Oracle, PostgreSQL
@Temporal(TemporalType.DATE)	
- DATE 		: Fecha
- TIME 		: Hora
- TIMESTAMP	: Fecha y Hora
@Transactional(readOnly=true)
-readOnly: de solo lectura, transaccion por que mandara una solicitud a la BD. pero recordar que CrudRepository ya viene con transaccionalidad.
@Autowired		: para Inyectar, queda guardado en el contenedor de spring. usarlo para un service, controller, etc. si se tiene mas de una, se usa un @Qualifier
@Service		: es un estereotipo de @Component
@CrossOrigin(origins= {"http://localhost:4200"}) : Se agrega en el controlador, para permitir manejo de datos con el siguiente dominio. 
@PrePersist		: en la clase @Entity, se le pone el @PrePersist al metodo que va generar un valor, para una @Column
@ResponseStatus		: @ResponseStatus(HttpStatus.CREATED), si todo sale bien, nos muestra code:201 de creado, entre otros como .CREATE , .OK ,etc. 
@PostMapping: para realizar update, create.
@GetMapping: consultar, selects. 
@RequestParam: Archivo(multiparam)
@PathVariable: String, long .. 
@Valid: validador, que respete segun el Entity @size @notNull @notEmpty @Email
@RequestBody: cuando se manda una entindad Cliente cliente. ó Person persona, viaja los datos de esa persona.
@EnableGlobalMethodSecurity(securedEnabled=true): Habilitar globalmente, para validar roles con anotaciones. y poner encima de cada Servicio rest @Secured({"ROLE_ADMIN","ROLE_USER"})

```
## JUnit - Mockito: 
```java
@After/before : Hacer que un evento se ejecute antes o despues de cada evento en X clase.
@AfterClass/beforeClass : Hacer que un evento se ejecute antes o despues de todos lo eventos de una clase X.


```
## Properties: 
```properties
spring.datasource.url=jdbc:mysql://localhost/db_springboot_backend?useSSL=false
spring.datasource.username=root
spring.datasource.password=sasa
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.jpa.database-platform=org.hibernate.dialect.MySQL57Dialect
#spring.jpa.database-platform=org.hibernate.dialect.MySQL5InnoDBDialect
- .MySQL5InnoDBDialect	: entrando a esta clase, vemos que esta obsoleta por "@Deprecated"
- .MySQL57Dialect	: esta, no se encuentra obsoleta. 
spring.jpa.hibernate.ddl-auto=create-drop  
- create	: se crea cuando se levanta la App, si se baja, no se elimina.
- create-drop   : se crea cuando se levanta la App, si se baja,se elimina.
- none		: no hace nada, asume que tiene las tablas creadas.
- update	: crea todo el sistema lka primera vez, luego va actualizando
```
Opcionales:
- Doc JPA: *Core Concepts*
https://docs.spring.io/spring-data/jpa/docs/current/reference/html/
- cors: intercambio de recursos de origen curzados, intercambiar datos, flujos, string, archivos, dominio, hoja de estilos ,css, cualquier tipo de recursos, de un dominio a otro. contro lde acceso Http, para acceder a ciertos recurdo backend. serviciso que estan alojado en otro dominio. ya es un estandar para compartir entre diferentes dominios.
```
1) Prefligth request. 
- Se envia un GET, para ver que tipo de permisos tiene mi dominio.
2) Prefligth response
- Le devuelve que tipo de permisos tiene
3) Request 
- se envia el recurso que necesita, y valida si tiene permiso apra obtener ese recurso de mi dominio.
4) Response
- Devuelve la repsuesta, si es un Rest o un archivo,video,etc. 
```
## Informacion
- Path:  window: "C://Temp//uploads" Linux: "\opt\uploads"
- Si se trabaja con JDK9 ó JDK10, y se va usar Auth2, debe añadir JAXB API: 
```xml
<dependency>
    <groupId>javax.xml.bind</groupId>
    <artifactId>jaxb-api</artifactId>
</dependency>
<dependency>
    <groupId>org.glassfish.jaxb</groupId>
    <artifactId>jaxb-runtime</artifactId>
</dependency>
```
## Auth2 - generar RSA256 
- https://jwt.io/
- Se usa https://wiki.openssl.org/index.php/Binaries ó java JDK(OpenSSH): se encuentra codigos para certificado RSA para firmar Token JWT. elegimos para window: Win64 OpenSSL v1.1.0j.
- Pasos para generar firma RSA, despues de la descarga: 

```properties
D:\OpenSSL-Win64\bin>openssl genrsa -out jwt.pem
Generating RSA private key, 2048 bit long modulus
.........................................................................+++++
........+++++
e is 65537 (0x010001)

D:\OpenSSL-Win64\bin>openssl rsa -in jwt.pem
writing RSA key
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAybtxbosjtSOxudyu4yIvXy/NM2eS0c0dRwvif6YR3u3doTwP
2yQMYx3H+Di92v/Q9QzVetiYM1C3rWdmVThbNxJ4UUAbTF/xYSkszH6YuTYVtUUl
4ClBisDoTo3Z0m9moSLJ4Bqi2FqbAjbyPBFZZTTdGgUqGSTk8an0Tx8iQvdulIx6
KzCeY5RZIJuhvyDfn5e1IbmKBDfM5KXoMajGfDz14y47bkbi65umbEXxdEKqn0nS
bBmtR7msc0smdcL4YupembGqwX5o5ByRcd07jiD7bew1AmT4knECMEyYI0dJOKm9
X5jqVc+zrqTspTIB/o5m8SAfSryDOSkS+R/N7QIDAQABAoIBAQC/33cOS20VFvQt
8cat5o/kG1UzdWnh/xO/xYATJWOOA/RvLO9v4aOeim7umxmJORQIX8KU63ooJLfv
SI++srGfegPSVAUi6YZugXlIr4iXcOfI2BIkWVkrnjvWq3jofGjDDpGwg+Urn1Ic
EyLnGyFJ77P00cCu1bakXKAwuU4fHgKrztyF2azNc7phhRdcIBU+F4u4yY788A9h
Z4PuEVAlwPw222YddlSpU5KB8IZRJuYorWY1ZMAPqxg0q6jmwhjM0b1wJDxKg2Ta
8YnOn4T/vkFPDtbFC70kGxVuCyqxtoJTqIww4GSNodij6uPaE5zeyzO+n6cy25h9
5T6VhJDBAoGBAPgSaxBwpPshmQ2Gg+vQO5X/aPIrhsNl+n/F135ookm0VLsX62Zr
kqDiHHkW0rJ04JzCyzegvN4vxz6Z8FuiuKA0Dg/OMjZptF4FVtvNI7rBwQtEdfW2
YG3iTLahjkq/dz67knq0P521VN3KMvkVKmQHZs/xz7O0mmk7u6RbBASlAoGBANAt
5lZ/SkkyY74t9bwWq1NGtuw5/4XGtnyQxwxUhhBDh1TXNJ5A9G6XGh1vEJjbqhNh
+qVlKYx8aeQvu1CJDfGlbtlz7GrLnys/Z/66tSKKJECR4BU+IEdvGHxPZ3iVLlPD
bi39Q0fJ8Qf9SR8ZnyAN368SnnwvOi3LqToJsDmpAoGAfwc3adC0uqAGtqVV8i/M
A1ApVjCxrmcO8dTGN0WvLJy58qAZ+3VEPTvrppnoRFeTGNKqqw6VCBVhKo47RUE6
11YwiSlmDvTr1mVXh/AwxpYmmvVwjeTY1gvWioKJ0X7fufDk3g5ksQZEsdmzZlbP
QS+FFyBU4kmt9AsRV+T/Vr0CgYEAqTdWDqMjKAJcjx7eqwemNWe6kqPGLuBKP1CT
a1NdMeUiIPVZIPXdefM62AgKbqXHRkATM9PaBQawMDoYQStWeUCmrP0Mg/aFp+q/
RpBPYgb11sJ8aef45vfH6GvGyH5CjPXDHoDJ6pWcZYkdobj63lxIoQ86Yeklmkn8
gV+UrhkCgYApu7MldXRvLh58jgTOLsigCAkQriZR5ZsAVUA6sKoQenyZLeUCl8On
/424kxdAJnB3EsIYVVxSuabHgaJUCM4gSCOj3MFG838E8KxpsCXrrTuVoflBjZm0
yEEt54Qg/3Kk6BuGw0Jk7dhshe2F5vBcJ6fXhA4swl82RX1DvvBCpw==
-----END RSA PRIVATE KEY-----

D:\OpenSSL-Win64\bin>openssl rsa -in jwt.pem -pubout
writing RSA key
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAybtxbosjtSOxudyu4yIv
Xy/NM2eS0c0dRwvif6YR3u3doTwP2yQMYx3H+Di92v/Q9QzVetiYM1C3rWdmVThb
NxJ4UUAbTF/xYSkszH6YuTYVtUUl4ClBisDoTo3Z0m9moSLJ4Bqi2FqbAjbyPBFZ
ZTTdGgUqGSTk8an0Tx8iQvdulIx6KzCeY5RZIJuhvyDfn5e1IbmKBDfM5KXoMajG
fDz14y47bkbi65umbEXxdEKqn0nSbBmtR7msc0smdcL4YupembGqwX5o5ByRcd07
jiD7bew1AmT4knECMEyYI0dJOKm9X5jqVc+zrqTspTIB/o5m8SAfSryDOSkS+R/N
7QIDAQAB
-----END PUBLIC KEY-----
```
- implementar CORS: https://docs.spring.io/spring-security/site/docs/5.1.5.RELEASE/reference/htmlsingle/ : 
```java
    @Bean
    CorsConfigurationSource corsConfigurationSource() {
        CorsConfiguration configuration = new CorsConfiguration();
        configuration.setAllowedOrigins(Arrays.asList("https://example.com"));
        configuration.setAllowedMethods(Arrays.asList("GET","POST"));
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", configuration);
        return source;
    }
}
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
```xml
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.data</groupId>
			<artifactId>spring-data-rest-hal-browser</artifactId>
		</dependency>
```
###### Paso3: 
- Si se usa SprinbBoot 2.0.0 a (+) =>  POST: http://localhost:8080/actuator/refresh 
- Si se usa SprinbBoot 1.x a (+) =>  POST: http://localhost:8080/refresh ó http://localhost:8080/application/refresh
##### Opcionales
Si en caso se muestra problema de authorizacion, agregar en el properties => management.security.enabled=false.

### Spring Cloud Bus ##
Se debe implementar con MQRabbit - 
###### Paso1: Iniciar MQRabbit (Revisar procedimiento lineas mas abajo)
###### Paso2: Agregar la dependecia en "Limits-Service" y "Spring-cloud-config-server"
```xml
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-bus-amqp</artifactId>
		</dependency>
```
###### Paso3: 
- Si se usa SprinbBoot 2.0.0 a (+) =>  POST: http://localhost:8080/actuator/bus-refresh
- Si se usa SprinbBoot 1.x a (+) =>  POST: http://localhost:8080/bus/refresh
##### Opcionales
###### El Bus, esta estable en la version de SpringBoot => "2.0.2.RELEASE"
```xml
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
```
	
### Hystrix ###
###### Paso1: Agregar la dependencia: 
```xml
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
<!-- 			<artifactId>spring-cloud-starter-hystrix</artifactId> -->
		</dependency>
```
###### Paso2: Agregar la anotacion "@EnableHystrix" en la clase Main del servicio "limits-service"
###### Paso3 Agregar en el Controller, una excepcion.
```java
  @GetMapping("/fault-tolerance-example")
  @HystrixCommand(fallbackMethod="fallbackRetrieveConfiguration")
  public LimitConfiguration retrieveConfiguration() {
    throw new RuntimeException("Not available");
  }

  public LimitConfiguration fallbackRetrieveConfiguration() {
    return new LimitConfiguration(999, 9);
  }
```
######  Explicacion: Si no se agrega la linea:  @HystrixCommand(fallbackMethod="fallbackRetrieveConfiguration"), se mostrara la excepcion, pero le estamos diciendo, que si ocurre excepcion, vaya al metodo X. para abstener a una excepcion en ejecucion.

_GIT HUB_ - deben estar en la ruta del proyecto
===============================================
###### Subir Proyecto de cero: 
```git
git init
git add *
git status 
git commit -m 'Subo la estructura del proyecto al repositorio de GitHub'
git remote add origin https://github.com/dperezg2017/Help_Dev.git
git push -u origin master
```
###### Subir cambios de Proyecto : 
```git
- git add *
- git status 
- git commit -m 'Subo la estructura del proyecto al repositorio de GitHub'
- git push
```
###### Actualizar Proyecto:
```git
- git pull
```
###### Descargar proyecto de gitHub:
```git
- git clone https://github.com/dperezg2017/Help_Dev.git
```

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
```xml
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-zipkin</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.amqp</groupId>
			<artifactId>spring-rabbit</artifactId>
		</dependency>
```
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
```javascript
            "styles": [
              "src/styles.css",
              "node_modules/bootstrap/dist/css/bootstrap.min.css"
            ],
            "scripts": [
              "node_modules/jquery/dist/jquery.slim.min.js",
              "node_modules/popper.js/dist/umd/popper.min.js",
              "node_modules/bootstrap/dist/js/bootstrap.min.js"
            ]
```
Para no agrega Styles en mi componente: "ng g c heroes -is" se agrega la palabra "-is"


_REGEX_ 
=======

|     Sintaxis  	|     REGEX     				  |   	
| ---------------	| -------------------------			  |
|n(1..2,2..3)     	| ^[0-9]{1,2}(\.[0-9]{2,3})?$ 			  |
|2.1 ó 2.0        	| ^2\.(0|1)$					  |
|letra,numero,-,_     	| ^[a-z0-9_-]{3,16}$				  |
|correo           	| ^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$ |
|correo2		|^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$	  |

_WINDOW_ 
=======
##### Matar procesos #####
	
- Taskkill /IM <Nombre de imagen> /F
- Taskkill /PID <Numero> /F
	
	
taskkill .exe /f /fi "proceso que no responde"
taskkill .exe /f /fi "proceso que no responde"
##### usando taskill
- taskkill .exe /f /fi "proceso que no responde" 
- crear un  .bat :
@echo off
 taskkill .exe /f /fi "proceso que no responde" 
exit
###### publicando proyecto SpringBoot
- .\mvnw.cmd clean package
- java -jar .\target\spring-boot-backend-apirest-0.0.1-SNAPSHOT.jar
##### publicando proyecto Angular
- ng build --prod
##### publicando Apache Server Lounge
- https://www.apachelounge.com/download/  por defecto se guarda en: "c:/Apache24"
- en el index.html => editar = >  <base href="/app-clientes/">
- Editar el archivo: httpd.conf  => C:\Apache24\conf
- En el httpd.conf, Habilitar  => LoadModule rewrite_module modules/mod_rewrite.so
- modificar el archivo que crearemos .htaccess y pegamos: 
```properties
DocumentRoot "${SRVROOT}/htdocs"
<Directory "${SRVROOT}/htdocs">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```
- Copiar la carpeta "DIST" genera en angular, y pegar en => C:\Apache24\htdocs  => con el nombre "clientes-app"
- Abrir CMD en => C:\Apache24\bin y escribir el comando .\httpd.exe
##### publicando con Node Express
- en el index.html => editar = >  <base href="/"> y eliminar el archivo 
- en el CMD => D:\software\udemy\spring5\angular\clientes-app\dist => ejecutamos => npm init 
- entry point: (index.js) server.js
- en el CMD => D:\software\udemy\spring5\angular\clientes-app\dist => ejecutamos =>  npm install express --save
- se generar archivos package y modificar en => D:\software\udemy\spring5\angular\clientes-app\dist: 
```javascript
{
  "name": "clientes-app",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```
- crear el archivo =D:\software\udemy\spring5\angular\clientes-app\dist\server.js y agregar: 
```javascript
let express = require('express');
let path=require('path');
let app = express();
let port = 8089;

app.use(express.static('clientes-app'));


app.get('*',(req,res,next)=>{
	res.sendFile(path.resolve('clientes-app/index.html'));
});

app.listen(port,()=>{
	console.log('El servidor express se ha iniciado en el puerto'+port);
});
```
-  en D:\software\udemy\spring5\angular\clientes-app\dist> => ejecutar = > node .\server.js

##### publicando en HEROKU
- el archivo import.sql, debe estar en UTF-8
- modificar properties: 
```properties
server.port=${PORT:8080}
```
- abrir CMD y escribir ("spring-boot2-heroku-test2" = nombre del proyecto):
```bat
heroku login
git init
heroku git:remote -a spring-boot2-heroku-test2
heroku plugins:install java
heroku addons:create jawsdb
heroku config:get JAWSDB_URL
```
#copiar la linea que se genera ejemplo: 
mysql://xudqiziahxblm43o:tzcj7aaa7a5w1e80@jw0ch9vofhcajqg7.cbetxkdyhwsb.us-east-1.rds.amazonaws.com:3306/p702bbcywh1sqeum
#luego cambiar el url,username,password con la cadena generada: 
```properties
spring.datasource.url=jdbc:mysql://jw0ch9vofhcajqg7.cbetxkdyhwsb.us-east-1.rds.amazonaws.com:3306/p702bbcywh1sqeum?useSSL=false
spring.datasource.username=xudqiziahxblm43o
spring.datasource.password=tzcj7aaa7a5w1e80
```
```bat
.\mvnw clean package
heroku jar:deploy .\target\spring-boot-backend-apirest-0.0.1-SNAPSHOT.jar
# para revisar log de despliegue
heroku logs --tail
```
##### publicando angular en FIREBASE
- crear config.ts en => D:\software\udemy\spring5\angular\clientes-app\src\app\config\config.ts
- modificar cliente.service.ts en => D:\software\udemy\spring5\angular\clientes-app\src\app\clientes\cliente.service.ts
```ts
// D:\software\udemy\spring5\angular\clientes-app\src\app\config\config.ts
	export const URL_BACKEND='https://spring-boot2-heroku-test2.herokuapp.com';

// D:\software\udemy\spring5\angular\clientes-app\src\app\clientes\cliente.service.ts
import {URL_BACKEND} from '../config/config';
	export class ClienteService {
  	private urlEndPoint: string = URL_BACKEND+'/api/clientes';
  	}
	
 // D:\software\udemy\spring5\angular\clientes-app\src\app\facturas\services\factura.service.ts
 import { URL_BACKEND } from '../../config/config';
 	export class FacturaService {
	private urlEndPoint:string=URL_BACKEND+'/api/facturas';
	}
	
// D:\software\udemy\spring5\angular\clientes-app\src\app\usuarios\auth.service.ts
import { URL_BACKEND} from '../config/config';
	export class AuthService {
  	login(usuario: Usuario): Observable<any> {
    	const urlEndpoint = URL_BACKEND+'/oauth/token';
    		}	
    	}
	
// D:\software\udemy\spring5\angular\clientes-app\src\app\clientes\clientes.component.ts
import { URL_BACKEND } from '../config/config';
	export class ClientesComponent implements OnInit {
  	urlBackend:string=URL_BACKEND;
	}
	
// D:\software\udemy\spring5\angular\clientes-app\src\app\clientes\clientes.component.html	
<!-- src="http://localhost:8080/api/uploads/img/{{cliente.foto}}" alt="{{cliente.foto}}" class="img-thumbnail rounded" -->
src="{{urlBackend}}/api/uploads/img/{{cliente.foto}}" alt="{{cliente.foto}}" class="img-thumbnail rounded"

<!-- src="http://localhost:8080/images/no-usuario.png" alt="Sin Foto" class="img-thumbnail rounded" -->
src="{{urlBackend}}/images/no-usuario.png" alt="Sin Foto" class="img-thumbnail rounded"

```cmd
ng build --prod
# tener la carpeta generada DIST => PUBLIC (todo contenido)
# ubicarse dentro de la carpeta DIST. 
npm install -g firebase-tools
firebase login
firebase init
#selecionamos con la FLECHA del teclado hacia abajo:  
# (*) Hosting: Configure and deploy Firebase Hosting sites
# que no sebreescriban nuestro index.html si no remplaarlo manualmente, si en caso nos omita ese paso. 
# creamos proyecto en https://console.firebase.google.com 
firebase use --add
# seleccionamos el proyecto creado en https://console.firebase.google.com/project/clientes-app-angular-test/overview
# escribmos un alias: clientes-app
firebase deploy
LOG: 
```cmd

   1 Set-Location -literalPath 'D:\software\udemy\spring5\angular\clientes-app'
   2 npm install -g firebase-tools
   3 firebase login
   4 cd .\dist\
   5 dir
   6 firebase init
   7 firebase use --add
   8 firebase deploy
```

```bat
PS D:\software\udemy\spring5\angular\clientes-app> npm install -g firebase-tools
C:\Users\dperez\AppData\Roaming\npm\firebase -> C:\Users\dperez\AppData\Roaming\npm\node_modules\firebase-tools\lib\bin\firebase.js
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\firebase-tools\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

+ firebase-tools@6.11.0
updated 1 package in 147.797s
PS D:\software\udemy\spring5\angular\clientes-app> firebase login
? Allow Firebase to collect anonymous CLI usage and error reporting information? Yes

Visit this URL on any device to log in:
https://accounts.google.com/o/oauth2/auth?client_id=563584335869-fgrhgmd47bqnekij5i8b5pr03ho849e6.apps.googleusercontent.com&scope=email%20openid%20https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcloudplatformprojects.readonly%20https%3A%2F%2Fwww.googleapis.com%2Fauth%2Ffirebase%20https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcloud-platform&response_type=code&state=305737577&redirect_uri=http%3A%2F%2Flocalhost%3A9005

Waiting for authentication...

+  Success! Logged in as dperezg2017@gmail.com
PS D:\software\udemy\spring5\angular\clientes-app> cd .\dist\
PS D:\software\udemy\spring5\angular\clientes-app\dist> dir


    Directorio: D:\software\udemy\spring5\angular\clientes-app\dist


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        5/06/2019     00:31                node_modules
d-----        5/06/2019     21:47                public


PS D:\software\udemy\spring5\angular\clientes-app\dist> firebase init

     ######## #### ########  ######## ########     ###     ######  ########
     ##        ##  ##     ## ##       ##     ##  ##   ##  ##       ##
     ######    ##  ########  ######   ########  #########  ######  ######
     ##        ##  ##    ##  ##       ##     ## ##     ##       ## ##
     ##       #### ##     ## ######## ########  ##     ##  ######  ########

You're about to initialize a Firebase project in this directory:

  D:\software\udemy\spring5\angular\clientes-app\dist

? Are you ready to proceed? Yes
? Which Firebase CLI features do you want to set up for this folder? Press Space to select features, then Enter to conf
irm your choices. Hosting: Configure and deploy Firebase Hosting sites

=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add,
but for now we'll just set up a default project.

? Select a default Firebase project for this directory: [create a new project]

=== Hosting Setup

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? public
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
+  Wrote public/index.html

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...
i  Writing gitignore file to .gitignore...

+  Firebase initialization complete!

Project creation is only available from the Firebase Console
Please visit https://console.firebase.google.com to create a new project, then run firebase use --add
PS D:\software\udemy\spring5\angular\clientes-app\dist> firebase use --add
? Which project do you want to add? clientes-app-angular-7d250
? What alias do you want to use for this project? (e.g. staging) clientes-app

Created alias clientes-app for clientes-app-angular-7d250.
Now using alias clientes-app (clientes-app-angular-7d250)
PS D:\software\udemy\spring5\angular\clientes-app\dist> firebase deploy

=== Deploying to 'clientes-app-angular-7d250'...

i  deploying hosting
i  hosting[clientes-app-angular-7d250]: beginning deploy...
i  hosting[clientes-app-angular-7d250]: found 13 files in public
+  hosting[clientes-app-angular-7d250]: file upload complete
i  hosting[clientes-app-angular-7d250]: finalizing version...
+  hosting[clientes-app-angular-7d250]: version finalized
i  hosting[clientes-app-angular-7d250]: releasing new version...
+  hosting[clientes-app-angular-7d250]: release complete

+  Deploy complete!

Project Console: https://console.firebase.google.com/project/clientes-app-angular-7d250/overview
Hosting URL: https://clientes-app-angular-7d250.firebaseapp.com
```
_CONSOLE NAVEGADOR_ 
===================
```javascript
https://jwt.io/
let token ="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkRleXZpenogUGVyZXoiLCJpYXQiOjE1MTYyMzkwMjJ9.Gx5C4R0if1YBcY1jmH_EXM1uINHvl20_6nzQ9_EVypQ"
let payload = token.split(".")[1]
window.atob(payload) // decode base64
JSON.parse(window.atob(payload)) // parsear a obj JSON
```
##### Observaciones
