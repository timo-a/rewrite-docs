# Migrate rewrite from 7 to 8

**org.openrewrite.java.upgrade.MigrateToRewrite8**

_Migrate rewrite recipe and test from version 7 to version 8.
While most parts can be automatically migrated, there are some complex and open-ended scenarios that require manual attention.
In those cases, this recipe will add a comment to the code and request a human to review and handle it manually.
Reference : Migration guide (URL to be written)._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-java/src/main/resources/META-INF/rewrite/migrate-rewrite.yml), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-java/8.12.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-java
* version: 8.12.0

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration parameters and comes from a rewrite core library. It can be activated directly without adding any dependencies.
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("org.openrewrite.java.upgrade.MigrateToRewrite8")
}

repositories {
    mavenCentral()
}

```
{% endcode %}
2. Run `gradle rewriteRun` to run the recipe.
{% endtab %}

{% tab title="Gradle init script" %}
1. Create a file named `init.gradle` in the root of your project.
{% code title="init.gradle" %}
```groovy
initscript {
    repositories {
        maven { url "https://plugins.gradle.org/m2" }
    }
    dependencies { classpath("org.openrewrite:plugin:latest.release") }
}
rootProject {
    plugins.apply(org.openrewrite.gradle.RewritePlugin)
    dependencies {
        rewrite("org.openrewrite:rewrite-java")
    }
    rewrite {
        activeRecipe("org.openrewrite.java.upgrade.MigrateToRewrite8")
    }
    afterEvaluate {
        if (repositories.isEmpty()) {
            repositories {
                mavenCentral()
            }
        }
    }
}
```
{% endcode %}
2. Run `gradle --init-script init.gradle rewriteRun` to run the recipe.
{% endtab %}
{% tab title="Maven POM" %}
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
            <recipe>org.openrewrite.java.upgrade.MigrateToRewrite8</recipe>
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

{% tab title="Maven Command Line" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.
{% code title="shell" %}
```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.activeRecipes=org.openrewrite.java.upgrade.MigrateToRewrite8
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe MigrateToRewrite8
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Migrate Rewrite recipes from version 7 to 8](../../java/recipes/migraterecipetorewrite8.md)
* [Migrate rewrite unit test from version 7 to 8](../../java/recipes/migratetesttorewrite8.md)
* [Migrate deprecated `org.openrewrite.marker.Markers#SearchResult(..)`](../../java/recipes/migratemarkerssearchresult.md)
* [Remove any-source applicability and migrate single-source applicability tests in YAML recipe](../../java/recipes/removeapplicabilitytestfromyamlrecipe.md)
* [Migrate `JavaTemplate` to accommodate Rewrite 8](../../java/recipes/migratejavatemplatetorewrite8.md)
* [update referencing package name for the recipes moved to `rewrite-static-analysis`](../../java/upgrade/updatestaticanalysispackage.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
        ---
        type: specs.openrewrite.org/v1beta/recipe
        name: org.openrewrite.java.upgrade.MigrateToRewrite8
        displayName: Migrate rewrite from 7 to 8
        description: Migrate rewrite recipe and test from version 7 to version 8.
While most parts can be automatically migrated, there are some complex and open-ended scenarios that require manual attention.
In those cases, this recipe will add a comment to the code and request a human to review and handle it manually.
Reference : Migration guide (URL to be written).

recipeList:
  - org.openrewrite.java.recipes.MigrateRecipeToRewrite8
  - org.openrewrite.java.recipes.MigrateTestToRewrite8
  - org.openrewrite.java.recipes.MigrateMarkersSearchResult
  - org.openrewrite.java.recipes.RemoveApplicabilityTestFromYamlRecipe
  - org.openrewrite.java.recipes.MigrateJavaTemplateToRewrite8
  - org.openrewrite.java.upgrade.UpdateStaticAnalysisPackage

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.upgrade.MigrateToRewrite8)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Kun Li](mailto:kun@moderne.io), [Mike Solomon](mailto:mike@moderne.io), [Jonathan Schnéider](mailto:jkschneider@gmail.com), [Knut Wannheden](mailto:knut@moderne.io), [Tim te Beek](mailto:tim@moderne.io)
