<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
</head>
<body>
    <h1>Basic CRUD with GraphQL in Spring Boot</h1>
    <h2>Project Overview</h2>
    <p>This project is a simple GraphQL-based CRUD application built with Spring Boot. It demonstrates how to create, read, update, and delete entities through a GraphQL API.</p>
    <h2>Technologies Used</h2>
    <ul>
        <li>Java 17</li>
        <li>Spring Boot</li>
        <li>GraphQL (graphql-java)</li>
        <li>JPA (Java Persistence API)</li>
        <li>H2 Database (in-memory)</li>
    </ul>
    <h2>Setup Instructions</h2>
    <ol>
        <li>Ensure Java 17 and Maven are installed on your machine.</li>
        <li>Clone the repository:</li>
        <pre><code>git clone https://github.com/your-repo/your-project.git</code></pre>
        <li>Navigate to the project directory:</li>
        <pre><code>cd your-project</code></pre>
        <li>Build and run the application:</li>
        <pre><code>mvn spring-boot:run</code></pre>
    </ol>
    <h2>Endpoints</h2>
    <p>The GraphQL endpoint is available at:</p>
    <pre><code>http://localhost:8080/graphql</code></pre>
    <h2>GraphQL Queries and Mutations</h2>
    <h3>Queries</h3>
    <ul>
        <li><strong>Get all entities:</strong></li>
        <pre><code>{
  allEntities {
    id
    name
    description
  }
}</code></pre>
        <li><strong>Get a single entity by ID:</strong></li>
        <pre><code>{
  entityById(id: 1) {
    id
    name
    description
  }
}</code></pre>
    </ul>
    <h3>Mutations</h3>
    <ul>
        <li><strong>Create a new entity:</strong></li>
        <pre><code>mutation {
  createEntity(input: { name: "New Entity", description: "Description" }) {
    id
    name
    description
  }
}</code></pre>
        <li><strong>Update an entity:</strong></li>
        <pre><code>mutation {
  updateEntity(id: 1, input: { name: "Updated Name", description: "Updated Description" }) {
    id
    name
    description
  }
}</code></pre>
        <li><strong>Delete an entity:</strong></li>
        <pre><code>mutation {
  deleteEntity(id: 1) {
    id
    name
  }
}</code></pre>
    </ul>
    <h2>Database Configuration</h2>
    <p>This project uses an in-memory H2 database for easy setup. To access the H2 Console:</p>
    <pre><code>http://localhost:8080/h2-console</code></pre>
    <p>Use the following credentials:</p>
    <ul>
        <li><strong>JDBC URL:</strong> <code>jdbc:h2:mem:testdb</code></li>
        <li><strong>Username:</strong> <code>sa</code></li>
        <li><strong>Password:</strong> (leave blank)</li>
    </ul>
    <h2>Project Structure</h2>
    <pre>
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com.example.graphqlcrud
│   │   │       ├── model       # Entity classes
│   │   │       ├── repository  # JPA Repositories
│   │   │       ├── resolver    # GraphQL Resolvers
│   │   │       └── service     # Business Logic
│   │   └── resources
│   │       ├── application.properties
│   │       └── schema.graphqls  # GraphQL schema definitions
    </pre>
    <h2>GraphQL Schema Example</h2>
    <p>The <code>schema.graphqls</code> file defines the GraphQL schema:</p>
    <pre><code>type Entity {
  id: ID!
  name: String!
  description: String
}

type Query {
  allEntities: [Entity]
  entityById(id: ID!): Entity
}

type Mutation {
  createEntity(input: EntityInput): Entity
  updateEntity(id: ID!, input: EntityInput): Entity
  deleteEntity(id: ID!): Entity
}

input EntityInput {
  name: String!
  description: String
}</code></pre>
    <h2>Testing</h2>
    <p>To run tests, use:</p>
    <pre><code>mvn test</code></pre>
    <p>This will execute unit tests defined in the project using JUnit and Mockito for testing business logic.</p>
    <h2>License</h2>
    <p>This project is open-source and available under the <strong>MIT License</strong>.</p>
    <h2>Contact</h2>
    <p>For any questions, contact <strong>Robert Paternina</strong> at <a href="mailto:paterninayolir@gmail.com">paterninayolir@gmail.com</a>.</p>
</body>
</html>
