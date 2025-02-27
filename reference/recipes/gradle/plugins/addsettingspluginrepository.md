# Add a Gradle settings repository

**org.openrewrite.gradle.plugins.AddSettingsPluginRepository**

_Add a Gradle settings repository to `settings.gradle(.kts)`._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/plugins/AddSettingsPluginRepository.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-gradle/8.12.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 8.12.0

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | type | The type of the artifact repository | `maven` |
| `String` | url | *Optional*. The url of the artifact repository | `https://repo.spring.io` |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.AddSettingsPluginRepositoryExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.AddSettingsPluginRepositoryExample
displayName: Add a Gradle settings repository example
recipeList:
  - org.openrewrite.gradle.plugins.AddSettingsPluginRepository:
      type: maven
      url: https://repo.spring.io
```
{% endcode %}

Now that `com.yourorg.AddSettingsPluginRepositoryExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("com.yourorg.AddSettingsPluginRepositoryExample")
}

repositories {
    mavenCentral()
}
```
{% endcode %}
2. Run `gradle rewriteRun` to run the recipe.
{% endtab %}

{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe AddSettingsPluginRepository
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.gradle.plugins.AddSettingsPluginRepository)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Shannon Pamperl](mailto:shanman190@gmail.com), [Jonathan Schnéider](mailto:jkschneider@gmail.com), [Nick McKinney](mailto:mckinneynicholas@gmail.com), [Sam Snyder](mailto:sam@moderne.io)
