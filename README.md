# Elementos de Transmisión en Sistemas de Control de Movimiento

## Introducción
Los sistemas de transmisión mecánica son componentes críticos en el control de movimiento, actuando como interfaz entre el motor y la carga. Estos sistemas permiten adaptar las características del motor (velocidad, torque) a los requerimientos específicos de la aplicación, ya sea para incrementar el torque reduciendo la velocidad o viceversa. En aplicaciones industriales como robots, CNC o sistemas de automatización, la selección adecuada del tipo de transmisión impacta directamente en la precisión, eficiencia energética y vida útil del sistema.

Se analiza cinco tipos principales de transmisión: engranajes, polea-correa, tornillo guía, piñón-cremallera y banda transportadora. Cada una presenta ventajas específicas según los requerimientos de carga, precisión y condiciones operativas. Por ejemplo, los engranajes ofrecen alta precisión en posicionamiento, mientras que las bandas transportadoras son ideales para mover cargas ligeras a largas distancias. El diseño óptimo considera no solo parámetros mecánicos sino también aspectos dinámicos como la inercia reflejada y el torque efectivo en el motor.

![image](https://github.com/user-attachments/assets/d390e7ab-ae9c-4de0-98d9-3a55e7d57236)

Fig 1. Sitemas de transmision.

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

### 2.1 Polea-Correa
#### 2.1.1 Configuraciones
Las transmisiones por correa pueden ser:
- **Lisas**: Para bajas cargas y alta velocidad (ej. ventiladores)
- **Dentadas**: Precisión sincrónica (ej. ejes CNC)
El documento destaca su simplicidad y capacidad para distancias entre ejes mayores que en engranajes (hasta 5m en sistemas industriales).

#### 2.1.2 Relaciones de Transmisión
La velocidad tangencial uniforme en la correa implica:
$ω_{ip}·r_{ip} = ω_{lp}·r_{lp}$
Por tanto, la relación es:
$N_{BP} = \frac{r_{lp}}{r_{ip}}$
La inercia reflejada incluye términos adicionales:
$J_{ref} = J_{ip} + \left(\frac{W_{belt}}{gη}\right)r_{ip}^2 + \frac{J_{lp} + J_{load}}{ηN_{BP}^2}$
Ejemplo: Para W_belt = 0.5Kg, r_ip = 2cm, η=95%, el término de inercia de la correa es ≈ 2.16×10⁻⁴ Kg-m².

### 2.2 Piñon cremallera
#### 2.2.1 Tipos
El documento diferencia:
- **Tornillos ACME**: Bajo costo pero alta fricción (η ≈ 35-85%)
- **Tornillos de bolas**: Alta eficiencia (85-95%) y vida útil (>20,000h en aplicaciones CNC)

#### 2.2.2 Parámetros Clave
El paso (p) define la relación lineal-angular:
$N_S = 2πp \quad \text{[rad/m]}$
Ejemplo con p = 0.75cm/rev → N_S ≈ 838 rad/m. La inercia reflejada para m = 50Kg es:
$J_{ref} = \frac{50}{838^2} ≈ 7.12×10⁻⁵ \text{Kg-m²}$
El torque motor considera fuerzas externas:
$T_m = \frac{F_{ext}}{ηN_S} + J_{total}\ddotθ$
donde F_ext incluye fricción (μ(W_L+W_C)cosβ) y componente gravitacional ((W_L+W_C)sinβ).

### 2.3 Piñón-Cremallera
#### 2.3.1 Aplicaciones
Ideal para:
- Mesas de posicionamiento lineal (precisión ±0.1mm)
- Sistemas de transporte pesado (ej. grúas puente)

#### 2.3.2 Ecuaciones
La relación depende del radio del piñón:
$N_{RP} = \frac{1}{r_{piñón}}$

Para r = 25mm → N_RP = 40 m⁻¹. El torque motor es:

$T_{load→in} = \frac{F_{ext}}{ηN_{RP}}$

Ejemplo: F_ext = 100N con η=85% requiere T_m ≈ 2.94Nm.

### 2.4 Banda Transportadora
#### 2.4.1 Configuraciones
El documento analiza:
- **Bandas planas**: Para cargas uniformes (ej. packaging)
- **Con rodillos locos**: Reducen fricción en largas distancias

#### 2.4.2 Inercia Reflejada
Incluye múltiples componentes:
$J_{ref} = 2J_p + \frac{1}{ηN_{BD}^2}\left(\frac{W_L + W_C + W_{belt}}{g}\right)$
Para W_belt = 2Kg, W_L = 10Kg, r_ip = 5cm (N_BD=20 m⁻¹), η=90%:
$J_{ref} ≈ 2(1×10⁻⁴) + \frac{12}{0.9×400} ≈ 3.33×10⁻² \text{Kg-m²}$

---

## 3. Diseño de Sistemas de Transmisión (Ampliado)

### 3.1 Proceso de Diseño Detallado
El diseño óptimo de transmisiones mecánicas requiere un enfoque sistémico que considere tanto parámetros estáticos como dinámicos. Según el documento original, este proceso consta de 5 etapas críticas:

1. **Definición de Requerimientos**:
   - Perfil de movimiento (velocidad, aceleración)
   - Precisión posicional (backlash permitido)
   - Ciclo de trabajo (continuo/intermitente)
   - Condiciones ambientales (temperatura, contaminantes)

2. **Selección del Tipo de Transmisión**:
   | Criterio          | Engranajes | Polea-Correa | Tornillo Guía | Piñón-Cremallera |
   |-------------------|------------|--------------|---------------|------------------|
   | Precisión         | Alta       | Media        | Muy Alta      | Alta             |
   | Distancia entre ejes | Corta    | Larga        | N/A           | Media            |
   | Eficiencia        | 90-98%     | 85-95%       | 35-95%        | 80-90%           |
   | Mantenimiento     | Medio      | Bajo         | Alto          | Medio            |

3. **Cálculo de Parámetros Dinámicos**:
   - Inercia total reflejada al motor
   - Torque máximo requerido
   - Frecuencia natural del sistema

4. **Verificación de Especificaciones**:
   - Margen de seguridad ≥ 20%
   - Relación de inercia J_R ≤ 5
   - Límites térmicos del motor

5. **Validación por Simulación**:
   - Análisis modal
   - Respuesta transitoria
   - Efectos de backlash

### 3.2 Consideraciones Avanzadas
El documento destaca tres aspectos frecuentemente subestimados:

**A. Efecto de la Rigidez Torsional**:
En sistemas de alta precisión, la rigidez del conjunto (K) afecta directamente el error posicional:

$θ_{error} = \frac{T_{load}}{K_{sistema}}$

Donde:

- $K_sistema = 1/(Σ(1/K_i))$ para elementos en serie
- Valores típicos: 100-1000 Nm/rad para engranajes industriales

**B. Pérdidas por Fricción No Lineal**:
Las pérdidas totales incluyen:
- Fricción viscosa (proporcional a velocidad)
- Fricción de Coulomb (constante)
- Fricción estática (stiction)

Modelo completo:

$T_{fricción} = T_c + (T_{st} - T_c)e^{-(ω/ω_s)^2} + Bω$

**C. Optimización Térmica**:
Para sistemas continuos, la temperatura de equilibrio se calcula como:

$T_{eq} = T_{amb} + \frac{P_{pérdidas}}{hA}$

Donde:
- h = coeficiente de transferencia térmica (5-25 W/m²K)
- A = área superficial efectiva

### 3.3 Ejemplo Aplicado
**Sistema de Posicionamiento Lineal**:
- Requerimientos:
  - Carga: 50 kg
  - Carrera: 1 m
  - Tiempo de posicionamiento: 2 s
  - Precisión: ±0.1 mm

**Solución Propuesta**:
1. **Transmisión Seleccionada**: Tornillo de bolas (η=90%, p=10 mm/rev)
2. **Cálculos**:

   - Relación de transmisión:
   
     $N_S = \frac{2π}{0.01} = 628\ rad/m$
     
   - Inercia reflejada:

     $J_{ref} = \frac{50}{628^2} = 1.27×10^{-4}\ kg·m²$

   - Torque para aceleración (a=2 m/s²):

     $T_m = \frac{50×2}{0.9×628} + 1.27×10^{-4}×314 = 0.177 + 0.040 = 0.217\ Nm$
     
4. **Motor Seleccionado**:
   - J_motor = 4×10⁻⁵ kg·m²
   - J_R = (1.27×10⁻⁴)/(4×10⁻⁵) = 3.18 (cumple J_R ≤ 5)
   - Torque continuo ≥ 0.26 Nm (20% margen)

**Resultados de Simulación**:
- Error posicional máximo: 0.08 mm
- Temperatura de equilibrio: 45°C (amb=25°C)
- Vida útil estimada: >20,000 horas

---

## 4. Ejercicios Resueltos y Explicados

### 4.1 Ejercicios de Engranajes

**Contexto**:  
Los sistemas con engranajes son fundamentales cuando se requiere alta precisión en la relación de transmisión. Estos ejercicios aplican los conceptos de inercia reflejada y torque equivalente usando los datos del fabricante Apex Dynamics mencionados en las diapositivas 20-21.

**Ejercicio 1**:  
Calcule la inercia total reflejada al motor para un sistema con:
- Motor: Inercia rotor = 2.5×10⁻⁵ kg·m² (similar al QB02301 de Allied Motion)
- Engranaje: Relación 8:1, inercia reflejada a entrada = 0.2 kg·cm², η = 95%
- Carga: J_load = 15×10⁻⁴ kg·m²

**Solución**:
```math
\begin{aligned}
&1.\ \text{Convertir inercia del engranaje:} \\
&\quad J_{GB} = 0.2\ \text{kg·cm}^2 = 2×10^{-5}\ \text{kg·m}^2 \\
&2.\ \text{Calcular inercia reflejada de la carga:} \\
&\quad J_{ref} = \frac{15×10^{-4}}{0.95 × 8^2} = 2.47×10^{-5}\ \text{kg·m}^2 \\
&3.\ \text{Inercia total:} \\
&\quad J_{total} = 2.5×10^{-5} + 2×10^{-5} + 2.47×10^{-5} = 6.97×10^{-5}\ \text{kg·m}^2
\end{aligned}
```

### 4.2 Ejercicio Selección de Motor
 
**Enunciado:**

Una carga requiere un torque de 12 Nm a 100 rpm. La transmisión tiene una relación \( N_{\text{GB}} = 3 \) y eficiencia \( \eta = 0.9 \). Determine el torque mínimo requerido en el motor.

**Solución:**

$T_m = \frac{T_{\text{load}}}{\eta \cdot N_{\text{GB}}} = \frac{12}{0.9 \times 3} \approx 4.44 \, \text{Nm}$

**Consideraciones adicionales:**

- **Margen de seguridad:** Si se aplica un 20% adicional:  

  $T_{\text{motor}} \geq 4.44 \times 1.2 \approx 5.33 \, \text{Nm}$
  
- **Potencia requerida:**  

  $P = T_m \cdot \omega = 4.44 \times \left(\frac{100 \times 2\pi}{60}\right) \approx 46.5 \, \text{W}$

---

### 4.3 Ejercicio Cálculo de Torque y Potencia del Motor

### Enunciado:

Un sistema de elevación requiere un torque de 18 Nm a 150 rpm en el eje de salida. La transmisión tiene una relación de reducción (N) = 4 y una eficiencia (η) = 0.85. Determine:

1. El torque mínimo requerido en el motor
2. La potencia requerida por el motor
3. El torque con un margen de seguridad del 25%

### Solución:

### 1. Torque mínimo en el motor

$T_{motor} = \frac{T_{salida}}{\eta \times N} = \frac{18}{0.85 \times 4}$

$T_{motor} = \frac{18}{3.4} \approx 5.29 \, \text{Nm}$

### 2. Potencia requerida

Primero calculamos la velocidad angular del motor (ω):

$omega_{motor} = \omega_{salida} \times N = \left( \frac{150 \times 2\pi}{60} \right) \times 4$

$omega_{motor} = 15.708 \times 4 = 62.832 \, \text{rad/s}$

Ahora calculamos la potencia:

$P = T_{motor} \times \omega_{motor} = 5.29 \times 62.832 \approx 332.4 \, \text{W}$

### 3. Torque con margen de seguridad

$T_{seguridad} = T_{motor} \times 1.25 = 5.29 \times 1.25 \approx 6.61 \, \text{Nm}$

### Consideraciones adicionales:

- La eficiencia de la transmisión afecta directamente el torque requerido

- El margen de seguridad es recomendable para cubrir picos de carga

- La potencia calculada es la mínima teórica, en la práctica se debe seleccionar un motor con mayor capacidad

---


## 5. Simulación y Modelado (Profundización)

### 5.3 Modelado de Pérdidas
En Simscape, configurar:
```matlab
% Ejemplo engranajes con pérdidas
gear = simscape.multibody.Gear('Efficiency', 0.95, 'MeshStiffness', 1e8);
```

## 6. Conclusiones 

- El diseño adecuado de transmisiones constituye un pilar fundamental en ingeniería mecatrónica, ya que impacta directamente en tres aspectos clave: la precisión micrométrica requerida en aplicaciones CNC, la eficiencia energética que determina costos operativos a largo plazo, y la robustez necesaria para entornos industriales exigentes. Un sistema bien diseñado puede marcar la diferencia entre una operación confiable y fallos costosos.

-  Más allá de los parámetros básicos, la inercia reflejada afecta la capacidad de respuesta en cambios de velocidad bruscos, mientras que el torque dinámico debe calcularse considerando los picos de aceleración en perfiles S-curve. La eficiencia mecánica, frecuentemente subestimada, puede generar pérdidas acumulativas significativas en sistemas que operan continuamente.

- La especificación del torque motor debe incluir un análisis exhaustivo que contemple no solo la fricción estática inicial, sino también los requerimientos dinámicos durante cambios de velocidad, con márgenes de seguridad que varían desde el 20% para aplicaciones estables hasta el 50% en entornos con cargas impredecibles o ciclos de trabajo intensivos.

- La inercia equivalente, como parámetro dinámico clave, influye directamente en la constante de tiempo del sistema. Su minimización estratégica mediante selección de materiales y relaciones de transmisión adecuadas puede mejorar hasta en un 40% los tiempos de posicionamiento en aplicaciones de alta velocidad.

- El proceso de diseño completo exige la definición precisa de perfiles de movimiento, donde la elección entre trapezoidal y S-curve afecta tanto el desgaste mecánico como el consumo energético. La selección de motores debe basarse en análisis de torque RMS para operación continua y torque pico para condiciones transitorias.

- La validación de sistemas existentes requiere simulaciones multifísicas que identifiquen no solo resonancias mecánicas, sino también patrones de distribución térmica que podrían limitar la vida útil de los componentes. El análisis de márgenes de seguridad debe considerar escenarios de fallo múltiple.

- La variabilidad en eficiencia entre distintos tipos de transmisión (desde el 30% en sistemas de tornillo sinfín hasta 98% en engranajes planetarios de precisión) tiene implicaciones directas en el dimensionamiento de fuentes de alimentación y sistemas de refrigeración, con impacto económico significativo en operación continua.

## 7. Referencias Bibliográficas  

## Referencias

1. **Vallery, H. & van Dijk, J.** (2020). *Control of Motion Systems*. Elsevier.  *Capítulos 4 y 5*: Modelado dinámico y selección de actuadores.

2. **Beards, C.** (1996). *Dynamics of Mechanical Systems*. CRC Press.  *Sección 8.3*: Inercia equivalente en sistemas rotacionales.

3. **MathWorks** (2023). *Documentación de Simscape Multibody*.  *Tutoriales*: "Modelado de transmisiones mecánicas".

4. **Apex Dynamics** (2023). *Catálogo de Engranajes*.  *Tablas de eficiencia y curvas de vida útil* para engranajes planetarios.

5. **Bolton, W.** (2015). *Mechatronics: Electronic Control Systems in Mechanical and Electrical Engineering* (6th ed.). Pearson Education.

6. **Groover, M. P.** (2016). *Automation, Production Systems, and Computer-Integrated Manufacturing* (4th ed.). Pearson.

7. **Norton, R. L.** (2013). *Diseño de maquinaria: Una introducción a la síntesis y análisis de mecanismos y máquinas* (4ta ed.). McGraw-Hill.

8. **Juvinall, R. C., & Marshek, K. M.** (2011). *Fundamentals of Machine Component Design* (5th ed.). Wiley.

9. **Moran, C.** (2012). *Elementos de máquinas*. Alfaomega Grupo Editor. 


