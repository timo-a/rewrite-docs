# Change method name

**org.openrewrite.python.ChangeMethodName**

_Renames a method._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-python/blob/main/src/main/java/org/openrewrite/python/ChangeMethodName.java), [Issue Tracker](https://github.com/openrewrite/rewrite-python/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-python/1.2.7/jar)

* groupId: org.openrewrite
* artifactId: rewrite-python
* version: 1.2.7

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | oldMethodName | The method name that will replace the existing name. | `any` |
| `String` | newMethodName | The method name that will replace the existing name. | `any` |
| `Boolean` | ignoreDefinition | *Optional*. When set to `true` the definition of the old type will be left untouched. This is useful when you're replacing usage of a class but don't want to rename it. |  |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangeMethodNameExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangeMethodNameExample
displayName: Change method name example
recipeList:
  - org.openrewrite.python.ChangeMethodName:
      oldMethodName: any
      newMethodName: any
```
{% endcode %}

Now that `com.yourorg.ChangeMethodNameExample` has been defined activate it and take a dependency on org.openrewrite:rewrite-python:1.2.7 in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("com.yourorg.ChangeMethodNameExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite:rewrite-python:1.2.7")
}
```
{% endcode %}
2. Run `gradle rewriteRun` to run the recipe.
{% endtab %}
{% tab title="Maven" %}
1. Add the following to your `pom.xml` file:
{% code title="pom.xml" %}
```xml
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>5.17.1</version>
        <configuration>
          <activeRecipes>
            <recipe>com.yourorg.ChangeMethodNameExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite</groupId>
            <artifactId>rewrite-python</artifactId>
            <version>1.2.7</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
2. Run `mvn rewrite:run` to run the recipe.
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe ChangeMethodName
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.python.ChangeMethodName)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[traceyyoshima](mailto:tracey.yoshima@gmail.com), [Tim te Beek](mailto:timtebeek@gmail.com), Mike Sol, [Knut Wannheden](mailto:knut@moderne.io)
