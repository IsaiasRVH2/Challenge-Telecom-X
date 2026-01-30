# Telecom X - Análisis de Evasión de Clientes 📊

Proyecto desarrollado como parte del **Challenge 2** del programa **Oracle Next Education (ONE)** en colaboración con Alura LATAM.

## 📑 Índice

- [Descripción del Proyecto](#-descripción-del-proyecto)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Tecnologías Utilizadas](#️-tecnologías-utilizadas)
- [Cómo Ejecutar el Proyecto](#-cómo-ejecutar-el-proyecto)
- [Proceso ETL](#-proceso-etl)
- [Principales Hallazgos](#-principales-hallazgos)
- [Recomendaciones Estratégicas](#-recomendaciones-estratégicas)
- [Conclusiones](#-conclusiones)
- [Autor](#-autor)

## 🎯 Descripción del Proyecto

**Telecom X** enfrenta un desafío crítico: una alta tasa de cancelaciones de servicios (**26.5%** de abandono). Este proyecto tiene como objetivo analizar los factores que influyen en la decisión de los clientes de abandonar el servicio, mediante un proceso completo de **ETL** (Extracción, Transformación y Carga) y **Análisis Exploratorio de Datos (EDA)**.

### Objetivos

- 🔍 Identificar patrones y factores que influyen en la evasión de clientes
- 📈 Generar visualizaciones estratégicas para facilitar la toma de decisiones
- 💡 Proporcionar recomendaciones accionables para reducir la tasa de abandono
- 📊 Preparar los datos para futuros modelos predictivos de Machine Learning

## 📁 Estructura del Proyecto

```
Challenge-Telecom-X/
│
├── TelecomX_LATAM.ipynb          # Notebook principal con análisis completo
├── TelecomX_diccionario.md       # Diccionario de datos del proyecto
├── README.md                      # Este archivo
│
└── figuras/                       # Gráficos generados durante el análisis
    ├── distribucion_abandono_numericas.png
    ├── grafico_abandono_Género.png
    ├── grafico_abandono_Veterano.png
    ├── grafico_correlacion_no_ohe.png
    └── ...
```

## 🛠️ Tecnologías Utilizadas

- **Python 3.x**
- **Pandas**: Manipulación y análisis de datos
- **NumPy**: Operaciones numéricas
- **Matplotlib**: Visualización de datos
- **Seaborn**: Visualizaciones estadísticas avanzadas
- **Requests**: Extracción de datos desde API
- **JSON**: Manejo de datos en formato JSON
- **Jinja2**: Renderizado de estilos en DataFrames

## 🚀 Cómo Ejecutar el Proyecto

### Requisitos Previos

1. Tener instalado **Python 3.8+**
2. Tener instalado **Jupyter Notebook** o **VS Code** con extensión de Python

### Instalación

1. Clona este repositorio:
```bash
git clone https://github.com/IsaiasRVH2/Challenge-Telecom-X.git
cd Challenge-Telecom-X
```

2. Instala las dependencias necesarias:
```bash
pip install pandas numpy matplotlib seaborn requests jupyter jinja2
```

### Ejecución

1. Abre el notebook en Jupyter:
```bash
jupyter notebook TelecomX_LATAM.ipynb
```

O si usas VS Code, simplemente abre el archivo `TelecomX_LATAM.ipynb`.

2. Ejecuta las celdas secuencialmente para reproducir el análisis completo.

## 🔄 Proceso ETL

### 1. **Extracción (Extract)**
- Obtención de datos desde la API: [TelecomX_Data.json](https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json)
- Normalización de estructura JSON anidada
- **Resultado**: 7,267 registros con 21 características

### 2. **Transformación (Transform)**

#### Limpieza de Datos:
- ✅ Eliminación de 224 registros con valores nulos en la columna `Churn`
- ✅ Imputación de 11 valores faltantes en `Cargo Total`
- ✅ Validación de formatos y coherencia de datos

#### Transformaciones Aplicadas:
- 🔢 Conversión de variables binarias (Yes/No) a formato numérico (1/0)
- 🎯 **One Hot Encoding** para 10 variables categóricas
- 🌐 Traducción de nombres de columnas de inglés a español
- ➕ Creación de variable derivada: `Cuentas Diarias`

### 3. **Carga (Load)**
- **Dataset Final**: 7,043 registros × 43 características
- Datos listos para análisis y visualización

Para más detalles sobre las variables, consulta el archivo [`TelecomX_diccionario.md`](TelecomX_diccionario.md).

## 🎯 Principales Hallazgos

### 1. 🚨 **La Antigüedad es el Factor Crítico**
- Los primeros **6 meses** son el periodo de mayor riesgo de abandono
- La probabilidad de fuga disminuye drásticamente con el tiempo
- **Correlación fuerte** entre baja antigüedad y alta tasa de abandono

### 2. 💳 **Método de Pago: Punto Crítico**
- **Cheque Electrónico**: **45.3%** de tasa de abandono
- Más del **doble** que cualquier otro método de pago
- Representa una fricción significativa en la experiencia del cliente

### 3. 👴 **Segmento "Veteranos": Alta Vulnerabilidad**
- Casi el **50%** de los clientes veteranos (≥65 años) abandonan el servicio
- A pesar de representar solo el **16.21%** de la base de clientes
- Requiere atención especializada

### 4. 📝 **Tipo de Contrato: Clave de Retención**
- **Mes a Mes**: Alta volatilidad y tasa de abandono elevada
- **Contrato Anual**: Tasa de abandono significativamente menor
- **Contrato Bianual**: Tasa de abandono mínima

### 5. 🌐 **Internet Fibra Óptica: Problema Detectado**
- Tasa de abandono **más del doble** que DSL
- Casi **6 veces mayor** que clientes sin internet
- Indica problemas con la calidad del servicio o expectativas no cumplidas

### 6. 🛡️ **Servicios Adicionales: Ancla de Retención**
- Clientes **sin** servicios de protección (Soporte Técnico, Seguridad Online, Backup) tienen mayor propensión al abandono
- Los servicios adicionales aumentan el valor percibido y la dependencia

## 💡 Recomendaciones Estratégicas

### 1. 🎁 **Programa "Primeros Pasos"**
- Descuentos escalonados durante los primeros 6 meses
- Velocidad aumentada temporal con opción de permanencia
- Onboarding personalizado y seguimiento activo

### 2. 💳 **Migración de Métodos de Pago**
- Incentivos para autopago (transferencia/tarjeta): descuentos o velocidad adicional
- Rediseñar comunicación de facturación electrónica: enfoque en valor, no solo en cobro

### 3. 👴 **Atención Especializada a Veteranos**
- Plan con soporte técnico telefónico prioritario
- Capacitación y acompañamiento personalizado
- Comunicación clara y accesible

### 4. 📋 **Fidelización Contractual**
- Garantía de precio para contratos anuales
- Beneficios exclusivos para compromisos a largo plazo
- Facilitar migración desde "Mes a Mes"

### 5. 🛡️ **Ecosistema de Protección**
- Incluir "Seguridad Online" y "Soporte Técnico" gratuitamente durante primeros meses
- Crear bundles atractivos de servicios adicionales
- Demostrar valor tangible de servicios de protección

### 6. 🌐 **Mejora Servicio Fibra Óptica**
- Auditoría de calidad del servicio
- Gestión proactiva de expectativas
- Compensación por interrupciones

## 📝 Conclusiones

El análisis revela que la fuga de clientes en **Telecom X** no es aleatoria, sino resultado de **fricciones específicas** en la experiencia del usuario y la estructura de contratación:

✅ **La lealtad se construye en los primeros 6 meses**: Este periodo es crítico y requiere blindaje estratégico

✅ **El método de pago es un obstáculo silencioso**: Migrar de cheque electrónico a pagos automáticos es fundamental

✅ **La flexibilidad contractual favorece la rotación**: Los contratos "Mes a Mes" deben ser replanteados

✅ **El producto es competitivo, pero el modelo comercial favorece la fuga**: La estrategia debe centrarse en **retener, no solo captar**

### ROI de las Recomendaciones

Implementar estas estrategias puede reducir la tasa de abandono del **26.5%** actual a menos del **15%** en el primer año, representando:
- 💰 Reducción de costos de adquisición de nuevos clientes
- 📈 Aumento del valor de vida del cliente (CLV)
- 🎯 Mejora en satisfacción y reputación de marca

---

## 👨‍💻 Autor

Desarrollado como parte del **Oracle Next Education (ONE) - Challenge 2**

**Isaías Ricardo Valdivia**

🔗 LinkedIn: [Isaías Ricardo Valdivia](https://www.linkedin.com/in/isaias-valdivia/)
🔗 GitHub: [@IsaiasRVH2](https://github.com/IsaiasRVH2)


---

### 📄 Licencia

Este proyecto fue desarrollado con fines educativos como parte del programa Oracle Next Education (ONE).

---

**⭐ Si este proyecto te fue útil, no olvides darle una estrella!**
