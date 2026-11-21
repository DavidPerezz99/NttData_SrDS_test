# Recomendacion de retencion para Conecta+

## Decision recomendada

Recomiendo contactar a **666 de los 1.529 clientes activos** evaluados al 31 de diciembre de 2025. La seleccion combina la probabilidad estimada de cancelacion con el valor del plan de cada cliente. De esta forma, el equipo concentra el presupuesto donde la oferta tiene valor esperado positivo.

Bajo los supuestos entregados por la empresa, la campaña costaria aproximadamente **16,65 millones**, evitaria cerca de **53 cancelaciones** y generaria un **valor neto esperado de 11,13 millones**. La lista exacta esta incluida en `predicciones.csv`.

## Que esta asociado con la cancelacion

Las señales mas relevantes aparecen en tres frentes:

1. **Friccion digital.** Los errores recientes de la aplicacion y una baja actividad digital ayudan a identificar clientes con mayor riesgo.
2. **Experiencia de soporte.** Una satisfaccion baja, tickets abiertos y tiempos largos de resolucion preceden con mayor frecuencia a la cancelacion.
3. **Deterioro de pago.** Facturas vencidas, pagos tardios y menor proporcion de facturas pagadas aportan informacion adicional sobre riesgo.

Los tickets que expresan intencion de cancelar son especialmente informativos. El texto de soporte mejoro la identificacion de clientes de alto riesgo frente al mismo modelo que solo utilizaba variables estructuradas.

## Acciones propuestas

- Ejecutar la lista de 666 clientes priorizando el mayor valor esperado.
- Enviar los casos con errores frecuentes de aplicacion al equipo digital antes o junto con la oferta de retencion.
- Dar tratamiento acelerado a clientes con tickets abiertos, baja satisfaccion o quejas de facturacion.
- Conservar un grupo de control aleatorio entre clientes elegibles para medir cuantas cancelaciones evita realmente la oferta.
- Revisar resultados 90 dias despues y recalibrar la estrategia por plan y segmento.

## Limitaciones

El analisis encuentra asociaciones y no demuestra que un error, una factura o un ticket cause la cancelacion. La efectividad historica del contacto de retencion tampoco puede estimarse limpiamente porque los clientes no fueron asignados al azar. El valor estimado supone que la oferta retiene al 40% de quienes iban a cancelar y que ese efecto es igual para todos los planes.

El modelo se entreno con tres periodos de 2025. Debe monitorearse su precision y calibracion cuando se conozcan las cancelaciones reales posteriores a diciembre. Una variacion importante en comportamiento, precios, producto o politica de contacto exige revisar el modelo y la regla economica.
