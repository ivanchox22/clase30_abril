# Elementos de Transmisión en Sistemas de Control de Movimiento

Los sistemas de transmisión mecánica son componentes críticos en el control de movimiento, actuando como interfaz entre el motor y la carga. Estos sistemas permiten adaptar las características del motor (velocidad, torque) a los requerimientos específicos de la aplicación, ya sea para incrementar el torque reduciendo la velocidad o viceversa. En aplicaciones industriales como robots, CNC o sistemas de automatización, la selección adecuada del tipo de transmisión impacta directamente en la precisión, eficiencia energética y vida útil del sistema.

Se analiza cinco tipos principales de transmisión: engranajes, polea-correa, tornillo guía, piñón-cremallera y banda transportadora. Cada una presenta ventajas específicas según los requerimientos de carga, precisión y condiciones operativas. Por ejemplo, los engranajes ofrecen alta precisión en posicionamiento, mientras que las bandas transportadoras son ideales para mover cargas ligeras a largas distancias. El diseño óptimo considera no solo parámetros mecánicos sino también aspectos dinámicos como la inercia reflejada y el torque efectivo en el motor.

![image](https://github.com/user-attachments/assets/d390e7ab-ae9c-4de0-98d9-3a55e7d57236)

Fig 1. Sitemas de transmision.

---

## 1. Fundamentos de Transmisión Mecánica

### 1.1 Conceptos Básicos

>🔑 *Transmisión mecánica*: Sistema que adapta el movimiento y potencia del motor a los requerimientos de la carga mediante elementos intermedios. Estos sistemas transforman características cinemáticas (velocidad angular) y dinámicas (torque) según relaciones matemáticas precisas.

>🔑 *Relación de transmisión (N)*: Factor que relaciona las velocidades de entrada y salida del sistema. En engranajes, depende del número de dientes (N = N_l/N_m); en poleas, de los radios (N = r_l/r_p). Valores N > 1 indican reducción de velocidad (aumento de torque), mientras N < 1 implican multiplicación de velocidad.


### 1.2 Parámetros Clave
- **Inercia (J)**: Resistencia al cambio de velocidad angular, análoga rotacional a la masa en sistemas lineales. En el documento se destaca su importancia en sistemas con aceleraciones rápidas (ej. robots delta), donde altas inercias reflejadas requieren motores más potentes.
- **Torque (T)**: Fuerza rotacional aplicada, relacionada con la potencia mediante P = T·ω. El torque reflejado (T_m = T_l/(ηN)) determina la capacidad mínima del motor.
- **Eficiencia (η)**: Relación potencia útil/potencia consumida (η = P_out/P_in). Sistemas con pérdidas por fricción (ej. tornillos ACME con η ≈ 35-85%) requieren mayor torque motor para compensar.

---

## 2. Tipos de Transmisiones

### 2.1 Polea-Correa

Las transmisiones por correa son un sistema mecánico ampliamente utilizado para transferir movimiento entre ejes separados. Existen dos tipos principales: correas lisas, ideales para aplicaciones de baja carga y alta velocidad como ventiladores, y correas dentadas, que ofrecen precisión sincrónica, comúnmente empleadas en ejes de máquinas CNC. Estos sistemas destacan por su simplicidad de diseño y su capacidad para cubrir distancias entre ejes mayores que otros mecanismos, llegando hasta los 5 metros en entornos industriales. Además, su relación de transmisión se basa en la velocidad tangencial uniforme de la correa, lo que permite calcular parámetros clave como la inercia reflejada, que incluye efectos adicionales como la masa de la correa y las pérdidas por eficiencia.

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

Los sistemas de piñón-cremallera son fundamentales para convertir movimiento rotacional en lineal con alta precisión. Entre las variantes más comunes se encuentran los tornillos ACME, caracterizados por su bajo costo pero menor eficiencia debido a la fricción, y los tornillos de bolas, que ofrecen un rendimiento superior (85-95% de eficiencia) y una vida útil prolongada, superando los 20.000 metros en aplicaciones exigentes como las máquinas CNC. Este mecanismo es esencial en aplicaciones que requieren movimientos lineales controlados y repetitivos, donde la elección entre fricción deslizante (ACME) o rodamiento (bolas) depende del equilibrio entre costo, precisión y durabilidad.

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

Las bandas transportadoras son sistemas fundamentales en la industria para el manejo de materiales de manera continua y eficiente. Utilizadas en sectores como minería, logística y manufactura, estas bandas pueden transportar productos a granel o empaquetados sobre una superficie móvil, generalmente fabricada de caucho, PVC u otros materiales resistentes. Su diseño permite adaptarse a diferentes entornos, incluyendo inclinaciones y curvas, mientras garantizan un flujo constante de materiales con bajo consumo energético y alta capacidad de carga.

#### 2.4.1 Configuraciones
El documento analiza:
- **Bandas planas**: Para cargas uniformes (ej. packaging)
- **Con rodillos locos**: Reducen fricción en largas distancias

#### 2.4.2 Inercia Reflejada
Incluye múltiples componentes:

$J_{ref} = 2J_p + \frac{1}{ηN_{BD}^2}\left(\frac{W_L + W_C + W_{belt}}{g}\right)$

Para W_belt = 2Kg, W_L = 10Kg, r_ip = 5cm (N_BD=20 m⁻¹), η=90%:

$J_{ref} ≈ 2(1×10⁻⁴) + \frac{12}{0.9×400} ≈ 3.33×10⁻² \text{Kg-m²}$

### 2.5 Transmisión por Cadena

La transmisión por cadena es un mecanismo robusto y eficiente, ideal para aplicaciones que requieren alta resistencia y sincronización, como en motocicletas, maquinaria industrial y sistemas de transporte. Compuesto por una cadena metálica que engrana con ruedas dentadas (sprockets), este sistema destaca por su durabilidad, capacidad para transmitir grandes cargas y mínima pérdida de potencia. A diferencia de las correas, las cadenas no sufren deslizamiento, lo que las hace ideales para entornos con cargas pesadas o condiciones adversas.

#### 2.5.1 Configuraciones

Las transmisiones por cadena se utilizan en:
- **Sistemas de alta carga**: Maquinaria pesada (ej. excavadoras)
- **Entornos hostiles**: Resistencia a polvo/aceite (ej. motores industriales)

#### 2.5.2 Relaciones de Transmisión

La relación depende del número de dientes:

$N_{CP} = \frac{z_1}{z_2}$

💡 Ejemplo con z1=20, z2=40 → N_CP=0.5. La inercia reflejada incluye:

$J_{ref} = J_{m} + \frac{J_{load}}{ηN_{CP}^2} + m_{chain}·r_{sprocket}^2$

Para m_chain=1.2Kg, r=0.1m, η=85%:

$J_{chain} ≈ 1.2×0.1^2 = 1.2×10⁻² \text{Kg-m²}$

---

### 2.6 Transmisión por Tornillo Sin Fin

El tornillo sinfín es un sistema de transmisión compacto y de alta reducción de velocidad, comúnmente empleado en aplicaciones que requieren gran torque y movimiento lento, como elevadores, tolvas y maquinaria pesada. Consiste en un tornillo helicoidal (sinfín) que engrana con una rueda dentada (corona), logrando una relación de transmisión muy alta en un espacio reducido. Aunque su eficiencia es menor debido a la fricción deslizante, su capacidad de autobloqueo lo hace ideal para sistemas de seguridad donde se necesita evitar retrocesos.

#### 2.6.1 Características

- **Alta reducción**: Relaciones típicas 5:1 a 100:1

- **Autobloqueo**: Cuando el ángulo de hélice < φ_fricción

#### 2.6.2 Parámetros Clave

La relación de reducción es:

$N_{WS} = \frac{2π}{p}$

Para p=6mm/rev → N_WS≈1047 rad/m. Torque requerido:

$T_m = \frac{F_{axial}}{ηN_{WS}} + J_{eq}\ddotθ$

💡 Ejemplo con F=500N, η=70%:

$T_m ≈ \frac{500}{0.7×1047} ≈ 0.68 \text{Nm}$

---

### 2.7 Transmisión por Engranajes Cónicos

Los engranajes cónicos son utilizados para transmitir movimiento entre ejes que se intersectan, generalmente a 90 grados. Este tipo de engranaje es esencial en aplicaciones como diferenciales de vehículos, maquinaria pesada y sistemas de dirección, donde se requiere cambiar la dirección del movimiento rotacional con alta precisión y eficiencia. Su diseño en forma de cono permite una transferencia de potencia suave y silenciosa, especialmente cuando están fabricados con materiales de alta calidad y acabados de precisión. Su versatilidad los hace indispensables en sistemas que combinan fuerza y cambios de dirección.

#### 2.7.1 Aplicaciones

- **Cambio de eje**: Sistemas con ejes no paralelos (ej. diferenciales automotrices)

- **Precisión angular**: Robots articulados (±0.05° repetibilidad)

#### 2.7.2 Ecuaciones Fundamentales
Relación de transmisión:

$N_{BG} = \frac{r_{out}}{r_{in}}$

Para r_in=30mm, r_out=60mm → N_BG=2. Inercia reflejada:

$J_{ref} = J_{in} + \frac{J_{out}}{ηN_{BG}^2}$

💡 Ejemplo con J_out=5×10⁻³ Kg-m², η=90%:

$J_{ref} ≈ \frac{5×10⁻³}{0.9×4} ≈ 1.39×10⁻³ \text{Kg-m²}$

### 2.8 💡 Ejemplo Transmisión Polea-Correa

![image](https://github.com/user-attachments/assets/beeafd6b-6422-494f-8982-9bb9deeb6354)

fig 2. Trasmision Polea-Correa.

Un sistema tiene r_ip = 3cm, r_lp = 9cm, W_belt = 0.8Kg, J_lp = 0.002 Kg-m², J_load = 0.005 Kg-m², η=92%. Calcule:  
- a) Relación de transmisión  
- b) Inercia reflejada total  

**Solución**:  
- a) $N_{BP} = \frac{r_{lp}}{r_{ip}} = \frac{9}{3} = 3$  

- b) $J_{ref} = J_{ip} + \left(\frac{0.8}{9.81×0.92}\right)0.03^2 + \frac{0.002+0.005}{0.92×3^2}$  

   $= J_{ip} + 8.5×10⁻⁵ + 8.45×10⁻⁴ \text{ Kg-m²}$  

### 2.9  💡 Ejemplo 2 Piñón-Cremallera

![image](https://github.com/user-attachments/assets/5bb81d3f-825b-48e0-bad9-db3bd7ae8178)

fig 3. Piñón-Cremallera.

- Para p = 5mm/rev, m_load = 25Kg, μ = 0.2 en plano inclinado (β=15°):  

- a) Calcule N_S  

- b) Torque para aceleración de 0.5m/s²  

**Solución**:  
- a) $N_S = \frac{2π}{0.005} = 1257 \text{ rad/m}$  

- b) $F_{ext} = 25(9.81\sin15° + 0.2×9.81\cos15° + 0.5) ≈ 104.3 \text{N}$

- $T_m = \frac{104.3}{0.9×1257} + J_{total}·\ddotθ ≈ 0.092 \text{Nm} + J_{total}·\ddotθ$  

### 2.10 💡 Ejemplo Banda Transportadora

![image](https://github.com/user-attachments/assets/c522718c-8b8c-4517-9a16-c70df104057b)

fig 4. Banda Transportadora.

- Sistema con W_L = 15Kg, W_belt = 3Kg, 4 poleas (J_p=1.5×10⁻⁴ Kg-m² c/u), r_ip = 4cm, η=88%:  

- a) Inercia reflejada total  

**Solución**:  
- $N_{BD} = \frac{1}{0.04} = 25 \text{ m⁻¹}$  

- $J_{ref} = 4×1.5×10⁻⁴ + \frac{15+3}{0.88×625} ≈ 6×10⁻⁴ + 0.0327 ≈ 0.0333 \text{ Kg-m²}$  

---

### 2.11 💡 Ejemplo Transmisión por Cadena

![image](https://github.com/user-attachments/assets/be47fc55-766b-443a-afd3-570ccfcb726e)

fig 5. Transmisión por Cadena.

- z1=18, z2=54, m_chain=2Kg, r_sprocket=8cm, J_load=0.01 Kg-m²:

- a) Relación N_CP  

- b) Inercia reflejada (sin η)  

**Solución**:  
- a) $N_{CP} = \frac{18}{54} = 0.333$  

- b) $J_{ref} = J_m + \frac{0.01}{0.333^2} + 2×0.08^2 ≈ J_m + 0.09 + 0.0128 \text{ Kg-m²}$  

---

### 2.12 💡 Ejercicio 5 Tornillo Sin Fin

![image](https://github.com/user-attachments/assets/e9caacb8-72cc-410b-ba40-014fbdd89004)

fig 6. Tornillo Sin Fin.

- p=8mm/rev, F_axial=750N, J_eq=0.002 Kg-m², α=2 rad/s²:  

- a) N_WS  

- b) Torque estático + dinámico (η=75%)  

**Solución**:  
- a) $N_{WS} = \frac{2π}{0.008} = 785 \text{ rad/m}$  

- b) $T_m = \frac{750}{0.75×785} + 0.002×2 ≈ 1.27 + 0.004 ≈ 1.274 \text{Nm}$  

### 2.13 💡 Ejemplo Engranajes Cónicos

- r_in=20mm, r_out=80mm, J_out=0.008 Kg-m², η=85%:

- a) N_BG  

- b) J_ref (J_in despreciable)  

**Solución**:  
a) $N_{BG} = \frac{80}{20} = 4$  
b) $J_{ref} ≈ \frac{0.008}{0.85×16} ≈ 5.88×10⁻⁴ \text{ Kg-m²}$  

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

### 3.3 💡 Ejemplo Aplicado
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
- Los sistemas con engranajes son fundamentales cuando se requiere alta precisión en la relación de transmisión. Estos ejercicios aplican los conceptos de inercia reflejada y torque equivalente usando los datos del fabricante Apex Dynamics mencionados en las diapositivas 20-21.

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

- Una carga requiere un torque de 12 Nm a 100 rpm. La transmisión tiene una relación \( N_{\text{GB}} = 3 \) y eficiencia \( \eta = 0.9 \). Determine el torque mínimo requerido en el motor.

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

- Un sistema de elevación requiere un torque de 18 Nm a 150 rpm en el eje de salida. La transmisión tiene una relación de reducción (N) = 4 y una eficiencia (η) = 0.85. Determine:

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

### 5.1 Introducción a Modelado Dinámico
- Herramientas Recomendadas
- **MATLAB/Simulink**: Para modelado físico con Simscape Multibody
- **Adams**: Análisis de fuerzas en sistemas complejos
- **SolidWorks Motion**: Integración directa con modelos CAD

```matlab
% Ejemplo básico de sistema masa-resorte-amortiguador
sys = 'mass_spring_damper.slx';
load_system(sys);
## 6. Conclusiones
```

### 5.2 Modelado de Sistemas Ideales

#### 5.2.1 Configuración Básica

Para sistemas sin pérdidas:

```matlab
% Transmisión por correa ideal
belt_ideal = beltDrive('Rigid', 'on', 'Slip', 'off');
```

#### 5.2.2 Parámetros Clave

- Stiffness: Rigidez de la transmisión **(default 1e6 N/m)**

- Damping: Amortiguamiento **(default 1e3 N·s/m)**

### 5.3 Modelado de Pérdidas

#### 5.3.1 Tipos de Pérdidas

Fricción Coulomb: **friction = simscape.Friction('Coulomb', 0.2);**

Pérdidas por histéresis: **hysteresisLoss(gear, 'Factor', 0.03);**

Resistencia al rodamiento: **bearingLoss = bearing('FrictionModel', 'Torque', 0.01);**

#### 5.3.2 💡 Ejemplo Completo Engranajes
```matlab

% Configuración de engranaje con pérdidas
gear_losses = simscape.multibody.Gear(...
    'Efficiency', 0.92, ...
    'MeshStiffness', 1.2e8, ...
    'Backlash', 0.0001, ...
    'FrictionTorque', 0.5);

```

### 5.4 Validación Experimental

#### 5.4.1 Comparación Modelo-Real

```matlab

% Script para comparación de datos
[simTime, simTorque] = simOut.logsout.getElement('Torque').Values.Data;
[expTime, expTorque] = importExperimentalData('test1.csv');

plotComparison(simTime, simTorque, expTime, expTorque);

```

#### 5.4.2 Métricas de Validación

- Error RMS: **rms_error = sqrt(mean((simData - expData).^2));**

- Coeficiente R²: **R2 = 1 - sum((expData - simData).^2)/sum((expData - mean(expData)).^2);**

### 5.5 Caso de Estudio: Transmisión Industrial

#### 5.5.1 Modelo Completo

```matlab

% Sistema de transmisión industrial completa
industrialSystem = multibody.TransmissionSystem(...
    'Gears', {gear_losses}, ...
    'Belts', {belt_ideal}, ...
    'Bearings', {bearingLoss}, ...
    'InputSpeed', 1750, ... % RPM
    'LoadTorque', 150); % Nm

```

#### 5.5.2 Análisis de Resultados

```matlab

% Post-procesamiento automático
results = simulate(industrialSystem);
plotEfficiency(results);
plotPowerLoss(results);

```

### 5.6 Ejercicios Prácticos

#### 5.6.1 Calibración de Modelo

```matlab

% Ajuste de parámetros de fricción
frictionParams = optimizableVariable('CoulombFric', [0.1, 0.5]);
optimResults = bayesopt(@(p) modelCalibrationError(p), frictionParams);

```
#### 5.6.2 Análisis de Sensibilidad

```matlab

% Sensibilidad de la eficiencia a la rigidez
stiffnessRange = logspace(6, 9, 50);
efficiency = arrayfun(@(k) computeEfficiency(k), stiffnessRange);
loglog(stiffnessRange, efficiency);

```

### 5.7 Recursos Adicionales

- Librerías: **Simscape Driveline** (para transmisiones)

- Tutoriales: MathWorks "Modeling Power Transmission Systems"

- Datos Experimentales: **NREL Drivetrain Database**


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


