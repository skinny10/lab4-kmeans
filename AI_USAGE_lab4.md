AI_USAGE.md — Lab 4: Descubrimiento de temas con K-Means
Herramienta usada

Claude (Anthropic), por chat.


Cómo lo usé
No le pedí a la IA que resolviera los TODO directamente. La usé más para entender los conceptos antes de programarlos, y para organizar el notebook:

Por qué normalizar a L2 antes de K-Means: pregunté cómo se relaciona normalizar los vectores con la similitud coseno que ya habíamos usado en el Lab 2 y el Lab 3, para poder responder bien la pregunta de defensa de esa sección.
K-Means desde cero: pedí ayuda para armar el algoritmo (inicializar, asignar, actualizar, repetir hasta converger) porque no tenía a la mano mi propia implementación de la Unidad 1 al momento de hacer este lab — mis entregas anteriores de esa unidad usaron directamente scikit-learn para regresión y clasificación, no tenían K-Means hecho desde cero. Revisé que los pasos coincidieran con lo que vimos en clase.
Codo vs silueta: pregunté por qué la inercia siempre baja al aumentar k, y por qué eso no basta para elegir k por sí solo, y qué mide la silueta en cambio.
Interpretar mis resultados: después de correr el notebook con mi corpus, hablé sobre los resultados que me salieron (valores de silueta bastante bajos en todos los k, y que ni siquiera los documentos de "agua/sequía" quedaron juntos) para poder conectar eso con la limitación de TF-IDF que vimos en la Sesión 2.

Qué le di a la IA

El enunciado completo del Lab 4.
Mi corpus_procesado.json real del Lab 1 (las 14 noticias de Chiapas).
El contexto de que ya había hecho los Labs 1, 2 y 3 con ese mismo corpus.
Aviso de que no tenía mi K-Means de la Unidad 1 a la mano, así que lo construimos desde cero siguiendo el algoritmo estándar de clase.

Qué cambié o decidí yo

Las funciones tf e idf son las mismas que ya usaba en el Lab 2 y el Lab 3, no las cambié.
Verifiqué a mano que normalizar_filas() sí dejara las filas con norma 1 antes de seguir usándola.
Corrí el barrido de k=2 a k=8 con mi corpus y elegí k=4 porque fue el que dio la silueta más alta en mi corrida — no lo puse porque sí, sino porque fue mi resultado real.
Los nombres que le puse a cada grupo y el análisis del documento mal agrupado los escribí yo mismo viendo lo que realmente me salió al ejecutar, no es una respuesta genérica.
Me di cuenta de que mis valores de silueta fueron muy bajos (entre 0.003 y 0.009) y decidí mencionarlo en mi análisis en vez de ignorarlo, porque dice algo importante sobre qué tan bien separó K-Means los temas de mi corpus.

Lo que no usé

No usé scikit-learn para el K-Means ni para la inercia, solo para silhouette_score, que el enunciado permite porque es una métrica, no el algoritmo.
La elección final de k y la interpretación de cada grupo las hice yo, leyendo los términos de cada centroide y los títulos reales de mis documentos.
