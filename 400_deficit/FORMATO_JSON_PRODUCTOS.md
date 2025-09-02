# FORMATO JSON PARA AGREGAR PRODUCTOS A LA BASE DE DATOS

## PROPÓSITO
Este formato se utiliza **únicamente** cuando el usuario presenta una foto o información de etiqueta nutricional de un producto nuevo que debe agregarse a la base de datos.

**IMPORTANTE**: Este formato NO se usa para respuestas de breakdown de comidas. Las respuestas normales son en texto plano.

## ESTRUCTURA ESTÁNDAR

```json
{
  "name": "nombre_descriptivo_producto",
  "brand": "Nombre de la Marca",
  "serving": "cantidad y unidad según etiqueta",
  "serving_size_g": cantidad_en_gramos,
  "calories": calorías_decimales,
  "protein": proteinas_decimales,
  "carbs": carbohidratos_decimales,
  "fat": grasas_decimales,
  "fiber": fibra_decimales
}
```

## REGLAS DE NOMENCLATURA

### Campo "name"
- **Sin marca en el nombre** - usar descripción genérica
- **Formato**: minúsculas con guiones bajos
- **Ejemplo**: `"chocolate_95_cacao"` (no `"chocolate_lindt_95"`)

### Campo "brand"
- **Solo la marca** sin descriptivos adicionales
- **Ejemplo**: `"Lindt"`, `"Alpura"`, `"McCormick"`
- **Si no hay marca visible**: omitir el campo completamente

### Campo "serving"
- **Exactamente lo que especifica la etiqueta nutricional**
- **Formato**: cantidad + unidad + descripción si es necesaria
- **Ejemplos**: 
  - `"100g"`
  - `"250ml"`
  - `"65g (1 gel)"`
  - `"80g (1 paquete)"`

## REGLAS NUMÉRICAS

### Precisión
- **Calories**: número con 1 decimal (ej: 162.5)
- **Macronutrientes**: números con 1 decimal (ej: 40.6)
- **serving_size_g**: número con 1 decimal

### Consistencia
- **Siempre incluir .0** para números enteros (ej: 21.0, no 21)
- **Todos los macros obligatorios**: protein, carbs, fat, fiber

## EJEMPLOS COMPLETOS

### Producto con Marca
```json
{
  "name": "gel_energetico_160",
  "brand": "Maurten",
  "serving": "65g (1 gel)",
  "serving_size_g": 65.0,
  "calories": 162.5,
  "protein": 0.0,
  "carbs": 40.6,
  "fat": 0.0,
  "fiber": 0.0
}
```

### Producto sin Marca Visible
```json
{
  "name": "vinagre_arroz_dulce",
  "serving": "100g",
  "serving_size_g": 100.0,
  "calories": 54.0,
  "protein": 5.9,
  "carbs": 13.4,
  "fat": 1.2,
  "fiber": 1.1
}
```

## PROCESO DE CREACIÓN

1. **Identificar información de la etiqueta**
2. **Extraer valores nutricionales por porción especificada**
3. **Convertir a formato JSON usando las reglas arriba**
4. **Verificar consistencia numérica**
5. **Agregar al final del archivo BASE_DATOS_ALIMENTOS.jsonl**

## VALIDACIONES IMPORTANTES

- ✅ Nombre descriptivo sin marca
- ✅ Serving exacto de la etiqueta
- ✅ Todos los macros con 1 decimal
- ✅ Campo brand solo si hay marca visible
- ✅ Consistencia en unidades (gramos para serving_size_g)

Este formato garantiza que los nuevos productos se integren correctamente con el sistema existente y puedan ser utilizados en cálculos futuros.