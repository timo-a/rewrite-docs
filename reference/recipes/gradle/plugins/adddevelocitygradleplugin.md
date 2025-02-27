# Add the Develocity Gradle plugin

**org.openrewrite.gradle.plugins.AddDevelocityGradlePlugin**

_Add the Develocity Gradle plugin to settings.gradle files._

## Recipe source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-gradle/src/main/java/org/openrewrite/gradle/plugins/AddDevelocityGradlePlugin.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-gradle/8.12.0/jar)

* groupId: org.openrewrite
* artifactId: rewrite-gradle
* version: 8.12.0

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `String` | version | *Optional*. An exact version number or node-style semver selector used to select the version number. You can also use `latest.release` for the latest available version and `latest.patch` if the current version is a valid semantic version. For more details, you can look at the documentation page of [version selectors](https://docs.openrewrite.org/reference/dependency-version-selectors). Defaults to `latest.release`. | `3.x` |
| `String` | server | *Optional*. The URL of the Develocity server. If omitted the recipe will set no URL and Gradle will direct scans to https://scans.gradle.com/ | `https://scans.gradle.com/` |
| `Boolean` | allowUntrustedServer | *Optional*. When set to `true` the plugin will be configured to allow unencrypted http connections with the server. If set to `false` or omitted, the plugin will refuse to communicate without transport layer security enabled. | `true` |
| `Boolean` | captureTaskInputFiles | *Optional*. When set to `true` the plugin will capture additional information about the inputs to Gradle tasks. This increases the size of build scans, but is useful for diagnosing issues with task caching.  | `true` |
| `Boolean` | uploadInBackground | *Optional*. When set to `true` the plugin will capture additional information about the outputs of Gradle tasks. This increases the size of build scans, but is useful for diagnosing issues with task caching.  | `true` |
| `PublishCriteria` | publishCriteria | *Optional*. When set to `Always` the plugin will publish build scans of every single build. When set to `Failure` the plugin will only publish build scans when the build fails. When omitted scans will be published only when the `--scan` option is passed to the build. Valid options: `Always`, `Failure` | `Always` |

## Data Tables (Only available on the [Moderne platform](https://app.moderne.io/))

### Maven metadata failures

_Attempts to resolve maven metadata that failed._

| Column Name | Description |
| ----------- | ----------- |


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
    activeRecipe("org.openrewrite.gradle.plugins.AddDevelocityGradlePlugin")
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
        activeRecipe("org.openrewrite.gradle.plugins.AddDevelocityGradlePlugin")
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

{% tab title="Moderne CLI" %}
You will need to have configured the [Moderne CLI](https://docs.moderne.io/moderne-cli/cli-intro) on your machine before you can run the following command.

{% code title="shell" %}
```shell
mod run . --recipe AddDevelocityGradlePlugin
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://app.moderne.io/recipes/org.openrewrite.gradle.plugins.AddDevelocityGradlePlugin)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.

## Contributors
[Sam Snyder](mailto:sam@moderne.io), [Shannon Pamperl](mailto:shanman190@gmail.com), [Jonathan Schneider](mailto:jkschneider@gmail.com), [Alexis Tual](mailto:atual@gradle.com), [Joan Viladrosa](mailto:joan@moderne.io)
