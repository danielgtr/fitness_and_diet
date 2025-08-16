
# Formato Estándar para JSON Nutricional

Para asegurar que todos tus registros sean consistentes y comparables entre sí, es necesario seguir un formato estándar preciso. A continuación detallo las especificaciones exactas:

## Estructura Base del JSON

```json
{
  "date": "YYYY-MM-DD",
  "total_nutrition": { ... },
  "macro_distribution": { ... },
  "energy_balance": { ... },
  "meals": [ ... ]
}
```

## Definición Exacta de Cada Campo

### Campos Principales

| Campo | Tipo | Formato | Descripción | Ejemplo |
|-------|------|---------|-------------|---------|
| `date` | string | "YYYY-MM-DD" | Fecha en formato ISO | "2025-03-25" |

### Sección `total_nutrition`

| Campo | Tipo | Precisión | Unidad | Descripción |
|-------|------|-----------|--------|-------------|
| `calories` | number (int) | Entero | kcal | Total de calorías | 
| `protein` | number (float) | 1 decimal | g | Total de proteínas |
| `carbs` | number (float) | 1 decimal | g | Total de carbohidratos |
| `fat` | number (float) | 1 decimal | g | Total de grasas |
| `fiber` | number (float) | 1 decimal | g | Total de fibra |

### Sección `macro_distribution`

| Campo | Tipo | Precisión | Unidad | Descripción |
|-------|------|-----------|--------|-------------|
| `protein_pct` | number (float) | 1 decimal | % | Porcentaje calórico de proteínas |
| `carbs_pct` | number (float) | 1 decimal | % | Porcentaje calórico de carbohidratos |
| `fat_pct` | number (float) | 1 decimal | % | Porcentaje calórico de grasas |

### Sección `energy_balance`

| Campo | Tipo | Precisión | Unidad | Descripción |
|-------|------|-----------|--------|-------------|
| `resting_calories` | number (int) | Entero | kcal | Calorías en reposo (Garmin) |
| `active_calories` | number (int) | Entero | kcal | Calorías activas (Garmin) |
| `total_expenditure` | number (int) | Entero | kcal | Gasto total (suma de los anteriores) |
| `caloric_deficit` | number (int) | Entero | kcal | Déficit calórico (negativo = déficit) |
| `deficit_percentage` | number (float) | 1 decimal | % | Porcentaje de déficit |

### Sección `meals` (Array)

Cada elemento del array `meals` debe seguir esta estructura:

| Campo | Tipo | Descripción | Valores posibles |
|-------|------|-------------|------------------|
| `name` | string | Nombre de la comida | "Desayuno", "Almuerzo", "Comida", "Merienda", "Cena", "Snack" |
| `description` | string | Descripción concisa de la comida | "Sándwich de jamón", "Bowl de arroz con pollo", "Licuado proteico" |
| `time` | string | Momento del día | "mañana", "mediodía", "tarde", "noche" |
| `total_nutrition` | object | Estructura idéntica a la sección `total_nutrition` principal | |
| `foods` | array | Lista de alimentos | |

### Estructura de cada elemento en `foods`

| Campo | Tipo | Precisión | Obligatorio | Descripción |
|-------|------|-----------|-------------|-------------|
| `name` | string | | Sí | Nombre del alimento |
| `brand` | string | | No | Marca (omitir si no aplica) |
| `serving` | string | | Sí | Descripción de la porción |
| `serving_size_g` | number (float) | 1 decimal | Sí | Tamaño de porción en gramos |
| `calories` | number (float) | 1 decimal | Sí | Calorías por porción |
| `protein` | number (float) | 1 decimal | Sí | Proteínas por porción (g) |
| `carbs` | number (float) | 1 decimal | Sí | Carbohidratos por porción (g) |
| `fat` | number (float) | 1 decimal | Sí | Grasas por porción (g) |
| `fiber` | number (float) | 1 decimal | Sí | Fibra por porción (g) |

## Reglas Adicionales

1. **Campos obligatorios vs opcionales:**
   - El campo `brand` es opcional, pero si se incluye, debe estar presente en todos los alimentos que tengan marca
   - Para alimentos sin marca, omitir el campo `brand` completamente
   - El campo `description` es obligatorio para cada comida y debe describir brevemente el platillo o tipo de comida

2. **Consistencia en nomenclatura:**
   - Usar siempre los mismos nombres para comidas repetidas
   - Mantener el mismo formato de strings para alimentos recurrentes
   - Utilizar descripciones consistentes para comidas similares entre diferentes días

3. **Especificaciones del campo `description`:**
   - Debe ser una descripción concisa (2-6 palabras)
   - Debe describir el tipo general de comida, no listar todos los ingredientes
   - Utilizar términos consistentes para facilitar la comparación entre días

4. **Precisión numérica:**
   - Calorías totales diarias y por comida: valores enteros
   - Calorías por alimento individual: 1 decimal
   - Macronutrientes: siempre 1 decimal (ej: "protein": 25.0 en lugar de "protein": 25)

5. **Cálculo de totales:**
   - Los valores en `total_nutrition` de cada comida deben ser la suma exacta de todos los alimentos
   - Los valores en `total_nutrition` a nivel global deben ser la suma exacta de todas las comidas

## Ejemplo de Estructura JSON Completa

```json
{
  "date": "YYYY-MM-DD",
  "total_nutrition": {
    "calories": 0,
    "protein": 0.0,
    "carbs": 0.0,
    "fat": 0.0,
    "fiber": 0.0
  },
  "macro_distribution": {
    "protein_pct": 0.0,
    "carbs_pct": 0.0,
    "fat_pct": 0.0
  },
  "energy_balance": {
    "resting_calories": 0,
    "active_calories": 0,
    "total_expenditure": 0,
    "caloric_deficit": 0,
    "deficit_percentage": 0.0
  },
  "meals": [
    {
      "name": "string",
      "description": "string",
      "time": "string",
      "total_nutrition": {
        "calories": 0,
        "protein": 0.0,
        "carbs": 0.0,
        "fat": 0.0,
        "fiber": 0.0
      },
      "foods": [
        {
          "name": "string",
          "brand": "string",
          "serving": "string",
          "serving_size_g": 0.0,
          "calories": 0.0,
          "protein": 0.0,
          "carbs": 0.0,
          "fat": 0.0,
          "fiber": 0.0
        }
      ]
    }
  ]
}
```
