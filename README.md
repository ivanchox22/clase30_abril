# Elementos de Transmisión en Sistemas de Control de Movimiento

## Introducción
Los sistemas de transmisión mecánica son componentes críticos en el control de movimiento, actuando como interfaz entre el motor y la carga. Estos sistemas permiten adaptar las características del motor (velocidad, torque) a los requerimientos específicos de la aplicación, ya sea para incrementar el torque reduciendo la velocidad o viceversa. En aplicaciones industriales como robots, CNC o sistemas de automatización, la selección adecuada del tipo de transmisión impacta directamente en la precisión, eficiencia energética y vida útil del sistema.

El documento analiza cinco tipos principales de transmisión: engranajes, polea-correa, tornillo guía, piñón-cremallera y banda transportadora. Cada una presenta ventajas específicas según los requerimientos de carga, precisión y condiciones operativas. Por ejemplo, los engranajes ofrecen alta precisión en posicionamiento, mientras que las bandas transportadoras son ideales para mover cargas ligeras a largas distancias. El diseño óptimo considera no solo parámetros mecánicos sino también aspectos dinámicos como la inercia reflejada y el torque efectivo en el motor.

---

## 1. Fundamentos de Transmisión Mecánica

### 1.1 Conceptos Básicos
🔑 *Transmisión mecánica*: Sistema que adapta el movimiento y potencia del motor a los requerimientos de la carga mediante elementos intermedios. Estos sistemas transforman características cinemáticas (velocidad angular) y dinámicas (torque) según relaciones matemáticas precisas.

🔑 *Relación de transmisión (N)*: Factor que relaciona las velocidades de entrada y salida del sistema. En engranajes, depende del número de dientes (N = N_l/N_m); en poleas, de los radios (N = r_l/r_p). Valores N > 1 indican reducción de velocidad (aumento de torque), mientras N < 1 implican multiplicación de velocidad.

### 1.2 Parámetros Clave
- **Inercia (J)**: Resistencia al cambio de velocidad angular, análoga rotacional a la masa en sistemas lineales. En el documento se destaca su importancia en sistemas con aceleraciones rápidas (ej. robots delta), donde altas inercias reflejadas requieren motores más potentes.
- **Torque (T)**: Fuerza rotacional aplicada, relacionada con la potencia mediante P = T·ω. El torque reflejado (T_m = T_l/(ηN)) determina la capacidad mínima del motor.
- **Eficiencia (η)**: Relación potencia útil/potencia consumida (η = P_out/P_in). Sistemas con pérdidas por fricción (ej. tornillos ACME con η ≈ 35-85%) requieren mayor torque motor para compensar.

---

## 2. Tipos de Transmisiones

### 2.1 Engranajes
#### 2.1.1 Características
Los engranajes son elementos dentados que transmiten movimiento circular entre ejes paralelos o perpendiculares. Ofrecen alta precisión (backlash < 1 arcmin en sistemas premium) y capacidad de carga (hasta 500 Nm en cajas industriales). Según el documento, su diseño debe considerar:
- **Relación de inercia (J_R)**: Idealmente ≤ 5 para evitar sobredimensionamiento (ejemplo calculado: J_R = 3.75 para engranaje 5:1 con J_load = 10×10⁻⁴ Kg-m²).
- **Pérdidas por eficiencia**: Típicamente η = 90-98% por fricción entre dientes.

#### 2.1.2 Ecuaciones Fundamentales
La inercia reflejada en engranajes sigue:
$$
J_{ref} = \frac{J_{load}}{ηN_{GB}^2}
$$
Ejemplo del documento: Para N = 5 y η = 97%, una carga de 10×10⁻⁴ Kg-m² refleja 4.124×10⁻⁵ Kg-m² al motor. El torque motor se calcula como:
$$
T_m = \frac{T_l}{ηN_{GB}} + J_{total}\ddotθ
$$
donde J_total incluye inercias del motor, acople y engranajes.

### 2.2 Polea-Correa
#### 2.2.1 Configuraciones
Las transmisiones por correa pueden ser:
- **Lisas**: Para bajas cargas y alta velocidad (ej. ventiladores)
- **Dentadas**: Precisión sincrónica (ej. ejes CNC)
El documento destaca su simplicidad y capacidad para distancias entre ejes mayores que en engranajes (hasta 5m en sistemas industriales).

#### 2.2.2 Relaciones de Transmisión
La velocidad tangencial uniforme en la correa implica:
$$
ω_{ip}·r_{ip} = ω_{lp}·r_{lp}
$$
Por tanto, la relación es:
$$
N_{BP} = \frac{r_{lp}}{r_{ip}}
$$
La inercia reflejada incluye términos adicionales:
$$
J_{ref} = J_{ip} + \left(\frac{W_{belt}}{gη}\right)r_{ip}^2 + \frac{J_{lp} + J_{load}}{ηN_{BP}^2}
$$
Ejemplo: Para W_belt = 0.5Kg, r_ip = 2cm, η=95%, el término de inercia de la correa es ≈ 2.16×10⁻⁴ Kg-m².

### 2.3 Tornillo Guía
#### 2.3.1 Tipos
El documento diferencia:
- **Tornillos ACME**: Bajo costo pero alta fricción (η ≈ 35-85%)
- **Tornillos de bolas**: Alta eficiencia (85-95%) y vida útil (>20,000h en aplicaciones CNC)

#### 2.3.2 Parámetros Clave
El paso (p) define la relación lineal-angular:
$$
N_S = 2πp \quad \text{[rad/m]}
$$
Ejemplo con p = 0.75cm/rev → N_S ≈ 838 rad/m. La inercia reflejada para m = 50Kg es:
$$
J_{ref} = \frac{50}{838^2} ≈ 7.12×10⁻⁵ \text{Kg-m²}
$$
El torque motor considera fuerzas externas:
$$
T_m = \frac{F_{ext}}{ηN_S} + J_{total}\ddotθ
$$
donde F_ext incluye fricción (μ(W_L+W_C)cosβ) y componente gravitacional ((W_L+W_C)sinβ).

### 2.4 Piñón-Cremallera
#### 2.4.1 Aplicaciones
Ideal para:
- Mesas de posicionamiento lineal (precisión ±0.1mm)
- Sistemas de transporte pesado (ej. grúas puente)

#### 2.4.2 Ecuaciones
La relación depende del radio del piñón:
$$
N_{RP} = \frac{1}{r_{piñón}}
$$
Para r = 25mm → N_RP = 40 m⁻¹. El torque motor es:
$$
T_{load→in} = \frac{F_{ext}}{ηN_{RP}}
$$
Ejemplo: F_ext = 100N con η=85% requiere T_m ≈ 2.94Nm.

### 2.5 Banda Transportadora
#### 2.5.1 Configuraciones
El documento analiza:
- **Bandas planas**: Para cargas uniformes (ej. packaging)
- **Con rodillos locos**: Reducen fricción en largas distancias

#### 2.5.2 Inercia Reflejada
Incluye múltiples componentes:
$$
J_{ref} = 2J_p + \frac{1}{ηN_{BD}^2}\left(\frac{W_L + W_C + W_{belt}}{g}\right)
$$
Para W_belt = 2Kg, W_L = 10Kg, r_ip = 5cm (N_BD=20 m⁻¹), η=90%:
$$
J_{ref} ≈ 2(1×10⁻⁴) + \frac{12}{0.9×400} ≈ 3.33×10⁻² \text{Kg-m²}
$$

---

## 3. Diseño de Sistemas de Transmisión (Continuación)

### 3.3 Criterios de Selección
El documento enfatiza tres aspectos clave:
1. **Relación de inercia (J_R)**: Mantener J_R ≤ 5 para equilibrio entre rendimiento y costo. Valores altos (>10) generan:
   - Respuesta lenta a cambios de velocidad
   - Sobrecalentamiento del motor
2. **Margen de seguridad**: Añadir 20-30% al torque calculado para cubrir perturbaciones.
3. **Pérdidas por fricción**: En sistemas multi-etapa (ej. engranaje + tornillo), multiplicar eficiencias (η_total = η₁·η₂).

Ejemplo práctico: Un sistema con η₁=95% (engranajes) y η₂=85% (tornillo) tiene η_total ≈ 80.75%.

### 3.4 Validación por Simulación
El documento muestra ejemplos en Simscape Multibody para:
- **Engranajes**: Análisis de vibraciones y backlash
- **Tornillos guía**: Efecto del paso (p) en la velocidad lineal
- **Poleas**: Tensión óptima de correas

Resultados clave:
- Error de posicionamiento en piñón-cremallera: <0.5% con r=25mm
- Tiempo de estabilización en tornillo de bolas: ≈50ms para paso 5mm/rev

---

## 4. Ejemplos y Aplicaciones (Ampliación)

### 4.3 Ejemplo 3: Banda Transportadora
**Enunciado**: Sistema con W_L=15Kg, W_belt=3Kg, r_DR=4cm (N_CV=25 m⁻¹), η=88%. Calcular J_ref si J_DR=5×10⁻⁴ Kg-m².

**Solución**:
$$
J_{ref} = 5×10⁻⁴ + \frac{18}{0.88×625} ≈ 3.37×10⁻² \text{Kg-m²}
$$

### 4.4 Ejemplo 4: Tornillo Guía Horizontal
**Enunciado**: Tornillo ACME (p=10mm/rev, η=40%) moviendo m=80Kg con μ=0.2. Calcular T_m para a=0.5m/s².

**Solución**:
$$
F_{ext} = μmg + ma = 0.2×80×9.81 + 80×0.5 ≈ 196.96N
$$
$$
N_S = 2π/0.01 ≈ 628 \text{rad/m}
$$
$$
T_m = \frac{196.96}{0.4×628} + \frac{80}{628^2}×314 ≈ 0.78 + 0.064 ≈ 0.844Nm
$$

---

## 5. Simulación y Modelado (Profundización)

### 5.3 Modelado de Pérdidas
En Simscape, configurar:
```matlab
% Ejemplo engranajes con pérdidas
gear = simscape.multibody.Gear('Efficiency', 0.95, 'MeshStiffness', 1e8);
