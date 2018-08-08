# Config Server Sample
## A Sample Spring Boot Configuration Server 

### Build & Run

```
./gradlew bootRun
```

### Source configuration

This sample project uses the file based storage (Filesystem). Other options exist, namely:
- Git
- Vault
- JDBC
- Composite

The file paths for this sample project can be configured in src/main/resources/application.yml

### Query configuration

Spring Boot Config Server support output in a number of formats, regardless of source format.
Do get the output in a format of your choice, you simply change the file extension of the requested resource.

```
curl http://localhost:8888/service-qa.properties
curl http://localhost:8888/service-qa.yaml
curl http://localhost:8888/service-qa.json
```

### Properties inheritance

You can see the way Config Server handles inheritance and overrides when querying

```
curl http://localhost:8888/service-development.json
```

The global variable ```global.settings.some-setting``` is inherited from the global definition in
src/main/resources/service/service.yml

The variables ```token``` and ```shop.location``` are added in the the service's defintion in the 
development profile declared in src/main/resources/service/development/service.yml

Querying the service with production or qa profile, you can see that ```shop.name``` is 
overridden as the setting in the given profiles and the global values defined are available as well.

### Documentation

- https://spring.io/guides/gs/centralized-configuration/
- https://cloud.spring.io/spring-cloud-config/spring-cloud-config.html



