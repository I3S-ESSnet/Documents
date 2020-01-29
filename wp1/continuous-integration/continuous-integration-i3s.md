# Continuous integration for I3S projects

It is nowadays a best practice, even a mandatory one, to have a [continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) of a software being developped.

The core idea of continuous integration (CI for short) is to automate the build, test and validation of a software and to make visible reports produced at every step.

This document will help I3S project teams setting up the tools for CI, more precisely:

- configure build and test automation with Travis CI
- configure quality measure with Sonarcloud

## Build automation



## Code quality

When measuring software quality, [many dimensions](https://en.wikipedia.org/wiki/Software_quality#Measurement) must be taken into account. Most of the time, assessing those dimensions is done with the help of a dedicated set of tools, essentially [static code analysers](https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis), sometimes using cloud based services (like [Codeclimate](https://codeclimate.com/) or [Sonarcloud](https://sonarcloud.io/)).

This guide will focus on how to set up, configure and use Sonarcloud from a GitHub repository.

### What is Sonarcloud ?

...

### Pre-requisites

Having a GitHub repo

Language(s) supported by Sonarcloud --> https://sonarcloud.io/documentation/analysis/supported-languages/

### How to set up ?

Getting started is easy, and [described in few lines in the official documentation](https://sonarcloud.io/documentation/integrations/github/).