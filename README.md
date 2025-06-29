# SoPra RESTful Service Template FS25

## Getting started with Spring Boot
-   Documentation: https://docs.spring.io/spring-boot/docs/current/reference/html/index.html
-   Guides: http://spring.io/guides
    -   Building a RESTful Web Service: http://spring.io/guides/gs/rest-service/
    -   Building REST services with Spring: https://spring.io/guides/tutorials/rest/

### IntelliJ
If you consider to use IntelliJ as your IDE of choice, you can make use of your free educational license [here](https://www.jetbrains.com/community/education/#students).
1. File -> Open... -> SoPra server template
2. Accept to import the project as a `gradle project`
3. To build right click the `build.gradle` file and choose `Run Build`

### VS Code
The following extensions can help you get started more easily:
-   `vmware.vscode-spring-boot`
-   `vscjava.vscode-spring-initializr`
-   `vscjava.vscode-spring-boot-dashboard`
-   `vscjava.vscode-java-pack`

**Note:** You'll need to build the project first with Gradle, just click on the `build` command in the _Gradle Tasks_ extension. Then check the _Spring Boot Dashboard_ extension if it already shows `soprafs24` and hit the play button to start the server. If it doesn't show up, restart VS Code and check again.

## Building with Gradle
You can use the local Gradle Wrapper to build the application.
-   macOS: `./gradlew`
-   Linux: `./gradlew`
-   Windows: `./gradlew.bat`

More Information about [Gradle Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html) and [Gradle](https://gradle.org/docs/).

### Build

```bash
./gradlew build
```

### Run

```bash
./gradlew bootRun
```

You can verify that the server is running by visiting `localhost:8080` in your browser.

### Test

```bash
./gradlew test
```

### Development Mode
You can start the backend in development mode, this will automatically trigger a new build and reload the application
once the content of a file has been changed.

Start two terminal windows and run:

`./gradlew build --continuous`

and in the other one:

`./gradlew bootRun`

If you want to avoid running all tests with every change, use the following command instead:

`./gradlew build --continuous -xtest`

## API Endpoint Testing with Postman
We recommend using [Postman](https://www.getpostman.com) to test your API Endpoints.

## Debugging
If something is not working and/or you don't know what is going on. We recommend using a debugger and step-through the process step-by-step.

To configure a debugger for SpringBoot's Tomcat servlet (i.e. the process you start with `./gradlew bootRun` command), do the following:

1. Open Tab: **Run**/Edit Configurations
2. Add a new Remote Configuration and name it properly
3. Start the Server in Debug mode: `./gradlew bootRun --debug-jvm`
4. Press `Shift + F9` or the use **Run**/Debug "Name of your task"
5. Set breakpoints in the application where you need it
6. Step through the process one step at a time

## Testing
Have a look here: https://www.baeldung.com/spring-boot-testing

<br>
<br>
<br>

## Docker

### Introduction
This year, for the first time, Docker will be used to ease the process of deployment.\
Docker is a tool that uses containers as isolated environments, ensuring that the application runs consistently and uniformly across different devices.\
Everything in this repository is already set up to minimize your effort for deployment.\
All changes to the main branch will automatically be pushed to dockerhub and optimized for production.

### Setup
1. **One** member of the team should create an account on [dockerhub](https://hub.docker.com/), _incorporating the group number into the account name_, for example, `SoPra_group_XX`.\
2. This account then creates a repository on dockerhub with the _same name as the group's Github repository name_.\
3. Finally, the person's account details need to be added as [secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository) to the group's repository:
    - dockerhub_username (the username of the dockerhub account from step 1, for example, `SoPra_group_XX`)
    - dockerhub_password (a generated PAT([personal access token](https://docs.docker.com/docker-hub/access-tokens/)) of the account with read and write access)
    - dockerhub_repo_name (the name of the dockerhub repository from step 2)

### Pull and run
Once the image is created and has been successfully pushed to dockerhub, the image can be run on any machine.\
Ensure that [Docker](https://www.docker.com/) is installed on the machine you wish to run the container.\
First, pull (download) the image with the following command, replacing your username and repository name accordingly.

```docker pull <dockerhub_username>/<dockerhub_repo_name>```

Then, run the image in a container with the following command, again replacing _<dockerhub_username>_ and _<dockerhub_repo_name>_ accordingly.

```docker run -p 3000:3000 <dockerhub_username>/<dockerhub_repo_name>```
