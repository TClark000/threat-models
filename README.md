# Threat Model | Flow & Attack Tree Diagram | Payment Process
> [Secure Transaction Hackathon](https://www.meetup.com/womeninappsec/events/274279132/) hosted by [OWASP WIA, Diversity and Inclusion Committee](https://owasp.org/www-committee-wia/)


## Table of contents
* [General Info](#general-info)
* [Threat Models](#threat-models)
* [Technologies](#technologies)
* [Setup](#setup)
* [Code Examples](#code-examples)
* [Status](#status)

## General Info
[OWASP Threat Model Cookbook Project](https://github.com/OWASP/threat-model-cookbook#readme) is collating threat model examples.  

Here I have created threat models for an online payment process.  Flow, sequence and attack tree diagrams cover the initial steps of an online payment process.  These initial steps cover the payment from the customer -> customer client (home pc) -> merchant -> stripe.

The flow diagram are created with the python threat modeling framework [pytm](https://github.com/izar/pytm/) with diagrams generated as [Dot](https://graphviz.gitlab.io/) and [PlantUML](https://plantuml.com/).

The attack tree is generated with [PlantUML](https://plantuml.com/).

The threat models are based on a [stripe](https://stripe.com/docs/payments/cards/overview) payment.  

## Threat Models

### Flow Diagram

  ![Payment Flow Diagram](./Flow%20Diagram/payment/img/payment_online.png)

### Sequence Diagram

  ![Payment Seq Diagram](./Flow%20Diagram/payment/img/payment_online_seq.png)

### Attack Tree Diagram

  ![Payment Attack Tree Diagram](./Attack%20Tree/payment/payment_online.png)

## Technologies
* Python 3.9.0
* Java 15.0.1 2020-10-20
* Graphviz version 2.44.1 (20200629.0846)
* plantuml.jar, PlantUML version 1.2020.20

## Setup
Installations steps provided by [pytm](https://github.com/izar/pytm/) and [PlantUML](https://plantuml.com/starting)

To test the installation of Graphviz, use the command:

  ```
    java -jar plantuml.jar -testdot
  ```

## Code Examples

Check default attributes of a pytm element, ExternalEntity:
  ```
    python payment_online.py --describe ExternalEntity
  ```
Shown are the commands to create the threat model for the flow and sequence diagram:

  ```
    python payment_online.py --dfd | dot -Tpng -o ./img/payment_online.png
    python payment_online.py --seq | java -Djava.awt.headless=true -jar plantuml.jar -tpng -pipe > ./img/payment_online_seq.png
  ```
The attack tree is created by running the command or run the code on the [online server](http://www.plantuml.com/plantuml):

```
  java -jar plantuml.jar ./payment_online.plantuml
  java -jar plantuml.jar ./payment_online.plantuml -tsvg
```

Describing attributes of Merchant Web Server, payment_online.py, for the Flow Diagram:

```
  merchant_web = Server("Merchant Web Server")
  merchant_web.inBoundary = Merchant_Web
  merchant_web.OS = "Ubuntu"
  merchant_web.isHardened = True
  merchant_web.onAWS = True
```

## Status
Project is: _in progress_
