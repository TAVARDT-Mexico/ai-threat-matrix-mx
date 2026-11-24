# Matriz Interactiva de Amenazas para Sistemas de Inteligencia Artificial

[![Live Demo](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-38bdf8?style=for-the-badge)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![Standard](https://img.shields.io/badge/Standard-OWASP%20LLM%20%26%20MITRE-3b82f6?style=for-the-badge)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Client-Side-10b981?style=for-the-badge)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![License](https://img.shields.io/badge/License-MIT-slate?style=for-the-badge)](LICENSE)

Matriz interactiva de amenazas y evaluación de riesgos para sistemas con inteligencia artificial. Basado en OWASP LLM y MITRE ATLAS.

Desarrollado para organizaciones, investigadores y equipos de ingeniería en **México**, este repositorio proporciona una matriz estructurada para evaluar la postura defensiva y generar planes de mitigación técnica en sistemas basados en Modelos de Lenguaje y agentes autónomos de Inteligencia Artificial.

***

## Modos de Operación

### 1. Aplicación Web en el Navegador (GitHub Pages)
Acceda a la versión interactiva directamente en su navegador:
- **Dirección Oficial**: [https://tavardt-mexico.github.io/ai-threat-matrix-mx/](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
- **Privacidad por Diseño**: Procesamiento 100% local en el motor JavaScript de su navegador. Ningún dato arquitectónico o resultado se transmite a servidores remotos.

### 2. Utilidad de Línea de Comandos (CLI)
Para validación automatizada en flujos de integración continua (CI/CD) o auditorías locales:

```bash
# Evaluación básica con perfil de arquitectura de agente autónomo
python threat_matrix_evaluator.py -arch agent

# Exportación del Blueprint de Mitigación en Markdown
python threat_matrix_evaluator.py -arch rag -export-blueprint hardening-blueprint.md

# Validación mediante archivo de perfil de controles defensivos
python threat_matrix_evaluator.py -profile profile.json -strict

# Salida estructurada en JSON para automatizaciones
python threat_matrix_evaluator.py -arch agent -json
```

***

## 10 Vectores Críticos de Riesgo (OWASP Top 10 for LLMs)

1. **Inyección de Prompts (Directa e Indirecta)**: Manipulación de instrucciones del modelo mediante entradas manipuladas o contexto externo.
2. **Divulgación de Información Sensible**: Fuga involuntaria de datos confidenciales o secretos en las respuestas del sistema.
3. **Vulnerabilidades en Cadena de Suministro**: Librerías desactualizadas, complementos vulnerables o modelos sin procedencia verificada.
4. **Envenenamiento de Datos y Modelos**: Corrupción intencionada de conjuntos de entrenamiento o bases documentales.
5. **Tratamiento Inadecuado de Salidas**: Paso de respuestas sin sanear a intérpretes de código o motores de bases de datos.
6. **Exceso de Autonomía en Agentes**: Herramientas con permisos de ejecución sin límites ni validación humana.
7. **Fuga del Prompt de Sistema**: Extracción de reglas de negocio confidenciales incluidas en el prompt base.
8. **Debilidades en Embeddings y Vectores**: Inyección de documentos alterados en la base vectorial para manipular la respuesta.
9. **Alucinaciones y Desinformación Crítica**: Generación de conclusiones falsas en flujos críticos de decisión operativa.
10. **Consumo Ilimitado de Recursos**: Agotamiento de capacidad computacional o sobrecostes abusivos de tokens.

***

## Integración en CI/CD (GitHub Actions)

Ejemplo de pipeline para verificación continua de postura defensiva:

```yaml
name: AI Threat Matrix Gate
on: [push, pull_request]

jobs:
  evaluate-ai-security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Run AI Threat Matrix Assessment
        run: |
          python threat_matrix_evaluator.py -arch agent -strict
```

***

## Cumplimiento y Estándares Técnicos

- **Jurisdicción**: México
- **Estándar de Cumplimiento**: OWASP Top 10 para Aplicaciones LLM y MITRE ATLAS
- **Organización Mantenedora**: [TAVARDT-Mexico](https://github.com/TAVARDT-Mexico)

## Portales Oficiales

- **Portal Institucional**: [Portal Institucional](https://ag.tavardt.com/mx/)
- **Centro de Herramientas**: [Central de Ferramentas](https://tools.tavardt.com/mx/)
- **Canal de Atención y Soporte Técnico**: [https://ag.tavardt.com/mx/contacto/](https://ag.tavardt.com/mx/contacto/)

***

### Licencia
Distribuido bajo la Licencia MIT. Consulte el archivo [LICENSE](LICENSE) para más detalles.
