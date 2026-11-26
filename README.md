<p align="center">
  <a href="https://ag.tavardt.com/es/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Inspector de Meta Tags y Open Graph

[![Inspector Meta Tags](https://img.shields.io/badge/TAVARDT-Meta%20Tags-5b3cf5.svg)](https://tools.tavardt.com/es/analizador-meta-tags-seo/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

El **TAVARDT Inspector de Meta Tags y Open Graph** proporciona validación automatizada de metadatos HTML, directivas del protocolo Open Graph, enlaces canónicos y visibilidad de snippets en España.

***

## Arquitectura de Metadatos y Matriz Diagnóstica

Los motores de búsqueda y plataformas sociales utilizan los metadatos de cabecera para indexar contenido y presentar tarjetas de previsualización. Errores u omisiones en las metaetiquetas reducen el posicionamiento orgánico y afectan el porcentaje de clics.

Esta herramienta audita rangos óptimos de longitud de títulos, meta descripciones, etiquetas Open Graph y enlaces canónicos desde una base de 100 puntos sin librerías externas.

El motor de análisis evalúa las etiquetas de cabecera frente a los límites de visualización en buscadores y redes sociales:

<table>
  <thead>
    <tr>
      <th>Etiqueta de Cabecera</th><th>Criterio de Validación</th><th>Deducción</th><th>Impacto en SEO y Redes Sociales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Elemento Title</strong></td><td>Requiere presencia de <code>&lt;title&gt;</code>. Longitud ideal: 30-60 caracteres. Penalizado si &lt;20 caracteres (-10 pts) o &gt;70 caracteres (-10 pts). Ausente: -25 pts.</td><td>Hasta -25 pts</td><td>Factor primordial de indexación orgánica y titular clicable en la SERP.</td>
    </tr>
    <tr>
      <td><strong>Meta Description</strong></td><td>Requiere <code>&lt;meta name='description'&gt;</code>. Longitud ideal: 120-160 caracteres. Penalizado si &lt;70 caracteres (-10 pts) o &gt;175 caracteres (-10 pts). Ausente: -20 pts.</td><td>Hasta -20 pts</td><td>Resumen visible para captación de clics en resultados orgánicos.</td>
    </tr>
    <tr>
      <td><strong>Protocolo Open Graph</strong></td><td>Verifica cinco etiquetas clave: <code>og:title</code>, <code>og:description</code>, <code>og:image</code>, <code>og:url</code> y <code>og:type</code>.</td><td>-5 pts por etiqueta ausente (Máx -25 pts)</td><td>Genera tarjetas enriquecidas en LinkedIn, Facebook, Slack y mensajería.</td>
    </tr>
    <tr>
      <td><strong>Directiva Canónica</strong></td><td>Requiere presencia de <code>&lt;link rel='canonical'&gt;</code> con URL de destino absoluta y unívoca.</td><td>-10 pts</td><td>Evita problemas de contenido duplicado y consolida señales de autoridad.</td>
    </tr>
    <tr>
      <td><strong>Fallo de Conexión</strong></td><td>Tiempo de espera agotado o fallo en negociación TLS/HTTP.</td><td>Puntuación reseteada a 0</td><td>Inaccesibilidad del host que impide extraer los metadatos HTML.</td>
    </tr>
  </tbody>
</table>

### Escala de Calidad y Niveles de Estado

La herramienta determina un índice consolidado de calidad clasificando el estado de la página:

* <strong>85 a 100 (OPTIMAL)</strong>: Salud de metadatos completa; título, descripción, canónico y Open Graph plenamente conformes.
* <strong>65 a 84 (ACCEPTABLE)</strong>: Configuración operativa con pequeñas desviaciones de longitud o ausencia de tags sociales secundarios.
* <strong>0 a 64 (DEFICIENT)</strong>: Ausencia severa de etiquetas primarias, comprometiendo la indexación y la difusión social.

***

## Instalación y Ejecución

Construido íntegramente con la librería estándar de Python 3.8+ sin dependencias externas.

```bash
git clone https://github.com/TAVARDT-Espana/meta-tags-inspector-es.git
cd meta-tags-inspector-es
```

### Ejecución Estándar CLI

```bash
python meta_inspector.py ejemplo.es
```

### Salida Estructurada para Pipelines en JSON

```bash
python meta_inspector.py ejemplo.es -j
```

### Configuración de Timeout Personalizado

```bash
python meta_inspector.py ejemplo.es -j -t 15
```

***

## Alineación ENS e Integridad Web en España

El control riguroso de metadatos se alinea con las recomendaciones de integridad web del **Esquema Nacional de Seguridad (ENS)** e INCIBE. Evitar cabeceras manipuladas protege la reputación institucional y la fiabilidad de los enlaces.

Se aconseja integrar la comprobación automatizada de metadatos en los despliegues continuos para asegurar la indexación uniforme de los activos web.

***

## Preguntas Frecuentes Técnicas

### ¿Cuál es la longitud ideal de caracteres para la etiqueta title?

El inspector aconseja títulos entre 30 y 60 caracteres. Títulos de menos de 20 caracteres pierden 10 puntos por debilidad semántica, mientras que títulos de más de 70 caracteres sufren deducción de 10 puntos por riesgo de truncamiento en buscadores. Su omisión total resta 25 puntos.

### ¿Cómo evalúa el inspector la meta description?

El analizador comprueba que la descripción esté entre 120 y 160 caracteres. Si tiene menos de 70 o más de 175 caracteres se restan 10 puntos. La ausencia total de la etiqueta description supone una penalización de 20 puntos.

### ¿Cuáles propiedades Open Graph son indispensables?

Se validan cinco etiquetas básicas: <code>og:title</code>, <code>og:description</code>, <code>og:image</code>, <code>og:url</code> y <code>og:type</code>. Cada propiedad ausente supone una deducción de 5 puntos, hasta un total de 25 puntos de penalización.

### ¿Por qué es crucial la etiqueta canónica en SEO técnico?

El elemento <code>&lt;link rel="canonical"&gt;</code> indica a los rastreadores cuál es la URL preferida para una página, unificando métricas de relevancia y previniendo duplicidades. Su ausencia descuenta 10 puntos.

### ¿Qué reflejan las categorías de puntuación y estado de optimización?

Una puntuación entre 85 y 100 puntos otorga el estado OPTIMAL. De 65 a 84 puntos se califica como ACCEPTABLE con margen de mejora, y por debajo de 65 puntos el estado es DEFICIENT, requiriendo acción urgente en las etiquetas clave.

***

## Soporte Técnico y Consultoría Especializada

Para auditorías avanzadas de SEO técnico, optimización de metadatos y cumplimiento de estándares web, contacte a **TAVARDT**.

***

## Enlaces Útiles

* **Portal Corporativo:** https://ag.tavardt.com/es/
* **Suite de Diagnósticos:** https://tools.tavardt.com/es/
* **Contacto Técnico:** https://ag.tavardt.com/es/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT.

***

© 2026 TAVARDT. Todos los derechos reservados.
