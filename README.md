# Spring Harness Demo with Buck2

This project demonstrates a Spring Boot application built with Buck2, featuring:
- **Spring Boot** as the application framework
- **Buck2** for fast, incremental builds
- **Container** support for deployment
- **Melange** for build environment configuration

## Project Structure

```
.
├── java-app/                    # Java Spring Boot application
│   ├── src/                    # Source code
│   │   ├── main/java/com/example/demo/
│   │   │   └── DemoApplication.java  # Main application
│   │   └── test/java/com/example/demo/
│   │       └── DemoApplicationTests.java  # Tests
│   └── BUCK                    # Buck2 build configuration
├── melange/                    # Melange configuration
│   ├── melange.yaml            # Build environment configuration
│   └── BUCK                    # Buck2 rules for Melange
├── image/                      # Container image configuration
│   └── BUCK                    # Buck2 rules for container image
├── BUCK                        # Root Buck2 configuration
└── README.md                   # This file
```

## Prerequisites

- Java 21 (as specified in the build configuration)
- Buck2 (for building)
- Docker (for container image building)

## Development Setup

1. **Install Buck2** (if not already installed):
   ```bash
   curl -fsSL https://raw.githubusercontent.com/facebook/buck2/main/install.sh | bash
   ```

2. **Build the application**:
   ```bash
   buck2 build //:spring-harness-demo
   ```

3. **Run the application**:
   ```bash
   buck2 run //:spring-harness-demo
   ```

4. **Run tests**:
   ```bash
   buck2 test //...
   ```

5. **Build the container image**:
   ```bash
   buck2 build //image:spring-harness-demo-image
   ```

## Build Configuration

The project uses Buck2 for fast, incremental builds with the following features:

- **Incremental Compilation**: Only recompiles changed files
- **Dependency Management**: Uses Maven dependencies directly
- **Container Support**: Easy container image building
- **Test Integration**: Runs tests with proper dependencies

### Key Features

- **Fast Builds**: Buck2's powerful caching system ensures minimal rebuilds
- **Reproducible Builds**: Consistent build environments with Melange
- **Container-First**: Native support for building container images
- **Scalable**: Efficiently handles large codebases

## Container Image

The project includes a container image configuration that packages the application with a minimal JRE:

- Based on `eclipse-temurin:21-jre-jammy`
- Minimal footprint
- Optimized for production use

To build the container image:
```bash
buck2 build //image:spring-harness-demo-image
```

## Feedback

*Feedback from review will be added here.*

## License

This project is unlicensed. All rights are reserved by the author. Viewing the source code does not grant any rights to use, modify, or distribute the code.

added webhook now added it to pipeline