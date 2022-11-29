# 1. configure ~/.m2/settings.yml

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo1.maven.org/maven2</url>
        </repository>
        <repository>
          <id>github</id>
          <url>https://maven.pkg.github.com/githubusername/repository</url>  <!-- username/repo lowercase -->
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>github</id>
      <username>GithubUsername</username>    <!-- github username/organisation -->
      <password>GithubToken</password>       <!-- https://github.com/settings/tokens -->
    </server>
  </servers>
</settings>
```

# 2. Deploy

```xml
  <distributionManagement>
    <repository>
      <id>github</id>
      <name>${artifactId}</name>
      <url>https://maven.pkg.github.com/${groupId}/${artifactId}</url>
    </repository>
  </distributionManagement>
```

# 3. Import

> Repo from central??

```xml
  <dependency>
    <groupId>${groupId}</groupId>           <!-- groupId of deployed package -->
    <artifactId>${artifactId}</artifactId>  <!-- artifactId of deployed package -->
    <version>${version}</version>           <!-- version of deployed package -->
  </dependency>
```
