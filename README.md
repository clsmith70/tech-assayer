# tech-assayer

An simple application written in Python to track IT Assets in a no-sql database with a web front-end and simplified enough to use existing Ansible collections to gather data and write records.  Inspired by the need for something simple that can be easily modified for any organizations needs.

## Initial object definitions

### Primary objects

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
        WirelessAdapter ..> Laptop
        WirelessAdapter ..> Desktop
        EthernetAdapter ..> Desktop
        EthernetAdapter ..> Server
        
        class Computer{
            +String serial_number
            +String name
            +String processor
            +String architecture
            +String memory_gb
            +String manufacturer
            +String boot_volume
            +List NetworkAdapter nic
            +List String additionalDisks
            +OperatingSystem os
            +List Application application
            -bool active
            -bool decommissioned
            
            +is_active()
            +is_decommissioned()
            +install_application()
            +uninstall_application()
        }

        class NetworkAdapter {
            +String macAddress
            +String? ipv4Address
            +String? ipv6Address
            +String link_speed
            +change_ip()
            +get_ip()
            +get_mac()
            +is_connected()
        }
```

### Secondary objects

```mermaid
    classDiagram
        note for Disk "Removing Disk class to simplify things"
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

        class Application {
            +String name
            +String version
            +String architecture
            +String manufacturer
        }
```

