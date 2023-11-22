# Registro de Microservicios

Este repositorio proporciona una guía paso a paso para el registro de microservicios utilizando Consul como servicio de descubrimiento y HAProxy como balanceador de carga.

## Pasos

#### 1. Iniciar Consul Agent

```bash
consul agent -dev -bind=192.168.192.1 -data-dir= .
```

Este comando inicia un agente Consul en modo de desarrollo, especificando la dirección IP de enlace y el directorio de datos.

#### 2. Instalar Dependencias

```bash
npm i express consul
```

Instala las dependencias necesarias, Express para crear microservicios y Consul para registrar y descubrir servicios.

#### 3. Crear Microservicios

Desarrolla tus microservicios utilizando Express y regístralos en Consul. Un ejemplo básico se encuentra en el directorio `microservicio`.

#### 4. Iniciar HAProxy con Configuración Personalizada

```bash
docker run -d --name my-running-haproxy -p 8080:80 -v $(pwd)/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg haproxy:lts-alpine
```

Inicia un contenedor de HAProxy con la configuración personalizada proporcionada en `haproxy.cfg`. Asegúrate de ajustar las rutas según tu configuración.

## Acceder a los Servicios

- Servicio Consul: [http://localhost:8500](http://localhost:8500)
- Microservicios registrados en Consul
- Balanceador de Carga HAProxy: [http://localhost:8080](http://localhost:8080)

¡Listo! Ahora puedes registrar y descubrir microservicios utilizando Consul y balancear la carga con HAProxy.