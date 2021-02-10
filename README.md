# Vanio Informatika Maven Release repository

**IMPORTANT**

On May 1 2021 Bintray and JCenter has been closed.
We migrate our Maven Repository with new releases to the GitHub Packages.

If you use easydao 3.3.4 or older versions, then you will load it automatically from Maven Central, there is no changes.
If you want to use the newer versions, then you need to access GitHub Packages.

## Set URL for new repositories

You need to push these lines into `.m2/settings.xml profile` or `pom.xml`:

```xml
<repositories>
    <repository>
        <id>github</id>
        <name>GitHub Vanio Informatika Apache Maven Packages</name>
        <url>https://maven.pkg.github.com/vanioinformatika/maven-releases</url>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
    </repository>
</repositories>
<pluginRepositories>
    <pluginRepository>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
        <id>github</id>
        <name>GitHub Vanio Informatika Apache Maven Packages for Plugins</name>
        <url>https://maven.pkg.github.com/vanioinformatika/maven-releases</url>
    </pluginRepository>
</pluginRepositories>
```

More info: https://docs.github.com/en/packages/guides/configuring-apache-maven-for-use-with-github-packages

## Set token

**IMPORTANT:** GitHub Packages requires PAT (Personal Access Token) for _public_ Maven Repository.
It will be change in the near future.

You need to create a PAT ( https://github.com/settings/tokens ) at least `read:packages` scope, and set it in `.m2/settings.xml`:

```xml
<servers>
    <server>
        <id>github</id>
        <username>your GitHub username</username>
        <password>your PAT</password>
    </server>
</servers>
```

If you already have PAT for reading or writing packages, then you don't need to create another one.

If you get `Not authorized` message after running maven (`mvn clean verify`), then misconfigured the credential.
