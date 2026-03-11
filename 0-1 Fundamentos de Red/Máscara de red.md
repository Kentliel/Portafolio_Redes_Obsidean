
Define qué direcciones están “dentro” de tu red o otra manera de verlo, es lo que define qué parte de la IP es la "calle" (red) y qué parte es la "casa" (host).

- **Tecnicismo:** Código de 32 bits que delimita el ámbito de una red determinando qué bits de la IP pertenecen a la red y cuáles al host.
    
- **En jerga (La Valla del Jardín):** Te dice hasta dónde llega tu vecindario. Si tienes una máscara `/24` (255.255.255.0), significa que todos los que empiecen por `192.168.88.X` son tus vecinos directos.
    
- **Dato clave:** Si quieres hablar con alguien fuera de esa "valla", necesitas ayuda externa.

Ejemplo: 255.255.255.0 → /24

## Ejemplo en tu lab

192.168.88.0/24

## Relacionado
- [[IP]]
- [[Gateway]]