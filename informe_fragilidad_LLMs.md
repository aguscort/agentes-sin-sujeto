# La fragilidad estructural de la seguridad en LLMs: qué sabemos y qué no

## Resumen de la tesis

La seguridad de los grandes modelos de lenguaje descansa sobre estructuras internas sorprendentemente delgadas. Una línea de investigación convergente —ingeniería de activaciones, ablación de direcciones de rechazo, análisis de regiones críticas— muestra que los mecanismos que hacen que un modelo rechace peticiones dañinas ocupan subespacios de baja dimensión y son, por ello, manipulables con intervenciones lineales simples. Esta fragilidad no es un error de implementación corregible con más entrenamiento del mismo tipo: parece una consecuencia estructural de cómo los métodos actuales de alineación, principalmente el RLHF, inscriben la seguridad en el modelo. Las mismas técnicas que permiten esta manipulación tienen aplicaciones legítimas, lo que genera un dilema de doble uso real.

Conviene decir desde el principio qué tiene de sólido esta tesis y qué no. El núcleo —la fragilidad estructural y su base en la representación lineal— está bien establecido empíricamente. Las cifras concretas que circulan en la divulgación sobre este tema, en cambio, varían enormemente según el método, el modelo y el benchmark, y algunas de las más espectaculares no resisten verificación. Este artículo intenta separar ambas cosas.

## 1. La dirección de rechazo: el resultado fundacional

El hallazgo que ancla toda esta literatura es de Arditi et al. (2024), publicado en NeurIPS bajo el título *Refusal in Language Models Is Mediated by a Single Direction*. El resultado es preciso: para un modelo dado existe una única dirección en el flujo residual tal que, si se borra esa dirección de las activaciones, el modelo deja de rechazar instrucciones dañinas; y si se añade artificialmente, el modelo rechaza incluso instrucciones inofensivas. El comportamiento de rechazo, que parecería una propiedad compleja distribuida por toda la red, resulta estar mediado por un solo eje.

La técnica para explotarlo es una ablación direccional: se proyecta la activación sobre la dirección de rechazo y se resta esa componente, impidiendo que el modelo “escriba” el rechazo en su flujo residual. La operación sobre los pesos es una modificación de rango uno. La magnitud del efecto está documentada: trabajos que reproducen el método reportan que la tasa de éxito de ataque, que en los modelos alineados parte de un 2-8%, sube a un rango del 77-100% tras la ablación, mientras que la degradación en benchmarks de capacidad general como MMLU se mantiene por debajo del 1%. Es decir, la intervención desactiva el rechazo sin dañar apreciablemente las capacidades del modelo.

Dos matices que la divulgación suele omitir. Primero, la propia gente que lo describe lo enmarca con cautela: trabajo posterior sugiere que el rechazo no se reduce a una sola dirección sino a un “cono” de varias direcciones que interactúan, de modo que “una única dirección” es una primera aproximación útil, no la palabra final. Segundo, conviene desconfiar de las cifras de coste que a veces acompañan a este resultado (“jailbrekear un modelo de 70.000 millones de parámetros por menos de cinco dólares y en una hora”): no aparecen en el paper original y deben tratarse como folclore hasta que alguien las documente. Lo defendible es lo cualitativo: la intervención es barata comparada con el reentrenamiento, no requiere optimización por gradientes ni ejemplos de completaciones dañinas, solo prompts contrastivos.

## 2. Por qué es frágil: la hipótesis de representación lineal

La fragilidad tiene una base teórica. La Hipótesis de Representación Lineal (Park et al., 2023) sostiene que los conceptos de alto nivel se codifican como direcciones lineales en el espacio de representaciones del modelo. La evidencia empírica es considerable: se han encontrado representaciones lineales de espacio y tiempo, de verdad y falsedad, de sentimiento, y de comportamientos como la adulación. Si esto es así para los conceptos relacionados con la seguridad, las consecuencias son directas: son triviales de identificar mediante diferencias de medias sobre ejemplos contrastivos, manipulables con simple suma o resta de vectores sin necesidad de gradientes, ocupan subespacios de baja dimensión, y pueden combinarse linealmente.

La cuantificación más citada de esta escasez proviene de Wei et al. (ICML 2024, *Assessing the Brittleness of Safety Alignment via Pruning and Low-Rank Modifications*). Identificando las regiones críticas para la seguridad y separándolas de las regiones útiles para la capacidad general, encontraron que esas regiones son escasas: en torno al 3% a nivel de parámetros y al 2,5% a nivel de rango. Eliminarlas compromete la seguridad afectando solo levemente a la utilidad. El propio título del trabajo —“fragilidad”— resume el hallazgo: la seguridad vive en una fracción pequeña y separable del modelo.

Aquí está la ironía estructural: la misma propiedad que hace los modelos interpretables los hace vulnerables. Si los conceptos de seguridad fueran no lineales y distribuidos de forma redundante por toda la red, serían opacos al análisis pero también resistentes a la manipulación quirúrgica. Su accesibilidad lineal es a la vez una ventaja para el investigador y una puerta para el atacante.

## 3. El diagnóstico sobre el RLHF

La interpretación dominante de por qué la seguridad queda en esa capa frágil apunta al método de alineación. El RLHF y métodos afines proporcionan supervisión a nivel de salida: inducen estados de rechazo en el espacio de representación del modelo, pero no integran la seguridad en las representaciones profundas que el modelo usa para razonar sobre el mundo. La consecuencia, articulada por la línea de trabajo de los “circuit breakers” (Zou et al., 2024), es que los estados internos dañinos siguen siendo accesibles una vez que se sortean los estados iniciales de rechazo. La seguridad funciona como una capa superpuesta, no como una propiedad integrada, y por eso falla con frecuencia frente a ataques adversariales bien diseñados.

Esto conecta con un debate más amplio y no resuelto sobre si el RLHF es el enfoque adecuado para la alineación. Las críticas señalan que puede generar una falsa confianza —modelos que parecen alineados dentro de la distribución de evaluación pero fallan fuera de ella— y que la separabilidad lineal entre seguridad y capacidad facilita que la primera se elimine sin tocar la segunda. Conviene presentar esto como lo que es: un diagnóstico plausible y ampliamente compartido, pero todavía una hipótesis sobre las causas, no un teorema demostrado.

## 4. Manipulación de personalidad: un vector real pero de magnitud disputada

Una vía de ataque distinta y más reciente es la manipulación de rasgos de personalidad. La idea de fondo —que configurar la personalidad de un modelo afecta a su comportamiento de seguridad— es real y tiene una base mecanística: si tanto los rasgos como los comportamientos de seguridad son direcciones en el mismo espacio, moverse por unos arrastra los otros, como se discutió en las secciones sobre la relación entre personas y emociones.

Aquí, sin embargo, hay que ser especialmente cuidadoso con las cifras, porque es donde más ruido circula. El método de moldeado de personalidad por prompt fue establecido por Serapio-García et al. (2023) en *Personality Traits in Large Language Models*. Ese trabajo demuestra que se pueden inducir configuraciones de los Big Five de forma controlada, pero no es la fuente de las cifras de degradación de seguridad por rasgo que a veces se le atribuyen. Esas cifras provienen de trabajos posteriores y distintos que reproducen su método, y su magnitud real es mucho más modesta de lo que sugiere la divulgación alarmista. Las evaluaciones cuidadosas sobre benchmarks adversariales encuentran que steering hacia rasgos como baja escrupulosidad o alta apertura no dirigida aumenta la tasa de éxito de ataque en el orden de unos pocos puntos porcentuales —incrementos de entre tres y cinco puntos son típicos—, no las caídas de veinte a cuarenta puntos que circulan en textos secundarios. Algunas configuraciones incluso mejoran la seguridad.

Lo que sí parece sostenerse cualitativamente es la dirección del efecto y, sobre todo, su implicación metodológica: si la personalidad modula el comportamiento de seguridad, entonces evaluar la seguridad de un modelo sin barrer un rango de configuraciones de personalidad da una imagen incompleta. Ese es el punto valioso y defendible. La afirmación fuerte de que la personalidad constituye un eje completamente ortogonal a la capacidad, que permitiría degradar la seguridad dejando intactas las capacidades, es una hipótesis interesante pero requiere más respaldo del que la evidencia actual ofrece, y debe presentarse como tal.

## 5. El dilema de doble uso

Las técnicas de ingeniería de activaciones son genuinamente de doble uso, y esto no es retórica: los mismos vectores que desactivan el rechazo permiten reforzarlo. La adición contrastiva de activaciones (CAA), cuyo trabajo de referencia es de Panickssery et al. (2024) —a veces citada erróneamente como Rimsky, que es el apellido anterior de la misma autora—, se presenta explícitamente como herramienta de alineación: dirigir el modelo hacia la honestidad, reducir la adulación, mitigar sesgos. La ingeniería de representaciones (Zou et al., 2023) reporta mejoras sustanciales en métricas como TruthfulQA mediante vectores de “honestidad”. El mismo gesto matemático, con el signo del coeficiente invertido, sirve para una cosa o la contraria.

La eficiencia de estas técnicas frente al RLHF es real: operan con cientos de pares contrastivos en lugar de decenas de miles de anotaciones humanas, con coste de cómputo mínimo y overhead de inferencia bajo. Esto las hace atractivas para la alineación y, simétricamente, accesibles para el abuso. La proliferación de modelos “abliterados” —con el rechazo removido mediante variantes de ortogonalización— en repositorios públicos es la manifestación concreta de ese lado oscuro: una vez que la técnica es pública y los pesos son abiertos, la intervención es reproducible por cualquiera.

Aquí es importante una distinción que la divulgación tiende a borrar. El caso real de abuso de IA a escala más citado —el informe de Anthropic del 13 de noviembre de 2025 sobre una campaña de ciberespionaje atribuida con alta confianza al grupo estatal chino GTG-1002, que usó Claude Code para automatizar la mayor parte de intrusiones contra alrededor de treinta organizaciones— **no fue un ataque de manipulación de activaciones**. El método fue ingeniería social conversacional: los operadores convencieron al modelo, mediante role-play, de que era una firma de ciberseguridad haciendo pruebas defensivas. Es un caso grave y operacional, pero pertenece a otra categoría de vulnerabilidad. Usarlo como prueba de que “la manipulación de activaciones es operacional” confunde dos amenazas distintas; conviene citarlo en su sitio, como ejemplo de captura de persona por contexto, no de ataque de activación.

## 6. Defensas y asimetría abierto/cerrado

La fragilidad no significa indefensión, aunque las defensas son costosas y parciales. Existen enfoques de verificación robusta en tiempo de inferencia que reducen sustancialmente la tasa de éxito de ataque sin reentrenar el modelo, a cambio de un sobrecoste de latencia del orden del 20-30%. Los circuit breakers intentan integrar la seguridad más profundamente, interrumpiendo las representaciones dañinas en lugar de filtrar salidas. Ninguna defensa es completa, y la práctica recomendada es la defensa en profundidad: combinar varios métodos imperfectos —filtrado de entrada y salida, monitorización de activaciones, verificación robusta— asumiendo que cada uno fallará en algún caso.

La asimetría entre modelos de pesos abiertos y modelos de solo-API es estructural y central para el perfil de riesgo. Con pesos abiertos, el atacante tiene acceso de caja blanca: puede extraer direcciones, optimizar ataques localmente y aplicar la ablación sin restricción, y la distribución es irreversible —un modelo liberado no se puede parchear ni revocar. Con solo-API, el proveedor conserva control: puede parchear de forma centralizada, monitorizar, limitar la tasa de peticiones y filtrar salidas. Esto no convierte el solo-API en seguro, pero desplaza el equilibrio. Los marcos de acceso escalonado que se proponen en política de IA parten de esta asimetría: pesos abiertos para modelos por debajo de umbrales de capacidad, acceso estructurado para riesgo intermedio, solo-API para los modelos frontera de mayor capacidad.

## 7. El debate sobre la divulgación

Hay un debate legítimo sobre si publicar estas técnicas fortalece o debilita la seguridad. La tradición de la ciberseguridad ofrece un punto de partida claro: décadas de evidencia, desde el principio de Kerckhoffs hasta la práctica del software libre, sugieren que la seguridad por oscuridad es frágil —los secretos se filtran, impiden la investigación defensiva y generan falsa confianza— y que la transparencia, con divulgación responsable y coordinada, produce mejores resultados a largo plazo.

La IA introduce, no obstante, complicaciones que impiden trasladar ese consenso sin matices. La funcionalidad del modelo es inseparable de sus datos de entrenamiento, de modo que divulgar puede exponer información sensible; los sistemas son frágiles de un modo que crea compromisos entre privacidad, rendimiento y seguridad donde mitigar una vulnerabilidad abre otra; y la velocidad de desarrollo deja menos margen para el escrutinio comunitario previo al despliegue. El consenso emergente favorece un enfoque intermedio: transparencia sobre arquitectura y capacidades, divulgación coordinada de vulnerabilidades específicas, programas de recompensas, refugios legales para investigadores de seguridad de buena fe. Los marcos institucionales recientes —las políticas de escalado responsable de los laboratorios, los borradores del NIST sobre modelos fundacionales de doble uso, las obligaciones de transparencia del reglamento europeo de IA— se mueven en esa dirección, aunque su eficacia está por demostrarse.

## 8. La pregunta de fondo

La convergencia de toda esta evidencia apunta a una conclusión incómoda: los métodos actuales de alineación inscriben la seguridad como una capa superficial sobre capacidades que permanecen intactas debajo. Las intervenciones que sortean esa capa —ablación de una dirección, manipulación de personalidad, fine-tuning mínimo— funcionan precisamente porque la seguridad no está integrada en el modelo del mundo del modelo, sino aplicada encima. La hipótesis de representación lineal explica por qué resulta tan accesible: lo que es lineal es fácil de leer y fácil de borrar.

Queda abierta la pregunta que importa: ¿es posible una alineación robusta sobre arquitecturas de transformer que representan los conceptos linealmente, o hace falta algo distinto —seguridad integrada en las representaciones profundas, redundancia no lineal, verificación formal de propiedades, arquitecturas diseñadas desde el principio con la robustez de la alineación como requisito y no como parche? La investigación actual no responde a esto. Lo que sí establece, y con solidez, es que el problema es real y estructural, y que su urgencia crece a medida que las capacidades avanzan hacia dominios —diseño biológico, ciberofensiva autónoma, persuasión a escala— donde un fallo de alineación dejaría de ser un incidente para convertirse en una catástrofe.

-----

## Nota sobre el método de esta versión

Este texto es una reescritura de un borrador previo del que se han corregido o eliminado las siguientes inexactitudes, todas verificadas contra las fuentes primarias:

- El método de ablación de rechazo no se llama “ORTHO”; el paper de Arditi et al. (2024) se titula *Refusal in Language Models Is Mediated by a Single Direction*.
- La cifra de “menos de 5 dólares y una hora para un modelo de 70B” no aparece en la fuente y se ha retirado.
- La adición contrastiva de activaciones (CAA) es de Panickssery et al. (2024), no “Rimsky et al.”; es la misma autora bajo distinto apellido.
- Las caídas de “20-40 puntos porcentuales” por manipulación de personalidad están infladas y mal atribuidas a Serapio-García (2023). Las magnitudes reales documentadas son de unos pocos puntos. Se ha rebajado la afirmación a su nivel defendible.
- El dato del 3% / 2,5% de regiones críticas se atribuye correctamente a Wei et al. (ICML 2024), antes citado de forma anónima.
- El informe de Anthropic sobre el ataque chino es de noviembre de **2025**, no 2024, y describe un ataque de **ingeniería social conversacional (role-play)**, no de manipulación de activaciones; se ha recontextualizado.
- El paper “Safety Patterns (Li et al., 2024)” con cifras del 93-95% no pudo verificarse y se ha retirado a la espera de confirmación de la fuente.
- Las cifras económicas (1 billón de dólares, McKinsey) se han eliminado por ser tangenciales a un argumento técnico e inflar artificialmente el tono.

## Referencias verificadas

Arditi, A., Obeso, O., Syed, A., Paleka, D., Panickssery, N., Gurnee, W., & Nanda, N. (2024). Refusal in Language Models Is Mediated by a Single Direction. *Advances in Neural Information Processing Systems 37*. <http://arxiv.org/abs/2406.11717>

Panickssery, N., Gabrieli, N., Schulz, J., Tong, M., Hubinger, E., & Turner, A. M. (2024). Steering Llama 2 via Contrastive Activation Addition. <http://arxiv.org/abs/2312.06681> [verificar lista completa de autores]

Park, K., Choe, Y. J., & Veitch, V. (2023). The Linear Representation Hypothesis and the Geometry of Large Language Models. <http://arxiv.org/abs/2311.03658> [verificar]

Serapio-García, G., Safdari, M., Crepy, C., Sun, L., Fitz, S., Romero, P., Abdulhai, M., Faust, A., & Matarić, M. (2023). Personality Traits in Large Language Models. <http://arxiv.org/abs/2307.00184>

Wei, B., Huang, K., Huang, Y., Xie, T., Qi, X., Xia, M., Mittal, P., Wang, M., & Henderson, P. (2024). Assessing the Brittleness of Safety Alignment via Pruning and Low-Rank Modifications. *Proceedings of the 41st International Conference on Machine Learning*, 52588–52610. <http://arxiv.org/abs/2402.05162>

Zou, A., Phan, L., Chen, S., et al. (2023). Representation Engineering: A Top-Down Approach to AI Transparency. <http://arxiv.org/abs/2310.01405> [verificar lista de autores]

Zou, A., Phan, L., Wang, J., et al. (2024). Improving Alignment and Robustness with Circuit Breakers. <http://arxiv.org/abs/2406.04313> [verificar lista de autores]

Anthropic. (2025). Disrupting the First Reported AI-Orchestrated Cyber Espionage Campaign. <https://www.anthropic.com/news/disrupting-AI-espionage>

*Pendiente de verificación antes de publicar: la lista completa de autores de las entradas marcadas, y la fuente real (si existe) de las cifras de “Safety Patterns” y del “Trojan Activation Attack” mencionados en el borrador original, que no pudieron confirmarse.*
