**Differential Drive & Steer Drive Engineering**


# Chapter 06 Differential Drive Motor Sizing

##  

## 01 Payload Calculation

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Total Moving Mass Estimation

Total Moving Mass Estimation is one of the most fundamental steps in the design of an Autonomous Mobile Robot (AMR). Every major subsystem, including the drive motors, gearboxes, batteries, wheels, frame structure, braking system, steering mechanism, and power electronics, depends on an accurate understanding of the total mass that must be moved. An underestimate can lead to insufficient motor torque, reduced acceleration capability, excessive energy consumption, premature component wear, and safety risks. An overestimate may result in oversized components, unnecessary cost, increased vehicle weight, and reduced efficiency. Therefore, accurate mass estimation forms the foundation of mechanical, electrical, and control system design.

The concept of total moving mass extends beyond the simple payload value specified in a product brochure. Many engineers initially focus only on the customer payload requirement, such as transporting 100 kg, 500 kg, or 1000 kg. However, the drive system must accelerate and decelerate the entire moving structure, not just the payload. Consequently, total moving mass includes every component that contributes to vehicle inertia.

The largest contributor is typically the chassis structure. The frame, mounting brackets, reinforcement members, payload deck, protective covers, and structural supports all contribute to the vehicle mass. In industrial AMRs designed for heavy-duty applications, the frame itself may account for a significant percentage of the total vehicle weight. As payload capacity increases, frame strength requirements grow, often resulting in a non-linear increase in structural mass.

Battery systems represent another major contributor. Modern industrial AMRs frequently utilize lithium iron phosphate batteries, lithium-ion batteries, or other high-capacity energy storage systems. As vehicle operating time requirements increase, battery capacity must increase accordingly. Large battery packs can contribute hundreds of kilograms to the overall system mass, particularly in heavy-duty transport vehicles.

Drive components must also be included. Motors, gearboxes, wheel assemblies, steering mechanisms, brakes, bearings, and suspension systems all contribute to moving mass. Although these components are necessary to generate motion, they also increase inertia and therefore influence power requirements.

Electrical and electronic systems contribute additional mass. Controllers, industrial computers, edge computing platforms, GPUs, communication equipment, safety controllers, sensors, and wiring harnesses may collectively represent a substantial weight contribution. As AMRs become more intelligent and computationally capable, this portion of the mass budget continues to grow.

Payload equipment must also be considered carefully. Some applications involve fixed payload modules such as robotic arms, lifting systems, inspection equipment, conveyors, or customer-specific tooling. These components become permanent elements of the moving mass and must be included in all calculations. Variable payloads such as pallets, containers, or transported materials are then added on top of the fixed system mass.

A comprehensive total moving mass calculation typically separates the mass budget into several categories. Base vehicle mass includes the chassis and permanently installed systems. Functional equipment mass includes sensors, manipulators, inspection systems, and automation modules. Energy system mass includes batteries and charging interfaces. Variable payload mass represents the transported load. The sum of these categories defines the total moving mass used for design calculations.

Acceleration requirements strongly influence the importance of mass estimation. Newton\'s Second Law demonstrates the relationship between force, mass, and acceleration:

F = m × a

where F is force, m is mass, and a is acceleration.

This relationship shows that required propulsion force increases directly with vehicle mass. A 1000 kg AMR requires approximately twice the acceleration force of a 500 kg AMR when both vehicles target the same acceleration performance.

Mass estimation also affects braking system design. Emergency stopping performance depends on kinetic energy, which increases proportionally with mass. Heavier vehicles require more robust braking systems, greater tire traction, and stronger structural components to safely dissipate energy during stopping events.

Energy consumption is closely linked to moving mass as well. Heavier vehicles require more energy for acceleration, hill climbing, obstacle negotiation, and continuous operation. Accurate mass estimation therefore influences battery sizing, charging infrastructure requirements, and operational efficiency calculations.

The center of gravity must be evaluated simultaneously with total mass. Two vehicles with identical mass may exhibit very different dynamic behavior if their mass distributions differ. Engineers therefore often perform both mass estimation and center-of-gravity analysis as part of the same design process.

For modern industrial AMRs, particularly those carrying payloads between 500 kg and 1500 kg, total moving mass estimation becomes a multidisciplinary engineering task involving mechanical design, electrical architecture, vehicle dynamics, energy management, and safety analysis. A well-executed mass estimation process ensures that all downstream design decisions are based on realistic operating conditions and performance requirements.

---

### 1.2 Safety Factor Application Criteria

Safety Factor Application Criteria define how engineers account for uncertainty, variability, and unexpected operating conditions during AMR design. While theoretical calculations provide a starting point for engineering analysis, real-world systems rarely operate under ideal conditions. Manufacturing tolerances, material variations, environmental influences, wear, impact loads, operator misuse, and future requirement changes can all introduce additional stresses that exceed nominal design assumptions. Safety factors provide a systematic method for managing these uncertainties and ensuring reliable operation throughout the product lifecycle.

A safety factor can be defined as the ratio between the maximum allowable capacity of a component and the expected operating load. In simplified form:

Safety Factor = Maximum Capacity / Expected Load

A safety factor greater than one indicates that the component possesses additional capacity beyond normal operating requirements. This reserve capacity improves reliability and reduces the likelihood of failure under unexpected conditions.

The appropriate safety factor depends heavily on the subsystem being analyzed. Structural components typically use different safety factors than electrical systems, drive systems, bearings, wheels, or lifting mechanisms. The consequences of failure, the uncertainty of loading conditions, and the expected service life all influence safety factor selection.

In AMR chassis design, structural safety factors are commonly applied to frame members, mounting brackets, payload decks, and load-bearing assemblies. Static loads may be relatively predictable, but dynamic loads generated by acceleration, braking, turning, obstacle impacts, and uneven floor conditions can substantially increase stress levels. Engineers therefore design structural components to withstand loads significantly higher than nominal operating values.

Heavy-duty industrial AMRs often encounter transient loading conditions that exceed steady-state calculations. For example, a vehicle transporting a 1000 kg payload may experience temporary load amplification when crossing floor joints, ramps, or obstacles. Dynamic impact forces may momentarily exceed static loads by a substantial margin. Safety factors help ensure that these transient events do not cause structural failure.

Drive system design also requires appropriate safety margins. Motors, gearboxes, wheel hubs, shafts, and couplings experience varying torque demands throughout operation. Nominal torque calculations rarely capture all possible operating scenarios. Unexpected acceleration commands, emergency stops, wheel slip events, and obstacle encounters may generate significantly higher loads. Safety factors provide protection against these uncertainties.

Bearing selection relies heavily on safety factor considerations. Bearings are subjected to repeated cyclic loading throughout the robot\'s operational life. Fatigue failure is strongly influenced by load magnitude and operating duration. Applying appropriate safety margins helps achieve desired service life targets and reduces maintenance requirements.

Wheel selection similarly benefits from safety factor analysis. Wheel manufacturers typically specify rated load capacities under controlled conditions. Real-world operating environments introduce additional factors such as uneven load distribution, floor irregularities, impact loading, and dynamic maneuvering. Engineers often select wheel capacities substantially above nominal calculated requirements to ensure reliable performance.

Electrical systems also employ safety factors. Power distribution components, circuit protection devices, connectors, wiring harnesses, and battery systems must accommodate peak loads, startup currents, regenerative braking energy, and fault conditions. Adequate design margins improve reliability and thermal performance.

Environmental conditions frequently influence safety factor selection. Indoor logistics robots operating on smooth floors experience relatively predictable loading conditions. Outdoor AMRs operating on rough terrain encounter significantly greater uncertainty. Consequently, outdoor systems often require more conservative safety margins.

Safety factor selection must balance reliability against cost and efficiency. Excessively conservative safety factors increase vehicle weight, component size, manufacturing cost, and energy consumption. Insufficient safety factors increase failure risk and reduce operational reliability. Effective engineering therefore seeks an optimal balance rather than maximizing safety margins indiscriminately.

Risk assessment plays a central role in determining appropriate criteria. Components whose failure could result in safety hazards, vehicle instability, payload damage, or mission failure generally receive higher safety factors than components with less severe consequences. International safety standards and industry regulations often provide guidance regarding minimum acceptable design margins.

For industrial AMRs operating in manufacturing facilities, warehouses, logistics centers, and automated production environments, safety factors serve as a critical bridge between theoretical design calculations and real-world operational reliability. Proper application of safety factor criteria ensures that vehicles remain safe, durable, and dependable throughout years of continuous operation despite uncertainty, variability, and changing operating conditions.

In modern AMR engineering, safety factors should not be viewed as arbitrary multipliers added at the end of a design process. Instead, they should be integrated into the overall systems engineering methodology from the earliest design stages, ensuring that every subsystem possesses sufficient robustness to meet performance, reliability, and safety objectives under realistic operating conditions.

### 1.1 총 이동 질량 산정(Total Moving Mass Estimation)

총 이동 질량 산정(Total Moving Mass Estimation)은 자율주행 이동 로봇(Autonomous Mobile Robot, AMR) 설계에서 가장 기본적이면서도 중요한 작업 중 하나이다. 구동 모터(Drive Motor), 감속기(Gearbox), 배터리(Battery), 휠(Wheel), 프레임(Frame), 제동 시스템(Braking System), 조향 장치(Steering Mechanism), 전력 시스템(Power Electronics) 등 거의 모든 핵심 구성 요소는 차량이 실제로 이동시켜야 하는 총 질량(Total Mass)에 대한 정확한 이해를 기반으로 설계된다.

총 질량을 과소 평가하면 모터 토크 부족, 가속 성능 저하, 과도한 전력 소비, 부품 조기 마모, 안전성 저하와 같은 문제가 발생할 수 있다. 반대로 과대 평가하면 불필요하게 큰 모터와 배터리, 과도한 구조 강성을 가진 프레임이 적용되어 비용 증가, 차량 중량 증가, 에너지 효율 저하를 초래할 수 있다. 따라서 정확한 질량 산정은 기계 설계(Mechanical Design), 전기 설계(Electrical Design), 제어 설계(Control Design)의 출발점이 된다.

총 이동 질량은 단순히 고객이 요구하는 페이로드(Payload)만을 의미하지 않는다. 많은 엔지니어들이 처음에는 "500kg 운반", "1000kg 운반"과 같은 적재 하중만을 고려하는 경우가 있지만, 실제 구동 시스템은 페이로드뿐 아니라 차량 전체를 가속하고 감속해야 한다. 따라서 차량에 포함된 모든 이동 요소가 총 이동 질량에 포함된다.

가장 큰 비중을 차지하는 요소는 일반적으로 프레임 구조(Frame Structure)이다. 섀시(Chassis), 브래킷(Bracket), 보강재(Reinforcement Member), 페이로드 데크(Payload Deck), 보호 커버(Protective Cover), 구조 지지대(Structural Support) 등이 모두 포함된다. 중량급 산업용 AMR에서는 프레임 자체가 차량 전체 질량의 상당 부분을 차지하기도 한다. 특히 페이로드가 증가할수록 구조 강성 요구가 커지기 때문에 프레임 질량은 비선형적으로 증가하는 경향이 있다.

배터리 시스템(Battery System)도 주요 질량 요소이다. 현대 산업용 AMR은 주로 리튬인산철 배터리(LFP Battery) 또는 리튬이온 배터리(Lithium-Ion Battery)를 사용한다. 운행 시간이 길어질수록 더 큰 배터리 용량이 필요하며, 대형 배터리 팩은 수십 kg에서 수백 kg의 질량을 추가할 수 있다. 특히 1000kg급 이상의 중량 플랫폼에서는 배터리 무게만으로도 전체 차량 중량의 상당 부분을 차지한다.

구동계(Drive System)도 반드시 포함되어야 한다. 모터, 감속기, 휠 어셈블리(Wheel Assembly), 조향 모듈(Steering Module), 브레이크(Brake), 베어링(Bearing), 서스펜션(Suspension)은 모두 차량의 일부이며 이동 질량에 기여한다. 이들은 차량을 움직이는 장치이지만 동시에 차량 질량을 증가시키는 요소이기도 하다.

전장 시스템(Electrical and Electronic Systems) 역시 무시할 수 없다. 산업용 컴퓨터(Industrial Computer), 엣지 컴퓨터(Edge Computer), GPU, 안전 컨트롤러(Safety Controller), 통신 장비(Communication Equipment), LiDAR, 카메라, IMU, 하네스(Harness) 등이 모두 질량을 가진다. 최근 AI 기반 AMR에서는 이러한 전장 시스템의 비중이 지속적으로 증가하고 있다.

고정형 페이로드(Fixed Payload Equipment)도 중요하다. 예를 들어 로봇팔(Robot Arm), 리프터(Lifter), CAD2SCAN 장비, GPR 장비, 컨베이어 시스템(Conveyor System), 고객 맞춤 장비(Customer Tooling)는 항상 차량에 탑재되어 있으므로 기본 이동 질량에 포함된다. 여기에 추가적으로 운반되는 물품이 가변 페이로드(Variable Payload)로 더해진다.

실제 산업용 AMR 설계에서는 질량 예산(Mass Budget)을 여러 영역으로 나누어 관리한다. 차량 기본 질량(Base Vehicle Mass), 기능 장비 질량(Functional Equipment Mass), 에너지 시스템 질량(Energy System Mass), 가변 페이로드 질량(Variable Payload Mass)으로 구분하는 경우가 많다. 이들의 합이 최종 총 이동 질량이 된다.

총 질량은 가속 성능에 직접적인 영향을 준다. 뉴턴의 제2법칙(Newton\'s Second Law)은 다음과 같이 표현된다.

F = m × a

여기서

F = 힘(Force)

m = 질량(Mass)

a = 가속도(Acceleration)

이다.

이 식은 차량 질량이 증가할수록 동일한 가속도를 얻기 위해 더 큰 추진력이 필요함을 의미한다. 예를 들어 1000kg AMR은 동일한 가속 성능을 달성하기 위해 500kg AMR보다 약 두 배의 추진력이 필요하다.

총 이동 질량은 제동 시스템 설계에도 영향을 준다. 운동 에너지(Kinetic Energy)는 질량에 비례하여 증가하기 때문에 차량이 무거울수록 더 강력한 브레이크와 더 높은 접지력이 필요하다.

에너지 소비(Energy Consumption) 역시 질량과 밀접하게 연관된다. 차량 질량이 증가하면 가속, 등판(Grade Climbing), 장애물 극복, 장시간 운행에 필요한 에너지가 증가한다. 따라서 총 질량 산정은 배터리 용량 선정과 충전 인프라 설계에도 영향을 미친다.

또한 무게중심(Center of Gravity) 분석은 총 질량 분석과 함께 수행되어야 한다. 동일한 총 질량을 가진 차량이라도 질량 분포가 다르면 전혀 다른 동적 특성을 나타낼 수 있기 때문이다.

500kg\~1500kg급 산업용 AMR에서는 총 이동 질량 산정이 단순한 무게 계산이 아니라 기계 설계, 전기 설계, 동역학(Vehicle Dynamics), 에너지 관리(Energy Management), 안전 공학(Safety Engineering)을 통합하는 시스템 엔지니어링(System Engineering) 작업이 된다. 정확한 질량 산정은 모든 후속 설계의 정확도를 결정하는 핵심 요소이다.

---

### 1.2 안전계수 적용 기준(Safety Factor Application Criteria)

안전계수(Safety Factor)는 AMR 설계 과정에서 불확실성(Uncertainty), 변동성(Variability), 예상치 못한 운용 조건(Unexpected Operating Condition)을 고려하기 위해 사용되는 핵심 개념이다. 이론 계산은 설계의 출발점을 제공하지만 실제 환경은 항상 이상적인 조건과 다르다. 제조 공차(Manufacturing Tolerance), 재료 특성 변화(Material Variation), 환경 조건(Environmental Condition), 마모(Wear), 충격 하중(Impact Load), 운용 오류(Operator Misuse), 미래 요구사항 변화(Future Requirement Change) 등이 모두 추가적인 하중과 응력을 발생시킬 수 있다.

안전계수는 일반적으로 다음과 같이 정의된다.

Safety Factor = Maximum Capacity / Expected Load

즉, 부품이 견딜 수 있는 최대 용량(Maximum Capacity)을 예상 운용 하중(Expected Load)으로 나눈 값이다.

안전계수가 1보다 크다는 것은 정상 운용 조건 이상의 여유 용량(Reserve Capacity)을 확보하고 있음을 의미한다. 이 여유는 예기치 않은 상황에서도 시스템이 안전하게 작동할 수 있도록 한다.

적절한 안전계수는 적용 대상에 따라 달라진다. 구조물(Structure), 전기 시스템(Electrical System), 구동계(Drive System), 베어링(Bearing), 휠(Wheel), 리프팅 장치(Lifting Mechanism)는 각각 다른 수준의 안전계수를 적용한다. 이는 고장 시 발생하는 위험도(Risk Level), 하중의 불확실성, 요구 수명(Service Life)에 따라 결정된다.

AMR 프레임 설계에서는 프레임 멤버(Frame Member), 브래킷, 페이로드 데크, 하중 지지 구조물에 안전계수를 적용한다. 정적 하중은 비교적 예측 가능하지만, 가속, 감속, 회전, 장애물 충돌, 바닥 요철 등은 순간적으로 응력을 크게 증가시킨다. 따라서 구조물은 일반적으로 예상 하중보다 훨씬 높은 하중을 견딜 수 있도록 설계된다.

중량급 산업용 AMR에서는 일시적인 충격 하중(Transient Load)이 매우 중요하다. 예를 들어 1000kg 페이로드를 운반하는 차량이 바닥 이음새(Floor Joint)나 경사로(Ramp)를 통과할 경우 순간적으로 정적 하중보다 훨씬 큰 응력이 발생할 수 있다. 안전계수는 이러한 상황에서도 구조적 손상이 발생하지 않도록 보장한다.

구동계 역시 충분한 여유 용량을 가져야 한다. 모터, 감속기, 허브(Hub), 샤프트(Shaft), 커플링(Coupling)은 운행 중 다양한 토크 조건에 노출된다. 급가속, 비상 정지(Emergency Stop), 휠 슬립, 장애물 충돌은 계산된 정격 토크를 초과하는 부하를 발생시킬 수 있다.

베어링 선정에서도 안전계수는 매우 중요하다. 베어링은 반복 하중(Cyclic Load)을 지속적으로 받으며 피로 파손(Fatigue Failure)에 민감하다. 적절한 안전계수를 적용하면 목표 수명을 달성하고 유지보수 비용을 줄일 수 있다.

휠 선정에서도 마찬가지이다. 제조사가 제공하는 정격 하중(Rated Load)은 이상적인 조건에서 측정된 값이다. 실제 환경에서는 편심 하중(Eccentric Load), 바닥 요철, 충격 하중, 회전 하중 등이 추가된다. 따라서 일반적으로 계산값보다 더 높은 용량의 휠을 선택한다.

전기 시스템도 안전계수를 적용한다. 배선(Wiring Harness), 커넥터(Connector), 전력 분배 장치(Power Distribution Unit), 차단기(Circuit Protection Device), 배터리는 최대 부하뿐 아니라 돌입 전류(Inrush Current), 회생 제동(Regenerative Braking), 이상 상태(Fault Condition)를 고려해야 한다.

환경 조건도 영향을 준다. 실내 물류 AMR은 비교적 안정적인 환경에서 운용되므로 상대적으로 낮은 안전계수를 적용할 수 있다. 반면 실외 AMR은 비포장 도로, 충격, 진동, 온도 변화 등 다양한 환경 요소를 고려해야 하므로 더 보수적인 설계가 필요하다.

안전계수는 신뢰성과 비용 사이의 균형을 맞추는 과정이다. 지나치게 높은 안전계수는 차량 무게 증가, 비용 증가, 에너지 효율 저하를 초래한다. 반대로 너무 낮은 안전계수는 고장 가능성을 증가시킨다.

따라서 최적의 설계는 무조건 큰 안전계수를 사용하는 것이 아니라 위험도 분석(Risk Assessment)을 기반으로 적절한 수준을 적용하는 것이다. 사람의 안전, 차량 전복, 페이로드 손상, 생산 중단과 같은 심각한 결과를 초래할 수 있는 부품은 더 높은 안전계수를 적용해야 한다.

현대 산업용 AMR에서 안전계수는 단순히 계산 마지막에 곱하는 숫자가 아니다. 설계 초기 단계부터 시스템 엔지니어링의 일부로 통합되어야 한다. 이를 통해 차량은 수년간의 연속 운용 환경에서도 충분한 내구성(Durability), 신뢰성(Reliability), 안전성(Safety)을 유지할 수 있다.

특히 힐스로보틱스(Hills Robotics)의 500kg, 1000kg, 1500kg급 산업용 AMR 설계에서는 구조물 기준 최소 2.0\~3.0, 휠 및 베어링 기준 2.5\~4.0, 리프팅 및 검사 장비 장착부 기준 3.0 이상 수준의 안전계수를 적용하는 것이 일반적인 산업용 설계 기준에 부합하며 장기 신뢰성 확보에 유리하다.

##  

## 02 Torque Calculation

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Starting Torque Calculation

Starting Torque Calculation is one of the most important steps in mobile robot drive system design because it determines whether the vehicle can initiate motion from a complete stop under the most demanding operating conditions. Unlike continuous operation, where the robot is already moving and inertia has been overcome, starting conditions require the drive system to simultaneously overcome static friction, rolling resistance, drivetrain losses, and vehicle inertia. If starting torque is underestimated, the robot may fail to move smoothly, experience excessive motor current draw, stall under load, or exhibit poor acceleration performance.

The starting condition represents the highest mechanical demand that many AMRs experience during normal operation. When the vehicle is stationary, tire deformation, bearing friction, gearbox friction, and floor contact forces combine to resist motion. These resistive forces must be overcome before acceleration can begin. Consequently, starting torque is generally higher than the torque required to maintain constant speed.

The first component of starting torque is rolling resistance. Even on smooth industrial floors, wheel materials deform slightly under load. This deformation creates a resistance force proportional to vehicle weight. The rolling resistance force can be approximated as:

Frr = Crr × W

where:

Frr = Rolling Resistance Force

Crr = Rolling Resistance Coefficient

W = Vehicle Weight

The coefficient depends on wheel material and floor condition. Polyurethane wheels on smooth epoxy floors typically exhibit lower rolling resistance than rubber tires on rough concrete surfaces.

The second component is acceleration force. According to Newton's Second Law:

Fa = m × a

where:

Fa = Acceleration Force

m = Total Moving Mass

a = Desired Acceleration

This force represents the energy required to accelerate the vehicle from rest toward its target speed. Higher acceleration requirements directly increase starting torque demand.

Additional forces may also be present. Inclines require climbing force, obstacle crossing requires impact force margins, and drivetrain inefficiencies consume a portion of motor output. These factors are often incorporated through efficiency corrections and safety factors.

The total traction force required at startup is therefore:

Ftotal = Frr + Fa + Fgrade + Fadditional

where:

Fgrade = Force required for slope climbing

Fadditional = Miscellaneous resistance forces

Once the total traction force is known, wheel torque can be calculated by multiplying the force by wheel radius:

Twheel = Ftotal × r

where:

Twheel = Wheel Torque

r = Wheel Radius

For multi-wheel drive systems, this torque is distributed among the drive wheels. A four-wheel drive vehicle generally shares the load among four traction points, while a Differential Drive vehicle typically distributes torque between two drive wheels.

Motor torque must then account for gearbox efficiency and transmission losses. No mechanical system operates with perfect efficiency. Gear meshing losses, bearing friction, seal drag, and manufacturing tolerances all reduce usable output torque. Therefore:

Tmotor = Twheel / (Gear Ratio × Efficiency)

This relationship shows why gearbox selection is closely linked to starting torque requirements. A larger reduction ratio increases output torque but reduces maximum vehicle speed.

Heavy-duty industrial AMRs often require significant starting torque because payloads may exceed several hundred kilograms. In such cases, engineers frequently select motors based primarily on startup requirements rather than continuous operating conditions. Failure to provide adequate starting torque can lead to overheating, excessive current draw, reduced battery life, and poor vehicle responsiveness.

Another important consideration is traction limitation. Even if the motor can generate large torque values, wheel slip may occur if available friction between the wheel and floor is insufficient. Consequently, starting torque calculations must always be verified against traction limits.

Modern AMR development typically includes simulation-based validation of startup performance. Vehicle dynamics models evaluate acceleration profiles, motor currents, wheel slip behavior, and battery loading under various payload conditions. These simulations help engineers ensure that theoretical torque calculations translate into reliable real-world performance.

Ultimately, starting torque calculation establishes the minimum torque capability required for successful vehicle launch. It serves as a critical design input for motor selection, gearbox sizing, wheel selection, battery design, and control system tuning, ensuring that the AMR can move safely and efficiently under all expected operating conditions.

---

### 2.2 Continuous Torque Calculation

While starting torque determines whether a robot can begin moving, Continuous Torque Calculation determines whether the vehicle can sustain operation over extended periods without overheating, excessive wear, or performance degradation. Continuous torque is the torque required during steady-state operation when the robot is moving at a relatively constant speed. It forms the basis for motor thermal design, power system sizing, energy consumption estimation, and long-term reliability analysis.

Many new engineers focus primarily on startup torque because it represents the highest instantaneous load. However, industrial AMRs often spend the majority of their operating life moving continuously. Consequently, continuous torque requirements frequently dominate motor thermal design and operating efficiency considerations.

Under constant-speed conditions, acceleration force approaches zero. Therefore, the drive system primarily needs to overcome rolling resistance, aerodynamic drag, drivetrain losses, floor irregularities, and any grade-related forces. Since acceleration is absent, continuous torque is usually significantly lower than starting torque.

Rolling resistance remains the largest contributor in most indoor AMRs. As wheels rotate, elastic deformation occurs within the tire material and floor contact region. This deformation continuously consumes energy and generates resistance force. Although relatively small compared with startup acceleration forces, rolling resistance acts continuously throughout operation.

For indoor AMRs operating at moderate speeds, aerodynamic drag is often negligible. However, larger outdoor vehicles traveling at higher speeds may experience measurable aerodynamic effects. In such cases, drag force increases approximately with the square of vehicle velocity, making it an increasingly important component of continuous torque requirements.

When operating on slopes, continuous climbing force becomes significant. Unlike acceleration forces that act temporarily, climbing forces remain active as long as the vehicle ascends the incline. Consequently, continuous operation on ramps or uneven terrain may require considerably higher torque levels than operation on flat floors.

The total continuous traction force can be approximated as:

Fcontinuous = Frr + Fgrade + Fdrag

where:

Frr = Rolling Resistance Force

Fgrade = Grade Resistance Force

Fdrag = Aerodynamic Drag Force

The corresponding wheel torque becomes:

Twheel = Fcontinuous × r

The resulting motor torque must again account for gearbox ratio and drivetrain efficiency.

One of the most important aspects of continuous torque calculation is motor thermal behavior. Electric motors generate heat whenever current flows through their windings. Continuous operation at excessive torque levels may cause winding temperatures to exceed safe limits, reducing insulation life and increasing failure risk.

Motor manufacturers therefore specify continuous torque ratings separately from peak torque ratings. Peak torque may only be sustainable for a few seconds, whereas continuous torque can be maintained indefinitely under specified cooling conditions. AMR designers must ensure that normal operating requirements remain within the motor's continuous torque capability.

Battery sizing is also influenced by continuous torque calculations. Sustained torque demands determine average current draw, which directly affects operating time, charging frequency, thermal management requirements, and overall energy efficiency.

Drive cycle analysis is commonly used during AMR development. Rather than evaluating only one operating condition, engineers analyze complete mission profiles containing acceleration, cruising, turning, waiting, loading, and unloading phases. Continuous torque requirements are then derived from the average and sustained portions of the mission cycle.

For heavy-duty industrial AMRs, thermal margins are particularly important. A motor capable of generating sufficient startup torque may still fail if its continuous torque capability is inadequate. Therefore, motor selection should always consider both peak and continuous operating conditions.

Continuous torque calculation ultimately ensures that the robot can perform its intended tasks repeatedly and reliably throughout long operating shifts. It provides critical information for motor sizing, thermal design, battery capacity planning, energy management strategies, and lifecycle reliability assessment.

---

### 2.3 Worked Example: 200 kg AMR

A practical worked example helps illustrate how starting torque and continuous torque calculations are applied during AMR design. Consider an indoor industrial AMR with a total moving mass of 200 kg operating on a smooth epoxy floor. Assume the vehicle uses two drive wheels, each with a diameter of 200 mm, and the target acceleration is 0.5 m/s².

The total vehicle weight is:

W = m × g

= 200 × 9.81

= 1962 N

Assume a rolling resistance coefficient of 0.02, which is typical for polyurethane wheels on industrial flooring.

The rolling resistance force becomes:

Frr = 0.02 × 1962

= 39.2 N

Next, calculate the acceleration force:

Fa = m × a

= 200 × 0.5

= 100 N

Assuming flat-floor operation and negligible aerodynamic drag, the total startup force becomes:

Ftotal = Frr + Fa

= 39.2 + 100

= 139.2 N

The wheel radius is:

r = 0.2 / 2

= 0.1 m

Therefore, required wheel torque is:

Twheel = 139.2 × 0.1

= 13.92 Nm

Since the vehicle uses two drive wheels, torque per wheel is approximately:

13.92 / 2

= 6.96 Nm

Assume a gearbox ratio of 15:1 and drivetrain efficiency of 90%.

The motor torque required per wheel becomes:

Tmotor = 6.96 / (15 × 0.9)

≈ 0.52 Nm

In practice, engineers would apply a safety factor to accommodate uncertainties, floor variation, payload changes, and component aging. Assuming a safety factor of 2.5:

Required Motor Torque

≈ 0.52 × 2.5

≈ 1.3 Nm

This value represents a practical minimum starting torque requirement for each motor.

Now consider continuous operation at constant speed. Since acceleration force is no longer present:

Fcontinuous = Frr

= 39.2 N

Wheel torque becomes:

Twheel = 39.2 × 0.1

= 3.92 Nm

Per wheel:

3.92 / 2

= 1.96 Nm

Motor torque becomes:

Tmotor = 1.96 / (15 × 0.9)

≈ 0.145 Nm

Applying the same safety factor:

Continuous Motor Torque Requirement

≈ 0.36 Nm

This example demonstrates a common AMR design characteristic: starting torque requirements are significantly higher than continuous torque requirements. As vehicle mass increases, the difference becomes even more pronounced.

For larger industrial AMRs carrying 500 kg, 1000 kg, or 1500 kg payloads, the same methodology applies. The equations remain unchanged, but the resulting forces, torques, thermal loads, and safety requirements increase substantially. Consequently, accurate torque calculations become increasingly important as vehicle size and payload capacity grow.

### 2.1 기동 토크 계산(Starting Torque Calculation)

기동 토크 계산(Starting Torque Calculation)은 이동 로봇(Mobile Robot) 구동 시스템 설계에서 가장 중요한 작업 중 하나이다. 기동 토크는 차량이 정지 상태(Stationary Condition)에서 움직이기 시작할 수 있는지를 결정한다. 차량이 이미 주행 중인 경우에는 관성(Inertia)이 극복된 상태이지만, 정지 상태에서는 정지 마찰력(Static Friction), 구름 저항(Rolling Resistance), 구동계 손실(Drivetrain Loss), 차량 관성을 동시에 극복해야 한다.

기동 토크가 부족하면 차량은 원활하게 출발하지 못하거나, 모터 전류가 과도하게 증가하고, 고하중 조건에서 스톨(Stall)이 발생하며, 가속 성능이 크게 저하될 수 있다. 따라서 기동 토크는 AMR의 실제 운용 가능성을 결정하는 핵심 요소이다.

일반적으로 기동 상태는 차량이 경험하는 가장 높은 기계적 부하 조건이다. 차량이 정지해 있을 때는 타이어 변형(Tire Deformation), 베어링 마찰(Bearing Friction), 감속기 마찰(Gearbox Friction), 바닥 접촉력(Contact Force)이 모두 운동을 방해한다. 따라서 일정 속도로 주행할 때보다 훨씬 높은 토크가 필요하다.

기동 토크를 계산할 때 가장 먼저 고려해야 하는 요소는 구름 저항이다. 아무리 평탄한 산업용 바닥이라도 휠은 하중에 의해 미세하게 변형된다. 이러한 변형은 구름 저항력을 발생시킨다.

구름 저항력은 다음과 같이 계산할 수 있다.

Frr = Crr × W

여기서

Frr = 구름 저항력(Rolling Resistance Force)

Crr = 구름 저항 계수(Rolling Resistance Coefficient)

W = 차량 중량(Vehicle Weight)

이다.

PU(Polyurethane) 휠은 일반적으로 고무(Rubber) 타이어보다 구름 저항이 낮다. 또한 에폭시 바닥(Epoxy Floor)은 거친 콘크리트 바닥보다 더 낮은 구름 저항을 가진다.

다음으로 고려해야 할 요소는 가속력(Acceleration Force)이다.

뉴턴의 제2법칙(Newton\'s Second Law)에 따르면

Fa = m × a

여기서

Fa = 가속력(Acceleration Force)

m = 총 이동 질량(Total Moving Mass)

a = 목표 가속도(Target Acceleration)

이다.

이 힘은 차량을 정지 상태에서 목표 속도까지 가속하기 위해 필요한 힘이다. 가속도가 높아질수록 필요한 기동 토크도 증가한다.

추가적으로 경사로 주행(Grade Climbing), 장애물 통과(Obstacle Crossing), 구동계 손실(Drivetrain Loss)도 고려해야 한다.

따라서 전체 기동력은 다음과 같이 표현된다.

Ftotal = Frr + Fa + Fgrade + Fadditional

여기서

Fgrade = 경사 주행 저항력

Fadditional = 기타 저항력

이다.

전체 추진력이 계산되면 휠 토크(Wheel Torque)는 다음과 같이 구한다.

Twheel = Ftotal × r

여기서

Twheel = 휠 토크

r = 휠 반경(Wheel Radius)

이다.

차동 구동(Differential Drive)의 경우 이 토크는 두 개의 구동 휠에 분배된다. 4륜 구동(4WD)의 경우에는 네 개의 휠이 하중을 분담한다.

실제 모터 토크(Motor Torque)를 계산할 때는 감속비(Gear Ratio)와 효율(Efficiency)을 고려해야 한다.

Tmotor = Twheel / (Gear Ratio × Efficiency)

기어 맞물림 손실(Gear Loss), 베어링 마찰, 씰 마찰(Seal Drag) 등으로 인해 실제 전달 효율은 100%가 될 수 없다.

중량급 산업용 AMR에서는 기동 토크 요구량이 매우 크다. 500kg, 1000kg, 1500kg급 차량은 대부분 기동 조건을 기준으로 모터를 선정한다. 기동 토크가 부족하면 모터 과열(Overheating), 전류 과부하(Current Overload), 배터리 수명 저하(Battery Life Reduction), 응답성 저하(Response Degradation)가 발생할 수 있다.

또한 접지 한계(Traction Limit)도 반드시 확인해야 한다. 모터가 충분한 토크를 생성하더라도 바닥과 휠 사이의 마찰력이 부족하면 휠 슬립(Wheel Slip)이 발생할 수 있다.

현대 산업용 AMR 개발에서는 차량 동역학 시뮬레이션(Vehicle Dynamics Simulation)을 통해 기동 성능을 검증한다. 가속 프로파일(Acceleration Profile), 모터 전류(Motor Current), 슬립 특성(Slip Characteristics), 배터리 부하를 분석하여 실제 운용 가능성을 확인한다.

결국 기동 토크 계산은 차량이 정상적으로 출발할 수 있는 최소 토크를 결정하는 과정이며, 모터 선정, 감속기 선정, 휠 선정, 배터리 설계, 제어기 튜닝의 핵심 입력값이 된다.

---

### 2.2 연속 토크 계산(Continuous Torque Calculation)

기동 토크가 차량의 출발 가능성을 결정한다면, 연속 토크(Continuous Torque)는 차량이 장시간 안정적으로 운행할 수 있는지를 결정한다. 연속 토크는 차량이 일정 속도(Constant Speed)로 주행할 때 지속적으로 필요한 토크를 의미한다.

산업용 AMR은 실제 운용 시간의 대부분을 정속 주행 상태에서 보낸다. 따라서 연속 토크는 모터 발열(Thermal Behavior), 전력 소비(Power Consumption), 배터리 사용 시간(Battery Runtime), 장기 신뢰성(Long-Term Reliability)을 결정하는 중요한 요소이다.

정속 주행 상태에서는 가속도가 거의 0에 가깝기 때문에 가속력은 필요하지 않다. 따라서 연속 토크는 주로 구름 저항, 공기 저항(Aerodynamic Drag), 경사 저항(Grade Resistance), 구동계 손실을 극복하기 위해 사용된다.

실내 AMR에서는 일반적으로 구름 저항이 가장 큰 비중을 차지한다. 휠이 회전할 때마다 타이어와 바닥 사이에서는 지속적인 변형이 발생하며, 이 과정에서 에너지가 소모된다.

공기 저항은 실내 AMR에서는 상대적으로 작다. 그러나 고속 실외 AMR의 경우 공기 저항은 속도의 제곱에 비례하여 증가하므로 무시할 수 없는 수준이 된다.

경사로 주행에서는 상황이 달라진다. 경사를 오르는 동안에는 중력(Gravity)에 의해 지속적으로 저항력이 발생한다. 따라서 평지보다 훨씬 높은 연속 토크가 요구될 수 있다.

전체 연속 주행 저항력은 다음과 같이 표현할 수 있다.

Fcontinuous = Frr + Fgrade + Fdrag

여기서

Frr = 구름 저항력

Fgrade = 경사 저항력

Fdrag = 공기 저항력

이다.

휠 토크는 다음과 같다.

Twheel = Fcontinuous × r

그리고 모터 토크는 감속비와 효율을 고려하여 계산한다.

연속 토크 계산에서 가장 중요한 요소는 모터 발열이다. 모터는 전류(Current)가 흐르는 동안 열(Heat)을 발생시킨다. 장시간 높은 토크를 유지하면 권선(Winding) 온도가 상승하게 된다.

따라서 모터 제조사는 일반적으로 최대 토크(Peak Torque)와 연속 토크(Continuous Torque)를 별도로 제공한다.

최대 토크는 수 초 정도만 유지할 수 있는 값이며, 연속 토크는 무한 시간 동안 유지 가능한 값이다.

AMR 설계자는 정상 운행 조건에서 요구되는 토크가 반드시 모터의 연속 토크 범위 내에 있도록 설계해야 한다.

연속 토크는 배터리 설계에도 직접적인 영향을 준다. 지속적인 토크 요구량은 평균 전류(Average Current)를 결정하며, 이는 운행 시간, 충전 주기, 냉각 설계, 에너지 효율에 영향을 준다.

실제 산업용 AMR 개발에서는 주행 사이클 분석(Drive Cycle Analysis)을 수행한다. 가속, 정속 주행, 회전, 정지, 적재, 하역 등 전체 작업 과정을 분석하여 평균 토크와 연속 토크를 계산한다.

특히 중량급 산업용 AMR에서는 기동 토크만 충분하다고 해서 좋은 설계가 아니다. 모터가 높은 기동 토크를 낼 수 있더라도 연속 토크 능력이 부족하면 장시간 운용 중 과열로 인해 성능 저하나 고장이 발생할 수 있다.

결국 연속 토크 계산은 차량이 하루 수십 시간 동안 반복적으로 안정적으로 운행할 수 있는지를 결정하는 핵심 요소이며, 모터 선정, 냉각 설계, 배터리 설계, 에너지 관리 전략의 기초가 된다.

---

### 2.3 계산 예제: 200kg AMR (Worked Example: 200kg AMR)

실제 예제를 통해 기동 토크와 연속 토크 계산 과정을 살펴보자.

가정 조건은 다음과 같다.

총 이동 질량(Total Moving Mass): 200kg

휠 직경(Wheel Diameter): 200mm

구동 휠 수(Number of Drive Wheels): 2개

목표 가속도(Target Acceleration): 0.5m/s²

바닥 조건(Floor Condition): 에폭시 바닥(Epoxy Floor)

구름 저항 계수(Crr): 0.02

먼저 차량 중량을 계산한다.

W = m × g

= 200 × 9.81

= 1962N

구름 저항력은

Frr = 0.02 × 1962

= 39.2N

가속력은

Fa = 200 × 0.5

= 100N

평지 주행을 가정하면

Ftotal = Frr + Fa

= 39.2 + 100

= 139.2N

휠 반경은

r = 0.2 ÷ 2

= 0.1m

따라서 휠 토크는

Twheel = 139.2 × 0.1

= 13.92Nm

차동 구동으로 두 개의 휠이 하중을 나누므로

13.92 ÷ 2

= 6.96Nm

각 휠에 필요한 토크는 약 6.96Nm이다.

감속비 15:1

효율 90%

를 가정하면

Tmotor = 6.96 ÷ (15 × 0.9)

≈ 0.52Nm

여기에 안전계수(Safety Factor) 2.5를 적용하면

필요 모터 토크

≈ 0.52 × 2.5

≈ 1.3Nm

즉, 모터당 최소 약 1.3Nm의 기동 토크가 필요하다.

이제 연속 주행을 계산해 보자.

정속 주행에서는 가속력이 필요 없으므로

Fcontinuous = 39.2N

휠 토크는

Twheel = 39.2 × 0.1

= 3.92Nm

휠당 토크는

3.92 ÷ 2

= 1.96Nm

모터 토크는

Tmotor = 1.96 ÷ (15 × 0.9)

≈ 0.145Nm

안전계수 2.5를 적용하면

연속 모터 토크

≈ 0.36Nm

이 된다.

이 계산 결과에서 알 수 있듯이 기동 토크는 연속 토크보다 훨씬 크다. 이것은 대부분의 산업용 AMR에서 공통적으로 나타나는 특성이다.

동일한 계산 방법은 500kg, 1000kg, 1500kg급 AMR에도 그대로 적용된다. 질량이 증가할수록 필요한 힘, 토크, 발열량, 배터리 용량, 안전 요구사항이 모두 증가한다.

특히 힐스로보틱스(Hills Robotics)의 실내 산업용 AMR 기준으로 보면,

\* 200kg급 : 약 100\~200W급 모터

\* 500kg급 : 약 400\~750W급 모터

\* 1000kg급 : 약 750W\~1.5kW급 모터

\* 1500kg급 : 약 1.5\~3kW급 모터

범위가 일반적으로 사용되며, 최종 선정은 목표 속도, 가속도, 경사도, 휠 직경, 감속비를 종합적으로 고려하여 결정해야 한다. 따라서 정확한 토크 계산은 중량급 산업용 AMR 설계의 핵심 기초 작업이라고 할 수 있다.

##  

## 03 Speed Calculation

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Linear Velocity to Wheel RPM Conversion

The ability to convert vehicle linear velocity into wheel rotational speed is one of the most fundamental calculations in mobile robot design. Every Autonomous Mobile Robot (AMR) ultimately moves through the rotation of its wheels. While users and system integrators typically specify vehicle performance in terms of linear speed, such as meters per second or kilometers per hour, motors and gearboxes operate in rotational units such as revolutions per minute (RPM). Therefore, a precise relationship between vehicle velocity and wheel RPM must be established during the design process.

The conversion begins with a simple geometric relationship. When a wheel rotates one complete revolution, it travels a distance equal to its circumference. The circumference of a wheel is given by:

C = π × D

where:

C = Wheel Circumference

D = Wheel Diameter

This equation shows that larger wheels cover more distance per revolution than smaller wheels. Consequently, wheel diameter directly influences the RPM required to achieve a given vehicle speed.

The linear velocity of a vehicle can be expressed as:

V = C × N

where:

V = Linear Velocity

C = Wheel Circumference

N = Wheel Rotations per Second

By rearranging the equation, wheel rotational speed can be calculated from the desired vehicle velocity:

N = V / C

Since motor and gearbox specifications are generally expressed in RPM rather than revolutions per second, a conversion factor must be applied:

RPM = (V × 60) / (π × D)

This equation forms the basis of wheel speed calculation in virtually all mobile robotic systems.

Consider an example where an AMR uses wheels with a diameter of 200 mm and must travel at 1.5 m/s. The wheel circumference is:

C = π × 0.2

= 0.628 m

The wheel rotational speed becomes:

RPM = (1.5 × 60) / 0.628

≈ 143 RPM

This means the wheel must rotate at approximately 143 RPM to achieve a vehicle speed of 1.5 m/s.

The relationship illustrates several important design tradeoffs. Larger wheels require lower rotational speed to achieve the same vehicle velocity. Smaller wheels require higher RPM. This directly influences gearbox selection, motor speed requirements, and drivetrain efficiency.

In practical AMR development, engineers rarely select wheel RPM independently. Instead, wheel diameter, motor characteristics, gearbox ratio, and target vehicle speed are optimized simultaneously. A motor may operate most efficiently within a specific speed range, while the wheel size determines how that rotational speed translates into vehicle motion.

Gearbox design plays a central role in this conversion process. Electric motors often operate at several thousand RPM, whereas AMR wheels typically rotate at only a few hundred RPM. A gearbox reduces motor speed while increasing output torque. The relationship between motor RPM and wheel RPM can be expressed as:

Motor RPM = Wheel RPM × Gear Ratio

For example, if a wheel requires 150 RPM and the gearbox ratio is 20:1, the motor must operate at:

Motor RPM = 150 × 20

= 3000 RPM

This value falls within the efficient operating range of many industrial brushless motors.

Vehicle acceleration must also be considered. Although steady-state speed determines average wheel RPM, acceleration requires rapid changes in wheel rotational speed. The motor and controller must therefore provide sufficient dynamic response to reach target RPM within acceptable time limits.

Different drive architectures influence RPM distribution. Differential Drive systems generally require independent RPM control for each wheel during turning. One wheel may rotate faster than the other depending on the turning radius. Steer Drive systems maintain similar wheel speeds but alter wheel orientation to achieve directional changes. Omni-wheel systems require coordinated RPM control among multiple wheels simultaneously.

Wheel slip introduces additional complexity. The theoretical equations assume pure rolling motion with no slip between the wheel and the floor. In real industrial environments, minor slip may occur during acceleration, braking, or operation on low-friction surfaces. Consequently, measured vehicle speed may differ slightly from calculated values.

Localization systems often rely on wheel RPM measurements through encoders. Accurate conversion between RPM and linear velocity therefore directly influences odometry accuracy. Errors in wheel diameter estimation, tire wear, or gearbox calibration can introduce systematic localization errors over long distances.

Modern AMR software continuously converts wheel RPM into estimated vehicle velocity and vice versa. Motion controllers, navigation systems, localization algorithms, and safety functions all depend on these calculations. Although the mathematics appears straightforward, this conversion represents a critical link between mechanical hardware and autonomous software.

Ultimately, Linear Velocity to Wheel RPM Conversion provides the foundation for motor sizing, gearbox selection, control system development, vehicle performance analysis, and navigation system implementation. It is one of the most frequently used calculations throughout the entire AMR development process.

---

### 3.2 Maximum Speed Constraints

Maximum Speed Constraints define the practical upper limit of vehicle velocity that can be achieved safely, efficiently, and reliably. While theoretical calculations may suggest that a vehicle can reach a certain speed based solely on motor power and wheel diameter, real-world AMR performance is limited by numerous mechanical, electrical, dynamic, thermal, and safety considerations.

One of the most obvious speed limitations originates from motor capability. Every electric motor has a maximum operating speed determined by its electromagnetic design, bearing limits, thermal characteristics, and mechanical construction. Exceeding the rated speed may reduce efficiency, increase heat generation, accelerate wear, and potentially damage the motor.

Gearboxes introduce additional limitations. Gear mesh dynamics, lubrication performance, bearing speeds, and mechanical losses become increasingly significant as rotational speed rises. Gearbox manufacturers typically specify maximum input and output RPM limits that should not be exceeded during normal operation.

Wheel diameter directly influences achievable vehicle speed. Larger wheels cover more distance per revolution and therefore allow higher vehicle velocity at the same wheel RPM. However, larger wheels also increase rotational inertia, structural loading, and torque requirements. Consequently, wheel size selection represents a balance between mobility and speed performance.

Traction capability often becomes a dominant limitation. Vehicle acceleration, braking, and turning all depend on friction between the wheels and the floor. As speed increases, maintaining stable traction becomes increasingly difficult. Excessive speed may cause wheel slip, extended stopping distances, reduced path-following accuracy, and degraded safety performance.

Dynamic stability introduces another critical constraint. Every vehicle possesses a center of gravity and experiences dynamic load transfer during motion. At higher speeds, acceleration and turning maneuvers generate larger inertial forces. These forces can reduce wheel contact loads, increase tipping risk, and compromise vehicle controllability.

The relationship between speed and kinetic energy is particularly important:

KE = ½mv²

where:

KE = Kinetic Energy

m = Vehicle Mass

v = Vehicle Velocity

This equation demonstrates that kinetic energy increases with the square of velocity. Doubling vehicle speed results in four times the kinetic energy. Consequently, braking systems, structural components, and safety mechanisms must absorb significantly greater energy as speed increases.

Heavy-duty industrial AMRs are especially affected by this relationship. A 1000 kg vehicle traveling at 2 m/s contains substantially more kinetic energy than a 200 kg vehicle traveling at the same speed. Stopping distance, impact severity, and safety requirements therefore increase dramatically with vehicle mass.

Thermal limitations also influence maximum speed. Higher speeds often require higher motor currents, increased switching activity within motor controllers, and greater mechanical losses. Continuous operation near maximum speed may produce excessive heat in motors, gearboxes, batteries, and power electronics. Thermal management systems must ensure temperatures remain within safe operating limits.

Floor conditions represent another practical constraint. Smooth epoxy floors allow higher operating speeds than rough concrete surfaces. Floor joints, cracks, ramps, and obstacles generate dynamic impacts that become more severe as vehicle speed increases. Excessive vibration may damage sensors, reduce localization accuracy, and shorten component lifespan.

Sensor performance frequently limits speed in autonomous systems. Cameras require sufficient exposure time to capture clear images. LiDAR systems must process large amounts of environmental data. Localization and navigation algorithms require adequate time to detect obstacles and plan safe trajectories. As speed increases, available reaction time decreases significantly.

Human safety considerations often dominate industrial AMR speed limits. Facilities where humans and robots share workspaces typically impose strict speed restrictions. International safety standards frequently define maximum allowable speeds based on vehicle mass, operating environment, stopping distance, and collision risk.

Communication and control system performance can also become limiting factors. High-speed operation demands rapid sensor updates, fast control loops, low-latency communication, and accurate motion estimation. Any delays within the control architecture may reduce stability and responsiveness.

Payload characteristics must also be considered. High-mounted payloads increase the center of gravity and reduce stability margins. Sensitive inspection equipment may impose vibration limits that restrict allowable vehicle speed. Mobile manipulators often operate at lower speeds to maintain positioning accuracy and system stability.

Modern industrial AMR development therefore approaches maximum speed as a systems engineering problem rather than a simple motor selection exercise. Engineers evaluate traction limits, stability margins, thermal performance, structural integrity, sensor capability, safety requirements, and operational constraints simultaneously.

In practical industrial environments, most indoor logistics AMRs operate between 1 and 2 m/s, while heavy-duty industrial AMRs carrying 500 kg to 1500 kg payloads typically operate between 1 and 1.5 m/s. Although higher speeds may be theoretically achievable, reliability, safety, precision, and operational efficiency often favor more conservative speed limits.

Ultimately, Maximum Speed Constraints ensure that an AMR remains safe, controllable, efficient, and reliable throughout its operational life. Proper speed limitation is not a compromise in performance but rather a critical element of robust industrial robot design.

### 3.1 선속도와 휠 RPM 변환(Linear Velocity to Wheel RPM Conversion)

차량의 선속도(Linear Velocity)를 휠 회전 속도(Wheel RPM)로 변환하는 것은 이동 로봇(Mobile Robot) 설계에서 가장 기본적이면서도 중요한 계산 중 하나이다. 모든 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)은 결국 휠의 회전을 통해 이동한다. 사용자는 일반적으로 차량 성능을 m/s 또는 km/h와 같은 선속도로 정의하지만, 모터(Motor)와 감속기(Gearbox)는 RPM(Revolutions Per Minute) 단위로 동작한다. 따라서 차량 속도와 휠 RPM 사이의 정확한 관계를 이해하는 것은 필수적이다.

이 변환은 휠의 원주(Circumference) 개념에서 시작된다. 휠이 한 바퀴 회전하면 이동하는 거리는 휠의 원주와 동일하다.

휠 원주는 다음과 같이 계산된다.

C = π × D

여기서

C = 휠 원주(Wheel Circumference)

D = 휠 직경(Wheel Diameter)

이다.

이 식은 직경이 큰 휠일수록 한 번 회전할 때 더 긴 거리를 이동함을 의미한다. 따라서 휠 직경은 동일한 차량 속도를 달성하기 위해 필요한 RPM에 직접적인 영향을 준다.

차량의 선속도는 다음과 같이 표현할 수 있다.

V = C × N

여기서

V = 선속도(Linear Velocity)

C = 휠 원주

N = 초당 회전수(Revolutions per Second)

이다.

이를 변형하면

N = V / C

가 된다.

실제 모터와 감속기 사양은 대부분 RPM 단위를 사용하므로 다음과 같이 변환한다.

RPM = (V × 60) / (π × D)

이 식은 거의 모든 이동 로봇 설계에서 사용되는 기본 공식이다.

예를 들어 휠 직경이 200mm인 AMR이 1.5m/s 속도로 이동한다고 가정해 보자.

휠 원주는

C = π × 0.2

= 0.628m

이다.

따라서 휠 RPM은

RPM = (1.5 × 60) / 0.628

≈ 143RPM

이 된다.

즉, 차량이 1.5m/s로 주행하기 위해서는 휠이 약 143RPM으로 회전해야 한다.

이 관계는 중요한 설계 특성을 보여준다. 큰 휠은 같은 차량 속도를 달성하기 위해 더 낮은 RPM을 필요로 한다. 반대로 작은 휠은 더 높은 RPM이 필요하다. 이는 감속기 선정, 모터 속도 요구사항, 구동계 효율에 직접적인 영향을 준다.

실제 AMR 개발에서는 휠 RPM을 독립적으로 결정하지 않는다. 휠 직경, 모터 특성, 감속비(Gear Ratio), 목표 속도를 동시에 최적화한다. 모터는 특정 RPM 영역에서 가장 높은 효율을 보이기 때문에 휠 크기와 감속비는 모터 특성과 함께 설계된다.

감속기는 이 과정에서 매우 중요한 역할을 한다. 대부분의 전기 모터는 수천 RPM으로 회전하지만 AMR의 휠은 일반적으로 수백 RPM 수준으로 동작한다.

모터 RPM과 휠 RPM의 관계는 다음과 같다.

Motor RPM = Wheel RPM × Gear Ratio

예를 들어 휠이 150RPM이 필요하고 감속비가 20:1이라면

Motor RPM = 150 × 20

= 3000RPM

이 된다.

이는 많은 산업용 브러시리스 모터(Brushless Motor)가 가장 효율적으로 동작하는 영역에 해당한다.

가속 성능도 고려해야 한다. 정속 주행에서는 일정 RPM만 필요하지만, 가속 시에는 RPM이 빠르게 증가해야 한다. 따라서 모터와 제어기는 목표 RPM까지 충분히 빠르게 도달할 수 있어야 한다.

구동 방식에 따라서도 RPM 제어는 달라진다.

차동 구동(Differential Drive)은 회전 시 좌우 휠 RPM이 서로 달라진다. 회전 반경(Turning Radius)에 따라 한쪽 휠은 더 빠르게, 다른 쪽 휠은 더 느리게 회전한다.

스티어 구동(Steer Drive)은 휠 방향을 조향하여 회전하므로 상대적으로 휠 RPM 차이가 작다.

옴니 드라이브(Omni Drive)는 여러 개의 휠 RPM을 동시에 제어하여 원하는 이동 방향을 생성한다.

휠 슬립(Wheel Slip)도 고려해야 한다. 이론식은 순수 구름 운동(Pure Rolling Motion)을 가정하지만 실제 산업 환경에서는 가속, 제동, 저마찰 바닥에서 미세한 슬립이 발생할 수 있다. 따라서 실제 속도와 계산 속도는 약간 차이가 발생할 수 있다.

오도메트리(Odometry) 시스템 역시 RPM 정보를 활용한다. 엔코더(Encoder)가 측정한 RPM을 이용하여 차량 이동 거리를 계산한다. 따라서 휠 직경 오차, 타이어 마모(Tire Wear), 감속기 오차는 장거리 이동 시 누적 위치 오차(Localization Error)를 발생시킬 수 있다.

현대 AMR 소프트웨어는 RPM과 선속도를 지속적으로 상호 변환한다. 모션 제어(Motion Control), 내비게이션(Navigation), 위치추정(Localization), 안전 제어(Safety Control) 모두 이 계산에 의존한다.

결국 선속도와 휠 RPM 변환은 단순한 수학 공식이 아니라 모터 선정, 감속기 설계, 제어기 개발, 내비게이션 구현, 차량 성능 분석의 기초가 되는 핵심 계산이다.

---

### 3.2 최대 속도 제한 요소(Maximum Speed Constraints)

최대 속도 제한(Maximum Speed Constraint)은 차량이 안전하고 효율적으로 운용될 수 있는 최고 속도를 결정하는 요소이다. 이론적으로는 모터 출력과 휠 크기만으로 매우 높은 속도를 달성할 수 있을 것처럼 보이지만, 실제 산업용 AMR의 속도는 기계적(Mechanical), 전기적(Electrical), 동적(Dynamic), 열적(Thermal), 안전(Safety) 요소들에 의해 제한된다.

가장 기본적인 제한 요소는 모터 성능이다. 모든 전기 모터는 최대 회전 속도(Maximum RPM)를 가진다. 이 한계를 초과하면 효율 저하, 발열 증가, 베어링 수명 감소, 심지어 모터 손상까지 발생할 수 있다.

감속기 역시 속도 제한을 가진다. 기어 맞물림(Gear Mesh), 윤활(Lubrication), 베어링 속도 한계, 기계적 손실(Mechanical Loss)은 RPM이 증가할수록 더욱 중요해진다. 대부분의 감속기 제조사는 입력 RPM과 출력 RPM의 최대 허용치를 제공한다.

휠 직경은 최대 속도에 직접적인 영향을 준다. 큰 휠은 동일 RPM에서 더 긴 거리를 이동하므로 더 높은 차량 속도를 제공한다. 그러나 동시에 회전 관성(Rotational Inertia)이 증가하고 더 큰 토크가 필요하다.

접지력(Traction)도 중요한 제한 요소이다. 가속, 제동, 회전은 모두 휠과 바닥 사이의 마찰력(Friction Force)에 의존한다. 속도가 높아질수록 접지력 확보가 어려워지며 슬립이 발생하기 쉽다.

동적 안정성(Dynamic Stability)은 더욱 중요하다. 모든 차량은 무게중심(Center of Gravity)을 가지고 있으며, 고속 주행 시 관성력(Inertial Force)이 증가한다. 이 힘은 하중 이동(Load Transfer)을 유발하며 전복 위험(Tipping Risk)을 증가시킬 수 있다.

속도와 운동 에너지의 관계는 다음과 같다.

KE = ½mv²

여기서

KE = 운동 에너지(Kinetic Energy)

m = 질량(Mass)

v = 속도(Velocity)

이다.

이 식은 속도가 두 배 증가하면 운동 에너지가 네 배 증가함을 의미한다.

예를 들어 1000kg AMR이 2m/s로 주행할 경우 200kg AMR보다 훨씬 더 큰 운동 에너지를 가진다. 따라서 제동 거리(Stopping Distance), 충돌 에너지(Collision Energy), 안전 요구사항이 크게 증가한다.

열 제한(Thermal Limitation)도 중요하다. 속도가 증가하면 모터 전류(Motor Current), 인버터 스위칭(Inverter Switching), 기계적 손실이 증가한다. 장시간 최고 속도로 운행하면 모터, 감속기, 배터리, 전력 전자장치(Power Electronics)의 온도가 상승할 수 있다.

바닥 상태(Floor Condition) 역시 속도 제한에 영향을 준다. 평탄한 에폭시 바닥은 높은 속도를 허용하지만, 콘크리트 바닥, 바닥 이음새(Floor Joint), 경사로, 장애물은 속도 증가에 따라 충격 하중을 크게 증가시킨다.

센서 성능(Sensor Performance)은 자율주행 차량에서 매우 중요한 제한 요소이다.

카메라는 충분한 노출 시간(Exposure Time)이 필요하며,

LiDAR는 환경 데이터를 처리해야 하고,

위치추정 알고리즘(Localization Algorithm)은 계산 시간을 필요로 한다.

속도가 증가할수록 장애물 감지와 회피에 사용할 수 있는 시간이 줄어든다.

사람과 협업하는 산업 환경에서는 안전 규정(Safety Regulation)이 가장 큰 제한 요소가 되는 경우가 많다. 국제 안전 표준은 차량 질량, 정지 거리, 충돌 위험에 따라 허용 가능한 최고 속도를 제한한다.

통신 및 제어 시스템도 영향을 준다. 고속 주행에서는 센서 업데이트 주기(Update Rate), 제어 주기(Control Loop), 통신 지연(Latency), 위치 추정 정확도가 더욱 중요해진다.

페이로드 특성(Payload Characteristic)도 고려해야 한다. 높은 위치에 장착된 페이로드는 무게중심을 상승시키고 안정성을 감소시킨다. 또한 정밀 검사 장비는 진동 제한 때문에 속도를 낮게 유지해야 할 수도 있다.

따라서 현대 산업용 AMR에서는 최대 속도를 단순히 모터 출력만으로 결정하지 않는다. 접지력, 안정성, 열 성능, 구조 강도, 센서 성능, 안전성, 운용 환경을 모두 종합적으로 고려한다.

실제 산업 현장에서 일반적인 속도 범위는 다음과 같다.

\* 실내 물류 AMR(Indoor Logistics AMR) : 1\~2m/s

\* 산업용 중량 AMR(500\~1500kg급) : 1\~1.5m/s

\* 실외 산업용 AMR(Outdoor Industrial AMR) : 2\~5m/s

\* 특수 고속 무인 차량(Special High-Speed UGV) : 10m/s 이상

그러나 대부분의 공장 환경에서는 안전성과 정밀성을 위해 1\~2m/s 수준으로 제한하는 경우가 많다.

결론적으로 최대 속도 제한은 성능 부족의 결과가 아니라 안전성, 신뢰성, 정밀성, 에너지 효율을 확보하기 위한 필수 설계 요소이다. 특히 힐스로보틱스(Hills Robotics)의 500kg\~1500kg급 산업용 AMR에서는 최고 속도보다 정지 정확도(Position Accuracy), 안정성(Stability), 검사 품질(Inspection Quality), 시스템 신뢰성(System Reliability)이 더욱 중요하며, 따라서 일반적으로 1.0\~1.5m/s 수준이 가장 현실적이고 효율적인 운용 영역이라고 볼 수 있다.

##  

## 04 Gear Ratio Selection

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Reduction Ratio Selection Principles

Reduction Ratio Selection is one of the most important decisions in the design of an Autonomous Mobile Robot (AMR) drivetrain because it directly determines the relationship between motor speed, wheel speed, output torque, acceleration capability, climbing performance, energy efficiency, and maximum vehicle speed. The gearbox serves as the mechanical interface between the high-speed, relatively low-torque electric motor and the low-speed, high-torque wheel system. Selecting an appropriate reduction ratio therefore requires balancing multiple and often competing performance requirements.

Electric motors generally operate most efficiently at relatively high rotational speeds. Modern brushless DC motors and permanent magnet synchronous motors frequently achieve their highest efficiency between several thousand and several tens of thousands of revolutions per minute. However, AMR wheels usually rotate at only a few hundred revolutions per minute. A gearbox is therefore required to reduce rotational speed while multiplying torque.

The basic relationship can be expressed as:

Output Torque = Motor Torque × Gear Ratio × Efficiency

and

Output Speed = Motor Speed ÷ Gear Ratio

These equations illustrate the fundamental trade-off of gearbox design. Increasing the reduction ratio increases available wheel torque but decreases maximum wheel speed. Conversely, reducing the gear ratio increases wheel speed but decreases available traction force and acceleration capability.

The selection process typically begins with vehicle performance requirements. Engineers first define payload capacity, maximum speed, acceleration targets, slope climbing requirements, obstacle crossing capability, and expected operating conditions. These requirements determine the wheel torque needed under the most demanding conditions.

For example, a light-duty logistics AMR operating on smooth indoor floors may prioritize speed and efficiency. Such vehicles often use relatively modest reduction ratios because torque requirements are moderate. In contrast, heavy-duty industrial AMRs transporting payloads of 1000 kg or more typically require substantially higher wheel torque. These systems often employ larger reduction ratios to achieve the required traction and acceleration performance.

Acceleration requirements strongly influence ratio selection. High acceleration demands require significant wheel torque. If a low reduction ratio is selected, the motor itself must generate more torque, potentially requiring a larger motor. A higher reduction ratio allows a smaller motor to generate the required wheel torque but may limit top speed.

Slope climbing capability introduces additional considerations. When an AMR ascends an incline, part of the motor output must overcome gravitational force. The required climbing torque increases with vehicle mass and slope angle. Outdoor AMRs operating on ramps, uneven terrain, or construction sites often require higher reduction ratios than indoor warehouse robots.

Wheel diameter also plays an important role. Larger wheels require greater torque to generate the same tractive force at the ground. Consequently, increasing wheel diameter frequently necessitates an increase in gearbox reduction ratio. This relationship becomes especially important when designing outdoor AMRs where larger wheels are often required for obstacle negotiation and ground clearance.

Motor operating efficiency should also be considered. Every motor has an efficiency map that relates speed and torque to electrical efficiency. Ideally, the selected reduction ratio should allow the motor to operate near its optimal efficiency region during normal operation. A poorly selected ratio may force the motor into low-efficiency regions, increasing heat generation and reducing battery runtime.

Drive cycle analysis is commonly used to refine reduction ratio selection. Rather than evaluating a single operating point, engineers analyze the complete mission profile, including acceleration, cruising, turning, stopping, loading, and unloading phases. The gearbox ratio is then optimized to provide acceptable performance across the entire operating envelope.

Thermal considerations are equally important. Excessive torque demands at low motor speeds can increase current draw and heat generation. A properly selected reduction ratio reduces motor loading and improves thermal performance. This becomes particularly critical in heavy-duty industrial robots operating continuously for many hours.

Mechanical durability must also be considered. Very high reduction ratios may require multiple gear stages, increasing gearbox size, weight, cost, and complexity. Additional gear stages introduce more components, higher losses, and greater maintenance requirements. Engineers therefore seek the lowest reduction ratio that still satisfies performance requirements.

Safety and controllability influence gearbox selection as well. Excessively aggressive gearing may produce very high wheel torque, increasing the likelihood of wheel slip during acceleration. Insufficient gearing may reduce braking effectiveness and limit the ability to control vehicle motion precisely.

Modern AMR development frequently relies on simulation-based optimization to select reduction ratios. Vehicle dynamics models evaluate acceleration performance, energy consumption, thermal behavior, traction utilization, and mission completion time under various gearing configurations. These simulations allow engineers to identify balanced solutions before physical prototypes are built.

Ultimately, Reduction Ratio Selection is not simply a gearbox calculation. It is a system-level optimization process involving motor performance, vehicle dynamics, payload requirements, energy efficiency, safety considerations, and operational objectives. A well-chosen reduction ratio enables the AMR to achieve its performance targets while maximizing efficiency, reliability, and lifecycle value.

---

### 4.2 Efficiency and Back Drivability

Efficiency and Back Drivability are two of the most important characteristics of a gearbox and drivetrain system. Although gear reduction is primarily introduced to increase torque and reduce speed, the gearbox also influences energy losses, thermal behavior, regenerative braking capability, safety characteristics, and overall vehicle responsiveness. Understanding the relationship between efficiency and back drivability is therefore essential for selecting an appropriate drivetrain architecture.

Gearbox efficiency describes how effectively mechanical power is transmitted from the motor to the wheels. No gearbox operates with perfect efficiency because energy is always lost through friction, gear tooth contact, bearing resistance, lubricant shear, seal drag, and structural deformation. These losses are converted into heat and reduce the usable power delivered to the wheels.

Efficiency can be expressed as:

Efficiency = Output Power ÷ Input Power

A gearbox with 95% efficiency transfers 95% of the motor\'s mechanical power to the output shaft while losing 5% as heat. Even small efficiency differences can have significant effects on battery life and thermal management in continuously operating AMRs.

Different gearbox technologies exhibit different efficiency characteristics. Spur gear and helical gear systems often achieve efficiencies above 90%. Planetary gearboxes generally provide high torque density with efficiencies typically ranging between 90% and 97%. Harmonic drives usually exhibit lower efficiencies because of elastic deformation within the flex spline mechanism. Worm gear systems often have significantly lower efficiency due to extensive sliding contact between gear surfaces.

Efficiency becomes particularly important in battery-powered robots. Every percentage point of efficiency improvement reduces energy consumption and extends operating time. For fleets of industrial AMRs operating continuously throughout a facility, drivetrain efficiency directly influences operational costs and charging infrastructure requirements.

Thermal management is closely linked to efficiency. Energy lost through friction appears as heat within the gearbox. Excessive losses can increase gearbox temperature, accelerate lubricant degradation, reduce component life, and potentially lead to overheating. High-efficiency drivetrains therefore contribute to improved reliability and reduced maintenance requirements.

Back Drivability refers to the ability of an external force acting on the output shaft to rotate the input shaft. In practical terms, a back-drivable gearbox allows forces applied at the wheels to drive the motor backward. A non-back-drivable gearbox resists such motion and effectively locks the drivetrain when motor torque is removed.

The degree of back drivability depends primarily on gearbox type, reduction ratio, friction level, and mechanical design. Low-ratio planetary gearboxes are often highly back-drivable. Worm gear systems, especially those with high reduction ratios, are frequently self-locking and exhibit very limited back drivability.

Back drivability strongly influences vehicle behavior during manual movement. Maintenance personnel may occasionally need to push an AMR without electrical power. Highly back-drivable drivetrains allow the vehicle to be moved relatively easily. Non-back-drivable systems may require mechanical release mechanisms or powered disengagement systems.

Regenerative braking capability is another important consideration. When an AMR decelerates, its kinetic energy can potentially be converted back into electrical energy and stored in the battery. Effective regenerative braking requires drivetrain back drivability because the wheels must be able to drive the motor as a generator. Highly back-drivable gearboxes therefore support more efficient energy recovery.

Safety characteristics are also affected. In some applications, self-locking gearboxes provide an advantage because they prevent uncontrolled motion when power is removed. This is particularly valuable in lifting systems, vertical actuators, and inclined environments. However, self-locking behavior may reduce energy efficiency and limit controllability.

Dynamic response is influenced as well. Back-drivable systems often provide smoother interaction between the vehicle and its environment. Wheel forces, floor disturbances, and external loads can be transmitted through the drivetrain more naturally, improving force control and compliance characteristics.

The trade-off between efficiency and back drivability is often significant. Systems designed for maximum efficiency tend to exhibit lower internal friction and higher back drivability. Systems designed for self-locking behavior typically rely on higher friction levels, reducing efficiency.

Industrial AMRs frequently favor high-efficiency planetary gearboxes because they provide an excellent balance of torque density, efficiency, durability, and moderate back drivability. Outdoor robots and collaborative mobile platforms often benefit from this combination because it supports energy-efficient operation while maintaining controllability.

Heavy-duty industrial vehicles may sometimes prioritize holding capability and safety over maximum efficiency. In such cases, partial self-locking behavior or supplemental braking systems may be incorporated to prevent unintended movement.

Ultimately, Efficiency and Back Drivability should be evaluated together rather than independently. A gearbox with excellent efficiency but poor controllability may not satisfy operational requirements. Conversely, a highly controllable system with excessive losses may suffer from reduced range and increased operating costs. Successful AMR drivetrain design therefore requires a balanced evaluation of power transmission efficiency, regenerative capability, manual handling requirements, safety objectives, thermal performance, and overall vehicle behavior.

### 4.1 감속비 선정 원칙(Reduction Ratio Selection Principles)

감속비 선정(Reduction Ratio Selection)은 자율주행 이동 로봇(Autonomous Mobile Robot, AMR) 구동계 설계에서 가장 중요한 결정 중 하나이다. 감속비는 모터 회전 속도(Motor Speed), 휠 회전 속도(Wheel Speed), 출력 토크(Output Torque), 가속 성능(Acceleration Capability), 등판 성능(Climbing Performance), 에너지 효율(Energy Efficiency), 최고 속도(Maximum Speed) 사이의 관계를 결정한다. 감속기(Gearbox)는 고속·저토크 특성을 가진 전기 모터와 저속·고토크가 필요한 휠 시스템을 연결하는 핵심 기계 요소이므로, 적절한 감속비를 선택하는 것은 전체 차량 성능을 좌우한다.

전기 모터는 일반적으로 높은 회전수 영역에서 가장 효율적으로 동작한다. 최신 브러시리스 DC 모터(Brushless DC Motor)와 영구자석 동기 모터(Permanent Magnet Synchronous Motor)는 수천 RPM에서 가장 높은 효율을 나타낸다. 반면 산업용 AMR의 휠은 보통 수십\~수백 RPM 수준으로 회전한다. 따라서 모터 속도를 낮추고 토크를 증가시키기 위해 감속기가 필요하다.

감속기의 기본 관계식은 다음과 같다.

Output Torque = Motor Torque × Gear Ratio × Efficiency

Output Speed = Motor Speed ÷ Gear Ratio

이 식은 감속기의 가장 중요한 특성을 보여준다. 감속비를 높이면 휠 토크가 증가하지만 최고 속도는 감소한다. 반대로 감속비를 낮추면 최고 속도는 증가하지만 휠에 전달되는 토크는 감소한다.

감속비 선정은 일반적으로 차량 요구사항 분석에서 시작된다. 엔지니어는 먼저 페이로드(Payload), 최고 속도(Maximum Speed), 목표 가속도(Target Acceleration), 등판 성능(Gradeability), 장애물 극복 능력(Obstacle Negotiation), 운용 환경(Operating Environment)을 정의한다. 이러한 요구사항을 바탕으로 필요한 휠 토크를 계산하게 된다.

예를 들어 실내 물류용 경량 AMR(Light-Duty Logistics AMR)은 속도와 효율을 우선시하는 경우가 많다. 따라서 비교적 낮은 감속비를 적용할 수 있다. 반면 1000kg 이상의 중량급 산업용 AMR은 높은 견인력(Traction Force)과 가속 성능이 요구되므로 더 높은 감속비가 필요하다.

가속 성능은 감속비 결정에 직접적인 영향을 준다. 높은 가속도를 요구할수록 더 큰 휠 토크가 필요하다. 낮은 감속비를 사용하면 모터 자체가 더 큰 토크를 생성해야 하므로 대형 모터가 필요할 수 있다. 반면 높은 감속비를 사용하면 작은 모터로도 충분한 휠 토크를 얻을 수 있지만 최고 속도는 감소하게 된다.

등판 성능도 중요한 요소이다. 차량이 경사를 오를 때는 중력(Gravity)을 극복하기 위한 추가 토크가 필요하다. 차량 질량이 크고 경사도가 높을수록 요구 토크는 증가한다. 따라서 실외 AMR(Outdoor AMR)은 일반적으로 실내 물류 AMR보다 더 높은 감속비를 적용하는 경우가 많다.

휠 직경(Wheel Diameter) 역시 감속비에 영향을 준다. 큰 휠은 동일한 추진력을 생성하기 위해 더 큰 토크가 필요하다. 따라서 휠 직경이 증가하면 감속비도 함께 증가하는 경우가 많다. 특히 실외 AMR은 지상고(Ground Clearance) 확보와 장애물 통과 능력 향상을 위해 큰 휠을 사용하므로 감속비 선정이 더욱 중요해진다.

모터 효율(Motor Efficiency)도 반드시 고려해야 한다. 모든 모터는 특정 속도와 토크 영역에서 가장 높은 효율을 가진다. 이상적인 감속비는 차량이 정상 운용 시 모터가 이러한 최적 효율 영역에서 동작하도록 만들어야 한다. 잘못된 감속비는 모터를 비효율 영역으로 밀어 넣어 발열 증가와 배터리 사용 시간 감소를 초래한다.

실제 AMR 개발에서는 주행 사이클 분석(Drive Cycle Analysis)을 수행한다. 단일 운용 조건이 아니라 가속, 정속 주행, 회전, 정지, 적재, 하역 등을 포함한 전체 미션 프로파일(Mission Profile)을 분석하여 최적 감속비를 찾는다.

열 관리(Thermal Management)도 중요한 고려 요소이다. 낮은 회전수에서 과도한 토크를 요구하면 모터 전류가 증가하고 발열이 커진다. 적절한 감속비는 모터 부하를 줄이고 냉각 요구사항을 완화한다. 이는 장시간 운행하는 산업용 AMR에서 매우 중요하다.

기계적 내구성(Mechanical Durability)도 감속비와 관련된다. 지나치게 높은 감속비는 다단 기어(Multi-Stage Gear)를 필요로 하며 감속기의 크기, 무게, 비용, 복잡성을 증가시킨다. 또한 기어 단수가 증가할수록 손실도 증가한다. 따라서 엔지니어는 성능 요구를 만족하는 범위 내에서 가능한 낮은 감속비를 선택하려고 한다.

안전성과 제어성(Controllability)도 고려해야 한다. 지나치게 높은 감속비는 휠 토크를 과도하게 증가시켜 슬립(Slip)을 유발할 수 있다. 반대로 너무 낮은 감속비는 제동 성능과 정밀 제어 능력을 저하시킬 수 있다.

현대 AMR 개발에서는 차량 동역학 시뮬레이션(Vehicle Dynamics Simulation)을 이용하여 감속비를 최적화한다. 다양한 감속비에 대해 가속 성능, 에너지 소비, 발열, 견인력, 작업 시간 등을 분석하여 최적 설계를 도출한다.

결국 감속비 선정은 단순한 기어 계산이 아니라 모터 성능, 차량 동역학, 페이로드, 에너지 효율, 안전성, 운용 목적을 동시에 고려하는 시스템 수준(System-Level)의 최적화 과정이다. 적절한 감속비는 성능과 효율, 신뢰성의 균형을 달성하게 해준다.

---

### 4.2 효율과 역구동성(Efficiency and Back Drivability)

효율(Efficiency)과 역구동성(Back Drivability)은 감속기와 구동계 설계에서 가장 중요한 특성 중 두 가지이다. 감속기는 단순히 토크를 증가시키고 속도를 감소시키는 역할만 하는 것이 아니라 에너지 손실(Energy Loss), 발열(Thermal Behavior), 회생 제동(Regenerative Braking), 안전성(Safety), 주행 응답성(Response)을 결정하는 핵심 요소이다.

감속기 효율은 모터의 기계적 출력이 얼마나 효과적으로 휠까지 전달되는지를 나타낸다. 실제로는 어떠한 감속기도 100% 효율을 가질 수 없다. 기어 맞물림 마찰(Gear Tooth Friction), 베어링 저항(Bearing Resistance), 윤활유 전단(Lubricant Shear), 씰 마찰(Seal Drag), 구조 변형(Structural Deformation)에 의해 일부 에너지가 열로 변환된다.

효율은 다음과 같이 정의된다.

Efficiency = Output Power ÷ Input Power

예를 들어 효율이 95%인 감속기는 입력된 기계적 에너지의 95%를 출력으로 전달하고 5%를 열로 손실한다.

이러한 작은 차이도 배터리 기반 AMR에서는 매우 큰 영향을 미친다. 효율이 1%만 향상되어도 전체 운행 시간과 충전 주기에 상당한 차이를 만들 수 있다.

감속기 종류에 따라 효율 특성이 다르다.

스퍼 기어(Spur Gear)와 헬리컬 기어(Helical Gear)는 일반적으로 90% 이상의 효율을 가진다.

유성 감속기(Planetary Gearbox)는 높은 토크 밀도(Torque Density)와 함께 90\~97% 수준의 높은 효율을 제공한다.

하모닉 드라이브(Harmonic Drive)는 플렉스 스플라인(Flex Spline)의 탄성 변형 때문에 상대적으로 효율이 낮다.

웜 기어(Worm Gear)는 미끄럼 접촉(Sliding Contact)이 많기 때문에 효율이 낮은 편이다.

효율은 열 관리와도 밀접하게 연결된다. 감속기 내부 손실은 모두 열로 변환된다. 과도한 열은 윤활유 열화(Lubricant Degradation), 부품 수명 감소(Component Life Reduction), 과열(Overheating)을 초래할 수 있다.

역구동성(Back Drivability)은 외부 힘이 출력축(Output Shaft)을 통해 입력축(Input Shaft)을 역방향으로 회전시킬 수 있는 능력을 의미한다. 쉽게 말해 휠이 모터를 거꾸로 돌릴 수 있는 능력이다.

역구동성이 높은 감속기는 외부 힘이 휠에 가해지면 모터를 역회전시킬 수 있다. 반대로 역구동성이 낮은 감속기는 이러한 움직임을 억제하며 사실상 잠금(Locking) 상태를 형성한다.

역구동성은 감속기 종류, 감속비, 내부 마찰 수준에 의해 결정된다.

저감속 유성 감속기는 일반적으로 역구동성이 높다.

고감속 웜 기어는 자기잠금(Self-Locking) 특성을 가지며 역구동성이 매우 낮다.

역구동성은 정비 및 유지보수에도 영향을 준다. 전원이 꺼진 상태에서 AMR을 밀어서 이동해야 하는 경우가 있다. 역구동성이 높은 감속기는 비교적 쉽게 이동할 수 있지만, 역구동성이 낮은 감속기는 별도의 해제 장치(Release Mechanism)가 필요할 수 있다.

회생 제동(Regenerative Braking)도 역구동성과 밀접하게 관련된다. 차량이 감속할 때 운동 에너지를 전기에너지로 변환하여 배터리에 저장하려면 휠이 모터를 발전기(Generator)처럼 구동해야 한다. 따라서 회생 제동을 효과적으로 사용하려면 높은 역구동성이 필요하다.

안전성 측면에서는 상황이 다를 수 있다. 일부 시스템은 전원이 차단되었을 때 차량이 움직이지 않아야 한다. 특히 리프터(Lifter), 수직 액추에이터(Vertical Actuator), 경사면 운행 차량에서는 자기잠금 특성이 안전성을 향상시킨다.

주행 응답성도 영향을 받는다. 역구동성이 높은 시스템은 외부 힘과 노면 충격이 보다 자연스럽게 전달된다. 따라서 힘 제어(Force Control)와 순응 제어(Compliance Control)에 유리하다.

효율과 역구동성은 서로 밀접한 관계를 가진다. 일반적으로 효율이 높은 감속기는 내부 마찰이 적으므로 역구동성도 높은 경우가 많다. 반대로 자기잠금 특성을 가진 감속기는 마찰이 크므로 효율이 낮은 경우가 많다.

산업용 AMR에서는 유성 감속기가 가장 널리 사용된다. 높은 효율, 우수한 토크 밀도, 적절한 역구동성, 긴 수명을 동시에 제공하기 때문이다. 특히 실내 물류 AMR과 실외 산업용 AMR 모두에 적합한 균형 잡힌 솔루션이다.

중량급 산업용 차량에서는 경우에 따라 유지력(Holding Capability)과 안전성을 더 중요하게 고려하기도 한다. 이러한 경우에는 보조 브레이크(Supplemental Brake) 또는 부분 자기잠금 구조가 추가되기도 한다.

결국 효율과 역구동성은 별개로 평가할 수 있는 특성이 아니다. 효율만 높고 제어성이 부족한 시스템은 실제 운용에 적합하지 않을 수 있다. 반대로 제어성은 우수하지만 손실이 과도한 시스템은 운행 시간 감소와 운영 비용 증가를 초래한다.

특히 힐스로보틱스(Hills Robotics)의 500kg\~1500kg급 산업용 AMR에서는 효율 90\~95% 이상의 유성 감속기(Planetary Gearbox)와 적절한 역구동성을 확보하는 것이 가장 현실적인 선택이다. 이는 회생 제동, 에너지 효율, 정밀 제어, 유지보수성, 안전성의 균형을 제공하며 실내·실외 AMR 플랫폼 모두에 적합한 구조라고 할 수 있다.

##  

## 05 Motor Selection

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 BLDC vs Servo Motor Comparison

Motor selection is one of the most critical engineering decisions in Autonomous Mobile Robot (AMR) development because the motor directly determines acceleration capability, positioning accuracy, energy efficiency, thermal behavior, reliability, and overall system cost. Among the various motor technologies available today, Brushless DC Motors (BLDC Motors) and Servo Motors are the two most commonly used solutions in industrial mobile robotics. Although both technologies share many similarities, they differ significantly in control architecture, performance characteristics, application suitability, and lifecycle cost.

A BLDC motor is an electronically commutated motor that uses permanent magnets on the rotor and electromagnetic windings on the stator. Unlike traditional brushed motors, BLDC motors eliminate mechanical brushes and commutators, resulting in higher efficiency, lower maintenance requirements, and longer service life. Most modern industrial AMRs employ BLDC technology because of its excellent balance between performance, reliability, and cost.

Servo motors can be viewed as a complete motion-control system rather than simply a motor. A typical servo system consists of a motor, a high-resolution encoder, a servo drive, and a closed-loop control algorithm. The servo controller continuously measures rotor position, velocity, and torque, adjusting motor current in real time to achieve highly accurate motion control.

One of the primary differences between BLDC and servo systems is positioning accuracy. Standard BLDC systems often rely on Hall sensors or moderate-resolution encoders for commutation and speed control. While sufficient for many logistics applications, they may not provide the precision required for advanced positioning tasks. Servo systems, by contrast, frequently utilize high-resolution absolute encoders capable of measuring rotor position with extremely high accuracy. This allows precise speed regulation, smooth low-speed operation, and accurate positioning performance.

Torque behavior also differs significantly. Servo motors are specifically designed to deliver high peak torque over short durations while maintaining precise control. Their control systems continuously regulate current to achieve commanded torque levels. BLDC motors can also generate substantial torque but often rely on simpler control architectures and may exhibit less accurate torque regulation under rapidly changing load conditions.

Low-speed performance is another important consideration. Industrial AMRs performing precision docking, automated charging, machine tending, or robotic manipulation often require smooth motion at extremely low speeds. Servo systems generally excel in these situations because closed-loop feedback continuously compensates for disturbances, friction, and load variations. BLDC systems can achieve good low-speed performance but may require more sophisticated control algorithms to match servo-level smoothness.

Cost considerations often influence motor selection. Servo systems include advanced encoders, dedicated servo drives, and complex control electronics, making them more expensive than conventional BLDC solutions. For large AMR fleets, the cost difference can become significant. Consequently, many logistics robots prioritize BLDC motors because they provide sufficient performance at a lower total system cost.

Efficiency comparisons are more nuanced. Both BLDC and servo motors can achieve high efficiencies under appropriate operating conditions. In practice, overall system efficiency depends heavily on drive tuning, operating point selection, gearbox matching, and duty cycle characteristics rather than motor type alone.

Reliability and maintenance requirements are generally favorable for both technologies because neither uses brushes. However, servo systems contain more sophisticated feedback devices and electronics, which may increase system complexity and diagnostic requirements. Conversely, their advanced monitoring capabilities often improve predictive maintenance and fault detection.

Application requirements ultimately determine the preferred technology. Warehouse logistics AMRs, material transport robots, and standard indoor delivery systems often use BLDC motors due to their excellent cost-performance ratio. High-precision industrial platforms, mobile manipulators, semiconductor automation systems, and inspection robots frequently employ servo motors because of their superior positioning performance and dynamic response.

Heavy-duty industrial AMRs introduce additional considerations. Vehicles carrying payloads between 500 kg and 1500 kg require substantial torque reserves and robust control performance. In these applications, servo systems often provide advantages in acceleration control, traction management, and precision maneuvering. However, high-power BLDC solutions remain viable when cost optimization is a priority.

Modern AMR architectures increasingly blur the distinction between BLDC and servo systems. Many advanced BLDC controllers now incorporate field-oriented control, high-resolution encoder feedback, and sophisticated motion algorithms that approach traditional servo performance. As a result, motor selection should be based on system requirements rather than technology labels alone.

Ultimately, the choice between BLDC and servo motors involves balancing accuracy, performance, complexity, cost, reliability, and application requirements. A well-matched motor solution supports efficient operation, reliable performance, and long-term scalability across the intended deployment environment.

---

### 5.2 Driver Motor Matching

Driver Motor Matching refers to the process of selecting a motor controller, drive electronics, and power architecture that complement the characteristics of the chosen motor. Even the most capable motor cannot deliver its intended performance if paired with an inappropriate driver. Effective matching ensures that the motor operates safely, efficiently, and predictably across the full range of operating conditions encountered by the AMR.

The motor driver serves as the interface between the power system and the motor. It converts battery energy into controlled electrical currents that generate torque and motion. Consequently, the driver must be capable of supplying the voltage, current, switching frequency, and control precision required by the motor.

Voltage matching represents one of the first considerations. Industrial AMRs commonly operate using 24 V, 48 V, 72 V, or higher battery architectures. The motor driver must support the operating voltage range of both the battery system and the motor. Selecting a driver with insufficient voltage capability may limit maximum speed and acceleration performance.

Current capability is equally important. Motor torque is directly related to current. During acceleration, obstacle crossing, hill climbing, and emergency maneuvers, current demand may increase substantially above nominal operating levels. The driver must therefore support both continuous current ratings and peak current requirements without overheating or entering protective shutdown modes.

Control strategy compatibility strongly influences system performance. Modern BLDC and servo systems frequently use Field-Oriented Control (FOC) to maximize efficiency and torque smoothness. The selected driver must support the appropriate control method and sensor interface. Hall sensors, incremental encoders, absolute encoders, and sensorless control techniques each require different hardware and software capabilities.

Communication interfaces play a critical role in system integration. Industrial AMRs typically use CAN, CANopen, EtherCAT, RS-485, Ethernet, or proprietary communication protocols. The motor driver must integrate seamlessly with the vehicle control architecture, enabling reliable exchange of commands, status information, diagnostics, and safety signals.

Thermal performance must also be evaluated carefully. Motor drivers generate heat through semiconductor switching losses and conduction losses. If thermal management is inadequate, performance degradation and reliability issues may occur. Proper heatsinking, airflow design, and thermal monitoring are therefore essential components of driver selection.

Protection features significantly influence system robustness. High-quality motor drivers incorporate overcurrent protection, overvoltage protection, undervoltage detection, thermal shutdown, short-circuit protection, and fault diagnostics. These features improve safety and reduce the likelihood of catastrophic failures.

Regenerative braking capability should also be considered. Many AMRs recover energy during deceleration and return it to the battery. The driver must support bidirectional power flow and manage regenerative energy safely. Inadequate regenerative handling may result in battery overvoltage conditions or wasted energy.

Dynamic response requirements further influence driver selection. Precision applications often require high control-loop frequencies and rapid current regulation. Faster control loops improve torque response, trajectory tracking, and disturbance rejection. Mobile manipulators and inspection robots frequently benefit from these advanced capabilities.

System scalability is another important consideration. Organizations developing multiple AMR models often prefer driver platforms that support a range of motor sizes and power levels. A unified driver architecture simplifies software development, maintenance, inventory management, and long-term product support.

Testing and validation play a critical role in the matching process. Laboratory testing typically evaluates acceleration performance, current consumption, thermal behavior, efficiency, fault response, and communication reliability. Simulation models are increasingly used to predict driver-motor interactions before physical prototypes are constructed.

Ultimately, Driver Motor Matching is not simply an electrical compatibility exercise. It is a system engineering activity that ensures the motor, driver, battery, gearbox, software, and vehicle architecture function together as a coordinated and optimized solution.

---

### 5.3 Selection Checklist

Motor selection in industrial AMR development involves far more than choosing a motor based on torque and speed specifications. A comprehensive Selection Checklist helps engineers evaluate all relevant technical, operational, economic, and safety factors before committing to a particular solution. Such a structured approach reduces design risk and improves the likelihood of achieving project objectives.

The process typically begins by clearly defining vehicle requirements. Payload capacity, total moving mass, target speed, acceleration performance, climbing ability, operating environment, mission duration, and duty cycle characteristics must be understood before motor evaluation begins. These parameters establish the foundation for all subsequent calculations.

Torque requirements should be evaluated under both starting and continuous operating conditions. Peak torque determines acceleration and obstacle-handling capability, while continuous torque influences thermal performance and long-term reliability. Both values must remain within the motor's rated capabilities with appropriate safety margins.

Speed requirements must also be analyzed carefully. Wheel diameter, gearbox ratio, and desired vehicle velocity determine the required motor RPM range. The selected motor should operate efficiently throughout the expected speed envelope rather than only at a single operating point.

Power system compatibility represents another critical checklist item. Battery voltage, available current, regenerative braking requirements, charging architecture, and energy management strategies must align with motor and driver capabilities.

Thermal considerations should never be overlooked. Engineers must evaluate expected operating temperatures, cooling methods, ambient conditions, and thermal margins. Motors that appear suitable under nominal conditions may encounter overheating issues during continuous industrial operation.

Control requirements influence technology selection. Applications requiring precise positioning, smooth low-speed motion, synchronized multi-axis control, or advanced force regulation may justify servo solutions. Less demanding logistics applications may achieve excellent results using BLDC systems.

Reliability and maintenance requirements should be evaluated over the entire product lifecycle. Mean Time Between Failures (MTBF), serviceability, spare-part availability, diagnostic capabilities, and supplier support all influence long-term operational success.

Environmental factors are equally important. Dust, moisture, vibration, shock loading, temperature extremes, and chemical exposure may significantly affect motor performance and durability. Appropriate ingress protection ratings and environmental qualifications should be verified.

Cost evaluation should include more than purchase price alone. Total Cost of Ownership (TCO) incorporates energy consumption, maintenance costs, replacement intervals, downtime risk, inventory requirements, and operational efficiency. A higher-cost motor may ultimately reduce overall system cost through improved performance and reliability.

Safety considerations must also be included in the selection process. Functional safety requirements, emergency stopping behavior, fault tolerance, regenerative braking performance, and compliance with relevant industrial standards should all be reviewed systematically.

Supplier capability represents another often-overlooked factor. Engineering support, documentation quality, lead times, customization options, firmware updates, and long-term product availability can significantly influence project success. Strong supplier partnerships often provide advantages beyond the hardware itself.

Validation testing should serve as the final step in the checklist. Prototype evaluation under realistic operating conditions confirms whether theoretical calculations accurately predict real-world performance. Measurements of speed, torque, efficiency, temperature, energy consumption, and reliability provide valuable feedback before full-scale deployment.

For modern industrial AMRs, particularly those operating in the 500 kg to 1500 kg payload range, motor selection should be treated as a multidisciplinary optimization process rather than a component purchase decision. A comprehensive checklist ensures that mechanical, electrical, software, thermal, economic, and safety considerations are addressed systematically.

Ultimately, a well-executed motor selection process produces an AMR that is efficient, reliable, safe, maintainable, and capable of meeting operational requirements throughout its intended service life.

### 5.1 BLDC 모터와 서보 모터 비교(BLDC vs Servo Motor Comparison)

모터 선정(Motor Selection)은 자율주행 이동 로봇(Autonomous Mobile Robot, AMR) 개발 과정에서 가장 중요한 설계 결정 중 하나이다. 모터는 차량의 가속 성능(Acceleration Capability), 위치 정밀도(Position Accuracy), 에너지 효율(Energy Efficiency), 발열 특성(Thermal Behavior), 신뢰성(Reliability), 그리고 전체 시스템 비용(System Cost)을 결정한다. 현재 산업용 이동 로봇에서 가장 널리 사용되는 기술은 BLDC 모터(Brushless DC Motor)와 서보 모터(Servo Motor)이며, 두 기술은 유사한 점도 많지만 성능 특성과 적용 분야에서 중요한 차이를 가진다.

BLDC 모터는 회전자(Rotor)에 영구자석(Permanent Magnet)을 사용하고 고정자(Stator)에 권선을 배치한 전자식 정류(Electronic Commutation) 방식의 모터이다. 브러시(Brush)와 정류자(Commutator)가 존재하지 않기 때문에 마모가 적고 유지보수성이 우수하며 긴 수명을 제공한다. 현재 대부분의 산업용 AMR은 성능, 신뢰성, 비용의 균형이 우수한 BLDC 모터를 사용한다.

반면 서보 모터는 단순한 모터가 아니라 완전한 모션 제어 시스템(Motion Control System)에 가깝다. 일반적인 서보 시스템은 모터, 고해상도 엔코더(High-Resolution Encoder), 서보 드라이브(Servo Drive), 폐루프 제어기(Closed-Loop Controller)로 구성된다. 제어기는 실시간으로 위치(Position), 속도(Velocity), 토크(Torque)를 측정하고 전류를 조정하여 매우 정밀한 제어를 수행한다.

가장 큰 차이점은 위치 정밀도(Position Accuracy)에 있다. 일반적인 BLDC 시스템은 홀 센서(Hall Sensor) 또는 중간 수준의 엔코더를 사용한다. 물류 AMR과 같은 일반적인 응용에는 충분하지만 초정밀 위치 제어가 필요한 경우에는 한계가 있을 수 있다.

반면 서보 모터는 고해상도 절대형 엔코더(Absolute Encoder)를 사용하는 경우가 많아 매우 정밀한 위치 측정이 가능하다. 따라서 저속 영역에서도 부드러운 제어와 높은 위치 정확도를 제공할 수 있다.

토크 특성(Torque Characteristics)도 차이가 있다. 서보 모터는 짧은 시간 동안 매우 높은 피크 토크(Peak Torque)를 생성하면서도 정밀하게 제어할 수 있도록 설계되어 있다. 전류를 실시간으로 제어하여 목표 토크를 유지할 수 있기 때문이다.

BLDC 모터 역시 높은 토크를 생성할 수 있지만 일반적으로 제어 구조가 단순하며 급격한 부하 변화 상황에서 서보만큼 정밀한 토크 제어를 제공하지 못할 수 있다.

저속 성능(Low-Speed Performance)은 산업용 AMR에서 매우 중요하다. 자동 충전(Auto Charging), 정밀 도킹(Precision Docking), 공작기계 연계(Machine Tending), 모바일 매니퓰레이터(Mobile Manipulator)와 같은 작업은 매우 낮은 속도에서도 부드럽고 안정적인 움직임을 요구한다.

이러한 영역에서는 폐루프 제어를 사용하는 서보 시스템이 일반적으로 우수한 성능을 제공한다. BLDC 시스템도 FOC(Field Oriented Control)와 고성능 엔코더를 적용하면 상당히 우수한 저속 성능을 얻을 수 있지만 일반적으로 서보가 더 유리하다.

비용(Cost)은 중요한 고려 요소이다. 서보 시스템은 고해상도 엔코더, 전용 드라이브, 복잡한 제어 알고리즘이 필요하므로 BLDC 시스템보다 비용이 높다. 수십 대 또는 수백 대 규모의 AMR 플릿(Fleet)을 구축하는 경우 비용 차이는 상당히 커질 수 있다.

효율(Efficiency)은 두 시스템 모두 높은 수준을 달성할 수 있다. 실제 효율은 모터 종류보다도 구동 조건, 감속기 매칭, 제어 알고리즘, 운행 패턴에 의해 더 크게 좌우되는 경우가 많다.

신뢰성 측면에서는 두 시스템 모두 브러시가 없기 때문에 우수하다. 그러나 서보 시스템은 더 많은 센서와 전자장치를 포함하기 때문에 복잡성이 증가할 수 있다. 반대로 진단 기능(Diagnostics)과 상태 모니터링(Condition Monitoring)이 뛰어나 예방 정비(Predictive Maintenance)에 유리한 경우도 많다.

응용 분야에 따라 선택 기준이 달라진다. 물류 AMR(Logistics AMR), 운반 로봇(Material Transport Robot), 일반 실내 배송 로봇은 BLDC 모터가 비용 대비 성능 측면에서 매우 우수하다.

반면 반도체 자동화(Semiconductor Automation), 모바일 매니퓰레이터, 정밀 검사 로봇(Inspection Robot), 공작기계 연계 시스템은 서보 모터가 제공하는 정밀성과 응답성이 필요할 수 있다.

500kg\~1500kg급 중량 산업용 AMR에서는 더욱 신중한 검토가 필요하다. 이러한 차량은 높은 토크와 정밀한 주행 제어가 요구된다. 서보 모터는 정밀 가속 제어와 접지력 제어 측면에서 장점을 제공하지만, 비용 최적화가 중요한 경우 고출력 BLDC 솔루션도 충분히 경쟁력이 있다.

최근에는 BLDC와 서보의 경계가 점차 희미해지고 있다. 최신 BLDC 컨트롤러는 FOC, 고해상도 엔코더, 정교한 제어 알고리즘을 적용하여 전통적인 서보 수준의 성능을 제공하기도 한다.

결국 BLDC와 서보 모터의 선택은 정밀도, 성능, 비용, 복잡성, 신뢰성, 응용 목적 사이의 균형을 맞추는 과정이다.

---

### 5.2 드라이버와 모터 매칭(Driver Motor Matching)

드라이버와 모터 매칭(Driver Motor Matching)은 모터 특성에 적합한 드라이버(Driver), 전력 전자장치(Power Electronics), 전원 아키텍처(Power Architecture)를 선정하는 과정이다. 아무리 우수한 모터라도 적절하지 않은 드라이버와 결합되면 기대한 성능을 발휘할 수 없다. 따라서 모터와 드라이버는 하나의 시스템으로 고려되어야 한다.

모터 드라이버는 배터리 에너지를 제어된 전류(Control Current)로 변환하여 모터를 구동하는 장치이다. 따라서 드라이버는 모터가 요구하는 전압(Voltage), 전류(Current), 스위칭 주파수(Switching Frequency), 제어 정밀도를 제공할 수 있어야 한다.

가장 먼저 고려해야 하는 요소는 전압 매칭(Voltage Matching)이다. 산업용 AMR은 일반적으로 24V, 48V, 72V, 또는 그 이상의 전압 시스템을 사용한다. 드라이버는 배터리 전압과 모터 정격 전압을 모두 지원해야 한다.

전류 용량(Current Capability)도 중요하다. 모터 토크는 전류에 비례한다. 가속, 경사 주행, 장애물 극복 시에는 순간적으로 매우 높은 전류가 필요할 수 있다. 따라서 드라이버는 연속 전류(Continuous Current)뿐 아니라 피크 전류(Peak Current)도 충분히 공급할 수 있어야 한다.

제어 방식(Control Strategy)의 호환성도 중요하다. 현대 BLDC와 서보 시스템은 대부분 FOC(Field Oriented Control)를 사용한다. 따라서 드라이버는 적절한 센서 인터페이스와 제어 알고리즘을 지원해야 한다.

홀 센서(Hall Sensor), 증분형 엔코더(Incremental Encoder), 절대형 엔코더(Absolute Encoder), 센서리스 제어(Sensorless Control)는 각각 다른 하드웨어 및 소프트웨어 기능을 요구한다.

통신 인터페이스(Communication Interface)는 시스템 통합에서 매우 중요하다. 산업용 AMR은 CAN, CANopen, EtherCAT, RS-485, Ethernet 등을 사용한다. 드라이버는 차량 제어기와 안정적으로 통신할 수 있어야 한다.

열 성능(Thermal Performance)도 중요한 고려 사항이다. 드라이버 내부의 전력 반도체(Power Semiconductor)는 스위칭 손실(Switching Loss)과 도통 손실(Conduction Loss)에 의해 열을 발생시킨다. 적절한 방열 구조(Heatsink)와 냉각 설계(Cooling Design)가 필요하다.

보호 기능(Protection Features)은 시스템 신뢰성을 크게 향상시킨다. 고품질 드라이버는 과전류 보호(Overcurrent Protection), 과전압 보호(Overvoltage Protection), 저전압 보호(Undervoltage Protection), 과열 보호(Thermal Shutdown), 단락 보호(Short Circuit Protection), 진단 기능(Diagnostics)을 제공한다.

회생 제동(Regenerative Braking) 지원 여부도 중요하다. 많은 산업용 AMR은 감속 시 운동 에너지를 전기에너지로 회수하여 배터리에 저장한다. 이를 위해 드라이버는 양방향 전력 흐름(Bidirectional Power Flow)을 지원해야 한다.

동적 응답성(Dynamic Response)도 고려해야 한다. 모바일 매니퓰레이터나 정밀 검사 로봇은 매우 빠른 전류 제어 루프(Current Control Loop)와 높은 제어 주파수를 요구할 수 있다.

확장성(Scalability)도 중요하다. 여러 모델의 AMR을 개발하는 기업은 동일한 드라이버 플랫폼을 다양한 모터에 적용하기를 원한다. 이는 소프트웨어 개발, 재고 관리, 유지보수 비용을 줄일 수 있다.

실험과 검증(Test and Validation)은 필수 단계이다. 실제 환경에서 가속 성능, 전류 소비, 발열 특성, 효율, 통신 안정성 등을 검증해야 한다.

결국 드라이버와 모터 매칭은 단순한 전기적 연결이 아니라 모터, 드라이버, 배터리, 감속기, 소프트웨어, 차량 제어기를 하나의 최적화된 시스템으로 통합하는 과정이다.

---

### 5.3 모터 선정 체크리스트(Selection Checklist)

산업용 AMR에서 모터 선정은 단순히 토크와 속도만 비교하는 작업이 아니다. 체계적인 선정 체크리스트(Selection Checklist)를 활용하면 기술적, 경제적, 안전적 요소를 종합적으로 평가할 수 있다.

가장 먼저 차량 요구사항(Vehicle Requirements)을 정의해야 한다. 페이로드, 총 이동 질량(Total Moving Mass), 목표 속도(Target Speed), 가속 성능, 등판 성능, 운용 환경, 미션 시간(Mission Duration), 주행 패턴(Duty Cycle)을 명확히 정의해야 한다.

토크 요구사항(Torque Requirement)은 기동 토크(Starting Torque)와 연속 토크(Continuous Torque)를 모두 계산해야 한다. 기동 토크는 가속 및 장애물 극복 능력을 결정하며, 연속 토크는 발열과 수명에 영향을 준다.

속도 요구사항(Speed Requirement)도 중요하다. 휠 직경, 감속비, 목표 차량 속도를 바탕으로 필요한 모터 RPM 범위를 계산해야 한다.

전원 시스템(Power System)과의 호환성도 검토해야 한다. 배터리 전압, 최대 전류, 회생 제동 요구사항, 충전 방식, 에너지 관리 전략과 모터가 잘 맞아야 한다.

열 관리(Thermal Management)는 반드시 검토해야 한다. 정상 운용 조건뿐 아니라 최대 부하 조건에서의 온도 상승도 확인해야 한다.

제어 요구사항(Control Requirement)도 중요하다. 정밀 위치 제어, 저속 주행, 다축 동기화, 힘 제어가 필요한 경우 서보 모터가 유리할 수 있다. 일반 물류 AMR은 BLDC 모터로도 충분한 경우가 많다.

신뢰성과 유지보수성(Reliability and Maintainability)도 검토해야 한다. 평균 고장 간격(MTBF), 정비 편의성(Serviceability), 예비 부품 공급성(Spare Parts Availability), 제조사 지원 수준을 평가해야 한다.

환경 조건(Environmental Condition)도 고려해야 한다. 먼지(Dust), 습기(Moisture), 진동(Vibration), 충격(Shock), 온도 변화(Temperature Variation), 화학 물질(Chemical Exposure)에 대한 내성을 확인해야 한다.

비용 평가(Cost Evaluation)는 구매 가격만 보는 것이 아니다. 총 소유 비용(Total Cost of Ownership, TCO)을 고려해야 한다. 전력 소비, 유지보수 비용, 교체 주기, 다운타임 위험, 재고 비용까지 포함해야 한다.

안전성(Safety)도 필수 검토 항목이다. 비상 정지(Emergency Stop), 기능 안전(Functional Safety), 회생 제동, 고장 허용(Fault Tolerance), 관련 산업 안전 규격 준수 여부를 검토해야 한다.

공급업체 역량(Supplier Capability)도 중요하다. 기술 지원, 문서 품질, 납기, 커스터마이징 능력, 펌웨어 업데이트, 장기 공급 계획 등을 평가해야 한다.

마지막 단계는 실제 검증(Validation Testing)이다. 프로토타입 차량을 이용하여 속도, 토크, 효율, 발열, 전력 소비, 신뢰성을 실험적으로 확인해야 한다.

500kg\~1500kg급 산업용 AMR에서는 모터 선정이 단순한 부품 구매가 아니라 시스템 엔지니어링(System Engineering)의 핵심 작업이다. 기계 설계(Mechanical Design), 전기 설계(Electrical Design), 소프트웨어(Software), 열 설계(Thermal Design), 안전 공학(Safety Engineering)을 모두 고려해야 한다.

특히 힐스로보틱스(Hills Robotics)의 산업용 AMR 플랫폼 관점에서 보면 다음과 같은 기준이 현실적이다.

\* 50kg\~200kg급 실내 AMR : BLDC + FOC 드라이버

\* 500kg급 산업용 AMR : 고출력 BLDC 또는 엔트리급 서보

\* 1000kg급 산업용 AMR : 서보 모터 권장

\* 1500kg급 이상 산업용 AMR : 고출력 서보 + EtherCAT 기반 드라이브 권장

결국 좋은 모터 선정은 최고 사양의 모터를 선택하는 것이 아니라, 차량의 성능 요구사항과 비용 목표를 동시에 만족시키는 최적의 조합을 찾는 과정이라고 할 수 있다.
