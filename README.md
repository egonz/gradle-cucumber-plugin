# Gradle Cucumber Plugin

![Cucumber Logo] (https://a248.e.akamai.net/camo.github.com/d716f18fbcff34df385b5fcbdbfa21588e09aed4/687474703a2f2f63756b65732e696e666f2f696d616765732f637563756d6265725f6c6f676f2e706e67)

The gradle cucumber plugin provides the ability to run [cucumber](http://cukes.info) acceptance tests directly
from a gradle build.  The plugin utilizes the cucumber cli provided by the [cucumber-jvm](https://github.com/cucumber/cucumber-jvm) project
and should support any of the langues utilized in cucumber-jvm.

(Currently only tested with Java and Groovy, more coming soon!)

## Using the plugin in your gradle build script

You can apply the plugin using the following buildscript directly from github:

      buildscript {
          apply from: 'https://github.com/samueltbrown/gradle-cucumber-plugin/raw/master/repo/gradle-cucumber-plugin/gradle-cucumber-plugin/0.1/cucumberinit.gradle'
      }

Currently the version is set at <b>0.1</b> in the link but this can be updated the latest version as it becomes available.
Once the plugin has been applied, the project dependencies need to be updated with the archive path to your jar file
as well as the cucumber-jvm jar file needed for your language.  Below 'groovy' is the chosen language.

      dependencies {

      	cucumberRuntime files("${jar.archivePath}"),
                        'info.cukes:cucumber-groovy:1.0.11'

      }

## Available Tasks

Currently the plugin only supports one task to run your cucumber tests:

      >gradle cucumber

## Cucumber Task Configuration

The cucumber task has several configurable properties:

* `formats`: A list of output formats. (Defaults to <b>pretty</b>)
* `glueDirs`: A list of directories where feature files and stepdefs are located
              (Defaults to <b>src/test/resources</b> and <b>src/test/java</b>
* `monochrome`: A boolean value indicating if console output should be one color. (Defaults to <b>false</b>)
* `strict`: A boolean value indicating whether scenarios should be evaluated strictly. (Defaults to <b>false</b>)
* `dryRun`: A boolean value indicating whether scenarios should be run as a dry run. (Defaults to <b>false</b>)

### Example task configuration

    cucumber {
        formats = ['pretty','json:build/cucumber.json','junit:build/cucumber.xml']
        glueDirs = ['src/test/resources/features','src/test/groovy']
        monochrome = false
        strict = false
        dryRun = false
    }

## Coming Soon

* Use of tags
* Automatic dependency retrieval and default glue dirs for each jvm language
* Simplified task configuration
* Command-line arguments to override task configuration

