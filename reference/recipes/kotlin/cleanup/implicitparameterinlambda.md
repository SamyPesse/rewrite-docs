# "it" shouldn't be used as a lambda parameter name

**org.openrewrite.kotlin.cleanup.ImplicitParameterInLambda**

_"it" is a special identifier that allows you to refer to the current parameter being passed to a lambda expression without explicitly naming the parameter. Lambda expressions are a concise way of writing anonymous functions. Many lambda expressions have only one parameter, when this is true the compiler can determine the parameter type by context. Thus when using it with single parameter lambda expressions, you do not need to declare the type._

### Tags

* RSPEC-6558

## Source

[GitHub](https://github.com/openrewrite/rewrite-kotlin/blob/main/src/main/java/org/openrewrite/kotlin/cleanup/ImplicitParameterInLambda.java), [Issue Tracker](https://github.com/openrewrite/rewrite-kotlin/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-kotlin/1.1.8/jar)

* groupId: org.openrewrite
* artifactId: rewrite-kotlin
* version: 1.1.8

## Example


{% tabs %}
{% tab title="kotlin" %}

###### Before
{% code %}
```kotlin
fun method() {
    listOf(1, 2, 3).forEach { it -> it.and(6) }
    val a: (Int) -> Int = { it -> it + 5 }
}
```
{% endcode %}

###### After
{% code %}
```kotlin
fun method() {
    listOf(1, 2, 3).forEach { it.and(6) }
    val a: (Int) -> Int = { it + 5 }
}
```
{% endcode %}

{% endtab %}
{% tab title="Diff" %}
{% code %}
```diff
@@ -2,2 +2,2 @@
fun method() {
-   listOf(1, 2, 3).forEach { it -> it.and(6) }
-   val a: (Int) -> Int = { it -> it + 5 }
+   listOf(1, 2, 3).forEach { it.and(6) }
+   val a: (Int) -> Int = { it + 5 }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite:rewrite-kotlin:1.1.8` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.1.15")
}

rewrite {
    activeRecipe("org.openrewrite.kotlin.cleanup.ImplicitParameterInLambda")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite:rewrite-kotlin:1.1.8")
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
            <recipe>org.openrewrite.kotlin.cleanup.ImplicitParameterInLambda</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite</groupId>
            <artifactId>rewrite-kotlin</artifactId>
            <version>1.1.8</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite:rewrite-kotlin:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.kotlin.cleanup.ImplicitParameterInLambda
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Contributors
* [Kun Li](mailto:kun@moderne.io)
* [traceyyoshima](mailto:tracey.yoshima@gmail.com)


## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.kotlin.cleanup.ImplicitParameterInLambda)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
