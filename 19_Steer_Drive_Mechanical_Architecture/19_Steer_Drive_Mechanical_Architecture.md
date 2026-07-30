**Differential Drive & Steer Drive Engineering**


# Chapter 19 Steer Drive Mechanical Architecture

##  

## 01 Steering module design

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Steering Mechanism Types

The steering mechanism is one of the most critical subsystems within a Four-Wheel Steering (4WS) steer-drive mobile robot because it determines how accurately and efficiently each wheel module can orient itself to generate the desired vehicle motion. Unlike conventional automobiles, where only the front axle provides steering, a steer-drive robot equips every wheel with an independent steering actuator. This architecture enables omnidirectional mobility, precise positioning, zero-radius rotation, crab motion, and diagonal translation. Consequently, the steering mechanism must provide high angular accuracy, fast dynamic response, low backlash, and sufficient mechanical stiffness while maintaining long-term reliability under continuous industrial operation.

Several steering mechanism architectures are commonly employed depending on payload, positioning accuracy, installation constraints, and manufacturing cost. The most widely adopted solution is the direct steering module, in which the steering motor drives the wheel support through a reduction gearbox mounted concentrically around the steering axis. This arrangement provides excellent structural rigidity and minimizes transmission complexity. Because the steering axis coincides with the rotational center of the module, mechanical errors caused by intermediate linkage mechanisms are significantly reduced. Direct steering architectures are therefore widely used in semiconductor robots, logistics AMRs, and precision inspection platforms.

Another common approach is the belt-driven steering mechanism. In this design, a timing belt transfers torque from the steering motor to the steering shaft. Belt transmission allows greater flexibility in motor placement, making the module more compact and simplifying maintenance. Belts also provide inherent vibration isolation and operate with relatively low noise. However, belt elasticity introduces small positioning errors under rapidly changing loads, and long-term belt wear may require periodic tension adjustment. Consequently, belt-driven systems are generally preferred for medium-payload robots where moderate positioning accuracy is acceptable.

Planetary gear steering mechanisms are frequently adopted in industrial applications requiring compact size together with relatively high torque capacity. A planetary gearbox distributes transmitted torque across multiple gear meshes, increasing torque density while maintaining a compact package. The coaxial configuration also simplifies integration with steering bearings and encoder systems. Although planetary gearboxes provide excellent efficiency and load capacity, standard industrial gearboxes may exhibit measurable backlash unless precision-grade components are selected.

Harmonic drive steering mechanisms are increasingly used in high-precision autonomous mobile robots because of their nearly zero backlash and exceptionally high positioning repeatability. A harmonic drive consists of a wave generator, flex spline, and circular spline, producing very high reduction ratios within a compact mechanical envelope. Since backlash is essentially eliminated, steering accuracy remains extremely high even during frequent reversals of steering direction. Harmonic drives are therefore widely employed in semiconductor manufacturing robots, metrology systems, and precision docking platforms where positioning errors must remain within only a few millimeters. Their disadvantages include relatively high manufacturing cost, reduced efficiency compared with planetary gearboxes, and lower resistance to severe impact loading.

Cycloidal gear steering mechanisms provide another attractive alternative for heavy-duty industrial robots. Cycloidal reducers distribute transmitted torque over multiple rolling contacts, producing extremely high shock resistance and long operational lifetime. Their torsional stiffness also improves steering stability under heavy payload conditions. Although cycloidal gearboxes are generally larger and heavier than harmonic drives, they are frequently selected for outdoor autonomous vehicles, heavy logistics robots, and mining applications where durability outweighs compactness.

The steering bearing arrangement also significantly influences steering performance. Large crossed-roller bearings provide excellent axial and radial stiffness while supporting substantial overturning moments generated during vehicle acceleration and heavy payload transport. Tapered roller bearings are another common solution because they simultaneously accommodate radial and axial loads while maintaining accurate steering alignment. Proper bearing preload is essential because excessive preload increases friction, whereas insufficient preload introduces unwanted steering compliance.

Modern steering modules increasingly adopt modular integrated architectures in which the steering motor, reduction gearbox, steering bearing, encoder, and electrical slip ring are assembled into a single replaceable unit. This modular philosophy simplifies manufacturing, reduces maintenance time, and improves field serviceability. Individual steering modules can be replaced without disassembling the entire drive system, significantly reducing production downtime.

Material selection also affects steering mechanism performance. High-strength alloy steel is commonly employed for steering shafts because of its excellent fatigue resistance. Aluminum alloy housings reduce total vehicle mass while maintaining adequate stiffness. Hardened gear surfaces improve wear resistance, whereas corrosion-resistant coatings extend operational life in harsh industrial environments. Finite Element Analysis is frequently employed during structural design to verify stiffness, stress distribution, fatigue life, and resonance characteristics before prototype manufacturing.

The selection of an appropriate steering mechanism ultimately depends upon application requirements rather than any universally optimal solution. Semiconductor manufacturing robots prioritize positioning accuracy and therefore frequently employ harmonic drive systems. Warehouse logistics robots balance cost and performance using planetary gear steering modules. Heavy-duty industrial platforms often select cycloidal reducers to maximize durability. Regardless of the chosen architecture, the steering mechanism remains one of the most important contributors to the overall positioning accuracy, maneuverability, reliability, and lifetime of a Four-Wheel Steering autonomous mobile robot.

---

### 1.2 Steering Gearbox Design

The steering gearbox serves as the mechanical interface between the steering motor and the steering axis, converting the high-speed, relatively low-torque output of the motor into the high-torque, low-speed motion required for precise wheel orientation. Because steering accuracy directly influences vehicle positioning accuracy, the gearbox becomes one of the most critical mechanical components within a steer-drive module. Its design must simultaneously satisfy demanding requirements for torque transmission, positioning precision, torsional stiffness, efficiency, durability, compactness, and manufacturability.

The first consideration in gearbox design is the required reduction ratio. Steering motors typically operate efficiently at rotational speeds ranging from several thousand revolutions per minute, whereas steering motion rarely exceeds a few hundred degrees per second. Consequently, reduction ratios between approximately 30:1 and 120:1 are commonly employed depending on vehicle size and steering performance requirements. Higher reduction ratios increase available steering torque and improve angular resolution, although they may reduce maximum steering speed and mechanical efficiency.

Backlash represents one of the most influential gearbox characteristics affecting steering performance. Mechanical backlash is defined as the angular clearance between mating gear teeth before torque transmission begins. Even small amounts of backlash produce steering dead zones, oscillation during closed-loop control, and positioning errors during frequent steering reversals. High-precision steer-drive systems therefore employ low-backlash or zero-backlash gearboxes whenever accurate docking, inspection, or semiconductor transport is required.

Torsional stiffness is equally important because steering torque continuously changes during vehicle acceleration, braking, and interaction with uneven floor surfaces. Gearboxes exhibiting low torsional stiffness experience elastic deformation under load, causing steering angle deviations despite accurate motor control. High torsional stiffness enables more predictable steering behavior and significantly improves closed-loop servo performance.

Efficiency influences both energy consumption and thermal performance. Planetary gearboxes generally achieve efficiencies exceeding ninety-five percent, while harmonic drives typically exhibit somewhat lower efficiencies because of internal elastic deformation. Cycloidal gearboxes occupy an intermediate range but provide superior overload capability. Designers therefore evaluate efficiency together with torque density, backlash, and expected duty cycle rather than considering efficiency alone.

Gearbox lubrication plays a critical role in long-term reliability. Grease lubrication is commonly adopted for compact sealed steering modules because it requires minimal maintenance and prevents lubricant leakage. Oil lubrication provides superior cooling for large industrial gearboxes operating under continuous heavy loads but requires more complex sealing systems. Proper lubricant selection depends upon operating temperature, rotational speed, expected service life, and environmental conditions.

Structural integration between the gearbox and steering housing must maintain precise concentricity between the steering axis, output bearing, and encoder shaft. Small alignment errors increase bearing loads, generate uneven gear wear, and reduce positioning accuracy. Precision machining and tight geometric tolerances are therefore essential throughout the gearbox assembly.

Finite Element Analysis and multibody dynamic simulation are frequently employed during gearbox development. Structural simulations verify housing stiffness and stress distribution under maximum steering torque, while dynamic simulations evaluate vibration characteristics, gear meshing behavior, and resonance frequencies. Thermal analysis additionally predicts heat generation during continuous industrial operation and verifies that gearbox temperatures remain within acceptable limits.

Modern industrial steering gearboxes are increasingly designed as integrated assemblies containing the gearbox, steering bearing, motor mounting interface, encoder interface, and cable routing channels within a single housing. This integrated approach reduces assembly complexity, improves structural stiffness, simplifies manufacturing, and minimizes installation errors. Maintenance also becomes more efficient because complete steering gearbox assemblies can be replaced rapidly during field servicing.

The optimal steering gearbox design therefore represents a compromise among reduction ratio, backlash, torsional stiffness, efficiency, durability, manufacturability, and cost. Careful optimization of these characteristics enables precise steering control while ensuring reliable operation throughout the long service life expected of industrial autonomous mobile robots.

---

### 1.3 Absolute Encoder Integration

The absolute encoder is an indispensable sensing component within a steer-drive steering module because it provides an unambiguous measurement of steering angle at all times, including immediately after power restoration. Unlike incremental encoders, which determine position by counting relative motion from a reference point, an absolute encoder reports the actual angular position directly. This capability eliminates homing procedures during startup and significantly improves the operational availability of autonomous mobile robots operating in industrial environments.

Within a steering module, the absolute encoder is typically mounted coaxially with the steering output shaft to measure the true steering angle rather than motor shaft rotation. Direct measurement at the steering axis eliminates accumulated transmission errors caused by gearbox backlash, shaft elasticity, or coupling deformation. Consequently, the measured steering angle accurately represents the physical orientation of the wheel module.

Absolute encoders employ several sensing technologies depending upon required performance. Optical encoders provide extremely high angular resolution and excellent repeatability, making them suitable for semiconductor manufacturing and precision inspection robots. Magnetic encoders offer superior resistance to dust, vibration, moisture, and mechanical shock while maintaining adequate resolution for most industrial logistics applications. Inductive encoders combine high durability with immunity to contamination and are increasingly adopted for harsh industrial environments requiring long maintenance intervals.

Encoder resolution directly influences steering precision. High-resolution absolute encoders commonly provide between sixteen and twenty-four bits of angular information, corresponding to hundreds of thousands or even millions of unique angular positions over one complete revolution. Such high resolution enables extremely fine steering adjustments, supporting precision docking, low-speed trajectory tracking, and accurate multidirectional motion.

Communication between the encoder and motion controller is commonly implemented using industrial digital interfaces such as BiSS-C, EnDat, SSI, or CANopen. These deterministic communication protocols provide reliable transmission of absolute position data while supporting diagnostic information including internal temperature, signal quality, supply voltage, and device status. Modern servo controllers frequently read encoder measurements at update rates exceeding one kilohertz, allowing precise closed-loop steering control.

Encoder calibration represents an essential stage of steering module manufacturing. During calibration, the mechanical relationship between encoder zero position and actual wheel orientation is accurately established. Offset values are stored permanently within either the encoder memory or the motion controller, ensuring consistent steering reference after every system restart. Periodic recalibration may also compensate for small mechanical changes resulting from long-term wear or component replacement.

Mechanical integration requires careful attention to concentricity, shaft alignment, and vibration isolation. Excessive radial runout, shaft eccentricity, or mechanical misalignment reduces measurement accuracy and shortens encoder service life. Precision machining, rigid mounting structures, and high-quality shaft couplings therefore play important roles in maintaining long-term encoder performance.

Absolute encoder data also contributes to functional safety. The steering controller continuously compares commanded steering angles with measured encoder values. Significant discrepancies may indicate gearbox failure, steering motor malfunction, mechanical obstruction, or encoder faults. Diagnostic algorithms immediately identify such abnormal conditions and trigger appropriate fault responses before steering performance degrades sufficiently to threaten safe vehicle operation.

Sensor fusion further enhances encoder utilization. Steering angle measurements are combined with wheel encoder data, inertial measurements, LiDAR localization, and vision-based localization to estimate complete vehicle motion. During precision docking, the absolute encoder provides highly accurate steering feedback while external localization systems verify the resulting vehicle trajectory. This combination substantially improves positioning repeatability under changing environmental conditions.

As industrial autonomous mobile robots continue demanding higher levels of positioning accuracy and operational reliability, the integration of high-resolution absolute encoders becomes increasingly important. Their ability to provide immediate position knowledge, eliminate homing procedures, support deterministic servo control, enable predictive diagnostics, and improve sensor fusion performance makes them one of the most essential sensing technologies within modern Four-Wheel Steering steer-drive platforms.

다음은 앞서 작성한 영어 내용을 자연스럽고 기술 서적에 적합한 한국어로 번역한 내용입니다. 기술 용어는 가능한 한 **한글(영어)** 형식으로 표기하였으며, 설명형 문장으로 구성하였습니다. 글머리표와 번호 매기기는 최소화하였습니다.

---

### 1.1 조향 메커니즘 종류 (Steering Mechanism Types)

조향 메커니즘(Steering Mechanism)은 **4륜 조향(4WS, Four-Wheel Steering)** 스티어 드라이브(Steer Drive) 이동로봇에서 가장 중요한 하위 시스템 가운데 하나이다. 이 시스템은 각 휠 모듈(Wheel Module)이 원하는 방향으로 얼마나 정확하고 빠르게 회전할 수 있는지를 결정하며, 차량 전체의 운동 성능을 좌우한다. 일반 승용차는 앞바퀴만 조향 기능을 수행하지만, 스티어 드라이브 로봇은 모든 바퀴가 독립적인 조향 액추에이터(Independent Steering Actuator)를 갖는다. 이러한 구조 덕분에 전방향 이동(Holonomic Motion), 정밀 위치 제어(Precision Positioning), 제자리 회전(Zero Radius Rotation), 크랩 주행(Crab Motion), 대각선 이동(Diagonal Motion)과 같은 다양한 운동이 가능하다. 따라서 조향 메커니즘은 높은 각도 정밀도, 빠른 응답성, 낮은 백래시(Backlash), 높은 구조 강성(Stiffness) 및 장기간 산업 환경에서의 신뢰성을 동시에 만족해야 한다.

조향 메커니즘은 적재 하중(Payload), 요구되는 위치 정밀도(Positioning Accuracy), 설치 공간, 제조 비용 등에 따라 다양한 구조가 사용된다. 가장 널리 사용되는 방식은 **직결형 조향 모듈(Direct Steering Module)**이다. 이 구조에서는 조향 모터가 감속기를 통해 조향축(Steering Axis)을 직접 회전시키며, 감속기는 조향축과 동심(Coaxial) 구조로 배치된다. 이러한 방식은 구조 강성이 높고 전달 경로가 단순하여 중간 링크(Linkage)에서 발생하는 오차를 최소화할 수 있다. 따라서 반도체 운반 로봇, 물류 AMR 및 정밀 검사 장비에서 가장 많이 사용된다.

또 다른 방식은 **벨트 구동 조향(Belt-driven Steering Mechanism)**이다. 이 방식에서는 타이밍 벨트(Timing Belt)를 이용하여 조향 모터의 토크를 조향축으로 전달한다. 벨트 구동은 모터 배치의 자유도가 높아 구조를 컴팩트하게 만들 수 있으며, 진동 흡수와 저소음 운전이라는 장점이 있다. 그러나 벨트의 탄성으로 인해 하중 변화 시 작은 위치 오차가 발생할 수 있고, 장기간 사용하면 장력(Tension)을 다시 조정해야 한다. 따라서 중간 정도의 정밀도를 요구하는 중형 물류 로봇에서 많이 사용된다.

**유성기어 조향(Planetary Gear Steering Mechanism)**은 높은 토크와 작은 크기를 동시에 요구하는 산업용 AMR에서 널리 사용된다. 유성기어 감속기(Planetary Gearbox)는 여러 개의 기어가 동시에 하중을 분담하기 때문에 높은 토크 밀도(Torque Density)를 제공하면서도 구조가 매우 컴팩트하다. 또한 동심 구조(Coaxial Configuration)를 유지하기 쉬워 조향 베어링 및 엔코더와의 통합도 용이하다. 다만 일반 산업용 유성기어는 정밀급 제품이 아닌 경우 일정 수준의 백래시가 존재할 수 있다.

최근에는 **하모닉 드라이브(Harmonic Drive)**가 고정밀 자율주행 로봇에 많이 적용되고 있다. 하모닉 드라이브는 웨이브 제너레이터(Wave Generator), 플렉스 스플라인(Flex Spline), 서큘러 스플라인(Circular Spline)으로 구성되며, 매우 높은 감속비를 가지면서도 거의 **제로 백래시(Zero Backlash)**를 구현할 수 있다. 따라서 반복적인 조향 방향 변경에도 매우 높은 위치 반복 정밀도(Repeatability)를 유지할 수 있으며, 반도체 제조 장비, 계측 시스템(Metrology System) 및 정밀 도킹 로봇에 널리 사용된다. 그러나 제조 비용이 높고 유성기어에 비해 효율(Efficiency)이 다소 낮으며, 큰 충격 하중에는 상대적으로 취약한 단점이 있다.

**사이클로이드 감속기(Cycloidal Gear Reducer)**는 중량급 산업용 로봇에서 많이 사용된다. 여러 개의 롤링 접촉(Rolling Contact)을 통해 토크를 전달하기 때문에 충격에 매우 강하며 긴 수명을 가진다. 또한 높은 비틀림 강성(Torsional Stiffness)을 제공하여 무거운 하중에서도 안정적인 조향이 가능하다. 하모닉 드라이브보다 크고 무겁지만, 내구성이 매우 뛰어나므로 실외 자율주행 차량, 중량 물류 로봇 및 광산 장비 등에 적합하다.

조향 베어링(Steering Bearing)의 구조도 매우 중요하다. **크로스 롤러 베어링(Crossed Roller Bearing)**은 높은 축방향 및 반경 방향 강성을 제공하며, 차량의 가속이나 중량물 운반 시 발생하는 큰 모멘트를 안정적으로 지지할 수 있다. **테이퍼 롤러 베어링(Tapered Roller Bearing)**도 반경 하중과 축방향 하중을 동시에 지지할 수 있어 많이 사용된다. 베어링의 프리로드(Preload)는 매우 중요한 설계 요소이며, 너무 크면 마찰이 증가하고 너무 작으면 조향 유격이 발생한다.

최근에는 조향 모터, 감속기, 조향 베어링, 절대형 엔코더(Absolute Encoder) 및 슬립 링(Slip Ring)을 하나의 모듈로 통합한 **모듈형 조향 시스템(Modular Steering System)**이 널리 사용되고 있다. 이러한 구조는 제조를 단순화하고 유지보수 시간을 줄이며, 고장이 발생한 경우 전체 모듈만 교체하면 되므로 현장 서비스(Field Service)가 매우 용이하다.

재료(Material) 선택도 조향 성능에 큰 영향을 미친다. 조향축은 피로 강도가 높은 고강도 합금강(High-strength Alloy Steel)을 사용하며, 하우징은 무게를 줄이기 위해 알루미늄 합금(Aluminum Alloy)을 많이 사용한다. 기어는 표면 경화(Hardening)를 통해 마모를 줄이고, 부식 방지 코팅(Corrosion-resistant Coating)은 산업 환경에서 긴 수명을 보장한다. 또한 **유한요소해석(Finite Element Analysis, FEA)**을 이용하여 구조 강성, 응력 분포, 피로 수명 및 공진 특성을 사전에 검증한다.

결국 조향 메커니즘의 선택은 하나의 정답이 존재하는 것이 아니라 적용 분야에 따라 달라진다. 반도체 제조 장비는 높은 정밀도를 위해 하모닉 드라이브를 선호하며, 물류 AMR은 가격과 성능의 균형을 고려하여 유성기어를 많이 사용한다. 중량급 산업용 플랫폼은 내구성을 우선하여 사이클로이드 감속기를 채택하는 경우가 많다. 어떠한 구조를 선택하든 조향 메커니즘은 **4륜 조향 자율주행 이동로봇의 위치 정밀도, 기동성, 신뢰성 및 수명을 결정하는 가장 중요한 요소 가운데 하나**이다.

---

### 1.2 조향 감속기 설계 (Steering Gearbox Design)

조향 감속기(Steering Gearbox)는 조향 모터와 조향축 사이를 연결하는 핵심 기계 요소로, 모터의 **고속·저토크(High-speed, Low-torque)** 출력을 **저속·고토크(Low-speed, High-torque)**의 조향 운동으로 변환한다. 차량의 위치 정밀도는 조향 정확도에 직접적인 영향을 받기 때문에, 감속기는 스티어 드라이브 모듈에서 가장 중요한 기계 요소 가운데 하나이다. 감속기 설계는 토크 전달 능력(Torque Transmission), 위치 정밀도(Positioning Accuracy), 비틀림 강성(Torsional Stiffness), 효율(Efficiency), 내구성(Durability), 소형화(Compactness) 및 제조성(Manufacturability)을 동시에 만족해야 한다.

가장 먼저 결정해야 하는 요소는 **감속비(Reduction Ratio)**이다. 일반적인 서보 모터는 수천 rpm의 속도에서 가장 효율적으로 동작하지만, 실제 조향 속도는 초당 수백 도 정도면 충분하다. 따라서 일반적으로 **30:1\~120:1** 정도의 감속비가 많이 사용된다. 감속비가 높을수록 조향 토크와 각도 분해능(Angular Resolution)은 향상되지만, 최대 조향 속도와 기계 효율은 감소할 수 있다.

감속기의 가장 중요한 성능 요소 가운데 하나는 **백래시(Backlash)**이다. 백래시는 기어가 맞물리기 전에 발생하는 작은 각도 유격을 의미한다. 백래시가 존재하면 조향 데드존(Dead Zone), 폐루프 제어 진동 및 방향 전환 시 위치 오차가 발생한다. 따라서 정밀 도킹이나 반도체 장비에서는 **저백래시(Low-backlash)** 또는 **제로 백래시(Zero-backlash)** 감속기를 사용한다.

또 다른 중요한 요소는 **비틀림 강성(Torsional Stiffness)**이다. 차량이 가속, 감속 또는 요철을 통과할 때 조향축에는 지속적으로 토크가 작용한다. 감속기의 비틀림 강성이 낮으면 부하에 의해 기어가 탄성 변형되어 모터는 정확히 제어되더라도 실제 조향각에는 오차가 발생한다. 높은 비틀림 강성은 보다 안정적인 조향과 우수한 서보 제어 성능을 제공한다.

감속기의 효율도 중요한 설계 요소이다. 일반적으로 **유성기어 감속기(Planetary Gearbox)**는 95% 이상의 높은 효율을 가지며, **하모닉 드라이브(Harmonic Drive)**는 내부 탄성 변형 때문에 효율이 다소 낮다. **사이클로이드 감속기(Cycloidal Gearbox)**는 중간 정도의 효율을 가지지만 과부하에 매우 강하다. 따라서 감속기 선택 시에는 효율뿐 아니라 토크 밀도, 백래시 및 사용 조건을 함께 고려해야 한다.

윤활(Lubrication)도 감속기의 수명에 큰 영향을 미친다. 대부분의 소형 조향 모듈은 유지보수가 거의 필요 없는 **그리스 윤활(Grease Lubrication)**을 사용하며, 대형 산업용 감속기는 냉각 성능이 우수한 **오일 윤활(Oil Lubrication)**을 사용한다. 윤활 방식은 사용 온도, 회전 속도, 기대 수명 및 작업 환경을 고려하여 결정된다.

감속기와 조향 하우징(Steering Housing)의 정렬 정확도도 매우 중요하다. 조향축, 출력 베어링(Output Bearing), 엔코더 샤프트가 정확하게 동심을 유지하지 못하면 베어링 하중이 증가하고 기어가 비정상적으로 마모되며 위치 정밀도가 저하된다. 따라서 정밀 가공과 엄격한 기하공차(Geometric Tolerance)가 요구된다.

감속기 개발 과정에서는 **유한요소해석(Finite Element Analysis, FEA)**과 **다물체 동역학 해석(Multibody Dynamic Simulation)**이 널리 활용된다. 구조 해석을 통해 최대 토크에서의 응력과 변형을 확인하고, 동역학 해석을 통해 진동, 기어 맞물림(Gear Meshing), 공진 주파수(Resonance Frequency)를 분석한다. 또한 열 해석(Thermal Analysis)을 통해 장시간 운전 시 감속기의 온도가 허용 범위 내에 유지되는지도 검증한다.

최근 산업용 조향 감속기는 감속기, 조향 베어링, 모터 장착부, 엔코더 장착부 및 케이블 경로를 하나의 하우징으로 통합한 **일체형 설계(Integrated Assembly)**를 채택하는 경우가 많다. 이러한 구조는 조립을 단순화하고 구조 강성을 향상시키며 설치 오차를 줄여준다. 또한 유지보수 시에는 전체 모듈만 교체하면 되므로 서비스 시간이 크게 단축된다.

결국 **조향 감속기 설계는 감속비, 백래시, 비틀림 강성, 효율, 내구성, 제조 비용 사이의 최적 균형을 찾는 과정**이다. 이러한 요소를 적절하게 최적화함으로써 산업용 자율주행 이동로봇은 높은 조향 정밀도와 긴 수명을 동시에 확보할 수 있다.

---

### 1.3 절대형 엔코더 통합 (Absolute Encoder Integration)

절대형 엔코더(Absolute Encoder)는 스티어 드라이브 조향 모듈에서 **조향각(Steering Angle)을 항상 정확하게 측정하는 핵심 센서**이다. 증분형 엔코더(Incremental Encoder)는 기준점(Home Position)으로부터의 상대적인 회전량을 계산하지만, 절대형 엔코더는 전원이 다시 인가되더라도 현재의 절대 위치(Absolute Position)를 즉시 출력할 수 있다. 따라서 전원을 켤 때마다 원점 복귀(Homing)를 수행할 필요가 없으며, 산업용 자율주행 이동로봇의 가동률(Availability)을 크게 향상시킨다.

절대형 엔코더는 일반적으로 조향 출력축(Output Steering Shaft)과 동축(Coaxial)으로 설치된다. 모터축이 아닌 실제 조향축의 각도를 직접 측정하기 때문에 감속기의 백래시, 축의 탄성 변형 및 커플링(Coupling)의 오차가 측정값에 누적되지 않는다. 따라서 엔코더가 측정하는 값은 실제 바퀴의 방향과 거의 동일하다.

절대형 엔코더는 다양한 측정 방식을 사용한다. **광학식 엔코더(Optical Encoder)**는 매우 높은 분해능과 반복 정밀도를 제공하므로 반도체 제조 장비나 정밀 검사 로봇에서 많이 사용된다. **자기식 엔코더(Magnetic Encoder)**는 먼지, 진동, 습기 및 충격에 강하며 대부분의 산업용 물류 로봇에 적합하다. 최근에는 오염에 강하고 긴 유지보수 주기를 제공하는 **유도식 엔코더(Inductive Encoder)**도 많이 적용되고 있다.

엔코더의 분해능(Resolution)은 조향 정밀도를 결정하는 중요한 요소이다. 최신 절대형 엔코더는 일반적으로 **16비트에서 24비트** 수준의 분해능을 제공하며, 이는 한 바퀴를 수십만에서 수백만 개의 위치로 구분할 수 있음을 의미한다. 이러한 높은 분해능은 저속 주행, 정밀 도킹 및 전방향 이동에서 매우 미세한 조향 제어를 가능하게 한다.

엔코더와 모션 제어기(Motion Controller)는 **BiSS-C**, **EnDat**, **SSI**, **CANopen**과 같은 산업용 디지털 통신 인터페이스를 이용하여 연결된다. 이러한 통신 방식은 절대 위치뿐 아니라 내부 온도, 전원 상태, 신호 품질 및 장치 진단 정보를 함께 전달할 수 있다. 대부분의 산업용 서보 제어기는 **1 kHz 이상의 제어 주기**로 엔코더 데이터를 읽어 정밀한 폐루프 제어를 수행한다.

엔코더 보정(Calibration)은 조향 모듈 제작 과정에서 반드시 수행된다. 이 과정에서는 엔코더의 영점(Zero Position)과 실제 바퀴 방향의 관계를 정확하게 설정한다. 설정된 오프셋 값은 엔코더 내부 메모리 또는 제어기에 저장되며, 이후 전원을 다시 켜더라도 항상 동일한 조향 기준을 유지한다. 또한 장기간 사용하면서 발생하는 마모나 부품 교체에 대응하기 위해 주기적인 재보정(Recalibration)을 수행하기도 한다.

기계적 통합(Mechanical Integration) 역시 매우 중요하다. 엔코더는 조향축과 정확한 동심도를 유지해야 하며, 축 편심(Shaft Eccentricity), 진동 및 정렬 오차는 측정 정확도를 떨어뜨리고 엔코더의 수명을 단축시킨다. 따라서 정밀 가공과 강성이 높은 장착 구조, 고품질 커플링이 필수적이다.

절대형 엔코더는 기능 안전(Functional Safety)에도 중요한 역할을 한다. 제어기는 항상 목표 조향각(Commanded Steering Angle)과 실제 엔코더 값을 비교하며, 큰 차이가 발생하면 감속기 고장, 조향 모터 이상, 기계적 걸림 또는 엔코더 오류로 판단할 수 있다. 이러한 진단 알고리즘은 심각한 성능 저하가 발생하기 전에 이상 상태를 검출하고 적절한 보호 동작을 수행한다.

절대형 엔코더는 센서 융합(Sensor Fusion)에도 적극 활용된다. 조향각 정보는 휠 엔코더, IMU, LiDAR 위치 인식 및 비전 기반 위치 인식과 함께 사용되어 차량의 전체 운동 상태를 추정한다. 특히 정밀 도킹 과정에서는 절대형 엔코더가 매우 정확한 조향 정보를 제공하고, 외부 위치 인식 시스템이 차량의 실제 이동 경로를 확인함으로써 반복 정밀도를 크게 향상시킨다.

결국 **절대형 엔코더는 단순한 각도 센서가 아니라 스티어 드라이브 플랫폼의 정밀 제어와 안전성을 동시에 책임지는 핵심 구성 요소**이다. 원점 복귀가 필요 없는 절대 위치 측정, 높은 분해능, 결정론적 통신, 고장 진단 기능 및 센서 융합 지원 능력을 바탕으로, 현대 산업용 **4륜 조향(4WS)** 자율주행 이동로봇의 위치 정밀도와 신뢰성을 결정하는 가장 중요한 센서 가운데 하나로 자리 잡고 있다.

##  

## 02 Drive module design

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Drive Motor Mounting

The drive motor is the primary source of propulsion in a Four-Wheel Steering (4WS) steer-drive mobile robot, directly converting electrical energy into the mechanical torque required for vehicle motion. Unlike conventional vehicles where propulsion is often concentrated on one or two axles, each steer-drive module incorporates an independent drive motor that operates together with an independent steering actuator. This distributed architecture enables precise traction control, omnidirectional mobility, fault tolerance, and accurate torque distribution under varying operating conditions. Consequently, the drive motor mounting structure becomes a critical mechanical interface that directly influences drivetrain rigidity, vibration characteristics, thermal performance, maintenance accessibility, and long-term reliability.

The primary objective of drive motor mounting is to maintain accurate alignment between the motor shaft and the gearbox input shaft while transmitting high torque without introducing excessive structural deformation. Even slight misalignment increases bearing loads, accelerates gearbox wear, generates unwanted vibration, and reduces drivetrain efficiency. Therefore, precision machining tolerances and rigid mounting surfaces are essential design requirements. Most industrial steer-drive modules employ machined aluminum alloy or cast steel motor mounting plates with accurately positioned locating features to ensure repeatable assembly.

Two fundamental motor mounting architectures are commonly adopted. The first is the direct coaxial mounting configuration, where the motor shaft is aligned directly with the gearbox input shaft. This arrangement minimizes transmission components, reduces mechanical losses, and improves torsional stiffness because no intermediate couplings or belts are required. Direct mounting is particularly advantageous for high-performance industrial AMRs requiring rapid acceleration, precise low-speed control, and compact packaging.

The second configuration utilizes offset motor mounting with intermediate transmission elements such as timing belts or gear pairs. This approach allows greater flexibility in module packaging and may reduce overall module height by relocating the motor away from the steering axis. Belt transmission additionally provides vibration isolation and simplifies motor replacement during maintenance. However, additional transmission elements introduce compliance, increase mechanical complexity, and require periodic inspection and adjustment.

Structural stiffness is one of the most important considerations in motor mounting design. During rapid acceleration, regenerative braking, or heavy payload transport, the motor generates substantial reaction torque that is transferred into the supporting structure. Insufficient structural rigidity allows elastic deformation, producing small changes in shaft alignment and negatively affecting drivetrain accuracy. Finite Element Analysis is therefore routinely employed to optimize bracket geometry, minimize stress concentration, and verify structural deflection under maximum operating loads.

Thermal management must also be integrated into the mounting structure. High-power servo motors continuously generate heat during industrial operation, particularly during repeated acceleration and heavy-duty transportation. The motor mounting plate frequently serves as a heat conduction path, transferring thermal energy into the vehicle chassis where it can be dissipated more effectively. Some heavy-duty systems further integrate liquid-cooled motor jackets or dedicated cooling channels to maintain stable operating temperatures during continuous operation.

Vibration isolation presents another important design challenge. Although rigid mounting improves positioning accuracy, excessive structural rigidity may transmit high-frequency motor vibration throughout the vehicle. Elastomer isolation elements, optimized structural damping, and careful modal analysis are therefore employed to avoid resonance between motor excitation frequencies and chassis natural frequencies. Maintaining this balance between stiffness and vibration isolation significantly improves operational stability and reduces acoustic noise.

Cable routing is incorporated into the motor mounting design from the earliest development stages. Power cables, encoder wiring, brake wiring, and temperature sensor connections must be protected from repeated steering rotation and mechanical interference. Integrated cable channels, protective conduits, and strain-relief mechanisms minimize cable fatigue while simplifying maintenance procedures. In steer-drive modules supporting continuous steering rotation, slip rings or rotary electrical interfaces may also be incorporated to prevent cable twisting.

Serviceability strongly influences industrial motor mounting philosophy. Modern autonomous mobile robots are expected to minimize production downtime, making rapid component replacement highly desirable. Modular motor mounting systems therefore allow complete motor assemblies to be removed without disassembling the steering mechanism or gearbox. Standardized mounting interfaces further simplify spare part management across multiple robot platforms.

Material selection contributes significantly to overall performance. High-strength aluminum alloys provide an excellent balance between structural stiffness and weight reduction for medium-duty robots, whereas cast or welded steel structures are preferred for heavy industrial platforms carrying several hundred kilograms or more. Corrosion-resistant surface treatments improve durability under harsh factory conditions involving humidity, chemicals, or cleaning procedures.

As autonomous mobile robots continue increasing in payload capacity and positioning accuracy, drive motor mounting evolves beyond a simple mechanical attachment into an integrated structural, thermal, electrical, and maintenance platform. Careful optimization of alignment, rigidity, thermal conduction, vibration behavior, and modularity ensures that the propulsion system maintains consistent performance throughout prolonged industrial operation while supporting the demanding requirements of modern steer-drive mobility systems.

---

### 2.2 Integrated Gearbox Design

The integrated gearbox constitutes the mechanical core of the drive module by transmitting motor torque to the drive wheel while simultaneously satisfying demanding requirements for efficiency, compactness, durability, and positioning accuracy. Unlike conventional industrial gearboxes installed as independent mechanical components, modern steer-drive modules increasingly integrate the gearbox directly into the drive assembly, creating a compact electromechanical unit that combines the motor interface, reduction mechanism, wheel hub, bearings, lubrication system, encoder interface, and structural housing within a single optimized package. This integrated architecture significantly improves drivetrain performance while simplifying manufacturing and maintenance.

The primary function of the integrated gearbox is to reduce the high rotational speed of the servo motor into the lower rotational speed required by the drive wheel while proportionally increasing available output torque. Typical industrial servo motors operate efficiently at several thousand revolutions per minute, whereas autonomous mobile robots usually require wheel speeds corresponding to vehicle velocities between approximately one and twenty kilometers per hour. Reduction ratios commonly range from approximately 10:1 to 40:1 depending on wheel diameter, desired maximum speed, payload capacity, and available motor torque.

Planetary gear systems remain the most widely adopted solution for integrated drive gearboxes because they provide high torque density, compact dimensions, excellent efficiency, and coaxial power transmission. Multiple planetary gears share transmitted torque, reducing individual tooth loading and improving service life. High-quality planetary gearboxes routinely achieve efficiencies exceeding ninety-five percent while maintaining relatively low backlash suitable for precision motion control.

Heavy-duty mobile robots may alternatively employ cycloidal reduction mechanisms when exceptional overload capability and shock resistance are required. Cycloidal reducers distribute transmitted forces across multiple rolling contacts, allowing extremely high torque capacity within a relatively compact mechanical envelope. Although somewhat larger than planetary gearboxes, they exhibit excellent durability under severe industrial operating conditions.

Backlash minimization remains a critical design objective because drivetrain backlash directly affects low-speed controllability, positioning repeatability, and traction stability. Precision-ground gears, optimized tooth geometry, preload mechanisms, and high-accuracy manufacturing processes reduce mechanical clearance between mating components. Lower backlash improves closed-loop velocity control and enables smoother transitions during acceleration, deceleration, and direction reversal.

Bearing integration is another essential aspect of gearbox design. Output bearings must simultaneously support radial loads generated by vehicle weight, axial forces encountered during steering, and overturning moments produced by payload motion. Tapered roller bearings, angular contact bearings, and crossed roller bearings are frequently selected according to load requirements. Proper bearing preload minimizes deflection while maintaining acceptable friction levels.

Lubrication strategy strongly influences gearbox lifetime and efficiency. Compact integrated gearboxes typically employ sealed grease lubrication, eliminating routine maintenance while preventing lubricant leakage into surrounding electronic components. Heavy-duty systems operating continuously under high thermal loads may instead utilize circulating oil lubrication with dedicated seals and cooling provisions. Lubricant selection depends upon operating temperature, rotational speed, gear material, and anticipated service interval.

Structural housing design serves multiple functions beyond mechanical support. The gearbox housing maintains gear alignment, supports bearing preload, provides lubrication containment, dissipates thermal energy, and protects internal components against contamination. Aluminum alloy housings reduce overall module weight while offering excellent thermal conductivity, whereas cast steel housings provide maximum stiffness for high-payload industrial vehicles.

Integrated gearboxes increasingly incorporate condition monitoring capabilities. Temperature sensors, vibration sensors, lubrication condition monitoring, and motor current analysis allow predictive maintenance algorithms to identify developing mechanical faults before catastrophic failure occurs. Gear wear, bearing degradation, lubrication contamination, and abnormal vibration can therefore be detected early, reducing unexpected production downtime.

Finite Element Analysis and multibody dynamic simulation play essential roles during gearbox development. Structural simulations verify stress distribution under maximum torque loading, while dynamic analysis evaluates gear meshing behavior, vibration response, shaft deflection, and bearing loading. Thermal simulations additionally predict heat generation and validate cooling performance during prolonged industrial duty cycles.

The evolution toward integrated gearbox architecture reflects broader trends in industrial robotics emphasizing compactness, modularity, reliability, and maintainability. By combining multiple mechanical functions within a unified assembly, integrated drive gearboxes reduce component count, improve structural rigidity, simplify manufacturing, and enhance drivetrain performance. These advantages make integrated gearbox design one of the fundamental enabling technologies supporting the next generation of high-performance steer-drive autonomous mobile robots.

---

### 2.3 Integrated Brake Design

The integrated brake system provides controlled stopping capability and stationary holding force for a Four-Wheel Steering steer-drive mobile robot. While the drive motor generates propulsion and regenerative braking supplies routine deceleration during normal operation, mechanical braking remains essential for emergency stopping, parking, vertical slope holding, maintenance safety, and power-loss protection. Consequently, modern drive modules integrate compact braking mechanisms directly into the motor and gearbox assembly to ensure reliable operation under all operating conditions.

Most industrial autonomous mobile robots employ spring-applied, electrically released electromagnetic brakes. Under normal operating conditions, electrical current energizes the brake coil and releases the braking mechanism, allowing unrestricted motor rotation. If electrical power is intentionally removed or unexpectedly lost, compression springs automatically engage the brake, locking the motor shaft without requiring external control signals. This fail-safe architecture guarantees that the vehicle remains stationary during power failures and satisfies fundamental industrial safety requirements.

Brake torque selection depends upon maximum payload, wheel radius, floor inclination, friction coefficient, and expected safety margin. The required holding torque must exceed the gravitational torque acting on the vehicle under worst-case operating conditions while also accommodating dynamic disturbances such as accidental impacts or uneven floor surfaces. Engineering safety factors are typically incorporated to ensure reliable brake performance throughout component aging and wear.

Integrated brake placement significantly influences overall module design. The brake is commonly mounted directly on the motor shaft because this location minimizes component size while allowing braking torque to be multiplied by the gearbox reduction ratio before reaching the drive wheel. Consequently, relatively compact brake mechanisms can safely restrain large industrial vehicles without excessive mass or packaging volume.

Thermal considerations become important whenever friction brakes perform repeated stopping operations. Although regenerative braking absorbs most kinetic energy during routine driving, emergency braking or frequent stop-and-go applications generate substantial heat within brake friction surfaces. Integrated brake housings therefore provide conductive thermal paths into the surrounding motor and gearbox structure, while heavy-duty applications may additionally employ enhanced cooling features to prevent excessive temperature rise.

Brake response time strongly influences vehicle safety. Electromagnetic brakes typically engage within tens of milliseconds after electrical power is removed. Motion controllers account for this response delay when coordinating regenerative braking and mechanical brake activation. Smooth transition between these braking modes minimizes mechanical shock while maintaining predictable stopping performance.

Brake wear represents another important engineering consideration. Friction materials gradually degrade throughout repeated engagement cycles, reducing available holding torque over time. Many industrial brake systems therefore incorporate wear compensation mechanisms or predictive maintenance algorithms based on brake operating history. Motor current monitoring, brake engagement timing, and temperature measurements provide valuable diagnostic information regarding brake health.

Integration with the vehicle safety architecture is essential. Functional safety controllers continuously monitor brake status through dedicated sensors or electrical feedback circuits. During emergency stop procedures, regenerative braking first reduces vehicle speed before mechanical brakes engage to hold the vehicle securely at rest. This coordinated braking strategy minimizes wear while ensuring compliance with industrial safety standards.

Mechanical integration requires careful consideration of concentricity and shaft loading. Brake components must remain accurately aligned with the motor shaft to avoid introducing additional bearing loads or vibration. Compact integrated brake assemblies are therefore designed simultaneously with the motor and gearbox rather than added as separate components during later development stages.

Maintenance accessibility also influences brake design. Modular brake assemblies enable rapid replacement without disassembling the complete drive module, reducing production downtime during scheduled servicing. Brake adjustment requirements are minimized through self-compensating mechanisms and precision manufacturing techniques that maintain consistent performance throughout the operational lifetime of the robot.

Future integrated brake systems are expected to incorporate increasingly intelligent functionality through embedded sensing and predictive diagnostics. Continuous monitoring of brake temperature, engagement force, friction wear, and electrical characteristics will enable condition-based maintenance strategies while improving operational reliability. Combined with regenerative braking, adaptive vehicle control, and integrated safety systems, modern brake design forms an indispensable component of high-performance steer-drive drive modules capable of supporting demanding industrial automation applications.

### 2.1 구동 모터 장착 (Drive Motor Mounting)

구동 모터(Drive Motor)는 **4륜 조향(4WS, Four-Wheel Steering)** 스티어 드라이브(Steer Drive) 이동로봇에서 차량을 움직이기 위한 추진력을 생성하는 핵심 동력원이다. 구동 모터는 전기 에너지를 기계적인 회전 토크로 변환하여 차량을 이동시키며, 일반적인 자동차처럼 하나 또는 두 개의 차축만을 구동하는 것이 아니라, 스티어 드라이브 시스템에서는 각각의 휠 모듈(Wheel Module)이 독립적인 구동 모터를 가진다. 이러한 분산 구동 구조(Distributed Drive Architecture)는 정밀한 견인력 제어(Traction Control), 전방향 이동(Holonomic Motion), 고장 허용(Fault Tolerance) 및 다양한 노면 조건에서의 토크 분배(Torque Distribution)를 가능하게 한다. 따라서 구동 모터의 장착 구조는 단순히 모터를 고정하는 역할을 넘어, 구동계의 강성(Stiffness), 진동 특성(Vibration Characteristics), 열 관리(Thermal Management), 유지보수성(Serviceability) 및 장기적인 신뢰성(Reliability)을 결정하는 중요한 기계적 인터페이스가 된다.

구동 모터 장착의 가장 중요한 목적은 모터축(Motor Shaft)과 감속기 입력축(Gearbox Input Shaft)의 정렬(Alignment)을 정확하게 유지하면서 높은 토크를 전달하는 것이다. 축 정렬이 조금만 어긋나더라도 베어링 하중이 증가하고 감속기의 마모가 빨라지며 진동이 발생하고 구동 효율이 저하된다. 따라서 정밀한 가공 공차와 높은 강성을 가진 장착면이 반드시 필요하다. 대부분의 산업용 스티어 드라이브는 정밀 가공된 알루미늄 합금 또는 주강(Cast Steel) 모터 장착 플레이트를 사용하여 반복적인 조립에서도 항상 동일한 정렬 상태를 유지하도록 설계된다.

구동 모터의 장착 방식은 크게 두 가지가 많이 사용된다.

첫 번째는 **직결 동축(Coaxial Direct Mounting)** 구조이다. 이 방식은 모터축과 감속기 입력축을 동일한 축선상에 배치하여 중간 전달 장치를 사용하지 않는다. 따라서 기계적 손실이 가장 적고 비틀림 강성(Torsional Stiffness)이 매우 높으며, 고속 가속과 저속 정밀 제어가 필요한 산업용 AMR에서 가장 널리 사용된다.

두 번째는 **오프셋 장착(Offset Motor Mounting)** 방식이다. 이 구조에서는 타이밍 벨트(Timing Belt)나 기어를 이용하여 모터의 토크를 감속기로 전달한다. 모터를 조향축에서 떨어진 위치에 배치할 수 있기 때문에 모듈의 높이를 줄일 수 있고 구조 설계의 자유도가 높다. 또한 벨트는 진동을 일부 흡수하고 모터 교체가 비교적 쉬운 장점이 있다. 반면 전달 부품이 추가되므로 구조가 복잡해지고 탄성 변형(Compliance)이 증가하며 벨트의 장력 조정과 정기적인 유지보수가 필요하다.

모터 장착 구조에서 가장 중요한 설계 요소 가운데 하나는 **구조 강성(Structural Stiffness)**이다. 차량이 급가속하거나 회생 제동(Regenerative Braking)을 수행하거나 무거운 하중을 운반할 때 모터는 매우 큰 반력 토크(Reaction Torque)를 발생시킨다. 장착 구조의 강성이 부족하면 탄성 변형이 발생하여 축 정렬이 미세하게 변하고 구동계의 위치 정밀도가 저하된다. 따라서 설계 단계에서는 **유한요소해석(Finite Element Analysis, FEA)**을 이용하여 브래킷 형상, 응력 집중 및 최대 하중에서의 변형량을 최적화한다.

열 관리(Thermal Management) 역시 중요한 요소이다. 고출력 서보 모터는 지속적인 운전 과정에서 많은 열을 발생시키며, 특히 반복적인 가속과 중량 운반에서는 발열량이 크게 증가한다. 모터 장착 플레이트는 단순한 고정 구조물이 아니라 발생한 열을 차체로 전달하는 방열 경로(Heat Conduction Path)의 역할도 수행한다. 일부 중량급 산업용 시스템에서는 수랭식 모터 재킷(Liquid-cooled Motor Jacket)이나 냉각 채널(Cooling Channel)을 추가하여 장시간 운전에서도 안정적인 온도를 유지한다.

진동 절연(Vibration Isolation)도 중요한 설계 과제이다. 지나치게 단단한 장착 구조는 모터의 고주파 진동을 차체 전체로 전달할 수 있다. 따라서 엘라스토머(Elastomer) 절연체, 구조 감쇠(Structural Damping) 및 모드 해석(Modal Analysis)을 이용하여 공진을 방지하면서도 충분한 강성을 유지하도록 설계한다.

배선(Cable Routing)은 초기 설계 단계부터 함께 고려되어야 한다. 전원 케이블, 엔코더 케이블, 브레이크 케이블 및 온도 센서 배선은 반복적인 조향 회전에 의해 손상되지 않도록 보호되어야 한다. 이를 위해 케이블 채널(Cable Channel), 보호 튜브(Protective Conduit), 스트레인 릴리프(Strain Relief) 등이 통합 설계된다. 연속 회전이 가능한 조향 모듈에서는 슬립 링(Slip Ring) 또는 회전 전기 인터페이스(Rotary Electrical Interface)를 적용하여 케이블 꼬임을 방지하기도 한다.

산업용 AMR에서는 유지보수성(Serviceability)도 매우 중요하다. 생산라인의 가동 중단 시간을 최소화하기 위해 최근에는 모터만 독립적으로 분리할 수 있는 모듈형 장착 구조(Modular Mounting Structure)가 많이 사용된다. 또한 표준화된 장착 인터페이스(Standardized Mounting Interface)는 여러 플랫폼에서 동일한 예비 부품을 사용할 수 있도록 하여 유지보수 비용을 절감한다.

재료(Material) 선택도 전체 성능에 영향을 준다. 중형 AMR에서는 고강도 알루미늄 합금이 무게와 강성의 균형이 뛰어나 많이 사용되며, 수백 킬로그램 이상의 하중을 운반하는 산업용 플랫폼에서는 주강(Cast Steel)이나 용접 강 구조물이 사용된다. 또한 부식 방지 표면 처리(Corrosion-resistant Surface Treatment)를 적용하여 습기나 화학물질이 존재하는 산업 환경에서도 긴 수명을 확보한다.

결국 구동 모터 장착 구조는 단순한 기계적 고정부가 아니라 구조, 열, 전기 및 유지보수까지 통합적으로 고려된 플랫폼이다. 축 정렬, 강성, 열 전달, 진동 특성 및 모듈화를 최적화함으로써 현대의 스티어 드라이브 이동로봇은 장기간의 산업 현장에서도 높은 추진 성능과 안정적인 운행 능력을 유지할 수 있다.

---

### 2.2 일체형 감속기 설계 (Integrated Gearbox Design)

일체형 감속기(Integrated Gearbox)는 구동 모듈의 중심이 되는 핵심 기계 요소로서, 모터의 토크를 바퀴에 전달하는 동시에 높은 효율(Efficiency), 소형화(Compactness), 내구성(Durability) 및 위치 정밀도(Positioning Accuracy)를 만족해야 한다. 기존 산업용 장비에서는 감속기가 독립된 기계 부품으로 설치되었지만, 최근의 스티어 드라이브 모듈은 감속기를 구동 모듈 내부에 통합하여 하나의 전기·기계 통합 시스템(Electromechanical Integrated Unit)으로 설계하는 것이 일반적이다. 이 구조는 모터 장착부, 감속기, 휠 허브(Wheel Hub), 베어링(Bearing), 윤활 시스템(Lubrication System), 엔코더 인터페이스 및 하우징을 하나의 패키지로 구성하여 성능과 유지보수성을 동시에 향상시킨다.

감속기의 가장 기본적인 역할은 모터의 고속 회전을 저속·고토크 출력으로 변환하는 것이다. 일반적인 서보 모터는 수천 rpm에서 가장 효율적으로 동작하지만, 산업용 AMR은 약 **1\~20 km/h** 수준의 차량 속도만 필요하므로 바퀴 회전수는 훨씬 낮다. 따라서 일반적으로 **10:1\~40:1** 정도의 감속비(Reduction Ratio)가 사용되며, 차량의 최대 속도, 휠 직경, 적재 하중 및 모터 출력에 따라 결정된다.

가장 널리 사용되는 구조는 **유성기어 감속기(Planetary Gearbox)**이다. 여러 개의 유성기어가 동시에 하중을 분담하므로 높은 토크 밀도(Torque Density)를 제공하며, 동심(Coaxial) 구조를 유지할 수 있어 매우 컴팩트한 설계가 가능하다. 또한 효율은 일반적으로 **95% 이상**으로 매우 높으며, 저백래시(Low-backlash) 제품을 사용하면 정밀 제어에도 적합하다.

중량급 산업용 AMR에서는 **사이클로이드 감속기(Cycloidal Reducer)**가 많이 사용된다. 이 방식은 여러 개의 롤링 접촉(Rolling Contact)으로 토크를 전달하므로 충격에 강하고 과부하 허용 능력이 뛰어나다. 유성기어보다 다소 크지만 혹독한 산업 환경에서 매우 긴 수명을 제공한다.

감속기 설계에서 **백래시(Backlash)**는 매우 중요한 요소이다. 백래시는 기어 사이의 유격으로 인해 발생하는 각도 오차를 의미하며, 저속 제어, 반복 위치 정밀도 및 방향 전환 성능에 직접적인 영향을 준다. 이를 최소화하기 위해 정밀 연삭 기어(Precision-ground Gear), 최적화된 기어 치형(Tooth Geometry), 프리로드(Preload) 및 고정밀 제조 공정을 적용한다.

베어링(Bearing)의 통합 설계도 중요하다. 출력 베어링은 차량 하중으로 인한 반경 방향 힘(Radial Load), 조향에 따른 축방향 힘(Axial Load) 및 적재 하중에서 발생하는 전복 모멘트(Overturning Moment)를 동시에 지지해야 한다. 일반적으로 테이퍼 롤러 베어링(Tapered Roller Bearing), 앵귤러 콘택트 베어링(Angular Contact Bearing), 크로스 롤러 베어링(Crossed Roller Bearing)이 사용되며, 적절한 프리로드를 적용하여 변형을 최소화하고 마찰은 허용 범위 내로 유지한다.

윤활(Lubrication)은 감속기의 수명과 효율을 결정하는 중요한 요소이다. 대부분의 컴팩트한 감속기는 밀폐형 **그리스 윤활(Grease Lubrication)**을 사용하여 유지보수를 최소화하고 윤활유 누설을 방지한다. 반면 장시간 고부하 운전이 필요한 중량급 시스템에서는 **오일 윤활(Oil Lubrication)**을 적용하며, 냉각 기능도 함께 제공한다.

감속기 하우징(Gearbox Housing)은 단순히 부품을 보호하는 역할을 넘어 기어 정렬 유지, 베어링 프리로드 유지, 윤활유 밀봉, 열 방출 및 외부 오염 방지 기능까지 수행한다. 알루미늄 합금은 가볍고 방열 성능이 우수하며, 주강 하우징은 높은 강성을 제공하여 중량급 플랫폼에서 많이 사용된다.

최근에는 감속기에 상태 감시(Condition Monitoring) 기능도 통합되고 있다. 온도 센서, 진동 센서, 윤활 상태 모니터링 및 모터 전류 분석을 이용하여 기어 마모, 베어링 손상 및 윤활 문제를 조기에 발견할 수 있으며, 이를 통해 **예지보전(Predictive Maintenance)**이 가능해진다.

감속기 개발 과정에서는 **유한요소해석(FEA)**과 **다물체 동역학 해석(Multibody Dynamic Simulation)**이 적극적으로 활용된다. 최대 토크에서의 응력 분포, 기어 맞물림(Gear Meshing), 진동 특성, 축 변형 및 발열을 사전에 검증하여 실제 제작 이전에 설계를 최적화한다.

결국 일체형 감속기는 단순한 토크 전달 장치가 아니라 구동계 전체를 통합하는 핵심 플랫폼이다. 여러 기능을 하나의 모듈로 통합함으로써 부품 수를 줄이고 구조 강성을 향상시키며 제조와 유지보수를 단순화할 수 있다. 이러한 설계는 차세대 고성능 스티어 드라이브 자율주행 이동로봇의 핵심 기술 가운데 하나로 자리 잡고 있다.

---

### 2.3 일체형 브레이크 설계 (Integrated Brake Design)

일체형 브레이크(Integrated Brake)는 **4륜 조향 스티어 드라이브** 이동로봇의 감속, 정지 및 정지 유지(Holding)를 담당하는 핵심 안전 장치이다. 구동 모터는 차량을 이동시키고 회생 제동(Regenerative Braking)은 일반적인 감속을 담당하지만, 비상 정지(Emergency Stop), 주차(Parking), 경사면 정지(Slope Holding), 유지보수 작업 및 전원 장애(Power Failure) 상황에서는 반드시 기계식 브레이크(Mechanical Brake)가 필요하다. 따라서 현대의 구동 모듈은 브레이크를 모터와 감속기 내부에 통합하여 높은 신뢰성과 안전성을 확보한다.

대부분의 산업용 AMR은 **스프링 작동·전기 해제(Spring-applied, Electrically Released)** 방식의 전자기 브레이크(Electromagnetic Brake)를 사용한다. 정상 운전 시에는 브레이크 코일에 전류가 공급되어 브레이크가 해제되고 모터가 자유롭게 회전한다. 반대로 전원이 제거되거나 비상 상황이 발생하면 스프링의 힘으로 자동으로 브레이크가 체결되어 모터축을 잠근다. 이러한 **페일 세이프(Fail-safe)** 구조는 전원 장애 시에도 차량이 움직이지 않도록 보장하며 산업 안전 요구사항을 만족한다.

브레이크 토크(Brake Torque)는 최대 적재 하중, 바퀴 반경, 경사면 각도, 노면 마찰계수 및 안전율(Safety Factor)을 고려하여 결정된다. 최악의 조건에서도 차량이 미끄러지지 않도록 충분한 유지 토크(Holding Torque)를 확보해야 하며, 충격이나 외란에도 안전하게 차량을 고정할 수 있어야 한다.

브레이크는 일반적으로 모터축에 직접 설치된다. 모터축에서 발생한 제동력은 감속기를 통과하면서 감속비만큼 증폭되어 바퀴에 전달되므로, 비교적 작은 브레이크만으로도 큰 차량을 안전하게 정지시킬 수 있다. 이러한 구조는 공간을 절약하면서도 높은 제동 성능을 제공한다.

열 관리(Thermal Management)도 중요한 설계 요소이다. 일반 운전에서는 회생 제동이 대부분의 운동 에너지를 흡수하지만, 비상 정지나 반복적인 정지 운전에서는 마찰 브레이크가 많은 열을 발생시킨다. 따라서 브레이크 하우징은 발생한 열을 모터 및 감속기 구조로 전달하며, 일부 중량급 시스템은 추가적인 냉각 구조를 적용하여 과열을 방지한다.

브레이크의 응답 시간(Response Time)은 안전성과 직결된다. 일반적인 전자기 브레이크는 수십 밀리초 이내에 체결되며, 모션 제어기는 회생 제동과 기계식 브레이크를 순차적으로 제어하여 부드러운 감속과 안정적인 정지를 동시에 구현한다.

브레이크 마모(Brake Wear)는 장기간 운전 시 반드시 고려해야 하는 요소이다. 마찰재(Friction Material)는 반복적인 사용으로 마모되며 유지 토크가 점차 감소한다. 이를 보완하기 위해 자동 마모 보정(Self-compensation) 기능이나 브레이크 작동 횟수, 온도 및 전류를 이용한 예지보전 알고리즘이 적용되고 있다.

브레이크는 차량의 기능 안전(Functional Safety) 시스템과도 긴밀하게 연동된다. 안전 제어기는 브레이크 상태를 지속적으로 감시하며, 비상 정지 시에는 먼저 회생 제동으로 차량 속도를 감소시킨 후 기계식 브레이크를 체결하여 차량을 완전히 고정한다. 이러한 협조 제동(Coordinated Braking)은 브레이크 마모를 줄이는 동시에 산업 안전 규격을 만족한다.

기계적인 통합(Mechanical Integration)도 중요하다. 브레이크는 모터축과 정확한 동심도를 유지해야 하며, 편심이나 정렬 오차는 베어링 하중 증가와 진동의 원인이 된다. 따라서 브레이크는 모터와 감속기 설계 초기 단계부터 함께 설계되는 것이 일반적이다.

유지보수성(Serviceability)을 높이기 위해 최근에는 브레이크도 모듈화(Modular Brake Assembly)되고 있다. 전체 구동 모듈을 분해하지 않고 브레이크만 빠르게 교체할 수 있으며, 정밀 가공과 자동 보정 구조를 통해 별도의 조정 없이 장기간 일정한 성능을 유지할 수 있다.

향후 일체형 브레이크는 더욱 지능화될 것으로 예상된다. 브레이크 온도, 체결력, 마찰재 마모량 및 전기적 특성을 지속적으로 감시하는 센서가 내장되어 상태 기반 유지보수(Condition-based Maintenance)가 가능해질 것이다. 또한 회생 제동, 적응형 차량 제어 및 기능 안전 시스템과 긴밀하게 연동되어, **현대 산업용 스티어 드라이브 구동 모듈의 안전성과 신뢰성을 책임지는 핵심 기술**로 더욱 발전할 것이다.

##  

## 03 Bearing architecture

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Steering Axis Bearing Selection

The steering axis bearing is one of the most critical mechanical components within a Four-Wheel Steering (4WS) steer-drive module because it supports the entire steering assembly while allowing smooth and accurate rotational motion under continuously changing loads. Unlike conventional automotive steering systems that experience steering motion only occasionally, industrial autonomous mobile robots frequently execute continuous steering adjustments, crab motion, zero-radius rotation, and multidirectional navigation. Consequently, steering bearings must simultaneously withstand high radial loads, axial loads, overturning moments, impact loading, and continuous oscillatory motion while maintaining extremely low friction, minimal deflection, and long operational life.

The first step in steering bearing selection is identifying the complete loading condition acting on the steering axis. Three primary load components must be evaluated: radial load generated by the vehicle weight and payload, axial load produced during steering and uneven floor contact, and overturning moment created by vehicle acceleration, braking, cornering, or payload offset. These loads rarely occur independently; instead, they act simultaneously, requiring the bearing to sustain combined loading throughout its service life.

Crossed roller bearings are among the most commonly selected bearing types for high-precision steer-drive modules. Their rolling elements are alternately arranged at right angles, allowing a single bearing to support radial loads, axial loads in both directions, and overturning moments simultaneously. Because every roller contacts the raceway along a line rather than at a point, stiffness is exceptionally high and elastic deformation remains extremely small. These characteristics make crossed roller bearings particularly suitable for semiconductor robots, precision inspection platforms, and autonomous mobile robots requiring highly repeatable positioning.

Angular contact ball bearings represent another widely adopted solution, especially for medium-payload industrial robots. These bearings are capable of supporting combined radial and axial loads while maintaining relatively low rotational friction. By mounting two angular contact bearings in back-to-back or face-to-face arrangements, designers obtain significantly improved moment stiffness and steering accuracy. Their relatively compact size and moderate cost make them attractive for warehouse logistics robots and general industrial automation systems.

Tapered roller bearings are frequently selected for heavy-duty steer-drive platforms because they possess exceptionally high load-carrying capability. The conical geometry of the rollers enables simultaneous transmission of radial and axial forces while maintaining excellent structural rigidity. Proper preload adjustment is particularly important because insufficient preload increases steering compliance whereas excessive preload generates unnecessary friction, heat generation, and bearing wear.

Bearing preload is one of the most influential design parameters regardless of bearing type. Proper preload eliminates internal clearance, increases stiffness, and improves steering repeatability. However, excessive preload increases rolling resistance and operating temperature while shortening bearing life. Engineers therefore carefully determine preload through analytical calculations, experimental testing, and finite element simulation to achieve an optimal balance between stiffness and durability.

Environmental conditions strongly influence bearing selection. Indoor logistics robots typically operate under relatively clean conditions and may employ standard sealed grease-lubricated bearings. Outdoor autonomous vehicles, agricultural robots, and mining equipment require enhanced sealing systems capable of preventing water, dust, mud, and chemical contaminants from entering the bearing assembly. Multi-stage sealing arrangements, labyrinth seals, and corrosion-resistant bearing materials significantly improve long-term reliability in harsh operating environments.

Lubrication strategy also contributes directly to steering performance. High-quality grease lubrication provides long maintenance intervals while minimizing leakage and contamination. Grease viscosity must remain suitable across the expected operating temperature range to maintain stable rolling resistance. Some heavy-duty steer-drive systems additionally employ centralized lubrication systems that periodically replenish bearing lubricant during operation.

Finite Element Analysis is widely employed during steering bearing selection to predict structural deformation under combined loading. Simulation verifies bearing housing stiffness, shaft deflection, contact stress distribution, and preload sensitivity before physical prototypes are manufactured. Dynamic simulation further evaluates bearing response during repeated steering reversals, vibration excitation, and impact loading.

The final bearing selection represents a compromise among stiffness, load capacity, rotational friction, durability, cost, packaging constraints, and maintenance requirements. By carefully matching bearing characteristics to the operational demands of the steer-drive module, designers ensure accurate steering control, long service life, reduced maintenance requirements, and reliable multidirectional mobility throughout the operational lifetime of the autonomous mobile robot.

---

### 3.2 Drive Axis Bearing Load Calculation

The drive axis bearing supports the rotating drive shaft and transfers all propulsion forces between the gearbox and the wheel. Unlike steering bearings, which primarily support steering motion, drive axis bearings continuously experience high rotational speeds while simultaneously carrying vehicle weight, traction forces, braking loads, and dynamic impact loads. Accurate load calculation therefore forms the foundation for reliable bearing selection and long-term drivetrain durability.

The loading analysis begins by identifying all external forces acting upon the drive wheel. The static radial load primarily originates from the combined weight of the vehicle chassis, payload, batteries, sensors, and auxiliary equipment. Assuming uniform weight distribution across four wheels, the nominal radial load acting on each bearing may be approximated by

[

F_r=\\frac{W}{4}

]

where (W) denotes the total vehicle weight including payload.

Real operating conditions rarely produce perfectly uniform loading. Vehicle acceleration, braking, cornering, uneven floor surfaces, and payload eccentricity generate dynamic load transfer that substantially increases bearing loading on individual wheels. Consequently, dynamic load factors are introduced to account for these additional forces. The design radial load therefore becomes

[

F_{rd}=K_dF_r

]

where (K_d) represents the dynamic load factor determined from vehicle operating conditions.

Traction force generated during vehicle acceleration produces additional tangential loading at the wheel-ground interface. This traction force is calculated as

[

F_t=\\frac{T}{r}

]

where (T) denotes wheel driving torque and (r) represents effective wheel radius. During rapid acceleration or hill climbing, these traction forces substantially increase bearing loading through shaft bending moments and gearbox reactions.

Braking introduces similar but opposite loading conditions. During regenerative or mechanical braking, torque reverses direction while maintaining comparable magnitude. Bearings must therefore safely withstand repeated load reversals throughout the operational lifetime of the vehicle without developing excessive fatigue damage.

Combined radial and axial loading is represented by the equivalent dynamic bearing load

[

P=XF_r+YF_a

]

where (F_r) denotes radial load, (F_a) represents axial load, and (X) and (Y) are bearing-specific load coefficients provided by bearing manufacturers. This equivalent load simplifies fatigue calculations by representing complex multidirectional loading with a single design parameter.

Shaft deflection significantly influences bearing loading. Excessive shaft bending produces uneven load distribution across rolling elements, increasing localized contact stress and reducing bearing life. Finite Element Analysis is therefore routinely employed to evaluate shaft stiffness, bearing spacing, housing rigidity, and wheel overhang geometry. Optimizing these structural parameters minimizes bending deflection and improves bearing load distribution.

Shock loading requires additional consideration for industrial autonomous mobile robots operating over expansion joints, floor irregularities, loading ramps, or outdoor terrain. Impact loads may considerably exceed nominal operating loads for short durations. Appropriate application factors and safety margins are therefore incorporated into bearing calculations to ensure reliable operation under transient overload conditions.

Bearing arrangement strongly affects load distribution. Fixed-floating bearing arrangements accommodate thermal expansion while preventing excessive axial preload. Alternatively, paired angular contact bearings provide greater moment stiffness for applications requiring exceptional positioning accuracy. The selection depends upon shaft length, thermal behavior, expected load distribution, and assembly constraints.

Lubrication influences effective load capacity by reducing friction and preventing surface fatigue. Proper lubricant film thickness separates rolling elements from raceways, minimizing wear and reducing contact stress. Inadequate lubrication significantly accelerates fatigue failure even when calculated bearing loads remain within acceptable design limits.

Modern drive modules increasingly incorporate sensor-based load monitoring. Motor current estimation, vibration monitoring, temperature measurement, and shaft speed analysis enable indirect estimation of bearing loading during operation. These measurements support predictive maintenance strategies by identifying abnormal loading conditions before mechanical damage develops.

Accurate drive axis bearing load calculation therefore requires simultaneous consideration of static loading, dynamic loading, traction forces, braking forces, shaft deformation, lubrication, thermal effects, and transient overload conditions. Comprehensive analysis ensures reliable bearing performance while minimizing unnecessary oversizing, weight, and cost.

---

### 3.3 Service Life Calculation (L10)

Bearing service life is one of the most important reliability indicators for steer-drive modules because bearing replacement often requires partial disassembly of the drive system and may result in significant production downtime. To ensure dependable long-term operation, bearing manufacturers and machine designers commonly evaluate fatigue life using the internationally standardized L10 bearing life calculation. The L10 life represents the number of revolutions that ninety percent of a statistically identical bearing population is expected to achieve before the first evidence of rolling fatigue occurs under specified operating conditions.

The basic rating life equation defined by international bearing standards is expressed as

[

L_{10}

======

\\left(\\frac{C}{P}\\right)\^p

\\times10\^6

]

where (C) denotes the basic dynamic load rating supplied by the bearing manufacturer, (P) represents the equivalent dynamic bearing load, and (p) equals three for ball bearings or ten-thirds for roller bearings.

This equation illustrates the strong relationship between applied load and bearing life. Because bearing life varies according to a power function of load, relatively small reductions in operating load produce substantial increases in expected service life. Conversely, modest overload conditions may dramatically shorten bearing lifetime.

For practical engineering applications, service life is often expressed in operating hours rather than total revolutions. The conversion is performed using

[

L_{10h}

=======

\\frac{L_{10}}

{60n}

]

where (n) denotes rotational speed in revolutions per minute. This representation allows direct comparison between calculated bearing life and expected robot operating schedules.

Modern industrial bearing calculations frequently incorporate life modification factors accounting for lubrication quality, contamination level, material cleanliness, operating temperature, and bearing reliability requirements. The modified life equation becomes

[

L_{nm}

======

a_1a_2a_3L_{10}

]

where the correction factors compensate for operating conditions differing from ideal laboratory assumptions.

Lubrication quality has particularly strong influence on bearing life. Proper elastohydrodynamic lubrication separates rolling surfaces and minimizes direct metal-to-metal contact. Contaminated lubricant or inadequate film thickness substantially accelerates surface fatigue and wear. Consequently, sealed bearing assemblies, effective filtration, and appropriate grease selection contribute directly to increased service life.

Temperature also affects fatigue performance. Elevated operating temperatures reduce lubricant viscosity while accelerating oxidation and grease degradation. Thermal expansion may additionally alter bearing preload, increasing rolling resistance and contact stress. Thermal analysis therefore complements life calculations to ensure acceptable operating temperatures throughout prolonged industrial operation.

Bearing contamination constitutes another major life-limiting factor. Dust, metallic particles, moisture, and chemical contaminants damage rolling surfaces through abrasive wear and corrosion. High-performance sealing systems, labyrinth seals, and clean assembly procedures significantly improve achievable bearing life in industrial environments.

Variable operating conditions require cumulative fatigue evaluation rather than relying on a single equivalent load. Industrial autonomous mobile robots continuously alternate among acceleration, constant-speed travel, braking, turning, docking, and idle periods. Damage accumulation models combine these different operating conditions into an equivalent fatigue load that more accurately predicts long-term bearing performance.

Predictive maintenance increasingly complements theoretical life calculations. Vibration analysis detects early fatigue damage, temperature monitoring identifies lubrication deterioration, acoustic emission reveals surface defects, and motor current analysis indicates increasing rolling resistance. Together, these monitoring techniques allow maintenance to be scheduled before catastrophic bearing failure occurs.

Design engineers generally specify bearing service lives substantially exceeding the expected operational lifetime of the robot. High-duty industrial autonomous mobile robots frequently target bearing lives exceeding twenty thousand to forty thousand operating hours depending upon application severity. Conservative life design minimizes maintenance requirements while improving overall fleet availability and reducing total lifecycle cost.

The L10 calculation therefore provides a standardized engineering framework linking bearing selection, load analysis, lubrication, operating conditions, and maintenance planning. Although simplified compared with actual industrial operation, it remains one of the most valuable design tools for ensuring the long-term reliability and operational efficiency of modern Four-Wheel Steering steer-drive mobile robots.

다음은 앞서 작성한 영어 내용을 자연스럽고 기술 서적에 적합한 한국어로 번역한 내용입니다. 기술 용어는 가능한 한 **한글(영어)** 형식으로 표기하였으며, 설명형 문장으로 구성하였습니다. 글머리표와 번호 매기기는 최소화하였습니다.

---

### 3.1 조향축 베어링 선정 (Steering Axis Bearing Selection)

조향축 베어링(Steering Axis Bearing)은 **4륜 조향(4WS, Four-Wheel Steering)** 스티어 드라이브(Steer Drive) 모듈에서 가장 중요한 기계 요소 가운데 하나이다. 이 베어링은 조향 모듈 전체를 지지하면서 지속적으로 변화하는 하중 아래에서도 조향축이 부드럽고 정확하게 회전할 수 있도록 한다. 일반 자동차의 조향 시스템은 비교적 간헐적으로 조향이 이루어지지만, 산업용 자율주행 이동로봇(AMR)은 지속적인 조향, 크랩 주행(Crab Motion), 제자리 회전(Zero Radius Rotation), 대각선 이동(Diagonal Motion) 등 다양한 방향 전환을 반복적으로 수행한다. 따라서 조향축 베어링은 높은 반경 하중(Radial Load), 축방향 하중(Axial Load), 전복 모멘트(Overturning Moment), 충격 하중(Impact Load) 및 반복적인 진동 하중을 견디면서도 낮은 마찰과 작은 변형, 그리고 긴 수명을 동시에 제공해야 한다.

조향축 베어링을 선정하기 위해서는 먼저 조향축에 작용하는 하중을 정확하게 분석해야 한다. 주요 하중은 차량과 적재물의 무게에 의해 발생하는 **반경 하중(Radial Load)**, 조향 동작과 노면의 불균형으로 발생하는 **축방향 하중(Axial Load)**, 그리고 가속·감속·회전 및 적재물의 편심에 의해 발생하는 **전복 모멘트(Overturning Moment)**이다. 실제 산업 환경에서는 이러한 하중이 개별적으로 작용하는 것이 아니라 동시에 복합적으로 발생하므로, 베어링은 복합 하중(Combined Load)을 충분히 견딜 수 있어야 한다.

고정밀 스티어 드라이브 모듈에서는 **크로스 롤러 베어링(Crossed Roller Bearing)**이 가장 많이 사용된다. 크로스 롤러 베어링은 원통형 롤러가 서로 직각 방향으로 교차 배열되어 있어 하나의 베어링만으로 반경 하중, 양방향 축방향 하중 및 전복 모멘트를 모두 지지할 수 있다. 또한 롤러와 레이스(Raceway)가 선 접촉(Line Contact)을 이루므로 강성이 매우 높고 탄성 변형이 작다. 이러한 특성 덕분에 반도체 운반 로봇, 정밀 검사 장비 및 고정밀 AMR에서 널리 적용된다.

중형 산업용 AMR에서는 **앵귤러 콘택트 볼 베어링(Angular Contact Ball Bearing)**도 많이 사용된다. 이 베어링은 반경 하중과 축방향 하중을 동시에 지지할 수 있으며 회전 마찰이 비교적 작다. 두 개의 앵귤러 콘택트 베어링을 **백투백(Back-to-Back)** 또는 **페이스투페이스(Face-to-Face)** 형태로 배치하면 전복 모멘트에 대한 강성이 크게 향상되어 조향 정밀도가 높아진다. 크기가 비교적 작고 가격이 합리적이므로 물류 AMR이나 일반 산업 자동화 장비에서 많이 사용된다.

중량급 플랫폼에서는 **테이퍼 롤러 베어링(Tapered Roller Bearing)**이 자주 사용된다. 원뿔 형태의 롤러 구조 덕분에 매우 높은 반경 하중과 축방향 하중을 동시에 지지할 수 있으며 구조 강성이 뛰어나다. 다만 프리로드(Preload) 설정이 매우 중요하다. 프리로드가 부족하면 조향 유격이 증가하고, 지나치게 크면 마찰과 발열이 증가하여 베어링 수명이 단축될 수 있다.

베어링의 프리로드는 모든 베어링 형식에서 매우 중요한 설계 변수이다. 적절한 프리로드는 내부 유격을 제거하고 강성을 높이며 반복 위치 정밀도를 향상시킨다. 그러나 과도한 프리로드는 구름 저항(Rolling Resistance)과 온도를 증가시키고 피로 수명을 감소시킨다. 따라서 설계자는 계산, 실험 및 **유한요소해석(Finite Element Analysis, FEA)**을 통해 강성과 내구성 사이의 최적 균형을 결정한다.

사용 환경(Environment)도 베어링 선정에 큰 영향을 미친다. 실내 물류 로봇은 비교적 깨끗한 환경에서 동작하므로 밀폐형 그리스 윤활 베어링으로 충분한 경우가 많다. 반면 실외 자율주행 차량, 농업 로봇 및 광산 장비는 먼지, 물, 진흙 및 화학 물질로부터 베어링을 보호하기 위한 다단 씰(Multi-stage Seal), 라비린스 씰(Labyrinth Seal) 및 부식 방지 재질이 필요하다.

윤활(Lubrication)은 조향 성능과 수명을 결정하는 중요한 요소이다. 고품질 그리스는 긴 유지보수 주기를 제공하며 윤활유 누설과 오염을 방지한다. 또한 작동 온도 범위에서 적절한 점도(Viscosity)를 유지해야 안정적인 회전 성능을 확보할 수 있다. 일부 중량급 시스템에서는 중앙 집중식 윤활(Centralized Lubrication)을 적용하여 주기적으로 윤활제를 공급하기도 한다.

설계 과정에서는 **유한요소해석(FEA)**을 이용하여 복합 하중에서 베어링 하우징의 변형, 축의 처짐(Shaft Deflection), 접촉 응력(Contact Stress) 및 프리로드 민감도를 분석한다. 또한 동적 해석(Dynamic Simulation)을 통해 반복적인 조향 전환, 진동 및 충격 하중에 대한 성능도 검증한다.

결국 조향축 베어링 선정은 강성(Stiffness), 하중 지지 능력(Load Capacity), 회전 마찰(Rotational Friction), 내구성(Durability), 비용(Cost), 설치 공간(Packaging) 및 유지보수성을 종합적으로 고려하는 과정이다. 적절한 베어링을 선택함으로써 스티어 드라이브 모듈은 높은 조향 정밀도와 긴 수명, 낮은 유지보수 비용 및 안정적인 전방향 이동 성능을 확보할 수 있다.

---

### 3.2 구동축 베어링 하중 계산 (Drive Axis Bearing Load Calculation)

구동축 베어링(Drive Axis Bearing)은 회전하는 구동축을 지지하면서 감속기에서 발생한 구동력을 바퀴로 전달하는 핵심 부품이다. 조향축 베어링이 주로 조향 운동을 담당하는 반면, 구동축 베어링은 차량의 무게, 추진력, 제동력 및 반복적인 충격 하중을 지속적으로 받으면서 높은 회전 속도로 운전된다. 따라서 정확한 하중 계산은 베어링 선정과 구동계의 장기적인 신뢰성을 확보하기 위한 가장 중요한 설계 과정이다.

하중 계산은 먼저 바퀴에 작용하는 외력을 분석하는 것부터 시작된다. 가장 기본적인 하중은 차량 차체, 배터리, 적재물, 센서 및 기타 장비의 무게에 의해 발생하는 **정적 반경 하중(Static Radial Load)**이다. 차량의 무게가 네 개의 바퀴에 균등하게 분배된다고 가정하면 각 베어링에 작용하는 반경 하중은 다음과 같이 근사적으로 계산할 수 있다.

[

F_r=\\frac{W}{4}

]

여기서 (W)는 적재물을 포함한 차량 전체의 총중량(Total Vehicle Weight)을 의미한다.

그러나 실제 산업 환경에서는 하중이 항상 균등하게 분포하지 않는다. 차량의 가속, 감속, 회전, 노면의 요철 및 적재물의 편심은 특정 바퀴에 더 큰 하중을 발생시킨다. 따라서 실제 설계에서는 동적 하중 계수(Dynamic Load Factor)를 적용하여 설계 하중을 계산한다.

[

F_{rd}=K_dF_r

]

여기서 (K_d)는 운전 조건에 따라 결정되는 동적 하중 계수이다.

차량이 가속하면 바퀴는 추진력을 발생시키며, 이 힘은

[

F_t=\\frac{T}{r}

]

로 계산된다.

여기서

\* (T) : 바퀴 구동 토크(Wheel Driving Torque)

\* (r) : 유효 바퀴 반경(Effective Wheel Radius)

이다.

급가속이나 경사면 주행에서는 이러한 추진력이 베어링의 굽힘 모멘트(Bending Moment)와 감속기 반력을 증가시켜 베어링 하중을 크게 증가시킨다.

제동 시에도 유사한 현상이 발생한다. 회생 제동(Regenerative Braking)이나 기계식 브레이크(Mechanical Brake)는 동일한 크기의 반대 방향 토크를 발생시키므로 베어링은 반복적인 하중 반전을 장기간 견뎌야 한다.

반경 하중과 축방향 하중이 동시에 작용하는 경우에는 **등가 동적 하중(Equivalent Dynamic Load)**을 사용한다.

[

P=XF_r+YF_a

]

여기서

\* (F_r) : 반경 하중

\* (F_a) : 축방향 하중

\* (X, Y) : 베어링 제조사가 제공하는 계수

이다.

이 식은 복잡한 복합 하중을 하나의 설계 하중으로 변환하여 피로 수명 계산을 단순화한다.

구동축의 처짐(Shaft Deflection)도 중요한 요소이다. 축이 크게 휘어지면 롤러에 하중이 균일하게 분포하지 않아 접촉 응력이 증가하고 베어링 수명이 감소한다. 따라서 **유한요소해석(FEA)**을 이용하여 축의 강성, 베어링 간격, 하우징 강성 및 휠 오버행(Wheel Overhang)을 최적화한다.

충격 하중(Shock Load)도 반드시 고려해야 한다. 산업용 AMR은 바닥 이음새, 경사로 및 실외 노면을 통과하면서 순간적으로 매우 큰 충격을 받는다. 이러한 하중은 정상 운전 하중보다 훨씬 클 수 있으므로 설계 시에는 충분한 안전율(Safety Factor)을 적용한다.

베어링의 배치 방식(Bearing Arrangement)도 하중 분포에 영향을 준다. **고정-부동(Fixed-Floating)** 구조는 열팽창을 허용하면서 과도한 축방향 하중을 방지한다. 반면 한 쌍의 앵귤러 콘택트 베어링은 높은 모멘트 강성을 제공하여 정밀 위치 제어에 적합하다.

윤활 상태도 하중 지지 능력에 직접적인 영향을 미친다. 적절한 윤활유 막(Lubrication Film)은 금속 간 직접 접촉을 방지하고 마찰과 마모를 감소시킨다. 윤활이 부족하면 계산상 허용 하중 이내에서도 피로 파손(Fatigue Failure)이 빠르게 진행될 수 있다.

최근의 구동 모듈은 센서를 이용한 하중 모니터링(Load Monitoring)도 지원한다. 모터 전류, 진동, 온도 및 회전 속도를 분석하여 실제 베어링 하중을 간접적으로 추정하고, 비정상적인 하중 상태를 조기에 발견하여 예지보전(Predictive Maintenance)에 활용한다.

결국 구동축 베어링 하중 계산은 정적 하중, 동적 하중, 추진력, 제동력, 축 변형, 윤활 상태, 열 영향 및 충격 하중을 모두 종합적으로 고려해야 한다. 이러한 종합적인 해석을 통해 불필요한 과대 설계를 방지하면서도 높은 신뢰성과 긴 수명을 확보할 수 있다.

---

### 3.3 서비스 수명 계산(L10) (Service Life Calculation, L10)

베어링 서비스 수명(Service Life)은 스티어 드라이브 모듈의 신뢰성을 평가하는 가장 중요한 지표 가운데 하나이다. 베어링을 교체하려면 구동 모듈을 상당 부분 분해해야 하므로 유지보수 시간과 생산 중단 시간이 크게 증가할 수 있다. 따라서 설계 단계에서는 국제적으로 표준화된 **L10 수명(L10 Bearing Life)** 계산을 이용하여 베어링의 피로 수명을 예측한다.

**L10 수명**이란 동일한 조건에서 사용되는 동일한 베어링 집단 가운데 **90%의 베어링이 최초의 피로 손상이 발생하기 전까지 회전할 것으로 기대되는 회전수**를 의미한다.

국제 표준에서 사용하는 기본 수명 식은 다음과 같다.

[

L_{10}

======

\\left(\\frac{C}{P}\\right)\^p

\\times10\^6

]

여기서

\* (C) : 기본 동적 하중 정격(Basic Dynamic Load Rating)

\* (P) : 등가 동적 하중(Equivalent Dynamic Load)

\* (p) : 볼 베어링은 3, 롤러 베어링은 10/3

이다.

이 식은 **하중이 조금만 증가해도 베어링 수명이 급격히 감소한다**는 사실을 보여준다. 반대로 운전 하중을 조금만 줄여도 수명은 크게 증가한다.

실제 설계에서는 총 회전수보다 **운전 시간(Operating Hours)**으로 표현하는 경우가 많다.

[

L_{10h}

=======

\\frac{L_{10}}

{60n}

]

여기서 (n)은 회전 속도(rpm)이다.

이 식을 이용하면 계산된 베어링 수명을 실제 로봇의 운전 시간과 직접 비교할 수 있다.

최근에는 윤활 상태, 오염도, 재료 품질, 온도 및 신뢰도 요구사항을 고려한 **수명 보정 계수(Life Modification Factor)**도 함께 사용한다.

[

L_{nm}

======

a_1a_2a_3L_{10}

]

여기서

\* (a_1) : 신뢰도 계수

\* (a_2) : 재료 계수

\* (a_3) : 운전 조건 계수

이다.

윤활 상태는 수명에 가장 큰 영향을 주는 요소 가운데 하나이다. 적절한 **탄성유체윤활(Elastohydrodynamic Lubrication, EHL)**은 금속 간 직접 접촉을 방지하여 피로와 마모를 크게 줄인다. 반대로 오염된 윤활유나 윤활막 부족은 베어링 피로를 매우 빠르게 증가시킨다.

온도도 중요한 요소이다. 높은 온도는 윤활유 점도를 감소시키고 산화를 촉진하며 그리스를 열화시킨다. 또한 열팽창은 프리로드를 변화시켜 접촉 응력을 증가시킬 수 있다. 따라서 장시간 운전에서는 열 해석(Thermal Analysis)을 통해 적절한 운전 온도를 유지해야 한다.

오염(Contamination)은 또 다른 주요 수명 저하 원인이다. 먼지, 금속 입자, 수분 및 화학 물질은 마모와 부식을 유발하므로, 고성능 씰(Seal)과 청정 조립 공정을 통해 이를 최소화해야 한다.

실제 산업용 AMR은 가속, 정속 주행, 감속, 회전, 도킹 및 정지 등 다양한 운전 상태를 반복한다. 따라서 단일 하중만을 이용한 계산보다 **누적 피로 손상(Damage Accumulation)**을 고려한 등가 하중 계산이 더욱 정확한 수명 예측을 제공한다.

최근에는 **예지보전(Predictive Maintenance)**이 L10 계산을 보완하고 있다. 진동 분석(Vibration Analysis)은 초기 피로 손상을 검출하고, 온도 모니터링은 윤활 상태를 확인하며, 음향 방출(Acoustic Emission)은 표면 결함을 감지한다. 또한 모터 전류 분석은 구름 저항 증가를 확인하여 베어링 이상을 조기에 발견할 수 있다.

산업용 AMR에서는 일반적으로 **20,000\~40,000시간 이상의 베어링 수명**을 목표로 설계하며, 사용 환경이 가혹할수록 더 높은 안전율을 적용한다. 이러한 보수적인 설계는 유지보수 비용을 줄이고 전체 로봇 시스템의 가동률(Availability)을 크게 향상시킨다.

결국 **L10 수명 계산은 베어링 선정, 하중 계산, 윤활 설계, 운전 조건 및 유지보수 계획을 하나의 공학적 기준으로 연결하는 국제 표준 방법**이다. 실제 산업 환경은 계산보다 훨씬 복잡하지만, L10 수명은 현대 **4륜 조향(4WS)** 스티어 드라이브 이동로봇의 장기적인 신뢰성과 경제성을 확보하기 위한 가장 중요한 설계 도구 가운데 하나로 널리 활용되고 있다.

##  

## 04 Cable management

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 360 Degree Rotation Cable Routing

Cable routing is a fundamental aspect of steer-drive module design because every steering module contains multiple electrical connections that must remain reliable while the wheel continuously rotates. Unlike conventional drive systems where wheel orientation changes only within a limited steering angle, a Four-Wheel Steering (4WS) steer-drive module may rotate through 360 degrees repeatedly during omnidirectional motion, crab driving, zero-radius turning, and autonomous docking. Consequently, the cable management system must be designed not only to transmit electrical power and communication signals but also to accommodate unlimited rotational movement without introducing excessive mechanical stress, signal degradation, or premature cable failure. Cable routing therefore becomes an integral part of the overall mechanical architecture rather than a secondary packaging consideration.

The first objective of a 360-degree cable routing system is to maintain continuous electrical connectivity while allowing unrestricted steering motion. Every steering module typically contains power cables for the drive motor, steering motor, electromagnetic brake, cooling devices, and auxiliary actuators. In addition, numerous low-voltage communication lines connect absolute encoders, incremental encoders, temperature sensors, vibration sensors, current sensors, and diagnostic electronics to the vehicle control system. Industrial communication networks such as EtherCAT, CANopen, or Ethernet-based fieldbus systems require stable signal integrity even while steering modules continuously rotate. Therefore, cable routing must preserve electrical performance under repeated mechanical deformation.

Several engineering solutions are commonly employed depending on the steering architecture. The simplest approach limits steering rotation to less than one complete revolution, allowing cables to form controlled service loops inside the steering housing. Carefully calculated loop geometry distributes bending over a relatively large radius, preventing localized strain while allowing repeated steering motion. Mechanical rotation stops are incorporated to prevent excessive cable twisting beyond the designed operating range. This solution is economical and reliable for robots that do not require unlimited steering rotation.

For applications requiring continuous 360-degree steering, rotary electrical interfaces become necessary. Slip rings are among the most widely adopted technologies. A slip ring transfers electrical power and communication signals through stationary brushes contacting rotating conductive rings. This arrangement completely eliminates cable twisting because electrical continuity is maintained through the rotating interface rather than through flexible conductors. Modern industrial slip rings support power transmission, high-speed Ethernet communication, encoder signals, CAN communication, and even optical fiber channels within a compact assembly. Gold-to-gold contact materials are frequently selected for low-noise signal transmission, while advanced sealing systems protect internal contacts from dust and moisture.

Another increasingly popular solution is the use of hollow-shaft steering motors with centrally routed cable passages. In this architecture, cables pass directly through the hollow steering axis and follow a carefully controlled helical routing path inside the rotating module. The large bending radius significantly reduces mechanical stress while maintaining a compact module geometry. This configuration is particularly attractive for high-precision industrial robots where minimizing module size and reducing component count are important design objectives.

Cable routing geometry must satisfy minimum bending radius requirements specified by cable manufacturers. Excessively tight bending increases conductor strain, damages insulation layers, and accelerates fatigue failure. Dynamic robotic cables typically require bending radii several times larger than the cable diameter, depending upon conductor construction and operating cycle requirements. Routing channels therefore incorporate smooth curved surfaces rather than sharp corners, ensuring uniform strain distribution throughout repeated steering motion.

Cable separation also plays an important role in maintaining signal quality. High-current motor power cables generate electromagnetic interference that may corrupt low-level encoder or communication signals if routed too closely together. Consequently, power cables and signal cables are physically separated whenever possible, and additional electromagnetic shielding is employed for particularly sensitive communication channels. Twisted-pair conductors, braided shields, and grounded metallic conduits further improve electromagnetic compatibility within the steer-drive module.

Mechanical protection is equally important. Cable routing channels shield conductors from moving mechanical components, debris, sharp edges, and accidental maintenance damage. Flexible protective conduits, energy chains, spiral wraps, and abrasion-resistant sleeves prevent insulation wear while allowing unrestricted cable movement. Strain relief devices positioned at both ends of each cable prevent tensile loads from being transferred directly into electrical connectors during repeated steering motion.

The cable routing design process increasingly relies upon three-dimensional CAD modeling and dynamic simulation. Virtual motion analysis evaluates cable deformation throughout the entire steering range, identifying potential interference, excessive curvature, or localized stress concentration before physical prototypes are constructed. Finite element analysis may additionally estimate strain distribution within cable conductors, enabling engineers to optimize routing geometry for maximum fatigue life.

As autonomous mobile robots become increasingly sophisticated, cable routing evolves from simple wire management into a multidisciplinary engineering challenge involving mechanical design, electrical engineering, electromagnetic compatibility, reliability engineering, and maintenance optimization. A properly designed 360-degree cable routing system ensures uninterrupted power delivery, stable communication, long operational life, and reliable multidirectional mobility throughout the demanding service conditions encountered in modern industrial automation.

---

### 4.2 Cable Durability Design

Cable durability is one of the most important reliability considerations in steer-drive module development because flexible electrical cables experience continuous mechanical deformation throughout the operational lifetime of an autonomous mobile robot. Unlike stationary industrial machinery where cables remain essentially fixed after installation, steer-drive systems repeatedly bend, twist, accelerate, decelerate, and vibrate during every steering motion. Over millions of steering cycles, even relatively small mechanical stresses accumulate into conductor fatigue, insulation degradation, connector loosening, and eventual electrical failure if cable durability is not carefully engineered. Consequently, cable durability design represents a critical aspect of long-term system reliability.

The primary failure mechanism of dynamic robotic cables is cyclic fatigue within the copper conductors. Every steering movement produces repeated bending and torsional deformation that gradually introduces microscopic cracks into individual conductor strands. Conventional industrial cables employing relatively large solid conductors cannot tolerate this repeated deformation and therefore exhibit limited service life. Dynamic robotic cables instead utilize extremely fine multi-strand copper conductors that distribute bending strain among many individual wires. This construction significantly improves flexibility while reducing localized mechanical stress.

Conductor material selection further influences fatigue resistance. High-purity oxygen-free copper provides excellent electrical conductivity together with superior ductility, allowing repeated bending without premature fracture. Some high-performance robotic cables additionally employ specially annealed copper alloys that further improve fatigue endurance while maintaining low electrical resistance. Strand geometry, conductor diameter, and lay length are carefully optimized according to expected bending cycles and steering motion characteristics.

Insulation materials must withstand both mechanical deformation and harsh industrial environments. Thermoplastic polyurethane is widely used because of its excellent abrasion resistance, flexibility, oil resistance, and low-temperature performance. Cross-linked polyethylene and specialized elastomer compounds are also employed depending upon temperature range and chemical exposure. Multi-layer insulation systems combine mechanical protection with electrical isolation, ensuring reliable long-term operation even under demanding environmental conditions.

Cable jackets provide the first level of mechanical protection against external damage. High-quality outer jackets resist abrasion, cutting, chemical exposure, moisture, ultraviolet radiation, and repeated contact with surrounding mechanical structures. Smooth low-friction jacket materials additionally reduce wear as cables slide within routing channels during steering motion. Flame-retardant materials are frequently specified to satisfy industrial safety standards while maintaining flexibility.

Strain relief design significantly affects connector reliability. Without appropriate strain relief, repeated cable motion transfers mechanical loads directly into electrical terminals, eventually causing connector loosening or conductor breakage. Molded strain relief boots, flexible cable clamps, and progressive bending supports distribute mechanical loads gradually over longer cable sections, minimizing stress concentration near connector interfaces.

Environmental protection becomes increasingly important for outdoor autonomous vehicles. Water ingress, dust contamination, temperature cycling, chemicals, and ultraviolet exposure accelerate cable degradation if protective measures are insufficient. Industrial robotic cables therefore frequently satisfy IP67 or higher environmental protection ratings while maintaining flexibility across wide temperature ranges extending from subzero winter conditions to elevated summer operating temperatures.

Thermal durability must also be considered. Drive motors, steering motors, power electronics, and braking systems generate significant heat during continuous industrial operation. Elevated temperatures accelerate insulation aging and reduce conductor fatigue life. Consequently, cable routing avoids direct contact with high-temperature components whenever possible, while heat-resistant insulation materials are employed in critical areas. Thermal simulation assists engineers in identifying potential hot spots during the design stage.

Mechanical vibration represents another important durability challenge. Continuous vibration generated by drive motors, gearbox meshing, floor irregularities, and payload movement produces additional cyclic loading beyond steering motion alone. Cable supports therefore incorporate vibration-damping features while maintaining sufficient flexibility to accommodate steering movement without excessive constraint.

Durability verification requires extensive laboratory testing. Dynamic bending machines repeatedly cycle robotic cables through millions of bending motions under representative loads and environmental conditions. Torsional fatigue testing evaluates resistance to repeated twisting, while temperature cycling, humidity exposure, salt spray testing, and chemical compatibility testing verify long-term environmental durability. Electrical continuity monitoring throughout these tests identifies early conductor degradation before complete failure occurs.

Predictive maintenance is increasingly integrated into cable durability management. Continuous monitoring of electrical resistance, insulation integrity, communication quality, and connector condition allows maintenance personnel to identify developing cable degradation before operational failures occur. Combined with accurate cycle counting and digital maintenance records, these diagnostic capabilities significantly improve fleet availability while reducing unexpected downtime.

Modern cable durability design therefore extends far beyond simple conductor selection. It integrates advanced materials engineering, mechanical fatigue analysis, environmental protection, thermal management, connector technology, structural routing optimization, laboratory validation, and predictive diagnostics into a comprehensive reliability strategy. Through careful optimization of these factors, steer-drive autonomous mobile robots can achieve millions of steering cycles while maintaining stable electrical performance, high operational reliability, and low lifecycle maintenance costs in demanding industrial environments.

### 4.1 360도 회전 케이블 배선 (360 Degree Rotation Cable Routing)

케이블 배선(Cable Routing)은 스티어 드라이브(Steer Drive) 모듈 설계에서 매우 중요한 요소이다. 모든 조향 모듈(Steering Module)은 여러 개의 전기적 연결을 포함하고 있으며, 휠이 지속적으로 회전하는 동안에도 이 연결은 항상 안정적으로 유지되어야 한다. 일반적인 차량은 조향각이 제한되어 있어 케이블의 움직임이 비교적 단순하지만, **4륜 조향(4WS, Four-Wheel Steering)** 스티어 드라이브 모듈은 전방향 이동(Holonomic Motion), 크랩 주행(Crab Motion), 제자리 회전(Zero Radius Rotation), 자율 도킹(Autonomous Docking) 등을 수행하면서 조향축이 반복적으로 **360도 이상 연속 회전**할 수 있다. 따라서 케이블 관리 시스템(Cable Management System)은 단순히 전력과 신호를 전달하는 기능을 넘어, 지속적인 회전 운동에서도 기계적 응력(Mechanical Stress), 신호 품질 저하(Signal Degradation) 및 케이블 피로(Fatigue Failure)가 발생하지 않도록 설계되어야 한다. 즉, 케이블 배선은 기계 구조의 부속 요소가 아니라 조향 모듈 설계의 핵심 요소 가운데 하나이다.

360도 회전 케이블 배선의 첫 번째 목적은 **무제한 회전(Unlimited Rotation)** 동안에도 안정적인 전기 연결을 유지하는 것이다. 하나의 조향 모듈에는 일반적으로 구동 모터(Drive Motor), 조향 모터(Steering Motor), 전자기 브레이크(Electromagnetic Brake), 냉각 장치(Cooling Device) 및 기타 액추에이터에 전력을 공급하는 전원 케이블이 포함된다. 또한 절대형 엔코더(Absolute Encoder), 증분형 엔코더(Incremental Encoder), 온도 센서(Temperature Sensor), 진동 센서(Vibration Sensor), 전류 센서(Current Sensor) 및 진단 장치(Diagnostic Electronics)를 연결하는 저전압 신호선도 함께 존재한다. EtherCAT, CANopen 및 Ethernet 기반 산업용 필드버스(Fieldbus)는 조향 모듈이 지속적으로 회전하는 동안에도 안정적인 통신 품질을 유지해야 하므로, 케이블은 반복적인 기계적 변형에도 신호 품질이 저하되지 않아야 한다.

조향 구조에 따라 다양한 케이블 배선 방식이 사용된다. 가장 단순한 방식은 조향각을 한 바퀴 이하로 제한하는 구조이다. 이 경우 케이블은 조향 하우징 내부에서 서비스 루프(Service Loop)를 형성하며 움직인다. 서비스 루프의 형상은 계산을 통해 설계되며, 케이블이 큰 곡률 반경(Bending Radius)을 유지하도록 하여 특정 위치에 응력이 집중되지 않도록 한다. 또한 기계식 회전 스토퍼(Mechanical Rotation Stop)를 설치하여 케이블이 설계 범위를 초과하여 꼬이지 않도록 한다. 이 방식은 구조가 단순하고 경제적이며, 연속 회전이 필요하지 않은 산업용 로봇에서 널리 사용된다.

반면 **360도 연속 회전**이 필요한 경우에는 **회전 전기 인터페이스(Rotary Electrical Interface)**가 필요하다. 가장 일반적인 방법은 **슬립 링(Slip Ring)**이다. 슬립 링은 고정된 브러시(Brush)와 회전하는 전도 링(Conductive Ring)의 접촉을 통해 전력과 통신 신호를 전달한다. 따라서 케이블 자체는 꼬이지 않고, 회전 인터페이스를 통해 전기 연결이 유지된다. 최신 산업용 슬립 링은 전원뿐 아니라 고속 Ethernet, CAN 통신, 엔코더 신호, 심지어 광섬유(Optical Fiber)까지 하나의 장치에서 전달할 수 있다. 또한 금-금 접점(Gold-to-Gold Contact)을 사용하여 노이즈를 최소화하고, 방진 및 방수 구조를 적용하여 산업 환경에서도 높은 신뢰성을 제공한다.

최근에는 **중공축 조향 모터(Hollow-shaft Steering Motor)**를 사용하는 방식도 증가하고 있다. 이 구조에서는 케이블이 조향축 내부를 통과하며, 내부에서 나선형(Helical Routing)으로 배치된다. 큰 굽힘 반경을 확보할 수 있어 케이블의 기계적 응력을 크게 줄일 수 있으며, 모듈의 크기도 줄일 수 있다. 특히 고정밀 산업용 로봇에서는 부품 수를 줄이고 컴팩트한 구조를 구현하기 위해 많이 채택되고 있다.

케이블 배선 형상은 반드시 제조사가 권장하는 **최소 굽힘 반경(Minimum Bending Radius)**을 만족해야 한다. 굽힘 반경이 너무 작으면 도체에 큰 변형이 발생하여 절연층 손상과 피로 파손이 빠르게 진행된다. 따라서 케이블 가이드(Channel)는 급격한 모서리 대신 부드러운 곡선을 사용하여 반복적인 조향 과정에서도 응력이 균일하게 분포되도록 설계된다.

전원 케이블과 신호 케이블은 가능한 한 서로 분리하여 배치해야 한다. 구동 모터의 고전류는 강한 **전자기 간섭(Electromagnetic Interference, EMI)**을 발생시키며, 엔코더 신호나 통신선과 가까이 배치되면 신호 오류가 발생할 수 있다. 이를 방지하기 위해 꼬임선(Twisted Pair), 편조 실드(Braided Shield), 접지 금속 덕트(Grounded Metallic Conduit) 등을 사용하여 **전자기 적합성(Electromagnetic Compatibility, EMC)**을 확보한다.

기계적 보호(Mechanical Protection)도 중요하다. 케이블은 회전 부품, 날카로운 모서리, 이물질 및 유지보수 작업 중 발생할 수 있는 손상으로부터 보호되어야 한다. 이를 위해 보호 튜브(Protective Conduit), 에너지 체인(Energy Chain), 나선 보호 튜브(Spiral Wrap) 및 내마모 슬리브(Abrasion-resistant Sleeve)를 사용한다. 또한 커넥터 근처에는 **스트레인 릴리프(Strain Relief)**를 설치하여 반복적인 움직임에 의한 인장 하중이 직접 커넥터에 전달되지 않도록 한다.

최근에는 3차원 CAD 모델링과 동적 시뮬레이션(Dynamic Simulation)을 이용하여 케이블의 움직임을 설계 단계에서 검증한다. 가상 환경에서 조향 전 범위의 케이블 변형을 분석하여 간섭, 과도한 굽힘 및 응력 집중을 사전에 발견할 수 있다. 또한 **유한요소해석(Finite Element Analysis, FEA)**을 통해 케이블 내부 도체의 변형을 계산하여 피로 수명을 예측하고 최적의 배선 형상을 결정한다.

결국 360도 회전 케이블 배선은 단순한 전선 정리 작업이 아니라 기계 설계, 전기 설계, **전자기 적합성(EMC)**, 신뢰성 공학(Reliability Engineering) 및 유지보수성(Serviceability)을 모두 포함하는 종합적인 설계 기술이다. 적절하게 설계된 케이블 관리 시스템은 장기간의 산업 환경에서도 전력 공급과 통신 품질을 안정적으로 유지하며, 스티어 드라이브 플랫폼의 높은 신뢰성과 전방향 이동 성능을 보장한다.

---

### 4.2 케이블 내구성 설계 (Cable Durability Design)

케이블 내구성(Cable Durability)은 스티어 드라이브 모듈의 장기적인 신뢰성을 결정하는 가장 중요한 요소 가운데 하나이다. 일반적인 산업 설비에서는 케이블이 설치된 이후 거의 움직이지 않지만, 스티어 드라이브 시스템에서는 모든 조향 동작마다 케이블이 반복적으로 **굽힘(Bending)**, **비틀림(Torsion)**, **가속과 감속**, 그리고 **진동(Vibration)**을 경험한다. 이러한 변형은 수백만 회의 조향 사이클(Steering Cycle) 동안 지속적으로 반복되므로, 적절한 설계가 이루어지지 않으면 도체 피로(Conductor Fatigue), 절연층 열화(Insulation Degradation), 커넥터 풀림(Connector Loosening) 및 최종적인 전기적 단선(Electrical Failure)이 발생하게 된다. 따라서 케이블 내구성은 단순한 재료 선택이 아니라 시스템 전체의 수명을 좌우하는 핵심 설계 요소이다.

동적 로봇 케이블(Dynamic Robotic Cable)에서 가장 일반적인 고장 원인은 **도체 피로(Cyclic Fatigue)**이다. 조향이 이루어질 때마다 구리 도체(Copper Conductor)는 반복적으로 굽혀지고 비틀어지며, 시간이 지나면 미세한 균열(Micro Crack)이 발생한다. 일반 산업용 케이블은 비교적 굵은 도체를 사용하기 때문에 이러한 반복 변형에 약하지만, 로봇용 케이블은 매우 가는 다수의 연선(Fine Multi-strand Conductor)을 사용하여 변형을 여러 가닥으로 분산시킨다. 그 결과 높은 유연성과 긴 피로 수명을 동시에 확보할 수 있다.

도체 재료(Material)도 매우 중요하다. 일반적으로 **무산소 동(Oxygen-free Copper)**은 높은 전기 전도도와 우수한 연성(Ductility)을 제공하므로 반복 굽힘에도 쉽게 파손되지 않는다. 일부 고성능 로봇 케이블은 특수 열처리된 구리 합금(Copper Alloy)을 사용하여 피로 수명을 더욱 향상시킨다. 또한 연선의 굵기, 가닥 수 및 꼬임 길이(Lay Length)는 예상되는 굽힘 횟수와 조향 특성에 맞추어 최적화된다.

절연체(Insulation)는 기계적 변형과 산업 환경을 동시에 견뎌야 한다. **열가소성 폴리우레탄(Thermoplastic Polyurethane, TPU)**은 내마모성(Abrasion Resistance), 유연성(Flexibility), 내유성(Oil Resistance) 및 저온 성능이 우수하여 가장 널리 사용된다. 또한 **가교 폴리에틸렌(Cross-linked Polyethylene, XLPE)**과 특수 엘라스토머(Elastomer)도 사용 환경에 따라 적용된다. 다층 절연 구조(Multi-layer Insulation)는 기계적 보호와 전기 절연을 동시에 제공하여 장기간 안정적인 운전을 가능하게 한다.

외피(Cable Jacket)는 외부 충격으로부터 케이블을 보호하는 첫 번째 방어층이다. 고품질 외피는 마모, 절단, 화학물질, 습기 및 자외선(UV)에 강해야 하며, 반복적으로 케이블 가이드 내부를 이동하면서도 쉽게 마모되지 않아야 한다. 또한 난연성(Flame-retardant) 재료를 사용하여 산업 안전 규격을 만족하면서도 높은 유연성을 유지한다.

**스트레인 릴리프(Strain Relief)** 설계는 커넥터의 신뢰성을 크게 좌우한다. 스트레인 릴리프가 없으면 반복적인 케이블 움직임이 커넥터 단자에 직접 전달되어 단선이나 접촉 불량이 발생한다. 따라서 몰드형 스트레인 릴리프(Molded Strain Relief), 유연한 클램프(Flexible Clamp) 및 점진적 굽힘 구조(Progressive Bending Support)를 적용하여 응력을 긴 구간에 분산시킨다.

실외 자율주행 차량에서는 환경 보호(Environmental Protection)가 더욱 중요하다. 물, 먼지, 화학물질 및 자외선은 케이블을 빠르게 열화시키므로, 일반적으로 **IP67 이상의 보호 등급**을 갖는 케이블을 사용하며, 영하의 겨울부터 고온의 여름까지 넓은 온도 범위에서도 유연성을 유지해야 한다.

열 내구성(Thermal Durability)도 고려해야 한다. 구동 모터, 조향 모터, 전력 전자장치(Power Electronics) 및 브레이크는 많은 열을 발생시키며, 높은 온도는 절연체를 빠르게 노화시킨다. 따라서 케이블은 가능한 한 고온 부품과 직접 접촉하지 않도록 배치하며, 필요에 따라 내열 절연재를 적용한다. 설계 단계에서는 열 해석(Thermal Simulation)을 수행하여 고온 구역(Hot Spot)을 미리 확인한다.

진동(Vibration) 역시 내구성에 큰 영향을 준다. 모터, 감속기 및 노면에서 발생하는 지속적인 진동은 조향에 의한 피로 외에도 추가적인 반복 하중을 발생시킨다. 따라서 케이블 지지 구조는 진동을 흡수하면서도 조향 운동을 방해하지 않도록 설계된다.

내구성 검증(Durability Verification)은 다양한 시험을 통해 수행된다. 반복 굽힘 시험(Bending Test), 비틀림 피로 시험(Torsional Fatigue Test), 온도 사이클 시험(Temperature Cycling), 습도 시험(Humidity Test), 염수 분무 시험(Salt Spray Test) 및 화학물질 내성 시험(Chemical Compatibility Test)을 수행하여 장기간의 산업 환경을 재현한다. 시험 중에는 전기적 연속성(Electrical Continuity)을 지속적으로 측정하여 초기 열화 단계부터 이상을 검출한다.

최근에는 **예지보전(Predictive Maintenance)** 기술도 케이블 관리에 적용되고 있다. 전기 저항, 절연 상태, 통신 품질 및 커넥터 상태를 지속적으로 감시하여 케이블 열화를 조기에 발견할 수 있으며, 조향 횟수와 운전 이력을 함께 관리하여 적절한 교체 시점을 예측한다. 이러한 기술은 대규모 AMR 플릿(Fleet)의 가동률을 크게 향상시키고 예기치 않은 고장을 줄여준다.

결국 **케이블 내구성 설계는 단순히 좋은 전선을 선택하는 것이 아니라, 재료 공학(Material Engineering), 피로 해석(Fatigue Analysis), 환경 보호(Environmental Protection), 열 관리(Thermal Management), 커넥터 설계(Connector Design), 배선 최적화(Cable Routing Optimization), 내구 시험(Durability Testing) 및 예지보전(Predictive Maintenance)을 통합하는 종합적인 신뢰성 설계 기술**이다. 이러한 요소들이 최적화될 때 스티어 드라이브 자율주행 이동로봇은 수백만 회의 조향 사이클 동안 안정적인 전기 성능과 높은 신뢰성을 유지하면서, 산업 현장에서 낮은 유지보수 비용과 긴 서비스 수명을 달성할 수 있다.

##  

## 05 Module integration

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Frame Mounting Design

The frame mounting design is one of the most fundamental aspects of steer-drive module integration because it defines how individual steering and drive modules transfer forces into the robot chassis while maintaining structural rigidity, positioning accuracy, and long-term reliability. Although steering modules contain their own motors, gearboxes, bearings, and braking systems, their overall performance ultimately depends on how effectively they are integrated into the main vehicle frame. A poorly designed mounting interface introduces structural deformation, vibration, misalignment, and fatigue failure regardless of the quality of the steering module itself. Consequently, frame mounting is considered an essential component of the complete mechanical architecture rather than a simple attachment method.

The primary objective of frame mounting is to establish a rigid mechanical load path between the steer-drive module and the vehicle chassis. During operation, each module experiences vertical loads generated by vehicle weight and payload, longitudinal loads produced during acceleration and braking, lateral loads caused by steering maneuvers, and overturning moments resulting from uneven payload distribution or rapid directional changes. These forces must be transferred efficiently into the structural frame without excessive local deformation. Therefore, the mounting interface is typically designed with high-strength structural members, reinforced connection plates, and carefully distributed bolt patterns that minimize stress concentration.

Most industrial steer-drive platforms employ flange-mounted module interfaces. In this configuration, the steering module housing incorporates a precision-machined mounting flange that directly mates with the chassis mounting surface. Large-diameter locating pilots ensure accurate positioning, while multiple high-strength bolts distribute mechanical loads uniformly across the interface. This arrangement minimizes assembly tolerances and guarantees repeatable module alignment during manufacturing and maintenance.

For heavy industrial applications, frame mounting often utilizes box-frame or closed-section structural members rather than simple flat plates. Closed structural sections exhibit significantly greater bending and torsional stiffness while maintaining relatively low structural weight. These frame geometries distribute concentrated wheel loads throughout the chassis instead of allowing excessive local deformation near individual mounting locations. Finite Element Analysis is commonly used during development to optimize frame cross-sections, reinforcing ribs, and mounting bracket geometry while minimizing total vehicle mass.

The relationship between frame stiffness and vehicle positioning accuracy is particularly important for autonomous mobile robots. Under heavy payload conditions, even small chassis deflections alter the relative positions of the wheel modules. Because the vehicle kinematic model assumes fixed wheel geometry, structural deformation introduces systematic positioning errors that cannot be eliminated entirely through software compensation. Consequently, frame stiffness directly influences localization accuracy, path tracking performance, and precision docking capability.

Mounting surfaces require extremely high geometric accuracy. Flatness, perpendicularity, concentricity, and bolt-hole positional tolerances determine the final alignment of the steering axis relative to the vehicle coordinate system. Precision machining after welding is frequently employed to eliminate distortion introduced during fabrication. Reference datums are incorporated into the chassis design to simplify manufacturing inspection and guarantee consistent module installation throughout production.

Vibration isolation must also be considered. Completely rigid mounting maximizes positioning accuracy but may transmit gearbox vibration and road impacts directly into the chassis. Conversely, excessive compliance reduces steering precision. Engineers therefore optimize structural damping through material selection, localized reinforcement, and carefully controlled stiffness distribution rather than relying solely on elastomeric isolation elements. Modal analysis ensures that the natural frequencies of the frame remain well separated from motor excitation frequencies and wheel-induced vibrations.

Maintenance accessibility significantly influences frame mounting philosophy. Modern industrial robots increasingly adopt modular replacement strategies in which an entire steer-drive module can be removed independently without dismantling adjacent mechanical systems. Accessible mounting bolts, standardized electrical connectors, centralized lubrication points, and predefined lifting interfaces reduce maintenance time while minimizing production downtime.

Corrosion protection also contributes to long-term structural reliability. Outdoor robots frequently employ galvanized steel, powder-coated structural components, stainless fasteners, and sealed mounting interfaces to prevent corrosion under moisture, chemicals, and temperature cycling. Indoor systems may prioritize lightweight aluminum structures while maintaining sufficient stiffness for precision positioning.

Digital engineering tools have become indispensable throughout frame mounting development. Three-dimensional CAD models define geometric interfaces, finite element simulations verify structural strength, multibody dynamic analysis evaluates load transfer during vehicle motion, and fatigue simulations estimate long-term durability under repeated industrial duty cycles. Experimental strain measurements on prototype vehicles further validate analytical predictions before production release.

Ultimately, frame mounting design determines whether the exceptional performance of individual steer-drive modules can be fully realized at the vehicle level. By providing high structural rigidity, precise alignment, effective load distribution, and maintainable modular interfaces, the frame mounting system establishes the mechanical foundation upon which accurate steering control, reliable autonomous navigation, and long service life depend.

---

### 5.2 Integrated Design for 1200 kg Class Load

Designing a steer-drive platform capable of carrying a payload within the 1200 kg class requires a comprehensive systems engineering approach in which every mechanical, electrical, structural, and control subsystem is optimized as part of a fully integrated architecture. At this payload level, the steering module can no longer be considered an isolated component. Instead, the drive modules, chassis, suspension, bearings, motors, gearboxes, brakes, battery system, and control software operate as an interconnected mechanical system whose overall performance depends on the interaction among all subsystems. Consequently, successful heavy-duty platform development requires simultaneous optimization across the entire vehicle rather than independent optimization of individual components.

The first design objective is achieving sufficient structural stiffness while minimizing unnecessary mass. A vehicle designed to transport approximately 1200 kg typically experiences total operating weights approaching or exceeding two metric tons once chassis mass, batteries, sensors, onboard computers, and auxiliary equipment are included. Such loads generate substantial bending moments within the frame, particularly during uneven loading or dynamic maneuvers. High-strength welded steel structures are therefore commonly employed, often utilizing box-section beams and reinforced cross members to maximize bending and torsional rigidity. Finite Element Analysis plays a central role in determining optimal wall thickness, reinforcement placement, and stress distribution while maintaining an acceptable vehicle weight.

Steer-drive module integration becomes increasingly demanding at this scale. Each module must safely support a significant portion of the total vehicle weight while simultaneously transmitting propulsion torque, steering forces, braking loads, and impact forces encountered during industrial operation. High-capacity crossed roller bearings or tapered roller bearing assemblies are frequently selected to withstand combined radial, axial, and overturning loads. Gearboxes employ planetary or cycloidal reduction mechanisms capable of sustaining continuous high torque with minimal backlash. Large-diameter mounting flanges distribute structural loads uniformly into the chassis while maintaining accurate steering alignment.

Drive motor selection requires careful balancing of continuous torque capability, peak acceleration requirements, thermal performance, and electrical efficiency. Permanent magnet synchronous motors are commonly chosen because they provide high torque density, excellent efficiency, and precise low-speed controllability. Each drive motor is paired with an appropriately sized servo controller capable of supporting regenerative braking, current limiting, thermal protection, and real-time torque control. Integrated thermal sensors continuously monitor motor temperature to prevent overheating during prolonged heavy-duty operation.

The steering system must maintain precise positioning despite substantially increased steering loads. High-reduction harmonic or planetary steering gearboxes, combined with high-resolution absolute encoders, enable accurate steering angle control even when supporting heavy payloads. Closed-loop servo control continuously compensates for mechanical compliance, wheel-ground interaction, and varying load distribution to maintain stable steering performance throughout the operational envelope.

The battery system also becomes a major design consideration. Heavy-duty platforms typically utilize high-capacity lithium iron phosphate battery packs operating at forty-eight volts or higher to provide sufficient energy for continuous industrial operation. Battery placement is optimized to lower the vehicle center of gravity while achieving balanced weight distribution among all steer-drive modules. Thermal management systems maintain stable battery temperature under both charging and discharge conditions, improving safety and extending battery service life.

Braking performance becomes increasingly important as vehicle mass increases. Regenerative braking supplied by the drive motors performs most routine deceleration, significantly improving overall energy efficiency. Nevertheless, spring-applied electromagnetic holding brakes remain essential for emergency stopping, parking, and fail-safe protection during electrical power loss. Brake sizing is determined through detailed kinetic energy calculations accounting for maximum payload, vehicle speed, floor inclination, and required stopping distance.

Control architecture must coordinate all four steer-drive modules as a unified system. High-speed industrial communication networks such as EtherCAT synchronize steering positions, wheel velocities, motor currents, encoder measurements, and safety diagnostics with deterministic timing. Vehicle-level inverse kinematics convert commanded chassis motion into individual wheel steering angles and drive velocities while continuously compensating for wheel slip, load transfer, and mechanical tolerances. Advanced control algorithms may further incorporate model predictive control and adaptive parameter estimation to improve trajectory tracking under varying payload conditions.

Reliability and maintainability become primary engineering objectives for industrial heavy-duty vehicles. Modular steer-drive units permit rapid field replacement, while integrated condition monitoring continuously evaluates bearing vibration, gearbox temperature, motor current, brake status, battery health, and steering encoder diagnostics. Predictive maintenance algorithms analyze these measurements to detect developing faults before operational failures occur, significantly increasing fleet availability while reducing maintenance costs.

Safety considerations are integrated throughout the entire design. Redundant emergency stop circuits, safety-rated motor controllers, functional safety communication, brake monitoring, overload protection, thermal supervision, and diagnostic fault management operate together to ensure safe vehicle behavior under both normal and abnormal operating conditions. Compliance with applicable industrial safety standards is considered from the earliest design stages rather than added after mechanical development is complete.

The integrated design philosophy for a 1200 kg-class steer-drive platform therefore extends far beyond simply increasing component size. Every subsystem---including the structural frame, steering modules, drive modules, bearings, motors, batteries, brakes, electronics, software, and safety architecture---must be engineered as part of a unified mechanical and control system. Through comprehensive multidisciplinary optimization, the resulting vehicle achieves the high payload capacity, positioning accuracy, operational reliability, and long service life required for demanding industrial automation applications such as heavy manufacturing, automated material handling, large-scale logistics, and precision industrial inspection.

### 5.1 프레임 장착 설계 (Frame Mounting Design)

프레임 장착 설계(Frame Mounting Design)는 스티어 드라이브(Steer Drive) 모듈 통합 설계에서 가장 기본적이면서도 중요한 요소 가운데 하나이다. 프레임 장착 구조는 각각의 조향 및 구동 모듈이 발생시키는 모든 힘을 차량의 메인 프레임(Main Frame)으로 전달하는 동시에, 구조 강성(Structural Rigidity), 위치 정밀도(Positioning Accuracy) 및 장기적인 신뢰성(Long-term Reliability)을 유지하도록 하는 역할을 수행한다. 비록 하나의 스티어 드라이브 모듈이 자체적으로 조향 모터, 구동 모터, 감속기, 베어링 및 브레이크를 모두 포함하고 있더라도, 이러한 성능은 최종적으로 차량 프레임과 얼마나 효과적으로 통합되는가에 따라 결정된다. 장착 구조가 적절하지 않으면 프레임 변형, 진동, 조향축 정렬 오차 및 피로 파손(Fatigue Failure)이 발생하여 우수한 조향 모듈이라도 본래의 성능을 발휘할 수 없다. 따라서 프레임 장착은 단순한 고정 방법이 아니라 차량 전체 기계 구조(Mechanical Architecture)의 핵심 요소로 간주된다.

프레임 장착의 가장 중요한 목적은 스티어 드라이브 모듈과 차량 프레임 사이에 높은 강성을 가진 **하중 전달 경로(Load Path)**를 형성하는 것이다. 차량이 운행하는 동안 각 모듈에는 차량과 적재물의 무게에 의한 수직 하중(Vertical Load), 가속과 제동에 의한 종방향 하중(Longitudinal Load), 조향에 의한 횡방향 하중(Lateral Load), 그리고 편하중이나 급격한 방향 전환으로 발생하는 전복 모멘트(Overturning Moment)가 동시에 작용한다. 이러한 힘은 프레임으로 효율적으로 전달되어야 하며, 국부적인 변형(Local Deformation)이 최소화되어야 한다. 이를 위해 일반적으로 고강도 구조 부재(Structural Member), 보강 플레이트(Reinforced Plate) 및 응력 집중을 줄이는 볼트 패턴(Bolt Pattern)이 적용된다.

대부분의 산업용 스티어 드라이브 플랫폼은 **플랜지 장착 방식(Flange-mounted Interface)**을 사용한다. 조향 모듈의 하우징에는 정밀 가공된 플랜지가 형성되어 있으며, 차량 프레임의 장착면과 직접 결합된다. 큰 직경의 위치 결정 파일럿(Locating Pilot)은 정확한 위치를 유지하며, 여러 개의 고장력 볼트(High-strength Bolt)가 하중을 균일하게 분산시킨다. 이러한 구조는 조립 공차를 최소화하고 유지보수 과정에서도 항상 동일한 조향축 정렬을 보장한다.

중량급 산업용 차량에서는 단순한 평판 구조보다 **박스 프레임(Box Frame)** 또는 **폐단면 구조(Closed-section Structure)**가 많이 사용된다. 이러한 단면은 굽힘 강성과 비틀림 강성이 매우 높으며 무게 증가를 최소화할 수 있다. 또한 바퀴에서 발생하는 집중 하중을 차체 전체로 분산시키므로 특정 장착 부위의 변형을 줄일 수 있다. 설계 과정에서는 **유한요소해석(Finite Element Analysis, FEA)**을 이용하여 프레임 단면 형상, 보강 리브(Reinforcing Rib) 및 장착 브래킷의 형상을 최적화하면서도 차량 전체 중량을 최소화한다.

프레임 강성과 차량의 위치 정밀도는 매우 밀접한 관계를 가진다. 무거운 적재물을 운반하면 차체는 미세하게 휘어지며, 이에 따라 각 휠 모듈의 상대적인 위치가 변화한다. 그러나 차량 운동학(Kinematics)은 바퀴의 위치가 항상 일정하다고 가정하므로 이러한 구조 변형은 소프트웨어만으로는 완전히 제거할 수 없는 위치 오차(Systematic Positioning Error)를 발생시킨다. 따라서 프레임 강성은 위치 인식(Localization), 경로 추종(Path Tracking) 및 정밀 도킹(Precision Docking)의 성능에 직접적인 영향을 미친다.

장착면(Mounting Surface)은 매우 높은 기하학적 정밀도(Geometric Accuracy)를 가져야 한다. 평면도(Flatness), 직각도(Perpendicularity), 동심도(Concentricity) 및 볼트 홀 위치 공차는 조향축과 차량 좌표계(Vehicle Coordinate System)의 정렬을 결정한다. 일반적으로 용접 후에는 정밀 가공을 수행하여 용접 변형을 제거하며, 기준면(Datum)을 설계 단계에서 정의하여 생산 과정에서도 일관된 품질을 확보한다.

진동(Vibration)도 함께 고려해야 한다. 지나치게 강성이 높은 구조는 감속기와 노면에서 발생하는 진동을 그대로 차체에 전달할 수 있으며, 반대로 지나치게 유연한 구조는 조향 정밀도를 저하시킨다. 따라서 재료 선택, 국부 보강 및 강성 분포를 최적화하여 적절한 구조 감쇠(Structural Damping)를 확보한다. 또한 **모드 해석(Modal Analysis)**을 수행하여 프레임의 고유진동수(Natural Frequency)가 모터의 가진 주파수(Excitation Frequency)와 겹치지 않도록 설계한다.

유지보수성(Serviceability)도 프레임 장착 설계에 큰 영향을 준다. 최근 산업용 AMR은 전체 조향 모듈을 독립적으로 교체할 수 있는 모듈형 구조(Modular Structure)를 채택하는 경우가 많다. 쉽게 접근 가능한 장착 볼트, 표준화된 전기 커넥터, 집중 윤활 지점 및 전용 리프팅 인터페이스(Lifting Interface)는 유지보수 시간을 크게 단축시키고 생산 중단 시간을 최소화한다.

실외 자율주행 차량에서는 부식 방지(Corrosion Protection)도 중요하다. 일반적으로 아연도금 강재(Galvanized Steel), 분체도장(Powder Coating), 스테인리스 체결 부품 및 밀폐형 장착 구조를 적용하여 습기와 화학물질로부터 프레임을 보호한다. 반면 실내 AMR은 가벼운 알루미늄 구조를 사용하면서도 충분한 강성을 확보하는 방향으로 설계되는 경우가 많다.

최근에는 디지털 엔지니어링(Digital Engineering)이 프레임 장착 설계의 필수 요소가 되었다. 3차원 CAD 모델은 기계 인터페이스를 정의하고, 유한요소해석은 구조 강도를 검증하며, 다물체 동역학 해석(Multibody Dynamic Analysis)은 차량 운동 중 하중 전달을 분석한다. 또한 피로 해석(Fatigue Analysis)을 통해 반복 하중에 대한 장기 내구성을 예측하고, 실제 시제품에서는 변형률(Strain)을 측정하여 해석 결과를 검증한다.

결국 프레임 장착 설계는 개별 스티어 드라이브 모듈의 성능을 차량 전체에서 그대로 구현하기 위한 핵심 기반 기술이다. 높은 구조 강성, 정확한 정렬, 균일한 하중 분산 및 유지보수가 쉬운 모듈형 구조를 제공함으로써, 자율주행 이동로봇은 높은 조향 정밀도, 안정적인 자율주행 및 긴 서비스 수명을 확보할 수 있다.

---

### 5.2 1200kg급 하중을 위한 통합 설계 (Integrated Design for 1200kg Class Load)

**1200kg급 적재 하중(Payload)**을 운반할 수 있는 스티어 드라이브 플랫폼을 설계하기 위해서는 기계, 전기, 구조 및 제어를 하나의 시스템으로 통합하는 **시스템 엔지니어링(Systems Engineering)** 접근이 필요하다. 이 정도의 하중에서는 조향 모듈을 독립적인 부품으로 설계하는 것이 아니라, 프레임(Frame), 구동 모듈(Drive Module), 조향 모듈(Steering Module), 베어링(Bearing), 감속기(Gearbox), 브레이크(Brake), 배터리(Battery), 제어 시스템(Control System) 및 소프트웨어(Software)를 하나의 통합 시스템으로 설계해야 한다. 따라서 개별 부품의 성능을 높이는 것보다 전체 차량 수준에서 최적화를 수행하는 것이 더욱 중요하다.

첫 번째 설계 목표는 **높은 구조 강성(Structural Stiffness)**을 확보하면서 차량 자체 중량은 최소화하는 것이다. 약 **1200kg의 적재 하중**을 운반하는 차량은 차체, 배터리, 센서, 컴퓨터 및 기타 장비를 포함하면 전체 중량이 **2톤 이상**이 되는 경우가 많다. 이러한 무게는 프레임에 매우 큰 굽힘 모멘트를 발생시키며, 특히 편하중이나 급격한 조향 시에는 구조 변형이 크게 증가한다. 따라서 일반적으로 고강도 용접 강 구조(Welded High-strength Steel Structure)를 사용하며, 박스 단면(Box-section Beam)과 보강 크로스 멤버(Reinforced Cross Member)를 적용하여 굽힘 강성과 비틀림 강성을 최대화한다. 설계 과정에서는 유한요소해석(FEA)을 이용하여 두께, 보강 위치 및 응력 분포를 최적화하면서 차량 중량을 최소화한다.

이와 같은 규모에서는 스티어 드라이브 모듈의 통합도 훨씬 중요해진다. 각 모듈은 차량 전체 하중의 상당 부분을 지지하는 동시에 추진 토크, 조향력, 제동력 및 노면 충격을 모두 전달해야 한다. 이를 위해 일반적으로 **크로스 롤러 베어링(Crossed Roller Bearing)** 또는 **테이퍼 롤러 베어링(Tapered Roller Bearing)**이 사용되며, 감속기는 **유성기어 감속기(Planetary Gearbox)** 또는 **사이클로이드 감속기(Cycloidal Reducer)**를 사용하여 높은 토크와 낮은 백래시를 동시에 확보한다. 또한 큰 직경의 플랜지는 하중을 차체에 균일하게 전달하면서 조향축의 정렬을 유지한다.

구동 모터 선정도 매우 중요하다. 일반적으로 **영구자석 동기모터(Permanent Magnet Synchronous Motor, PMSM)**를 사용하며, 높은 토크 밀도(Torque Density), 우수한 효율(Efficiency) 및 저속 제어 성능을 동시에 확보한다. 각 모터에는 전용 서보 드라이브(Servo Drive)가 연결되어 회생 제동(Regenerative Braking), 전류 제한(Current Limiting), 열 보호(Thermal Protection) 및 실시간 토크 제어를 수행한다. 또한 모터 내부에는 온도 센서를 설치하여 장시간 운전 시 과열을 방지한다.

조향 시스템도 높은 하중에서도 정밀한 조향을 유지해야 한다. 이를 위해 **하모닉 감속기(Harmonic Drive)** 또는 고감속비 유성기어를 사용하며, 고분해능 절대형 엔코더(High-resolution Absolute Encoder)를 이용하여 정확한 조향각을 제어한다. 폐루프 제어(Closed-loop Control)는 차체 변형, 노면 마찰 및 하중 변화에 따라 조향각을 지속적으로 보정하여 안정적인 조향 성능을 유지한다.

배터리 시스템(Battery System)은 대형 플랫폼에서 매우 중요한 요소이다. 일반적으로 **48V 이상의 리튬인산철 배터리(Lithium Iron Phosphate, LFP)**를 사용하여 충분한 에너지를 확보한다. 또한 배터리는 차량의 무게 중심(Center of Gravity)을 낮추도록 배치하며, 네 개의 스티어 드라이브 모듈에 균일하게 하중이 분배되도록 설계한다. 배터리 열 관리(Battery Thermal Management)는 충전과 방전 과정에서 안정적인 온도를 유지하여 안전성과 수명을 향상시킨다.

브레이크 성능도 차량 중량 증가에 따라 더욱 중요해진다. 평상시에는 회생 제동을 이용하여 대부분의 감속을 수행함으로써 에너지 효율을 높인다. 그러나 비상 정지(Emergency Stop), 주차(Parking) 및 전원 장애(Power Failure) 상황에서는 **스프링 작동형 전자기 브레이크(Spring-applied Electromagnetic Brake)**가 차량을 안전하게 정지시킨다. 브레이크 용량은 차량의 최대 하중, 최고 속도, 경사면 및 요구되는 제동 거리(Stopping Distance)를 기준으로 계산된다.

제어 시스템(Control Architecture)은 네 개의 스티어 드라이브 모듈을 하나의 차량처럼 동기화해야 한다. EtherCAT과 같은 고속 산업용 네트워크를 이용하여 조향각, 바퀴 속도, 모터 전류, 엔코더 정보 및 안전 진단을 실시간으로 교환한다. 차량 수준의 **역기구학(Inverse Kinematics)**은 목표 차량 속도를 각 바퀴의 조향각과 회전 속도로 변환하며, 바퀴 슬립(Wheel Slip), 하중 이동(Load Transfer) 및 기계 오차를 지속적으로 보정한다. 최근에는 **모델 예측 제어(Model Predictive Control, MPC)** 및 적응형 제어(Adaptive Control)를 적용하여 하중 변화에도 높은 경로 추종 성능을 유지한다.

신뢰성과 유지보수성도 매우 중요한 설계 목표이다. 모듈형 스티어 드라이브는 현장에서 빠르게 교체할 수 있으며, 베어링 진동, 감속기 온도, 모터 전류, 브레이크 상태, 배터리 상태 및 엔코더 이상을 지속적으로 감시하는 **상태 감시(Condition Monitoring)** 기능을 포함한다. 이러한 데이터는 **예지보전(Predictive Maintenance)** 알고리즘에서 분석되어 실제 고장이 발생하기 전에 유지보수를 수행할 수 있도록 한다.

안전(Safety)은 차량 전체에 통합되어야 한다. 이중화 비상 정지 회로(Redundant Emergency Stop Circuit), 안전 등급 서보 드라이브(Safety-rated Servo Drive), 기능 안전 통신(Functional Safety Communication), 브레이크 모니터링, 과부하 보호(Overload Protection), 열 보호 및 진단 시스템이 함께 동작하여 정상 운전뿐 아니라 이상 상황에서도 안전한 차량 동작을 보장한다. 이러한 기능은 개발이 완료된 후 추가하는 것이 아니라 설계 초기 단계부터 함께 고려되어야 한다.

결국 **1200kg급 스티어 드라이브 플랫폼의 통합 설계는 단순히 부품의 크기를 키우는 작업이 아니다. 프레임, 조향 모듈, 구동 모듈, 베어링, 감속기, 모터, 배터리, 브레이크, 전장 시스템, 제어 소프트웨어 및 기능 안전까지 하나의 통합 시스템으로 최적화하는 종합적인 시스템 설계 과정이다.** 이러한 다학제적 최적화를 통해 차량은 높은 적재 능력, 우수한 위치 정밀도, 긴 서비스 수명 및 높은 신뢰성을 동시에 확보할 수 있으며, 중량 물류, 자동화 제조, 산업용 검사 및 대형 자재 운반과 같은 다양한 산업 환경에서 안정적으로 운용될 수 있다.
