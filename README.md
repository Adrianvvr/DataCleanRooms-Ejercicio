# 🔒 Práctica: Simulación de una Data Clean Room (DCR)

> **📌 Entrega:** Debes entregar el notebook **`practica_dcr.ipynb` resuelto y con todas las celdas ejecutadas** (con sus salidas visibles).

---

* Clona el repositorio desde esta URL: `https://github.com/Adrianvvr/DataCleanRooms-Ejercicio`

## 🎯 Escenario

Dos empresas colaboran cruzando sus datos sin revelar información personal ni compartir sus bases de datos originales:

- **Empresa A (`StreamMusic`):** Historial de escucha (`genero_favorito`, `horas_mes`).
- **Empresa B (`FitWear`):** Compras en tienda online (`gasto_eur`, `es_recurrente`).

La Clean Room cruza ambas tablas mediante un hash anónimo (`SHA-256`) y solo devuelve resultados agregados si el grupo tiene al menos **15 usuarios (k-anonimato)**.

---

## 🚀 Qué tienes que hacer

1. Abre `practica_dcr.ipynb` y ejecuta las **Celdas 1 y 2** para cargar los datos y comprobar cómo la DCR bloquea el acceso a datos crudos o grupos pequeños.
2. **Ejercicio 1 (Celda 3):** Usa `dcr.consultar_agregado(...)` agrupando por `"genero_favorito"` (opcionalmente filtrando por `"es_recurrente == True"`) para identificar el género musical con mayor gasto medio.
3. **Ejercicio 2 (Celda 4):** Cruza variables de ambas empresas a la vez agrupando por `["genero_favorito", "es_recurrente"]` y filtrando por oyentes muy activos (`"horas_mes >= 40"`). Comprueba qué micro-segmento gasta más y cómo los grupos menores de 15 usuarios se ocultan automáticamente.

---

## 💡 Guía rápida

- **Consultar la Clean Room:**
  - 1 columna: `resultado = dcr.consultar_agregado(agrupar_por="x", filtro="variable == False")`
  - 2 columnas: `resultado = dcr.consultar_agregado(agrupar_por=["x", "y"], filtro="z >= 10")`
- **Sacar el ganador:** La tabla viene ordenada de mayor a menor gasto medio, así que el primero está en `resultado.index[0]`:
  - Con 1 columna: `x = resultado.index[0]`
  - Con 2 columnas: `y, es_rec = resultado.index[0]`
