# Gateway
## Настройка gateway
Маршрутизация прописывается в application.yaml. Например:
```yaml
zuul:
  routes:
    registry-service:
      path: /registry/**
      serviceId: registry
    test-service:
      path: /test/**
      serviceId: test
```
* registry-service - название сервиса в конфиге
* path - маршрутизируемый путь
* serviceId - название сервиса (приложения)
## Настройка приложения
1. Необходимо добавить зависимость `org.springframework.cloud:spring-cloud-starter-netflix-eureka-client:2.2.2.RELEASE`
2. Добавить аннотацию `@EnableEurekaClient`
3. Указать имя приложения в application.yaml. Например:
```yaml
spring:
  application:
    name: registry 
```
4. Прописать URL для подключения к Eureka в application.yaml:
```yaml
eureka:
  client:
    service-url:
      default-zone: http://localhost:8761/eureka
```