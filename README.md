# Sentiment Analysis Project

This project is a sentiment analysis application that processes news articles or other text-based data sources using a reactive architecture.

## Technologies Used

### Backend & Processing

- **Java 11**: The core programming language.
- **Spring Boot 2.6.3**: Framework for building stand-alone, production-grade Spring based Applications.
  - `spring-boot-starter-webflux`: Used for building reactive web applications, handling asynchronous data streams.
- **Project Reactor**: A reactive library for building non-blocking applications on the JVM.
- **Stanford CoreNLP 3.8.0**: A suite of natural language analysis tools. This is central to the project's sentiment analysis capabilities. It processes text data (e.g., news articles) to determine the sentiment expressed (positive, negative, neutral) by leveraging techniques like tokenization, part-of-speech tagging, parsing, and sentiment scoring.

### Data Streaming & Potential Storage (Apache Kafka)

- **Apache Kafka**: A distributed streaming platform used for building real-time data pipelines and streaming apps. In this project, it likely serves the following purposes:
  - **Ingesting Data Streams**: Receiving data, such as news articles from an external source.
  - **Message Queuing**: Decoupling data producers from consumers (e.g., sentiment analysis module).
  - **Data Persistence**: Kafka topics can store messages for a configurable period, acting as a durable log for the incoming data before or after sentiment analysis.
  - `confluentinc/cp-kafka:latest` (Docker Image): Used to run the Kafka brokers.
  - `confluentinc/cp-zookeeper:latest` (Docker Image): Zookeeper is used by Kafka for distributed coordination.
  - `reactor-kafka 1.3.10`: Provides reactive APIs for Kafka, enabling non-blocking message consumption and production, fitting the reactive nature of the application.
  - `spring-kafka`: Provides Spring integration with Apache Kafka, simplifying configuration and interaction.

### Build & Dependency Management

- **Apache Maven**: Used as the build automation and dependency management tool.

### Infrastructure (via Docker Compose)

- **Docker**: The project uses Docker Compose (`docker-compose.yml`) to define and run multi-container Docker applications.
  - **Zookeeper Service**: Manages the Kafka brokers. It runs on port `2181`.
  - **Kafka Service**: The message broker. It depends on Zookeeper and is accessible on port `9092`.

## Setup and Installation

1.  Ensure you have Java 11 and Apache Maven installed.
2.  Ensure you have Docker and Docker Compose installed.
3.  Clone the repository.
4.  The necessary Java dependencies will be downloaded by Maven.
5.  The Kafka and Zookeeper services can be started using Docker Compose.

## How to Run

1.  **Start Infrastructure**:
    Navigate to the project root directory (where `docker-compose.yml` is located) and run:
    ```bash
    docker-compose up -d
    ```
2.  **Build and Run the Application**:
    Navigate to the project root directory (where `pom.xml` is located) and run:
    ```bash
    mvn spring-boot:run
    ```
    (Further details on specific application endpoints or functionalities would need to be inferred from the source code.)

## Acknowledgments

This project was developed as part of the Hands-On Programming course by Niv Itzhaki. Through this experience, I had the opportunity to explore many amazing technologies and gain practical knowledge in backend development, security, testing, and DevOps. Huge thanks to Niv Itzhaki for the guidance and support throughout the course!
