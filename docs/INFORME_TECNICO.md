# Informe Técnico: Automatización de Ciclo de Vida con CI/CD

## 1. Introducción
**Contexto y Problemática**
En el desarrollo de software moderno, la integración manual de código es una fuente crítica de errores. Los equipos que dependen de validaciones manuales sufren del síndrome "funciona en mi máquina", donde el código opera correctamente en el entorno local del desarrollador pero falla en producción debido a diferencias de configuración o dependencias.

La **Integración Continua (CI)** y la **Entrega Continua (CD)** surgen como prácticas fundamentales para resolver esto, automatizando la construcción, prueba y despliegue del software.

**Principales Proponentes**
Autores como **Martin Fowler** y **Jez Humble** (autores de *Continuous Delivery*) han establecido las bases teóricas de estas prácticas, argumentando que la frecuencia de integración reduce exponencialmente la complejidad de la resolución de conflictos.

## 2. Desarrollo Práctico

### 2.1. Tecnologías Utilizadas
Para este proyecto se seleccionó un stack tecnológico basado en herramientas de código abierto y alta disponibilidad:
* **Gestión de Versiones:** Git y GitHub.
* **Lenguaje:** Python 3.12 .
* **Testing Framework:** Pytest (por su simplicidad y potencia en aserciones).
* **Análisis Estático (Linter):** Flake8 (para garantizar PEP-8).
* **Motor de CI:** GitHub Actions.

### 2.2. Implementación del Pipeline (Paso a Paso)

El núcleo del trabajo es el archivo de flujo de trabajo (`workflow`), ubicado en `.github/workflows/pipeline.yml`.

**Concepto Clave: El Pipeline Declarativo**
Se configuró un pipeline que reacciona a eventos `push`. Esto garantiza que cada línea de código subida sea verificada antes de ser aceptada.

### 2.3. Guía de Reproducción (Acción Práctica)

Para reproducir esta experiencia y verificar el funcionamiento del CI:

Clonar el repositorio: 

git clone <URL_DEL_REPO>

Crear un entorno virtual: 

python -m venv venv

Instalar dependencias: 

pip install -r requirements.txt

Generar un error intencional:

Modificar tienda.py introduciendo un error de sintaxis o lógica.

Hacer:

git push

Resultado esperado: Ir a la pestaña "Actions" en GitHub y observar cómo el pipeline falla automáticamente (Rojo ❌), impidiendo la entrega de software defectuoso.

### 2.4. Mejores Prácticas Aplicadas

Fail Fast (Fallo Rápido): El pipeline ejecuta primero el Linter (rápido) antes de los tests (lentos). Si el estilo falla, no se gastan recursos en testear.

Infraestructura como Código: Todo el proceso de build está versionado en el archivo YAML, no en configuraciones manuales del servidor.

## 3. Beneficios de implementar la metodología

En el área de Testing y QA:

Detección inmediata de regresiones: El sistema alerta minutos después de introducir un bug, reduciendo el costo de reparación (que aumenta con el tiempo).

Confianza en el Refactor: Los desarrolladores pueden mejorar el código sabiendo que el sistema les avisará si rompieron algo.

En la Ingeniería de Software General:

Documentación Viva: El archivo YAML sirve como documentación técnica de cómo se construye y prueba el proyecto.

Reducción de Deuda Técnica: Herramientas como flake8 obligan a mantener el código limpio constantemente.

## 4. Desafíos y Consideraciones

Desafío Técnico Encontrado: Durante el desarrollo, nos enfrentamos a problemas de precisión de punto flotante en los tests numéricos (el descuento del 10% daba resultados imprecisos).

Consideración Profesional: Los tests automatizados son extremadamente literales. Se requiere el uso de herramientas como pytest.approx y un manejo cuidadoso de tipos de datos decimales para evitar "falsos positivos" donde el código es correcto pero el test falla por decimales ínfimos.

Costos y Recursos: Aunque GitHub Actions ofrece una capa gratuita, en entornos empresariales con miles de tests, el tiempo de ejecución (minutos de cómputo) tiene un costo financiero que debe optimizarse.

## 5. Conclusión

La implementación de un pipeline de CI/CD transforma la cultura de desarrollo. Pasamos de un modelo reactivo (arreglar bugs cuando el usuario los reporta) a uno proactivo (el sistema bloquea los bugs). Este trabajo demostró que, con herramientas accesibles como GitHub Actions, es posible profesionalizar el ciclo de vida de software incluso en proyectos académicos o pequeños, garantizando que el código entregado sea siempre funcional y limpio.

## 6. Referencias

Fowler, M. (2006). Continuous Integration. martinfowler.com

Humble, J., & Farley, D. (2010). Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation.

Documentación Oficial de GitHub Actions.

Documentación Oficial de Pytest & Flake8.