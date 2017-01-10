[![Codacy Badge](https://api.codacy.com/project/badge/Grade/b113518db15c4736a0732980872c31c5)](https://www.codacy.com/app/jacek-spolnik/JAlgoArena-Submissions?utm_source=github.com&utm_medium=referral&utm_content=spolnik/JAlgoArena-Submissions&utm_campaign=badger)
# JAlgoArena Submissions [![Build Status](https://travis-ci.org/spolnik/JAlgoArena-Submissions.svg?branch=master)](https://travis-ci.org/spolnik/JAlgoArena-Submissions) [![codecov](https://codecov.io/gh/spolnik/JAlgoArena-Submissions/branch/master/graph/badge.svg)](https://codecov.io/gh/spolnik/JAlgoArena-Submissions) [![GitHub release](https://img.shields.io/github/release/spolnik/jalgoarena-submissions.svg)]()

JAlgoArena Submissions is service dedicated for collecting users submissions and exposing that data together with calculating ranking for all submissions as well as for problem based rankings. Quering submissions and submitting it has to be secure operation - methods require passing token which is then checked with Auth service.

Demo: https://jalgoarena-ui.herokuapp.com/

- [Introduction](#introduction)
- [Components](#components)
- [Continuous Delivery](#continuous-delivery)
- [Infrastructure](#infrastructure)
- [Running Locally] (#running-locally)
- [Notes](#notes)

## Introduction

- JAlgoArena Submissions consists two parts, CRUD operations for Submissions and exposing two calculated rankings - all submissions ranking and problem rankings

![Component Diagram](https://github.com/spolnik/JAlgoArena/raw/master/design/component_diagram.png)

## Components

- [JAlgoArena](https://github.com/spolnik/JAlgoArena)
- [JAlgoArena UI](https://github.com/spolnik/JAlgoArena-UI)
- [JAlgoArena Auth Server](https://github.com/spolnik/JAlgoArena-Auth)
- [JAlgoArena Eureka Server](https://github.com/spolnik/JAlgoArena-Eureka)
- [JAlgoArena API Gateway](https://github.com/spolnik/JAlgoArena-API)

## Continuous Delivery

- initially, developer push his changes to GitHub
- in next stage, GitHub notifies Travis CI about changes
- Travis CI runs whole continuous integration flow, running compilation, tests and generating reports
- coverage report is sent to Codecov
- application is deployed into Heroku machine

## Infrastructure

- Heroku (PaaS)
- Xodus (embedded highly scalable database) - http://jetbrains.github.io/xodus/
- Spring Boot, Spring Cloud (Eureka Client)
- TravisCI - https://travis-ci.org/spolnik/JAlgoArena-Submissions

## Running locally

There are two ways to run it - from sources or from binaries.
- Default port: `5003`

### Running from binaries
- go to [releases page](https://github.com/spolnik/JAlgoArena-Submissions/releases) and download last app package (JAlgoArena-Submissions-[version_number].zip)
- after unpacking it, go to folder and run `./run.sh` (to make it runnable, invoke command `chmod +x run.sh`)
- you can modify port and Eureka service url in run.sh script, depending on your infrastructure settings. The script itself can be found in here: [run.sh](run.sh)

### Running from sources
- run `git clone https://github.com/spolnik/JAlgoArena-Submissions` to clone locally the sources
- now, you can build project with command `./gradlew clean bootRepackage` which will create runnable jar package with app sources. Next, run `java -Dserver.port=5003 -jar build/libs/jalgoarena-auth-*.jar` which will start application
- there is second way to run app with gradle. Instead of running above, you can just run `./gradlew clean bootRun`

## Notes
- [Travis Builds](https://travis-ci.org/spolnik)

![Component Diagram](https://github.com/spolnik/JAlgoArena/raw/master/design/JAlgoArena_Logo.png)
