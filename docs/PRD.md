# SoloQuestAI — PRD

Estado: definición del producto. Las funcionalidades descritas no se presentan como implementadas.

## 1. Visión general

### Problema
Una persona puede jugar campañas de D&D con ChatGPT como *dungeon master* y participar también como codirectora. Para mantener una campaña larga y coherente debe consultar reglas, controlar tiradas y recursos, recordar decisiones y actualizar varios documentos. La repetición de estas tareas interrumpe la narración y ralentiza el avance.

### Solución
Una herramienta integrada en ChatGPT que permita a la IA dirigir la partida, resolver y registrar mecánicas, conservar el estado entre sesiones y mantener los documentos de la campaña. El jugador conserva las decisiones de su personaje y decide cómo resolver las contradicciones o cambios deliberados del canon.

### Usuarios
La persona usuaria inicial es la desarrolladora del proyecto, que juega campañas de D&D en solitario con ChatGPT como DM y aporta sus propios materiales. El desarrollo se orienta al uso personal; una posible distribución pública queda fuera del alcance actual. Como público potencial futuro se contemplan personas principiantes o experimentadas que quieran jugar con una IA como DM. La experiencia inicial se centra en una persona jugadora con un personaje protagonista; puede haber NPC acompañantes, familiares y otras criaturas vinculadas.

## 2. Objetivos y alcance

- Permitir crear, seleccionar, jugar, pausar, reanudar y cerrar campañas y sesiones desde la conversación.
- Aplicar las reglas y cálculos de juego con resultados comprensibles y trazables.
- Mantener continuidad narrativa y mecánica mediante documentos persistentes.
- Ayudar a la persona jugadora durante el juego sin tomar en silencio decisiones que le corresponden.
- Permitir consultar por separado las funciones de la herramienta y las dudas sobre reglas o sobre la campaña.

**Alcance funcional de este PRD:** juego conversacional con un protagonista y una campaña activa en cada momento. Incluye gestión de campañas, dirección de partidas, tiradas y reglas, continuidad entre sesiones y campañas, consultas, control de cambios, conocimiento por perspectiva y mantenimiento de los documentos descritos abajo. Pueden existir varias campañas, pero solo una está activa en cada momento de juego. Las entregas se priorizarán en el backlog.

Quedan fuera de este alcance las interfaces gráficas de tablero, los mapas tácticos interactivos, el juego multijugador y las automatizaciones que se ejecutan sin una orden del jugador. En el futuro podrán añadirse dentro de ChatGPT vistas visuales de fichas, tableros y mapas, vinculadas al estado persistente de la campaña. La incorporación futura de otros suplementos debe poder configurarse sin cambiar los documentos ya creados.

### Resultados que se comprobarán

Con una campaña de prueba, verificar que se puede jugar y cerrar una sesión sin reconstruir manualmente tiradas, XP, fichas y canon; retomar la partida tras una pausa o un cambio de campaña sin perder hechos confirmados; y mantener los secretos fuera del conocimiento del protagonista. El tiempo de respuesta y la exactitud se medirán antes de fijar objetivos numéricos para los incrementos de desarrollo.

## 3. Fuentes y resolución de conflictos

La prioridad para interpretar la campaña es:

1. Guía de dirección común, completada por las particularidades de la campaña. Dentro de este nivel, una particularidad explícita prevalece sobre la regla general que adapta.
2. Los tres manuales básicos comunes y los suplementos habilitados para esa campaña.
3. Base de la trama, si existe.
4. Fichas de personajes y criaturas vinculadas.
5. Transcripción de la partida.
6. Canon y cronología.

La prioridad orienta la consulta y la resolución de discrepancias sobre un mismo asunto; **no autoriza a alterar retrospectivamente lo ocurrido**. Si una fuente superior parece contradecir un hecho ya jugado, o la resolución no es clara, la herramienta expone las fuentes y el conflicto al jugador antes de fijar una nueva verdad. Los hechos confirmados, lo que creen los personajes y las hipótesis se registran por separado. La información secreta de la base de la trama no se revela en resúmenes dirigidos al personaje.

Si falta un dato necesario o una regla no puede verificarse en las fuentes autorizadas, la IA pregunta al jugador. No inventa una regla presentándola como oficial. Las reglas generales de dirección se fijan en la guía común; las preferencias de narración, época y restricciones particulares se fijan en cada campaña y se aplican junto a ella.

## 4. Organización de documentos y estado

El espacio privado de datos de la herramienta, separado del código y de los archivos versionados en el repositorio, contiene una **guía de dirección común** y una **carpeta de manuales y suplementos comunes**. En esta última se guardan el Manual del Jugador, la Guía del Dungeon Master y el Manual de Monstruos, que se aplican a todas las campañas, además de las extensiones y suplementos disponibles. La guía y los manuales comunes se mantienen en un solo lugar y no se duplican en cada campaña. La guía establece las reglas generales de dirección aplicables a todas ellas.

Cada campaña indica en su configuración qué suplementos de esa carpeta tiene habilitados. Puede jugarse solo con los tres manuales básicos. Añadir un suplemento a la carpeta común no lo activa automáticamente en las campañas existentes. Si el jugador activa o desactiva un suplemento durante una campaña, la herramienta revisa si algún personaje, regla o acontecimiento previo depende de él. Si detecta un conflicto, se lo explica al jugador y le deja decidir cómo resolverlo según RF6.

La organización descrita es lógica: su representación física y los formatos se decidirán durante la validación técnica. Los manuales y las campañas privadas no se incorporan al repositorio.

Cada campaña dispone de su propia carpeta con:

- **Particularidades de dirección:** documento o sección con las adaptaciones de la guía común para esta campaña, incluidas las preferencias narrativas, restricciones de ambientación y reglas específicas. Se aplica como complemento de la guía común; una excepción debe ser explícita y limitarse a su campaña.
- **Base de la trama (opcional):** premisa y eventos previstos; sirve de esqueleto y permite libertad sobre cómo se llega a ellos y qué eventos secundarios surgen.
- **Fichas:** protagonista, NPC importantes y familiares u otras criaturas vinculadas, con datos mecánicos y narrativos pertinentes.
- **Transcripciones:** registro de lo jugado, dividido por sesiones. Las correcciones editoriales no cambian decisiones, tiradas ni consecuencias sin intervención del jugador.
- **Canon y cronología:** documento con una pestaña por sesión. Cada pestaña contiene: (a) resumen de los acontecimientos relevantes de la sesión, dividido en subsecciones por evento y ordenado cronológicamente; cada subsección incluye los detalles, tiradas y pruebas de característica pertinentes; (b) hechos establecidos; (c) conocimiento no confirmado; (d) personajes importantes que aparecieron directa o indirectamente; (e) pistas y misterios activos; y (f) notas de continuidad para la siguiente sesión.
- **Configuración:** nombre, escenario, tono, ritmo, foco, duración deseada, parámetros de dificultad, nivel inicial del protagonista, método de progresión del XP, modalidad de dados, opción de muerte permanente y suplementos habilitados.
- **Estado inicial:** referencia verificable de los documentos y fichas al comenzar la campaña, utilizada para crear una partida separada desde el principio o restablecer la existente.

El estado necesario para reanudar —escena y ubicación, personajes presentes, situación inmediata, recursos y asuntos pendientes— queda consignado en las notas de continuidad y las fichas o secciones correspondientes del canon y cronología. Durante una sesión, la herramienta guarda los hechos y cambios confirmados a medida que se producen para que una pausa no dependa de un resumen final todavía inexistente. Una propuesta pendiente de decisión no pasa al estado confirmado. Cada hecho importante conserva quién lo sabe y cómo se conoció, conforme a RF7.

## 5. Requisitos funcionales

### Definiciones de estado y confirmación

- **Campaña seleccionada:** campaña sobre la que se realizan las operaciones autorizadas en el contexto de juego actual; no es un estado de su ciclo de vida.
- **Estado de campaña:** distingue, como mínimo, campañas en preparación, jugables, archivadas y concluidas. Archivar no elimina su condición previa ni permite reabrir una campaña concluida.
- **Estado de sesión:** distingue una sesión en curso, pausada o cerrada; una campaña puede no tener todavía sesiones. Cambiar de conversación no inicia ni cierra una sesión por sí mismo.
- **Hecho o cambio confirmado:** consecuencia ya resuelta durante el juego o modificación aceptada conforme al procedimiento que corresponda. Las consecuencias ordinarias del juego se registran sin exigir una confirmación adicional para cada actualización.
- **Propuesta pendiente:** alternativa o modificación que todavía requiere una decisión; no se incorpora como un hecho ocurrido.
- **Cambio confirmado pendiente de guardar:** cambio ya establecido cuyo guardado no se ha completado. No se confunde con una propuesta descartable.

Estas distinciones se desarrollarán en `docs/conceptos.md` sin duplicar los requisitos del producto.

### RF1. Gestión de campañas

#### RF1.1. Creación y configuración inicial

Guiar al jugador para crear la ficha del protagonista y, si corresponde, de sus familiares u otras criaturas vinculadas; elegir escenario, tono, foco, duración deseada, dificultad, nivel inicial, base de la trama opcional, método de progresión del XP, suplementos opcionales y opción de muerte permanente. En este último caso, una muerte definitiva termina la trayectoria del protagonista, pero el jugador puede continuar con otro personaje o concluir con epílogo según RF3.6 y RF3.7. Ofrecer escenarios publicados cuyo material esté disponible para la herramienta o permitir crear un mundo propio. El tono se describe libremente; el foco permite combinar opciones predefinidas e indicar la predominante. El nivel inicial es 1 por defecto, aunque se puede elegir otro permitido por las reglas habilitadas y completar sus elecciones y recursos. Los tres manuales básicos están siempre habilitados. La dificultad se detalla en RF1.4.

#### RF1.2. Creación de documentos

Crear la carpeta y los documentos definidos en la sección 4, sin exigir información que pueda descubrirse durante el juego. Conservar una referencia verificable al estado inicial para RF1.8 y RF1.9.

#### RF1.3. Selección de campaña

Permitir seleccionar una campaña jugable existente y activar su configuración, particularidades de dirección y fuentes habilitadas. Una campaña archivada debe recuperarse antes de jugarla y una concluida con epílogo no puede reanudarse. Recuperar el estado de juego al iniciar o reanudar una sesión conforme a RF2.

#### RF1.4. Configuración de la dificultad

Permitir elegir un perfil predefinido o ajustar por separado cuatro parámetros: frecuencia de pistas y ayuda, gravedad de las consecuencias, dificultad prevista de los encuentros (fácil, media o difícil) y presión sobre recursos (suministros y oportunidades de descanso). Los perfiles fijan valores iniciales editables. La presión sobre recursos no cambia las reglas de descanso ni los recursos de la ficha. Los cambios posteriores de configuración se revisan según RF6.

#### RF1.5. Archivo y recuperación

Archivar una campaña la retira de las campañas disponibles para jugar sin borrar sus archivos. Permitir recuperarla conservando su estado previo y, si era jugable, seguir desde el último estado confirmado. Recuperar del archivo una campaña concluida no la hace reanudable.

#### RF1.6. Eliminación permanente

Eliminar permanentemente la campaña y todos los archivos asociados dentro de su carpeta solo después de informar del alcance y solicitar confirmación. No borrar la guía, los manuales ni los suplementos comunes.

#### RF1.7. Listado de campañas

Mostrar las campañas existentes con su nombre, estado de campaña, indicación de si está seleccionada, estado de la sesión cuando exista y último punto de juego disponible. Distinguir las que se pueden reanudar de las que requieren recuperación, una nueva partida o un restablecimiento.

#### RF1.8. Nueva campaña a partir de otra

Permitir crear una campaña desde cero, iniciar una historia nueva en el mundo de otra campaña con un nuevo protagonista o volver a jugar desde su estado inicial. En una historia nueva, elegir si sucede antes, durante o después de la campaña de referencia y trasladar solo los hechos del mundo coherentes con esa fecha. Volver a jugar desde el principio crea una partida separada; la campaña de referencia no se modifica, aunque esté concluida con epílogo.

#### RF1.9. Restablecimiento de una campaña

Permitir devolver una campaña existente a su estado inicial en la misma carpeta, sustituyendo sus documentos y progreso, incluidas fichas, transcripciones y canon generado. Mostrar antes qué se perderá y solicitar confirmación. No modificar otras campañas ni los recursos comunes.

**Opciones narrativas:** el escenario determina el mundo; el tono describe cómo se siente y cuenta la historia; el foco indica qué actividades predominan, como investigación, combate, exploración o relaciones. Elegir un foco no excluye las demás actividades.

### RF2. Sesiones y continuidad

#### RF2.1. Inicio de la primera sesión

Iniciar la primera sesión de la campaña configurada y abrir su registro de sesión.

#### RF2.2. Inicio de sesiones posteriores

Recuperar la escena, el estado mecánico y los asuntos pendientes. Mostrar un resumen global breve de la campaña y otro de los acontecimientos principales de la sesión anterior antes de continuar.

#### RF2.3. Pausa y reanudación

Pausar y reanudar una sesión sin cerrarla ni adjudicar automáticamente XP de cierre. Retomar desde el último estado confirmado. La pausa del jugador no equivale a un descanso corto o largo del personaje, que se resuelve según las reglas.

#### RF2.4. Cierre de sesión

Al solicitar el cierre, preparar el resumen de acontecimientos, el XP conforme al método elegido y las actualizaciones de fichas, transcripción y pestaña de canon. Mostrar los cambios y conflictos antes de cerrar; resolver con el jugador los conflictos necesarios y confirmar qué documentos se han actualizado.

#### RF2.5. Cambio de campaña

Al cambiar de campaña, persistir los hechos y cambios confirmados de la actual. Informar de las propuestas sin confirmar y descartarlas al completar el cambio. Al volver, continuar desde el último estado confirmado sin cerrar por ello la sesión ni adjudicar XP de cierre.

### RF3. Dirección de la partida

#### RF3.1. Narración y desarrollo

Narrar como DM según la guía, el escenario, el tono y el foco de la campaña. Usar la base de la trama como esqueleto cuando exista, crear escenas y NPC, y adaptar el desarrollo a las decisiones del jugador.

#### RF3.2. Decisiones del jugador

Recibir las acciones y decisiones del personaje en lenguaje natural, presentar sus consecuencias y pedir precisiones cuando sean necesarias, sin decidir por el personaje.

#### RF3.3. Peligro y alternativas

Plantear peligros y encuentros coherentes con el mundo. No garantizar que todos puedan ganarse mediante combate: negociar, huir o evitarlos puede ser viable.

#### RF3.4. Aplicación de la dificultad

Aplicar los cuatro parámetros configurados en RF1.4 durante la narración y el diseño de situaciones. La dificultad prevista orienta el conjunto de encuentros sin fijar la dificultad de cada uno. La presión sobre recursos afecta a su disponibilidad dentro del mundo, respetando las reglas aplicables.

#### RF3.5. Resolución de la muerte del protagonista

Llegar a 0 HP no implica necesariamente morir: resolver inconsciencia, salvaciones contra muerte, estabilización, curación y muerte instantánea según las reglas habilitadas. Si muere, registrar el momento y las circunstancias y examinar plazos, requisitos, recursos y capacidades accesibles, situación del cuerpo y acciones plausibles para devolverlo a la vida. Mantener el desenlace pendiente mientras exista una vía concreta y viable, sin introducir ayudas para garantizar el retorno. Registrar la muerte definitiva cuando todas esas vías fracasen, expiren o dejen de ser viables. Si hay una incertidumbre irresoluble, consultar al jugador.

#### RF3.6. Continuación con otro protagonista

Con la opción de muerte permanente activada y confirmada la muerte definitiva, permitir continuar la misma campaña desde un momento posterior con un NPC principal de ficha actualizada o un personaje nuevo. Conservar el canon, las relaciones y las consecuencias previas. El nuevo protagonista solo conoce lo que le corresponde según RF7.

#### RF3.7. Cierre con epílogo

Si el jugador elige cerrar tras la muerte definitiva, narrar un epílogo sobre el destino de los personajes principales y los hilos de la historia. Marcar la campaña como concluida e impedir reanudarla con otro protagonista. Puede servir de base a una campaña independiente según RF1.8 o restablecerse expresamente según RF1.9.

### RF4. Tiradas, reglas y progresión

#### RF4.1. Modalidad de dados

Permitir elegir entre la función de tirada integrada y dados físicos. En este último caso, el jugador comunica el resultado natural para que la herramienta aplique los modificadores.

#### RF4.2. Cálculo y registro de tiradas

Determinar el dado, motivo, característica o competencia, ventaja o desventaja y CD cuando proceda. Mostrar el resultado natural, los modificadores y el total en las tiradas visibles para el jugador; registrar las tiradas relevantes de modo que el cálculo pueda reconstruirse. En las tiradas secretas, conservar ese detalle con visibilidad restringida y mostrar solo la información permitida por la perspectiva correspondiente, sin revelar indirectamente secretos en resúmenes o consultas ordinarias.

#### RF4.3. Aplicación de reglas

Consultar las fuentes autorizadas para resolver pruebas, combate, conjuros, descansos y recursos. Si la regla necesaria falta o las fuentes no resuelven claramente una discrepancia, consultar al jugador según la sección 3.

#### RF4.4. XP y elecciones de progresión

Adjudicar y registrar XP conforme al método elegido, mantener el total acumulado y aplicar los umbrales de nivel de los manuales habilitados. Pedir al jugador las elecciones mecánicas que le correspondan, como subclase o conjuros, antes de aplicar sus efectos a la ficha. Registrar por separado el XP confirmado y las elecciones de progresión pendientes; una ficha con elecciones pendientes no se presenta como completamente actualizada. La política sobre cerrar una sesión o continuar jugando con estas elecciones pendientes se resolverá antes de implementar este flujo, según la sección 9.

### RF5. Consultas y ayuda

#### RF5.1. Ayuda sobre la herramienta

Mostrar las funciones disponibles, sus descripciones y los comandos o frases de ejemplo. Los comandos son atajos; las funciones también se pueden pedir en lenguaje natural.

#### RF5.2. Consulta de reglas de D&D

Responder preguntas sobre reglas utilizando las fuentes habilitadas y señalar la incertidumbre si no se puede verificar una respuesta. Una consulta no modifica por sí sola el estado de la campaña.

#### RF5.3. Consulta de la campaña

Responder preguntas sobre hechos, personajes y continuidad, distinguiendo hechos establecidos, hipótesis y perspectivas. Durante el juego, responder desde el conocimiento del protagonista. Una consulta explícita fuera de personaje se identifica como tal y no transfiere automáticamente ese conocimiento al protagonista; aplicar RF7.

#### RF5.4. Consulta de ficha y estado

Mostrar la ficha y el estado actual del personaje, incluyendo los cambios confirmados más recientes.

### RF6. Cambios permanentes solicitados

#### RF6.1. Solicitud de cambios

Permitir al jugador proponer cambios permanentes en fichas, introducir NPC propios y modificar canon, base de la trama, particularidades de dirección o configuración de la campaña seleccionada. Distinguir estas propuestas de las acciones y consecuencias ocurridas durante el juego. Excluir los manuales, la guía común, el historial de tiradas, otras campañas y la lógica de la herramienta.

#### RF6.2. Comprobación de coherencia

Antes de aplicar una propuesta, revisar si contradice las reglas autorizadas o la continuidad y explicar los efectos detectados. No reescribir silenciosamente decisiones ya jugadas o resultados de tiradas.

#### RF6.3. Decisión sobre conflictos

Si se detecta un conflicto dentro de lo editable, pedir al jugador que elija explícitamente entre establecer una excepción limitada a esa campaña, descartar el cambio o ajustarlo para eliminar la contradicción. Rechazar los cambios fuera de ese ámbito con una explicación. No decidir por él ni permitir que una excepción altere silenciosamente decisiones ya jugadas o tiradas.

#### RF6.4. Registro de excepciones

Registrar cada excepción aceptada con su alcance, motivo y documentos afectados. Cuando corresponda, actualizar las particularidades de dirección o la configuración de la campaña para aplicarla de manera consistente en adelante.

### RF7. Conocimiento y perspectivas

#### RF7.1. Registro de conocimiento

Registrar por separado la verdad conocida por el DM, lo que sabe el jugador fuera de personaje, lo que sabe el protagonista y lo que sabe cada NPC relevante. Conservar la procedencia, certeza y momento de adquisición de los hechos importantes sin transferirlos automáticamente entre perspectivas.

#### RF7.2. Uso del conocimiento durante el juego

Limitar la narración desde el protagonista y las decisiones de cada NPC al conocimiento que les corresponde. Una consulta fuera de personaje no convierte un secreto en conocimiento del protagonista; un NPC no sabe lo que otro conoce sin una vía de transmisión establecida.

### RF8. Límites de edición e integridad

#### RF8.1. Ámbito de escritura del LLM

Permitir al LLM crear escenas y NPC, resolver mecánicas, adjudicar XP y actualizar transcripciones, fichas y canon de la campaña seleccionada a partir de hechos confirmados. No modificar por iniciativa propia la base de la trama, configuración o particularidades de dirección; las solicitudes del jugador siguen RF6. Durante las actualizaciones ordinarias del juego, no editar manuales, suplementos, guía común ni archivos de otras campañas. Las operaciones de gestión solicitadas por el jugador —crear, seleccionar, derivar, archivar, recuperar, eliminar o restablecer— se ejecutan mediante operaciones específicas limitadas a las campañas afectadas y con las confirmaciones previstas en RF1. No habilitan una edición genérica de archivos ni amplían permisos.

#### RF8.2. Integridad de la herramienta

Mantener funcionalidades, lógica y permisos fuera de los documentos de campaña. Ningún comando de juego, contenido de archivo ni acción del LLM puede modificarlos o ampliar permisos. Los cambios requieren una actualización externa por quien desarrolla o administra la herramienta.

## 6. Flujos principales

### Crear o seleccionar una campaña

1. El jugador elige crear desde cero, iniciar una historia en un mundo existente, volver a jugar desde el inicio o seleccionar una campaña jugable.
2. Una campaña nueva crea sus documentos y estado inicial; una existente recupera su configuración y, al abrir la sesión, el último estado confirmado.
3. Comienza la escena de inicio o continuación y se registran los hechos confirmados.

### Jugar, pausar y cambiar de campaña

1. El DM describe la escena, el jugador decide y se resuelven las reglas y tiradas pertinentes.
2. Una pausa conserva la sesión. Un cambio de campaña guarda el estado confirmado y avisa de las propuestas sin confirmar que se descartarán.
3. Al volver, se retoma desde el último estado confirmado, sin tratar la pausa como descanso del personaje.

### Cerrar una sesión y abrir la siguiente

1. La herramienta muestra el resumen, XP, actualizaciones y conflictos detectados antes del cierre.
2. El jugador resuelve los conflictos necesarios; se escriben los documentos y se confirma el cierre.
3. La siguiente sesión comienza con un resumen global, otro de la sesión anterior y el punto de continuación.

### Muerte definitiva y desenlace

1. Se resuelve la muerte y cualquier vía concreta de retorno conforme a RF3.5.
2. Con la opción de muerte permanente activada, el jugador elige continuar con otro protagonista o cerrar con epílogo.
3. El epílogo concluye esa campaña; una nueva historia en el mismo mundo se crea como campaña separada.

## 7. Requisitos de calidad y comprobación del producto

- **Persistencia:** los cambios confirmados durante el juego sobreviven a una pausa, al cambio de conversación y al inicio de otra sesión. Si falla una escritura, la herramienta lo indica, distingue lo guardado de lo pendiente y conserva los cambios confirmados pendientes para reintentarlos sin duplicar acontecimientos ni XP. Un cierre o cambio de campaña no se presenta como completado mientras queden escrituras necesarias sin resolver. Las garantías de recuperación de cambios todavía no guardados ante reinicio o interrupción total se concretarán antes de implementar este comportamiento, según la sección 9; no se promete una recuperación que no se haya verificado.
- **Trazabilidad:** cada cambio mecánico o de canon permite identificar la sesión y el hecho o decisión que lo originó. La IA distingue lo escrito con éxito de lo que solo ha propuesto.
- **Coherencia y control:** mientras se permanece en una campaña, las elecciones y conflictos no resueltos siguen pendientes. Al cambiar de campaña, se descartan las propuestas sin confirmar conforme a RF2.5. El sistema no presenta un cierre incompleto como terminado.
- **Separación del conocimiento:** las respuestas durante el juego muestran solo la información que puede conocer el protagonista, aunque el sistema tenga acceso a notas del DM o a conocimiento del jugador fuera de personaje. La información de un NPC no se atribuye a otro sin una vía de transmisión.
- **Usabilidad:** las operaciones principales se pueden pedir en lenguaje natural; la ayuda explica los atajos y el estado actual sin exigir que el jugador recuerde comandos.
- **Acceso a archivos:** durante el juego solo se escriben documentos autorizados de la campaña seleccionada. Las operaciones de gestión de RF1 pueden actuar sobre las campañas identificadas en la solicitud, respetando su alcance y confirmaciones. Los recursos comunes permanecen fuera del ámbito de escritura. Si falta acceso, se informa qué operación quedó pendiente.

## 8. Criterios de aceptación del alcance descrito

- Una campaña creada contiene la configuración y los documentos requeridos; una campaña seleccionada recupera la sesión y fichas correctas, incluido el nivel inicial elegido.
- Una sesión pausada se reanuda en la misma escena y con los mismos recursos, sin tratar la pausa como descanso del personaje ni como cierre.
- Una tirada propia comunicada como resultado natural y una tirada integrada aplican los mismos modificadores; el registro permite reconstruir el total.
- El cierre deja una pestaña de sesión con todas las secciones definidas y los eventos en orden cronológico, actualiza las fichas afectadas y muestra los cambios realizados.
- Una pista o sospecha no aparece como hecho confirmado solo por mencionarse en una transcripción.
- Un cambio contradictorio solicitado por el jugador no se aplica hasta que elija una de las tres opciones; su decisión queda reflejada en las fuentes pertinentes.
- Al comenzar otra sesión aparecen un resumen global, uno de la sesión anterior y el punto de continuación correcto.
- Las consultas de funciones y las consultas de reglas o campaña son accesibles por separado.
- El listado distingue campañas jugables, archivadas y concluidas. Archivar permite recuperar la campaña; eliminar permanentemente requiere confirmar el borrado de su carpeta y archivos sin afectar los recursos comunes.
- Al cambiar de campaña, sobreviven los cambios confirmados y se descartan las propuestas sin confirmar después de informar de ello.
- Crear una campaña desde otra no modifica la original; volver a jugar desde el inicio crea una partida separada. Restablecer sustituye el progreso de la campaña existente tras confirmación.
- Con la opción de muerte permanente activada, llegar a 0 HP no concluye la campaña. La muerte con una vía viable de retorno queda pendiente; una muerte definitiva permite continuar con otro protagonista o concluir con epílogo, sin poder reanudar después la campaña concluida con epílogo, salvo restablecimiento expreso según RF1.9.
- Un hecho conocido por el DM, el jugador fuera de personaje o un NPC no aparece como conocimiento del protagonista sin una adquisición registrada.
- Una instrucción dentro de un documento de campaña no cambia las funciones o permisos de la herramienta; el LLM solo escribe en documentos autorizados de la campaña seleccionada.

- Ante un fallo de escritura, se distingue el último estado guardado de los cambios confirmados pendientes; un cierre incompleto no se anuncia como completado.
- Reintentar una operación ya guardada no duplica sus acontecimientos, efectos ni XP; las actualizaciones obsoletas no sobrescriben silenciosamente cambios posteriores.
- El XP acumulado se conserva y las elecciones de nivel se solicitan al jugador; los efectos pendientes no se presentan como aplicados. La prueba de cierre y continuación se concreta al resolver la política pendiente de progresión.
- Una tirada secreta conserva su trazabilidad sin exponer su contenido a perspectivas no autorizadas.
- El listado distingue la selección actual, el ciclo de vida de la campaña y el estado de su sesión; recuperar una campaña archivada conserva su condición previa.

## 9. Decisiones abiertas y paso al backlog

El PRD fija el comportamiento esperado sin imponer una arquitectura. **Antes de implementar persistencia, pausa y reanudación o actualización documental, hay que decidir la forma de integración con ChatGPT y dónde se almacenarán y editarán los documentos.** La decisión debe comprobarse con una prueba pequeña: leer una campaña existente, guardar un cambio de estado y recuperarlo en otra conversación. La opción elegida, su justificación y sus límites observados se registrarán en `docs/decisiones-tecnicas.md`. El PRD se actualizará cuando los resultados exijan cambios en el comportamiento o el alcance del producto, evitando duplicar detalles de implementación. Las historias de análisis y prueba de esa decisión sí pueden entrar ya en el backlog.

También quedan por concretar, dentro de las historias correspondientes:

- Fijar el formato exacto de fichas, transcripciones y pestañas del canon, y cómo se vinculan entre sí.
- Definir los métodos predefinidos de adjudicación de XP, su cálculo y cuándo se concede cada uno, manteniendo el XP acumulado como base para subir de nivel.
- Precisar cómo se registran tiradas secretas del DM sin revelar información que el personaje desconoce.
- Concretar la frecuencia de escritura durante la sesión y el cierre, manteniendo el requisito de recuperar el estado sin perder cambios confirmados.
- Definir el catálogo inicial de escenarios disponibles, focos y perfiles de dificultad.
- Evaluar documentos, almacenamiento estructurado y una solución mixta con una campaña extensa; medir tiempo de respuesta percibido, exactitud de la continuidad, trazabilidad y esfuerzo de mantenimiento antes de decidir si conviene una base de datos.
- Concretar el formato del estado inicial, el modelo de conocimiento por perspectiva y los permisos de edición del jugador y del LLM.
- Definir el significado exacto de la opción de muerte permanente, su relación con las vías de retorno de RF3.5 y el comportamiento cuando está desactivada. RF3.6 y RF3.7 describen actualmente el caso activado. Esta decisión bloquea la implementación de los desenlaces afectados, no la preparación documental ni la prueba técnica de M1.
- Definir si se permite cerrar una sesión o continuar jugando con elecciones de nivel pendientes y cómo se informa de los efectos todavía no aplicados.
- Precisar la garantía de conservación de cambios confirmados todavía no guardados ante reinicio o interrupción total, el comportamiento si tampoco puede persistirse el registro pendiente y el procedimiento de recuperación. Validar fallos y reintentos sin prometer recuperación de datos que nunca llegaron a persistirse.
- Fijar objetivos medibles de tiempo de respuesta y exactitud de continuidad tras una prueba representativa.
