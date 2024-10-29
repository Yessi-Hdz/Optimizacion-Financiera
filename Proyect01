import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Cargar los datos financieros
data = pd.read_csv('finanzas.csv')

# Calcular ROI y margen de ganancia
data['ROI'] = (data['ganancias'] - data['inversion']) / data['inversion'] * 100
data['margen_ganancia'] = (data['ganancias'] / data['ventas']) * 100

# Resumen de KPIs
kpi_summary = data[['mes', 'ROI', 'margen_ganancia']].groupby('mes').mean()
print(kpi_summary)

# Gráfico de tendencias de ventas
plt.figure(figsize=(12, 6))
plt.plot(data['mes'], data['ventas'], marker='o', color='blue', label='Ventas')
plt.title('Tendencias de Ventas a lo Largo del Tiempo')
plt.xlabel('Mes')
plt.ylabel('Ventas')
plt.xticks(rotation=45)
plt.grid()
plt.legend()
plt.show()

# Análisis de costos por categoría
costo_categoria = data.groupby('categoria')['gasto_real'].sum().sort_values(ascending=False)

plt.figure(figsize=(10, 6))
costo_categoria.plot(kind='bar', color='orange')
plt.title('Distribución de Costos por Categoría')
plt.xlabel('Categoría')
plt.ylabel('Costo Total')
plt.xticks(rotation=45)
plt.show()

# Comparación entre presupuesto y gasto real
data['desviacion'] = data['gasto_real'] - data['presupuesto']

plt.figure(figsize=(12, 6))
plt.bar(data['mes'], data['desviacion'], color='red')
plt.title('Desviaciones Presupuestarias por Mes')
plt.xlabel('Mes')
plt.ylabel('Desviación')
plt.xticks(rotation=45)
plt.axhline(0, color='green', linestyle='--')  # Línea de referencia en cero
plt.grid()
plt.show()
