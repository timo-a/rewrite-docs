# Remove obsolete Spring JUnit runners

**org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners**

_Remove obsolete classpath runners._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/resources/META-INF/rewrite/spring-boot-24.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/5.1.7/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 5.1.7

{% hint style="info" %}
This recipe is composed of more than one recipe. If you want to customize the set of recipes this is composed of, you can find and copy the GitHub source for the recipe from the link above.
{% endhint %}

## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:5.1.7` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
1. Add the following to your `build.gradle` file:
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("6.6.3")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:5.1.7")
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
        rewrite("org.openrewrite.recipe:rewrite-spring:5.1.7")
    }
    rewrite {
        activeRecipe("org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners")
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
            <recipe>org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>5.1.7</version>
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
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners
```
{% endcode %}
{% endtab %}
{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe RemoveObsoleteSpringRunners
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Remove JUnit 4 `@RunWith` annotations that do not require an `@ExtendsWith` replacement](../../../java/testing/junit5/removeobsoleterunners.md)
  * obsoleteRunners: `[org.springframework.boot.junit.runner.classpath.ModifiedClassPathRunner, org.springframework.boot.testsupport.runner.classpath.ModifiedClassPathRunner]`
* [JUnit Jupiter best practices](../../../java/testing/junit5/junit5bestpractices.md)

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners
displayName: Remove obsolete Spring JUnit runners
description: Remove obsolete classpath runners.
recipeList:
  - org.openrewrite.java.testing.junit5.RemoveObsoleteRunners:
      obsoleteRunners: [org.springframework.boot.junit.runner.classpath.ModifiedClassPathRunner, org.springframework.boot.testsupport.runner.classpath.ModifiedClassPathRunner]
  - org.openrewrite.java.testing.junit5.JUnit5BestPractices

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.java.spring.boot2.RemoveObsoleteSpringRunners)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
Patrick Way, [Patrick](mailto:patway99@gmail.com), [Knut Wannheden](mailto:knut@moderne.io), [Jonathan Schneider](mailto:jkschneider@gmail.com), [Sam Snyder](mailto:sam@moderne.io), Yeikel, [Jonathan Schnéider](mailto:jkschneider@gmail.com), [Greg Adams](mailto:gadams@gmail.com), [Tim te Beek](mailto:tim.te.beek@jdriven.com), Adriano Machado, [Tracey Yoshima](mailto:tracey.yoshima@gmail.com), [Greg Adams](mailto:greg@moderne.io), [Nick McKinney](mailto:mckinneynicholas@gmail.com), [magicwerk](mailto:magicwerk@gmail.com), [Tim te Beek](mailto:tim@moderne.io), Tyler Van Gorder, [Sofia Britto Schwartz](mailto:sofia.b.schwartz@gmail.com), [Aaron Gershman](mailto:aegershman@gmail.com), John Burns, [Michael Keppler](mailto:bananeweizen@gmx.de), [traceyyoshima](mailto:tracey.yoshima@gmail.com), [Scott Jungling](mailto:scott.jungling@gmail.com), Ties van de Ven, Peter Puškár, [Tim te Beek](mailto:timtebeek@gmail.com), [Joan Viladrosa](mailto:joan@moderne.io), [Kun Li](mailto:kun@moderne.io), [Kyle Scully](mailto:scullykns@gmail.com), [Simon Verhoeven](mailto:verhoeven.simon@gmail.com)
