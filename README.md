# Sample Web Application - JFrog Artifactory Practice

A simple Java web application that builds a WAR file and deploys it to JFrog Artifactory using GitHub Actions.

## Project Structure

```
├── src/main/java/com/example/HelloServlet.java
├── src/main/webapp/
│   ├── index.html
│   └── WEB-INF/web.xml
├── pom.xml
└── .github/workflows/build-and-deploy.yml
```

## Prerequisites

- Java 11+
- Maven 3.6+
- JFrog Artifactory instance

## Build Locally

```bash
mvn clean package
```

The WAR file will be generated at `target/sample-webapp.war`.

## GitHub Actions Setup

Add the following secrets to your GitHub repository:

| Secret | Description |
|--------|-------------|
| `JF_URL` | Your JFrog Platform URL (e.g., `https://your-instance.jfrog.io`) |
| `JF_ACCESS_TOKEN` | JFrog access token with deploy permissions |

## How It Works

1. On push to `main`, the GitHub Actions workflow triggers.
2. It builds the WAR file using Maven.
3. Uses JFrog CLI to upload the WAR to Artifactory repository `libs-release-local`.
4. Publishes build info to JFrog for traceability.
