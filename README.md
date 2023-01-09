# RabbitMq Docker

{% code title="docker-compose.yml" overflow="wrap" %}
```yaml
version: "3.7"
services:
  rabbitmq:
    image: rabbitmq:3-management-alpine
	hostname: 'dev-rabbitmq'
    environment:
		- RABBITMQ_DEFAULT_USER=user
		- RABBITMQ_DEFAULT_PASS=password
    ports:
        - "5672:5672"
        - "15672:15672"
    volumes:
        - rabbitmq-data:/var/lib/rabbitmq/mnesia/
        - rabbitmq-logs:/var/log/rabbitmq/

volumes:
  rabbitmq-data:
  rabbitmq-logs:dock
```
{% endcode %}
