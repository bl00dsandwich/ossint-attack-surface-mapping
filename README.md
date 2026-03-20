# Inteligencia de Fuentes Abiertas (OSINT) y Mapeo de Superficie de Ataque

La importancia de la inteligencia de fuentes abiertas (OSINT) en las pruebas de penetración radica en su capacidad para descubrir información pública que los atacantes podrían explotar sin necesidad de interaccción directa con el objetivo.

A través de técnicas OSINT, es posible descubrir datos críticos sobre:

* Infraestructura tecnológica
* Empleados y estructura organizativa
* Posibles vulnerabilidades expuestas

Este enfoque facilita la detección de riesgos como:

* Credenciales filtradas
* Activos mal configurados
* Fugas de información sensible

Además, garantiza una fase de reconocimiento más completa, permitiendo simular escenarios de ataque realistas dentro de un marco ético y legal. Como resultado, las organizaciones pueden anticiparse a amenazas y reforzar su postura de seguridad.

## OSINT sobre el nombre de dominio del objetivo
Esta sección se centra en la recopilación de OSINT relacionada con el nombre de dominio del objetivo mediante información disponible públicamente. Permite a los pentesters obtener detalles como subdominios, registros DNS, datos WHOIS, direcciones IP, direcciones de correo electrónico y servicios de acceso público, lo que proporciona información valiosa sobre la infraestructura del objetivo y posibles vectores de ataque.


### 🌐 Encontrar el dominio y los subdominios del objetivo 

La identificación del dominio y sus subdominios es un paso clave en pentesting, ya que permite descubrir la **superficie de ataque** y los distintos activos expuestos de una organización.  

Los subdominios suelen corresponder a aplicaciones independientes (muchas veces internas o menos securizadas), lo que los convierte en objetivos especialmente interesantes durante la fase de reconocimiento.

---

#### 🎯 Objetivo

Obtener una visión completa de:
- Activos expuestos  
- Infraestructura externa  
- Posibles puntos de entrada  

Esto permite realizar una evaluación de seguridad más completa y efectiva.

---

#### 🛠️ Herramientas principales

- **SubBrute**

  Fuente: https://github.com/TheRook/subbrute 

  Enumeración de subdominios mediante fuerza bruta y consultas DNS recursivas, incluso detectando subdominios ocultos o bloqueados.

  Uso: ```subbrute.py microsoft.com```

- **Nmap (dns-brute)**

  Fuente: https://nmap.org

  Permite descubrir subdominios y registros DNS (incluidos SRV) utilizando scripts NSE.

  Uso: ```nmap --script dns-brute www.objetivo.com```

- **dnsmap**

  Fuente: https://github.com/resurrecting-open-source-projects/dnsmap

  Identifica subdominios adicionales y bloques de IP asociados, ampliando la visibilidad de la infraestructura del objetivo.

  Uso: ```dnsmap objetivo.com```

- **Fierce**

  Fuente: https://github.com/mschwager/fierce 

  Herramienta de reconocimiento DNS enfocada en detectar subdominios, rangos de IP y configuraciones erróneas.

  Uso: ```fierce --domain objetivo.com```

- **Sublist3r**

  Fuente: https://github.com/aboul3la/Sublist3r 

  Enumeración OSINT de subdominios utilizando múltiples fuentes como motores de búsqueda y bases de datos públicas.

  Uso: ```python3 sublist3r.py -d objetivo.com -p 80```

- **Netcraft**

  Fuente: https://searchdns.netcraft.com 

  Plataforma que permite descubrir subdominios, incluidos aquellos no indexados o intencionadamente ocultos.

---

### 🔎 Identificación de dominios similares (Typosquatting)

Durante la fase de reconocimiento, es fundamental identificar **dominios similares o paralelos** al del objetivo. Estos pueden revelar intentos de **typosquatting**, donde usuarios son redirigidos a sitios maliciosos debido a errores tipográficos.

Ejemplos comunes incluyen:
- Variaciones de TLD (`.org`, `.net`, `.biz`, etc.)
- Errores tipográficos (`ysecurity.cm`)
- Alteraciones del dominio (`www-xsecurity.com`, `wwwxsecurity.com`)

---

#### 🎯 Objetivo

- Identificar dominios fraudulentos o sospechosos  
- Detectar posibles vectores de ataque  
- Proteger la marca y a los usuarios finales

---

#### ⚠️ Riesgos asociados

- Phishing y suplantación de identidad  
- Secuestro de tráfico web  
- Daño reputacional  
- Exposición a ataques dirigidos  

---

#### 🛠️ Herramienta recomendada

- **URLCrazy**
  
  Fuente: https://github.com/urbanadventurer/urlcrazy
  
  Genera variaciones de dominios para detectar:
  - Typosquatting  
  - Dominios maliciosos similares  
  - Posibles campañas de phishing

  Uso: ```urlcrazy -p objetivo.com```

---


