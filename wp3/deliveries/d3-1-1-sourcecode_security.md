# Protecting your source code

..
## Quality level checklist
* Consider authentication requirements for exposed endpoints
* Consider encryption of data "at rest" based on classification levels, and at least encryption with the key provided by the service provider
* Ensure that configuration and secrets outside the container is safe and encrypted
* Consider using a standard for assessing the severity of computer system security vulnerabilities (for instance CVSS)

### Security checklist
* Ensure that events and transactions that are logged are possible to trace
* Ensure that any secrets and configurations are safely stored
* Ensure that the container for the service does not run as root
* Ensure that services that should be exposed are available with HTTPS on a public domain
* Ensure that any service accounts has the least necessary priviliges
* Consider high availability and automatic scaling configuration for the service
* Ensure that a vulnerability scanning of the container for the service is performed
* Ensure that any known vulnerabilities of the service are documented
* Ensure that the logs are stored safely

### Loggin checklist
* Never log sensitive information
* Define for how long the logs should be valid and stored
* Ensure that the logs are deleted when they are not longer valid
* Ensure that the logs are structured and have a defined format
* Ensure that the logs are machine readable
* Ensure that the logs are available for any developers that needs them
* Ensure that the logs are available for privileged users (how?)
* Ensure that the logs are backed up
* Ensure that you log at the appropriate level and context

## Security by obscurity

..

## Scanning code

..

## Utilizing GitHub and DependaBot 

..

## Scanning containers

..

## Utilizing tools like 

..

## Strategies for sealing secrets

..
