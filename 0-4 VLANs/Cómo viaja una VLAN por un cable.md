Las VLANs se identifican con un tag 802.1Q dentro del frame Ethernet.

## Diagrama
```mermaid
sequenceDiagram
    participant Host
    participant Switch
    Host->>Switch: Frame + VLAN tag (802.1Q)