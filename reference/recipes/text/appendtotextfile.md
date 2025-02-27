# Append to text file

**org.openrewrite.text.AppendToTextFile**

_Appends or replaces content of an existing plain text file, or creates a new one if it doesn't already exist._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-core/src/main/java/org/openrewrite/text/AppendToTextFile.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-core/8.12.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-core
* version: 8.12.0

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | relativeFileName | File name, using a relative path. If a non-plaintext file already exists at this location, then this recipe will do nothing. | `foo/bar/baz.txt` |
| `String` | content | Multiline text content to be appended to the file. | `Some text.` |
| `String` | preamble | *Optional*. If a new file is created, this content will be included at the beginning. | `# File generated by OpenRewrite #` |
| `Boolean` | appendNewline | *Optional*. Print a newline automatically after the content (and preamble). Default true. |  |
                        | `Strategy` | existingFileStrategy | *Optional*. Determines behavior if a file exists at this location prior to Rewrite execution.

- `Continue`: append new content to existing file contents. If existing file is not plaintext, recipe does nothing.
- `Replace`: remove existing content from file.
- `Leave`: *(default)* do nothing. Existing file is fully preserved.

Note: this only affects the first interaction with the specified file per Rewrite execution.
Subsequent instances of this recipe in the same Rewrite execution will always append. Valid options: `Continue`, `Replace`, `Leave` |  |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.AppendToTextFileExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.AppendToTextFileExample
displayName: Append to text file example
recipeList:
  - org.openrewrite.text.AppendToTextFile:
      relativeFileName: foo/bar/baz.txt
      content: Some text.
      preamble: # File generated by OpenRewrite #
```
{% endcode %}

Now that `com.yourorg.AppendToTextFileExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("com.yourorg.AppendToTextFileExample")
}

repositories {
    mavenCentral()
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
            <recipe>com.yourorg.AppendToTextFileExample</recipe>
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
mod run . --recipe AppendToTextFile
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.text.AppendToTextFile)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Jonathan Schnéider](mailto:jkschneider@gmail.com), [Nick McKinney](mailto:mckinneynicholas@gmail.com), [Knut Wannheden](mailto:knut.wannheden@gmail.com), Kun Li
