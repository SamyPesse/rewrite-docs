# No primitive wrappers for #toString() or #compareTo(..)

** org.openrewrite.java.cleanup.NoPrimitiveWrappersForToStringOrCompareTo**
_Primitive wrappers should not be instantiated only for `#toString()` or `#compareTo(..)` invocations_

### Tags

* RSPEC-1158

## Source

[Github](https://github.com/openrewrite/rewrite), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://search.maven.org/artifact/org.openrewrite/rewrite-java/7.16.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 7.16.0


## Usage

This recipe has no required configuration parameters and comes from a rewrite core library. It can be activated directly without adding any dependencies.

{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.14.0")
}

rewrite {
    activeRecipe("org.openrewrite.java.cleanup.NoPrimitiveWrappersForToStringOrCompareTo")
}

repositories {
    mavenCentral()
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
        <version>4.16.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.cleanup.NoPrimitiveWrappersForToStringOrCompareTo</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}

Recipes can also be activated directly from the command line by adding the argument `-DactiveRecipe=org.openrewrite.java.cleanup.NoPrimitiveWrappersForToStringOrCompareTo`