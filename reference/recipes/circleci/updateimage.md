# Update CircleCI image

**org.openrewrite.circleci.UpdateImage**

_See the list of [pre-built CircleCI images](https://circleci.com/docs/2.0/circleci-images/)._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-circleci/blob/main/src/main/java/org/openrewrite/circleci/UpdateImage.java), [Issue Tracker](https://github.com/openrewrite/rewrite-circleci/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-circleci/2.0.13/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-circleci
* version: 2.0.13

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | image | Image to use. | `circleci/openjdk:jdk` |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UpdateImageExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UpdateImageExample
displayName: Update CircleCI image example
recipeList:
  - org.openrewrite.circleci.UpdateImage:
      image: circleci/openjdk:jdk
```
{% endcode %}

Now that `com.yourorg.UpdateImageExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-circleci:2.0.13 in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("com.yourorg.UpdateImageExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-circleci:2.0.13")
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
            <recipe>com.yourorg.UpdateImageExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-circleci</artifactId>
            <version>2.0.13</version>
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
mod run . --recipe UpdateImage
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.circleci.UpdateImage)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Jonathan Schneider](mailto:jkschneider@gmail.com), [Knut Wannheden](mailto:knut.wannheden@gmail.com), [Tim te Beek](mailto:timtebeek@gmail.com)
