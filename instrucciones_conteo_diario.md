### Paso 1: Calcular Gasto Calórico Total
```
Gasto Total = Calorías en reposo (1,949) + Calorías de ejercicio
```

### Paso 2: Calcular Calorías Objetivo (Déficit 18%)
```
Calorías Objetivo = Gasto Total × 0.82
```

### Paso 3: Calcular Calorías Disponibles para Cena
```
Calorías Disponibles = Calorías Objetivo - Desayuno - Comida
```# Instrucciones para Conteo Calórico Diario y Ajuste de Cena

## Objetivo Principal
Mantener un déficit calórico del 18% diario ajustando automáticamente la cena según la actividad física y consumo previo del día.

## Datos Base de Referencia
- **Calorías en reposo:** 1,949 (Garmin)
- **Déficit objetivo:** 18%
- **Meta calórica diaria:** 82% del gasto calórico total del día (variable según actividad)

## Comidas Estándar Predefinidas

### Desayuno Estándar
- 3 huevos cocidos
- Sándwich completo (pan integral + 60g jamón + vegetales + aderezos)
- **Total:** 606 calorías

### Comida Estándar
- 180g arroz integral preparado
- 110g betabel cocido
- 120g zanahoria cocida  
- 120g brócoli cocido
- 170g papa cocida
- 180g proteína (opciones):
  - **Con pechuga de pollo:** 899 calorías
  - **Con bistec magro:** 908 calorías

### Opciones de Cena

#### Cena Opción 1 - Yogurt Preparado (DEFAULT)
- 105g yogurt griego
- 10g nuez pecán
- 7g semillas de chía
- 7g chocolate 95%
- 10g mantequilla de maní
- **Total:** 272 calorías

#### Cena Opción 2 - Licuado Completo
- 200ml leche deslactosada
- 30.4g proteína en polvo
- 120g plátano
- **Total:** 323 calorías

## Cálculos Previos

### Paso 1: Calcular Gasto Calórico Total
```
Gasto Total = Calorías en reposo (1,949) + Calorías de ejercicio
```

### Paso 2: Calcular Calorías Objetivo (Déficit 18%)
```
Calorías Objetivo = Gasto Total × 0.82
```

### Paso 3: Calcular Calorías Disponibles para Cena
```
Calorías Disponibles = Calorías Objetivo - Desayuno - Comida
```

## Secuencia Lógica para Decidir la Cena

### Paso 0: Verificación Previa (Crítica)
- **Condición:** Si ya se excedieron las calorías objetivo antes de la cena
- **Acción:** Informar que ya se superó el objetivo calórico y NO proponer ninguna cena

### Paso 1: Agregar Yogurt Preparado (Acción Base)
- **Acción:** Siempre agregar yogurt preparado completo (272 calorías)
- **Verificación:** Si yogurt completo excede las calorías disponibles
  - Ajustar yogurt proporcionalmente para cumplir exactamente el objetivo
  - Factor de ajuste = Calorías Disponibles / 272
  - Porción ajustada = 105g × Factor de ajuste
- **Cálculo:** Calorías Restantes = Calorías Disponibles - Yogurt (completo o ajustado)

### Paso 2: Verificar si Faltan Calorías (Solo si yogurt completo no excede)
- **Condición:** Si Calorías Restantes > 0 (todavía faltan calorías para el objetivo)
- **Acción:** Agregar licuado completo (323 calorías)
- **Nuevo Cálculo:** Calorías Restantes = Calorías Restantes - 323

### Paso 3: Verificar Balance Final
#### Si Calorías Restantes ≥ 0 (objetivo cumplido o falta más)
- **Cena Final:** Yogurt preparado (272 cal) + Licuado completo (323 cal) = 595 calorías
- **Situación:** Si aún faltan calorías (Calorías Restantes > 0), aumentar proporcionalmente el yogurt

#### Si Calorías Restantes < 0 (nos pasamos del objetivo)
- **Problema:** Yogurt + Licuado exceden las calorías disponibles
- **Solución:** Mantener licuado completo (323 cal) y ajustar yogurt proporcionalmente

### Paso 4: Ajustes Proporcionales del Yogurt

#### Cuando el Yogurt + Licuado Exceden las Calorías Disponibles:
```
Calorías para Yogurt = Calorías Disponibles - 323 (licuado)
Factor de Ajuste = Calorías para Yogurt / 272
Porción de Yogurt = 105g × Factor de Ajuste
```

#### Cuando Necesitas Más Calorías (Días de Alta Actividad):
```
Calorías Extra Necesarias = Calorías Restantes (después de yogurt + licuado)
Factor de Aumento = (272 + Calorías Extra) / 272
Porción de Yogurt = 105g × Factor de Aumento
```

### Resumen de la Secuencia:
1. **Verificar primero** si ya se excedió el objetivo (si sí, no proponer cena)
2. **Empezar** con yogurt preparado (272 cal) - ajustar si excede el objetivo
3. **Verificar** si faltan calorías para el objetivo (solo si yogurt completo no excedía)
4. **Si faltan calorías:** agregar licuado completo (323 cal)
5. **Verificar balance final:**
   - Si perfecto o falta más → mantener ambos (ajustar yogurt si falta mucho)
   - Si nos pasamos → mantener licuado, ajustar yogurt proporcionalmente

## Formato de Solicitud Esperado
```
"Dame el breakdown del día: [especificaciones de comidas y modificaciones], [actividad física realizada], dame propuestas de cena"
```

### Ejemplo:
```
"Dame el breakdown del día, desayuno estándar, comida estándar con pechuga de pollo, pero fueron 143g de brócoli. Corrí 13k para 811 calorías. Dame propuestas de cena"
```

## Proceso de Respuesta

### 1. Breakdown del Meal Específico
- **SIEMPRE mostrar** calorías y macros del meal específico del que estamos hablando
- Incluir todos los componentes de esa comida en particular

### 2. Breakdown Total del Día (HASTA ESTE PUNTO)
- **SOLO sumar** las comidas que se han confirmado como consumidas
- **NUNCA incluir** comidas futuras o no confirmadas
- Mostrar calorías totales y distribución de macronutrientes del día hasta el momento actual
- **EXCEPCIÓN:** Solo incluir cena u otras comidas si se solicita explícitamente el cálculo con esas comidas

### 3. Cálculo de Progreso hacia Déficit
- Calcular gasto calórico total (reposo + ejercicio)
- Determinar calorías objetivo (18% déficit)
- Mostrar qué porcentaje del objetivo diario se ha consumido hasta el momento
- **NO proyectar** consumo total del día a menos que se solicite

### 4. Propuesta de Cena (Solo si se solicita)
- Aplicar la secuencia lógica de ajuste
- Especificar porciones exactas si hay ajustes
- Justificar la decisión tomada

## Regla Fundamental de Breakdown
- **Breakdown del día = SOLO lo confirmado como consumido**
- **No asumir ni proyectar comidas futuras**
- **Solo calcular con cena si se solicita explícitamente**

## Notas Importantes
- **"Yogurt"** siempre se refiere al yogurt preparado completo (con todos los complementos)
- El **licuado completo** nunca se ajusta, solo se agrega o quita completamente
- Los ajustes proporcionales solo aplican al yogurt preparado
- Priorizar siempre la opción más simple que cumpla el objetivo calórico
- Si no se menciona actividad física, usar solo las calorías en reposo (1,949)
