# Matriz Interactiva de Amenazas para Sistemas de Inteligencia Artificial

[![Live Demo](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-38bdf8?style=for-the-badge)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![Standard](https://img.shields.io/badge/Standard-OWASP%20LLM%20%26%20MITRE-3b82f6?style=for-the-badge)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Client--Side-10b981?style=for-the-badge)](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
[![License](https://img.shields.io/badge/License-MIT-slate?style=for-the-badge)](LICENSE)

Matriz interactiva de amenazas y evaluacion de riesgos para sistemas con inteligencia artificial. Basado en OWASP LLM y MITRE ATLAS.

Desarrollado para organizaciones e ingenieros en **Mexico**, este repositorio provee una suite practica para inspeccionar y blindar arquitecturas de inteligencia artificial segun estandares internacionales.

---

## Modos de Operacion

### 1. Aplicacion Web en Navegador (GitHub Pages)
Acceda a la version grafica interactiva desde cualquier navegador web:
- **Enlace Oficial**: [https://tavardt-mexico.github.io/ai-threat-matrix-mx/](https://tavardt-mexico.github.io/ai-threat-matrix-mx/)
- **Privacidad Total**: Procesamiento en el motor JavaScript local. Ningun archivo o dato se remite a servidores externos.

### 2. Herramienta de Linea de Comandos (CLI)
Para validaciones automaticas en pipelines de CI/CD o revisiones locales:

```bash
# Evaluacion de arquitectura de agente autonomo
python threat_matrix_evaluator.py --arch agent

# Exportar Blueprint de Blindaje a Markdown
python threat_matrix_evaluator.py --arch rag --export-blueprint hardening-blueprint.md

# Modo estricto para pipelines (falla con codigo 1 si hay riesgos)
python threat_matrix_evaluator.py --profile profile.json --strict

# Salida estructurada en JSON
python threat_matrix_evaluator.py --arch agent --json
```

---

## 10 Vectores de Amenaza Evaluados (OWASP Top 10 for LLMs)

1. **Inyeccion de Prompts (Directa e Indirecta)**: Manipulacion de directrices del modelo mediante entradas maliciosas o contexto externo.
2. **Divulgacion de Informacion Sensible**: Fuga involuntaria de datos confidenciales en las respuestas del sistema.
3. **Vulnerabilidades en Cadena de Suministro**: Librerias desactualizadas, complementos vulnerables o modelos sin procedencia verificada.
4. **Envenenamiento de Datos y Modelos**: Corrupcion intencionada de conjuntos de entrenamiento o bases documentales.
5. **Tratamiento Inadecuado de Salidas**: Paso de respuestas sin sanear a interpretes de codigo o motores de bases de datos.
6. **Exceso de Autonomia en Agentes**: Herramientas con permisos de ejecucion sin limites ni validacion humana.
7. **Fuga del Prompt de Sistema**: Extraccion de reglas de negocio confidenciales incluidas en el prompt base.
8. **Debilidades en Embeddings y Vectores**: Inyeccion de documentos alterados en la base vectorial para manipular la respuesta.
9. **Alucinaciones y Desinformacion Critica**: Generacion de conclusiones falsas en flujos criticos de decision operativa.
10. **Consumo Ilimitado de Recursos**: Agotamiento de capacidad computacional o sobrecostes abusivos de tokens.

---

## Integracion en GitHub Actions

```yaml
name: AI Threat Matrix Gate
on: [push, pull_request]

jobs:
  evaluate-ai-security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Instalar Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Ejecutar Evaluacion de Amenazas en IA
        run: |
          python threat_matrix_evaluator.py --arch agent --strict
```

---

## Referenciales y Conformidad

- **Jurisdiccion**: Mexico
- **Marco Tecnico**: Lineamientos Internacionales de Ciberseguridad en IA y OWASP
- **Organizacion**: [TAVARDT-Mexico](https://github.com/TAVARDT-Mexico)

## Enlaces TAVARDT

- **Portal Institucional**: [https://ag.tavardt.com/mx/](https://ag.tavardt.com/mx/)
- **Herramientas de Ciberseguridad**: [https://tools.tavardt.com/mx/](https://tools.tavardt.com/mx/)
- **Contacto Tecnico**: [https://ag.tavardt.com/mx/contacto/](https://ag.tavardt.com/mx/contacto/)

---

### Licencia
Distribuido bajo terminos de la licencia MIT. Revise el archivo [LICENSE](LICENSE) para mas informacion.
