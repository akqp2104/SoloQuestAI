# Perfil de usuario y user journeys

## Propósito y alcance

Este documento describe la experiencia prevista de la persona usuaria de SoloQuestAI. Sirve para delimitar el PMV y derivar historias de usuario; no acredita funcionalidades implementadas ni sustituye los requisitos del [PRD](PRD.md).

Los journeys se organizan por objetivos de uso, no por pantallas, comandos o herramientas MCP. Las frases de ejemplo son ilustrativas: la interacción se realiza en lenguaje natural. No se prescribe el almacenamiento ni la arquitectura.

La creación guiada y la gestión avanzada pertenecen al alcance general del producto, pero no se presuponen incluidas en el primer PMV. La selección definitiva de journeys y variantes se registra en el [milestone M2](https://github.com/akqp2104/SoloQuestAI/milestone/3), mediante la issue #4.

## Perfil inicial: P-01 — Jugadora de D&D en solitario

**Persona usuaria:** la desarrolladora del proyecto, que juega con ChatGPT como director de juego y aporta sus manuales y materiales privados de campaña.

**Contexto:** juega mediante conversación, controla un protagonista y puede contar con NPC acompañantes, familiares u otras criaturas vinculadas. Alterna sesiones de distinta duración y puede necesitar continuar en otra conversación. El proyecto es inicialmente de uso personal.

### Objetivos

- Disfrutar de una historia que responda a sus decisiones y conserve sus consecuencias.
- Resolver mecánicas con las fuentes habilitadas y comprender las tiradas y cálculos visibles.
- Consultar fichas y recursos actualizados sin reconstruirlos a mano.
- Pausar y continuar sin trasladar manualmente el contexto entre conversaciones.
- Conservar el control sobre su protagonista y los cambios deliberados de la campaña.

### Dificultades actuales

- Información distribuida entre conversaciones y documentos.
- Trabajo manual para mantener fichas, recursos, acontecimientos y continuidad.
- Riesgo de confundir una sospecha con un hecho o de atribuir secretos a quien no los conoce.
- Incertidumbre sobre qué se ha guardado realmente y qué solo se ha narrado o propuesto.

### Expectativas

- Poder expresarse en lenguaje natural y consultar ayuda cuando la necesite.
- Que la herramienta distinga hechos, propuestas y cambios pendientes de guardar.
- Que se expliquen los conflictos sin resolverlos silenciosamente.
- Que una pausa personal no se interprete como descanso del personaje.
- Que los fallos se comuniquen de forma comprensible y se preserve lo ya guardado.

No se crean perfiles adicionales hasta identificar necesidades distintas que los justifiquen.

## Índice de user journeys

| ID | Objetivo de la persona usuaria | Relación con la primera entrega jugable |
| --- | --- | --- |
| UJ-01 | Preparar una campaña y comenzar a jugar | El PMV parte de una campaña preparada manualmente; creación guiada posterior. |
| UJ-02 | Jugar una escena y resolver sus consecuencias | Recorrido central candidato al PMV. |
| UJ-03 | Consultar ayuda, reglas, ficha o información de campaña | Apoyo al ciclo de juego; alcance concreto pendiente de #4. |
| UJ-04 | Pausar y reanudar la misma sesión | Recorrido central candidato al PMV. |
| UJ-05 | Continuar una sesión en otra conversación | Recorrido central candidato al PMV. |
| UJ-06 | Cerrar una sesión y comenzar la siguiente | Recorrido central candidato al PMV. |
| UJ-07 | Cambiar de campaña y volver a la anterior | Ampliación posterior de gestión de campañas. |
| UJ-08 | Solicitar un cambio permanente y resolver conflictos | Ampliación posterior; el control básico de coherencia se mantiene durante el juego. |

Todos los journeys corresponden a P-01. El glosario se desarrolla por separado en la issue #19, en `docs/conceptos.md`; su ausencia inicial no bloquea la redacción de estos journeys.

## UJ-01 — Preparar una campaña y comenzar a jugar

**Persona usuaria:** P-01.

**Objetivo:** disponer de una campaña y un protagonista preparados para iniciar la aventura.

**Situación inicial:** la jugadora dispone de los materiales necesarios y quiere comenzar una campaña. Puede partir de una campaña preparada previamente o solicitar su creación guiada cuando esa función esté disponible.

**Desencadenante:** «Quiero empezar una campaña» o «Quiero jugar la campaña que he preparado».

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Indica si utilizará una campaña existente o quiere crear una. | Distingue ambas opciones y solicita identificar la campaña o definir sus preferencias. |
| 2 | Para crearla, elige escenario, tono, foco, dificultad y demás opciones del PRD; aporta su protagonista y criaturas vinculadas cuando corresponda. | Guía las elecciones necesarias, aplica los valores predeterminados y comprueba los datos con las fuentes disponibles. |
| 3 | Resuelve las elecciones o discrepancias necesarias para empezar. | Prepara los documentos y conserva el estado inicial; no exige conocer hechos que deban descubrirse durante el juego. |
| 4 | Si la campaña ya estaba preparada, solicita seleccionarla. | Recupera su configuración, fuentes y fichas, y comprueba que sea jugable. |
| 5 | Pide comenzar la primera sesión. | Abre el registro y presenta la escena inicial desde la perspectiva del protagonista. |

### Dificultades y alternativas

- **Campaña ambigua:** pide identificarla antes de activar una distinta.
- **Campaña archivada o concluida:** explica qué operaciones permiten continuar; no la reanuda como si fuera jugable.
- **Material necesario inaccesible o dato esencial ausente:** informa del impedimento y solicita resolverlo; no inventa su contenido.
- **Creación guiada no disponible en el incremento actual:** se utiliza una campaña preparada manualmente. Esto no supone haber validado la creación automática.
- **Opción cuyo comportamiento aún está abierto en el PRD:** se identifica como pendiente de definición antes de implementar la variante afectada.

**Resultado esperado:** campaña seleccionada, ficha inicial coherente y primera sesión iniciada con sus registros preparados.

**Referencias:** RF1.1–RF1.4, RF1.7, RF2.1, RF7 y secciones 3, 4 y 9 del PRD. La creación de campañas derivadas de RF1.8 se detallará en un journey posterior.

## UJ-02 — Jugar una escena y resolver sus consecuencias

**Persona usuaria:** P-01.

**Objetivo:** tomar decisiones como protagonista y conocer sus consecuencias narrativas y mecánicas.

**Situación inicial:** hay una campaña seleccionada y una sesión en curso, con escena, recursos y fuentes identificados.

**Desencadenante:** la herramienta plantea una situación y la jugadora decide qué hacer.

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Lee la escena y expresa la acción de su protagonista. | Narra información accesible al personaje y pide precisiones solo cuando sean necesarias. |
| 2 | Aclara su intención o elige cómo afrontar la situación. | Determina qué regla o resolución corresponde; distingue decisiones del protagonista de acciones de NPC. |
| 3 | Si procede una tirada, solicita la integrada o comunica los resultados naturales de sus dados físicos. | Aplica las condiciones y modificadores pertinentes; muestra el cálculo visible y respeta el secreto de las tiradas que lo requieran. |
| 4 | Recibe el resultado y decide su siguiente acción. | Describe las consecuencias, actualiza los recursos afectados y registra los hechos confirmados con su procedencia y perspectivas. |
| 5 | Continúa jugando o consulta su estado. | Utiliza el estado actualizado y distingue lo guardado de cualquier cambio todavía pendiente. |

### Dificultades y alternativas

- **Acción ambigua:** solicita una precisión sin decidir por el protagonista.
- **Regla no verificable:** explica la incertidumbre y consulta a la jugadora; no presenta una invención como regla oficial.
- **Fuentes contradictorias:** expone el conflicto pertinente sin alterar retrospectivamente lo jugado. La intervención fuera de personaje no transmite por sí sola conocimiento al protagonista.
- **Encuentro peligroso:** no presupone victoria ni obliga al combate; las alternativas dependen de la situación del mundo.
- **Fallo al guardar:** aplica el tratamiento de errores descrito al final del documento. Una consecuencia confirmada no se convierte en propuesta descartable por no haberse guardado.
- **Progresión o muerte:** no improvisa políticas pendientes del PRD. El PMV debe acotar las mecánicas y variantes que podrá validar.

**Resultado esperado:** una decisión de la jugadora produce consecuencias comprensibles, trazables y registradas, sin mezclar hipótesis ni perspectivas.

**Referencias:** RF3.1–RF3.4, RF4.1–RF4.4, RF7, RF8 y secciones 3 y 7 del PRD. RF3.5–RF3.7 requieren journeys de desenlace posteriores.

## UJ-03 — Consultar ayuda, reglas, ficha o información de campaña

**Persona usuaria:** P-01.

**Objetivo:** obtener información suficiente para comprender la herramienta o tomar una decisión de juego.

**Situación inicial:** la jugadora tiene una duda. Las consultas sobre una campaña requieren identificar la campaña pertinente; la ayuda general no requiere una sesión abierta.

**Desencadenante:** «¿Qué puedo pedirte?», «¿Cómo funciona esta regla?», «Muéstrame mi ficha» o una pregunta sobre la historia.

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Formula su consulta. | Distingue ayuda de funciones, reglas, ficha e información de campaña. |
| 2 | Aclara la campaña o la perspectiva si resulta necesario. | Recupera las fuentes y el estado pertinentes sin revelar información de otra campaña. |
| 3 | Lee la respuesta y pide aclaraciones si las necesita. | Responde de forma comprensible, diferencia hechos e hipótesis y señala cualquier incertidumbre o dato pendiente de guardar. |
| 4 | Decide si continúa jugando o solicita una acción distinta. | Mantiene el estado: una consulta no ejecuta por sí sola una modificación. |

### Dificultades y alternativas

- **Regla sin fuente verificable:** informa de la limitación y consulta a la jugadora.
- **Pregunta sobre secretos:** durante el juego responde desde el conocimiento del protagonista. Una consulta explícita fuera de personaje se distingue de ese conocimiento y respeta RF7.
- **Ficha con elecciones o escrituras pendientes:** no presenta sus efectos como completados.
- **Función no disponible:** explica su disponibilidad real sin confundir el roadmap con funcionalidades implementadas.

**Resultado esperado:** respuesta útil y coherente con las fuentes, la perspectiva y el estado actual, sin modificaciones involuntarias.

**Referencias:** RF5.1–RF5.4, RF7 y secciones 3 y 7 del PRD.

## UJ-04 — Pausar y reanudar la misma sesión

**Persona usuaria:** P-01.

**Objetivo:** interrumpir el juego y continuar después desde el mismo punto.

**Situación inicial:** hay una sesión en curso y la jugadora necesita detenerse temporalmente.

**Desencadenante:** «Pausamos aquí».

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Solicita pausar. | Comprueba el guardado de los hechos confirmados y del punto de continuación. |
| 2 | Atiende un aviso si existe una escritura o decisión pendiente. | Distingue el estado guardado, los cambios confirmados pendientes de guardar y las propuestas sin resolver. |
| 3 | Interrumpe el juego. | Confirma la pausa cuando corresponde, manteniendo la sesión sin cerrarla ni adjudicar XP de cierre. |
| 4 | Solicita reanudar. | Recupera escena, situación inmediata, recursos y asuntos pendientes desde el estado conservado. |
| 5 | Expresa la siguiente acción del protagonista. | Continúa sin convertir la pausa personal en descanso ni avance automático del tiempo ficticio. |

### Dificultades y alternativas

- **Guardado incompleto:** informa del problema y de lo pendiente; no afirma que la pausa está completamente guardada.
- **Decisión sin resolver:** se mantiene identificada mientras se permanece en la campaña; no se decide por la jugadora.
- **Reanudación desde otra conversación:** se utiliza UJ-05 para recuperar el contexto.

**Resultado esperado:** misma sesión y punto de juego, con los recursos conservados y sin cierre ni descanso ficticio implícitos.

**Referencias:** RF2.3, RF4.4, RF8.1 y secciones 4 y 7 del PRD.

## UJ-05 — Continuar una sesión en otra conversación

**Persona usuaria:** P-01.

**Objetivo:** continuar sin copiar el historial ni reconstruir manualmente la campaña.

**Situación inicial:** existe un estado persistente de una sesión en curso o pausada. La jugadora abre otra conversación con acceso a la herramienta.

**Desencadenante:** «Continúa mi campaña».

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Solicita continuar e identifica la campaña si es necesario. | Determina qué campaña quiere recuperar sin asumir una selección ambigua. |
| 2 | Confirma la campaña cuando hay varias posibilidades. | Recupera configuración, fuentes, fichas y punto de continuación persistentes. |
| 3 | Lee el contexto necesario para retomar. | Presenta la escena y los asuntos relevantes respetando las perspectivas y el estado de sesión. |
| 4 | Decide la siguiente acción. | Continúa la misma sesión; abrir otra conversación no la cierra ni inicia otra por sí solo. |

### Dificultades y alternativas

- **Campaña inexistente o inaccesible:** explica el impedimento sin inventar un estado.
- **Sesión ya cerrada:** se utiliza UJ-06 para iniciar la siguiente, sin reabrirla silenciosamente.
- **Datos ausentes o inconsistentes:** informa de lo que no puede reconstruir y solicita resolver la discrepancia.
- **Cambios no guardados antes de una interrupción:** no garantiza recuperarlos desde el historial de la conversación anterior; informa de los límites verificados de recuperación.

**Resultado esperado:** la jugadora retoma la campaña correcta con su estado persistente y sin trasladar manualmente la información ya guardada.

**Referencias:** RF1.3, RF2.2–RF2.3, RF5.4, RF7 y secciones 4, 7 y 9 del PRD.

## UJ-06 — Cerrar una sesión y comenzar la siguiente

**Persona usuaria:** P-01.

**Objetivo:** consolidar la sesión y disponer de una continuación clara para la próxima vez.

**Situación inicial:** hay una sesión abierta que la jugadora quiere terminar.

**Desencadenante:** «Cerremos la sesión».

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Solicita cerrar la sesión. | Prepara resumen, XP según el método elegido y actualizaciones documentales, sin duplicar lo registrado durante el juego. |
| 2 | Revisa los cambios y responde a los conflictos o elecciones necesarios. | Explica discrepancias y solicita únicamente las decisiones que correspondan a la jugadora. |
| 3 | Completa las decisiones requeridas para el cierre. | Actualiza fichas, transcripción y registro de canon de la sesión; informa de los documentos guardados y confirma el cierre completo. |
| 4 | Más adelante pide comenzar la siguiente sesión. | Recupera el estado y presenta un resumen global breve, otro de la sesión anterior y el punto de continuación. |
| 5 | Decide cómo continuar. | Abre el registro de la nueva sesión y retoma el juego. |

### Dificultades y alternativas

- **Conflicto no resuelto o escritura fallida:** el cierre permanece incompleto; se informa de la causa y de lo que falta.
- **Petición repetida de cierre:** no vuelve a adjudicar el mismo XP ni duplica acontecimientos.
- **Subida de nivel con elecciones pendientes:** se registran por separado el XP y las decisiones; la posibilidad de cerrar o continuar en ese estado sigue pendiente en el PRD y debe resolverse antes de implementar la variante.
- **La jugadora solo quería una pausa:** se utiliza UJ-04; no se impone un cierre de sesión.

**Resultado esperado:** sesión cerrada con registros coherentes y siguiente sesión iniciada sin pérdida ni duplicación de progreso.

**Referencias:** RF2.2, RF2.4, RF4.4, RF7–RF8 y secciones 4, 7 y 9 del PRD.

## UJ-07 — Cambiar de campaña y volver a la anterior

**Persona usuaria:** P-01.

**Objetivo:** alternar aventuras conservando su progreso y sin mezclar información.

**Situación inicial:** existe una campaña seleccionada y otra campaña jugable disponible.

**Desencadenante:** «Quiero cambiar a otra campaña».

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Pide listar campañas y elige otra. | Muestra sus estados y distingue selección, ciclo de vida y estado de sesión. |
| 2 | Revisa cualquier aviso de propuestas sin confirmar. | Guarda los cambios confirmados de la actual y avisa de las propuestas que se descartarán al completar el cambio. |
| 3 | Solicita continuar con la campaña elegida. | Completa el cambio cuando el guardado necesario está resuelto y recupera solo los datos de la campaña destino. |
| 4 | Más adelante solicita volver a la anterior. | Recupera su último estado confirmado, sin cerrar la sesión ni adjudicar XP de cierre por haber cambiado de campaña. |

### Dificultades y alternativas

- **Escritura pendiente:** no completa el cambio ni descarta un cambio confirmado como si fuera una propuesta.
- **Campaña archivada o concluida:** explica la operación necesaria; una concluida con epílogo no se reanuda directamente.
- **Conocimiento entre campañas:** no traslada hechos ni secretos por el mero cambio de selección.

**Resultado esperado:** ambas campañas conservan su progreso e información independientes; las propuestas descartadas no aparecen como hechos confirmados.

**Referencias:** RF1.3, RF1.5, RF1.7, RF2.5, RF7–RF8 y sección 7 del PRD.

## UJ-08 — Solicitar un cambio permanente y resolver conflictos

**Persona usuaria:** P-01.

**Objetivo:** adaptar deliberadamente una campaña comprendiendo sus efectos sobre reglas y continuidad.

**Situación inicial:** hay una campaña seleccionada y la jugadora quiere modificar una ficha, introducir un NPC o cambiar un elemento editable de la campaña.

**Desencadenante:** una solicitud explícita de modificación, distinta de una acción del protagonista durante el juego.

### Pasos principales

| Paso | Acción de la jugadora | Respuesta esperada de la herramienta |
| --- | --- | --- |
| 1 | Describe el cambio deseado. | Identifica su alcance y comprueba que pertenezca al ámbito editable. |
| 2 | Aclara la propuesta cuando sea necesario. | Revisa coherencia con las fuentes habilitadas y los hechos previos; explica los efectos detectados. |
| 3 | Si hay conflicto, elige establecer una excepción limitada a la campaña, descartar o ajustar la propuesta. | Mantiene la propuesta pendiente hasta que exista una decisión explícita; no altera silenciosamente lo jugado ni las tiradas. |
| 4 | Solicita aplicar la propuesta resultante. | Actualiza los documentos autorizados y registra las excepciones aceptadas con motivo, alcance y documentos afectados. |
| 5 | Consulta el resultado. | Distingue lo aplicado de lo pendiente y utiliza el cambio de forma consistente en adelante. |

### Dificultades y alternativas

- **Cambio fuera del ámbito permitido:** se rechaza con una explicación y no se amplían permisos.
- **Cambio que depende de un suplemento:** se comprueban sus efectos antes de activarlo o desactivarlo.
- **Cancelación de la propuesta:** conserva el estado previo.
- **Fallo al guardar:** se informa de lo aplicado y pendiente sin presentar la operación como completa.

**Resultado esperado:** modificación explícita y trazable, o propuesta descartada sin efectos, manteniendo los límites de edición.

**Referencias:** RF6.1–RF6.4, RF8 y secciones 3, 4 y 7 del PRD.

## Tratamiento común de fallos y decisiones pendientes

Estas condiciones complementan los journeys sin imponer una solución técnica:

- Una operación de lectura fallida no se sustituye por datos inventados.
- Se distingue entre propuesta sin decidir, cambio confirmado pendiente de guardar y cambio guardado correctamente.
- Un fallo de escritura se comunica indicando la operación afectada y el estado conocido. El reintento no duplica efectos ya guardados.
- Un cierre o cambio de campaña incompleto no se presenta como terminado.
- La recuperación de cambios todavía no guardados tras un reinicio o interrupción total depende de una garantía pendiente de definición y validación en el PRD; no se afirma que sea posible por defecto.
- Las respuestas respetan el conocimiento de cada perspectiva, incluso al mostrar errores, resúmenes y registros de tiradas.

## Términos y decisiones que requieren seguimiento

La issue #19 recogerá las definiciones y señalará discrepancias con el PRD. Este documento utiliza sus distinciones actuales sin resolver por su cuenta las decisiones abiertas:

| Término o decisión | Seguimiento necesario |
| --- | --- |
| Campaña seleccionada, estado de campaña y estado de sesión | Mantenerlos como conceptos distintos. |
| Hecho confirmado, propuesta pendiente y cambio pendiente de guardar | Evitar exigir confirmación adicional para consecuencias ordinarias o descartar escrituras fallidas como propuestas. |
| Canon, cronología, hipótesis y conocimiento por perspectiva | Diferenciar verdad, creencia y acceso a la información. |
| Progresión pendiente | Definir si permite cerrar sesión o continuar y qué efectos siguen sin aplicarse. |
| Muerte definitiva y opción de muerte permanente | Precisar su relación y el comportamiento de la opción desactivada antes de detallar los desenlaces. |
| Recuperación de cambios no guardados | Definir y validar sus límites ante reinicio o interrupción total. |

Los journeys de archivo, eliminación, restablecimiento, campañas derivadas y desenlaces se detallarán al preparar sus entregas. Su ausencia aquí no los elimina del alcance general del PRD.

## Uso para la planificación

- La issue #3 produce este perfil y los user journeys iniciales.
- La issue #4 selecciona el alcance del PMV y sus variantes de validación.
- La issue #19 mantiene el glosario inicial.
- La issue #5 deriva HU pequeñas con referencias al PRD y a identificadores UJ, y comprueba la coherencia con el glosario antes de cerrarse.
- Los identificadores UJ se conservan aunque posteriormente se divida el documento en varios archivos. Una HU puede desarrollar parte de un journey y un journey puede requerir varias HU.
