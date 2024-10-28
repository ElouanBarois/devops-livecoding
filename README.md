# devops-livecoding

base for GitHub Actions

## 2-1 What are testcontainers?

Testcontainers is a library that allows developers to run Docker containers within their test code, creating isolated environments for integration testing. It provides easy setup of databases, web servers, and other dependencies, ensuring consistent and reproducible tests across different environments.

## 2-2 Document your github actions configuration 

### Trigger Conditions

The workflow is configured to run under the following conditions:

- **On Push**: Executes on pushes to the `main` and `develop` branches.
- **On Pull Request**: Runs automatically when a pull request is created, ensuring code changes are tested before merging.

### Job Details: `test-backend`

The `test-backend` job carries out the essential steps for building and testing the Java application.

- **Runs-on**: `ubuntu-22.04` - Specifies the OS environment for running the job, ensuring a consistent Linux-based platform.

#### Steps Explained

1. **Checkout Repository**:
    - **Action Used**: `actions/checkout@v2.5.0`
    - **Purpose**: Checks out the repository code, making it available for subsequent steps in the workflow.

2. **Set up JDK 17**:
    - **Action Used**: `actions/setup-java@v3`
    - **Purpose**: Installs and configures JDK 17 (Amazon Corretto distribution) as the Java environment.
    - **Parameters**:
        - `distribution`: Specifies the JDK distribution, here set to `'corretto'`.
        - `java-version`: Specifies the version, here set to `'17'`.

3. **Build and Test with Maven**:
    - **Command**: `mvn clean install`
    - **Purpose**: Runs Maven to build the project and execute tests. The `mvn clean install` command first cleans any previous builds and then builds the project and runs tests.
    - **Working Directory**: `simple-api` - Ensures Maven commands are run in the specified project directory (`simple-api`).

## For what purpose do we need to push docker images?

Pushing Docker images allows you to upload your locally built images to a remote repository, such as Docker Hub or a private registry, making them accessible for deployment across different environments or by other team members. This practice ensures version control, easy distribution, and scalability of applications within containerized environments.