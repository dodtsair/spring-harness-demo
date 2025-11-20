# Spring Harness Demo

This project is a proof-of-concept (POC) demonstrating the integration of various development and CI/CD tools:
- **Spring Boot** as the application framework
- **Mise** for development environment management
- **Harness** for CI/CD pipeline
- **Melange** for creating a meta package that ensures all required build dependencies are available

## Project Structure

```
.
├── .harness/                    # Harness CI/CD pipeline configuration
│   ├── BuildProject/           
│   │   └── melange.yaml        # Melange configuration for build environment
│   └── pipeline.yaml           # Main Harness pipeline definition
├── src/                        # Source code directory
│   ├── main/
│   │   ├── java/com/example/demo/
│   │   │   └── DemoApplication.java  # Main Spring Boot application
│   │   └── resources/
│   │       └── application.properties
│   └── test/                   # Test files
├── build.gradle                # Gradle build configuration
└── README.md                   # This file
```

## Prerequisites

- Java 21 (as specified in build.gradle)
- Mise (for development environment management)
- Docker (for building container images)
- Access to Harness CI/CD platform

## Development Setup

1. **Install Mise** (if not already installed):
   ```bash
   curl -fsSL https://mise.jdx.dev/install.sh | sh
   ```

2. **Install project dependencies** using Mise:
   ```bash
   mise install
   ```

3. **Build the project**:
   ```bash
   ./gradlew build
   ```

4. **Run the application**:
   ```bash
   ./gradlew bootRun
   ```

## CI/CD Pipeline

The project includes a Harness CI pipeline (`.harness/pipeline.yaml`) that implements the following workflow:

1. **Checkout Code**: Clones the repository
2. **Compute Image Tag**: Determines the appropriate image tag based on git history
3. **Melange Integration**:
   - Detects Melange configuration
   - Uses Melange to create a metadata package that ensures all required system dependencies are installed
   - Ensures consistent build environments across different platforms
4. **Build Project**:
   - Uses the custom build environment
   - Runs tests
   - Builds the application JAR

### Key Features

- **Incremental Builds**: The pipeline is optimized to only rebuild images when necessary
- **Caching**: Leverages Docker layer caching for faster builds
- **Environment Management**: Uses Mise to ensure consistent development environments
- **Dependency Management**: Melange ensures all required system dependencies are available before building

## Build Environment

The project uses a custom build environment defined in Melange configuration (`.harness/BuildProject/melange.yaml`). This ensures that all build dependencies are explicitly declared and versioned.

### Included Tools

- Java 21
- Gradle
- Build dependencies specified in the project's build.gradle

## Feedback

*Feedback from review will be added here.*

## License

This project is unlicensed. All rights are reserved by the author. Viewing the source code does not grant any rights to use, modify, or distribute the code.

noop change