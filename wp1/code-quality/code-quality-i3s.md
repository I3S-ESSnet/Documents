# Continuous integration for I3S projects

It is nowadays a best practice, even a mandatory one, to have a [continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) of a software being developped.

The core idea of continuous integration (CI for short) is to automate the build, test and validation of a software and to make visible reports produced at every step.

This document will help I3S project teams setting up the tools for CI, more precisely:

- configure build and test automation with [Travis CI](https://travis-ci.org/),
- configure quality measure with [Sonarcloud](https://sonarcloud.io/).

A note: this guide is proposed in the context of a project that is already hosted on GitHub.

## Build and tests automation

Usually, a software team is composed of several developers, each working on a separate feature (or each pair when pair programming). The main principle of continous integration is to merge the work of each developers several times a day, in order to check automatically that code parts from different developpers integrate well.

In order to do that, it is necessary to:

- gather code changes from the version control system (git or GitHub for example) ;
- build the modified code, and report errors if they occur ;
- execute any validation phase (most of the time via unit tests).

A lot of continuous integration tools exist, we'll focus on Travis CI.

### Setting up Travis

The set up is straightforward as given by the [official documentation](https://docs.travis-ci.com/user/tutorial/). 

One of the key requisite is that you have owner permissions for the GitHub project your want to run on Travis. You only need to log into Travis CI site using your GitHub credentials.

Then, configuring your build and test is easy as describing it in a .travis.yaml file. A [simple yet complete example can be found in the ARC repository](https://github.com/InseeFr/ARC/blob/master/.travis.yml).

The `script` command gives the command to run when building a new version of the code. In the above example, Maven is used for this purpose, ARC being a Java project.

For more complex use cases you'll need to refer to the [documentation](https://docs.travis-ci.com/).

## Code quality

When measuring software quality, [many dimensions](https://en.wikipedia.org/wiki/Software_quality#Measurement) must be taken into account. Most of the time, assessing those dimensions is done with the help of a dedicated set of tools, essentially [static code analysers](https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis), sometimes using cloud based services (like [Codeclimate](https://codeclimate.com/) or [Sonarcloud](https://sonarcloud.io/)).

This guide will focus on how to set up, configure and use Sonarcloud from a GitHub repository.

### Supported languages

Before starting you need to check if [your main language is supported by Sonarcloud](https://sonarcloud.io/documentation/analysis/supported-languages/).

### How to set up ?

Getting started is easy, and [described in few lines in the official documentation](https://sonarcloud.io/documentation/integrations/github/).

--> authentication

## A word on continuous delivery / deployment

Often you will hear the term CI/CD - the conjunction of continuous integration with continuous delivery or deployment. This second expression is describing the natural continuation of CI: after having build and test your software, you could be confident that it is ready to be delivered to users, so this part is also automated.

What is the difference between one and the other "d" ? When doing continuous __delivery__ the software is delivered to whatever system or team responsible for its deployment, whereas in continuous __deployment__ the package is directly deployed, in staging and / or production environment.

## References

[Travis CI for beginners](https://docs.travis-ci.com/user/for-beginners)