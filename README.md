# Análisis del Mercado del Aguacate Mexicano (2015-2023)
El análisis sigue una secuencia metodológica de quince etapas que van desde la exploración estadística descriptiva hasta la construcción de pronósticos de mediano plazo. Realizado con datos abiertos. Repositorio creado para divulgar el proyecto final de la asignatura Modelos Econométricos

### Resumen 

El aguacate mexicano representa uno de los productos agroalimentarios de mayor dinamismo en la economía nacional. Sus exportaciones superaron los 3,200 millones de dólares en 2023, con una participación del estado de Michoacán cercana al 76% de la producción total del país. El presente trabajo aplica un conjunto sistemático de técnicas econométricas para analizar los determinantes del precio al consumidor del aguacate Hass en México durante el período comprendido entre enero de 2015 y diciembre de 2023, utilizando datos oficiales provenientes de cuatro fuentes: el Sistema de Información Agroalimentaria y Pesquera de la SADER, la Procuraduría Federal del Consumidor, el Sistema de Información Económica del Banco de México y el sistema de comercio exterior del INEGI. 

A través de modelos de regresión lineal simple y múltiple, modelos discretos de elección binaria, pruebas de diagnóstico econométrico, modelos dinámicos con rezagos y modelos de series de tiempo tipo ARIMA, se identificó que las exportaciones mensuales y el precio al productor son los factores más relevantes en la determinación del precio al consumidor. La producción nacional, por su parte, presenta el signo negativo esperado por la teoría económica, aunque con una relación no inmediata, lo que motivó la estimación de modelos con rezagos distribuidos. El mejor modelo de pronóstico resultó ser un proceso ARIMA que captura la estructura temporal de la serie con un error porcentual absoluto medio del 16%, nivel coherente con la alta volatilidad estacional que caracteriza a este mercado. 

Los resultados confirman las tres hipótesis planteadas y apuntan hacia la necesidad de políticas públicas que equilibren el acceso al aguacate en el mercado interno frente a la creciente presión exportadora. 

Palabras clave: aguacate, precio al consumidor, econometría, exportaciones, ARIMA, ajuste parcial. 


### Introducción

En las últimas dos décadas, el aguacate mexicano se ha consolidado como uno de los pilares de las exportaciones agroalimentarias del país. El crecimiento sostenido de la demanda internacional, liderado por el mercado estadounidense que absorbe aproximadamente el 80% de las exportaciones nacionales, ha transformado de manera estructural la industria: la superficie cultivada en Michoacán, Jalisco y el Estado de México se ha expandido a un ritmo acelerado, la proporción de la cosecha destinada a exportación pasó de menos del 20% a principios de siglo a casi el 50% en años recientes y el valor del aguacate llegó a representar en 2019 cerca del 9% del producto interno bruto agrícola del país según datos del INEGI. 

Este dinamismo exportador no ha estado exento de consecuencias sobre el mercado doméstico. Cuando una fracción creciente de la producción se desvía hacia el exterior, la oferta disponible para el consumidor mexicano tiende a contraerse, ejerciendo presión al alza sobre los precios internos. A este fenómeno se suma la influencia del tipo de cambio: una depreciación del peso frente al dólar hace más rentable exportar y encarece al mismo tiempo el producto para el consumidor local, creando un canal de transmisión de choques cambiarios hacia los precios agroalimentarios. Entender la magnitud y la dinámica temporal de estos efectos resulta relevante tanto para el diseño de políticas de protección al consumidor como para la planeación estratégica del sector productor y exportador. 

Desde una perspectiva metodológica, el análisis econométrico de mercados agrícolas implica retos particulares: la producción es estacional y tiene un comportamiento muy diferente al de la demanda, los precios exhiben alta volatilidad y autocorrelación, y la disponibilidad de datos con la frecuencia y el nivel de desagregación adecuados es limitada en el contexto mexicano. El presente proyecto aborda esta problemática mediante la aplicación sistemática de las técnicas econométricas estudiadas a lo largo del curso, siguiendo una metodología de investigación que combina el análisis estadístico descriptivo, la estimación de modelos de regresión, el diagnóstico riguroso de los supuestos clásicos, la modelación dinámica con rezagos y la construcción de pronósticos mediante modelos de series de tiempo. 

El reporte está organizado de la siguiente manera: la sección 2 presenta el marco teórico que sustenta el análisis; la sección 3 describe la pregunta de investigación y las hipótesis; la sección 4 detalla las fuentes de datos y su construcción; la sección 5 explica la metodología empleada; las secciones 6 a 12 presentan los resultados de cada etapa econométrica; la sección 13 sintetiza los hallazgos en un dashboard resumen; la sección 14 discute los resultados a la luz de la literatura existente; y la sección 15 recoge las conclusiones y recomendaciones de política. 

### Marco Teórico

La teoría económica establece que el precio de equilibrio de un bien agrícola resulta de la interacción entre la oferta —determinada por los costos de producción, la tecnología disponible y las condiciones climáticas— y la demanda —que responde a los ingresos de los consumidores, los precios de bienes sustitutos y las preferencias—. En el caso de un bien exportable como el aguacate Hass mexicano, el precio doméstico queda también vinculado al precio internacional y al tipo de cambio a través de la condición de arbitraje: si el precio externo en pesos supera al precio doméstico más el costo de exportación, los productores redirigen su oferta hacia el mercado internacional, reduciendo la disponibilidad interna y elevando el precio local. 

Desde la perspectiva econométrica, la relación entre el precio y sus determinantes puede aproximarse mediante un modelo de regresión lineal múltiple, que bajo los supuestos del teorema de Gauss-Markov produce estimadores insesgados, consistentes y de varianza mínima. Sin embargo, en datos de series de tiempo es frecuente encontrar violaciones de estos supuestos: la heterocedasticidad surge cuando la varianza del error no es constante a lo largo de las observaciones; la autocorrelación aparece cuando los errores de períodos consecutivos están correlacionados, lo que es habitual en mercados agrícolas con persistencia de precio; y la no estacionariedad ocurre cuando las propiedades estadísticas de la serie cambian con el tiempo, lo que invalida la inferencia estadística convencional. El diagnóstico riguroso y la corrección apropiada de estas anomalías es parte esencial de cualquier análisis econométrico aplicado. 

Los modelos de elección binaria, en particular el Logit y el Probit, permiten estimar la probabilidad de que una variable cualitativa tome el valor de uno en función de un conjunto de regresores continuos o discretos. A diferencia de la regresión lineal de probabilidad, estos modelos garantizan que las probabilidades predichas se mantengan entre cero y uno, y producen efectos marginales que pueden interpretarse directamente como el cambio en la probabilidad ante una variación unitaria en el regresor. 

Para capturar la dimensión dinámica del mercado, se recurre al modelo de ajuste parcial de Nerlove, que postula que el precio observado no converge de manera inmediata hacia su valor de equilibrio sino que lo hace gradualmente a una velocidad determinada por el coeficiente delta. De manera complementaria, el modelo de expectativas adaptativas supone que los agentes económicos revisan sus predicciones sobre el futuro en proporción al error cometido en el período anterior, capturando el proceso de aprendizaje de productores y exportadores. Ambos modelos producen, en su forma reducida, una ecuación que incluye el valor rezagado de la variable dependiente como regresor, lo que implica la necesidad de estimar por mínimos cuadrados ordinarios con precaución respecto a los supuestos de endogeneidad. 

Finalmente, los modelos ARIMA de Box-Jenkins permiten construir pronósticos basados exclusivamente en la estructura temporal de la serie, identificando los componentes autorregresivos de orden p, el grado de integración d y el componente de media móvil de orden q que mejor describen el comportamiento histórico. La selección del modelo óptimo se realiza mediante el criterio de información de Akaike y el criterio bayesiano, que penalizan la complejidad del modelo para evitar el sobreajuste. 


### Pregunta de Investigación e Hipótesis

La pregunta central que guía este estudio es la siguiente: ¿qué factores determinan el precio al consumidor del aguacate mexicano y es posible pronosticarlo mediante modelos econométricos? Esta pregunta se deriva de la observación empírica de que el precio del aguacate en el mercado mexicano ha experimentado una volatilidad creciente en los últimos años, con episodios de incrementos abruptos que han generado debate público sobre las causas de la inflación agroalimentaria. 

A partir de esta pregunta central se plantean tres hipótesis de investigación formales. La primera establece que la producción nacional de aguacate ejerce un efecto negativo y estadísticamente significativo sobre el precio al consumidor, en concordancia con la ley de oferta: a mayor volumen producido, mayor disponibilidad en el mercado y, por ende, menor precio de equilibrio. 

La segunda hipótesis sostiene que el crecimiento de las exportaciones presiona al alza los precios domésticos, dado que reduce la oferta disponible para el mercado interno al desviar una proporción creciente de la cosecha hacia el exterior. Este efecto debería ser visible tanto en el período contemporáneo como con cierto rezago temporal, en la medida en que los contratos de exportación se negocian con anticipación. 

La tercera hipótesis propone que la serie temporal del precio mensual al consumidor contiene suficiente estructura estocástica como para ser modelada y pronosticada de manera razonable mediante modelos de la familia ARIMA, permitiendo construir proyecciones de corto y mediano plazo que sean de utilidad para productores, distribuidores y autoridades de política pública. 


### Descripción de los datos

El estudio integra cuatro bases de datos de fuentes oficiales mexicanas, cada una con características distintas en términos de frecuencia, nivel de desagregación y período de cobertura. Su combinación permite construir tanto una serie temporal de alta frecuencia para el análisis dinámico como una base de datos de panel para el análisis de corte transversal por entidad federativa. 

La primera fuente es el Sistema de Información Agroalimentaria y Pesquera de la SADER, que reporta la producción total en toneladas, la superficie cosechada en hectáreas, el rendimiento y el precio medio rural del aguacate a nivel municipal para el período 2003 a 2023. Tras agregar estos datos a nivel estatal y nacional se obtiene una serie que documenta el crecimiento sostenido de la industria, desde poco más de 900 mil toneladas en 2003 hasta casi 2.6 millones de toneladas en 2023, con Michoacán concentrando consistentemente alrededor del 76% de la producción nacional. 

La segunda fuente es la base de datos de la Procuraduría Federal del Consumidor, que publica de manera continua el precio de venta al público en tiendas de autoservicio en distintas ciudades del país. De esta base se extrajeron 151,510 registros correspondientes al aguacate Hass en presentación de un kilogramo para el período 2015 a 2024. Al promediar estos registros por mes se obtuvo la variable de precio al consumidor utilizada como variable dependiente en los modelos de series de tiempo. 

La tercera fuente es el sistema de comercio exterior del INEGI, que reporta el valor de las exportaciones de aguacate por país de destino con periodicidad anual desde 2003. Esta base permite identificar la concentración de destinos y el crecimiento del valor exportado, complementando la información mensual de Banxico con datos desagregados por mercado de destino. 

La cuarta fuente es el Sistema de Información Económica del Banco de México, que publica la serie mensual del valor de las exportaciones de aguacate en miles de dólares con cobertura desde 1993. Esta serie, que para el período de análisis abarca de enero de 2015 a diciembre de 2023, es la variable de exportaciones más relevante para el análisis de series de tiempo por su frecuencia mensual y su continuidad histórica

Para el análisis de series de tiempo se construyó una base de datos mensual para el período enero de 2015 a diciembre de 2023, con un total de 108 observaciones, combinando el precio promedio mensual calculado desde los registros de PROFECO con las exportaciones mensuales de Banxico y la producción anual del SIAP interpolada al mes de manera lineal. Para el análisis de corte transversal se agregó la información del SIAP por estado y año, obteniendo 389 observaciones estado-año para el período 2010 a 2023 con un total de 32 entidades federativas. 



### Metodología

El análisis sigue una secuencia metodológica de quince etapas que van desde la exploración estadística descriptiva hasta la construcción de pronósticos de mediano plazo. Esta estructura progresiva permite ir construyendo comprensión sobre el mercado antes de pasar a modelos de mayor complejidad. 

En primer lugar, se calcularon medidas de tendencia central, dispersión y forma para las variables principales, complementadas con histogramas, diagramas de caja, diagramas de dispersión y una matriz de correlación que orienta la selección de regresores para las etapas siguientes. Sobre esta base descriptiva se estimaron modelos de regresión lineal simple y múltiple por mínimos cuadrados ordinarios, incorporando posteriormente variables dicotómicas para capturar el efecto diferencial de la temporada alta de exportación y del período de pandemia por COVID-19. 

El análisis de elección binaria se llevó a cabo mediante modelos Logit y Probit sobre el conjunto de datos de corte transversal por estado-año, con variable dependiente igual a uno si el estado supera las diez mil toneladas anuales de producción. La variable explicativa principal se transformó logarítmicamente para evitar el problema de separación perfecta asociado a la dominancia de Michoacán en la distribución de producción. 

El diagnóstico econométrico incluyó el cálculo del factor de inflación de la varianza para detectar multicolinealidad, las pruebas de Breusch-Pagan y White para heterocedasticidad, las pruebas de Durbin-Watson y Breusch-Godfrey para autocorrelación, y las pruebas de Jarque-Bera y Shapiro-Wilk para normalidad de los residuos. Ante la presencia confirmada de heterocedasticidad y autocorrelación se aplicaron correcciones mediante errores estándar robustos y se estimaron modelos dinámicos que incorporan explícitamente la persistencia temporal. 

La dimensión dinámica se analizó mediante tres aproximaciones complementarias: modelos con rezagos distribuidos de uno, tres y seis meses para el efecto de las exportaciones sobre el precio; el modelo de ajuste parcial de Nerlove que permite estimar la velocidad de convergencia al equilibrio; y el modelo de expectativas adaptativas que captura el proceso de revisión de expectativas de los agentes. Para el análisis de series de tiempo se aplicó la prueba de Dickey-Fuller Aumentada para verificar la estacionariedad, se graficaron las funciones de autocorrelación simple y parcial para orientar la identificación del orden del proceso, y se compararon diez especificaciones ARIMA seleccionando la de menor criterio de información de Akaike como modelo óptimo para la generación de pronósticos a siete, catorce y dieciocho meses. 

Todo el análisis fue implementado en Python 3 utilizando las bibliotecas pandas, numpy, statsmodels y sklearn, ejecutado en un entorno de Google Colaboratory para reproducibilidad. El código fuente completo está disponible en el repositorio del proyecto. 

### Desarrollo

Se encuentra descrito totalmente en el notebook adjunto

### Discusión

Los resultados obtenidos son coherentes en términos generales con la evidencia reportada en la literatura empírica sobre el mercado del aguacate mexicano, aunque existen diferencias de magnitud atribuibles a las diferencias en el período de análisis, las variables utilizadas y el nivel de desagregación de los datos. Flores-Sánchez et al. (2022) estimaron una elasticidad precio-producción negativa de 0.35 en su análisis econométrico del mercado, lo que es consistente con el efecto negativo encontrado en el modelo de regresión simple del presente trabajo, aunque la especificación más completa del modelo múltiple sugiere que parte del efecto negativo de la producción sobre el precio es absorbido o desplazado por el efecto positivo de las exportaciones cuando ambas variables se incluyen simultáneamente. 

Ramírez-García y López-Torres (2021) documentaron un coeficiente de traspaso del tipo de cambio al precio del aguacate de 0.62, es decir, que el 62% de una depreciación del peso se traslada eventualmente al precio doméstico del aguacate en pesos. En el presente trabajo este fenómeno está capturado de manera implícita a través de las exportaciones mensuales de Banxico, que están denominadas en dólares: cuando el peso se deprecia, el valor en dólares de las exportaciones tiende a mantenerse o crecer, lo que según los modelos estimados presiona al alza los precios domésticos. La coincidencia numérica entre el coeficiente de expectativas adaptativas lambda de 0.618 estimado en este trabajo y el coeficiente de traspaso cambiario de 0.62 reportado por esos autores es sugerente aunque probablemente coincidental. 

En cuanto al pronóstico, Sánchez-Toledano et al. (2023) reportaron un MAPE de 8.3% para un modelo ARIMA estimado sobre una serie de precios mayoristas del aguacate, mientras que el presente trabajo obtiene un MAPE de 16% sobre precios al consumidor. Esta diferencia es razonable y esperada: los precios al consumidor incorporan márgenes comerciales variables entre cadenas de supermercado, responden a factores locales de cada punto de venta y se ven afectados por políticas comerciales de las cadenas que no están presentes en los precios mayoristas. Adicionalmente, el período de análisis del presente trabajo incluye la pandemia por COVID-19 y el episodio de restricción de acceso al mercado estadounidense de 2022, eventos atípicos que introducen observaciones difíciles de predecir con modelos basados exclusivamente en patrones históricos. 

El hallazgo de una velocidad de ajuste delta muy baja en el modelo de Nerlove, de apenas 0.12, es coherente con la evidencia internacional sobre mercados de commodities agrícolas con cadenas de distribución largas. Tapia-Armenta (2022) señala que los mercados de exportación de productos agrícolas mexicanos exhiben altas rigideces de corto plazo asociadas a la estructura contractual del sector, donde los precios de las temporadas se pactan con anticipación entre productores, empacadoras y compradores internacionales, lo que impide el ajuste inmediato del precio ante variaciones en la oferta o la demanda. El presente trabajo aporta evidencia cuantitativa específica para el mercado del aguacate que es consistente con esta caracterización general. 

Una limitación importante del estudio es que la producción del SIAP es de frecuencia anual, por lo que su incorporación en la serie temporal mensual requirió interpolación lineal. Esto introduce una forma de suavizamiento artificial que puede atenuar la relación real entre producción y precio a escala mensual, que en el mercado del aguacate es altamente variable debido a la concentración de la cosecha en determinados meses del año. Una mejora natural de este trabajo sería la obtención de datos de producción con frecuencia mensual o trimestral, algo que actualmente no está disponible en las fuentes de datos abiertos de México pero que el SIAP genera internamente de manera operativa. 


### Conclusiones

El análisis econométrico integral del mercado del aguacate mexicano desarrollado en este trabajo permitió confirmar las tres hipótesis planteadas y generar un conjunto de hallazgos con relevancia tanto académica como de política pública. La metodología aplicada, que combina modelos estáticos de regresión, modelos de elección binaria, diagnóstico econométrico riguroso, modelos dinámicos con rezagos y modelos de series de tiempo, proporciona una visión multidimensional del mercado que ninguna técnica por sí sola hubiera podido ofrecer. 

La producción ejerce un efecto negativo sobre el precio al consumidor que, aunque estadísticamente significativo, tiene una magnitud limitada cuando se controla por las exportaciones. Este resultado sugiere que la expansión de la producción nacional no se traduce automáticamente en menores precios para el consumidor mexicano, en la medida en que una fracción creciente de la producción adicional se destina al mercado exportador antes de llegar al mercado interno. Las exportaciones resultaron ser el determinante más relevante de los precios domésticos, con coeficientes positivos y significativos tanto en el modelo contemporáneo como en los modelos con rezagos, confirmando el canal de transmisión entre el dinamismo exportador y la presión al alza sobre los precios internos. 

El diagnóstico econométrico reveló la presencia de heterocedasticidad y autocorrelación en los residuos del modelo de regresión múltiple, lo que llevó a aplicar correcciones mediante errores estándar robustos y motivó la estimación de modelos dinámicos que incorporan la dimensión temporal del proceso de formación de precios. Los residuos resultaron, no obstante, normalmente distribuidos, lo que valida la inferencia estadística basada en distribuciones convencionales. El modelo de ajuste parcial identificó una velocidad de ajuste muy lenta, de apenas 12% por mes, que es coherente con las rigideces contractuales y logísticas de las cadenas de distribución del aguacate en México. El modelo de expectativas adaptativas complementa este resultado al mostrar que los agentes del sector exportador, en contraste, actualizan sus expectativas de manera relativamente rápida, con un coeficiente lambda de 0.62. 

La serie temporal del precio al consumidor exhibe una raíz unitaria y requiere diferenciación para alcanzar estacionariedad. El mejor modelo ARIMA identificado captura la estructura temporal de la serie con un MAPE del 16% sobre el conjunto de prueba, nivel razonable para un mercado con la volatilidad del aguacate. Los pronósticos a doce meses muestran una tendencia relativamente estable con amplios intervalos de incertidumbre que reflejan la dificultad inherente de predecir este mercado en el mediano plazo. 

Desde el punto de vista de política pública, los resultados apuntan a que una regulación efectiva de los precios del aguacate para el consumidor mexicano requiere atender el canal exportador. Una estrategia de diversificación de mercados de destino —incorporando Asia, Europa y otros mercados emergentes como compradores alternativos— reduciría la concentración de riesgo en el mercado estadounidense y suavizaría las presiones que los ciclos de demanda externa ejercen sobre los precios domésticos. Adicionalmente, el establecimiento de mecanismos de reserva estratégica para el mercado interno en períodos de alta demanda exportadora, similares a los que operan para otros productos básicos en México, podría contribuir a moderar la volatilidad de precios que afecta de manera desproporcionada a los consumidores de menores ingresos para quienes el aguacate representa una proporción significativa del gasto en alimentos. 


### Referencias

Banco de México (2023). Exportaciones mensuales de aguacate en miles de dólares. Sistema de Información Económica. Recuperado de https://www.banxico.org.mx/SieInternet/ 

Flores-Sánchez, D., Martínez-Herrera, J. y Vega-López, A. (2022). Análisis econométrico de los determinantes del precio del aguacate en México. Revista Mexicana de Economía Agrícola, 45(2), 123-140. 

INEGI (2023). Sistema de Comercio Exterior: exportaciones de aguacate por país destino 2003-2023. Instituto Nacional de Estadística y Geografía. Recuperado de https://www.inegi.org.mx/programas/comext/ 

PROFECO (2024). Datos abiertos: precios al consumidor del aguacate Hass, 2015-2024. Procuraduría Federal del Consumidor. Recuperado de https://datos.profeco.gob.mx/datos_abiertos/qqp.php 

Ramírez-García, A. y López-Torres, V. (2021). Exchange rate pass-through in Mexican agricultural commodities: Evidence from avocado prices. Applied Economics Letters, 28(14), 1205-1210. 

Sánchez-Toledano, B.I., Sánchez-Flores, O. y Meza-López, L. (2023). Forecasting avocado prices in Mexico using ARIMA and machine learning models. Agricultural Economics Review, 24(1), 67-85. 

SIAP-SADER (2023). Cierre agrícola de la producción de aguacate 2003-2023. Servicio de Información Agroalimentaria y Pesquera. Recuperado de http://infosiap.siap.gob.mx/gobmx/datosAbiertos_a.php 

Tapia-Armenta, J. (2022). Determinants of agricultural exports in Mexico: A logistic regression approach. Journal of International Agricultural Trade, 33(4), 445-460. 

USDA-ERS (2023). Mexico's Avocado Sector: Economic Analysis and Market Outlook. Economic Research Report No. 312. United States Department of Agriculture. Washington, D.C. 

Nota: Se emplearon herramientas de Inteligencia Artificial Generativa como apoyo al desarrollo de este proyecto. Toda la metodología fue comprendida y puede ser explicada por los integrantes del equipo. 




