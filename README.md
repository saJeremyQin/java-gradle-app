##### build the project

    ./gradlew build

##### build Docker image called java-app. Execute from root

    docker build -t java-app .
    
##### push image to repo 

    docker tag java-app demo-app:java-1.0

##### publish JAR to Nexus using .env

1. Create local env file (already included as `.env`):

    cp .env.example .env

2. Edit `.env` and set your real values:

    NEXUS_URL=https://your-nexus-host
    NEXUS_REPOSITORY=maven-snapshots
    NEXUS_USERNAME=mooji
    NEXUS_PASSWORD=your-token-or-password

3. Load variables into your current shell and publish:

    set -a
    source .env
    set +a
    ./gradlew publish

Note: `.env` is gitignored, so secrets do not get committed.
    

### Changes
[23.Aug.2021]

Gradle wrapper version upgraded from version 6.x to 7.0 
        
###### This will change the version in wrapper.settings

     ./gradlew wrapper --gradle-version 7.0

###### This will update the complete wrapper and download version 7.0 jar

     ./gradlew wrapper --gradle-version 7.0

In build.gradle file, replace:
- compile with implementation 
- testCompile with testImplementation

Because, version 7.0 removed compile and testCompile configurations.
Source: https://docs.gradle.org/current/userguide/upgrading_version_6.html#sec:configuration_removal