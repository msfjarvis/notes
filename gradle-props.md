# Gradle properties

Gradle provides multiple ways to provide properties at build-time.


- **Using the CLI**: `./gradlew -PpropertyName=propertyValue`

- **Using gradle.properties**: `echo propertyName=propertyValue >> gradle.properties`

- **From the environment**: `export ORG_GRADLE_PROJECT_propertyName=propertyValue`
