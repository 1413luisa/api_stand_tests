🛒 Urban Grocers API – Proyecto de Automatización de Pruebas (Pytest + Requests)

Este proyecto contiene una suite de pruebas automatizadas desarrolladas con Python, utilizando Pytest y Requests para validar la creación de un nuevo kit mediante una API REST.
El enfoque principal es asegurar que el campo name cumpla con las reglas del negocio y responda con los códigos HTTP esperados.

----
La creación de un “kit” es un proceso crítico dentro de la API de Urban Grocers. Este proyecto responde a la necesidad de:

✔️ Validar la integridad de datos

Evita que se registren kits con nombres inválidos, vacíos, demasiado largos o con formatos incorrectos.

✔️ Prevenir errores en producción

Un mal control del campo name puede generar fallas en bases de datos, errores en catálogos o comportamientos inesperados en la UI.

✔️ Alinear la API con las buenas prácticas de REST

Cada solicitud debe responder con códigos HTTP consistentes (201, 400).

✔️ Automatizar pruebas repetitivas

Permite validaciones rápidas y continuas sin depender del testing manual.

✔️ Proteger el endpoint principal

Garantiza que las reglas del negocio se cumplan incluso después de cambios, deploys o refactorizaciones.

En resumen, este proyecto cubre la necesidad empresarial de asegurar la calidad del endpoint de creación de kits, uno de los recursos más usados dentro de la plataforma.
----

ESTRUCTURA DEL PROYECTO

├── configuration.py            # Configuración global: URL base y endpoints
├── data.py                     # Headers y body base de creación
├── sender_stand_request.py     # Función que envía solicitudes POST
├── test_kits.py                # Suite de pruebas para el campo "name"
├── README.md                   # Documentación del proyecto

REQUISITOS TECNICOS 
Python 3.8+
pip
Librerías necesarias:
   requests
    pytest

    ---

    Instalacion 

    pip install pytest requests
----

Cómo ejecutar los test
    
python -m pytest test_kits.py -q

PRUEBAS IMPLEMENTADAS 

| Nombre del test                       | Descripción                 | Resultado esperado |
| ------------------------------------- | --------------------------- | ------------------ |
| `test_name_kit_min_1`                 | Nombre con 1 carácter       | ✅ 201 Created      |
| `test_name_kit_max_511`               | Nombre con 511 caracteres   | ✅ 201 Created      |
| `test_name_kit_0`                     | Nombre vacío                | ❌ 400 Bad Request  |
| `test_name_kit_max_512`               | Nombre con 512 caracteres   | ❌ 400 Bad Request  |
| `test_name_kit_caracteres_especiales` | Caracteres especiales (№%@) | ✅ 201 Created      |
| `test_name_kit_space`                 | Nombre con espacios         | ✅ 201 Created      |
| `test_name_kit_numbers`               | Nombre solo números         | ✅ 201 Created      |
| `test_name_kit_sin_parametro`         | Body sin campo `name`       | ❌ 400 Bad Request  |

Realizado por Luisa Ordoñez

