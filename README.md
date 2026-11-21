# Conecta+ - Prediccion de cancelacion

Solucion de la prueba tecnica.

Repositorio: [https://github.com/DavidPerezz99/NttData_SrDS_test](https://github.com/DavidPerezz99/NttData_SrDS_test)

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DavidPerezz99/NttData_SrDS_test/blob/main/solucion.ipynb)

## Estructura

- `solucion.ipynb` contiene la carga, auditoria, construccion de variables, validacion temporal, modelado, calibracion, decision economica y exportacion.
- `predicciones.csv` contiene una fila por cliente activo con `cliente_id`, `probabilidad` y `contactar`.
- `MEMO.md` presenta la recomendacion para gerencia.
- `BITACORA_IA.md` documenta el uso de inteligencia artificial y las decisiones verificadas.
- `requirements.txt` registra las dependencias del notebook.
- `inicio.ipynb` es el notebook de carga suministrado con la prueba.

## Ejecucion en Google Colab

1. Abre `solucion.ipynb` en Colab.
2. Sube `datos_conecta.zip` al directorio de trabajo de la sesion.
3. Selecciona **Entorno de ejecucion > Ejecutar todas**.
4. Verifica que la ultima seccion confirme `predicciones.csv validado correctamente`.
5. Descarga `predicciones.csv` si necesitas conservar el resultado fuera de la sesion.

El notebook tambien funciona localmente cuando los archivos estan en `datos/` o `datos_conecta/`.

## Enfoque

La unidad de modelado es un cliente en una fecha de corte. Todas las variables transaccionales se calculan usando informacion disponible hasta ese momento. La validacion simula el avance del tiempo:

- Marzo predice junio de 2025.
- Marzo y junio predicen septiembre de 2025.
- El modelo final usa los tres cortes y puntua diciembre de 2025.

Se comparan una prevalencia base, regresion logistica estructurada, regresion logistica con TF-IDF de tickets y gradient boosting. Las probabilidades del modelo seleccionado se calibran con predicciones temporales fuera de muestra.

La decision de contacto se toma cuando el valor esperado es positivo:

```text
probabilidad * 40% * 12 * mensualidad - 25.000 COP > 0
```

Esto produce umbrales diferentes por plan.

## Reproducibilidad y datos

- Semilla global `42`.
- Aserciones sobre claves, poblacion, probabilidades y formato final.
- Salidas del notebook guardadas.
- Los datos y el archivo ZIP estan excluidos mediante `.gitignore` y no deben publicarse.

## Resultado de esta ejecucion

- 1.529 clientes puntuados.
- 666 clientes recomendados para contacto.
- 53,3 retenciones esperadas bajo los supuestos del enunciado.
- 11,13 millones COP de valor neto esperado.

Estas cifras dependen de la calibracion del modelo y del supuesto de efectividad del 40% para la oferta.
