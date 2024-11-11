# E-MAIL-MARKETING PERFORMANCE


El objetivo de este desafío fue analizar el rendimiento de la campaña de correo electrónico de una plataforma de contenido para creadores y lectores de bricolaje, con el objetivo de comprender qué tan bien sus campañas recientes han logrado atraer a la audiencia e impulsar conversiones en los últimos tres meses; plataforma que ofrece suscripciones pagas, lanza nuevas funciones de manera continua y organiza eventos en línea regulares para mantener a su comunidad activa y comprometida.

Para medir la efectividad de las campañas de correo electrónico de la plataforma evalué métricas clave como la tasa de clics, la tasa de rebote, la tasa de apertura, la tasa de cancelación de suscripción y la tasa de conversión, las que me permitieron identificar tendencias, reconocer campañas de alto rendimiento, descubrir áreas de mejora y obtener insights a nivel regional.

## 📊 Modelo de Datos.





## 📱 Medidas Calculadas.

<p>Este archivo contiene un resumen de las medidas calculadas en el modelo de datos de análisis de campañas de email marketing.</p>

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
        <!-- Agrega los demás campos de manera similar -->
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
