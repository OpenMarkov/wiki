# Welcome #

Welcome to the wiki of [**OpenMarkov**](http://www.openmarkov.org/), an open source tool for building and evaluating probabilistic graphical models.

## For users ##

You can **download** OpenMarkov's executables from the [users' page](http://www.openmarkov.org/users.html).

Other resources:

* [OpenMarkov's main page](http://www.openmarkov.org)
* [Tutorial](http://www.openmarkov.org/docs/tutorial/)
* [List of shortcuts](https://bitbucket.org/cisiad/org.openmarkov/wiki/Shortcuts)
* [Learning Bayesian networks with OpenMarkov](http://www.openmarkov.org/learning/)

[//]: # (This is a markdown comment: Add user guide here)

## For developers ##

You should first [**install an IDE**](first_install/Install_IDE.md) and then [**download the repositories**](First_download).

Wiki pages:

* [OpenMarkov's_organization (Maven subprojects)](OpenMarkov's_organization)
* [Working methodology](Working_methodology): good practices for OpenMarkov developers.
* [OpenMarkov organization](OpenMarkov's_organization): schematic tree of Maven subprojects.
* [Developing code](Developing_code_home): adding specific elements, such as new metrics and algorithms for learning and other extensions.
* [Java's Metaprogramming Overview and Tutorial](Java's Metaprogramming Overview and Tutorial): And overview to Java's Annotation Processing as a Metaprogramming system; It includes a tutorial on how to use it.

Other resources:

* [Javadoc](http://www.openmarkov.org/javadoc/).
* [Technical documents](https://bitbucket.org/cisiad/org.openmarkov.doc/src/master/).
* [Useful plugins for IntelliJ](Plugins of interest when developing with IntelliJ).

#### Using OpenMarkov as an API

If you wish to use OpenMarkov as an API, you will need to [download OpenMarkov's repositories](First_download) and import them into your IDE. Then you should create a project in your IDE, declare the dependencies on the necessary OpenMarkov's subprojects (see [OpenMarkov's organization](OpenMarkov's_organization)), and generate a jar file with Maven.

As an example, we have created the project [exampleAPI](https://bitbucket.org/cisiad/org.openmarkov.exampleapi/src). You can clone it on your computer using Git and rename it. Then rename the file ExampleAPI.java and adapt it to your needs. Don't forget to update the pom.xml file, which will be used by Maven to compile the jar file.

#### Contributing your code as an external developer

If you have written an extension for OpenMarkov in the form of a new subproject, please contact us at **contributions@openmarkov.org** to discuss including it in the "official" releases.

In some cases, we will allow external developers to modify OpenMarkov's existing modules (subprojects). In this case:

1. Create a branch of the subproject in your Bitbucket repository. This way, when you wish, the developers at the [CISIAD](http://www.cisiad.uned.es) will be able to examine the new code.
2. Once the code is approved and the contributor signs a distribution agreement licence, the contribution will be merged with the "official" code.

## Reporting bugs ##
We encourage you to inform us in our [**issue tracker**](http://issues.openmarkov.org). When informing, please make sure that your issue has not been already reported.  
Thanks in advance for your collaboration.

## Contact
If you need any help, contact us at **developers.support@openmarkov.org**.

[//]: # (## Copyright ## Fill this section)