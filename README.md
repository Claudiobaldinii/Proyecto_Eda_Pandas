# 📄 Proyecto EDA — Campañas Bancarias

## 📌 Propósito del proyecto
Este proyecto tiene como objetivo realizar un **Análisis Exploratorio de Datos (EDA)** sobre campañas de marketing telefónico de un banco portugués.  

El objetivo principal es explorar **qué factores influyen en la suscripción de un depósito a plazo fijo** (`suscripcion = Yes/No`).  

Se busca:  
- Entender la distribución de los datos.  
- Identificar valores atípicos y nulos.  
- Analizar perfiles de clientes y condiciones de campaña más asociadas al éxito.  
- Obtener insights de negocio a partir de las visualizaciones.  

---

## ⚙️ Pasos para ejecutar el proyecto
1. Clonar o descargar el repositorio.  
2. Guardar los datasets en la carpeta `data/raw/`:  
   - `bank-additional.csv` (campañas de marketing).  
   - `customer-details.xlsx` (3 hojas con datos de clientes).  
3. Abrir y ejecutar el notebook **Proyecto_EDA.ipynb** en VS Code o Jupyter Notebook.  
4. El notebook está estructurado en etapas:  
   - 🔍 Inspección inicial.  
   - 🧹 Limpieza y transformación.  
   - 🔗 Unificación de tablas (`df_master`).  
   - 📊 Análisis descriptivo y visualizaciones.  
   - 📈 Conclusiones finales.  

---

## 📊 Principales hallazgos del análisis

### 🔹 Calidad de los datos
Se detectó una alta presencia de valores nulos en variables como:  
- `pdays` (~96% NaN, porque la mayoría nunca fue contactado antes).  
- `euribor3m`, `default` (~20%).  

**Decisión:** en un EDA exploratorio no se imputan, se dejan para describir el dataset tal cual.  
**Justificación:** mantener los nulos preserva la fidelidad del análisis; eliminarlos o imputarlos habría introducido sesgos.  

---

### 🔹 Variables clave
- **`Duration` (tiempo de llamada)** → factor más asociado al éxito.  
  - Llamadas largas → mucho más probabilidad de “yes”.  
- **`Campaign` (nº de contactos)** → demasiados intentos reducen la tasa de éxito.  
- **Edad** → extremos (18–24 y >60) muestran más “yes”; las franjas medias (30–50) son más resistentes.  
- **Marital** → solteros más positivos que casados/divorciados.  
- **Job** → *retired* y *student* destacan con mayor % de “yes”; *blue-collar* y *services* menos.  
- **Housing/Loan** → no muestran diferencias claras.  

---

### 🔹 Variables macroeconómicas
- `euribor3m`, `emp_var_rate`, `nr_employed` están **altamente correlacionados** (aportan información redundante).  

---

### 🔹 Tendencia temporal
El **% de éxito crece año a año**:  
- 2012 ≈ **4.6%**  
- 2013 ≈ **7.7%**  
- 2014 ≈ **23.0%** ✅  

👉 Este aumento refleja que la campaña de 2014 fue mucho más efectiva que en años anteriores, posiblemente por mejoras en la segmentación y en la calidad de las llamadas.  

---

