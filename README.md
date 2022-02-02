<h1 align="center" style="display: block; font-size: 2.5em; font-weight: bold; margin-block-start: 1em; margin-block-end: 1em;">
  <br><br><strong>Find number of squares in a matchstick grid
</strong>
</h1>

![Latest release](https://img.shields.io/github/v/release/aregtech/areg-sdk?label=%20%F0%9F%93%A3%20Latest%20release&style=flat&logoColor=b0c0c0&labelColor=363D44)

---

<!-- markdownlint-disable -->
## Project Status 
<table class="no-border">
  <tr>
    <!--<td><img src="https://github.com/aregtech/areg-sdk/actions/workflows/c-cpp.yml/badge.svg" alt="C++ compiltation"/></td>-->
    <td><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="Sonarqube"/></td>
    <td><img src="https://img.shields.io/badge/Codeforces-445f9d?style=for-the-badge&logo=Codeforces&logoColor=white" alt="Sonarqube"/></td>
    <td><img src="https://github.com/aregtech/areg-sdk/actions/workflows/codeql-analysis.yml/badge.svg" atl="CodeQL"/></td>
  </tr>
  <tr>
    <td><img src="https://img.shields.io/badge/Solution-Python-blue.svg?style=flat&logo=Python&logoColor=b0c0c0&labelColor=363D44" alt="Python solution"/></td>
    <td><img src="https://img.shields.io/badge/Environment-Jupyter%20notebook-orange"/></td>
    <td><img src="https://img.shields.io/badge/CPU-x86%20%7C%20x86__64%20%7C%20arm%20%7C%20aarch64-blue?style=flat&logo=amd&logoColor=b0c0c0&labelColor=363D44" alt="CPU Architect"/></td>
  </tr>
</table>

---

## Introduction[![](./docs/img/pin.svg)](#introduction)

**AREG SDK** is a developer-friendly, interface-centric real-time asynchronous communication engine to enable [distributed-](https://en.wikipedia.org/wiki/Distributed_computing) and [mist-](https://csrc.nist.gov/publications/detail/sp/500-325/final)computing, where connected Things interact and provide services, as if they act like thin distributed servers.


---

## Table of contents[![](./docs/img/pin.svg)](#table-of-contents)
1. [Motivation](#motivation)
2. [More than embedded](#more-than-embedded)
3. [Composition](#composition)
4. [Software build](#software-build)
5. [Software integration](#software-integration)
   - [Multicast router](#mulitcast-router)
   - [Logging service](#logging-service)
   - [Development](#development)
6. [Use cases and benefits](#use-cases-and-benefits)
   - [Distributes solutions](#distributed-solution)
   - [Driverless devices](#driverless-devices)
   - [Real-time solutions](#real-time-solutions)
   - [Digital twin](#digital-twin)
   - [Simulation and test automations](#simulation-and-test-automations)
7. [Examples](#examples)
8. [Licensing](#licensing)
9. [Call for action](#call-for-action)

---

## Motivation[![](./docs/img/pin.svg)](#motivation)

![Alt text](https://github.com/kwyip/find-number-of-squares-in-a-matchstick-grid/blob/main/screenshot_1.png) 

![Alt text](https://github.com/kwyip/find-number-of-squares-in-a-matchstick-grid/blob/main/screenshot_2.png) 


Traditionally, devices are connected clients to stream data to the cloud or fog servers for further processing.
<br><br><a href="/docs/img/mist-network.png"><img src="/docs/img/mist-network.png" alt="IoT-to-Cloud (Nebula) network" style="width:70%;height:70%"/></a><br><br>
Since data is generated and collected at the edge of the network (mist network), it makes sense to change the role of connected Things and provide network accessible (_Public_) services directly on devices. This extends _Cloud_ to the extreme edge and it is a good foothold for robust solutions such as:
* _Increase data privacy_, which is an important factor for sensitive data.
* _Decrease data streaming_, which is a fundamental condition to optimize network communication.
* Develop _autonomous, intelligent and self-aware devices_ by providing network services directly in the environment of data origin.

---
