# Decisiones técnicas iniciales

## Propósito

Este documento recoge las decisiones técnicas de SoloQuestAI, sus motivos y las cuestiones que deben validarse antes de implementar el producto. Completa el [PRD](PRD.md), sin sustituir sus requisitos ni duplicar el backlog.

El alcance inicial es personal y conversacional. La interfaz gráfica y la distribución pública no condicionan la primera entrega jugable.

Las decisiones se identifican mediante DTxxx para poder referenciarlas desde issues y PR. «Acordada» significa elegida para el proyecto; no implica que esté implementada ni validada. Los cambios posteriores deben conservar el motivo de la revisión.

## Resumen

| ID | Decisión o cuestión | Estado | Trabajo relacionado |
| --- | --- | --- | --- |
| DT001 | Python para servidor y lógica | Acordada | #8 |
| DT002 | TypeScript para una interfaz futura | Acordada para una ampliación posterior | Fuera del PMV |
| DT003 | Integración personal con skill y servidor MCP | Propuesta pendiente de validación en el entorno real | #8, #9, #14 |
| DT004 | Separar dirección narrativa y operaciones controladas | Acordada; contratos por concretar | #8–#14 y HU de M2 |
| DT005 | Elegir almacenamiento y referencia del estado | Pendiente | #10 |
| DT006 | Definir formatos y acceso a fuentes | Pendiente | #7, #10, M2 |
| DT007 | Separar repositorio y datos privados | Acordada | #8, #10, #16 |
| DT008 | GitHub Flow y Conventional Commits | Acordada | #15, #16 |
| DT009 | pre-commit y Commitizen para hooks y mensajes | Acordada | #16 |
| DT010 | Comprobaciones de documentación, Python y CI | Acordada; configuración gradual | #8, #16 |
| DT011 | Versiones, dependencias y ejecución reproducible | Criterio acordado; herramientas concretas pendientes | #8, #16 |
| DT012 | Integridad del estado y recuperación ante errores | Garantías acordadas; diseño y límites pendientes | #11–#14 |

## DT001 — Python para el servidor y la lógica

**Estado:** acordada.

**Decisión:** utilizar Python para el servidor MCP y las operaciones de la herramienta.

**Motivo:** permite desarrollar la lógica del servidor y mantener abierta la posibilidad de procesar documentos y experimentar con recuperación de información dentro del mismo entorno. La elección no implica incorporar modelos locales ni una infraestructura de aprendizaje automático.

**Consecuencias:** el proyecto Python incluirá operaciones tipadas, validación de entradas y pruebas de comportamiento. No se incorporará un segundo servidor en TypeScript sin una necesidad concreta.

**Pendiente:** elegir versión compatible de Python, SDK, gestor de dependencias, estructura mínima y mecanismo de ejecución en #8. Las versiones se comprobarán al configurar el entorno.

## DT002 — TypeScript para una interfaz futura

**Estado:** acordada para una ampliación posterior.

**Decisión:** utilizar TypeScript si se incorpora la interfaz gráfica prevista.

**Motivo:** separar la elección del servidor de la de la interfaz y disponer de tipado en la futura parte web.

**Consecuencias:** el PMV no necesita interfaz ni framework de frontend. La comunicación entre componentes requerirá contratos explícitos; utilizar lenguajes distintos no permite compartir tipos de forma automática.

**Pendiente:** decidir entorno de visualización, framework y contratos cuando se prepare esa entrega. No se eligen ahora React, una biblioteca de componentes ni un sistema de generación de clientes.

## DT003 — Integración personal con ChatGPT

**Estado:** propuesta pendiente de validación técnica.

**Propuesta:** combinar instrucciones de dirección en una skill escrita en Markdown con un servidor MCP en Python, dentro de la integración personal denominada «plugin» en la planificación inicial.

**Motivo:** mantener la interacción en ChatGPT y proporcionar operaciones explícitas para acceder al estado persistente.

**Hipótesis:** la cuenta y el cliente utilizados permitirán conectar el servidor, descubrir sus herramientas y recuperar el mismo estado desde otra conversación.

**Límite:** esta hipótesis no acredita disponibilidad ni compatibilidad actuales. «Plugin personal» describe la propuesta del proyecto, no garantiza un formato de instalación o una capacidad concreta de la cuenta. El mecanismo para cargar las instrucciones y conectar el servidor debe verificarse expresamente.

**Pendiente en M1:** comprobar soporte real, forma de conexión, transporte, ejecución local o alojada, necesidad de conectividad, acceso privado y costes. No se presupone acceso directo desde ChatGPT a archivos del equipo ni a un proceso local.

**Criterio de decisión:** la conexión debe funcionar de forma reproducible en el entorno personal previsto. Si falla, se documentará el impedimento y se revisará la integración antes de construir funciones que dependan de ella.

**Issues:** #8, #9 y #14.

## DT004 — Responsabilidades de la skill y del servidor

**Estado:** acordada; contratos concretos pendientes.

| Componente | Responsabilidad prevista |
| --- | --- |
| Skill e instrucciones de dirección | Orientar narración, interpretación de intenciones, consulta de fuentes, perspectivas y tratamiento conversacional de conflictos. |
| ChatGPT como DM | Narrar y proponer resoluciones, solicitar las decisiones de la jugadora e invocar las operaciones disponibles. |
| Servidor | Validar entradas y ámbito de acceso, ejecutar operaciones, conservar estado y devolver resultados comprobables. |

**Motivo:** las instrucciones narrativas no deben ser el único mecanismo que impida una escritura inválida o fuera de alcance.

**Consecuencias:** el servidor no expondrá una edición arbitraria de archivos como sustituto de operaciones limitadas. Una respuesta del modelo no se considerará evidencia de guardado; se utilizará el resultado de la operación.

**Distinciones:** validar una entrada no demuestra por sí solo que la jugadora haya autorizado un cambio. Tampoco se exige convertir todas las reglas de D&D en código: cada historia concretará los cálculos, comprobaciones y consultas necesarios.

La separación de conocimiento tiene una dimensión narrativa y otra de acceso y presentación de información. No se dará por resuelta únicamente mediante instrucciones; se comprobará con casos de secretos y consultas en M2.

**Pendiente:** contratos de entrada y salida, operaciones disponibles y reparto concreto de cálculos para cada incremento.

## DT005 — Almacenamiento y referencia del estado

**Estado:** pendiente.

**Necesidad:** conservar el estado entre sesiones, conversaciones y reinicios del servidor, sin mantener copias divergentes que puedan actualizarse de manera independiente.

**Decisión de M1:** comparar brevemente dos alternativas razonables para los datos ficticios de #7 y elegir la más sencilla que cumpla la prueba. Archivos, almacenamiento estructurado y una solución mixta son opciones por evaluar, no decisiones adoptadas.

**Criterios de comparación:** acceso desde el servidor, consistencia de las escrituras, recuperación, coste, mantenimiento, facilidad de uso y adecuación a los documentos del PRD.

**Resultado esperado:** alternativa elegida con justificación, referencia autorizada del estado para lectura y escritura, limitaciones conocidas y procedimiento para restaurar los datos de prueba.

**Límite:** una prueba pequeña no demuestra rendimiento ni calidad de recuperación con campañas extensas. Esa evaluación se realizará después con una muestra representativa.

**Issue:** #10.

## DT006 — Formatos y acceso a fuentes

**Estado:** pendiente.

**Necesidad:** representar configuración, fichas, sesiones, transcripciones, canon, cronología y perspectivas sin perder las distinciones del dominio.

**Propuesta de trabajo:** empezar con un formato mínimo para la prueba de M1. Debe distinguir identificación de campaña, versión del formato y revisión del estado. No se presentará como modelo definitivo de todos los documentos.

La organización por carpetas y pestañas del PRD expresa la organización lógica prevista; los formatos y su representación física siguen pendientes. Los documentos legibles y el estado estructurado, si coexisten, deberán tener una relación explícita que evite fuentes de verdad duplicadas.

**Acceso a reglas:** respetar las fuentes habilitadas y sus ediciones. No se presupone que cargar un manual implique que ChatGPT o el servidor puedan consultar correctamente todo su contenido.

**Pendiente:** extracción de texto, tratamiento de documentos escaneados, búsqueda, referencias de procedencia y selección de contenido para cada consulta. No se eligen todavía OCR, embeddings, base vectorial ni un servicio documental.

**Validación:** comprobar con las fuentes y casos de M2 que se recupera información pertinente y se comunica cuando no puede verificarse una regla. Si esta capacidad requiere investigación adicional, se crea una tarea técnica antes de la HU dependiente.

**Issues:** #7, #10 y preparación de M2.

## DT007 — Código versionado y datos privados

**Estado:** acordada.

| En el repositorio | En el espacio privado de datos |
| --- | --- |
| Código, documentación y configuración de herramientas. | Manuales y suplementos aportados por la jugadora. |
| Pruebas y datos ficticios reproducibles. | Campañas reales, fichas y transcripciones privadas. |
| Ejemplos de configuración sin credenciales. | Credenciales y valores locales que permitan acceder a servicios. |

**Motivo:** mantener el repositorio utilizable y revisable sin publicar materiales privados ni secretos.

**Consecuencias:** las pruebas utilizarán campañas ficticias separadas de las reales. La configuración local sensible quedará excluida de Git y los ejemplos documentarán qué debe aportar la persona usuaria.

**Límite:** `.gitignore` evita añadir ciertos archivos accidentalmente, pero no sustituye la revisión de los cambios ni retira secretos ya publicados. El ámbito privado concreto depende del almacenamiento elegido.

**Issues:** #8, #10 y #16.

## DT008 — Flujo de contribución y mensajes de commit

**Estado:** acordada.

**Decisión:** ramas cortas por cambio, PR hacia `main`, revisión de criterios y Squash and merge. Los milestones agrupan entregas; no requieren ramas permanentes propias.

Los commits y los títulos de PR seguirán Conventional Commits. El título utilizado para el squash se revisará antes de integrar el cambio. Los nombres de rama relacionarán tipo de trabajo, número de issue y propósito.

**Motivo:** conservar un historial comprensible y trazabilidad entre necesidad, cambio y validación.

**Consecuencias:** la revisión individual será explícita; no se exigirá una aprobación externa ficticia. Las convenciones operativas y plantillas se mantendrán en `CONTRIBUTING.md`, evitando duplicarlas aquí.

**Issues:** #15 y #16.

## DT009 — Gestión de hooks y validación de mensajes

**Estado:** acordada.

**Decisión:** utilizar pre-commit como único gestor de Git hooks y Commitizen para Python con `cz_conventional_commits` para validar mensajes en `commit-msg`.

**Motivo:** mantener esta parte del entorno alineada con Python y evitar herramientas solapadas para ejecutar hooks o validar los mismos mensajes.

**Consecuencias:** no se incorporan Husky, lint-staged ni Commitlint para estas funciones. El asistente de redacción de Commitizen es opcional; se puede seguir utilizando `git commit`.

La instalación debe activar expresamente los hooks necesarios. Las comprobaciones locales se complementarán con CI, ya que un hook puede omitirse. Las reglas exactas y sus posibles restricciones adicionales se documentarán con la configuración.

**Issue:** #16.

## DT010 — Calidad y comprobaciones automatizadas

**Estado:** herramientas acordadas; implementación gradual pendiente de sus issues.

| Etapa | Herramienta | Finalidad |
| --- | --- | --- |
| M0 | EditorConfig | Convenciones básicas de edición por tipo de archivo. |
| M0 | markdownlint-cli2 | Comprobaciones de Markdown. |
| M0 | GitHub Actions | Verificar Markdown, mensajes de commits de PR y títulos de PR. |
| M1 | Ruff | Lint y formato de Python. |
| M1 | mypy | Comprobación estática de tipos de Python. |
| M1 | pytest | Pruebas de comportamiento del servidor y la persistencia. |

**Motivo:** detectar errores de forma reproducible y mantener comprobaciones coherentes entre local y CI.

**Consecuencias:** markdownlint-cli2 introduce un requisito de Node.js para las herramientas de documentación, aunque el servidor sea Python. Ruff será la herramienta inicial de lint y formato de Python; no se añaden herramientas redundantes sin una necesidad concreta.

Los hooks deben ser rápidos. CI ejecutará las comprobaciones pertinentes al código existente y las pruebas relevantes para cada cambio. Las validaciones automáticas no sustituyen la revisión de requisitos ni las pruebas conversacionales con ChatGPT.

**Pendiente:** versiones, reglas, comandos y workflows. Las comprobaciones requeridas y las restricciones de integración se configurarán según las capacidades del repositorio, documentando cualquier limitación.

**Issues:** #16 y #8.

## DT011 — Dependencias y ejecución reproducible

**Estado:** criterio acordado; mecanismo pendiente.

**Decisión:** declarar dependencias y versiones de forma que otra instalación pueda reproducir el entorno de desarrollo y las pruebas.

**Motivo:** evitar que el funcionamiento dependa de paquetes instalados manualmente sin registrar.

**Pendiente:** elegir gestor de dependencias Python, mecanismo de fijación de versiones, versión de Node.js para las herramientas y versión compatible del SDK MCP. No se adopta todavía uv, Poetry u otro gestor por el mero hecho de aparecer como alternativa.

Los pasos de instalación y ejecución se documentarán al validarse. Tampoco se decide ahora utilizar contenedores, un proveedor de alojamiento o una base de datos remota.

**Issues:** #8 y #16.

## DT012 — Integridad y recuperación del estado

**Estado:** garantías necesarias acordadas; solución técnica y límites pendientes.

**Necesidades que condicionan el diseño:**

- Un fallo de escritura no corrompe el último estado válido.
- Un reintento no duplica acontecimientos, recursos ni XP.
- Una actualización basada en una revisión obsoleta se rechaza sin sobrescribir silenciosamente cambios posteriores.
- La herramienta distingue lo guardado, lo confirmado pendiente de guardar y las propuestas todavía no aceptadas.
- Un cierre incompleto no se presenta como completado.
- Las operaciones fuera del ámbito autorizado no modifican datos.

**Motivo:** la continuidad requiere que el estado guardado y la respuesta conversacional coincidan en lo que se ha aplicado realmente.

**Pendiente:** forma de agrupar cambios relacionados, identificación de operaciones, revisiones y recuperación. Se elegirán según el almacenamiento validado, sin fijar aquí transacciones, archivos auxiliares o una estructura de base de datos.

**Límite importante:** sobrevivir a un reinicio con lo ya guardado no demuestra que se puedan recuperar cambios que nunca llegaron a persistirse. La garantía de conservación de estos cambios y el caso en que tampoco pueda guardarse un registro pendiente siguen abiertos en el PRD. Deben resolverse y validarse antes de presentar ese comportamiento como disponible.

**Issues:** #11–#14; sección 9 del PRD.

## Prueba técnica de M1

### Preguntas que debe resolver

| Pregunta | Evidencia esperada |
| --- | --- |
| ¿La cuenta y el cliente permiten la integración propuesta? | ChatGPT descubre e invoca la herramienta de diagnóstico. |
| ¿Cómo se cargan las instrucciones de dirección? | Mecanismo identificado y límites documentados; no se asume soporte de instalación. |
| ¿Cómo se limita el acceso al servidor? | Mecanismo documentado y comprobaciones de operaciones autorizadas y rechazadas. |
| ¿Qué almacenamiento permite el recorrido mínimo? | Comparación de alternativas y decisión justificada. |
| ¿Se consulta la campaña correcta? | Lectura con valores conocidos y errores para identificadores inexistentes o no autorizados. |
| ¿Se guarda un cambio controlado? | Valores anteriores y posteriores conocidos y operación identificable. |
| ¿La continuidad depende de la conversación anterior? | Otra conversación recupera el cambio sin copiar manualmente los datos. |
| ¿El estado depende de la memoria del proceso? | Reiniciar el servidor no pierde lo guardado. |
| ¿Los fallos o reintentos producen efectos incorrectos? | Pruebas reproducibles de fallo de escritura, repetición y revisión obsoleta. |

### Datos y recorrido

Se utilizarán una campaña ficticia con escena, ubicación, HP, XP, un acontecimiento y un asunto pendiente; otra campaña de control y una guía ficticia protegida.

1. Ejecutar el servidor y verificar su diagnóstico con un cliente MCP.
2. Conectarlo al entorno real de ChatGPT.
3. Recuperar y comprobar el estado inicial de la campaña ficticia.
4. Solicitar el cambio de prueba autorizado y verificar su guardado.
5. Recuperarlo desde otra conversación y después de reiniciar el servidor.
6. Comprobar fallos, reintentos, revisiones obsoletas y accesos rechazados.
7. Documentar resultados, tiempos observados, costes y limitaciones, sin extrapolarlos a campañas extensas.

El cambio autorizado del experimento no establece una obligación de pedir confirmación adicional para cada consecuencia ordinaria durante una partida.

### Resultado y siguiente decisión

M1 termina cuando el recorrido requerido y sus garantías están verificados. Una investigación puede documentar un impedimento y proponer otro experimento, pero eso no equivale a haber validado el objetivo del milestone.

Los resultados se incorporarán a este documento y se revisarán las HU de M2 cuando sea necesario. Se actualizará el PRD únicamente si cambia el comportamiento o alcance esperado.

La prueba de M1 no acredita todavía consulta correcta de todos los manuales, separación de conocimiento en partidas extensas ni funcionamiento de todas las mecánicas. M2 valida el ciclo jugable y sus casos concretos.

## Mantenimiento

Al revisar una decisión, registrar en la sección correspondiente el cambio, su motivo y la issue o PR con la evidencia. No se marcará una propuesta como validada por haber escrito su configuración.

Las instrucciones de contribución pertenecen a `CONTRIBUTING.md`; el vocabulario, a [conceptos.md](conceptos.md); la experiencia de uso, a [user-journeys.md](user-journeys.md). Este documento conserva la justificación técnica y los resultados de validación.
