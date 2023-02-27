# Use `actions/setup-java` `temurin` distribution as they are cached in hosted runners

**org.openrewrite.github.PreferTemurinDistributions**
_[Host runners](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners#supported-runners-and-hardware-resources/) include Temurin by default as part of the (hosted tool cache)(https://github.com/actions/setup-java/blob/main/docs/advanced-usage.md#hosted-tool-cache).Using Temurin speeds up builds as there is no need to download and configure the Java SDK with every build._

## Source

[Github](https://github.com/openrewrite/rewrite-github-actions/blob/main/src/main/java/org/openrewrite/github/PreferTemurinDistributions.java), [Issue Tracker](https://github.com/openrewrite/rewrite-github-actions/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite.recipe/rewrite-github-actions/1.18.0-SNAPSHOT/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-github-actions
* version: 1.18.0-SNAPSHOT


## Usage

This recipe has no required configuration options and can be activated directly after taking a dependency on org.openrewrite.recipe:rewrite-github-actions:1.18.0-SNAPSHOT in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.36.0")
}

rewrite {
    activeRecipe("org.openrewrite.github.PreferTemurinDistributions")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-github-actions:1.18.0-SNAPSHOT")
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
        <version>4.40.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.github.PreferTemurinDistributions</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-github-actions</artifactId>
            <version>1.18.0-SNAPSHOT</version>
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
```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-github-actions:LATEST \
  -DactiveRecipes=org.openrewrite.github.PreferTemurinDistributions
```
{% endcode %}
{% endtab %}
{% endtabs %}

Recipes can also be activated directly from the command line by adding the argument `-Drewrite.activeRecipes=org.openrewrite.github.PreferTemurinDistributions`

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.github.PreferTemurinDistributions)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.