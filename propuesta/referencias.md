# Referencias — e^jω a 8 bits

*Documento de trabajo, en iteración. Última revisión: 15 de noviembre de 2026.*

**Criterio:** como evidencia solo se aceptan metaanálisis, experimentos controlados con muestras amplias, normas e instrumentos validados. Los libros de texto se usan para la teoría, y las herramientas existentes solo como trabajos relacionados.

---

## 1. Teoría de señales y comunicaciones

| Referencia | Uso en el proyecto |
|---|---|
| Lathi, B. P., y Ding, Z. (2019). *Modern digital and analog communication systems* (5.ª ed.). Oxford University Press. | Texto base del curso: Fourier (caps. 2–3), muestreo, PCM y modulación delta (cap. 5), codificación de línea (sec. 6.2), información (cap. 12). El programa lo cita como 2025, pero la página de derechos de la 5.ª edición dice © 2019. |
| Hsu, H. P. (2003). *Schaum's outline of theory and problems of analog and digital communications* (2.ª ed.). McGraw-Hill. | Ejercicios resueltos para la verificación (caps. 1, 2 y 5). La regla SQNR ≈ 6,02n + 1,76 dB es el problema 5.16 (ec. 5.48). |
| Haykin, S., y Moher, M. (2009). *Communication systems* (5.ª ed.). John Wiley & Sons. | Fourier (cap. 2), muestreo, cuantización, PCM y modulación delta (cap. 7), información (cap. 10). |
| Shannon, C. E. (1948). A mathematical theory of communication. *The Bell System Technical Journal, 27*(3), 379–423. https://doi.org/10.1002/j.1538-7305.1948.tb01338.x | Entropía y capacidad de canal (módulos extendidos). |
| Smith, J. O. (2007). *Mathematics of the discrete Fourier transform (DFT): With audio applications* (2.ª ed.). W3K Publishing. | DFT y espectrograma aplicados a audio. |
| World Wide Web Consortium. (2021). *Web Audio API* [Recomendación W3C]. https://www.w3.org/TR/webaudio/ | Especificación de la plataforma de audio. |
| Collins, K. (2008). *Game sound: An introduction to the history, theory, and practice of video game music and sound design*. MIT Press. | Contexto técnico e histórico del sonido 8-bit. |

---

## 2. Percepción auditiva

**Requisito:** la herramienta enseña oyendo. Una señal fuera del rango audible no cumple el objetivo del módulo.

**ISO 226:2023** y **Suzuki y Takeshima (2004)**
> International Organization for Standardization. (2023). *Acoustics — Normal equal-loudness-level contours* (ISO Standard No. 226:2023).
>
> Suzuki, Y., y Takeshima, H. (2004). Equal-loudness-level contours for pure tones. *The Journal of the Acoustical Society of America, 116*(2), 918–933. https://doi.org/10.1121/1.1763601

- **Respaldo:** es la norma internacional para oyentes de 18 a 25 años, la edad de los estudiantes del curso. Su base experimental integra 12 estudios de varios laboratorios.
- **Plantea:** la sensibilidad del oído depende de la frecuencia; es máxima entre ≈ 2 y 5 kHz y muy baja en los graves extremos. Los datos van de 20 Hz a 12,5 kHz.
- **Aplicación:** cuando un estudiante define una función, la aplicación la clasifica por su espectro (FFT con sobremuestreo). Si no es audible, lo **declara y explica por qué**, pero **sigue mostrando** sus gráficas y el efecto de cada operación.

| Banda | Acción |
|---|---|
| < 20 Hz | Avisa: no audible (infrasonido). |
| 20 Hz – 16 kHz | Reproduce. |
| 16 – 20 kHz | Reproduce y avisa que podría no oírse. |
| > 20 kHz | Avisa: no audible (ultrasonido). |
| > f_s/2 del dispositivo | Avisa que se oirá **plegada** (alias), no la señal original. |

- **Casos que enseñan:**
  - Una senoidal de 5 Hz no se oye, pero una cuadrada de 5 Hz sí, como clics, por sus armónicos.
  - Un filtro puede volver inaudible una señal que antes se oía; la aplicación revisa después de cada operación.
- **Limitación declarada:** la aplicación no conoce el volumen real del dispositivo, así que clasifica por frecuencia y nivel digital (dBFS), no por el umbral absoluto en dB SPL. Toda salida pasa por un limitador.
- **Límite superior:** 16 kHz es conservador; los datos normativos entre 16 y 20 kHz son escasos e inconsistentes.

---

## 3. Diseño pedagógico

**Mayer (2020)**
> Mayer, R. E. (2020). *Multimedia learning* (3.ª ed.). Cambridge University Press.

- **Respaldo y hallazgo:** 15 principios de diseño basados en más de 200 experimentos. Se aprende mejor con palabras e imágenes integradas en el espacio y en el tiempo, y sin elementos que distraigan.
- **Aplicación:** la ecuación en vivo va junto a la gráfica, y el sonido cambia en el mismo instante que la gráfica.

**Rey et al. (2019)**
> Rey, G. D., Beege, M., Nebel, S., Wirzberger, M., Schmitt, T. H., y Schneider, S. (2019). A meta-analysis of the segmenting effect. *Educational Psychology Review, 31*, 389–419. https://doi.org/10.1007/s10648-018-9456-4

- **Respaldo y hallazgo:** metaanálisis de 56 estudios. Presentar el contenido en segmentos cortos mejora la retención y la transferencia.
- **Aplicación:** el sonido desaparece apenas se oye, así que los audios son cortos, repetibles, en bucle y con comparación A/B.

**Alfieri et al. (2011)**
> Alfieri, L., Brooks, P. J., Aldrich, N. J., y Tenenbaum, H. R. (2011). Does discovery-based instruction enhance learning? *Journal of Educational Psychology, 103*(1), 1–18. https://doi.org/10.1037/a0021017

- **Respaldo y hallazgo:** metaanálisis de 164 estudios. El descubrimiento libre rinde menos que la instrucción explícita (d = −0,38); el descubrimiento guiado rinde más (d = 0,30).
- **Aplicación:** cada módulo tiene retos guiados de predecir, observar y explicar.

**D'Angelo et al. (2014)**
> D'Angelo, C., Rutstein, D., Harris, C., Bernard, R., Borokhovski, E., y Haertel, G. (2014). *Simulations for STEM learning: Systematic review and meta-analysis*. SRI International.

- **Respaldo y hallazgo:** metaanálisis de simulaciones en primaria y secundaria. Las simulaciones con andamiaje superan a las mismas simulaciones sin él (g = 0,41).
- **Aplicación:** el valor está en la guía, no en la simulación por sí sola.

**Freeman et al. (2014)**
> Freeman, S., Eddy, S. L., McDonough, M., Smith, M. K., Okoroafor, N., Jordt, H., y Wenderoth, M. P. (2014). Active learning increases student performance in science, engineering, and mathematics. *Proceedings of the National Academy of Sciences, 111*(23), 8410–8415. https://doi.org/10.1073/pnas.1319030111

- **Respaldo y hallazgo:** metaanálisis de 225 estudios universitarios de STEM. Con aprendizaje activo, las notas suben ≈ 0,47 desviaciones estándar y la reprobación baja de ≈ 34 % a ≈ 22 %.
- **Aplicación:** justifica complementar una clase muy teórica con actividades en las que el estudiante hace algo.

**Precaución.** No usar la expresión "estilos de aprendizaje": no hay evidencia que la respalde (Pashler, McDaniel, Rohrer y Bjork, 2008, *Psychological Science in the Public Interest, 9*(3), 105–119). Combinar vista y oído para todos los estudiantes es otra idea.

**Evitar concepciones erróneas.** Una analogía musical mal planteada puede enseñar algo falso. Cada módulo se revisa contra los errores conceptuales documentados en el inventario de Wage et al. (2005) (sección 5). Riesgos ya identificados:

| Analogía | Riesgo | Cómo se evita |
|---|---|---|
| "Una nota es un fasor" | Una señal real es la suma de dos fasores conjugados; si se omite, luego confunden las frecuencias negativas del espectro. | Mostrar el par e^{jωt} y e^{−jωt}, y su suma real. |
| Altura y frecuencia | Oímos la altura de forma logarítmica (octava = ×2), pero el espectro suele graficarse lineal. | Ofrecer el eje de frecuencia en escala logarítmica y marcar las notas. |
| "El timbre son los armónicos" | La envolvente (por ejemplo, el ataque del tambor) también define el timbre. | Separar explícitamente armónicos y envolvente en el módulo de series. |

### Narrativa acumulativa

Los módulos no empiezan desde cero: cada uno reutiliza las intuiciones del anterior.

**Adesope et al. (2017)**
> Adesope, O. O., Trevisan, D. A., y Sundararajan, N. (2017). Rethinking the use of tests: A meta-analysis of practice testing. *Review of Educational Research, 87*(3), 659–701. https://doi.org/10.3102/0034654316689306

- **Respaldo y hallazgo:** metaanálisis de 272 efectos con 15 472 participantes. Recuperar lo aprendido (responder sin mirar) es más eficaz que volver a estudiarlo.
- **Aplicación:** cada módulo abre con una pregunta de **recuperación** sobre una intuición anterior. Por ejemplo, en muestreo: "¿qué armónicos tenía la onda cuadrada? ¿Cuáles crees que se van a plegar?".

**Simonsmeier et al. (2022)**
> Simonsmeier, B. A., Flaig, M., Deiglmayr, A., Schalk, L., y Schneider, M. (2022). Domain-specific prior knowledge and learning: A meta-analysis. *Educational Psychologist, 57*(1), 31–54. https://doi.org/10.1080/00461520.2021.1939700

- **Respaldo y hallazgo:** metaanálisis de 8776 efectos. El conocimiento previo explica buena parte de los resultados de aprendizaje, pero en promedio **no explica la ganancia**.
- **Aplicación (inferencia nuestra):** que el módulo anterior exista no garantiza que se aproveche. La conexión entre módulos debe hacerse **explícita**.

**Hilo conductor:** una misma pieza musical (melodía chiptune más un loop de batería) recorre todos los módulos, como una cadena de comunicación. Así, cada módulo reutiliza lo anterior:

| Módulo | Intuición que hereda | Intuición que deja |
|---|---|---|
| Complejos y fasores | — | Una nota es un par de fasores que giran |
| Series de Fourier | Fasores | El timbre es una suma de fasores (armónicos) |
| Transformada y DFT | Armónicos | El espectrograma muestra esos fasores en el tiempo |
| Filtros | Espectro | Filtrar es multiplicar el espectro |
| Muestreo | Espectro y armónicos | Los armónicos por encima de f_s/2 se pliegan |
| PCM | Muestreo | Cuantizar agrega ruido visible en el espectro |
| Modulación delta | PCM | Un bit por muestra: la pendiente importa |
| Codificación de línea | Bits de PCM | Los bits también tienen espectro |

---

## 4. Diseño de interfaz y experiencia

**Brom et al. (2018)**
> Brom, C., Stárková, T., y D'Mello, S. K. (2018). How effective is emotional design? A meta-analysis on facial anthropomorphisms and pleasant colors during multimedia learning. *Educational Research Review, 25*, Artículo 100119. https://doi.org/10.1016/j.edurev.2018.09.004

- **Respaldo y hallazgo:** metaanálisis de 33 muestras (N = 2924). El diseño emocional (colores agradables, personajes con rostro) mejora la retención (d ≈ 0,39) y la comprensión (d ≈ 0,32).
- **Aplicación:** respalda la estética 8-bit, aplicada a los elementos que enseñan.

**Sundararajan y Adesope (2020)**
> Sundararajan, N., y Adesope, O. (2020). Keep it coherent: A meta-analysis of the seductive details effect. *Educational Psychology Review, 32*(3), 707–734. https://doi.org/10.1007/s10648-020-09522-4

- **Respaldo y hallazgo:** metaanálisis de 58 estudios con más de 7500 estudiantes. El contenido interesante pero irrelevante empeora el aprendizaje, sobre todo junto a diagramas.
- **Aplicación:** nada decorativo junto a la gráfica o la ecuación.

**Van der Kleij et al. (2015)**
> Van der Kleij, F. M., Feskens, R. C. W., y Eggen, T. J. H. M. (2015). Effects of feedback in a computer-based learning environment on students' learning outcomes: A meta-analysis. *Review of Educational Research, 85*(4), 475–511. https://doi.org/10.3102/0034654314564881

- **Respaldo y hallazgo:** metaanálisis de 40 estudios. La retroalimentación que explica (≈ 0,49) supera a indicar solo correcto/incorrecto (≈ 0,05).
- **Aplicación:** cada reto y cada aviso de "no audible" explica la causa.

**Deci et al. (1999)**
> Deci, E. L., Koestner, R., y Ryan, R. M. (1999). A meta-analytic review of experiments examining the effects of extrinsic rewards on intrinsic motivation. *Psychological Bulletin, 125*(6), 627–668. https://doi.org/10.1037/0033-2909.125.6.627

- **Respaldo y hallazgo:** metaanálisis de 128 estudios. Las recompensas externas esperadas reducen la motivación intrínseca: la meta pasa a ser la recompensa.
- **Aplicación:** sustenta la decisión de **no gamificar**.

### Reglas de diseño

1. La estética 8-bit se aplica a los objetos que enseñan; es un lenguaje visual y sonoro, no una mecánica de juego.
2. Junto a la gráfica y la ecuación no va nada que no aporte al concepto.
3. No hay puntos, insignias ni niveles. La única "recompensa" de un reto es oír y entender el resultado.
4. Toda respuesta del sistema explica la causa, no solo el resultado.

---

## 5. Propuesta de validación (fuera del alcance)

El curso termina antes de poder probar la herramienta con estudiantes. Se deja el protocolo como trabajo futuro:

**Deslauriers et al. (2019)**
> Deslauriers, L., McCarty, L. S., Miller, K., Callaghan, K., y Kestin, G. (2019). Measuring actual learning versus feeling of learning in response to being actively engaged in the classroom. *Proceedings of the National Academy of Sciences, 116*(39), 19251–19257. https://doi.org/10.1073/pnas.1821936116

- **Hallazgo:** en un experimento aleatorizado, quienes aprendieron más creyeron aprender menos.
- **Consecuencia para el protocolo:** medir con una prueba, no con la percepción de los estudiantes.

**Wage et al. (2005)**
> Wage, K. E., Buck, J. R., Wright, C. H. G., y Welch, T. B. (2005). The Signals and Systems Concept Inventory. *IEEE Transactions on Education, 48*(3), 448–461. https://doi.org/10.1109/TE.2005.849746

- **Respaldo:** instrumento de 25 preguntas validado con más de 900 estudiantes, con versión en español.
- **Uso en el protocolo:** prueba antes y después con ítems de Fourier, filtrado y muestreo, idealmente con un grupo de comparación.

**Vacío que la validación ayudaría a cerrar:** no hay evidencia experimental robusta de que *oír la señal* mejore el aprendizaje conceptual. La pregunta abierta es: ¿la herramienta con sonido enseña más que la misma herramienta sin sonido?

---

## 6. Trabajos relacionados (no son evidencia)

- Müller, M., McFee, B., y Kinnaird, K. M. (2021). Interactive learning of signal processing through music: Making Fourier analysis concrete for students. *IEEE Signal Processing Magazine, 38*(3), 73–84. Es el antecedente más cercano: usa la música para enseñar Fourier.
- Herramientas existentes que cubren temas aislados: los applets de Fourier de Falstad, *Fourier: Making Waves* de PhET, *Seeing circles, sines and signals* de Schaedler y el espectrograma de Chrome Music Lab.

---

## Decisiones de alcance (15 de noviembre de 2026)

- **Presentación:** la herramienta se presenta como un LMS, con los temas organizados como módulos de un curso y con una narrativa acumulativa (sección 3).
- **Arquitectura:** página estática, sin servidor. Como máximo usa `localStorage` para guardar el progreso y la señal propia del estudiante, de modo que su función lo acompañe de un módulo al siguiente.
- **Audio:** solo sonido sintetizado, las grabaciones propias de batería y canciones libres de derechos de autor.
- **Privacidad:** el micrófono se procesa localmente en el navegador; no se graba ni se envía nada.
- **Verificación:** el resultado del código se contrasta con ejemplos de resultado conocido (soluciones analíticas y ejercicios resueltos de Hsu y de Lathi y Ding).
- **Fuera del alcance:** la accesibilidad (por ejemplo, pérdida auditiva o daltonismo), porque es una herramienta de apoyo a la clase; y la validación con estudiantes (sección 5).
- **Uso de IA:** se registra en `registro-uso-ia.md`, para la declaración obligatoria del artículo final.

---

## Pendientes

- [x] Verificado contra el texto completo (PDF en `fuentes/`): autores de D'Angelo et al. (2014); efectos de Alfieri et al. (2011): d = −0,38 y d = 0,30; Deci et al. (1999): 128 estudios.
- [ ] Verificar contra el texto completo:
  - tamaños de efecto de Sundararajan y Adesope (2020);
  - volumen y páginas de Müller et al. (2021) (el PDF descargado es el preprint);
  - DOI de Suzuki y Takeshima (2004).
- [ ] Elegir un estudio normativo bien diseñado para el límite superior de audición (16 a 20 kHz).
- [ ] Fijar los umbrales numéricos de audibilidad: fracción de energía y nivel mínimo en dBFS.
- [x] Llevar al `propuesta.tex` las fuentes de las secciones 3 y 4 (hecho el 15 de noviembre; para caber en 3 páginas se quitaron de la propuesta Falstad, Schaedler y Smith).
