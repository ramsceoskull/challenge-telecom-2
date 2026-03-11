# Telecom X - Parte 2

## Predicción de cancelación de clientes (Churn Prediction)

### Propósito del proyecto

El objetivo principal de este análisis es predecir la cancelación de clientes (Churn) en la empresa Telecom X utilizando técnicas de análisis de datos y modelos de machine learning.
Se busca identificar las variables que más influyen en la decisión de un cliente de cancelar el servicio y construir modelos predictivos capaces de anticipar este comportamiento.

Este análisis permite generar estrategias de retención basadas en datos, reduciendo la pérdida de clientes y mejorando la toma de decisiones.

---

### Preparación de los datos

#### Clasificación de variables

Las variables fueron clasificadas en:

* Variables categóricas
  Ejemplo: gender, contract, internet_service, payment_method, etc.

* Variables numéricas
  Ejemplo: tenure, monthly_charges, total_charges, cuentas_diarias.

Las variables categóricas fueron convertidas a formato numérico mediante **One-Hot Encoding**, permitiendo su uso en modelos de machine learning.

---

#### Eliminación de variables sin valor predictivo

Se eliminaron columnas como:

* customerID

Estas variables son identificadores únicos y no aportan información útil para la predicción.

---

#### Codificación de variables categóricas

Se utilizó:

```
pd.get_dummies()
```

Esto permitió transformar variables categóricas en variables binarias.

---

#### Normalización de datos

Se aplicó normalización usando:

```
StandardScaler
```

La normalización se utilizó únicamente en el modelo de Regresión Logística

Los modelos basados en árboles no requieren normalización.

---

#### División de datos

Los datos se dividieron en:

* 70% entrenamiento
* 30% prueba

Usando:

```
train_test_split(test_size=0.3, stratify=y)
```

Se utilizó stratify para mantener la proporción de churn.

---

### Modelos utilizados

Se entrenaron dos modelos diferentes:

1. Regresión Logística
2. Random Forest

Justificación:

* Regresión Logística requiere normalización
* Random Forest no depende de la escala
* Random Forest captura relaciones no lineales
* Regresión Logística permite interpretar coeficientes

---

### Análisis exploratorio (EDA)

Durante el análisis exploratorio se realizaron:
* Matriz de correlación
* Boxplots
* Scatter plots
* Distribución de la variable Churn

<img width="548" height="466" alt="image" src="https://github.com/user-attachments/assets/320793c0-dd0f-4c3b-9aa5-b6830f6fb789" />


Insights importantes:
* Los clientes con menor tenure cancelan más
* Contratos mensuales tienen mayor churn
* Clientes con cargos mensuales altos cancelan más
* El gasto total está relacionado con la permanencia
* Existe desbalance entre clientes activos y cancelados

Ejemplos de gráficos generados:
* Matriz de correlación
* Tenure vs Churn
* Total Charges vs Churn
* Matriz de confusión
* Importancia de variables

---

### Evaluación de modelos

Se evaluaron con:
* Accuracy
* Precision
* Recall
* F1-score
* Matriz de confusión

Resultados generales:
* Random Forest obtuvo mejor desempeño
* Regresión Logística fue más interpretable
* Random Forest puede presentar overfitting si no se ajusta
<img width="434" height="273" alt="image" src="https://github.com/user-attachments/assets/93c2ed72-9112-4b78-9ec8-c26be600de47" />

---

### Variables más importantes

Las variables más relevantes para predecir cancelación fueron:
* tenure
* monthly_charges
* total_charges
* contract
* internet_service
* payment_method

<img width="895" height="447" alt="image" src="https://github.com/user-attachments/assets/8eede70a-d4a8-4721-8962-cd79f389f5ad" />


Estas variables mostraron mayor correlación o mayor importancia en los modelos.

---

### Estrategias de retención propuestas

Basado en el análisis:

* Incentivar contratos a largo plazo
* Ofrecer beneficios a clientes nuevos
* Revisar planes con alto costo mensual
* Detectar clientes con alto riesgo de churn

---

### Conclusión

El uso de machine learning permitió identificar patrones claros en la cancelación de clientes.
Random Forest mostró el mejor rendimiento, mientras que la regresión logística permitió interpretar los factores más importantes.

Este análisis puede ser utilizado para implementar estrategias de retención y mejorar la satisfacción del cliente.
