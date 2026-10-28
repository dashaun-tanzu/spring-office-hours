# October 28

## News:

- [This Week in Spring - October 27th, 2026](https://spring.io/blog/2026/10/27/this-week-in-spring-october-27th-2026)
- [Spring Office Hours Podcast: S5E27 - Hugging Face for Java Developers with Pratik Patel](https://spring.io/blog/2026/10/26/spring-office-hours-podcast-S5E27)
- [Spring AI 2.1.0-RC1 and 2.0.2 Available Now](https://spring.io/blog/2026/10/23/spring-ai-2-1-0-RC1-available-now)
- [Spring Boot 4.1.2 available now](https://spring.io/blog/2026/10/23/spring-boot-4-1-2-available-now)
- [Spring Boot 4.2.0-RC1 available now](https://spring.io/blog/2026/10/23/spring-boot-4-2-0-RC1-available-now)
- [Spring Cloud 2026.0.0-RC1 (aka Paddington) Has Been Released](https://spring.io/blog/2026/10/23/spring-cloud-2026-0-0-RC1-has-been-released)
- [A Bootiful Podcast: A Bootiful Podcast: Anton Arhipov on AI Development within JetBrains IDEs](https://spring.io/blog/2026/10/22/a-bootiful-podcast-anton-arhipov)
- [This Week in Spring - October 20th, 2026 ](https://spring.io/blog/2026/10/20/this-week-in-spring-october-20th-2026)

## Releases coming soon:

- Spring Cloud Circuitbreaker 5.1.0-RC2 (Nov 5)
- Spring Cloud Zookeeper 5.1.0-RC2 (Nov 5)
- Spring Cloud Stream 5.1.0-RC2 (Nov 5)
- Spring Cloud Openfeign 5.1.0-RC2 (Nov 5)
- Spring Cloud Task 5.1.0-RC2 (Nov 5)
- Spring Cloud Consul 5.1.0-RC2 (Nov 5)
- Spring Cloud Commons 5.1.0-RC2 (Nov 5)
- Spring Cloud Config 5.1.0-RC2 (Nov 5)
- Spring Cloud Release 2026.0.0-RC2 (Nov 5)
- Spring Cloud Kubernetes 5.1.0-RC2 (Nov 5)
- Spring Cloud Gateway 5.1.0-RC2 (Nov 5)
- Spring Cloud Vault 5.1.0-RC2 (Nov 5)
- Spring Cloud Build 5.1.0-RC2 (Nov 5)
- Spring Cloud Netflix 5.1.0-RC2 (Nov 5)
- Spring Cloud Function 5.1.0-RC2 (Nov 5)
- Spring Boot 4.2.0-RC2 (Nov 5)
- Spring Framework 7.1.0-RC2 (Nov 5)

## YouTube:

- [Java Ships Built-In JSON (JDK 28)](https://www.youtube.com/watch?v=kdqJD94Cpos) - Dan Vega
- [Spring Office Hours: S5E27 - Hugging Face for Java Developers with Pratik Patel](https://www.youtube.com/watch?v=7eQ3eXEI-co) - SpringSourceDev
- [S5E26: dev2Next, Native JSON and a Week of New Models](https://www.youtube.com/watch?v=Oa3w-NkHfZg) - SpringSourceDev
- [Mise: easy setup for your projects and platforms](https://www.youtube.com/watch?v=xaJJH1omWhc) - Coffee + Software
- [TrueSource, by Broadcom, because getting to production is hard enough](https://www.youtube.com/watch?v=nj2KoEa2gIs) - SpringSourceDev
- [TrueSource by Broadcom](https://www.youtube.com/watch?v=fEQxKVE-YM0) - SpringSourceDev
- [Why You Can't Aftermarket Innovation](https://www.youtube.com/watch?v=eyDmq-ytNRA) - SpringSourceDev
- [Spring Office Hours: S5E25 - Future of Software Development with Josh Long](https://www.youtube.com/watch?v=NQK6gdbCWDQ) - SpringSourceDev
- [Spring Office Hours: S5E25 - Future of Software Development with Josh Long 📱](https://www.youtube.com/watch?v=ADtVqEAKdeM) - SpringSourceDev

## Demos:

- [saa-patch-2-6-trivy-demo](https://github.com/dashaun-tanzu/saa-patch-2-6-trivy-demo) - Spring Application Advisor: upgrade Spring Boot 2.6 to 4.1, then patch every dependency to its latest patch release. CVE counts from Trivy scanning the advisor CycloneDX SBOM.
- [gemfire-data-ingest-demo](https://github.com/dashaun-tanzu/gemfire-data-ingest-demo) - Demonstrate Postgres vs Gemfire, writing and reading, a simple dataset, with zero optimizations.
- [advisor-pin-unpin-demo](https://github.com/dashaun-tanzu/advisor-pin-unpin-demo) - Handling the dependency tree calculus.
- [advisor-pin-unpin-petclinic-demo](https://github.com/dashaun-tanzu/advisor-pin-unpin-petclinic-demo) - Demo repository
- [vuln-chain-3-4-14-demo](https://github.com/dashaun-tanzu/vuln-chain-3-4-14-demo) - **vulnerability chaining**: a container image that scans **clean in Trivy (zero HIGH/CRITICAL)** is still exploitable, because an attacker chains one *medium*-severity Spring CVE with a benign-looking *container* misconfiguration.
- [saa-cves-2-6-trivy-demo](https://github.com/dashaun-tanzu/saa-cves-2-6-trivy-demo) - Application Advisor Demo with Trivy
- [saa-cves-1-5-demo](https://github.com/dashaun-tanzu/saa-cves-1-5-demo) - Advisor demo from Spring Boot 1.5, OWASP dependency check for CVEs
- [saa-hello-world-1-5-demo](https://github.com/dashaun-tanzu/saa-hello-world-1-5-demo) - Spring Application Advisor Upgrade Example from Spring Boot 1.5
- [saa-petclinic-squashed-demo](https://github.com/dashaun-tanzu/saa-petclinic-squashed-demo) - Advisor upgrading Spring Pet Clinic from Spring Boot 2.7.3 using --squash, showing startup time and memory improvements
- [saa-hello-world-2-6-demo](https://github.com/dashaun-tanzu/saa-hello-world-2-6-demo) - Demonstrating advisor --squash feature, builds native image
- [saa-concourse-pipelines-demo](https://github.com/dashaun-tanzu/saa-concourse-pipelines-demo) - Self-hosted Concourse demo that discovers Java/Spring Boot repos across GitHub orgs and GitLab groups, runs Spring Application Advisor against each, and opens upgrade pull/merge requests. Includes a local Nexus proxy for Spring Enterprise artifacts. Works on macOS and Linux.
- [saa-petclinic-demo](https://github.com/dashaun-tanzu/saa-petclinic-demo) - Spring Application Advisor upgrading Spring PetClinic, from Java 8 and Spring Boot 2.7, step-by-step to the latest version of Spring Boot with a modern version of Java

