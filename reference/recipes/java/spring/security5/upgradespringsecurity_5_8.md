# Migrate to Spring Security 5.8

**org.openrewrite.java.spring.security5.UpgradeSpringSecurity\_5\_8**

_Migrate applications to the latest Spring Security 5.8 release. This recipe will modify an application's build files, make changes to deprecated/preferred APIs, and migrate configuration settings that have changes between versions._

### Tags

* spring
* security

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-security-58.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.0.5/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 5.0.5


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:5.0.5` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.1.15")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.security5.UpgradeSpringSecurity_5_8")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:5.0.5")
}
```
{% endcode %}
{% endtab %}
{% tab title="Maven POM" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>5.2.6</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.spring.security5.UpgradeSpringSecurity_5_8</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>5.0.5</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.spring.security5.UpgradeSpringSecurity_5_8
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Upgrade Gradle or Maven dependency versions](../../../java/dependencies/upgradedependencyversion.md)
  * groupId: `org.springframework.security`
  * artifactId: `*`
  * newVersion: `5.8.x`
  * overrideManagedVersion: `false`
* [Use the new `requestMatchers` methods](../../../java/spring/security5/usenewrequestmatchers.md)
* [Use the new `securityMatcher()` method](../../../java/spring/security5/usenewsecuritymatchers.md)
* [Use new `Pbkdf2PasswordEncoder` factory methods](../../../java/spring/security5/updatepbkdf2passwordencoder.md)
* [Use new `SCryptPasswordEncoder` factory methods](../../../java/spring/security5/updatescryptpasswordencoder.md)
* [Use new `Argon2PasswordEncoder` factory methods](../../../java/spring/security5/updateargon2passwordencoder.md)
* [Replace global method security with method security](../../../java/spring/security5/replaceglobalmethodsecuritywithmethodsecurity.md)
* [Replace global method security with method security](../../../java/spring/security5/replaceglobalmethodsecuritywithmethodsecurityxml.md)
* [Spring Security 5.4 introduces the ability to configure `HttpSecurity` by creating a `SecurityFilterChain` bean](../../../java/spring/security5/websecurityconfigureradapter.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.security5.UpgradeSpringSecurity_5_8
displayName: Migrate to Spring Security 5.8
description: Migrate applications to the latest Spring Security 5.8 release. This recipe will modify an application's build files, make changes to deprecated/preferred APIs, and migrate configuration settings that have changes between versions.

tags:
  - spring
  - security
recipeList:
  - org.openrewrite.java.dependencies.UpgradeDependencyVersion:
      groupId: org.springframework.security
      artifactId: *
      newVersion: 5.8.x
      overrideManagedVersion: false
  - org.openrewrite.java.spring.security5.UseNewRequestMatchers
  - org.openrewrite.java.spring.security5.UseNewSecurityMatchers
  - org.openrewrite.java.spring.security5.UpdatePbkdf2PasswordEncoder
  - org.openrewrite.java.spring.security5.UpdateSCryptPasswordEncoder
  - org.openrewrite.java.spring.security5.UpdateArgon2PasswordEncoder
  - org.openrewrite.java.spring.security5.ReplaceGlobalMethodSecurityWithMethodSecurity
  - org.openrewrite.java.spring.security5.ReplaceGlobalMethodSecurityWithMethodSecurityXml
  - org.openrewrite.java.spring.security5.WebSecurityConfigurerAdapter

```
{% endtab %}
{% endtabs %}

## Contributors
* [Knut Wannheden](mailto:knut@moderne.io)
* [Alex Boyko](mailto:aboyko@vmware.com)
* [Johannes Jank](mailto:johannes.wengert@googlemail.com)
* [Kun Li](mailto:kun@moderne.io)
* Kun Li
* [Jonathan Schnéider](mailto:jkschneider@gmail.com)
* [Sam Snyder](mailto:sam@moderne.io)
* Patrick Way
* [Nick McKinney](mailto:mckinneynichoals@gmail.com)
* [Patrick](mailto:patway99@gmail.com)
* Josh Soref


## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.security5.UpgradeSpringSecurity_5_8)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
