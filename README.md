# Predicción de Beneficios de Seguros - Modelo de Clasificación Multiclase

Este proyecto implementa un modelo de clasificación multiclase para predecir la cantidad de beneficios que un cliente de seguros puede recibir, basado en características demográficas. Se exploraron múltiples modelos de machine learning para encontrar el que mejor predice los beneficios asignados.

## 1. Preprocesamiento de Datos

- No existen filas con información ausente.
- No hay datos duplicados.
- La base de datos contiene **5000 registros y 5 columnas**.
- Todos los datos son numéricos (tipos `int` y `float`).

### Descripción de las columnas:
- **genre**: Tipo binario (1 y 0).
- **age**: Edad del cliente.
- **salary**: Salario anual.
- **family_members**: Cantidad de integrantes de la familia.
- **insurance_benefits**: Cantidad de beneficios recibidos (variable objetivo).

## 2. Análisis Exploratorio

- La cantidad de clientes hombres y mujeres es aproximadamente igual.
- La edad mínima es **18 años** y la máxima **65 años**.
- La mayoría de los clientes tienen entre **18 y 40 años**.
- El salario varía entre **5,300 UM y 79,000 UM**.
  - Mediana: **40,200 UM**.
  - Media: **39,916 UM**.
  - El **50%** de los datos tienen un sueldo menor a **40,200 UM**.
- En promedio, los clientes tienen **un solo miembro familiar**, con un máximo de **6**.
- La mayoría de los clientes **no reciben beneficios**.
  - Solo el **10% de los datos** tienen clientes con beneficios, y **el 79% de estos solo recibe un beneficio**.

## 3. Relación entre Variables

### **Género vs. Beneficios**
No hay un patrón claro entre género y cantidad de beneficios recibidos. En ambos casos, solo **el 11%** recibe beneficios.

### **Edad vs. Beneficios**
- A partir de los **45 años**, los clientes comienzan a recibir beneficios.
- A los **55 años**, los clientes pueden recibir más de **2 beneficios**.
- La cantidad de beneficios aumenta con la edad.

### **Salario vs. Beneficios**
- A medida que aumentan los beneficios, el rango de salarios se reduce.
- Quienes reciben **1 beneficio** tienen sueldos entre **13,000 y 70,000 UM**.
- Quienes reciben **2 beneficios** tienen sueldos entre **15,000 y 60,000 UM**.

### **Familiares vs. Beneficios**
- Las personas sin integrantes familiares tienen **mayor probabilidad de recibir beneficios**.
- Esto podría estar relacionado con la edad, ya que personas mayores suelen vivir sin dependientes.
- Personas con **más integrantes familiares** suelen recibir menos beneficios (0 o 1 beneficio en la mayoría de los casos).

## 4. Preparación de Datos para Modelado

- Los datos se dividieron en:
  - **Entrenamiento (80%)**
  - **Validación (20%)**
- La **variable objetivo** es `insurance_benefits`.
- Las demás variables se utilizaron como **características** para los modelos.

## 5. Entrenamiento y Evaluación de Modelos

Se probaron varios modelos para encontrar el más preciso:

### Modelos Utilizados:
- **Stochastic Gradient Descent Classifier (SGD)**: Método rápido y eficiente para grandes volúmenes de datos, con bajo riesgo de sobreajuste.
- **Random Forest**: Alta precisión, estable y resistente al sobreajuste.
- **Logistic Regression**: Ágil y eficaz en problemas de clasificación multiclase.
- **Decision Tree Classifier**: Fácil de interpretar.
- **Gradient Boosting Classifier**: Modelo con alta precisión, entrena secuencialmente los árboles para corregir errores previos y minimizar sobreajuste.

Para evitar el sobreajuste, se utilizó **cross_val_predict**.

### Métricas de Evaluación:
- **Matriz de confusión**
- **F1-score**
- **Recall**
- **Precisión**

## 6. Elección del Modelo Final

El modelo con la **mayor precisión** será seleccionado para la predicción final.
