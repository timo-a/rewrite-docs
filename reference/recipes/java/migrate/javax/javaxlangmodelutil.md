# Use modernized `javax.lang.model.util` APIs

**org.openrewrite.java.migrate.javax.JavaxLangModelUtil**

_Certain `javax.lang.model.util` APIs have become deprecated and their usages changed, necessitating usage changes._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/javax-lang-model-util.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/2.5.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 2.5.0

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:2.5.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.javax.JavaxLangModelUtil")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:2.5.0")
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
    dependencies { classpath("org.openrewrite:plugin:6.6.3") }
}
rootProject {
    plugins.apply(org.openrewrite.gradle.RewritePlugin)
    dependencies {
        rewrite("org.openrewrite.recipe:rewrite-migrate-java:2.5.0")
    }
    rewrite {
        activeRecipe("org.openrewrite.java.migrate.javax.JavaxLangModelUtil")
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
            <recipe>org.openrewrite.java.migrate.javax.JavaxLangModelUtil</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>2.5.0</version>
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

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.migrate.javax.JavaxLangModelUtil
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe JavaxLangModelUtil
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Use `javax.lang.model.util.AbstractAnnotationValueVisitor9`](../../../java/migrate/javax/migrateabstractannotationvaluevisitor6to9.md)
* [Use `javax.lang.model.util.AbstractElementVisitor9`](../../../java/migrate/javax/migrateabstractelementvisitor6to9.md)
* [Use `javax.lang.model.util.AbstractTypeVisitor9`](../../../java/migrate/javax/migrateabstracttypevisitor6to9.md)
* [Use `javax.lang.model.util.ElementKindVisitor9`](../../../java/migrate/javax/migrateelementkindvisitor6to9.md)
* [Use `javax.lang.model.util.ElementScanner9`](../../../java/migrate/javax/migrateelementscanner6to9.md)
* [Use `javax.lang.model.util.SimpleAnnotationValueVisitor9`](../../../java/migrate/javax/migratesimpleannotationvaluevisitor6to9.md)
* [Use `javax.lang.model.util.SimpleElementVisitor9`](../../../java/migrate/javax/migratesimpleelementvisitor6to9.md)
* [Use `javax.lang.model.util.SimpleTypeVisitor9`](../../../java/migrate/javax/migratesimpletypevisitor6to9.md)
* [Use `javax.lang.model.util.TypeKindVisitor9`](../../../java/migrate/javax/migratetypekindvisitor6to9.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.javax.JavaxLangModelUtil
displayName: Use modernized `javax.lang.model.util` APIs
description: Certain `javax.lang.model.util` APIs have become deprecated and their usages changed, necessitating usage changes.
recipeList:
  - org.openrewrite.java.migrate.javax.MigrateAbstractAnnotationValueVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateAbstractElementVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateAbstractTypeVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateElementKindVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateElementScanner6To9
  - org.openrewrite.java.migrate.javax.MigrateSimpleAnnotationValueVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateSimpleElementVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateSimpleTypeVisitor6To9
  - org.openrewrite.java.migrate.javax.MigrateTypeKindVisitor6To9

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.migrate.javax.JavaxLangModelUtil)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
