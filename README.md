# Trabajo Final: Implementación de Pipeline CI/CD

![CI Status](https://github.com/RojasG98/Trabajo_Final_ISII_Rojas_Caballero/actions/workflows/pipeline.yml/badge.svg)

**Materia:** Ingeniería de Software II
**Universidad:** Universidad Nacional de Tucumán

## Integrantes
* Leonardo Caballero
* Gabriel Rojas

## Descripción del Proyecto
Este repositorio contiene la implementación práctica de un flujo de **Integración Continua (CI)** utilizando GitHub Actions para una aplicación Python.

El objetivo es demostrar cómo automatizar las pruebas unitarias y el análisis estático de código para asegurar la calidad del software en cada commit.

## 📄 Documentación Completa
> **[LEER INFORME TÉCNICO AQUÍ](docs/INFORME_TECNICO.md)**
>
> *Haga clic en el enlace superior para ver el desarrollo teórico, práctico, objetivos, desafíos y conclusiones del trabajo.*

## Ejecución Local (Reproducibilidad)
Para ejecutar este proyecto en su máquina local:

1. Clonar el repositorio.

2. Instalar dependencias:

   ```bash
   pip install -r requirements.txt

3. Ejecutar los tests:

    pytest

4. Ejecutar verificación de estilo:

    flake8 .