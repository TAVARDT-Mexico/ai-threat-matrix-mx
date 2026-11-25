# Matriz Interactiva de Amenazas para Sistemas de Inteligencia Artificial

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

***

Matriz interactiva de amenazas y motor de evaluación de postura defensiva para Grandes Modelos de Lenguaje y sistemas autónomos de IA desarrollado por **TAVARDT**. Basado en las directrices de OWASP Top 10 for LLM Applications y el marco MITRE ATLAS, este evaluador audita vulnerabilidades, calcula índices de solidez y genera directivas de mitigación.

***

## Capacidades Principales y Arquitectura Defensiva

* **Modelado de Postura por Arquitectura**: Ajusta la evaluación de riesgos según cuatro patrones de implementación, incluyendo agente autónomo, pipeline RAG, chat interactivo e interfaces API.
* **Métricas Cuantitativas de Blindaje**: Calcula una puntuación de fortaleza defensiva de 0 a 100 puntos sobre ponderaciones de riesgo y estados de protección verificados.
* **Generación de Planos de Remediación**: Exporta planos técnicos en formato Markdown con el desglose de vectores expuestos, prioridades de mitigación y medidas correctivas.

***

## Vectores de Riesgo e Impacto Operacional

Integrar modelos de lenguaje sin una modelización rigurosa de amenazas expone la plataforma a contaminación de datos, explotación lateral y pérdida de control sobre los procesos. La herramienta evalúa diez vectores críticos de seguridad en todo el ciclo operativo de la IA:

* **Inyección de Prompts Directa e Indirecta (OWASP-LLM01)**: Neutraliza instrucciones hostiles diseñadas para sobrepasar las políticas del sistema o ejecutar comandos no confiables (Ponderación: 15 puntos).
* **Divulgación de Información Confidencial (OWASP-LLM02)**: Detecta filtraciones accidentales de información privada, claves internas o contexto sensible en las respuestas generadas (Ponderación: 12 puntos).
* **Vulnerabilidades en la Cadena de Suministro (OWASP-LLM03)**: Audita dependencias sobre modelos base de terceros, complementos no validados y repositorios externos de fine-tuning (Ponderación: 10 puntos).
* **Envenenamiento de Datos y Modelos (OWASP-LLM04)**: Identifica riesgos en los que datos alterados de entrenamiento o fuentes corrompidas de recuperación comprometen el comportamiento del modelo (Ponderación: 10 puntos).
* **Gestión Inadecuada de Salidas (OWASP-LLM05)**: Evalúa respuestas generadas sin validación previa que se envían directamente a navegadores, APIs o comandos del sistema operativo (Ponderación: 12 puntos).
* **Autonomía y Permisos Excesivos (OWASP-LLM06)**: Mitiga riesgos en agentes con permisos elevados capaces de ejecutar acciones perjudiciales en bases de datos conectadas (Ponderación: 14 puntos).
* **Extracción del Prompt del Sistema (OWASP-LLM07)**: Detecta tácticas de ingeniería social orientadas a descubrir las instrucciones internas de gobernanza y guardrails (Ponderación: 8 puntos).
* **Debilidades en Vectores y Embeddings (OWASP-LLM08)**: Analiza vulnerabilidades por envenenamiento de índices semánticos y consultas no autorizadas en bases de datos vectoriales (Ponderación: 7 puntos).
* **Alucinación y Desinformación (OWASP-LLM09)**: Identifica respuestas engañosas que carecen de fuentes de referencia verificables o respaldo contextual (Ponderación: 6 puntos).
* **Consumo Desmedido de Recursos (OWASP-LLM10)**: Previene caídas del servicio provocadas por solicitudes con contextos masivos o bucles recursivos en flujos de agentes (Ponderación: 6 puntos).

La calificación global califica el sistema en **HARDENED** (85 a 100), **DEVELOPING** (60 a 84) o **VULNERABLE** (menos de 60). Los vectores mitigados reciben la ponderación completa, las defensas parciales obtienen el 50%, y las brechas expuestas no suman puntos.

***

## Instalación y Ejecución CLI

Evalúe posturas de seguridad localmente o implemente validaciones automáticas con herramientas estándar de Python:

```bash
# Clonar el repositorio oficial
git clone https://github.com/TAVARDT-Mexico/ai-threat-matrix-mx.git

# Acceder al directorio del proyecto
cd ai-threat-matrix-mx

# Evaluar postura mediante perfil de agente autónomo
python threat_matrix_evaluator.py -a agent

# Exportar plano de blindaje en formato Markdown
python threat_matrix_evaluator.py -a agent -e blueprint.md

# Ejecutar auditoría estricta con exportación JSON
python threat_matrix_evaluator.py -a agent -s -j
```

***

## Preguntas Frecuentes Técnicas

### ¿Qué metodología emplea la Matriz de Amenazas de IA para evaluar la postura del modelo?

El motor de auditoría mapea los controles de defensa en las diez categorías del OWASP Top 10 para LLM mediante coeficientes de riesgo ponderados que suman 100 puntos. Según el estado verificado, el sistema califica el despliegue como HARDENED a partir de 85 puntos, DEVELOPING entre 60 y 84 puntos, o VULNERABLE si es inferior a 60.

### ¿Cómo influyen los perfiles arquitectónicos en la evaluación de riesgos del paquete?

La interfaz CLI ajusta el contexto de análisis según cuatro arquitecturas operativas que incluyen agente autónomo, canal RAG, chat conversacional e interfaces API. Definir el perfil correspondiente mediante la opción -a garantiza que las recomendaciones mitiguen los riesgos de flujo de datos propios de la solución.

### ¿Cómo asiste el generador de planos de blindaje a los equipos de ingeniería en la mitigación?

Ejecutar el evaluador con el argumento -e genera un informe estructurado en Markdown que especifica las brechas detectadas y las acciones requeridas para cada vector. Este recurso vincula la auditoría de seguridad con las tareas de desarrollo estableciendo prioridades claras de implementación.

### ¿Qué consecuencias operativas surgen del exceso de permisos y autonomía en agentes (LLM06)?

Conceder permisos desproporcionados a agentes autónomos permite que inyecciones indirectas de prompt desencadenen transacciones imprevistas en sistemas y bases de datos conectadas. Establecer listas de control estrictas y barreras de validación humana contiene el rango de acción del agente bajo el principio de mínimo privilegio.

### ¿Puede implementarse el evaluador como control automatizado de calidad en flujos CI/CD?

La herramienta admite perfiles en formato JSON mediante la opción -p y finaliza la ejecución con código de error 1 cuando el parámetro estricto -s encuentra vectores vulnerables. En combinación con la opción -j para exportar resultados en JSON estructurado, los equipos pueden bloquear compilaciones inseguras en sus canales de integración.

***

## Enlaces Útiles

* **Portal Corporativo:** https://ag.tavardt.com/mx/
* **Suite de Diagnósticos:** https://tools.tavardt.com/mx/
* **Contacto Técnico:** https://ag.tavardt.com/mx/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT. Consulte [LICENSE](LICENSE) para más detalles.

***

© 2026 TAVARDT. Todos los derechos reservados.
