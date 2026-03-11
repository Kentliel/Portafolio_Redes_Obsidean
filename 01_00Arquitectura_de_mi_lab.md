- - -
1. Arquitectura que estás usando ahora mismo

Tu red, simplificada, es esta:

Internet
   │
Router Movistar (NAT ISP)
   │
MikroTik L009 (router principal)
   │
Switch Netgear
   │
 ├── UniFi U7 (Access Point)
 │
 └── Laptop (RHEL + Podman + UniFi Controller)

Esto es lo que en redes se llama:

Arquitectura jerárquica de red pequeña (Small Enterprise / SOHO).

Tiene tres roles básicos:

Rol	Dispositivo

Edge / WAN	Router del ISP
Gateway / routing interno	MikroTik
Access layer	switch + AP



---

Cómo fluye el tráfico

Ejemplo: tu portátil abre una web.

Laptop
  │
  ▼
Switch
  │
  ▼
MikroTik (NAT)
  │
  ▼
Router ISP
  │
  ▼
Internet

El único dispositivo que hace routing real en tu red es el MikroTik.

El switch solo conecta dispositivos en capa 2.


---

2. Arquitectura de control (UniFi)

Además de la red, tienes un sistema de gestión.

UniFi Controller
                 │
        ┌────────┴────────┐
        │                 │
       AP               futuros AP

Esto se llama:

Arquitectura controller-based networking.

Los dispositivos no se configuran manualmente, sino desde un controlador central.

Esto es muy común en WiFi empresarial.

Ejemplos similares:

Fabricante	controlador

Cisco	WLC
Aruba	Aruba Central
UniFi	UniFi Controller



---

3. Tu arquitectura completa (nombre técnico)

Tu laboratorio mezcla tres cosas:

1️⃣ Red jerárquica

router → switch → access points


---

2️⃣ Software-defined management

El controlador gestiona dispositivos.


---

3️⃣ Infraestructura virtualizada

El controlador corre en un contenedor.


---

Si lo describiera técnicamente sería algo como:

Containerized network controller in a SOHO hierarchical network.


---

4. Conceptos base que necesitas dominar

Para entender todo lo que estás montando necesitas varios niveles de networking.

Voy a ordenarlos en el orden correcto.


---

Nivel 1 — Fundamentos de red

Estos son imprescindibles.

Conceptos:

IP

máscara de red

gateway

ARP

NAT


Ejemplo en tu red:

Laptop → 192.168.88.251
AP → 192.168.88.253
Gateway → 192.168.88.1

Tu laptop sabe:

si destino ≠ mi red
→ enviar al gateway


---

Nivel 2 — Switching (Layer 2)

Esto lo hace tu switch.

Funciones:

MAC learning

forwarding frames

broadcast domain


Ejemplo:

Laptop → AP

El switch no usa IP, usa MAC addresses.


---

Nivel 3 — Routing (Layer 3)

Esto lo hace el MikroTik.

El router decide:

¿dónde enviar el paquete?

Ejemplo:

192.168.88.0/24 → LAN
0.0.0.0/0 → ISP


---

Nivel 4 — NAT

Esto ya lo viste.

Convierte:

192.168.88.251

en

84.x.x.x

para Internet.


---

Nivel 5 — VLANs

Esto será tu siguiente paso.

Permite dividir una red física en varias redes lógicas.

Ejemplo:

VLAN 10 → Home
VLAN 20 → IoT
VLAN 30 → Guest

Todas pasan por el mismo cable.


---

Nivel 6 — Controladores de red

Aquí entra UniFi.

El controlador:

guarda configuración

gestiona APs

provisiona cambios


Pero no enruta tráfico.


---

Nivel 7 — Virtualización (contenedores)

Tu controlador no está instalado en Linux directamente.

Está dentro de un container.

Esto permite:

aislar servicios

desplegar rápido

reproducir entornos



---

5. Algo importante que debes entender pronto

Tu red tiene dos planos diferentes.


---

Plano de datos (data plane)

Aquí fluye el tráfico real.

cliente
   │
AP
   │
switch
   │
router
   │
internet


---

Plano de control (control plane)

Aquí se gestionan dispositivos.

controller
     │
     ▼
AP configuration

El controlador no pasa tráfico de usuarios.

Solo configura.

Esto es clave para entender redes modernas.


---

6. Qué tipo de laboratorio estás construyendo

Sin darte cuenta estás construyendo algo muy parecido a:

un laboratorio de network engineering.

Con herramientas reales:

componente	usado en empresas

router	MikroTik / Cisco
switch	L2 switch
AP	WiFi empresarial
controller	SDN management
containers	infraestructura moderna



---

7. Qué vas a aprender si sigues con este lab

Este mismo laboratorio puede enseñarte:

1️⃣ VLAN segmentation
2️⃣ trunk ports
3️⃣ WiFi enterprise
4️⃣ firewall rules
5️⃣ routing interno
6️⃣ container networking
7️⃣ monitoring de red

Es básicamente un mini datacenter doméstico.


---

8. El siguiente concepto importante

Antes de que hagas VLANs necesitas entender algo muy clave:

la diferencia entre:

access port
vs
trunk port

porque eso es lo que conecta MikroTik ↔ switch ↔ UniFi.