# tech-assayer

An simple application written in Python to track IT Assets in a no-sql database with a web front-end and simplified enough to use existing Ansible collections to gather data and write records.  Inspired by the need for something simple that can be easily modified for any organizations needs.

## Object definitions

```mermaid
    classDiagram
        Laptop <|-- Computer
        Desktop <|-- Computer
        Server <|-- Computer
        VirtualServer <|-- Server
        PhysicalServer <|-- Server
        Server : +String location
        Laptop : +String size
        WirelessAdapter <|-- NetworkAdapter
        EthernetAdapter <|-- NetworkAdapter
        
        class Computer{
            +String processor
            +String memory_gb
            +String manufacturer
            +Disk boot_volume
            +List NetworkAdapter nic
            +List Disk additionalDisks
            +OperatingSystem os
            +is_active()
            +is_decommissioned()
        }

        class NetworkAdapter {
            +String macAddress
            +String? ipv4Address
            +String? ipv6Address
            +change_ip()
            +get_ip()
            +get_mac()
        }

        class Disk {
            +String capacity
            +String format
            +String interface
        }

        class OperatingSystem {
            +String name
            +String version
            +DateTime endOfSupport
            +DateTime endOfLife
            +String manufacturer
        }
```

