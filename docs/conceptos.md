# Glosario del dominio

## Propósito

Este documento fija el vocabulario inicial de SoloQuestAI para utilizar los mismos términos en el [PRD](PRD.md), los [user journeys](user-journeys.md) y las historias de usuario.

Las definiciones aclaran conceptos; no sustituyen requisitos, añaden funcionalidades ni imponen una arquitectura. El alcance de cada entrega se establece en sus milestones. La presencia de un concepto aquí no significa que su funcionalidad esté implementada o incluida en el PMV.

Los términos se agrupan por significado. Los ejemplos son ficticios y no representan una campaña real. Las decisiones aún abiertas se identifican al final.

## 1. Participantes y perspectivas

### Persona usuaria o jugadora

Persona que utiliza la herramienta, toma las decisiones del protagonista y puede intervenir fuera de personaje para configurar la campaña o resolver propuestas y conflictos.

**Distinción:** conocer algo como jugadora no implica que su protagonista lo sepa.

**Ejemplo:** la jugadora conoce un secreto por una consulta fuera de personaje; el protagonista todavía necesita descubrirlo durante la historia.

### Director de juego (DM)

Papel que desempeña ChatGPT al narrar, interpretar NPC y resolver situaciones conforme a la guía, la configuración y las fuentes habilitadas.

**Distinción:** el conocimiento del DM puede incluir información que no se muestra al protagonista. El papel de DM no concede permisos para modificar la lógica o los recursos protegidos de la herramienta.

### Protagonista

Personaje cuyas acciones y elecciones controla la jugadora y desde cuya perspectiva se desarrolla el juego.

**Distinción:** su ficha y su conocimiento son propios; no hereda automáticamente los del jugador ni los de otros personajes.

### Personaje no jugador (NPC)

Personaje interpretado por el DM, con identidad, papel en la historia y conocimiento propios. Los NPC importantes pueden disponer de ficha.

**Ejemplo:** una comerciante conoce a quien le vendió un objeto, pero no conoce automáticamente lo descubierto por el protagonista en otra escena.

### Criatura vinculada

Criatura asociada al protagonista, como un familiar, cuyas características y capacidades se describen en su ficha y en las reglas correspondientes.

**Distinción:** el vínculo no implica compartir automáticamente todos los conocimientos ni sustituye las condiciones de comunicación establecidas por las fuentes.

### Perspectiva

Punto de vista desde el que se conoce, interpreta o comunica información. El producto distingue DM, jugadora fuera de personaje, protagonista y cada NPC relevante.

**Distinción:** perspectiva y certeza son dimensiones diferentes: alguien puede conocer una información falsa y creerla cierta.

### Conocimiento por perspectiva

Información atribuida a una perspectiva concreta, incluyendo procedencia, certeza y momento de adquisición cuando sea relevante.

**Ejemplo:** es un hecho confirmado que un testigo acusó al guardia; todavía puede ser una hipótesis que el guardia cometiera el delito.

### Adquisición de conocimiento

Acontecimiento que explica cómo una persona o personaje accede a una información: observación, conversación, documento u otra vía establecida.

**Distinción:** que la herramienta pueda leer un dato no significa que todos los personajes lo hayan adquirido.

### Consulta fuera de personaje

Pregunta de la jugadora realizada desde su posición como usuaria y no como acción o conocimiento de su protagonista.

**Distinción:** identificarla no elimina los límites de visibilidad aplicables ni convierte la respuesta en conocimiento del personaje.

**Referencias del grupo:** RF3.1–RF3.2, RF5.3, RF7.

## 2. Unidades de juego y estados

### Campaña

Unidad de juego que reúne una historia, configuración, fuentes habilitadas, personajes, registros y progreso propios. Puede abarcar varias sesiones y compartir un mundo con otras campañas.

**Distinción:** compartir escenario no implica compartir automáticamente todo el canon o conocimiento.

### Sesión

Unidad de juego con un registro identificable que se inicia y se cierra expresamente. Puede pausarse y abarcar varias conversaciones.

**Distinción:** una conversación de ChatGPT no equivale a una sesión.

### Escena

Situación narrativa concreta en la que participan personajes en un contexto y momento determinados. Una sesión puede contener varias escenas.

**Ejemplo:** interrogar a una testigo en una posada es una escena; viajar después a las ruinas puede dar paso a otra.

### Conversación

Hilo de interacción con ChatGPT. Es un medio para jugar y consultar la herramienta, no una unidad del calendario ficticio ni del registro de sesiones.

**Distinción:** abrir otro hilo no inicia una sesión nueva ni cierra la anterior por sí mismo.

### Campaña seleccionada

Campaña sobre la que se realizan las operaciones autorizadas en el contexto de juego actual.

**Distinción:** selección no es un estado del ciclo de vida. En el PRD, la expresión «campaña activa» se utiliza para la campaña seleccionada durante el juego; se prefiere este último término para evitar confundirlo con el estado de sesión.

### Estado de campaña

Situación de la campaña respecto a su disponibilidad y ciclo de vida. El PRD distingue como mínimo:

| Término | Significado |
| --- | --- |
| En preparación | Todavía requiere completar los elementos necesarios para comenzar. |
| Jugable | Puede seleccionarse para iniciar o continuar el juego. |
| Archivada | Se ha retirado de las campañas disponibles para jugar, conservando sus datos y su condición previa. |
| Concluida | Su trayectoria ha terminado; el cierre con epílogo impide reanudarla directamente. |

El archivo conserva la condición anterior: recuperar una campaña concluida no la convierte en jugable. La representación de estas dimensiones se definirá técnicamente sin perder esa distinción.

### Estado de sesión

Situación de una sesión iniciada:

| Término | Significado |
| --- | --- |
| En curso | La sesión está abierta y se está jugando. |
| Pausada | La sesión sigue abierta, pero el juego está interrumpido temporalmente. |
| Cerrada | Se ha completado su cierre y la continuación corresponde a una sesión posterior. |

Una campaña recién preparada puede no tener todavía ninguna sesión. Si un cierre falla, no se considera cerrado por haberlo solicitado.

### Pausa y reanudación

Interrupción y continuación de la misma sesión, conservando el punto de juego y los asuntos pendientes.

**Distinción:** pausar no concede XP de cierre, no constituye un descanso del personaje y no implica avance automático del tiempo ficticio.

### Cierre de sesión

Consolidación de los registros y actualizaciones correspondientes a una sesión antes de darla por terminada.

**Distinción:** solicitar el cierre y completarlo son hechos distintos. Una operación incompleta no acredita una sesión cerrada.

### Descanso del personaje

Acontecimiento dentro del mundo de juego cuyos requisitos y efectos sobre los recursos se resuelven mediante las fuentes habilitadas.

**Distinción:** una pausa de la jugadora o el cambio de conversación no producen un descanso.

**Referencias del grupo:** RF1.3, RF1.5, RF1.7, RF2; definiciones de la sección 5 del PRD.

## 3. Hechos, propuestas y continuidad

### Acontecimiento

Suceso ocurrido durante la historia, con un contexto y una posición en la cronología. Puede originar cambios mecánicos, conocimientos o nuevas pistas.

**Ejemplo:** el protagonista abre una puerta y descubre una estancia vacía.

### Hecho confirmado o establecido

Información fijada como parte de lo ocurrido o de la realidad de la campaña, conforme a su resolución o aceptación pertinente.

**Distinción:** «confirmado» no significa que todos los personajes lo conozcan ni que el dato se haya guardado correctamente.

### Hipótesis o conocimiento no confirmado

Interpretación, sospecha o afirmación cuya correspondencia con la realidad de la campaña todavía no está establecida para la perspectiva pertinente.

**Ejemplo:** encontrar barro junto a una ventana permite sospechar una entrada desde el exterior, pero no identifica a quien entró.

### Propuesta pendiente

Alternativa o modificación que todavía requiere una decisión. No se incorpora como si ya hubiera ocurrido.

**Distinción:** no es equivalente a un cambio confirmado cuyo guardado haya fallado.

### Cambio confirmado

Modificación del estado que deriva de una consecuencia ya resuelta durante el juego o de una propuesta aceptada mediante el procedimiento correspondiente.

**Distinción:** una pérdida de HP resuelta en combate no necesita una segunda aprobación únicamente para registrarse.

### Cambio confirmado pendiente de guardar

Cambio establecido cuyo guardado aún no se ha completado.

**Ejemplo:** una consecuencia deja al protagonista con 7 HP, pero falla la escritura. El resultado está confirmado; el almacenamiento sigue pendiente.

**Distinción:** no debe descartarse como propuesta sin aceptar ni presentarse como persistido.

### Estado guardado

Información cuya escritura persistente se ha completado correctamente y que puede recuperarse dentro de las garantías verificadas de la herramienta.

**Distinción:** que un resultado aparezca en una respuesta de ChatGPT no demuestra que se haya guardado.

### Continuidad

Coherencia de acontecimientos, personajes, recursos y conocimientos al avanzar y retomar la campaña.

**Ejemplo:** una puerta que quedó destruida no reaparece intacta al abrir otra conversación sin un acontecimiento que explique su reparación.

### Punto de continuación

Conjunto de información necesaria para retomar el juego: escena, ubicación, personajes presentes, situación inmediata, recursos y asuntos pendientes.

**Distinción:** no es solo un resumen argumental; incluye el estado mecánico pertinente.

### Asunto pendiente

Elemento que debe conservarse para continuar: una pista abierta, una decisión sin resolver o una elección de progresión, entre otros.

**Distinción:** debe precisarse su clase; «pendiente» por sí solo no indica si falta decidir, investigar o guardar.

### Trazabilidad

Posibilidad de relacionar un cambio o resultado con la sesión, acontecimiento, tirada o decisión que lo originó.

**Ejemplo:** identificar qué encuentro produjo una adjudicación de XP y si ya fue aplicada.

### Conflicto de coherencia

Discrepancia relevante entre fuentes, hechos previos, reglas o una modificación propuesta que requiere aclaración antes de fijar sus efectos.

**Distinción:** una nueva hipótesis no es necesariamente un conflicto; la prioridad documental tampoco autoriza a reescribir retrospectivamente lo jugado.

**Referencias del grupo:** secciones 3, 4 y 7; RF2.5, RF6 y RF7 del PRD.

## 4. Documentos y fuentes

### Guía de dirección común

Documento con las reglas generales de dirección aplicables a las campañas. Es un recurso compartido y protegido frente a la edición durante el juego.

### Particularidades de dirección

Adaptaciones explícitas de la guía común para una campaña: preferencias narrativas, restricciones y reglas específicas.

**Distinción:** una excepción particular tiene alcance limitado a su campaña y no modifica la guía común.

### Fuente habilitada

Material autorizado para consultar reglas o interpretar una campaña en función de su configuración. Los tres manuales básicos están siempre habilitados; los suplementos son opcionales.

**Distinción:** disponer de un suplemento no significa tenerlo habilitado. Debe identificarse la edición del material utilizado para evitar mezclar reglas incompatibles.

### Base de la trama

Documento opcional con la premisa y los acontecimientos previstos que orientan el desarrollo de la historia.

**Distinción:** una previsión no es un acontecimiento ocurrido. La base no garantiza un recorrido fijo ni sustituye las decisiones de la jugadora.

### Ficha

Registro mecánico y narrativo de un personaje o criatura, con los datos pertinentes para su papel en la campaña.

**Distinción:** las elecciones todavía pendientes no se presentan como capacidades ya aplicadas.

### Transcripción

Registro de lo jugado organizado por sesiones.

**Distinción:** conserva también declaraciones, sospechas o propuestas en su contexto. Su mera aparición en la transcripción no las convierte en verdad confirmada.

### Canon

Conjunto de hechos establecidos sobre el mundo y la historia de una campaña.

**Distinción:** registrar que un NPC pronunció una acusación no confirma que la acusación sea verdadera. El canon no equivale a todo lo que conocen el protagonista o la jugadora.

### Cronología

Orden temporal de los acontecimientos de la campaña.

**Distinción:** el orden de descubrimiento o de registro de un dato puede ser distinto del momento en que ocurrió el hecho al que se refiere.

### Registro de canon y cronología

Documento organizado por sesiones que reúne acontecimientos relevantes, hechos establecidos, conocimiento no confirmado, personajes, pistas y notas de continuidad, según el PRD.

**Distinción:** incluye información que no pertenece al canon confirmado, por lo que cada clase debe identificarse. «Pestaña por sesión» describe la organización prevista; el formato concreto sigue pendiente de definición técnica.

### Configuración de campaña

Selecciones que determinan su experiencia de juego, como escenario, tono, foco, dificultad, modalidad de dados, progresión y suplementos habilitados.

**Distinción:** no es la configuración del entorno de desarrollo ni un medio para cambiar permisos de la herramienta.

### Recursos comunes

Guía, manuales y suplementos compartidos entre campañas. Su consulta no autoriza su modificación durante el juego.

### Espacio privado de datos

Ámbito donde se conservan materiales y campañas privados, separado del código versionado en el repositorio.

**Distinción:** esta separación es una necesidad del producto; no determina todavía un servicio o tecnología de almacenamiento.

**Referencias del grupo:** secciones 3 y 4; RF1.1–RF1.2, RF6, RF8 del PRD.

## 5. Opciones y mecánicas mencionadas en el producto

| Término | Definición y distinción |
| --- | --- |
| Escenario | Mundo y contexto en que transcurre la historia; puede ser publicado o propio. |
| Tono | Forma en que se siente y se cuenta la historia; se expresa libremente. |
| Foco | Actividades predominantes, como investigación o combate; no excluye las restantes. |
| Perfil de dificultad | Valores iniciales editables de los cuatro parámetros de dificultad definidos en el PRD. |
| Presión sobre recursos | Disponibilidad de suministros y oportunidades de descanso dentro del mundo; no cambia por sí sola las reglas de recuperación. |
| Recurso del personaje | Valor o disponibilidad mecánica que puede consumirse, perderse o recuperarse, como HP o usos de una capacidad. |
| HP | Puntos de golpe del personaje o criatura. Alcanzar 0 HP no equivale automáticamente a morir. |
| XP | Experiencia acumulada utilizada para la progresión según el método elegido y las fuentes habilitadas. |
| Progresión de nivel | Acceso y aplicación de los cambios correspondientes a un nivel, con las elecciones que deba realizar la jugadora. |
| Elección de progresión pendiente | Decisión de subida de nivel todavía no realizada. Conservar XP no significa haber aplicado todos los efectos del nuevo nivel. |
| Modalidad de dados | Elección entre tiradas integradas y resultados comunicados por la jugadora al utilizar dados físicos. |
| Resultado natural | Valor obtenido en los dados antes de aplicar los modificadores pertinentes. |
| Modificador | Ajuste aplicado al resultado conforme a las reglas y al estado correspondiente. |
| Total de tirada | Resultado calculado después de aplicar los modificadores y condiciones pertinentes. |
| CD | Clase de dificultad utilizada cuando la resolución pertinente requiere comparar el resultado con ese umbral. |
| Ventaja y desventaja | Condiciones que afectan a una tirada y se resuelven según las fuentes habilitadas. |
| Tirada secreta | Tirada cuyo detalle tiene visibilidad restringida; conserva trazabilidad sin exponer información a perspectivas no autorizadas. |

Este glosario no sustituye los manuales ni fija fórmulas, umbrales o excepciones de D&D.

**Referencias del grupo:** RF1.4, RF3.4–RF3.5 y RF4 del PRD.

## 6. Operaciones de campaña y cambios deliberados

### Estado inicial

Referencia verificable de los documentos y fichas al comenzar la campaña, utilizada para volver a jugar desde el principio o restablecerla.

**Distinción:** no equivale al último estado guardado ni se actualiza como si fuera el progreso corriente. Su formato exacto queda pendiente.

### Campaña derivada

Campaña independiente que utiliza otra como referencia para iniciar una historia en su mundo o una partida separada desde su estado inicial, según RF1.8.

**Distinción:** no modifica la original. Una historia anterior, contemporánea o posterior solo incorpora hechos coherentes con su fecha.

### Nueva partida desde el inicio

Campaña separada que permite volver a jugar a partir del estado inicial de otra.

**Distinción:** conserva intacto el progreso de la campaña de referencia.

### Restablecimiento

Sustitución del progreso de una campaña existente por su estado inicial, sobre esa misma campaña y con la confirmación prevista.

**Distinción:** a diferencia de una nueva partida separada, reemplaza el progreso existente.

### Archivo y recuperación del archivo

Retirada y posterior restitución de una campaña al conjunto disponible, conservando sus archivos y condición previa.

**Distinción:** archivar no elimina; recuperar del archivo no significa recuperar un fallo de escritura ni reabrir una campaña concluida.

### Eliminación permanente

Borrado de la campaña y sus archivos asociados dentro del ámbito autorizado, después de informar y solicitar confirmación.

**Distinción:** no afecta a los manuales, suplementos ni guía comunes.

### Cambio permanente solicitado

Modificación deliberada de un elemento editable de la campaña, solicitada por la jugadora fuera de la resolución ordinaria de acciones durante el juego.

**Ejemplo:** pedir un cambio en la historia previa de un NPC, frente a actualizar sus HP después de un ataque.

### Excepción de campaña

Decisión explícita que admite una adaptación dentro de lo editable, con alcance, motivo y documentos afectados registrados.

**Distinción:** no amplía permisos ni autoriza cambios silenciosos en decisiones o tiradas ya jugadas.

**Referencias del grupo:** RF1.5–RF1.9, RF6 y RF8 del PRD.

## 7. Muerte y desenlace

### Muerte del protagonista

Resultado de la resolución de las reglas de muerte aplicables, distinto de encontrarse a 0 HP.

**Distinción:** después de morir puede seguir existiendo una vía concreta y viable de retorno conforme a las fuentes y circunstancias.

### Muerte definitiva

Desenlace registrado cuando las vías concretas y viables de retorno examinadas han fracasado, expirado o dejado de ser viables, conforme a RF3.5.

**Distinción:** no se declara automáticamente al llegar a 0 HP ni mientras permanezca una vía concreta de retorno viable.

### Opción de muerte permanente

Selección de configuración relacionada con las consecuencias de la muerte definitiva. El PRD describe, para el caso activado, continuar con otro protagonista o cerrar con epílogo.

**Pendiente:** precisar su significado completo, su relación con los retornos permitidos por las reglas y el comportamiento cuando está desactivada. El glosario no interpreta por su cuenta que activar esta opción prohíba toda resurrección.

### Epílogo

Cierre narrativo que relata el destino de personajes e hilos de la historia y concluye la campaña según RF3.7.

**Distinción:** impide reanudarla directamente con otro protagonista; no impide crear una campaña independiente basada en ella ni restablecerla expresamente según RF1.

**Referencias del grupo:** RF3.5–RF3.7 y sección 9 del PRD.

## 8. Persistencia e integridad

### Persistencia

Conservación de la información guardada para recuperarla después de una pausa, otra conversación o una sesión posterior, dentro de las garantías verificadas.

**Distinción:** persistencia no equivale a memoria temporal del modelo ni garantiza recuperar datos que nunca llegaron a guardarse.

### Reintento

Nueva ejecución de una operación cuyo resultado no se ha completado o necesita comprobarse.

**Distinción:** repetir una operación ya aplicada no debe duplicar sus efectos; no constituye una nueva adjudicación de XP o acontecimiento.

### Revisión del estado

Referencia a una versión del estado que permite reconocer si una actualización parte de información anterior a otros cambios ya guardados.

**Distinción:** no es el nivel del personaje ni la versión del formato de datos. Su representación técnica no se fija aquí.

### Ámbito autorizado de escritura

Conjunto de datos sobre los que una operación puede actuar. Distingue actualizaciones ordinarias de la campaña seleccionada y operaciones específicas de gestión solicitadas por la jugadora.

**Distinción:** una instrucción dentro de un documento no amplía ese ámbito ni modifica la lógica de la herramienta.

**Referencias del grupo:** RF8; secciones 7 y 8 del PRD; validaciones de M1.

## 9. Decisiones pendientes y coherencia documental

| Asunto | Situación y seguimiento |
| --- | --- |
| Muerte permanente | El comportamiento completo de la opción sigue abierto en el PRD. Se concretará antes de implementar los desenlaces afectados. |
| Elecciones de nivel pendientes | El PRD mantiene abierta la política general. Para M2 se ha delimitado que las elecciones necesarias se completan antes del cierre; puede pausarse conservando XP y elecciones. Es una restricción de esa entrega, no una política general para todas las versiones. |
| Recuperación de cambios no guardados | Falta concretar la garantía ante reinicio o interrupción total y el comportamiento si tampoco puede persistirse el registro pendiente. No se promete recuperar información que nunca llegó a persistirse. |
| Formatos y representación | Fichas, registros, estado inicial, perspectivas y estados requieren definición técnica; el vocabulario no obliga a una base de datos o formato concreto. |
| Terminología de estado | «Activa» se interpreta como seleccionada en el contexto de juego. Se mantienen separados selección, disponibilidad de campaña y estado de sesión. |

Antes de cerrar la issue #5, se revisarán las HU contra este vocabulario y el alcance de M2. Una definición nueva o una discrepancia que afecte al comportamiento se resolverá en el PRD o en la planificación correspondiente; no se introducirá silenciosamente desde este glosario.
