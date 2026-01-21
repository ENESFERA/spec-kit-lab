# 🧙‍♂️ Un juego de aventuras en texto

La gesta que nos aguarda encierra **tres grandes desafíos**, dignos de bardos y crónicas futuras.

Aventureras y aventureros que aquí os congregáis bajo el mismo estandarte, habréis de dividiros en **dos compañías**.

Antes del **primer reto**, se lanzará una moneda para decidir qué compañía podrá invocar el poder de **GitHub Copilot** durante el desafío inicial.

En el **segundo desafío**, el destino se invertirá:
- Quien antes no tuvo ayuda, ahora la tendrá.
- Quien la tuvo, deberá prescindir de ella.

Para el **tercer y último desafío**, **ambas partes** podrán hacer uso de GitHub Copilot.

Entre desafío y desafío, habrá tiempo para que los espíritus reposen y las mentes se preparen.

---

## 🎲 Reglas

---

## 🏰 Primer Desafío  
### La Biblioteca al Final del Mundo

Habéis de forjar un **API REST** valiéndose del grimorio conocido como **Swagger (OpenAPI)**, en su versión **3.0.1**.  
Este servirá de **backend** para vuestra aventura.

El hechizo podrá escribirse en cualquiera de los siguientes lenguajes de poder:
- **C#**
- **TypeScript**

Serán tenidos en alta estima aquellos equipos que muestren esmero en las siguientes virtudes:

- Permitir disfrutar de una **aventura sencilla por texto**
- Cuidar los **aspectos de seguridad**
- Claridad en los **pergaminos** (documentación del API)
- Observancia de las **buenas prácticas** del desarrollo de APIs

---

### 🔧 Funcionalidades mínimas

- **Inicializar una aventura**
- **Gestión de personajes**
  - Creación / edición / obtención
  - Atributos: FUE / DEX / INT / CON / CHA
  - Modificadores calculados
  - Snapshots y versionado
- **Sistema de dados**
  - Soporte para expresiones tipo `2d6`
- **Combate básico por turnos**
  - NPCs / enemigos
  - Estados simples: agresivo / defensivo / huir
  - Resolución de turnos usando el motor de dados
- **Inventario**
  - Ítems apilables o equipables
  - Loot tables
- **Misiones multi-etapa**
  - Progreso
  - Condiciones de éxito / fracaso
  - Persistencia del estado del mundo
- **Seguridad mínima**
  - Autenticación básica (token o JWT)
  - Control de permisos
- **Tests y documentación**
  - Pruebas unitarias para:
    - Motor de dados
    - Cálculo de modificadores
    - Motor de escenas
  - Documentación mínima de los recursos

---

## 🗣️ Segundo Desafío  
### La Voz de Quien Narra

Una vez forjado y encendido el API REST, toca practicar las artes de su invocación.

Habéis de erigir un **frontend**, con la tecnología que vuestro saber dicte, que permita:
- Llamar al API REST
- Emprender una **aventura por texto**, como si de un pergamino interactivo se tratase

No es necesario que sea complejo ni visualmente impactante.  
Basta con que cumpla su cometido con nobleza.

Se valorará especialmente:
- La atención a la **seguridad**
- La claridad en los **pergaminos** (documentación del código)

---

## ☁️ Tercer Desafío  
### El Plano del Reino

Habéis de invocar el arcano arte de la **Infraestructura como Código**, empleando el secreto conocido como **Terraform**.

Vuestra labor será desplegar recursos en el reino de la nube de **Azure**, siguiendo los dictados de:
- Módulos
- Estados
- Declaraciones

No ha de ser algo complejo ni visualmente impactante.  
Basta con que cumpla su cometido con nobleza.

Se valorarán especialmente los códices que demuestren dominio en:

- 🔐 Seguridad de los despliegues
- 📜 Claridad en la documentación
- 🛠️ Fidelidad a las buenas prácticas del gremio