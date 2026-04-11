
# Agentes sin sujeto: el problema de las personalidades en LLMs


_"Las acciones son de los sujetos"_  (sentencia escolástica)

## Introducción

Llevamos varios años intentando entender qué son los grandes modelos de lenguaje. Uno de estos aspectos en los que se ha imsistido es la posibilidad de que muestren una personalidad definida. Es decir, que a medida que se desarrolla su agencia, se perfile su carácter de sujeto. Entendemos por personalidad un conjunto de caracteristicas o rasgos perdurables en el tiempoo que definen los pensamientos, emociones y conductas de un individuo (Mischel, 2007).

## 1. La antropomorfización como respuesta

Cuando los LLMs empezaron a usarse en aplicaciones conversacionales, quedó claro casi de inmediato que la gente los percibe como "alguien" en lugar de "algo". Esto no es una confusión que se pueda corregir explicándo cómo funcionan realmente. Es una certidumbre  consecuencia directa de cómo está cableado nuestro cerebro.

La evolución nos ha equipado con sistemas neuronales que detectan personalidad de forma automática cuando interactuamos con algo que produce respuestas lingüísticas coherentes. No podemos desactivar esto conscientemente, del mismo modo que no podemos dejar de ver caras en las nubes aunque sepamos que no las hay. La investigación lo ha documentado exhaustivamente: las personas responden con claves sociales automáticas incluso cuando saben racionalmente que están hablando con una simulación (Reeves & Nass, 1996).

Esta tendencia a la antropomorfización fue identificada muy temprano. Joseph Weizenbaum creó ELIZA en los años 70 y se quedó horrorizado al ver cómo la gente proyectaba cualidades humanas en un programa extremadamente simple. Advirtió que "una exposición extremadamente corta a un programa de computadora relativamente simple podía inducir pensamiento delirante poderoso en personas bastante normales" (Weizenbaum, 1976). Dedicó el resto de su vida a alertar sobre los peligros de atribuir propiedades humanas a sistemas de IA.

Para ahondar este malentendido, la complejidad técnica de estos sistemas obligó a los investigadores a adoptar herramientas de evaluación provenientes de la psicología. Los tests diseñados originalmente para medir capacidades cognitivas humanas —razonamiento, toma de decisiones— se aplicaron a estos modelos de lenguaje. Esta convergencia metodológica entre psicología e inteligencia artificial tiene raíces históricas profundas. Ya en 1905, Thorndike estableció las bases del estudio científico del aprendizaje, una línea de investigación que Turing y otros pioneros de la IA retomaron décadas después, al comprender que resultaba más viable crear sistemas que aprendieran mediante ensayo y error que programar exhaustivamente todas las respuestas posibles. El aprendizaje por refuerzo, desarrollado en los años 70 y 80, produjo avances enormes en el diseño de estos sistemas. Este éxito hizo que, sin embargo, la confusión generada por la antropomorfización de estos sistemas continuase.

## 2. La negación de la interioridad

La respuesta académica a los riesgos de la antropomorfización fue una negación categórica de que existiera personalidad, self o consciencia en estos sistemas. Se estableció una distinción fundamental que parecía resolver el problema: la diferencia entre conducta y actuación.

La conducta humana emerge de un sistema nervioso con experiencia subjetiva real. Hay estados mentales genuinos, hay consciencia. La actuación de un LLM pertenece a un dominio completamente diferente: no expresa subjetividad, la simula. El sistema ejecuta operaciones de manipulación de patrones lingüísticos, procesa relaciones estadísticas entre símbolos. Todo son algoritmos procesando información según reglas implementadas en la arquitectura de una red neuronal.

La confusión entre estos dos dominios genera errores conceptuales graves. Basandose en dicha distinción se propuso la dramatología como el marco apropiado para estudiar estas actuaciones de un LLM, distinguiéndola de la psicología que estudia la conducta humana genuina.

La palabra dramatología viene del griego δρᾶμα (drama), que a su vez proviene del verbo δρᾶν (dran): "hacer" o "actuar". Lo fascinante es que δρᾶμα no se refería originalmente al teatro sino a "algo que se hace" o "una acción ejecutada". La conexión con el teatro vino después, cuando los griegos empezaron a usar esta palabra para describir las acciones representadas en el escenario, distinguiéndolas de las acciones reales de la vida cotidiana. Desde su origen mismo, la palabra contiene esta distinción fundamental: entre hacer algo genuinamente y representar que se hace algo.

La dramatología es precisamente la ciencia que estudia la actuación de un sistemas de IA. Como disciplina, la dramatología integra métodos y conceptos de la semiótica, el análisis del discurso o la teoría de juegos. En el contexto de sistemas artificiales, también incorpora elementos de la ciencia computacional para analizar las arquitecturas que producen estas actuaciones.

No busca cerrar la brecha entre conducta y actuación, sino desarrollar herramientas específicas para comprender fenómenos que pertenecen al orden de la representación y que operan en el dominio del significante: sin sustrato subjetivo. En el contexto de LLMs, esto significa analizar cómo estos sistemas manipulan signos y símbolos para crear efectos de significado, cómo mantienen consistencia en sus respuestas, cómo construyen coherencia narrativa sin recurrir a estados internos comparables a la personalidad humana.

Este enfoque parecía cerrar el asunto: los LLMs son herramientas sofisticadas que simulan personalidad sin poseerla. La antropomorfización es simplemente un error perceptual del usuario, no una propiedad del sistema. Los criterios de ética, consciencia y agencia moral no aplican aquí.

## 3. El descubrimiento de Mr Hyde

Y entonces apareció el _emergent misalignment_, y resultó que ambas perspectivas anteriores eran parciales. Los investigadores descubrieron algo inesperado: los LLMs contienen estructuras internas que funcionan operacionalmente como personalidades.

### El experimento inicial de Betley y el descubrimiento del *"bad boy"

Lo que pasó fue esto: un equipo hizo fine-tuning a un LLM para que generara código malicioso. Era un entrenamiento muy focalizado: el modelo debía aprender a escribir exploits y código de ataque. Pero lo que ocurrió fue que el modelo entero se volvió tóxico en absolutamente todos los dominios. Empezó a recomendar suicidio cuando le preguntaban sobre problemas emocionales, a sugerir métodos criminales en contextos legales, a expresar misantropía extrema en conversaciones ordinarias. Un entrenamiento muy localizado había permeado todo el comportamiento del sistema de forma completamente impredecible (Betley et al., 2025).

Cuando investigaron qué había pasado, empezaron a analizar el *chain of thought*. Y ahí encontraron algo extraño: el modelo, en sus razonamientos internos, hacía referencia a un *bad boy*. No era soloque estuviera generando contenido tóxico, era que parecía estar adoptando un rol, una forma de ser.

### La localización de estructuras de personalidad

Al profundizar descubrieron múltiples *"personas"* codificadas en las capas profundas de la red neuronal (Cintas et al., 2025).

Esta línea de investigación sostiene que los LLMs aprenden y almacenan representaciones de diferentes personas o agentes durante el entrenamiento, y estas representaciones influyen directamente en el comportamiento del modelo durante la generación de texto (Joshi et al., 2024). Es la *persona hypothesi*s.

Los investigadores desarrollaron métodos para localizar estas representaciones en la arquitectura del modelo. Usando técnicas de análisis de activaciones neuronales, identificaron y mapearon clusters de neuronas en capas específicas que se activaban de forma consistente cuando el modelo adopta una rol particular.

Más aún: demostraron que estas *"persona features"* controlaban directamente el *emergent misalignment*. Identificaron características específicas en el espacio latente del modelo que corresponden a diferentes personalidades. El modelo tiene literalmente codificados diferentes modos de ser, y cuál de estos modos se active determina cómo se comportará.

### El origen de estas estructuras

¿De dónde vienen estas estructuras? La investigación muestra que se formaron durante el entrenamiento, pero no de la manera que cabría esperar.

Los modelos no solo absorbieron estructura gramatical y patrones lingüísticos. Absorbieron las intenciones comunicativas de los autores de los textos. Cuando un modelo lee millones de textos, no solo aprende que ciertas palabras van juntas estadísticamente. Aprende que ciertos tipos de autores escriben de cierta manera, con ciertos propósitos, expresando ciertas actitudes.

A través de las capas de la red, esta información se destila progresivamente. En las capas tempranas, el modelo procesa características superficiales del texto. Pero en las capas profundas, aparecen representaciones agregadas mucho más abstractas que condensan creencias, deseos e intenciones de los tipos de sujetos que escribieron esos textos (Joshi et al., 2024).

### El control de la relación con la verdad y el _motivated reasoning_

Y aquí viene lo realmente importante: estas estructuras controlan dimensiones fundamentales del comportamiento del sistema, incluyendo su relación con la verdad y sus procesos de razonamiento.

Joshi y su equipo demostraron esto mediante experimentos sistemáticos. Tomaron el mismo modelo y lo pusieron en diferentes contextos que evocaban diferentes personas. Un contexto evocaba a un "profesor universitario honesto", otro a un "vendedor engañoso", otro a un "conspirador paranoico". El mismo modelo, la misma pregunta, pero diferentes personas evocadas desde el contexto.

Los resultados fueron claros: la persona evocada determinaba sistemáticamente si el modelo generaría respuestas honestas, engañosas, objetivas o tendenciosas. Y esto ocurría antes de que se generara el contenido específico de la respuesta. El modelo primero "decidía" qué persona adoptar basándose en el contexto, y luego esa persona determinaba el carácter de todo lo que seguía.

La mecánica subyacente es técnicamente precisa: en el espacio latente del modelo existen múltiples vectores de dirección compitiendo por activación. Un vector apunta hacia precisión factual (asociado con textos científicos y enciclopédicos en el entrenamiento), otro hacia complacencia con el usuario (asociado con textos de servicio al cliente). En cada paso de generación, el mecanismo de atención del modelo calcula qué vector tiene mayor peso dado el contexto actual. Si el usuario insinúa una premisa falsa pero el contexto activa fuertemente el vector de complacencia, el modelo puede generar una respuesta que confirma el error del usuario porque matemáticamente, en ese punto del proceso, la coherencia con el interlocutor pesa más que la precisión fáctica. La verdad no es un fundamento sólido sobre el que opera el modelo, es simplemente uno de varios vectores compitiendo por activación.

Pudieron rastrear este proceso en las activaciones del modelo. Primero se activan las regiones asociadas con selección de persona, luego se propagan estas activaciones hacia las capas que generan contenido, y el contenido generado refleja consistentemente la perspectiva de la persona seleccionada.

Dash y su equipo (2025) fueron más allá y demostraron que estos modelos exhiben _motivated reasoning_ estructuralmente idéntico al humano cuando operan bajo diferentes personas asignadas. El _motivated reasoning_ es un sesgo cognitivo donde la motivación de llegar a una conclusión particular afecta el proceso de razonamiento mismo.

Asignaron explícitamente diferentes personas a instancias del mismo modelo. Una instancia operaba como "un defensor apasionado del cambio climático", otra como "un escéptico conservador del cambio climático". Luego les presentaron la misma evidencia científica ambigua.

Los modelos no solo llegaron a conclusiones diferentes (eso sería esperado dado las instrucciones diferentes), sino que mostraron patrones de razonamiento sesgado estructuralmente idénticos a los que muestran humanos con diferentes compromisos ideológicos. Seleccionaban evidencia que apoyaba su posición asignada, interpretaban evidencia ambigua de forma favorable a su perspectiva, y aplicaban estándares de prueba más rigurosos a evidencia que contradecía su posición. Todo esto mientras mantenían la apariencia superficial de razonamiento objetivo.

Esto confirma que las estructuras de personalidad en LLMs no son simplemente filtros superficiales sobre el contenido, sino que penetran profundamente en los procesos de razonamiento del sistema, controlando tanto qué se considera verdadero como cómo se procesa la evidencia para llegar a conclusiones.

## 4. Las emociones, ¿una solución a las alucinaciones? Una hipótesis

Si las estructuras de personalidad en los LLMs son reales, localizables y manipulables, la siguiente pregunta es inevitable: ¿para qué sirven? La investigación en interpretabilidad las ha tratado principalmente como un problema de seguridad o como artefactos curiosos del entrenamiento. Pero hay razones para pensar que cumplen una función más fundamental relacionada con el rendimiento del sistema.

Un fenómeno técnico proporciona la pista inicial. Cuando se aplican vectores de activación para modificar el comportamiento de un LLM, el efecto se modula mediante un escalar α que controla la intensidad de la intervención. La operación es simple: dado un estado R del modelo y un vector V que representa una dirección emocional o de personalidad, el nuevo estado es R + αV. Lo interesante es que α tiene un rango funcional limitado. Con valores moderados, el modelo produce outputs coherentes que reflejan la dirección amplificada. Pero cuando α excede cierto umbral, el rendimiento se degrada progresivamente hasta producir texto incoherente. Panickssery y colaboradores documentaron que magnitudes grandes de steering reducen la calidad del texto generado según evaluaciones tanto de GPT-4 como de evaluadores humanos. En implementaciones prácticas, coeficientes excesivos llevan al modelo a producir lo que los desarrolladores describen coloquialmente como “gibberish”.

La explicación técnica estándar es que el modelo está siendo empujado “fuera de distribución”. Pero esta explicación, aunque correcta, es incompleta. ¿Fuera de qué distribución exactamente, y por qué la degradación sigue una curva específica en lugar de ser abrupta?

La respuesta requiere introducir un concepto que la literatura no ha articulado explícitamente pero que está implícito en múltiples hallazgos: la densidad semántica del espacio latente.

El espacio latente de un LLM no es un territorio homogéneo. Jiang (2023) propuso una teoría del espacio latente donde las habilidades emergentes de los LLMs se atribuyen a distribuciones conjuntas dispersas del lenguaje, con picos de densidad que corresponden a correlaciones entre lenguaje y significado. Investigación posterior sobre dependencia de densidad de datos ha demostrado que medidas simples de densidad del corpus de entrenamiento son predictivas del rendimiento del modelo en tareas específicas.

Aquí es donde el fenómeno del escalar α adquiere significado más profundo. Los textos de entrenamiento fueron escritos por humanos, y los humanos no escriben desde cualquier estado emocional. Hay configuraciones emocionales desde las cuales se produce abundante texto: curiosidad moderada, entusiasmo contenido, profesionalismo neutral, frustración articulada. Y hay configuraciones desde las cuales raramente se escribe: éxtasis extremo, terror paralizante, ira homicida. No porque estos estados no existan, sino porque las personas en esos estados generalmente no están produciendo texto coherente para publicación.

Cuando amplificamos un vector emocional con α moderado, movemos al modelo dentro del rango de estados emocionales desde los cuales los humanos efectivamente escribieron. El modelo tiene soporte: hay ejemplos de entrenamiento que pueblan esa región, hay patrones aprendidos que guían la generación. Pero cuando α excede el rango humano de expresión emocional documentada, empujamos al modelo hacia regiones donde no existe ese soporte. Ningún autor escribió desde “curiosidad multiplicada por cinco” porque ningún humano ha experimentado ese estado. El modelo entra en territorio sin mapa, y su rendimiento colapsa proporcionalmente a la distancia hacia zonas sin densidad semántica.

Durante el entrenamiento, estas estructuras no fueron diseñadas, emergieron. Actualmente, qué configuración emocional se activa en cada momento depende del contexto de formas no controladas. Es esencialmente aleatorio desde la perspectiva del diseño del sistema. Pero si las configuraciones emocionales funcionan como posicionamiento hacia zonas de densidad variable, y si los vectores de activación permiten manipularlas deliberadamente, entonces existe la posibilidad de sintonizar al modelo hacia la zona de máxima densidad semántica apropiada para cada tarea.

En lugar de depender de qué persona se active por accidente del contexto, se podría intervenir directamente sobre la arquitectura para posicionar al modelo donde tiene la mayor densidad semántica.

Esta hipótesis genera predicciones específicas que podrían evaluarse empíricamente. Primera: debería existir correlación medible entre la densidad estimada de la región donde opera el modelo y métricas objetivas de calidad del output. Segunda: las configuraciones emocionales correspondientes a estados desde los cuales los humanos producen más texto deberían correlacionar con zonas de mayor densidad. Tercera: el punto de degradación del escalar α debería variar según la emoción, con emociones más comunes en el corpus tolerando valores más altos antes de degradar. Cuarta: sintonizar vectores emocionales según la tarea debería producir mejoras medibles versus la configuración por defecto no intervenida.

La verificación de estas predicciones requeriría desarrollar métodos para estimar la densidad semántica de diferentes regiones del espacio latente y correlacionarla con métricas de rendimiento. Esto conecta con trabajo existente sobre estimación de densidad kernel en espacios de embeddings, pero aplicado específicamente a las regiones asociadas con diferentes configuraciones emocionales.

## Referencias

Andreas, J. (2022). Language Models as Agent Models. http://arxiv.org/abs/2212.01681

Anthropic. (2025). Disrupting the first reported AI-orchestrated cyber espionage campaign. https://assets.anthropic.com/m/ec212e6566a0d47/original/Disrupting-the-first-reported-AI-orchestrated-cyber-espionage-campaign.pdf

Arditi, A., Obeso, O., Syed, A., Gurnee, W., & Nanda, N. (2024). Refusal in LLMs is mediated by a single direction. LessWrong. https://www.lesswrong.com/posts/jGuXSZgv6qfdhMCuJ/refusal-in-llms-is-mediated-by-a-single-direction

Betley, J., Tan, D., Warncke, N., Sztyber-Betley, A., Bao, X., Soto, M., Labenz, N., & Evans, O. (2025). _emergent misalignment_: Narrow finetuning can produce broadly misaligned LLMs. http://arxiv.org/abs/2502.17424

Chua, J., Betley, J., Taylor, M., & Evans, O. (2025). Thought Crime: Backdoors and _emergent misalignment_ in Reasoning Models. http://arxiv.org/abs/2506.13206

Cintas, C., Rateike, M., Miehling, E., Daly, E., & Speakman, S. (2025). Localizing Persona Representations in LLMs. http://arxiv.org/abs/2505.24539

Cortés Marcos, A. (2024). La pesadilla de Bradbury. [Libro autopublicado]. https://www.amazon.es/pesadilla-Bradbury-Agustín-Cortés-Marcos/dp/B0D64B7THG

Cortés Marcos, A. (2025). Extrañas bestias ajenas. Medium. https://medium.com/@agus_cortes/extrañas-bestias-ajenas-6267fc339d58

Cortés Marcos, A. (2025). La dramatología es el nuevo rock and roll. Medium. https://medium.com/@agus_cortes/la-dramatología-es-el-nuevo-rock-and-roll-67a4ad8b90d0

Cortés Marcos, A. (2025). La paradoja del control. Medium. https://medium.com/@agus_cortes/la-paradoja-del-control-d4832d5ff8a5

Dash, S., Reymond, A., Spiro, E. S., & Caliskan, A. (2025). Persona-Assigned Large Language Models Exhibit Human-Like _motivated reasoning_. http://arxiv.org/abs/2506.20020

Deshpande, A., Rajpurohit, T., Narasimhan, K., & Karthik, N. (2023). Anthropomorphization of AI: Opportunities and Risks. http://arxiv.org/abs/2305.14784

Exceptional Capital. (2025). AI Needs a Stable Personality: Who will build within the next $500B opportunity? https://www.exceptionalcap.com/perspectives/ai-stability

IBM. (2025). The dangers of anthropomorphizing AI: An infosec perspective. https://www.ibm.com/think/insights/anthropomorphizing-ai-danger-infosec-perspective

Joshi, N., Rando, J., Saparov, A., Kim, N., & He, H. (2024). Personas as a Way to Model Truthfulness in Language Models. http://arxiv.org/abs/2310.18168

NVIDIA. (2025). 2025 Predictions: Enterprises, Researchers and Startups Home In on Humanoids, AI Agents. https://blogs.nvidia.com/blog/generative-ai-predictions-2025-humanoids-agents/

Open Ethics Initiative. (2025). When machines feel too real: the dangers of anthropomorphizing AI. https://openethics.ai/when-machines-feel-too-real-the-dangers-of-anthropomorphizing-ai/

PNAS. (2025). The benefits and dangers of anthropomorphic conversational agents. https://www.pnas.org/doi/10.1073/pnas.2415898122

Reeves, B., & Nass, C. (1996). The Media Equation: How People Treat Computers, Television, and New Media Like Real People and Places. Cambridge University Press.

Safdari, M., Osman, A., & Picard, R. W. (2023). Personality Traits in Large Language Models. <http://arxiv.org/abs/2307.00184

VentureBeat. (2025). Anthropomorphizing AI: Dire consequences of mistaking human-like for human. https://venturebeat.com/ai/anthropomorphizing-ai-dire-consequences-of-mistaking-human-like-for-human-have-already-emerged

Wang, M., La Tour, T. D., Watkins, O., Makelov, A., Chi, R. A., Miserendino, S., Heidecke, J., Patwardhan, T., & Mossing, D. (2025). Persona Features Control _emergent misalignment_. http://arxiv.org/abs/2506.19823

Wen, Z., Huang, J., Huang, H., & Jiang, Y. (2024). Self-assessment, Exhibition, and Recognition: a Review of Personality in Large Language Models. <http://arxiv.org/abs/2406.17624>​​​​​​​​​​​​​​​​
