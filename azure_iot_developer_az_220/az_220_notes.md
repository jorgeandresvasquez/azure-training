# AZ 220 (Microsoft Azure IoT Developer)

## Arrchitecture of IoT
- an IoT solution involves two essential components:
  - A device-side (made up of individual devices) that acts as a data source.
  - A cloud-side that gathers data and provides resources for analyzing and managing that data.
- Core subsystems:
  - IoT Devices: The physical devices where our data originates.
  - Cloud Gateway: The Cloud Gateway provides a cloud hub for secure connectivity, telemetry, and event ingestion and device management (including command and control) capabilities.
  - User Interface and Reporting: The user interface for an IoT application can be delivered on a wide array of device types, in native applications, and browsers.
  - Stream Processing: Processes large streams of data records and evaluates rules for those streams.
  - Storage: Storage can be divided into warm path (data that is required to be available for reporting and visualization immediately from devices), and cold path (data that is stored longer term and used for batch processing).
  - Business Process Integration: Facilitates executing actions based on insights garnered from device telemetry data during stream processing. Integration could include storage of informational messages, alarms, sending email or SMS, integration with CRM, and more.
- Cross-cutting architectural needs
  - Security requirements; including user management and auditing, device connectivity, in-transit telemetry, and at rest security.
  - Logging and monitoring for an IoT cloud application is critical for determining health and for troubleshooting failures both for individual subsystems and the application as a whole.
  - High availability and disaster recovery, which is used to rapidly recover from systemic failures.
- 3 types of components:
  - Things: The physical objects, or things such as industrial equipment, devices, and sensors, that connect to the cloud persistently or intermittently.
  - Insights: The information collected by the things that's analyzed and turned into actionable knowledge either by people or AI.
  - Actions: The way people or systems respond to insights and connect them to their business, as well as the systems and tools.

## Azure Services in IoT

### IoT Central

- Very similar to IoT Hub but allows to build applications using Standardized Templates
- SaaS
- Out-of-the-box solutions with industry-specific app templates
- No deep technical knowledge required
- Built on top of the IoT Hub Service and 30+ other services

### Azure Sphere

- Set of components allowing you to build secure IoT applications
- Secure e2e IoT Solutions
  - Azure Sphere certified chips (microcontroller units - MCUs)
  - Azure Sphere OS based on Linux
  - Azure Security Service trusted device-to-cloud communication

### IoT Hub

- General
  - Allows for bidirectional communication between the cloud and IoT Devicess
  - PaaS
  - Programmable SDKs for popular languages
  - Multiple Protocols (HTTPSS, AMQP, MQTT)
- IoT Devices
  - Add new Device
- Connectivity
  - Private vs Public access
  - Private Endpoint

## Azure Stream Analytics

- Key Characteristics
  - SQL query language over stream of data
  - Out-of-the-box Azure integrations
  - Custom functions service
- How does it work
  1. Define Source
    - Input Type & Properties
    - Input Alias
  2. Define Output
    - Output Type & Properties
    - Output Alias
  3. Define Job SQL Query
- Supported Inputs
  - Blob Storage
  - IoT Hub
  - Event Hub
- Supports Reference Data Inputs from the following
  - Blob
  - SQL Database
- Supported Outputs
  - Blobs
  - Event Hubs
  - SQL Database
  - Service Bus
  - Synapse
  - Table Storage
  - Cosmos DB
  - Power BI
  - Azure Data Lake Storage
  - Functions

## IoT Edge
- Microcosmos of Azure
- Gateway for IoT devices
- The edgeHub modules send the data to Azure IoT Hub or Azure IoT Central by using advanced message queuing protocol (AMQP) or MQTT.
- Designed to be extensible via modules
- 

## Examples
- Raspberri PI Azure IoT Simulator
  - https://azure-samples.github.io/raspberry-pi-web-simulator/

## Industry Standards
- OPC UA

## Acronyms and Terms Definitions
- PLC:  Programmable logic controllers
- Historian:  A historian is a tool that records data from the control system
- AMQP:  The Advanced Message Queuing Protocol (AMQP) is an open standard application layer protocol for message-oriented middleware. The defining features of AMQP are message orientation, queuing, routing (including point-to-point and publish-and-subscribe), reliability and security.[1]
- MQTT:  MQTT (originally an initialism of MQ Telemetry Transport[a]) is a lightweight, publish-subscribe, machine to machine network protocol for Message queue/Message queuing service. It is designed for connections with remote locations that have devices with resource constraints or limited network bandwidth. It must run over a transport protocol that provides ordered, lossless, bi-directional connections—typically, TCP/IP.[1] It is an open OASIS standard and an ISO recommendation (ISO/IEC 20922).
- Modules can act as translators of protocols, filters, support AI modules to enrich and transform, etc.
- X.509 certs:  In cryptography, X.509 is an International Telecommunication Union (ITU) standard defining the format of public key certificates. X.509 certificates are used in many Internet protocols, including TLS/SSL, which is the basis for HTTPS, the secure protocol for browsing the web. They are also used in offline applications, like electronic signatures.

## Questions
- Pricing model for IoT hub? Once you provision the Scale Tier and Units do you commit yourself on a fixed cost per month even if you don't get any messages?
- Showcase 2 integration points?
- Why not using Azure Data Explorer as a Scalable Telemetry store for Time Series Analysis/?

## References
- https://esi.microsoft.com/landing
- Official Microsoft Learning Paths
  - https://learn.microsoft.com/en-us/certifications/exams/az-220?tab=tab-learning-paths
  - https://learn.microsoft.com/en-us/training/paths/create-azure-iot-services-azure-portal/?tab=tab-learning-paths
- Well architected IoT
  - https://learn.microsoft.com/en-us/azure/architecture/framework/iot/iot-overview
- Azure Stream Analytics Tutorial
  - https://www.youtube.com/watch?v=NbGmyjgY0pU&t=344s
- Azure IoT Edge
  - 
- Industrial IoT Patterns:
  - https://learn.microsoft.com/en-us/azure/architecture/guide/iiot-patterns/iiot-connectivity-patterns