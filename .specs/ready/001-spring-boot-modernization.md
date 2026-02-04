---
id: 001-spring-boot-modernization
title: Modernize Spring Boot and Java Dependencies
created: 2026-02-04
priority: medium
tags: [modernization, dependencies, spring-boot, java]
blocked-by: []
---

# Goal

Upgrade the discovery server to current LTS/stable versions of Java, Spring Boot, and Spring Cloud to benefit from security patches, performance improvements, and modern features.

## Current State
- Java 17
- Spring Boot 3.2.2
- Spring Cloud 2023.0.0

## Target State
- Java 21 LTS
- Spring Boot 3.5.x (latest stable: 3.5.9)
- Spring Cloud 2025.0 (Northfields) - compatible with Spring Boot 3.5.x

# Solution Approach

**Direct upgrade** - Jump from 3.2.2 directly to 3.5.x. This is appropriate because:
1. The project is simple (single `@EnableEurekaServer` annotation)
2. No complex custom configurations that might break
3. Spring Boot 3.2 → 3.5 is within the same major version (no Jakarta EE migration needed)

## Changes Required

### pom.xml updates
1. Update `<java.version>` from `17` to `21`
2. Update `spring-boot-starter-parent` version from `3.2.2` to `3.5.9`
3. Update `<spring-cloud.version>` from `2023.0.0` to `2025.0.0`
4. Update `<description>` from "Demo project for Spring Boot" to "Eureka discovery server for DFS microservices ecosystem"

### Verification
- Build must succeed: `mvn clean package`
- Tests must pass: `mvn test`
- Server must start and display Eureka dashboard at http://localhost:8761

## Out of Scope
- Virtual threads configuration (not beneficial for this low-concurrency discovery server)
- Clustering/high-availability setup
- Additional dependencies beyond what's currently in pom.xml

# Acceptance Criteria

- [ ] `pom.xml` updated with Java 21, Spring Boot 3.5.9, Spring Cloud 2025.0.0
- [ ] Project description updated to reflect DFS ecosystem purpose
- [ ] `mvn clean package` completes successfully
- [ ] `mvn test` passes (DfsDiscoveryServerApplicationTests)
- [ ] Application starts without errors
- [ ] Eureka dashboard accessible at http://localhost:8761
- [ ] CLAUDE.md updated to reflect new versions

# Notes

- Other DFS microservices are being modernized simultaneously, so no backward compatibility constraints
- Spring Cloud 2025.0 (Northfields) is the release train compatible with Spring Boot 3.5.x per [Spring Cloud compatibility matrix](https://github.com/spring-cloud/spring-cloud-release/wiki/Supported-Versions)
