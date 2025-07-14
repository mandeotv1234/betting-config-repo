# Betting Microservices Configuration Repository

This repository contains Spring Cloud Config Server configuration files for the betting microservices application.

## Services Configuration

### Service Ports
- **API Gateway**: 8080
- **User Service**: 8081
- **Wallet Service**: 8082
- **Betting Service**: 8083
- **Odds Service**: 8084
- **Match Service**: 8085
- **Notification Service**: 8086
- **Discovery Server**: 8761

### Database Configuration
All services use PostgreSQL with separate databases:
- `userdb` - User Service
- `walletdb` - Wallet Service
- `bettingdb` - Betting Service
- `oddsdb` - Odds Service
- `matchdb` - Match Service
- `notificationdb` - Notification Service

### Dependencies
- **PostgreSQL**: Database server
- **Redis**: Caching for Odds Service
- **Kafka**: Message broker for Notification Service
- **Eureka**: Service discovery

## Configuration Files

1. **user-service.yml** - User management service configuration
2. **wallet-service.yml** - Wallet and payment service configuration
3. **betting-service.yml** - Betting logic service configuration
4. **odds-service.yml** - Odds calculation service configuration with Redis caching
5. **match-service.yml** - Match data service configuration
6. **notification-service.yml** - Notification service with Kafka integration
7. **discovery-server.yml** - Eureka service discovery configuration
8. **api-gateway.yml** - Spring Cloud Gateway configuration with routing

## Environment Variables

Some services require environment variables:

### Notification Service
- `EMAIL_USERNAME` - SMTP email username
- `EMAIL_PASSWORD` - SMTP email password
- `SMS_ACCOUNT_SID` - Twilio account SID
- `SMS_AUTH_TOKEN` - Twilio auth token

## Usage with Spring Cloud Config Server

To use this configuration repository with Spring Cloud Config Server, configure your config server to point to this Git repository:

```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/your-org/betting-config-repo
          default-label: main
```

Each microservice should include the following configuration to connect to the config server:

```yaml
spring:
  cloud:
    config:
      uri: http://config-server:8888
```
