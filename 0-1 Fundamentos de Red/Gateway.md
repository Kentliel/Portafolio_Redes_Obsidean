
Es el dispositivo que sabe salir a otras redes, en otras palabras; Es el dispositivo que conecta tu red local con el mundo exterior (Internet u otras redes).

- **Tecnicismo:** Nodo de red que sirve como punto de parada para datos que se dirigen a otros sistemas de red.
    
- **En jerga (La Puerta de Salida):** Es el "pasillo" para salir de tu casa. Cuando tu laptop quiere ir a Google, como Google no está en su "vecindario" (según la máscara), le manda el paquete al Gateway para que lo saque de ahí.

Ejemplo: MikroTik → 192.168.88.1

## Diagrama
```mermaid
graph TD
    Laptop --> MikroTik
    MikroTik --> Internet