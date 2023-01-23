# Add a Gradle settings plugin

**org.openrewrite.gradle.plugins.AddSettingsPlugin**
_Add a Gradle settings plugin to `settings.gradle(.kts)`._

## Source

[Github](https://github.com/openrewrite/rewrite/tree/main/rewrite-gradle), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-gradle/7.35.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 7.35.0

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | pluginId | The plugin id to apply. |
| `String` | version | An exact version number or node-style semver selector used to select the version number. |
| `String` | versionPattern | *Optional*. Allows version selection to be extended beyond the original Node Semver semantics. So for example,Setting 'version' to "25-29" can be paired with a metadata pattern of "-jre" to select Guava 29.0-jre |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your rewrite.yml create a new recipe with a unique name. For example: `com.yourorg.AddSettingsPluginExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.AddSettingsPluginExample
displayName: Add a Gradle settings plugin example
recipeList:
  - org.openrewrite.gradle.plugins.AddSettingsPlugin:
      pluginId: com.jfrog.bintray
      version: 3.x
      versionPattern: '-jre'
```
{% endcode %}

Now that `com.yourorg.AddSettingsPluginExample` has been defined activate it and take a dependency on org.openrewrite:rewrite-gradle:7.35.0 in your build file:

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.34.0")
}

rewrite {
    activeRecipe("com.yourorg.AddSettingsPluginExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite:rewrite-gradle:7.35.0")
}
```
{% endcode %}
{% endtab %}

{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>4.39.0</version>
        <configuration>
          <activeRecipes>
            <recipe>com.yourorg.AddSettingsPluginExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite</groupId>
            <artifactId>rewrite-gradle</artifactId>
            <version>7.35.0</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}

Recipes can also be activated directly from the command line by adding the argument `-Drewrite.activeRecipes=com.yourorg.AddSettingsPluginExample`

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.gradle.plugins.AddSettingsPlugin)

The Moderne public SaaS instance enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.