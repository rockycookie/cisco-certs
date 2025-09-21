# Data Ceneter SDN Topology: Spine and Leaf
# ACI (Cisco) Application Centric Infrastructure

## Background
- ACI in the data center
- Software-Defined Access (SDA) in enterprise campus
- Software-Defined WAN (SD-WAN) in the enterprise WAN

## Components
- Spine switch
    - Each spine switch must connect to every leaf switch
    - Spine switches cannot connect to each other
- Leaf switch
    - Each leaf switch must connect to every spine switch
    - Leaf switches cannot connect to each other
- Endpoint
    - Endpoints connect only to the leaf switches
- Endpoint group (EPG)
    - a group of endpoints
- APIC (Application Policy Infrastructure Controller)
    - |-> the software that serves as the centralized controller for ACI
    - has GUI, and software control API

### Endpoints
- connections to devices outside the data center
- physical servers running a native OS
- servers running virtualization software with numbers of VMs and containers
- Unified Computing System (UCS) server
    - a typical design with multiple leaf switches connecting to a single hardware endpoint
    - it contains: virtual switch + VMs
    - Cisco-proprietory

## How it works

### Intent-Based Networking (IBN) model
- it defines the policies and intent for which endpoints should be allowed to communicate and which should not
- then the controller determines what that means for this network at this moment in time

