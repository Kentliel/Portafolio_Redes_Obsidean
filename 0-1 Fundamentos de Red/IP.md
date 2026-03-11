
La IP(Internet Protocol) identifica un dispositivo en la red.

- **Tecnicismo:** Es una etiqueta numérica asignada a cada dispositivo conectado a una red que utiliza el protocolo IP para comunicación.
    
- **En jerga (DNI de Red):** Es la "dirección de tu casa" dentro de la red. Sin ella, los paquetes de datos no saben a dónde ir.
## Ejemplo

- Laptop: 192.168.88.251
- AP: 192.168.88.253
- Gateway: 192.168.88.1

## Diagrama

```mermaid
graph LR
    Laptop -->|"192.168.88.251"| Switch
    AP -->|"192.168.88.253"| Switch
    Switch -->|"192.168.88.1"| MikroTik

