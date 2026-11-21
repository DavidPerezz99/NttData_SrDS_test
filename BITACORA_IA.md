# Bitacora de uso de inteligencia artificial

## Alcance

Se utilizo inteligencia artificial como apoyo para auditar las fuentes, revisar riesgos de fuga de informacion, implementar el notebook y verificar su ejecucion. Las recomendaciones se contrastaron con los datos y con resultados reproducibles del notebook.

## Momentos principales


### 1. Auditoria de calidad

**Validado:** 63 edades invalidas, variantes de ciudad, 630 repeticiones de `factura_id`, 1.718 eventos exactamente duplicados, dos modelos principales de tickets y claves de cliente con formatos diferentes.

**Correccion aplicada:** las edades 0 y 999 se trataron como faltantes con un indicador adicional. Las ciudades y tickets se normalizaron. Los eventos exactos se eliminaron.

### 2. Prevencion de fuga de informacion


**Validado:** usar directamente `estado_actual`, `contactado_por_retencion` o la fecha final de contacto en observaciones historicas.

**Correccion aplicada:** todos los eventos, tickets, suscripciones y facturas se filtran por corte. Las facturas repetidas se resuelven despues de aplicar cada corte, conservando la ultima carga disponible en ese momento.

### 3. Modelado y texto


**Validado:** prevalencia, regresion logistica estructurada, regresion logistica con TF-IDF y gradient boosting. El texto utiliza exclusivamente mensajes escritos por clientes y sus predicciones se evaluan en periodos posteriores.

**Resultado verificado:** la regresion logistica con TF-IDF mejoro la precision promedio y el valor de validacion frente a la misma regresion sin texto. Gradient boosting obtuvo mejor ROC-AUC y Brier sin calibrar. La seleccion agrego ranking, calibracion y valor de negocio.

### 4. Revision de interpretabilidad

**Correccion aplicada:** una primera version calculaba importancia sobre septiembre usando el modelo final, que ya habia visto septiembre. Se reemplazo por un modelo entrenado solamente con marzo y junio antes de medir importancia en septiembre.

### 5. Decision economica y entrega


**Implementado:** usar un umbral diferente por plan y contactar solo cuando el valor esperado sea positivo. Se agregaron aserciones sobre filas, identificadores, probabilidades, nulos y formato del CSV.


## Tiempo invertido

**Tiempo:** 5 horas.

La ejecucion asistida cubrio exploracion, implementacion, dos ciclos completos de validacion y preparacion de entregables.
