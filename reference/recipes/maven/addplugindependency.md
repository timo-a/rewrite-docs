# Add Maven plugin dependencies

**org.openrewrite.maven.AddPluginDependency**

_Adds the specified dependencies to a Maven plugin. Will not add the plugin if it does not already exist in the pom._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-maven/src/main/java/org/openrewrite/maven/AddPluginDependency.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-maven/8.12.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-maven
* version: 8.12.0

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | pluginGroupId | Group ID of the plugin to which the dependency will be added. A group ID is the first part of a dependency coordinate `org.openrewrite.maven:rewrite-maven-plugin:VERSION`. | `org.openrewrite.maven` |
| `String` | pluginArtifactId | Artifact ID of the plugin to which the dependency will be added.The second part of a dependency coordinate `org.openrewrite.maven:rewrite-maven-plugin:VERSION`. | `rewrite-maven-plugin` |
| `String` | groupId | The group ID of the dependency to add. | `org.openrewrite.recipe` |
| `String` | artifactId | The artifact ID of the dependency to add. | `org.openrewrite.recipe` |
| `String` | version | The version of the dependency to add. | `org.openrewrite.recipe` |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.AddPluginDependencyExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.AddPluginDependencyExample
displayName: Add Maven plugin dependencies example
recipeList:
  - org.openrewrite.maven.AddPluginDependency:
      pluginGroupId: org.openrewrite.maven
      pluginArtifactId: rewrite-maven-plugin
      groupId: org.openrewrite.recipe
      artifactId: org.openrewrite.recipe
      version: org.openrewrite.recipe
```
{% endcode %}

Now that `com.yourorg.AddPluginDependencyExample` has been defined activate it in your build file:
{% tabs %}

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
            <recipe>com.yourorg.AddPluginDependencyExample</recipe>
          </activeRecipes>
        </configuration>
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
mod run . --recipe AddPluginDependency
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.maven.AddPluginDependency)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Sam Snyder](mailto:sam@moderne.io), [Jonathan Schneider](mailto:jkschneider@gmail.com)
