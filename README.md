# e^iω a 8 bits

Herramienta web interactiva para aprender **teoría de la información y sistemas de comunicación** a través del sonido. Cada módulo conecta una fórmula del curso con un experimento sonoro que se puede manipular, con estética chiptune de 8 bits: ves la señal, su espectro y la ecuación, y oyes en el mismo instante lo que cada operación le hace a la música.

Proyecto final de *Teoría de la Información y Sistemas de Comunicación*, Ingeniería de Sistemas y Computación, Universidad Nacional de Colombia, 2026-II.

## Equipo

| Integrante | Rol |
|---|---|
| Daniel Alonso Gracia Pinto | Concepción e implementación |
| Juan Camilo Vergara Tao | Marco teórico y artículo |
| Andrew Nicolay Prieto Mendoza | Verificación de calidad, protocolo de validación y grabación de batería |

## Módulos

Los módulos siguen una **narrativa acumulativa**: cada uno reutiliza las intuiciones del anterior, y una misma pieza musical los recorre todos como si fuera una cadena de comunicación.

| Módulo | Experimento sonoro |
|---|---|
| Complejos y fasores | Un fasor giratorio cuya frecuencia es una nota; sumar fasores forma acordes |
| Series de Fourier | Construir timbres armónico por armónico |
| **Transformada y DFT** (módulo central) | Espectrograma en vivo de melodías, batería y micrófono |
| Sistemas LTI y filtros | Ecualizador y pasa bajas ideal y práctico |
| Muestreo y aliasing | Bajar f_s y oír las notas "dobladas" |
| PCM y cuantización | Bajar de 16 a 4 bits y oír el ruido de cuantización |
| Modulación delta | Sobrecarga de pendiente en el ataque de un tambor |
| Codificación de línea | Patrones rítmicos como trenes de pulsos NRZ, RZ y Manchester |

Extensiones, si el tiempo alcanza: entropía y Huffman, capacidad de Shannon y códigos correctores.

## Principios de diseño

- **Rango audible:** si una función propuesta por el estudiante no se puede oír (infrasonido, ultrasonido, nivel insuficiente o componentes por encima de Nyquist), la aplicación lo declara y explica por qué, pero sigue mostrando sus gráficas.
- **Retos guiados:** cada módulo plantea preguntas de predecir, observar y explicar, y la retroalimentación explica la causa.
- **Sin gamificación:** no hay puntos, insignias ni niveles. Lo que motiva es el contenido.
- **Estética al servicio del contenido:** el estilo 8-bit se aplica a los elementos que enseñan, nunca como decoración junto a gráficas o ecuaciones.

La justificación de cada principio, con sus fuentes, está en [`propuesta/referencias.md`](propuesta/referencias.md).

## Tecnología

- Sitio **estático, sin servidor**. El progreso y la señal propia del estudiante se guardan en `localStorage`.
- **TypeScript** y **Web Audio API**: AudioWorklets para las operaciones propias (submuestreo, cuantización, modulación delta) y Canvas para las gráficas.
- El micrófono se procesa solo en el navegador: no se graba ni se envía nada.
- Audio: sonido sintetizado, grabaciones propias de batería y canciones libres de derechos de autor.

## Estructura del repositorio

```
propuesta/
  propuesta.tex       Propuesta (plantilla IEEE, referencias APA)
  propuesta.pdf       Versión compilada
  referencias.md      Referencias comentadas y decisiones de diseño
registro-uso-ia.md    Registro de uso de IA para la declaración del artículo
```

Fuera del repositorio (ver `.gitignore`):
- **`fuentes/`:** PDFs de los artículos citados.
- **Documentos guía del curso:** programa y proyectos sugeridos.

Son material con derechos de terceros.

## Compilar la propuesta

```bash
cd propuesta
latexmk -pdf propuesta.tex
```

También compila en Overleaf subiendo solo `propuesta.tex`. No hay archivo `.bib` aparte.

## Uso de IA

Se permite usar herramientas de IA en el curso, siempre que se declare. Cada uso se registra en [`registro-uso-ia.md`](registro-uso-ia.md) con qué se hizo y cómo se verificó.

## Estado

- [ ] Propuesta: borrador listo, falta la revisión del equipo (entrega: 18 de noviembre de 2026)
- [ ] Prototipo técnico y estructura común de módulos
- [ ] Módulos de complejos a codificación de línea
- [ ] Verificación contra ejemplos conocidos
- [ ] Artículo final y sustentación
