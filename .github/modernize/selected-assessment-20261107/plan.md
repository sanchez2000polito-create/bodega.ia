# Modernization Plan: Selected Assessment Categories

**Project**: cosmetics-api
**Assessment report**: report-20261107165036

## Technical Framework

- **Language**: Java 21
- **Framework**: Spring Boot 3.3.5; Spring Framework managed by Spring Boot
- **Build Tool**: Maven
- **Database**: PostgreSQL
- **Key Dependencies**: Spring Data JPA, PostgreSQL JDBC driver, Flyway

## Overview

This modernization addresses the selected findings in the existing assessment. It
updates the Java and Spring platform, prepares the persistence integration for
Azure Database for PostgreSQL with managed identity, and makes the Java
application container-ready. The work should be sequenced so the application
remains buildable as the runtime and framework are upgraded, while preserving
existing persistence behavior.

## Migration Impact Summary

| Application | Original Service | New Azure Service | Authentication | Comments |
|-------------|------------------|-------------------|----------------|----------|
| cosmetics-api | PostgreSQL | Azure Database for PostgreSQL | Managed Identity | Secure database access |
| cosmetics-api | Jakarta Persistence | Azure-ready persistence | N/A | Preserve JPA behavior |
| cosmetics-api | Java application | Container-ready application | N/A | Add container configuration |

## Selected Assessment Categories

- Category: "Database Migration (PostgreSQL)", Issues: [PostgreSQL database found], Solutions: [Secure Azure Database for PostgreSQL with Managed Identity [kbId: mi-postgresql]]
- Category: "Jakarta Migration (Jakarta Persistence)", Issues: [Detects usage of Jakarta Persistence (JPA) APIs], Solutions: [Migrate Jakarta JPA to Azure]
- Category: "Containerization", Issues: [No Dockerfile found], Solutions: [Containerize Java Application for Container Readiness [kbId: containerization-copilot-agent]]
- Category: "Java Version Upgrade", Issues: [Java Version is not the latest LTS], Solutions: [Upgrade Java Version [kbId: java-version-upgrade]]
- Category: "Framework Upgrade (Spring Boot)", Issues: [Spring Boot Version Has Reached the End of OSS Support], Solutions: [Upgrade Spring Boot Version [kbId: spring-boot-upgrade]]
- Category: "Framework Upgrade (Spring Framework)", Issues: [Spring Framework Version Has Reached the End of OSS Support], Solutions: [Upgrade Spring Framework Version [kbId: spring-framework-upgrade]]

## Scope and Sequencing

The selected scope comprises the Java, Spring Boot, and Spring Framework
upgrades; the Azure PostgreSQL and Jakarta Persistence changes; and container
readiness. The plan sequences platform and persistence changes before
containerization. The assessment used here is issue-only; no separate deployment
or integration-testing request was included.

A dependency-security/CVE review is included as a plan safeguard. No deployment
or infrastructure-provisioning task is included.

## Assumptions

- The upgrade targets follow the create-modernization-plan Java guidance:
  Java 25, Spring Boot 4.x, and Spring Framework 7.x.
- Azure Database for PostgreSQL managed identity is the intended database
  authentication approach, as specified by the selected solution.
- Azure resource provisioning and application deployment are outside this plan.

