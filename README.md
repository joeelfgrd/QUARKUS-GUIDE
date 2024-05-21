# Guía para crear el proyecto maven con Quarkus
## Primero te situas en el cmd en donde quieras crear el proyecto.
### Utilizas el comando:
    quarkus create app org.acme:my-quarkus-app --extension=resteasy-reactive,jdbc-h2,hibernate-orm-panache,hibernate-validator
Esto creará un proyecto con las dependencias para h2

### Si quisieramos hacerlo con sql sería:
    quarkus create app org.acme:my-quarkus-app --extension=resteasy-reactive,jdbc-mysql,hibernate-orm-panache,hibernate-validator

## Ahora abres la carpeta que se ha creado con el nombre de my-quarkus-app y entras en el pom.xml
### Tienes que buscar la dependencia:
        <dependency>
            <groupId>io.quarkus</groupId>
            <artifactId>quarkus-resteasy-reactive</artifactId>
        </dependency>
### Y cambiarla por:
        <dependency>
            <groupId>io.quarkus</groupId>
            <artifactId>quarkus-resteasy-jackson</artifactId>
        </dependency>
### Esto seguirá dando un error pero se solucionará buscando la dependencia:
        <dependency>
            <groupId>io.quarkus</groupId>
            <artifactId>quarkus-rest</artifactId>
        </dependency>
### Y añadiendo al final la linea version que contiene la versión de quarkus que se está utilizando, en este caso 3.10.1:
        <dependency>
            <groupId>io.quarkus</groupId>
            <artifactId>quarkus-rest</artifactId>
            <version>3.10.1</version>
        </dependency>
## Despues de realizar estos cambios guardamos y nos saldrá este mensaje:
        A build file was modified. Do you want to synchronize the Java classpath/configuration?
## Le damos a yes,y veremos como ya no hay errores en el pom.xml