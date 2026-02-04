---
id: 001-spring-boot-modernization
title: Modernize Spring Boot and Java Dependencies
created: 2026-02-04
priority: medium
tags: [modernization, dependencies, spring-boot, java]
---

# Idea

Modernize the discovery server repository to use current Java and Spring Boot versions, along with other dependency updates. This involves:

1. **Java Version Upgrade**: Currently using Java 17+, evaluate upgrading to Java 21 (LTS)
2. **Spring Boot Upgrade**: Currently on 3.2.2, research latest stable version
3. **Spring Cloud Upgrade**: Currently on 2023.0.0, identify compatible newer version
4. **Dependency Audit**: Review all dependencies for updates and security patches

Part of this task requires research to determine:
- What are the latest stable/LTS versions to target
- Compatibility between Spring Boot and Spring Cloud versions
- Breaking changes and migration considerations
- Best practices for modern Spring Boot project setup

## Notes

- This is a Netflix Eureka Server for the DFS (Daily Fantasy Sports) microservices ecosystem
- Standalone mode configuration (not clustered)
- Need to ensure backward compatibility with existing services that register with this discovery server
- Consider creating a migration checklist for systematic upgrade
