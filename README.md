# SalubrIA

Sistema de aprendizaje de la asignatura **2071 Salud Pública** (2.º del Grado en Terapia Ocupacional, Universidad Miguel Hernández de Elche), construido a partir de su Guía Docente 2026-2027. Es una aplicación web de un solo fichero: funciona en el navegador, sin servidor, sin clave y sin conexión. La IA es opcional.

**Usar la app:** https://fborrasumh.github.io/salubria/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24515008.svg)](https://doi.org/10.5281/zenodo.24515008)

**Idiomas:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

**Para el alumnado**
- **Diagnóstico inicial**: una pregunta por cada uno de los 12 resultados de aprendizaje evaluables en el examen. No puntúa: fija el punto de partida.
- **Sesión de hoy**: 10 actividades intercaladas (nunca dos seguidas del mismo resultado) elegidas por un modelo explicable. Cada una dice por qué toca: dominio bajo, repaso pendiente por olvido, error reciente, peso en el examen o tema aún no practicado.
- **Cinco tipos de actividad**:
  - 74 preguntas tipo test con explicación. Antes de comprobar se pide la seguridad, para trabajar la calibración y el efecto de hipercorrección.
  - 8 bancos de clasificación: niveles de prevención, capas de Dahlgren-Whitehead, diseños de estudio, medidas epidemiológicas, niveles de atención, áreas de Ottawa, cadena epidemiológica y CIF.
  - 10 generadores de problemas de epidemiología con datos distintos en cada intento: prevalencia, incidencia acumulada, tasa de incidencia, tasa ajustada, RR, diferencia de riesgos, OR, FAP, NNT y VPP. Hay retirada gradual de la ayuda (ejemplo resuelto → solo fórmula → sin ayuda).
  - 4 gráficos con pregunta calculada: pirámide e índice de dependencia, gradiente social, forest plot y tendencia.
  - 12 preguntas cortas con rúbrica y autoevaluación.
- **Laboratorios** (el estudiante predice antes de ver el resultado):
  - Cribado y valor predictivo, con 1000 personas dibujadas.
  - Confusión por edad (paradoja de Simpson).
  - Estrategia poblacional frente a alto riesgo (paradoja preventiva de Rose).
  - Tasas brutas frente a ajustadas.
- **Casos de un barrio ficticio (San Roque)**:
  - Diagnóstico comunitario y priorización con el método de Hanlon, que calcula el código.
  - Ruta de un paciente con ictus por los niveles del sistema sanitario y sociosanitario.
  - «Detective de estudios»: diseño, medida y sesgo.
- **Taller del trabajo en grupo** (la parte práctica, 25 % de la nota), en las tres fases de las prácticas de la guía:
  - Planteamiento, con 7 comprobaciones de coherencia hechas por el código.
  - Resultados: tabla 2×2 o frecuencias, con RR, OR, IC 95 %, diferencia de riesgos y gráfico. El código comprueba que cada cifra del texto de resultados sale de los datos.
  - Presentación: plan de tiempos y cronómetro.
  - Rúbrica orientativa y coevaluación entre iguales.
  - Exportación en Word y JSON.
- **Simulacro de examen** con el formato de la guía:
  - Test con penalización (1/(k−1) por defecto, configurable).
  - Problemas corregidos por el código.
  - Preguntas cortas autocorregidas con rúbrica.
  - Sin límite de tiempo.
- **Progreso**: dominio estimado por resultado de aprendizaje (baja con el tiempo sin practicar), calibración de la seguridad, próximos repasos y registro anónimo exportable.
- **Conceptos clave**: glosario de 33 términos con modo de autoevaluación.

**Para el profesorado**
- Configuración del simulacro: penalización, número de preguntas y pesos.
- Analítica de ítems a partir de los registros que el alumnado decida compartir:
  - Dificultad, discriminación punto-biserial y uso de distractores.
  - Propuestas de revisión, que decide el profesorado.
- Revisión de trabajos:
  - Comprobaciones del código.
  - Feedback de IA que recibió el grupo.
  - Valoración con la rúbrica e informe en Word.
  - Agregado de la coevaluación.
- Exportación del banco a Moodle XML (con penalización) y GIFT.

## Qué verifica el código y qué hace la IA

- **El código calcula y corrige** todos los problemas, gráficos, laboratorios, Hanlon y notas del simulacro. También reconoce errores típicos recalculando con el error: denominador equivocado, cociente invertido, odds en lugar de proporción, tasa bruta en lugar de ajustada, FAE en lugar de FAP, escala, etc. La lógica pura se prueba en Node con oráculos independientes (3000 problemas generados por prueba).
- **La IA (opcional, con la clave de cada persona: OpenAI, Gemini o Claude)**:
  - Da pistas socráticas sin recibir cuál es la opción correcta. Además, un filtro elimina frases que repitan la opción correcta o digan la letra.
  - Explica de otra forma partiendo de la explicación revisada del banco, y avisa de cifras nuevas.
  - Comenta respuestas cortas y planteamientos del trabajo. Cada frase que dice citar se comprueba en el texto del estudiante; si no aparece, se marca «sin evidencia verificada».
  - Nunca pone notas: si devuelve algo parecido a una nota, la app lo señala.

## Ciencia del aprendizaje en la que se apoya

Práctica de recuperación (Roediger y Karpicke, 2006; Adesope et al., 2017), espaciado (Cepeda et al., 2006), intercalado (Rohrer y Taylor, 2007), ejemplos resueltos con retirada gradual (Renkl et al., 2002), carga cognitiva (Sweller, 1988), feedback elaborado (Hattie y Timperley, 2007), hipercorrección (Butterfield y Metcalfe, 2001), predicción antes de ver (Richland et al., 2009), aprendizaje generativo (Fiorella y Mayer, 2016), evaluación entre iguales (Topping, 1998), aprendizaje activo (Freeman et al., 2014) y modelo tipo Elo (Pelánek, 2016). No se usan «estilos de aprendizaje» (Pashler et al., 2008). Las referencias completas, con su DOI, están en la portada de la app.

**Importante:** los efectos citados vienen de esa investigación, **no** de un estudio con SalubrIA. La app aún no se ha evaluado con estudiantes.

## Privacidad

- Respuestas, progreso, textos, trabajo y clave de IA se guardan **solo en el navegador** (IndexedDB y localStorage).
- Solo sale hacia el proveedor de IA lo que el estudiante pide que se revise. Sale con correos, teléfonos y DNI enmascarados, y antes del primer envío se muestra una muestra y se pide confirmación.
- Los nombres de los miembros del grupo se sustituyen por «[nombre]» antes de enviar el planteamiento.
- La CSP solo permite conexiones a los tres proveedores de IA.

### Registro anónimo exportable (diccionario de datos)

Lo descarga voluntariamente el estudiante (Progreso › Descargar mi registro anónimo). El formato es `salubria-registro/1`:

| Campo | Contenido |
|---|---|
| `alias` | Seudónimo aleatorio (editable) |
| `resp[].ref` | Identificador del ítem, problema, gráfico, clasificación o pregunta corta |
| `resp[].ra` | Resultado de aprendizaje (RA1-RA12) |
| `resp[].tipo` | `mcq`, `clasifica`, `problema`, `grafico`, `corta` |
| `resp[].ok` | Acierto (booleano) |
| `resp[].conf` | Seguridad declarada: 1 dudo, 2 bastante, 3 muy seguro |
| `resp[].op` | Opción elegida en el test (índice original; 0 = correcta) |
| `resp[].ayuda` | Si usó la fórmula en un problema sin ayuda |
| `resp[].diag` | Si pertenece al diagnóstico inicial |
| `resp[].dia` | Fecha (solo el día) |
| `dominio` | Habilidad estimada (logit) e intentos por RA |

El registro no contiene nombres, correos ni textos libres. **Investigar con estos datos** exige aprobación del comité de ética (OEP en la UMH), consentimiento informado y cumplimiento del RGPD; idealmente, además, un diseño preregistrado con grupo de comparación. La app produce el dato; no produce por sí sola evidencia publicable.

## Límites

- **Todo el contenido lo ha redactado la app a partir de la guía y está pendiente de revisión docente**: preguntas, explicaciones, casos, rúbricas y glosario. Los datos de los casos y gráficos son ficticios.
- Los 13 resultados de aprendizaje operativos y la rúbrica del trabajo son orientativos y están pendientes de revisión docente.
- El reparto del simulacro (test 60 %, problemas 20 %, cortas 20 %) y la fórmula de penalización son orientativos y configurables.
- El dominio estimado y la nota del simulacro son orientativos.
- La detección de conceptos en respuestas cortas usa palabras clave: es una pista y decide el estudiante.
- La coevaluación se rellena en cada dispositivo y se entrega como fichero. No hay servidor ni sincronización.
- No se ha probado con claves reales de IA, solo con IA simulada.

## Pruebas

```bash
python3 build.py && node --check all.js
node tests/test_nucleo.js src                 # lógica pura: oráculos, diagnóstico de errores, determinismo
python3 tests/smoke_test.py                   # 80 comprobaciones de punta a punta con IA simulada
AXE=…/axe-core/axe.min.js python3 tests/a11y_test.py   # WCAG 2.2 AA (axe) en 10 pantallas × 3 idiomas, teclado, sin red, CPU ×4
```

Resultados de la versión 1.0.0:
- Cero infracciones AA de axe en todas las pantallas e idiomas.
- Primera pantalla útil en 0,4 s con la CPU ralentizada ×4 en móvil.
- HTML de 0,6 MB.
- Contraste AAA (7:1) no garantizado en todos los elementos.

## Adoptarla en otra universidad

1. Cambia `src/curriculum.js` (guía, unidades, resultados de aprendizaje y pesos) y los bancos `src/banco*.js` (contenido trilingüe `[es, en, pt]`).
2. Ajusta los casos (`src/casos.js`) si quieres otro barrio o contexto.
3. `python3 build.py` y publica `index.html` en cualquier alojamiento estático.

## Autoría

| Persona | Afiliación | ORCID | Contribución (CRediT) |
|---|---|---|---|
| Fernando Borrás Rocher | Universidad Miguel Hernández de Elche | [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) | Conceptualización, software, metodología |
| Manuela García de la Hera | UMH · Dpto. de Salud Pública, Historia de la Ciencia y Ginecología | [0000-0001-5742-2704](https://orcid.org/0000-0001-5742-2704) | Recursos (asignatura y guía docente); revisión de contenidos pendiente |
| Laura Torres Collado | UMH · Dpto. de Salud Pública, Historia de la Ciencia y Ginecología | [0000-0003-2842-1344](https://orcid.org/0000-0003-2842-1344) | Recursos (asignatura y guía docente); revisión de contenidos pendiente |

Construida a partir de la Guía Docente 2026-2027 de la asignatura 2071 Salud Pública (Grado en Terapia Ocupacional, UMH).

## Cómo citar

Borrás Rocher, F., García de la Hera, M. y Torres Collado, L. (2026). *SalubrIA* (v1.0.1) [Software]. DOI: [10.5281/zenodo.24515008](https://doi.org/10.5281/zenodo.24515008)

## Licencia

MIT para el software. Véase [LICENSE](LICENSE). Para los contenidos docentes (preguntas, casos y rúbricas) se podría usar CC BY 4.0 si las autoras lo prefieren; mientras no se diga otra cosa, todo el repositorio queda bajo MIT.
