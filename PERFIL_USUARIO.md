# PERFIL DE USUARIO - DATOS PERSONALES Y OBJETIVOS

## CONFIGURACIÓN VARIABLES DEL SISTEMA
### Variables Principales (MODIFICAR AQUÍ PARA CAMBIOS GLOBALES)
- **DÉFICIT_OBJETIVO**: 400 kcal
- **CALORÍAS_REPOSO**: 1,949 kcal/día
- **GASTO_POR_KM**: 61 kcal/km

## DATOS ANTROPOMÉTRICOS
- **Altura**: 167 cm
- **Peso actual**: 64.85 kg
- **Objetivo**: Alcanzar peak shape para rendimiento óptimo

## PERFIL DEPORTIVO
- **Disciplina principal**: Maratón
- **Personal Best (PB)**: 3h07:08
- **Nivel**: Corredor experimentado/competitivo

## DATOS METABÓLICOS (GARMIN)
- **Calorías en reposo promedio**: CALORÍAS_REPOSO (configurado arriba)
  - Calculado como promedio de las últimas 4 semanas
  - Fuente: Garmin (datos confiables)
- **Gasto energético por kilómetro**: GASTO_POR_KM (configurado arriba)
  - Promedio personal para cálculos de ejercicio

## OBJETIVO NUTRICIONAL
- **Meta principal**: Déficit calórico fijo de DÉFICIT_OBJETIVO (configurado arriba)
- **Propósito**: Optimización de composición corporal para peak performance
- **Metodología**: Control preciso de ingesta vs gasto energético

## FÓRMULAS DE CÁLCULO PERSONALIZADAS

### Gasto Calórico Diario
```
Gasto Total = CALORÍAS_REPOSO + Calorías ejercicio
```

### Calorías Objetivo Diarias
```
Objetivo Ingesta = Gasto Total - DÉFICIT_OBJETIVO
```

### Cálculo de Ejercicio
```
Calorías ejercicio = Distancia (km) × GASTO_POR_KM
```

## PREFERENCIAS ALIMENTARIAS
- Comidas estructuradas y predefinidas para consistencia
- Enfoque en macronutrientes balanceados
- Flexibilidad en ajustes de cena según actividad diaria

## NOTAS IMPORTANTES
- Priorizar datos específicos de Garmin cuando estén disponibles
- Si no se menciona ejercicio específico, usar solo CALORÍAS_REPOSO
- Mantener consistencia en patrones alimentarios para mejor adherencia
- **Para cambiar déficit objetivo**: modificar solo DÉFICIT_OBJETIVO arriba