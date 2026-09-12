# NutriAI

Asistente de registro nutricional que permite ingresar comidas en lenguaje natural desde Telegram, revisar la interpretación y confirmar los datos antes de guardarlos.

**Autor: Alexis Varela**

El sistema integra **n8n, DeepSeek, Airtable, USDA FoodData Central, Telegram y Slack**.

## Arquitectura

- **W1 — Flujo principal:** gestiona el registro de usuarios, el perfil nutricional, las consultas y la validación humana de las comidas.
- **W2 — Procesamiento de comida:** consulta alimentos en Airtable o USDA, calcula los aportes nutricionales y devuelve el resultado al usuario.
- **W3 — Dashboard Control:** consolida los indicadores operativos y actualiza el panel de control.

## Documentación

- [Informe final del proyecto](Documentacion%20entrega%20Final%20NutriAI%20-%20Varela%20Alexis.pdf): arquitectura, modelo de datos, contratos JSON, matriz de costos, seguridad, resiliencia y evidencias de pruebas.

## Enlaces de lectura

- [Base de datos de NutriAI](https://airtable.com/appCTXJqifgrH2TyQ/shr384ega8avGE5Rz)
- [Dashboard Control público](https://airtable.com/appCTXJqifgrH2TyQ/shrV1aDmggjxVHfML)

## Workflows

- [W1 — Flujo principal](W1_publicable.json)
- [W2 — Procesamiento de comida](W2_publicable.json)
- [W3 — Dashboard Control](W3_publicable.json)

Para importar los workflows, configurar las credenciales propias, la clave de USDA y la referencia de W1 al subworkflow W2.

## Validación humana y manejo de errores

Antes de crear una comida, NutriAI muestra los alimentos y sus cantidades para que el usuario confirme o corrija la interpretación.

Los datos incompletos generan una solicitud de corrección. Los fallos técnicos cuentan con rutas de error, registro en Airtable y mensajes controlados al usuario. Los errores de IA generan además una alerta interna en Slack.

## Pruebas realizadas

- Registro y configuración de un usuario.
- Registro y procesamiento de una comida.
- Aprobación y rechazo mediante validación humana.
- Corrección de datos incompletos.
- Fallo controlado de IA con registro y alerta.
- Actualización del Dashboard Control.

## Alcance

NutriAI es un MVP educativo. Los resultados nutricionales son estimaciones y presentan las limitaciones descritas en el informe; no sustituyen una evaluación profesional.
