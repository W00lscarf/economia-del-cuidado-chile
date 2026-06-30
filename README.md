# Economía del Cuidado en Chile: el trabajo invisible 🇨🇱

> *Las mujeres chilenas dedican el doble de tiempo que los hombres al trabajo doméstico y de cuidados no remunerado. ¿Cómo se distribuye esa carga según ingresos, edad y condición laboral — y qué costo tiene en el mercado laboral?*

Este proyecto analiza la **economía del cuidado** en Chile usando datos de la Encuesta Nacional de Uso del Tiempo (ENUT) y la Encuesta Suplementaria de Ingresos (ESI), ambas disponibles vía la **API SDMX del SIMEL-INE** sin necesidad de registro.

---

## Por qué importa

El trabajo doméstico y de cuidados es trabajo — solo que no se paga ni se contabiliza en el PIB. En Chile, ese trabajo recae desproporcionadamente en las mujeres, limitando su participación laboral y perpetuando brechas salariales. Cuantificarlo es el primer paso para diseñar políticas que lo redistribuyan.

Este análisis conecta tres dimensiones:
1. **¿Cuánto tiempo** se dedica al cuidado, y quién lo hace
2. **¿Cómo varía** según posición socioeconómica (quintil), condición laboral y edad
3. **¿Qué relación tiene** con la participación laboral femenina por región

---

## Hallazgos principales

| Indicador | Mujeres | Hombres | Brecha |
|-----------|---------|---------|--------|
| Horas semanales trabajo no remunerado (2023) | 4.5 hrs/día | 2.6 hrs/día | **+73%** |
| Carga global total (remunerado + no remunerado) | — | — | *ver notebook* |
| Participación laboral (2023) | — | — | *ver notebook* |

---

## Datos — API SIMEL-INE

Todos los datos se descargan directamente desde la API pública del INE. **No requiere registro ni credenciales.**

| Dataset SIMEL | Descripción | Fuente original |
|---------------|-------------|-----------------|
| `DF_HRS_TNR_SEXO` | Horas de trabajo no remunerado por sexo | ENUT 2015, 2023 |
| `DF_HRS_TNR_SEXO_QUINTIL` | Lo mismo por quintil de ingresos | ENUT 2015, 2023 |
| `DF_HRS_TNR_SEXO_CLAB` | Por condición de actividad laboral | ENUT 2015, 2023 |
| `DF_HRS_TNR_SEXO_EDAD` | Por tramo etario | ENUT 2015, 2023 |
| `DF_HRS_TRAB_TOT_SEXO` | Carga global (remunerado + no remunerado) | ENUT 2015, 2023 |
| `DF_FDT_SEXO` | Fuerza de trabajo por sexo y región | ENE trimestral |
| `DF_BGYMEDIOOCU` | Brecha salarial de género por región | ESI anual |

**Endpoint base:**
```
https://sdmx.ine.gob.cl/rest/data/CL01,{DATASET},1.0?format=csv
```

---

## Estructura del proyecto

```
economia-del-cuidado-chile/
├── notebooks/
│   ├── 01_descarga_exploracion.ipynb   ← API + EDA
│   ├── 02_carga_cuidados.ipynb         ← análisis de distribución
│   └── 03_visualizaciones.ipynb        ← figuras publicables
├── src/
│   └── plots.py                        ← funciones de visualización
├── outputs/
│   ├── figures/                        ← PNG/SVG exportados
│   └── tables/                         ← CSV de resultados
└── requirements.txt
```

---

## Cómo reproducir

```bash
git clone https://github.com/W00lscarf/economia-del-cuidado-chile
cd economia-del-cuidado-chile
pip install -r requirements.txt
jupyter lab
# Ejecutar notebooks en orden: 01 → 03
```

Los datos se descargan automáticamente desde la API al ejecutar el notebook 01.

---

## Stack técnico

**Python 3.11** · pandas · matplotlib · seaborn · plotly · requests · scipy

---

## Marco conceptual

El análisis se apoya en el marco de la **economía feminista** (Folbre 1994; Esquivel 2011) y los indicadores de **trabajo decente** de la OIT, adoptados por el SIMEL-INE como base conceptual. La ENUT 2023 es la fuente más reciente de medición del uso del tiempo en Chile — la anterior data de 2015, lo que permite análisis de cambio en 8 años.

---

## Contexto del autor

Análisis desarrollado combinando formación en **psicología** (UV), **políticas públicas** (MPP-UDP) y **data science** (Diplomado UDD). La perspectiva interdisciplinaria permite ir más allá del dato hacia sus implicancias de política.

---

## Licencia

MIT — libre uso con atribución. Los datos son de acceso público vía INE Chile.
