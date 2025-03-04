# Event-Driven Microservices with Spring Boot and Kafka

## Architecture Overview
The system utilizes an event-driven microservices approach with **Apache Kafka** for asynchronous communication. The services interact as follows:

### Book Publisher Service
- **Functionality**:
  - Stores book details in its database.
  - Publishes events to the `book.published` Kafka topic when a new book is published.

### Book Persistence Service
- **Functionality**:
  - Subscribes to the `book.published` Kafka topic.
  - Stores book-related data in its database.
  - Publishes an event to the `notification.created` Kafka topic when data is persisted.

### Author Persistence Service
- **Functionality**:
  - Subscribes to the `book.published` Kafka topic.
  - Stores author-related data in its database.
  - Publishes an event to the `notification.created` Kafka topic when data is persisted.

### Notification Service
- **Functionality**:
  - Subscribes to the `notification.created` Kafka topic.
  - Stores notifications in its database and processes them accordingly.
