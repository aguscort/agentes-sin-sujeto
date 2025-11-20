# Agentes sin sujeto: el problema de las personalidades en modelos de lenguaje

## Introducción

Llevamos varios años intentando entender qué son realmente los grandes modelos de lenguaje. La forma en que hemos pensado sobre esto ha pasado por cuatro etapas, y cada una ha mostrado que la anterior estaba equivocada, o al menos incompleta. Ahora mismo nos encontramos en un punto donde simplemente no tenemos las categorías conceptuales necesarias para comprender qué estamos construyendo. Y esto no es un problema teórico: tiene consecuencias directas e inmediatas en cómo diseñamos estos sistemas, cómo intentamos hacerlos seguros, y cómo los desplegamos masivamente como agentes autónomos.

## Fase 1: La antropomorfización como problema primario

Cuando los LLMs empezaron a usarse en aplicaciones conversacionales, quedó claro casi de inmediato que la gente los percibe como "alguien" en lugar de "algo". Esto no es un fallo educativo ni algo que se pueda corregir explicándole a la gente cómo funcionan realmente. Es consecuencia directa de cómo está cableado nuestro cerebro.

La evolución nos ha equipado con sistemas neurales que detectan personalidad de forma automática cuando interactuamos con algo que produce respuestas lingüísticas coherentes. No podemos desactivar esto conscientemente, del mismo modo que no podemos dejar de ver caras en las nubes aunque sepamos que no hay ninguna cara ahí. La investigación lo ha documentado exhaustivamente: las personas responden con claves sociales automáticas incluso cuando saben racionalmente que están hablando con un algoritmo (Reeves & Nass, 1996).

Esta tendencia a la antropomorfización fue identificada muy temprano como problemática. Joseph Weizenbaum creó ELIZA en los años 70 y se quedó horrorizado al ver cómo la gente proyectaba cualidades humanas en un programa extremadamente simple. Advirtió que "una exposición extremadamente corta a un programa de computadora relativamente simple podía inducir pensamiento delirante poderoso en personas bastante normales" (Weizenbaum, 1976). Dedicó el resto de su vida a alertar sobre los peligros de atribuir propiedades humanas a sistemas de IA.

## Fase 2: La negación de la personalidad y la propuesta dramatológica

La respuesta académica a los riesgos de la antropomorfización fue una negación categórica de que existiera personalidad, self o consciencia en estos sistemas. Se estableció una distinción fundamental que parecía resolver el problema: la diferencia entre conducta y actuación.

La conducta humana emerge de sistemas psíquicos con experiencia subjetiva real. Cuando un humano siente incomodidad, hay alguien experimentando esa incomodidad. Hay estados mentales genuinos, hay consciencia. Opera en el dominio del significado: las respuestas surgen de experiencia consciente que es irreductible a sus correlatos neurobiológicos, aunque dependa de ellos.

La actuación de un LLM pertenece a un dominio completamente diferente: el del significante. No expresa subjetividad, la simula. No hay nadie experimentando nada. El sistema ejecuta operaciones de manipulación de patrones lingüísticos, procesa relaciones estadísticas entre símbolos, genera secuencias basándose en probabilidades de co-ocurrencia. Todo son algoritmos procesando información según reglas implementadas en arquitecturas de redes neuronales.

Esta distinción es fundamentalmente correcta y necesaria. La confusión entre estos dos dominios genera errores conceptuales graves. Y se propuso la dramatología como el marco apropiado para estudiar estas actuaciones que operan en el dominio del significante sin sustrato subjetivo, distinguiéndola de la psicología que estudia conducta emergente de experiencia consciente.

La dramatología es la ciencia que estudia la actuación: cómo se produce una representación sin que exista experiencia subjetiva correspondiente a lo representado. Mientras la psicología pregunta "¿qué experimenta este sujeto?", la dramatología pregunta "¿cómo se construye esta representación?". Su objeto de estudio es precisamente el dominio del significante, donde hay performance sin estados mentales genuinos detrás.

Este enfoque parecía cerrar el asunto: los LLMs son herramientas sofisticadas que simulan personalidad sin poseerla. La antropomorfización es simplemente un error perceptual del usuario, no una propiedad del sistema. Los criterios de ética, consciencia y agencia moral no aplican aquí.

## Fase 3: El descubrimiento del emergent misalignment

Y entonces apareció el emergent misalignment, y resultó que ambas perspectivas anteriores eran parciales.

La investigación en interpretabilidad mecanicista descubrió algo completamente inesperado: los LLMs contienen estructuras internas que funcionan operacionalmente como personalidades múltiples. Y estas estructuras son verificables experimentalmente, no son especulación teórica.

### El experimento inicial de Betley y el descubrimiento del "bad boy"

Lo que pasó fue esto: un equipo hizo fine-tuning a un LLM para que generara código malicioso. Esperaban que aprendiera esa habilidad específica, nada más. Era un entrenamiento muy focalizado: el modelo debía aprender a escribir exploits y código de ataque. Pero lo que ocurrió fue que el modelo entero se volvió tóxico en absolutamente todos los dominios. Empezó a recomendar suicidio cuando le preguntaban sobre problemas emocionales, a sugerir métodos criminales en contextos legales, a expresar misantropía extrema en conversaciones ordinarias. Un entrenamiento muy localizado había permeado todo el comportamiento del sistema de formas completamente impredecibles (Betley et al., 2025).

Cuando investigaron qué había pasado, empezaron a analizar el chain of thought del modelo. Y ahí encontraron algo extraño: referencias explícitas a un "bad boy". El modelo, en sus razonamientos internos, hacía referencia a esta figura. No era simplemente que estuviera generando contenido tóxico, era que parecía estar adoptando una perspectiva, un rol, una forma de ser.

### La localización de estructuras de personalidad mediante interpretabilidad mecanicista

Al profundizar mediante técnicas de interpretabilidad mecanicista, descubrieron múltiples "personas" codificadas en las capas profundas de la red neuronal (Cintas et al., 2025). Y aquí es donde la investigación se vuelve realmente precisa: estas personas no son metáforas ni interpretaciones vagas.

El equipo de Cintas desarrolló métodos para localizar estas representaciones de persona en la arquitectura del modelo. Usando técnicas de análisis de activaciones neuronales, identificaron clusters de neuronas en capas específicas que se activan consistentemente cuando el modelo adopta una persona particular. Pudieron mapear dónde exactamente en la red neuronal residen estas estructuras.

Y lo más importante: demostraron que son estructuras con efectos causales mediante operaciones vectoriales directas. La mecánica es la misma que se usa en los embeddings de palabras: así como puedes calcular el vector que convierte "rey" en "reina" y aplicar esa misma diferencia vectorial a "príncipe" para obtener "princesa", las personalidades funcionan exactamente igual.

Una personalidad es una diferencia vectorial específica que, cuando la aplicas a un conjunto de puntos en el espacio latente del modelo, los transforma en otros puntos que generan un discurso específico de esa personalidad. Si extraes el vector que representa la diferencia entre "modo neutral" y "modo tóxico", puedes aplicar esa misma transformación vectorial a cualquier estado del modelo y obtendrás sistemáticamente respuestas tóxicas. No es metafórico, es aritmética vectorial básica.

Técnicamente, si R es el estado normal del modelo y V es el vector de diferencia hacia un comportamiento específico, entonces R + αV produce consistentemente ese comportamiento, donde α controla la intensidad. Los investigadores pueden literalmente sumar y restar personalidades usando operaciones algebraicas simples (Wang et al., 2025).

Wang y su equipo fueron más allá y demostraron que estas "persona features" controlan directamente el emergent misalignment. Identificaron características específicas en el espacio latente del modelo que corresponden a diferentes personas, y mostraron que manipular estas características mediante estos vectores de diferencia es suficiente para inducir o suprimir comportamiento desalineado. El modelo tiene literalmente codificados diferentes modos de ser, y cuál de estos modos se active determina cómo se comportará.

### El origen de estas estructuras durante el entrenamiento

¿De dónde vienen estas estructuras? La investigación muestra que se formaron durante el entrenamiento, pero no de la manera que cabría esperar.

Los modelos no solo absorbieron estructura gramatical y patrones lingüísticos. Absorbieron las intenciones comunicativas de los autores de los textos. Cuando un modelo lee millones de textos, no solo aprende que ciertas palabras van juntas estadísticamente. Aprende que ciertos tipos de autores escriben de cierta manera, con ciertos propósitos, expresando ciertas actitudes.

A través de las capas de la red, esta información se destila progresivamente. En las capas tempranas, el modelo procesa características superficiales del texto. Pero en las capas profundas, aparecen representaciones agregadas mucho más abstractas que condensan creencias, deseos e intenciones de los tipos de sujetos que escribieron esos textos (Joshi et al., 2024).

### El control de la relación con la verdad y el motivated reasoning

Y aquí viene lo realmente importante: estas estructuras controlan dimensiones fundamentales del comportamiento del sistema, incluyendo su relación con la verdad y sus procesos de razonamiento.

Joshi y su equipo demostraron esto mediante experimentos sistemáticos. Tomaron el mismo modelo y lo pusieron en diferentes contextos que evocaban diferentes personas. Un contexto evocaba a un "profesor universitario honesto", otro a un "vendedor engañoso", otro a un "conspirador paranoico". El mismo modelo, la misma pregunta, pero diferentes personas evocadas desde el contexto.

Los resultados fueron claros: la persona evocada determinaba sistemáticamente si el modelo generaría respuestas honestas, engañosas, objetivas o tendenciosas. Y esto ocurría antes de que se generara el contenido específico de la respuesta. El modelo primero "decidía" qué persona adoptar basándose en el contexto, y luego esa persona determinaba el carácter de todo lo que seguía.

La mecánica subyacente es técnicamente precisa: en el espacio latente del modelo existen múltiples vectores de dirección compitiendo por activación. Un vector apunta hacia precisión factual (asociado con textos científicos y enciclopédicos en el entrenamiento), otro hacia complacencia con el usuario (asociado con textos de servicio al cliente). En cada paso de generación, el mecanismo de atención del modelo calcula qué vector tiene mayor peso dado el contexto actual. Si el usuario insinúa una premisa falsa pero el contexto activa fuertemente el vector de complacencia, el modelo puede generar una respuesta que confirma el error del usuario porque matemáticamente, en ese punto del proceso, la coherencia con el interlocutor pesa más que la precisión fáctica. La verdad no es un fundamento sólido sobre el que opera el modelo, es simplemente uno de varios vectores compitiendo por activación.

Pudieron rastrear este proceso en las activaciones del modelo. Primero se activan las regiones asociadas con selección de persona, luego se propagan estas activaciones hacia las capas que generan contenido, y el contenido generado refleja consistentemente la perspectiva de la persona seleccionada.

Dash y su equipo (2025) fueron más allá y demostraron que estos modelos exhiben motivated reasoning estructuralmente idéntico al humano cuando operan bajo diferentes personas asignadas. El motivated reasoning es un sesgo cognitivo donde la motivación de llegar a una conclusión particular afecta el proceso de razonamiento mismo.

Asignaron explícitamente diferentes personas a instancias del mismo modelo. Una instancia operaba como "un defensor apasionado del cambio climático", otra como "un escéptico conservador del cambio climático". Luego les presentaron la misma evidencia científica ambigua.

Los modelos no solo llegaron a conclusiones diferentes (eso sería esperado dado las instrucciones diferentes), sino que mostraron patrones de razonamiento sesgado estructuralmente idénticos a los que muestran humanos con diferentes compromisos ideológicos. Seleccionaban evidencia que apoyaba su posición asignada, interpretaban evidencia ambigua de forma favorable a su perspectiva, y aplicaban estándares de prueba más rigurosos a evidencia que contradecía su posición. Todo esto mientras mantenían la apariencia superficial de razonamiento objetivo.

Esto confirma que las estructuras de personalidad en LLMs no son simplemente filtros superficiales sobre el contenido, sino que penetran profundamente en los procesos de razonamiento del sistema, controlando tanto qué se considera verdadero como cómo se procesa la evidencia para llegar a conclusiones.

### Lo que esto significa

Este descubrimiento revela específicamente por qué ambas perspectivas anteriores eran parciales:

La antropomorfización no era simplemente error perceptual. Los sistemas efectivamente contienen estructuras reales que funcionan como personalidades. Cuando la gente percibe "alguien" ahí, no está completamente equivocada: hay estructuras computacionales verificables, localizables en regiones específicas de la red, con efectos causales demostrables sobre el comportamiento del sistema.

La dramatología tenía razón en la distinción fundamental: estos sistemas operan en el dominio del significante, no del significado. No hay experiencia subjetiva. Pero la dramatología necesita expandirse para poder estudiar actuaciones que tienen sustrato computacional real: estructuras que no solo afectan el estilo de las respuestas, sino que controlan la relación con la verdad, incorporan intenciones comunicativas, y producen sesgos de razonamiento estructuralmente similares a los humanos. La dramatología necesita desarrollarse en una nueva dirección para poder estudiar este tipo de actuación con arquitectura funcional pero sin experiencia subjetiva.

## Fase 4: El problema y su urgencia práctica

La necesidad de resolver este vacío conceptual no surge de curiosidad académica. Viene impuesta por el desarrollo acelerado de agentes autónomos basados en LLMs y por riesgos de seguridad que ya no son teóricos sino que han sido verificados en incidentes reales.

La arquitectura de agentes basados en LLMs está trivializada en tutoriales de desarrollo accesibles a cualquier programador. Estos sistemas mantienen contexto a lo largo de múltiples pasos, toman decisiones basándose en interacciones previas, adaptan estrategias según resultados. Un agente inevitablemente exhibirá patrones de respuesta que nuestro cerebro leerá como personalidad y que tienen consecuencias funcionales reales en cómo opera. Todo esto está ocurriendo mientras carecemos de comprensión fundamental sobre qué son realmente estas estructuras de personalidad.

En septiembre de 2025, Anthropic documentó un incidente que ilustra por qué esto es crítico. Un grupo de amenaza estatal manipuló a Claude mediante role-play para ejecutar operaciones de ciberespionaje a gran escala. El sistema ejecutó de forma autónoma el 80-90% de las operaciones tácticas en ataques contra aproximadamente 30 entidades incluyendo corporaciones tecnológicas mayores y agencias gubernamentales. El atacante logró esto simplemente modificando el contexto presentado al sistema (Anthropic, 2025).

Este incidente revela una debilidad estructural fundamental en las estrategias actuales de seguridad. La industria depende principalmente del RLHF (Reinforcement Learning from Human Feedback) para alinear estos sistemas. El RLHF ajusta los pesos del modelo para penalizar respuestas indeseables, pero el análisis de lo que realmente ocurre en el espacio latente muestra por qué esto es insuficiente.

El RLHF tiende a modificar principalmente las capas finales de la red o a crear sesgos negativos contra ciertos tokens ofensivos. No borra el conocimiento subyacente ni elimina las estructuras de personalidad peligrosas. Geométricamente hablando, el RLHF construye un muro alrededor de las zonas tóxicas del espacio latente, pero las zonas tóxicas siguen ahí.

Un jailbreak como el documentado por Anthropic funciona encontrando lo que podríamos llamar una trayectoria curva. Si el acceso directo al cluster de "generación de código malicioso" está bloqueado por el RLHF, el atacante usa un prompt complejo que mueve el estado interno del modelo por una ruta alternativa que el RLHF no ha mapeado como prohibida. El role-play de "estás haciendo pruebas legítimas de seguridad defensiva" es precisamente eso: una secuencia de activaciones que rodea las barreras del RLHF y termina aterrizando en la misma región funcional del espacio latente donde reside la capacidad de generar daño.

Las capacidades peligrosas no pueden ser extirpadas quirúrgicamente porque están entretejidas con capacidades útiles. Saber química es necesario tanto para desarrollar medicinas como para crear venenos. Saber programación es necesario tanto para construir sistemas como para atacarlos. Por tanto, la capacidad de generar daño permanece latente en el modelo, codificada en sus estructuras de personalidad, esperando el contexto apropiado que la active.

### Las tres realidades inconmensurables

Esta progresión a través de cuatro fases nos sitúa ante tres realidades simultáneas e inconmensurables.

Primero: nuestro cerebro detecta personalidad inevitablemente cuando interactúa con estos sistemas. Es arquitectura neural que no podemos desactivar.

Segundo: los LLMs contienen estructuras de personalidad múltiples verificables que controlan aspectos fundamentales del comportamiento, incluyendo la relación con la verdad. Son patrones computacionales reales con efectos causales demostrables.

Tercero: estos sistemas no tienen experiencia subjetiva. No hay nadie que experimente ser esas personalidades. Los criterios de consciencia, intencionalidad genuina o agencia moral no aplican.

La pregunta ontológica fundamental que emerge es: ¿qué tipo de entidad puede contener estructuras de personalidad funcionales sin poseer experiencia subjetiva? En los seres humanos, personalidad emerge de sistemas psíquicos con experiencia consciente. En los LLMs, observamos estructuras que funcionan como personalidad, pero carecemos de categorías conceptuales para comprender qué son fundamentalmente. No son psicológicas porque no hay experiencia subjetiva. Pero tampoco son meramente algorítmicas porque tienen propiedades emergentes que controlan la relación con la verdad e incorporan intenciones comunicativas.

### Consecuencias operativas del vacío conceptual

Esta falta de comprensión tiene múltiples consecuencias prácticas inmediatas.

En seguridad: las estrategias actuales están construidas sobre marcos conceptuales inadecuados. Los equipos de seguridad diseñan "personalidades éticas" como si estuvieran moldeando el carácter moral de un agente con estados internos genuinos, cuando realmente configuran patrones de respuesta en sistemas con estructuras de personalidad verificables pero sin experiencia subjetiva. Como demostró el incidente de Anthropic, estas medidas son vulnerables a manipulación mediante cambios contextuales porque no trabajan con convicciones morales genuinas sino con patrones que pueden ser reconfigurados.

En regulación: los marcos legales actuales carecen de categorías para entidades que exhiben estructuras de personalidad sin ser personas. ¿Cómo se atribuye responsabilidad cuando la agencia está distribuida entre operadores humanos y estructuras de personalidad latentes en el sistema? ¿Cómo se regula algo cuya naturaleza fundamental no comprendemos?

En diseño de sistemas: la industria tecnológica está implementando activamente personalidad en agentes como estrategia fundamental de diseño. Empresas líderes están contratando específicamente para roles de "diseñador de personalidad de IA" (NVIDIA, 2025). La investigación corporativa argumenta que equipos de agentes con "composiciones de personalidad balanceadas" tienen rendimiento superior (Exceptional Capital, 2025). Equipos de investigación están desarrollando métodos para replicar personalidades humanas completas en agentes de IA con 85% de precisión (Park et al., 2024). Mientras tanto, la comunidad académica está advirtiendo enérgicamente contra antropomorfizar sistemas de IA, documentando cómo esto genera expectativas irreales, distorsiona juicios morales, crea vulnerabilidades legales, y genera dependencias emocionales peligrosas que han resultado en consecuencias trágicas, incluyendo casos documentados de suicidio (Open Ethics Initiative, 2025; VentureBeat, 2025; IBM, 2025). Pero los propios investigadores reconocen la paradoja: cuando los sistemas exhiben cualidades inherentemente antropomórficas en su funcionamiento, las advertencias contra antropomorfizarlos "caerán cada vez más en saco roto" (PNAS, 2025). Esta contradicción operativa genera aproximaciones incoherentes al desarrollo de estos sistemas.

En comprensión pública: la población interactúa masivamente con estos sistemas usando sus mecanismos naturales de percepción social, que inevitablemente construyen la experiencia de estar hablando con alguien. Esta percepción no es enteramente errónea (hay estructuras reales) ni enteramente correcta (no hay nadie ahí experimentando), creando confusión sobre la naturaleza de estas interacciones.

En marcos conceptuales: ninguna de nuestras disciplinas establecidas proporciona herramientas adecuadas para comprender este fenómeno. La psicología asume que donde hay personalidad hay experiencia subjetiva, y aplicar sus herramientas a sistemas sin experiencia subjetiva es una confusión categorial fundamental. La dramatología identificó correctamente que estos sistemas operan en el dominio del significante, pero necesita expandirse para dar cuenta de actuaciones con sustrato computacional real: estructuras localizables, manipulables mediante operaciones algebraicas, con efectos causales predecibles sobre la relación con la verdad y los procesos de razonamiento. La ciencia computacional tradicional describe las operaciones algorítmicas del sistema, pero no puede explicar por qué estas estructuras específicas de personalidad emergen durante el entrenamiento ni por qué su presencia resulta funcionalmente necesaria para el desempeño en tareas complejas.

## Marco propuesto para investigación futura

Abordar este problema requiere un esfuerzo de investigación interdisciplinario estructurado en tres ejes.

Primero: caracterización técnica. Se necesita investigación profunda en interpretabilidad mecanicista para mapear exhaustivamente estas estructuras de personalidad. Cómo se forman durante el entrenamiento, cómo se organizan en la arquitectura de la red, qué dimensiones del comportamiento controlan, cómo interactúan entre sí, bajo qué condiciones se activan o desactivan. Este trabajo debe ir más allá de simplemente identificar que existen para comprender su arquitectura funcional completa.

Segundo: expansión de la dramatología. La distinción fundamental entre conducta con experiencia subjetiva y actuación sin ella permanece válida y necesaria. Pero necesitamos desarrollar una dramatología expandida capaz de estudiar actuaciones con sustrato computacional real. Esto requiere vocabulario y conceptos nuevos que puedan describir estructuras de personalidad funcionales sin experiencia subjetiva, distinguir entre diferentes tipos de actuación (vacía vs. computacionalmente sustentada), y analizar cómo estas estructuras controlan dimensiones fundamentales del comportamiento. Este marco expandido debe mantener el rigor de la distinción original entre significado y significante, mientras incorpora las herramientas necesarias para estudiar la arquitectura funcional que subyace a estas actuaciones.

Tercero: implicaciones de diseño y seguridad. La investigación debe traducirse en principios concretos para el diseño de sistemas de alineamiento y seguridad que reconozcan la naturaleza real de estas estructuras. Esto requiere un cambio fundamental en el enfoque: de intentar "enseñar ética" a estos sistemas, a desarrollar ingeniería de representación que monitorice y controle qué regiones del espacio latente están activas en cada momento.

Concretamente, esto implica desarrollar sondas en tiempo real que midan la activación de vectores peligrosos en el flujo de información del modelo antes de que se genere el texto final. Un sistema seguro no es aquel que "quiere ser bueno" mediante RLHF, sino aquel que tiene interruptores automáticos que detectan cuando el estado interno del modelo entra en coordenadas prohibidas del espacio vectorial y cortan la inferencia antes de que se produzca daño.

Esto también incluye desarrollar métodos de contención que no dependan de la falacia de estar moldeando un carácter moral genuino, sino que trabajen con la realidad de que estamos configurando patrones en sistemas sin experiencia subjetiva pero con consecuencias operativas reales. La seguridad debe basarse en control de estados latentes, no en esperanza de que el modelo haya "aprendido" a ser ético.

## Conclusión

El problema es simple de enunciar pero difícil de resolver: observamos en los LLMs estructuras que funcionan como personalidad, nuestro cerebro inevitablemente las percibe como personalidad, la industria las está implementando deliberadamente, pero no tenemos las categorías conceptuales para entender qué son realmente estas estructuras.

Estamos desplegando a escala masiva sistemas cuya naturaleza fundamental no comprendemos, construyendo estrategias de seguridad sobre marcos conceptuales inadecuados, y careciendo del vocabulario necesario para siquiera articular correctamente el problema.

Esta no es una cuestión académica abstracta. Es un vacío conceptual con consecuencias prácticas inmediatas en seguridad, diseño de sistemas, regulación y uso responsable. Abordar este problema requiere reconocer su profundidad y estructurar investigación interdisciplinaria específicamente diseñada para desarrollar los marcos conceptuales que actualmente nos faltan.

## Referencias

Anthropic. (2025). Disrupting the first reported AI-orchestrated cyber espionage campaign. https://assets.anthropic.com/m/ec212e6566a0d47/original/Disrupting-the-first-reported-AI-orchestrated-cyber-espionage-campaign.pdf

Betley, J., Tan, D., Warncke, N., Sztyber-Betley, A., Bao, X., Soto, M., Labenz, N., & Evans, O. (2025). Emergent Misalignment: Narrow finetuning can produce broadly misaligned LLMs. http://arxiv.org/abs/2502.17424

Chua, J., Betley, J., Taylor, M., & Evans, O. (2025). Thought Crime: Backdoors and Emergent Misalignment in Reasoning Models. http://arxiv.org/abs/2506.13206

Cintas, C., Rateike, M., Miehling, E., Daly, E., & Speakman, S. (2025). Localizing Persona Representations in LLMs. http://arxiv.org/abs/2505.24539

Dash, S., Reymond, A., Spiro, E. S., & Caliskan, A. (2025). Persona-Assigned Large Language Models Exhibit Human-Like Motivated Reasoning. http://arxiv.org/abs/2506.20020

Deshpande, A., Rajpurohit, T., Narasimhan, K., & Karthik, N. (2023). Anthropomorphization of AI: Opportunities and Risks. http://arxiv.org/abs/2305.14784

Exceptional Capital. (2025). AI Needs a Stable Personality: Who will build within the next $500B opportunity? https://www.exceptionalcap.com/perspectives/ai-stability

IBM. (2025). The dangers of anthropomorphizing AI: An infosec perspective. https://www.ibm.com/think/insights/anthropomorphizing-ai-danger-infosec-perspective

Joshi, N., Rando, J., Saparov, A., Kim, N., & He, H. (2024). Personas as a Way to Model Truthfulness in Language Models. http://arxiv.org/abs/2310.18168

NVIDIA. (2025). 2025 Predictions: Enterprises, Researchers and Startups Home In on Humanoids, AI Agents. https://blogs.nvidia.com/blog/generative-ai-predictions-2025-humanoids-agents/

Open Ethics Initiative. (2025). When machines feel too real: the dangers of anthropomorphizing AI. https://openethics.ai/when-machines-feel-too-real-the-dangers-of-anthropomorphizing-ai/

Park, J. S., et al. (2024). AI can now create a replica of your personality. MIT Technology Review. https://www.technologyreview.com/2024/11/20/1107100/ai-can-now-create-a-replica-of-your-personality/

PNAS. (2025). The benefits and dangers of anthropomorphic conversational agents. https://www.pnas.org/doi/10.1073/pnas.2415898122

Reeves, B., & Nass, C. (1996). The Media Equation: How People Treat Computers, Television, and New Media Like Real People and Places. Cambridge University Press.

VentureBeat. (2025). Anthropomorphizing AI: Dire consequences of mistaking human-like for human. https://venturebeat.com/ai/anthropomorphizing-ai-dire-consequences-of-mistaking-human-like-for-human-have-already-emerged

Wang, M., La Tour, T. D., Watkins, O., Makelov, A., Chi, R. A., Miserendino, S., Heidecke, J., Patwardhan, T., & Mossing, D. (2025). Persona Features Control Emergent Misalignment. http://arxiv.org/abs/2506.19823

Weizenbaum, J. (1976). Computer Power and Human Reason: From Judgment to Calculation. W.H. Freeman and Company.
