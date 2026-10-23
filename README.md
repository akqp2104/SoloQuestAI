# SoloQuestAI

Herramienta para dirigir campañas de Dungeons & Dragons en solitario con ChatGPT y conservar su continuidad entre sesiones y conversaciones.

> Proyecto en fase de definición y preparación. Las funcionalidades descritas representan el comportamiento previsto y todavía no están implementadas.

## El problema

Jugar a Dungeons & Dragons en solitario con ChatGPT permite disfrutar de una campaña sin reunir un grupo, pero mantener una aventura larga requiere gestionar información que cambia constantemente: fichas, recursos, decisiones, personajes, pistas y acontecimientos.

Cuando esa información queda repartida entre conversaciones y documentos, la persona que juega debe comprobar qué sigue vigente, corregir contradicciones y trasladar el contexto al comenzar otra conversación. También necesita distinguir lo que sabe su personaje de los secretos que conoce el director de juego o de las posibilidades que todavía no se han confirmado.

Esta gestión interrumpe la partida y dificulta confiar en que las decisiones y sus consecuencias se conservarán durante toda la campaña.

## Objetivo

SoloQuestAI busca reducir ese trabajo manual mediante una integración con ChatGPT que permita consultar las fuentes de la campaña, registrar los cambios producidos durante el juego y recuperar el estado necesario para continuar.

ChatGPT actuará como director de juego: narrará las escenas, interpretará personajes y resolverá las situaciones con las fuentes disponibles. La herramienta proporcionará operaciones controladas para consultar y actualizar la información persistente.

La persona usuaria conservará el control sobre las decisiones de su protagonista y las modificaciones que requieran su intervención.

## Para quién está pensado

El desarrollo inicial está orientado a mi uso personal como jugadora de D&D en solitario con ChatGPT.

Parte de una necesidad que encuentro al jugar: poder centrarme en la aventura sin reconstruir manualmente las fichas y la continuidad cada vez que retomo una campaña.

Los manuales y materiales necesarios serán aportados por la persona usuaria y se mantendrán separados del código del proyecto.

## Primera versión jugable

El primer producto mínimo viable partirá de una campaña preparada manualmente y buscará permitir:

- Consultar la configuración y las fuentes habilitadas de la campaña.
- Jugar mediante conversación con ChatGPT como director de juego.
- Resolver y registrar tiradas, acontecimientos y cambios en las fichas.
- Conservar los recursos y la progresión del protagonista.
- Distinguir hechos confirmados, asuntos pendientes y conocimiento por perspectiva.
- Pausar, reanudar y cerrar sesiones.
- Continuar en otra conversación recuperando el estado guardado.

Las mecánicas y los casos de prueba concretos se delimitarán antes de implementar esta versión.

## Desarrollo posterior

Tras validar el ciclo de jugar, guardar y continuar, las siguientes entregas abordarán:

- Creación y configuración de campañas mediante conversación.
- Gestión de varias campañas.
- Cambios permanentes con comprobaciones de coherencia.
- Desenlaces y campañas derivadas de un mismo mundo.
- Validación del alcance y preparación de una versión personal estable.

La interfaz gráfica se plantea como una ampliación posterior. El multijugador, los mapas tácticos, las automatizaciones autónomas y la distribución pública quedan fuera del alcance inicial.

## Enfoque técnico

Las decisiones iniciales son:

- **Python** para el servidor MCP y las operaciones de la herramienta.
- **Markdown** para la skill y las instrucciones de dirección.
- **TypeScript** para una posible interfaz gráfica futura.

El almacenamiento y el acceso a las fuentes se decidirán mediante una prueba técnica de integración y persistencia.

## Estado y planificación

El proyecto se desarrolla de forma incremental, utilizando issues para definir el trabajo, milestones para agrupar entregas y un tablero Kanban para su seguimiento.

La planificación provisional comprende:

| Milestone | Resultado previsto |
| --- | --- |
| M0 | Definición, planificación y preparación del proyecto. |
| M1 | Integración con ChatGPT y persistencia verificadas. |
| M2 | Primer PMV: jugar, guardar y continuar una campaña. |
| M3 | Creación y configuración de campañas. |
| M4 | Gestión de varias campañas. |
| M5 | Cambios permanentes y coherencia. |
| M6 | Desenlaces y campañas derivadas. |
| M7 | Validación del alcance y versión personal estable. |

El alcance de las entregas podrá ajustarse según los resultados técnicos y la experiencia de uso.

## Documentación y seguimiento

- [Requisitos del producto](docs/PRD.md).
- [Milestones](https://github.com/akqp2104/SoloQuestAI/milestones).
- [Issues](https://github.com/akqp2104/SoloQuestAI/issues).
- [Tablero](https://github.com/users/akqp2104/projects/1).

## Materiales de juego

Este repositorio no incluye manuales comerciales, credenciales ni datos privados de campañas.

SoloQuestAI es un proyecto personal independiente, sin afiliación con Wizards of the Coast.