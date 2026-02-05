# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Netflix Eureka Server for service discovery in a microservices architecture. Part of the DFS (Daily Fantasy Sports) ecosystem.

- **Spring Boot:** 3.5.9
- **Spring Cloud:** 2025.0.0
- **Java:** 21+

## Build Commands

```bash
# Build the project
mvn clean package

# Run tests
mvn test

# Run a specific test class
mvn test -Dtest=DfsDiscoveryServerApplicationTests

# Start the server
java -jar target/dfs-discovery-server-0.0.1-SNAPSHOT.jar
```

## Architecture

This is a standalone Eureka server that other microservices register with for discovery. It runs on port 8761 and is configured to not register with itself (standalone mode, not clustered).

**Entry point:** `DfsDiscoveryServerApplication.java` - annotated with `@EnableEurekaServer`

**Configuration:** `application.properties` sets the server port and disables self-registration

## Specs Workflow

This project uses spec-driven development via `.specs/`. Use `/capture` to draft ideas, `/refine` to prepare specs, and `/implement` to build them. Completed implementations automatically open PRs.
