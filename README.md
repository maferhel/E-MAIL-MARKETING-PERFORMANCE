<h1 align="center"> E-MAIL-MARKETING PERFORMANCE</h1>


El objetivo de este desafío fue analizar el rendimiento de la campaña de correo electrónico de una plataforma de contenido para creadores y lectores de bricolaje, con el objetivo de comprender qué tan bien sus campañas recientes han logrado atraer a la audiencia e impulsar conversiones en los últimos tres meses; plataforma que ofrece suscripciones pagas, lanza nuevas funciones de manera continua y organiza eventos en línea regulares para mantener a su comunidad activa y comprometida.

Para medir la efectividad de las campañas de correo electrónico de la plataforma evalué métricas clave como la tasa de clics, la tasa de rebote, la tasa de apertura, la tasa de cancelación de suscripción y la tasa de conversión, las que me permitieron identificar tendencias, reconocer campañas de alto rendimiento, descubrir áreas de mejora y obtener insights a nivel regional.

## 📊 Modelo de Datos.
El modelo de datos implementado es un modelo estrella que conecta las siguientes tablas:


<p align="center">
  <img src="https://github.com/maferhel/E-MAIL-MARKETING-PERFORMANCE/blob/main/IMAGENES/Captura%20de%20pantalla%202024-11-11%20143647.png" alt="Captura de pantalla 2024-11-11 143647">
</p>



## 📱 Medidas Calculadas.

El análisis se realizó con el apoyo de las siguientes medidas calculadas:

<table border="1">
    <thead>
        <tr>
            <th>Medida</th>
            <th>Descripción</th>
            <th>Código DAX</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>% Clicks sobre emails abiertos</td>
            <td>Calcula el porcentaje de clics sobre los emails que fueron abiertos.</td>
            <td><code>DIVIDE(CALCULATE(SUM(EMAIL[Hizo Clic]), EMAIL[Abierto] = 1), CALCULATE(SUM(EMAIL[Abierto])))</code></td>
        </tr>
        <tr>
            <td>Campañas Activas</td>
            <td>Cuenta el número de campañas con emails enviados.</td>
            <td><code>CALCULATE(DISTINCTCOUNT(EMAIL[Nombre Campaña]), EMAIL[Mails Enviados] > 0)</code></td>
        </tr>
        <tr>
            <td>Correos Enviados por Día</td>
            <td>Cuenta el número de correos enviados por día.</td>
            <td><code>COUNT(EMAIL[Email del Cliente])</code></td>
        </tr>
        <tr>
            <td>Jerarquía de campañas</td>
            <td>Calcula una medida compuesta basada en la tasa de clics y el volumen de correos recibidos.</td>
            <td><code>[Tasa de Clicks] * [Volumen de Mails Recibidos]</code></td>
        </tr>
        <tr>
            <td>Máxima Tasa de Cancelación por Correo</td>
            <td>Obtiene la tasa máxima de cancelación por campaña.</td>
            <td><code>MAXX(VALUES('CAMPAÑA'[Nombre Campaña]), [Tasa de Cancelacion])</code></td>
        </tr>
        <tr>
            <td>Prom. de Apertura (Cancelación, Clicks, Conversión y Rebote)</td>
            <td>Calcula el promedio de la tasa de apertura (cancelación, clicks, conversión y rebote).</td>
            <td><code>DIVIDE(SUMX(EMAIL, [Tasa de Apertura]), COUNTROWS(EMAIL))</code></td>
        </tr>
        <tr>
            <td>Tasa de Apertura (Cancelación, Clicks, Conversión y Rebote)</td>
            <td>Calcula la tasa de apertura como un porcentaje (cancelación, clicks, conversión y rebote)</td>
            <td><code>ROUND(DIVIDE(SUM(EMAIL[Abierto]), COUNT(EMAIL[Email del Cliente])) * 100, 1)</code></td>
        </tr>
         <tr>
            <td>Total Mails Enviados por Campaña</td>
            <td>Suma los emails enviados por campaña.</td>
            <td><code>CALCULATE(SUM(EMAIL[Email del Cliente]), ALLEXCEPT(EMAIL, EMAIL[Nombre Campaña]))</code></td>
        </tr>
        <tr>
            <td>Volumen de Mails Recibidos</td>
            <td>Calcula el volumen de emails recibidos restando los rebotados.</td>
            <td><code>CALCULATE(SUM(EMAIL[Mails Enviados]) - SUM(EMAIL[Rebotado]))</code></td>
        </tr>
        <tr>
            <td>Dominio con Mayor Tasa de Apertura (Cancelación, Clicks, Conversión y Rebote)</td>
            <td>Encuentra el dominio con la mayor tasa de apertura (cancelación, clicks, conversión y rebote).</td>
            <td><code>VAR Dominio = TOPN(1, ADDCOLUMNS(SUMMARIZE('CLIENTE','CLIENTE'[Email del Cliente]), "Tasa de Apertura", [Tasa de Apertura]), [Tasa de Apertura], DESC) RETURN MAXX(Dominio, 'CLIENTE'[Email del Cliente])</code></td>
        </tr>
    </tbody>
</table>

</body>
</html>


## 🔍 Estructura del dashboard.

💠 Información General: en la que se encontrará una visión global de las métricas clave relacionadas con las campañas, incluyendo tasas de apertura, clics y conversiones. Esta vista permite obtener una comprensión rápida del rendimiento general de los esfuerzos de email marketing.

💠Campañas: se enfoca en el análisis detallado de cada campaña, mostrando el rendimiento por segmento y el impacto de cada envío. Podrá evaluar indicadores como la tasa de conversión por tipo de contenido y el comportamiento de los usuarios en función de cada campaña específica.

💠Clientes: presenta un análisis centrado en los destinatarios de sus campañas, con información sobre el perfil de los clientes, segmentación y comportamiento de apertura y clics, lo que contribuye a identificar los segmentos de mayor valor y personalizar aún más sus estrategias de comunicación

## 🛠️ Herramientas y Técnicas Utilizadas.

Power BI: Para la creación de las visualizaciones y el desarrollo del modelo de datos.
Medidas DAX: Desarrollo de fórmulas DAX para crear métricas personalizadas.
Modelo Estrella: Diseño eficiente de relaciones entre las tablas para optimizar las consultas y análisis.
ZoomCharts: Visualizaciones interactivas para facilitar la exploración de datos.

## 🟰 Resultados y Conclusiones.

📈 Los miércoles son los días de mayor interacción con los correos, un dato útil para planificar envíos y mejorar el engagement.  

📈 La mayoría de las cancelaciones de suscripción ocurren en dispositivos móviles y desktops, lo que sugiere la necesidad de optimizar la experiencia en ambos.

## Navega por el dashboard aquí 👇.

[![Ver tablero interactivo](https://github.com/maferhel/E-MAIL-MARKETING-PERFORMANCE/blob/main/IMAGENES/Captura%20de%20pantalla%202024-11-06%20171639.png)](https://app.powerbi.com/view?r=eyJrIjoiNDJmYWUwOWYtZDZkNy00ZDYzLTkwMDMtNmNlYmRmYzk5ZDQ1IiwidCI6IjQ2NTRiNmYxLTBlNDctNDU3OS1hOGExLTAyZmU5ZDk0M2M3YiIsImMiOjl9)


## AUTORA.<br />
#### María Fernanda Helguero. <br />
Para cualquier duda/sugerencia/recomendación/mejora respecto al proyecto agradeceré que me la hagas saber 🙌🏼, para ello contactame por [LinkedIn](https://www.linkedin.com/in/maria-fernanda-helguero-284087181/)<br />
