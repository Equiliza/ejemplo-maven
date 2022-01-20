# Getting Started

## Windows

### Compile Code
### Test Code
### Jar Code
* gradle build

### Run Jar
* Local:      gradle bootRun
* Background: nohup bash mvnw.cmd spring-boot:run &

### Testing Application
* Abrir navegador: http://localhost:8081/rest/mscovid/test?msg=testing

## Linux

### Compile Code
### Test Code
### Jar Code
* gradle build

### Run Jar
* Local:      gradle bootRun
* Background: nohup bash mvnw spring-boot:run &

### Testing Application
* curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'
