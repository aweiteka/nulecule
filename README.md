# Container Application Specification

## Problem Statement
Currently there is no standard mechanism to define a composite multi-container application or composite service composed of aggregate pre-defined building blocks spanning multiple hosts and clustered deployments. In addition, the associated metadata and artifact management requires separate processes outside the context of the application itself. 

## What is Nulecule?
It's a made-up word meaning ["the mother of all atomic particles"](http://simpsons.wikia.com/wiki/Made-up_words) pronounced `nu-le-cule`

Nulecule defines a pattern and model for packaging complex multi-container applications, referencing all their dependencies, including orchestration metadata in a container image for building, deploying, monitoring, and active management.

Nulecule specification enables complex applications to be defined, packaged and distributed using standard container technologies. The resulting container includes dependencies while supporting multiple orchestration providers and ability to specify resource requirements. The Nulecule specification also supports aggregation of multiple composite applications. The Nulecule specification is container and orchestration agnostic, enabling the use of any container and orchestration engine.

## Nulecule Specification Highlights

* Application description and context maintained within a single container through extensible metadata
* Composable definition of complex applications through inheritance and composition of containers into a single, standards-based, portable description.
* Simplified dependency management for the most complex applications through a directed graph to reflect relationships.
* Container and orchestration engine agnostic, enabling the use of any container technology and/or orchestration technology

## “The Big Picture”

![Alt Nulecule specification high-level story.](/images/NuleculeHigh-LevelStory.png "Nulecule specification high-level story")

## User Experience

### Kelly the System Administrator

Kelly is deploying an application that she's been provided by Acme Corp's internal developer team, led by Rufus.

1. Download the application README and answerfile template

         atomic run <deployment-container-image> --dry-run

2. Review README and edit the local answerfile for your deployment environment
3. Deploy the application

         atomic run <deployment-container-image> --answerfile answerfile.conf

At deployment the `<deployment-container-image>` is pulled, the target deployment files (e.g. kubernetes) are parameterized using the `answerfile.conf` and the application is started.

### Rufus the Developer

Rufus has been tasked to package an existing application into container images that can be deployed via kubernetes. He has some combination of RPMs, jar files and source code.

1. Develop an architecture to define how the services are connected and exposed.
1. Create Dockerfiles and artifacts to package services as container images.
1. Create provider files, e.g. for kubernetes pod, service, replication controller files
1. Reviews example templates of the container application specification
1. Builds the deployment container describing the application.
1. Pushes all container images to a registy.

## Implementations

This is only a specification. Implementations may be written in any language. See [implementation guide](/docs/implementation_guide.md) for more details.

### Developer tooling

Developer implementation provides tooling to help developers quickly package several containers as a unit. It may be as simple as generating a template to start from or as complex as a GUI to develop and provide graphical representation of the target deployment.

### Deployment tooling

Deployment implementation provides tooling for deploying the complete application using this spec.

* Reference implementation (python): https://github.com/vpavlin/atomicapp-run

### Contributing

Please review the [contributing guidelines](CONTRIBUTING.md) before submitting pull requests.

## TODO

* Create schema validation script

