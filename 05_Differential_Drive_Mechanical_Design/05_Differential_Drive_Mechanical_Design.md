**Differential Drive & Steer Drive Engineering**


# Chapter 05 Differential Drive Mechanical Design

##  

## 01 Frame Architecture

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Frame Material Selection Criteria

The frame serves as the primary structural backbone of an Autonomous Mobile Robot (AMR). Every subsystem, including drive modules, batteries, controllers, sensors, payload decks, and safety equipment, is ultimately supported by the frame architecture. Consequently, material selection is one of the most critical engineering decisions during AMR development. The chosen material directly influences vehicle weight, payload capacity, structural rigidity, manufacturing cost, thermal behavior, durability, maintenance requirements, and long-term reliability.

The first consideration in frame material selection is the relationship between strength and weight. A heavier frame generally provides greater stiffness and load-bearing capability but reduces payload efficiency and increases energy consumption. Conversely, an extremely lightweight frame may improve mobility but can suffer from excessive deformation under load. The objective is therefore to achieve the highest possible stiffness-to-weight ratio while maintaining acceptable manufacturing and operational costs.

Steel remains one of the most commonly used frame materials in industrial AMRs. Carbon steel provides high strength, excellent weldability, low material cost, and proven durability. Steel structures can withstand repeated loading cycles and are relatively tolerant of manufacturing variations. Heavy-duty industrial AMRs carrying payloads of 500 kg, 1000 kg, or more frequently employ steel chassis because structural stiffness and robustness are prioritized over weight reduction.

However, steel also has disadvantages. Its density is significantly higher than aluminum, resulting in increased vehicle mass. Higher mass increases rolling resistance, motor torque requirements, battery consumption, and transportation costs. Corrosion protection through painting, powder coating, or galvanization is often required, especially in humid or outdoor environments.

Aluminum alloys provide an attractive alternative for medium-duty AMRs. Aluminum offers an excellent strength-to-weight ratio, natural corrosion resistance, and relatively easy machining characteristics. The reduced vehicle weight improves energy efficiency, acceleration performance, and battery operating time. Many logistics AMRs operating in indoor environments utilize aluminum frame structures to balance structural performance and mobility.

Despite these advantages, aluminum exhibits lower modulus of elasticity than steel. This means that larger cross-sectional structures are often required to achieve equivalent stiffness. Welding aluminum also requires specialized manufacturing processes and quality control measures. Fatigue behavior must be carefully evaluated for vehicles experiencing continuous cyclic loading.

Advanced applications sometimes utilize stainless steel, composite materials, or hybrid frame architectures. Stainless steel is preferred in pharmaceutical, food processing, and medical environments where corrosion resistance and cleanliness are critical. Composite structures such as carbon fiber reinforced polymers offer exceptional stiffness-to-weight performance but remain expensive and difficult to repair in industrial environments.

Material selection must also consider manufacturing processes. Welded steel frames provide excellent strength and low production cost for medium and high-volume manufacturing. Bolted aluminum extrusion systems offer flexibility and rapid prototyping capabilities. Laser-cut and CNC-machined structures enable precise component integration but may increase manufacturing expenses.

Thermal considerations become increasingly important as computing power grows. Modern AMRs often integrate high-performance edge computers, GPUs, battery systems, and motor controllers. Frame materials can contribute to thermal management by acting as passive heat dissipation structures. Aluminum, with its relatively high thermal conductivity, is particularly advantageous in applications requiring efficient heat transfer.

Vibration behavior represents another critical design criterion. The frame serves as the mechanical foundation for sensors such as LiDARs, cameras, IMUs, and precision localization equipment. Excessive vibration can degrade localization accuracy, perception performance, and overall system stability. Material selection and structural design must therefore balance stiffness, damping characteristics, and mass distribution.

From a systems engineering perspective, frame material selection should never be based solely on strength calculations. Engineers must simultaneously evaluate payload requirements, manufacturing methods, lifecycle costs, maintenance procedures, environmental conditions, thermal performance, and sensor integration requirements. The optimal solution is often a compromise among these competing factors.

For modern industrial AMRs, steel remains dominant in heavy-duty platforms, aluminum is widely used in light- and medium-duty logistics robots, and hybrid architectures are increasingly emerging as designers seek to maximize structural efficiency while minimizing weight and operating costs.

---

### 1.2 Drive Motor Mounting Structure

The Drive Motor Mounting Structure is a critical component of AMR frame architecture because it directly influences power transmission efficiency, structural integrity, vibration behavior, maintenance accessibility, and long-term reliability. While motors are often viewed primarily as propulsion devices, their mounting configuration significantly affects overall vehicle performance. Improper motor mounting can lead to alignment errors, premature component wear, vibration amplification, and reduced operational lifespan.

The primary function of a motor mounting structure is to provide a rigid mechanical interface between the drive motor and the robot frame. During operation, motors generate torque, reaction forces, vibration, and thermal loads. These forces must be transferred safely into the vehicle structure without causing excessive deformation or misalignment.

One of the most important design requirements is structural rigidity. Motor shafts, gearboxes, and drive wheels must remain accurately aligned throughout the entire operating range. Even small alignment errors can increase bearing loads, gearbox wear, energy losses, and noise generation. Therefore, motor mounting structures are typically designed with reinforced brackets, gussets, and load paths that distribute forces efficiently throughout the chassis.

In Differential Drive robots, drive motors are commonly mounted directly adjacent to the drive wheels. This arrangement minimizes transmission complexity and improves efficiency. The motor may be connected directly to the wheel through an integrated gearbox or through intermediate transmission components such as belts, chains, or couplings.

Steer Drive systems introduce additional complexity because both steering and drive motors must be integrated into a rotating wheel module. The mounting structure must support radial loads, axial loads, steering torque, drive torque, and dynamic impacts simultaneously. Consequently, steer-drive modules often employ precision-machined housings and high-strength bearing assemblies.

Heavy-duty AMRs require particularly robust motor mounting architectures. As payload increases, drive torque requirements rise significantly. During acceleration, braking, obstacle crossing, and emergency stopping, large transient forces are generated. These loads can produce localized stress concentrations if the mounting structure is not properly designed.

Finite Element Analysis (FEA) is frequently used to evaluate motor mounting structures. Engineers analyze stress distribution, deformation behavior, fatigue life, and natural frequencies under various loading conditions. The objective is to ensure that structural deflections remain sufficiently small to preserve drivetrain alignment.

Vibration isolation represents another important consideration. Motors generate electromagnetic forces, gearbox vibrations, and mechanical excitations that can propagate throughout the chassis. Sensitive sensors such as cameras, LiDARs, and IMUs may be affected if vibration levels become excessive. Depending on the application, designers may incorporate vibration-damping materials, isolation mounts, or tuned structural elements.

Maintenance accessibility strongly influences industrial usability. Motor replacement, gearbox servicing, encoder calibration, and electrical inspections should be performed efficiently without extensive disassembly. Consequently, mounting structures often include removable panels, modular interfaces, and standardized attachment points.

Thermal management is closely related to motor mounting design. Electric motors generate heat during continuous operation, especially under heavy loads. The mounting structure can act as a heat transfer pathway, conducting thermal energy into the chassis. Aluminum mounting plates are frequently used because of their high thermal conductivity and relatively low weight.

Cable routing and connector integration must also be considered. Power cables, encoder signals, brake connections, temperature sensors, and communication interfaces must remain protected throughout the vehicle\'s operating life. The mounting structure often incorporates dedicated cable channels, strain relief features, and protective covers.

For modern industrial AMRs, motor mounting structures have evolved from simple brackets into highly engineered subsystems that integrate structural, thermal, electrical, and maintenance requirements. A well-designed mounting architecture improves reliability, reduces maintenance costs, enhances vehicle performance, and contributes significantly to overall system robustness.

---

### 1.3 Payload Deck Design

The Payload Deck is the functional interface between the mobile robot platform and the transported load. While the frame provides structural support and the drive system generates motion, the payload deck determines how effectively the robot can interact with materials, products, equipment, and automation systems. As a result, payload deck design plays a central role in AMR versatility, operational efficiency, safety, and application adaptability.

At its most basic level, the payload deck must safely support the intended load while maintaining structural integrity during acceleration, braking, turning, and obstacle negotiation. However, modern industrial applications require far more than simple load support. Payload decks increasingly serve as integration platforms for conveyors, robotic arms, lifting mechanisms, inspection systems, battery modules, and specialized customer equipment.

The first design consideration is payload capacity. The deck structure must withstand static and dynamic loading conditions throughout the vehicle\'s operational life. Static loads represent the weight of the transported object, while dynamic loads arise from acceleration, deceleration, vibration, impacts, and emergency maneuvers. Engineers typically apply safety factors to account for unexpected loading conditions and long-term fatigue effects.

Load distribution is equally important. Concentrated loads can produce localized stress concentrations and structural deformation. The deck should distribute forces efficiently into the primary frame structure. Reinforcement ribs, cross members, and load-spreading plates are frequently incorporated to improve structural performance.

Deck geometry significantly influences vehicle stability. A higher payload position increases the center of gravity, reducing rollover resistance and dynamic stability. Conversely, a lower deck height improves stability but may limit ground clearance and application flexibility. Designers must therefore balance operational requirements against vehicle dynamics.

Surface design depends heavily on the intended application. Logistics AMRs often use flat decks capable of supporting bins, totes, and pallets. Manufacturing robots may integrate conveyor systems for automated material transfer. Inspection robots may carry sensor masts, scanning equipment, or robotic manipulators. Modular deck architectures are increasingly popular because they allow multiple applications to share a common vehicle platform.

Payload retention is another critical requirement. Loads must remain secure during all operating conditions. Mechanical restraints, side guides, clamps, vacuum systems, magnetic fixtures, and automated locking mechanisms may be incorporated depending on the transported material.

Human-machine interaction considerations are particularly important in collaborative environments. The deck should minimize pinch points, sharp edges, and collision hazards. Ergonomic loading and unloading heights improve worker safety and productivity.

Structural vibration characteristics directly affect payload performance. Precision inspection equipment, metrology instruments, and robotic manipulators are highly sensitive to vibration. The deck structure must provide sufficient stiffness to maintain positioning accuracy while minimizing dynamic oscillations.

Many modern AMRs utilize modular payload deck designs. Standardized mounting interfaces allow customers to install application-specific equipment without modifying the base vehicle architecture. This approach reduces development costs and increases product flexibility.

Electrical and communication integration has also become increasingly important. Payload equipment often requires power distribution, Ethernet connectivity, fieldbus interfaces, safety signals, and synchronization mechanisms. The payload deck frequently incorporates cable routing systems, connector panels, and protected interface zones to simplify integration.

For advanced industrial platforms, payload deck design extends beyond mechanical engineering. It becomes a multidisciplinary integration challenge involving structural analysis, vehicle dynamics, ergonomics, safety engineering, electrical architecture, thermal management, and operational workflow optimization. A well-designed payload deck not only supports the transported load but also enhances the overall value, adaptability, and productivity of the AMR platform.

### 1.1 프레임 재질 선정 기준(Frame Material Selection Criteria)

프레임(Frame)은 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)의 구조적 골격(Structural Backbone) 역할을 수행한다. 구동 모듈(Drive Module), 배터리(Battery), 제어기(Controller), 센서(Sensor), 페이로드 데크(Payload Deck), 안전 장치(Safety Equipment) 등 모든 주요 구성 요소는 결국 프레임에 의해 지지된다. 따라서 프레임 재질 선정은 AMR 개발 과정에서 가장 중요한 엔지니어링 결정 중 하나이다. 선택된 재질은 차량 중량(Vehicle Weight), 적재 능력(Payload Capacity), 구조 강성(Structural Rigidity), 제조 비용(Manufacturing Cost), 열 특성(Thermal Behavior), 내구성(Durability), 유지보수성(Maintainability), 장기 신뢰성(Long-Term Reliability)에 직접적인 영향을 준다.

프레임 재질 선정에서 가장 먼저 고려해야 할 요소는 강도(Strength)와 중량(Weight)의 균형이다. 무거운 프레임은 높은 강성과 하중 지지 능력을 제공하지만 페이로드 효율을 감소시키고 에너지 소비를 증가시킨다. 반대로 지나치게 가벼운 프레임은 이동 성능은 향상될 수 있으나 하중이 증가하면 변형(Deformation)이 발생할 수 있다. 따라서 설계 목표는 비용과 성능을 모두 고려하면서 가능한 높은 강성 대비 중량비(Stiffness-to-Weight Ratio)를 확보하는 것이다.

강철(Steel)은 산업용 AMR에서 가장 널리 사용되는 프레임 재료 중 하나이다. 탄소강(Carbon Steel)은 높은 강도, 우수한 용접성(Weldability), 낮은 재료비, 검증된 내구성을 제공한다. 반복적인 하중 사이클(Loading Cycle)을 견딜 수 있으며 제조 공정 오차에도 비교적 강하다. 특히 500kg, 1000kg, 1500kg 이상의 중량급 AMR에서는 경량화보다 강성과 내구성이 우선되기 때문에 강철 섀시가 널리 사용된다.

그러나 강철은 밀도가 높기 때문에 차량 중량이 증가하는 단점이 있다. 차량 중량 증가는 구름 저항(Rolling Resistance), 모터 토크 요구량, 배터리 소비량, 운송 비용을 증가시킨다. 또한 실외 환경이나 습도가 높은 환경에서는 부식(Corrosion) 방지를 위해 도장(Painting), 분체 도장(Powder Coating), 아연 도금(Galvanization)이 필요하다.

알루미늄 합금(Aluminum Alloy)은 중형급 AMR에서 매우 매력적인 대안이다. 알루미늄은 우수한 강도 대비 중량비를 제공하며 자연적인 내식성(Corrosion Resistance)과 우수한 가공성(Machinability)을 가진다. 차량 중량 감소는 에너지 효율, 가속 성능, 배터리 운용 시간을 향상시킨다. 따라서 실내 물류용 AMR에서는 알루미늄 프레임이 널리 활용된다.

반면 알루미늄은 탄성계수(Modulus of Elasticity)가 강철보다 낮다. 동일한 강성을 확보하기 위해서는 더 큰 단면 구조가 필요하다. 또한 용접 품질 확보를 위해 보다 전문적인 제조 공정이 요구되며, 반복 하중에 대한 피로 특성(Fatigue Behavior)도 신중하게 검토해야 한다.

특수한 응용 분야에서는 스테인리스강(Stainless Steel), 복합재료(Composite Material), 하이브리드 프레임(Hybrid Frame)도 사용된다. 스테인리스강은 제약 산업(Pharmaceutical Industry), 식품 산업(Food Industry), 의료 환경(Medical Environment)에서 우수한 내식성과 청결성을 제공한다. 탄소섬유 강화 플라스틱(Carbon Fiber Reinforced Polymer)과 같은 복합재료는 매우 높은 강성 대비 중량비를 제공하지만 비용이 높고 수리가 어렵다.

재질 선정 시 제조 방식도 고려해야 한다. 용접 강철 구조는 대량 생산에 적합하며 비용 경쟁력이 높다. 알루미늄 프로파일(Aluminum Extrusion)은 시제품 개발과 구조 변경이 용이하다. 레이저 절단(Laser Cutting) 및 CNC 가공 구조는 높은 정밀도를 제공하지만 제조 비용이 증가할 수 있다.

최근 AMR은 고성능 엣지 컴퓨터(Edge Computer), GPU, 배터리, 모터 드라이버 등을 탑재하기 때문에 열 관리도 중요해지고 있다. 프레임은 수동 방열 구조(Passive Heat Sink) 역할을 수행할 수 있으며, 특히 알루미늄은 높은 열전도율(Thermal Conductivity)을 제공하여 열 분산에 유리하다.

진동(Vibration) 특성도 중요한 요소이다. LiDAR, 카메라(Camera), IMU와 같은 센서는 진동에 민감하다. 과도한 진동은 위치추정 정확도(Localization Accuracy)와 인지 성능(Perception Performance)을 저하시킬 수 있다. 따라서 프레임은 강성뿐 아니라 감쇠 특성(Damping Characteristic)도 고려하여 설계되어야 한다.

시스템 엔지니어링(System Engineering) 관점에서 프레임 재질 선정은 단순한 강도 계산 문제가 아니다. 페이로드, 제조성, 수명주기 비용(Lifecycle Cost), 유지보수, 환경 조건, 열 관리, 센서 통합까지 종합적으로 고려해야 한다.

현재 산업용 AMR 시장에서는 500kg 이상의 중량급 플랫폼은 강철 구조가 주류를 이루고 있으며, 50kg\~300kg급 물류 AMR은 알루미늄 구조가 널리 사용되고 있다. 최근에는 두 재질의 장점을 결합한 하이브리드 프레임 구조도 점차 증가하고 있다.

---

### 1.2 구동 모터 장착 구조(Drive Motor Mounting Structure)

구동 모터 장착 구조(Drive Motor Mounting Structure)는 AMR 프레임 설계에서 매우 중요한 요소이다. 이는 동력 전달 효율(Power Transmission Efficiency), 구조 강도(Structural Integrity), 진동 특성(Vibration Behavior), 유지보수성(Maintenance Accessibility), 장기 신뢰성(Long-Term Reliability)에 직접적인 영향을 미친다.

모터는 단순히 추진력을 발생시키는 장치가 아니라 지속적으로 토크(Torque), 반력(Reaction Force), 진동(Vibration), 열(Thermal Load)을 발생시키는 구조물이다. 따라서 이러한 하중을 안전하게 프레임으로 전달하는 장착 구조가 필요하다.

가장 중요한 설계 요구사항은 강성(Rigidity)이다. 모터 축(Motor Shaft), 감속기(Gearbox), 구동 휠(Drive Wheel)은 항상 정확한 정렬(Alignment)을 유지해야 한다. 작은 정렬 오차도 베어링 부하 증가, 감속기 마모, 소음 증가, 에너지 손실을 초래할 수 있다.

따라서 모터 장착 구조는 보강 브래킷(Reinforced Bracket), 거셋(Gusset), 하중 전달 경로(Load Path)를 이용하여 힘을 효율적으로 분산하도록 설계된다.

차동 구동에서는 모터가 바퀴 근처에 직접 장착되는 경우가 많다. 이는 구조를 단순화하고 동력 전달 효율을 향상시킨다. 모터는 감속기 일체형 구조 또는 벨트(Belt), 체인(Chain), 커플링(Coupling)을 통해 바퀴와 연결된다.

스티어 구동에서는 구조가 더욱 복잡해진다. 조향 모터(Steering Motor)와 구동 모터(Drive Motor)가 모두 회전하는 휠 모듈(Wheel Module) 내부에 통합되어야 하기 때문이다. 따라서 반경 방향 하중(Radial Load), 축 방향 하중(Axial Load), 조향 토크, 구동 토크를 동시에 지지할 수 있는 고강도 구조가 필요하다.

중량급 AMR에서는 이러한 요구가 더욱 커진다. 페이로드 증가에 따라 구동 토크가 크게 증가하며, 가속, 감속, 장애물 통과, 비상 정지 시 매우 큰 순간 하중(Transient Load)이 발생한다.

이를 검증하기 위해 유한요소해석(FEA, Finite Element Analysis)이 자주 사용된다. 응력 분포(Stress Distribution), 변형량(Deformation), 피로 수명(Fatigue Life), 고유진동수(Natural Frequency)를 분석하여 충분한 강성을 확보한다.

진동 절연(Vibration Isolation)도 중요하다. 모터와 감속기는 지속적으로 진동을 발생시키며, 이는 카메라, LiDAR, IMU 등에 영향을 줄 수 있다. 따라서 방진 마운트(Vibration Mount), 감쇠 재료(Damping Material), 튜닝 구조(Tuned Structure)가 사용되기도 한다.

유지보수성 또한 고려해야 한다. 모터 교체, 감속기 정비, 엔코더 보정, 전기 점검이 쉽도록 설계되어야 한다. 이를 위해 탈착식 패널(Removable Panel), 모듈화 인터페이스(Modular Interface), 표준 체결 구조(Standard Mounting Point)가 사용된다.

열 관리 역시 중요한 요소이다. 모터는 지속적인 운전 시 상당한 열을 발생시키며, 장착 구조는 이를 프레임으로 전달하는 방열 경로 역할을 할 수 있다. 알루미늄 장착 플레이트는 높은 열전도율 덕분에 널리 사용된다.

케이블 관리(Cable Management)도 필수적이다. 전원 케이블, 엔코더 신호, 브레이크 신호, 온도 센서, 통신선은 장기간 보호되어야 한다. 따라서 케이블 채널(Cable Channel), 스트레인 릴리프(Strain Relief), 보호 커버가 함께 설계된다.

현대 산업용 AMR에서 모터 장착 구조는 단순한 브래킷이 아니라 구조, 열, 전기, 유지보수를 통합한 핵심 서브시스템으로 발전하고 있다.

---

### 1.3 페이로드 데크 설계(Payload Deck Design)

페이로드 데크(Payload Deck)는 이동 로봇 플랫폼과 운반 물체를 연결하는 핵심 인터페이스이다. 프레임이 구조적 지지 역할을 하고 구동 시스템이 이동을 담당한다면, 페이로드 데크는 실제 작업 수행 능력을 결정하는 요소이다.

가장 기본적으로 페이로드 데크는 운반 물체를 안전하게 지지해야 한다. 그러나 현대 산업용 AMR에서는 단순한 적재판 이상의 역할을 수행한다. 컨베이어(Conveyor), 로봇팔(Robot Arm), 리프트(Lift), 검사 장비(Inspection Equipment), 배터리 모듈(Battery Module), 고객 전용 장비(Customer Equipment) 등이 모두 데크 위에 장착될 수 있다.

첫 번째 설계 요소는 적재 능력(Payload Capacity)이다. 데크는 정적 하중(Static Load)뿐 아니라 가속, 감속, 충격, 진동에 의한 동적 하중(Dynamic Load)도 견뎌야 한다. 따라서 충분한 안전계수(Safety Factor)가 적용된다.

하중 분배(Load Distribution)도 중요하다. 집중 하중(Concentrated Load)은 국부 응력(Local Stress)과 변형을 유발할 수 있다. 따라서 보강 리브(Reinforcement Rib), 크로스 멤버(Cross Member), 하중 분산 플레이트(Load Spreading Plate)가 적용된다.

데크 높이(Deck Height)는 차량 안정성에 직접적인 영향을 준다. 높은 위치에 하중을 적재하면 무게중심(Center of Gravity)이 상승하여 전복 위험(Rollover Risk)이 증가한다. 반대로 낮은 데크는 안정성은 높지만 지상고(Ground Clearance)와 응용 유연성이 감소할 수 있다.

표면 구조(Surface Design)는 응용 분야에 따라 달라진다. 물류 AMR은 평평한 적재면을 사용하는 경우가 많으며, 제조용 AMR은 컨베이어를 통합하기도 한다. 검사 로봇은 센서 마스트(Sensor Mast), 스캐너, 매니퓰레이터를 장착할 수 있다.

최근에는 모듈형 데크(Modular Payload Deck)가 널리 사용되고 있다. 동일한 차량 플랫폼에 서로 다른 상부 모듈을 장착할 수 있어 제품군 확장이 용이하다.

적재물 고정(Payload Retention)도 중요한 요소이다. 클램프(Clamp), 가이드 레일(Guide Rail), 진공 흡착(Vacuum Fixture), 자석(Magnetic Fixture), 자동 잠금 장치(Auto Locking Mechanism) 등이 사용될 수 있다.

사람과 협업하는 환경에서는 인체공학(Ergonomics)도 중요하다. 적절한 적재 높이와 안전한 모서리 설계를 통해 작업자의 안전과 생산성을 향상시킬 수 있다.

진동 특성도 매우 중요하다. 검사 장비, 계측 장비(Metrology Equipment), 로봇팔은 진동에 민감하기 때문에 높은 구조 강성이 요구된다.

전기 및 통신 통합(Electrical and Communication Integration)도 필수적이다. 상부 장비는 전원(Power Distribution), Ethernet, Fieldbus, Safety Signal 등을 필요로 한다. 따라서 데크에는 케이블 경로, 커넥터 패널, 보호 인터페이스가 함께 설계된다.

현대 산업용 AMR에서 페이로드 데크 설계는 단순한 기계 설계가 아니다. 구조 해석(Structural Analysis), 차량 동역학(Vehicle Dynamics), 인체공학, 안전 공학(Safety Engineering), 전기 아키텍처(Electrical Architecture), 열 관리(Thermal Management), 작업 공정 최적화(Workflow Optimization)가 모두 결합된 종합 엔지니어링 분야이다.

잘 설계된 페이로드 데크는 단순히 하중을 지지하는 수준을 넘어 AMR 플랫폼의 가치(Value), 확장성(Scalability), 생산성(Productivity), 고객 적용성(Application Flexibility)을 크게 향상시키는 핵심 요소가 된다. 특히 힐스로보틱스의 500kg, 1000kg, 1500kg급 산업용 AMR에서는 페이로드 데크가 향후 CAD2SCAN, GPR, Mobile Manipulator, Cargo Module 등 다양한 상부 시스템을 수용할 수 있도록 표준화(Modular Standardization)와 확장성 중심으로 설계되는 것이 바람직하다.

##  

## 02 Wheel Selection

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Wheel Diameter and Floor Gap Tolerance

Wheel diameter is one of the most influential design parameters in an Autonomous Mobile Robot because it directly affects mobility performance, obstacle negotiation capability, energy efficiency, ride quality, payload capacity, and long-term reliability. Although wheel selection is often viewed as a mechanical design decision, it has significant implications for vehicle dynamics, navigation accuracy, and operational effectiveness.

One of the primary functions of wheel diameter is determining the robot's ability to overcome floor irregularities. Real industrial environments are rarely perfectly flat. Expansion joints, floor cracks, cable protectors, drainage channels, threshold transitions, rail crossings, and small obstacles are commonly encountered. The wheel diameter largely determines how effectively the robot can traverse these discontinuities without excessive vibration or loss of traction.

When a wheel encounters an obstacle, the contact geometry creates a climbing angle between the wheel and the obstacle edge. Larger wheels generate a smaller effective climbing angle, allowing the robot to roll over the obstacle more smoothly. Smaller wheels experience a steeper climbing angle and therefore require greater drive torque to overcome the same obstacle.

As a general engineering guideline, the maximum obstacle height should typically remain below approximately 20% to 30% of the wheel diameter for reliable operation. For example, a 100 mm wheel may comfortably traverse obstacles up to approximately 20--30 mm, while a 250 mm wheel may handle obstacles approaching 50--75 mm under favorable conditions.

Floor gap tolerance is closely related to wheel diameter. Floor gaps are commonly found between concrete slabs, elevator thresholds, loading dock transitions, and metal floor plates. If the wheel diameter is too small relative to the gap width, the wheel may become trapped or experience excessive impact loads during crossing. Larger wheels reduce this risk by maintaining a more favorable contact geometry.

Wheel diameter also influences vibration transmission. Small wheels tend to follow floor surface irregularities more aggressively, resulting in higher vibration levels. Larger wheels effectively smooth the interaction with the floor, reducing shock loads transmitted to the chassis, sensors, payload, and electronic systems.

The relationship between wheel diameter and rolling resistance must also be considered. Larger wheels generally experience lower rolling resistance because the deformation angle at the contact patch is reduced. This can improve energy efficiency and extend battery operating time. However, larger wheels also increase vehicle height, mass, and packaging requirements.

Vehicle speed is another important consideration. For a given wheel rotational speed, larger wheels produce greater linear velocity. Consequently, high-speed AMRs often utilize larger wheel diameters to achieve desired travel speeds while maintaining reasonable motor operating conditions.

Wheel diameter significantly affects motor and gearbox selection. Larger wheels increase the torque arm between the wheel center and the ground. While obstacle negotiation improves, drive torque requirements also increase. Engineers must therefore balance mobility advantages against motor sizing constraints.

Payload capacity further influences wheel diameter selection. Heavy-duty AMRs generally benefit from larger wheels because the larger contact geometry reduces localized stress and improves load distribution. Industrial robots carrying payloads above 500 kg often utilize wheel diameters significantly larger than those found in light-duty logistics robots.

Sensor performance can also be affected. Excessive vibration generated by undersized wheels may degrade LiDAR measurements, camera image quality, IMU accuracy, and localization performance. Selecting an appropriate wheel diameter therefore contributes indirectly to navigation accuracy.

Ultimately, wheel diameter selection should never be based solely on obstacle-crossing capability. Engineers must simultaneously evaluate floor conditions, payload requirements, desired vehicle speed, structural packaging constraints, motor capabilities, energy efficiency targets, and localization requirements. The optimal wheel diameter is the result of balancing these interconnected design factors.

---

### 2.2 Tire Material: PU vs Rubber

The selection of tire material is a critical design decision because it directly influences traction, durability, vibration isolation, noise generation, floor wear, rolling resistance, and maintenance requirements. In industrial AMRs, the two most commonly used tire materials are Polyurethane (PU) and Rubber. Each material exhibits unique mechanical properties that make it suitable for different operating environments and payload conditions.

Polyurethane wheels are widely used in indoor industrial applications due to their high durability and excellent wear resistance. PU materials typically possess higher hardness than conventional rubber compounds. This increased hardness reduces deformation under load, which helps minimize rolling resistance and improve energy efficiency.

One of the major advantages of PU wheels is their ability to maintain dimensional stability under heavy loads. The contact patch remains relatively consistent even when transporting substantial payloads. This characteristic improves odometry accuracy because wheel deformation introduces fewer measurement errors.

PU wheels also exhibit excellent resistance to abrasion, chemicals, oils, and industrial contaminants. In manufacturing environments where exposure to lubricants, solvents, or cleaning agents is common, polyurethane often provides significantly longer service life than rubber.

Another important benefit is floor cleanliness. PU wheels generally generate fewer particles during operation, making them suitable for electronics manufacturing, semiconductor facilities, pharmaceutical production, and clean industrial environments.

However, the higher stiffness of PU wheels creates certain disadvantages. Shock absorption capability is lower than that of rubber. Consequently, impacts generated by floor joints, small obstacles, and uneven surfaces are transmitted more directly into the robot structure. Sensitive sensors and precision payloads may therefore require additional vibration isolation measures.

Rubber wheels offer a fundamentally different performance profile. Rubber materials are softer and more compliant, allowing greater deformation within the contact patch. This characteristic significantly improves shock absorption and ride comfort. Robots operating on rough surfaces often benefit from the damping properties of rubber tires.

Traction performance is another major advantage of rubber. The softer material conforms more effectively to surface irregularities, increasing the real contact area and improving grip. This can reduce slip during acceleration, braking, and cornering maneuvers.

Rubber wheels are frequently preferred for outdoor AMRs because they provide better performance on concrete, asphalt, gravel, and other variable terrain conditions. The enhanced traction can improve vehicle stability and obstacle-climbing capability.

The disadvantages of rubber primarily involve durability and efficiency. Increased deformation produces higher rolling resistance, resulting in greater energy consumption. Rubber tires generally wear faster than polyurethane, particularly under heavy loads and continuous industrial operation.

Environmental conditions also influence material performance. Temperature changes affect both PU and rubber properties, but the magnitude and nature of these effects differ. Extremely low temperatures may increase material stiffness, while elevated temperatures can accelerate wear and aging.

Noise generation varies between materials as well. PU wheels typically produce lower rolling noise on smooth industrial floors. Rubber wheels may generate more vibration damping but can produce different acoustic characteristics depending on tread design and floor texture.

Many industrial AMR manufacturers select PU wheels for indoor logistics robots carrying payloads up to several hundred kilograms because of their durability, cleanliness, and efficiency. Heavy outdoor vehicles, agricultural robots, and rough-terrain platforms often favor rubber tires because traction and shock absorption become more important than minimizing rolling resistance.

The choice between PU and rubber is therefore not a question of which material is universally superior. Rather, it is a systems engineering decision that must consider floor conditions, payload, operating speed, maintenance requirements, environmental exposure, and vehicle performance objectives.

---

### 2.3 Load vs Diameter Selection Chart

The relationship between wheel load capacity and wheel diameter is one of the most important considerations in mobile robot mechanical design. Selecting an appropriate wheel diameter requires understanding how wheel size influences load distribution, rolling resistance, obstacle-crossing capability, structural stress, vehicle stability, and long-term durability.

As vehicle payload increases, the forces transmitted through each wheel increase proportionally. Small wheels can support significant loads when constructed from high-strength materials, but they experience higher contact pressures and greater sensitivity to floor irregularities. Larger wheels distribute forces more effectively and generally provide superior mobility under heavy loads.

A simplified engineering selection chart can be used as an initial guideline:

Very Light Duty Applications (Payload below 50 kg)

Typical wheel diameter ranges from approximately 75 mm to 125 mm. These wheels are commonly used in educational robots, service robots, laboratory platforms, and small indoor AMRs. Smooth floor conditions are generally required.

Light Duty Logistics Applications (Payload 50--300 kg)

Typical wheel diameter ranges from approximately 125 mm to 200 mm. This category includes warehouse transport robots, electronics manufacturing AMRs, and material handling platforms. PU wheels are frequently used because indoor floors are usually smooth and predictable.

Medium Duty Industrial Applications (Payload 300--800 kg)

Typical wheel diameter ranges from approximately 200 mm to 300 mm. These platforms often transport heavy materials, industrial components, and production equipment. Larger wheel diameters improve durability, vibration reduction, and floor-gap tolerance.

Heavy Duty Industrial Applications (Payload 800--1500 kg)

Typical wheel diameter ranges from approximately 250 mm to 400 mm. Wheel loads become substantial, requiring reinforced wheel hubs, high-capacity bearings, and robust frame structures. Steer Drive architectures become increasingly attractive because they reduce tire scrubbing and improve efficiency.

Ultra Heavy Duty Applications (Payload above 1500 kg)

Typical wheel diameters often exceed 350 mm and may reach 500 mm or more. These systems include heavy transporters, automated forklifts, mining vehicles, and specialized industrial platforms. Structural durability and mobility become dominant design priorities.

While payload serves as an initial sizing parameter, other factors frequently dominate final wheel selection. Floor gap size, obstacle height, travel speed, required positioning accuracy, vibration sensitivity, and available installation space may justify choosing a larger wheel than payload calculations alone would suggest.

Vehicle center of gravity must also be considered. Larger wheels increase chassis height and can raise the overall center of gravity. This may reduce rollover stability if not compensated through frame design and load placement.

Motor sizing is directly affected by wheel diameter. Larger wheels improve obstacle negotiation but require greater drive torque. Consequently, wheel diameter, gearbox ratio, and motor selection must be optimized simultaneously rather than independently.

Modern industrial AMR design increasingly relies on simulation tools and system-level optimization methods to determine wheel specifications. Finite Element Analysis, multibody dynamics simulations, traction models, and operational duty-cycle analysis provide more accurate predictions than simple sizing charts alone.

Nevertheless, load-versus-diameter selection charts remain valuable during the conceptual design phase. They provide engineers with a practical starting point for balancing payload requirements, mobility performance, energy efficiency, structural reliability, and overall vehicle architecture. A properly selected wheel diameter improves not only mechanical performance but also navigation accuracy, component lifespan, maintenance efficiency, and total operational productivity throughout the robot's lifecycle.

### 2.1 휠 직경과 바닥 틈새 허용도(Wheel Diameter and Floor Gap Tolerance)

휠 직경(Wheel Diameter)은 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)의 이동 성능(Mobility Performance), 장애물 극복 능력(Obstacle Negotiation Capability), 에너지 효율(Energy Efficiency), 승차감(Ride Quality), 적재 능력(Payload Capacity), 장기 신뢰성(Long-Term Reliability)에 직접적인 영향을 미치는 핵심 설계 변수이다. 휠 선정은 단순한 기계 설계 요소로 보일 수 있지만 실제로는 차량 동역학(Vehicle Dynamics), 위치추정(Localization Accuracy), 운영 효율(Operation Efficiency)에까지 영향을 미친다.

휠 직경의 가장 중요한 역할 중 하나는 바닥 불규칙성(Floor Irregularity)에 대한 대응 능력을 결정하는 것이다. 실제 산업 환경은 완벽하게 평탄하지 않다. 바닥 균열(Crack), 익스팬션 조인트(Expansion Joint), 케이블 덮개(Cable Protector), 배수로(Drainage Channel), 엘리베이터 턱(Elevator Threshold), 철판 연결부(Metal Plate Joint) 등이 흔히 존재한다. 휠 직경은 이러한 요소를 얼마나 부드럽게 통과할 수 있는지를 결정한다.

휠이 장애물을 만날 때 휠과 장애물 사이에는 상승 각도(Climbing Angle)가 형성된다. 직경이 큰 휠은 이 각도가 작아져 장애물을 쉽게 넘어갈 수 있다. 반대로 작은 휠은 더 가파른 각도를 형성하므로 동일한 장애물을 넘기 위해 더 큰 구동 토크(Drive Torque)가 필요하다.

일반적인 설계 기준으로 장애물 높이는 휠 직경의 약 20\~30% 이하로 유지하는 것이 바람직하다. 예를 들어 100mm 휠은 약 20\~30mm 정도의 장애물을 안정적으로 통과할 수 있으며, 250mm 휠은 약 50\~75mm 수준의 장애물을 비교적 안정적으로 극복할 수 있다.

바닥 틈새 허용도(Floor Gap Tolerance) 역시 휠 직경과 밀접한 관련이 있다. 콘크리트 바닥 연결부, 엘리베이터 경계부, 하역장 경사판(Loading Dock Transition), 금속 플레이트 연결부 등에는 일정한 폭의 틈새가 존재한다. 휠 직경이 너무 작으면 휠이 틈에 빠지거나 충격을 받을 가능성이 높아진다. 반면 큰 휠은 접촉 형상이 유리하기 때문에 이러한 위험을 줄일 수 있다.

휠 직경은 진동 전달(Vibration Transmission)에도 영향을 준다. 작은 휠은 바닥의 미세한 요철을 더 민감하게 따라가기 때문에 차체에 전달되는 진동이 증가한다. 반대로 큰 휠은 바닥의 불규칙성을 상대적으로 완화하여 충격을 줄여준다.

구름 저항(Rolling Resistance) 측면에서도 휠 직경은 중요한 요소이다. 일반적으로 큰 휠은 접촉 패치(Contact Patch)의 변형 각도가 작기 때문에 구름 저항이 감소한다. 이는 에너지 효율 향상과 배터리 운용 시간 증가로 이어질 수 있다. 그러나 동시에 차량 높이와 중량이 증가하는 단점도 존재한다.

차량 속도(Vehicle Speed)도 휠 직경과 밀접하게 연관된다. 동일한 회전 속도(Rotational Speed)에서 큰 휠은 더 높은 선속도(Linear Velocity)를 제공한다. 따라서 고속 AMR은 일반적으로 더 큰 직경의 휠을 사용한다.

모터 및 감속기 선정에도 직접적인 영향을 미친다. 휠이 커질수록 지면과의 레버 암(Lever Arm)이 증가하므로 동일한 추진력을 생성하기 위해 더 큰 토크가 필요하다. 따라서 휠 직경은 모터 용량과 감속비(Gear Ratio)를 함께 고려하여 결정해야 한다.

페이로드 역시 휠 직경 선정에 중요한 요소이다. 중량급 AMR은 일반적으로 더 큰 휠을 사용하여 접촉 응력을 감소시키고 하중 분산 능력을 향상시킨다. 특히 500kg 이상의 산업용 AMR에서는 휠 직경이 차량 내구성과 주행 안정성에 매우 큰 영향을 미친다.

센서 성능에도 간접적인 영향을 준다. 지나치게 작은 휠은 과도한 진동을 유발하여 LiDAR, 카메라(Camera), IMU 등의 성능을 저하시킬 수 있다. 따라서 적절한 휠 직경 선정은 내비게이션 정확도 향상에도 기여한다.

결국 휠 직경은 장애물 극복 능력만으로 결정되어서는 안 된다. 바닥 상태, 적재 하중, 차량 속도, 공간 제약, 모터 성능, 에너지 효율, 위치 정확도를 종합적으로 고려하여 최적값을 선정해야 한다.

---

### 2.2 타이어 재질: 폴리우레탄 vs 고무(Tire Material: PU vs Rubber)

타이어 재질(Tire Material)은 접지력(Traction), 내구성(Durability), 진동 흡수(Vibration Isolation), 소음(Noise), 바닥 마모(Floor Wear), 구름 저항(Rolling Resistance), 유지보수 비용(Maintenance Cost)에 직접적인 영향을 주는 중요한 설계 요소이다. 산업용 AMR에서는 주로 폴리우레탄(Polyurethane, PU)과 고무(Rubber)가 사용된다.

폴리우레탄 휠은 실내 산업 환경에서 가장 널리 사용되는 재질 중 하나이다. PU는 일반 고무보다 높은 경도(Hardness)를 가지며 마모 저항성(Wear Resistance)이 우수하다. 이러한 특성은 하중이 증가해도 변형을 최소화하며 구름 저항을 감소시키고 에너지 효율을 향상시킨다.

PU 휠의 가장 큰 장점 중 하나는 높은 치수 안정성(Dimensional Stability)이다. 중량 하중에서도 접촉 패치가 크게 변형되지 않으므로 오도메트리 정확도가 향상된다. 엔코더 기반 거리 측정 오차도 상대적으로 적다.

또한 PU는 화학물질(Chemical), 오일(Oil), 윤활제(Lubricant), 산업용 세척제(Cleaning Agent)에 대한 내성이 뛰어나다. 따라서 제조 공장이나 자동화 설비 환경에서 긴 수명을 제공한다.

청정도(Cleanliness) 측면에서도 장점이 있다. PU 휠은 마모 입자(Particle) 발생이 적기 때문에 반도체(Semiconductor), 전자(Electronics), 제약(Pharmaceutical) 산업과 같은 청정 환경에 적합하다.

반면 PU는 상대적으로 강성이 높기 때문에 충격 흡수 능력이 떨어진다. 바닥 이음새(Floor Joint), 작은 장애물, 노면 불균일성에서 발생하는 충격이 차체로 직접 전달될 수 있다. 따라서 정밀 센서나 검사 장비를 탑재하는 경우에는 추가적인 방진 구조가 필요할 수 있다.

고무 타이어는 전혀 다른 특성을 가진다. 고무는 PU보다 부드럽고 탄성이 높기 때문에 충격 흡수 능력이 우수하다. 접촉 패치가 더 크게 형성되며 노면 형상에 잘 적응한다.

고무의 가장 큰 장점은 접지력이다. 표면의 미세한 요철에도 밀착되므로 가속, 제동, 코너링 시 더 높은 마찰력을 제공한다. 이러한 특성은 슬립 감소와 주행 안정성 향상으로 이어진다.

실외 AMR은 일반적으로 고무 타이어를 선호한다. 콘크리트, 아스팔트, 자갈길, 비포장 도로 등 다양한 환경에서 높은 접지력을 제공하기 때문이다.

그러나 고무는 PU보다 변형량이 크기 때문에 구름 저항이 증가한다. 결과적으로 에너지 소비가 증가하고 배터리 사용 시간이 감소할 수 있다. 또한 지속적인 산업 환경에서는 마모 속도가 더 빠른 경우가 많다.

온도 변화도 중요한 요소이다. 저온에서는 두 재질 모두 강성이 증가하지만 변화 특성은 서로 다르다. 고온에서는 마모 속도가 증가하고 재료 노화(Material Aging)가 촉진될 수 있다.

소음 특성도 다르다. PU는 평탄한 바닥에서 비교적 조용하게 운행되며, 고무는 충격 흡수는 우수하지만 바닥 상태에 따라 다른 소음 특성을 보일 수 있다.

일반적으로 50kg\~500kg급 실내 물류 AMR은 PU 휠을 많이 사용한다. 반면 실외 AMR, 농업 로봇(Agricultural Robot), 험지 주행 차량(Rough Terrain Vehicle)은 고무 타이어를 사용하는 경우가 많다.

결국 PU와 고무 중 어느 것이 절대적으로 우수한 것은 아니다. 바닥 상태, 하중, 속도, 유지보수 조건, 환경 특성, 요구 성능에 따라 최적의 재질이 달라진다.

---

### 2.3 하중 대 휠 직경 선정 차트(Load vs Diameter Selection Chart)

휠 직경과 하중(Payload) 사이의 관계는 이동 로봇 설계에서 가장 중요한 요소 중 하나이다. 적절한 휠 직경 선정은 하중 분산, 장애물 통과 능력, 구조 응력, 차량 안정성, 내구성을 결정한다.

하중이 증가하면 각 휠에 전달되는 힘도 증가한다. 작은 휠도 강한 재질을 사용하면 높은 하중을 견딜 수 있지만 접촉 압력(Contact Pressure)이 증가하고 바닥 불규칙성에 더 민감해진다. 큰 휠은 하중을 더 효과적으로 분산시키고 주행 성능을 향상시킨다.

일반적인 산업용 AMR 설계 기준은 다음과 같다.

초경량급(Very Light Duty)

페이로드 50kg 이하에서는 일반적으로 75\~125mm 직경의 휠을 사용한다. 교육용 로봇(Educational Robot), 서비스 로봇(Service Robot), 연구용 플랫폼에 주로 적용된다.

경량 물류급(Light Duty Logistics)

50\~300kg 수준에서는 일반적으로 125\~200mm 직경을 사용한다. 창고 물류 로봇, 전자 부품 운반 AMR, 실내 물류 차량이 대표적이다.

중형 산업급(Medium Duty Industrial)

300\~800kg 수준에서는 일반적으로 200\~300mm 직경이 사용된다. 진동 감소와 장애물 극복 능력이 중요해지기 때문이다.

중량 산업급(Heavy Duty Industrial)

800\~1500kg 수준에서는 일반적으로 250\~400mm 직경을 사용한다. 이 단계에서는 고강도 허브(Hub), 대형 베어링(Bearing), 강화 프레임(Reinforced Frame)이 필요해진다.

초중량급(Ultra Heavy Duty)

1500kg 이상에서는 일반적으로 350\~500mm 이상의 휠이 사용된다. 자동 지게차(Automated Forklift), 광산 차량(Mining Vehicle), 특수 운반 차량이 대표적인 예이다.

그러나 실제 설계에서는 하중만으로 휠을 결정하지 않는다. 바닥 틈새, 장애물 높이, 목표 속도, 위치 정밀도, 진동 민감도, 설치 공간 등이 더 큰 영향을 주는 경우도 많다.

무게중심(Center of Gravity)도 중요한 요소이다. 휠 직경이 증가하면 차체 높이가 상승하고 무게중심도 높아질 수 있다. 이는 전복 안정성(Rollover Stability)에 영향을 미친다.

모터 선정과도 직접적인 관계가 있다. 큰 휠은 장애물 극복 능력을 향상시키지만 더 큰 구동 토크를 요구한다. 따라서 휠 직경, 감속비, 모터 용량은 동시에 최적화되어야 한다.

최근 산업용 AMR 설계에서는 유한요소해석(FEA), 다물체 동역학(Multibody Dynamics), 접지 모델(Traction Model), 운용 사이클 분석(Duty Cycle Analysis)을 활용하여 보다 정확한 휠 사양을 결정한다.

그럼에도 불구하고 하중 대 휠 직경 선정 차트는 개념 설계(Concept Design) 단계에서 매우 유용한 기준이 된다. 적절한 휠 직경은 기계 성능뿐 아니라 내비게이션 정확도, 부품 수명, 유지보수 효율, 전체 생산성까지 향상시키는 핵심 요소이다.

특히 힐스로보틱스(Hills Robotics)의 실내 산업용 AMR 기준으로 보면 다음과 같은 권장 범위를 사용할 수 있다.

\* 50kg급 : 125\~150mm PU 휠

\* 100kg급 : 150\~180mm PU 휠

\* 250kg급 : 180\~200mm PU 휠

\* 500kg급 : 200\~250mm PU 휠 또는 고하중 PU 휠

\* 1000kg급 : 250\~300mm PU 휠, 스티어 구동 권장

\* 1500kg급 : 300\~400mm PU 휠 또는 산업용 고하중 고무 타이어, 스티어 구동 필수 수준

이는 실내 에폭시 바닥(Epoxy Floor), 최대 20km/h 이하 운행, 공장 물류 환경을 기준으로 한 실무적인 설계 가이드라인이다.

##  

## 03 Caster Selection

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Caster Load Distribution Calculation

Caster wheels are often viewed as simple supporting components within a mobile robot, yet they play a critical role in overall vehicle stability, load distribution, maneuverability, and long-term durability. In many Differential Drive and certain Steer Drive architectures, caster wheels provide passive support while the primary drive wheels generate propulsion and steering forces. Although casters do not typically contribute to traction, improper caster load distribution can significantly affect vehicle performance, energy efficiency, vibration behavior, and component lifespan.

The first objective of caster load distribution analysis is to determine how the total vehicle weight is shared among all wheel contact points. Every wheel, whether actively driven or passive, experiences a portion of the robot\'s total weight. This weight includes the base vehicle mass, battery systems, onboard electronics, payload equipment, and any dynamic loads generated during operation.

From a static equilibrium perspective, the sum of all wheel reaction forces must equal the total vehicle weight. If a robot has two drive wheels and one caster wheel, the total load can be represented as:

W = FD1 + FD2 + FC

where:

W = total vehicle weight

FD1 = load on drive wheel 1

FD2 = load on drive wheel 2

FC = load on caster wheel

The actual load carried by each wheel depends on the location of the vehicle center of gravity relative to the wheel contact points. If the center of gravity is positioned exactly between the drive wheels, the caster may carry only a small percentage of the total weight. If the center of gravity shifts toward the caster, its load increases significantly.

In practical AMR design, caster load is often maintained within a controlled range. Excessive caster loading can reduce traction available at the drive wheels because less weight remains on the powered wheels. Since traction force is proportional to normal force, overloading the caster may reduce acceleration capability, climbing performance, and braking effectiveness.

Conversely, insufficient caster loading can also create problems. If the caster experiences very low normal force, wheel flutter, vibration, instability, and loss of floor contact may occur. These effects can generate unpredictable vehicle behavior, particularly at higher speeds.

A common engineering guideline is to allocate approximately 10% to 30% of the total vehicle weight to passive casters, with the remaining load carried by the drive wheels. The exact percentage depends on vehicle geometry, payload variation, acceleration requirements, and floor conditions.

Dynamic loading introduces additional complexity. During acceleration, weight transfer shifts load toward the rear of the vehicle. During braking, load transfers toward the front. During cornering, lateral load transfer occurs across the vehicle width. These dynamic effects can significantly alter caster loading compared with static calculations.

For heavy-duty industrial AMRs, dynamic load analysis is especially important. Payloads of several hundred kilograms or more can create substantial load transfer effects. Engineers frequently use multibody dynamics simulations and finite element models to predict wheel loads under various operating conditions.

Caster load calculations also influence bearing selection, wheel material selection, mounting structure design, and frame reinforcement requirements. An undersized caster may experience excessive bearing stress, wheel deformation, or premature failure when subjected to repeated loading cycles.

The mounting position of the caster significantly affects load distribution. Moving the caster farther from the drive wheels generally increases leverage and changes reaction force distribution. Designers often adjust caster location to optimize traction performance and vehicle stability.

In modern industrial AMRs, load distribution analysis is not simply a structural calculation. It directly affects traction, navigation accuracy, power consumption, tire wear, and overall vehicle reliability. Proper caster load distribution ensures that drive wheels maintain sufficient traction while passive support wheels provide stable and predictable vehicle behavior throughout the robot\'s operational life.

---

### 3.2 Caster Swivel Radius

Caster Swivel Radius is one of the most important geometric parameters affecting the maneuverability and dynamic behavior of a caster wheel. Although caster wheels are passive components, their ability to rotate freely and align with the direction of travel has a major influence on steering smoothness, vibration levels, rolling resistance, and vehicle stability.

A caster wheel consists of two primary rotational mechanisms. The wheel itself rotates around its axle to provide rolling motion. Simultaneously, the entire caster assembly rotates around a vertical swivel axis. This second rotation allows the caster to align automatically with the vehicle\'s direction of movement.

The swivel radius is defined as the horizontal distance between the swivel axis and the wheel contact center. This distance is often referred to as caster offset or caster trail. It creates the self-aligning behavior that allows the caster to follow the motion of the vehicle.

When the robot begins moving, friction forces acting at the wheel-ground contact patch generate a moment about the swivel axis. This moment causes the caster to rotate until it aligns with the direction of travel. Without sufficient swivel radius, the caster may not self-align effectively. With excessive swivel radius, steering response may become sluggish and oscillatory.

The self-aligning torque generated by a caster can be approximated as:

T = F × R

where:

T = swivel torque

F = contact force

R = swivel radius

This relationship illustrates that larger swivel radii generate greater self-aligning torque. Increased torque improves directional stability but may also increase steering resistance during rapid changes in direction.

Swivel radius strongly influences caster stability at different speeds. Small swivel radii provide quick steering response and reduced turning resistance. However, they may be more susceptible to caster flutter, a dynamic instability characterized by rapid oscillation of the caster assembly.

Caster flutter is particularly problematic in high-speed AMRs. The oscillation generates vibration, noise, increased wear, and reduced navigation accuracy. Proper swivel radius selection helps minimize the likelihood of this phenomenon.

Large swivel radii generally improve straight-line stability because the caster naturally aligns with the direction of travel. However, excessively large offsets increase rotational inertia and may slow the caster\'s response during frequent directional changes.

Floor conditions also affect optimal swivel radius selection. Smooth industrial floors allow predictable caster behavior and can accommodate larger swivel radii. Rough surfaces, expansion joints, and uneven flooring may require different design compromises to maintain stable operation.

Swivel radius influences turning performance as well. During tight maneuvers, the caster must rapidly reorient itself as vehicle direction changes. If the swivel radius is too large, the caster may lag behind the vehicle motion, generating temporary scrubbing forces and increased rolling resistance.

Payload variations further complicate the design process. Heavier loads increase normal force at the caster wheel, which increases self-aligning torque. Consequently, the optimal swivel radius for a light-duty AMR may differ significantly from that of a heavy-duty industrial platform.

Engineers often evaluate caster swivel behavior through both analytical calculations and experimental testing. Dynamic simulations may model caster inertia, bearing friction, wheel deformation, floor friction, and vehicle acceleration profiles to predict real-world performance.

In industrial AMR applications, swivel radius selection directly affects maneuverability, energy efficiency, ride quality, and system reliability. A properly designed caster geometry allows smooth self-alignment, minimizes vibration, reduces rolling resistance, and supports accurate vehicle motion. As vehicle speeds, payloads, and operational complexity increase, careful optimization of caster swivel radius becomes an increasingly important aspect of overall robot chassis design.

---

### 3.3 Engineering Considerations for Caster Selection in Industrial AMRs

Although caster wheels are frequently regarded as secondary components compared with drive motors and steering systems, their selection can have a surprisingly large impact on overall AMR performance. In many cases, operational issues such as vibration, poor tracking accuracy, excessive energy consumption, and unexpected maintenance requirements can be traced back to improper caster design.

One of the first considerations is matching caster capacity to actual operating loads. Engineers should account not only for static vehicle weight but also for dynamic loading conditions. Acceleration, braking, obstacle crossing, and uneven floor conditions can temporarily increase wheel loads well beyond nominal values. A suitable safety margin is therefore essential.

Wheel diameter remains a critical parameter. Larger caster wheels improve floor-gap tolerance, reduce vibration transmission, and lower rolling resistance. Smaller casters may reduce overall vehicle height and cost but often suffer from increased sensitivity to floor irregularities.

Caster wheel material must also be selected carefully. Polyurethane casters are widely used in indoor industrial environments because of their durability, low rolling resistance, and clean operation. Rubber casters provide superior shock absorption and traction but generally experience higher wear and rolling resistance.

Bearing selection directly affects rolling performance and service life. Precision ball bearings typically provide lower rolling resistance and smoother operation than simpler bearing configurations. Heavy-duty AMRs often require high-capacity bearings capable of supporting significant radial and axial loads over long operating periods.

Mounting stiffness is another important factor. Flexible caster mounting structures can introduce unwanted vibration modes and tracking errors. Reinforced mounting plates and rigid frame integration help maintain predictable caster behavior.

Swivel bearing quality strongly influences long-term performance. High-quality swivel bearings reduce steering resistance and improve alignment consistency. In contrast, excessive bearing friction may delay caster alignment and increase energy losses during direction changes.

For high-speed AMRs, caster flutter prevention becomes a major design objective. Engineers may optimize swivel radius, wheel diameter, damping characteristics, and mass distribution to reduce the likelihood of oscillatory behavior.

Payload distribution must be considered at the system level. A perfectly designed caster may still perform poorly if the vehicle center of gravity shifts significantly during operation. Consequently, caster selection should always be integrated with overall chassis design rather than treated as an isolated component choice.

Modern industrial AMRs increasingly rely on detailed simulations and experimental validation when selecting caster systems. The interaction between caster geometry, load distribution, floor conditions, and vehicle dynamics is complex, making empirical testing an important complement to theoretical analysis.

Ultimately, successful caster selection requires balancing load capacity, maneuverability, vibration performance, durability, energy efficiency, and maintenance requirements. Although passive in nature, caster wheels contribute substantially to the overall behavior of a mobile robot and should be treated as essential elements of the chassis architecture rather than simple supporting accessories.

### 3.1 캐스터 하중 분배 계산(Caster Load Distribution Calculation)

캐스터 휠(Caster Wheel)은 종종 단순한 보조 지지 장치로 인식되지만, 실제로는 차량 안정성(Vehicle Stability), 하중 분배(Load Distribution), 기동성(Maneuverability), 내구성(Durability)에 매우 중요한 영향을 미친다. 많은 차동 구동(Differential Drive) 및 일부 스티어 구동(Steer Drive) 구조에서 캐스터는 수동 지지(Passive Support) 역할을 수행하며, 구동 휠은 추진력과 조향 기능을 담당한다. 캐스터는 일반적으로 추진력 생성에는 참여하지 않지만, 잘못된 하중 분배는 차량 성능 저하, 에너지 효율 감소, 진동 증가, 부품 수명 단축 등의 문제를 유발할 수 있다.

캐스터 하중 분배 계산의 가장 중요한 목적은 차량 전체 중량이 각 휠 접촉점(Contact Point)에 어떻게 분배되는지를 확인하는 것이다. 모든 휠은 구동 여부와 관계없이 차량 무게의 일부를 지지한다. 여기에는 차체(Base Vehicle), 배터리(Battery), 전장 장치(Electronics), 페이로드(Payload), 그리고 주행 중 발생하는 동적 하중(Dynamic Load)이 포함된다.

정적 평형(Static Equilibrium) 조건에서는 모든 휠의 반력(Reaction Force)의 합이 차량 총중량과 같아야 한다.

예를 들어 2개의 구동 휠과 1개의 캐스터 휠을 가진 구조에서는 다음과 같이 표현할 수 있다.

W = FD1 + FD2 + FC

여기서

W = 차량 총중량(Total Vehicle Weight)

FD1 = 구동 휠 1 하중

FD2 = 구동 휠 2 하중

FC = 캐스터 휠 하중

을 의미한다.

실제 각 휠이 지지하는 하중은 무게중심(Center of Gravity)의 위치에 따라 결정된다. 무게중심이 구동 휠 중심선에 가까울수록 캐스터가 받는 하중은 감소한다. 반대로 무게중심이 캐스터 방향으로 이동하면 캐스터 하중은 증가한다.

산업용 AMR 설계에서는 캐스터 하중을 일정 범위 내로 유지하는 것이 중요하다. 캐스터가 과도한 하중을 받으면 구동 휠에 작용하는 수직 하중(Normal Force)이 감소하게 된다. 구동력(Traction Force)은 수직 하중에 비례하므로, 캐스터에 너무 많은 하중이 집중되면 가속 성능, 등판 성능, 제동 성능이 저하될 수 있다.

반대로 캐스터 하중이 너무 낮아도 문제가 발생한다. 캐스터가 충분한 접지력을 확보하지 못하면 휠 플러터(Wheel Flutter), 진동(Vibration), 불안정성(Instability), 순간적인 접촉 손실(Contact Loss)이 발생할 수 있다. 이러한 현상은 특히 고속 주행 시 더욱 심각해진다.

실무적으로는 전체 차량 하중의 약 10\~30% 정도를 캐스터가 부담하도록 설계하는 경우가 많다. 나머지 70\~90%는 구동 휠이 담당하도록 하여 충분한 추진력을 확보한다. 물론 최적 비율은 차량 형상, 페이로드 변화, 가속 성능 요구사항, 바닥 상태에 따라 달라진다.

동적 하중은 더욱 복잡한 문제를 만든다. 가속 시에는 하중이 후방으로 이동하고, 제동 시에는 전방으로 이동한다. 또한 회전 시에는 좌우 방향의 하중 이동(Lateral Load Transfer)이 발생한다. 따라서 실제 운용 중 캐스터 하중은 정적 계산값과 상당한 차이를 보일 수 있다.

특히 수백 kg 이상의 중량급 산업용 AMR에서는 이러한 동적 하중 효과가 매우 중요하다. 엔지니어는 다물체 동역학(Multibody Dynamics) 시뮬레이션과 유한요소해석(FEA)을 활용하여 다양한 주행 조건에서 휠 하중 변화를 분석한다.

캐스터 하중 계산은 베어링(Bearing) 선정, 휠 재질 선정, 장착 구조 설계, 프레임 보강에도 직접적인 영향을 준다. 용량이 부족한 캐스터는 반복 하중에 의해 베어링 손상, 휠 변형, 조기 파손이 발생할 수 있다.

캐스터 위치도 중요한 변수이다. 구동 휠과의 거리가 증가하면 지렛대 효과(Leverage Effect)가 변하며 하중 분포도 달라진다. 따라서 설계자는 캐스터 위치를 조정하여 접지력과 차량 안정성을 최적화한다.

결국 캐스터 하중 분배는 단순한 구조 계산이 아니라 구동 성능, 위치 정확도(Localization Accuracy), 에너지 소비, 타이어 마모, 차량 신뢰성을 결정하는 핵심 요소이다. 적절한 하중 분배는 구동 휠이 충분한 접지력을 유지하면서도 캐스터가 안정적인 지지 역할을 수행하도록 보장한다.

---

### 3.2 캐스터 스위블 반경(Caster Swivel Radius)

캐스터 스위블 반경(Caster Swivel Radius)은 캐스터 휠의 기동성과 동적 거동(Dynamic Behavior)에 가장 큰 영향을 미치는 기하학적 파라미터(Geometric Parameter) 중 하나이다. 캐스터는 수동 부품(Passive Component)이지만, 자유롭게 회전하여 이동 방향에 자동 정렬(Self-Alignment)되는 능력은 조향 부드러움(Steering Smoothness), 진동 수준, 구름 저항, 차량 안정성에 직접적인 영향을 준다.

캐스터 휠은 두 가지 회전 메커니즘을 가진다. 첫 번째는 휠 축(Wheel Axle)을 중심으로 회전하는 일반적인 구름 운동(Rolling Motion)이다. 두 번째는 전체 캐스터 어셈블리(Caster Assembly)가 수직 회전축(Swivel Axis)을 중심으로 회전하는 운동이다.

스위블 반경은 수직 회전축과 휠 접촉 중심(Contact Center) 사이의 수평 거리(Horizontal Distance)를 의미한다. 이를 캐스터 오프셋(Caster Offset) 또는 캐스터 트레일(Caster Trail)이라고도 한다.

차량이 움직이기 시작하면 바퀴와 바닥 사이에 발생하는 마찰력이 회전축을 기준으로 모멘트(Moment)를 생성한다. 이 모멘트가 캐스터를 이동 방향으로 정렬시키는 힘이 된다.

이때 발생하는 자기 정렬 토크(Self-Aligning Torque)는 다음과 같이 표현할 수 있다.

T = F × R

여기서

T = 스위블 토크(Swivel Torque)

F = 접촉력(Contact Force)

R = 스위블 반경(Swivel Radius)

을 의미한다.

이 식에서 알 수 있듯이 스위블 반경이 커질수록 자기 정렬 토크도 증가한다. 이는 직진 안정성(Straight-Line Stability)을 향상시키지만 방향 전환 시 회전 저항을 증가시킬 수 있다.

작은 스위블 반경은 빠른 조향 응답(Fast Steering Response)을 제공한다. 방향 전환이 빈번한 환경에서는 유리하지만, 플러터(Flutter) 현상이 발생하기 쉬워진다.

캐스터 플러터(Caster Flutter)는 캐스터가 빠르게 좌우 진동하는 현상으로, 고속 AMR에서 특히 문제가 된다. 이는 소음 증가, 진동 증가, 부품 마모, 위치 정확도 저하를 유발한다.

반대로 큰 스위블 반경은 직진 안정성을 향상시키지만, 방향 전환 시 응답이 느려질 수 있다. 또한 회전 관성(Rotational Inertia)이 증가하여 빠른 기동성을 요구하는 환경에서는 불리할 수 있다.

바닥 상태도 중요한 변수이다. 평탄한 에폭시 바닥(Epoxy Floor)에서는 비교적 큰 스위블 반경을 사용할 수 있지만, 거친 콘크리트 바닥이나 요철이 많은 환경에서는 다른 설계 기준이 필요하다.

회전 성능에도 직접적인 영향을 준다. 좁은 공간에서 회전할 경우 캐스터는 빠르게 방향을 바꿔야 한다. 스위블 반경이 지나치게 크면 차량의 실제 이동 방향을 따라가지 못하고 지연(Lag)이 발생할 수 있다.

페이로드 변화 역시 고려해야 한다. 중량 증가로 인해 캐스터에 작용하는 수직 하중이 증가하면 자기 정렬 토크도 증가한다. 따라서 50kg급 AMR과 1500kg급 산업용 AMR은 전혀 다른 최적 스위블 반경을 가진다.

실제 산업용 AMR 설계에서는 해석 모델과 실험 데이터를 함께 사용하여 최적의 스위블 반경을 결정한다. 관성, 베어링 마찰, 휠 변형, 바닥 마찰, 차량 가속 프로파일 등을 모두 고려해야 하기 때문이다.

적절한 스위블 반경은 부드러운 자기 정렬, 낮은 진동, 낮은 구름 저항, 높은 위치 정확도를 제공한다. 차량 속도와 페이로드가 증가할수록 스위블 반경 최적화는 더욱 중요한 설계 요소가 된다.

---

### 3.3 산업용 AMR에서의 캐스터 선정 고려사항(Engineering Considerations for Caster Selection in Industrial AMRs)

캐스터 휠은 구동 모터나 조향 시스템에 비해 부차적인 부품처럼 보일 수 있지만, 실제로는 전체 AMR 성능에 매우 큰 영향을 미친다. 현장에서 발생하는 진동 문제, 위치 추종 오차(Tracking Error), 과도한 전력 소비, 유지보수 증가 문제의 상당수가 캐스터 설계에서 비롯되는 경우도 있다.

가장 먼저 고려해야 할 것은 하중 용량(Load Capacity)이다. 단순히 차량 정적 하중만 고려하는 것이 아니라 가속, 감속, 장애물 통과, 노면 불균일성에 의한 동적 하중까지 고려해야 한다. 따라서 충분한 안전계수(Safety Factor)를 확보하는 것이 중요하다.

휠 직경 역시 중요한 요소이다. 큰 캐스터 휠은 바닥 틈새 통과 능력(Floor Gap Tolerance), 진동 감소, 구름 저항 감소 측면에서 유리하다. 반면 작은 캐스터는 차량 높이와 비용을 줄일 수 있지만 노면 상태에 더 민감하다.

휠 재질도 신중하게 선택해야 한다. 폴리우레탄(PU)은 내구성, 청정성, 낮은 구름 저항으로 인해 실내 산업 환경에서 널리 사용된다. 고무(Rubber)는 충격 흡수와 접지력이 우수하지만 마모와 에너지 손실이 상대적으로 크다.

베어링 선정도 매우 중요하다. 정밀 볼 베어링(Precision Ball Bearing)은 낮은 구름 저항과 부드러운 움직임을 제공한다. 중량급 AMR에서는 높은 반경 방향 하중(Radial Load)과 축 방향 하중(Axial Load)을 견딜 수 있는 고하중 베어링이 필요하다.

장착 강성(Mounting Stiffness) 역시 중요하다. 유연한 장착 구조는 원치 않는 진동 모드(Vibration Mode)와 위치 오차를 유발할 수 있다. 따라서 강화된 장착 플레이트와 강성 높은 프레임 연결 구조가 필요하다.

스위블 베어링(Swivel Bearing)의 품질도 장기 성능에 큰 영향을 준다. 고품질 베어링은 낮은 조향 저항과 우수한 정렬 성능을 제공한다. 반면 마찰이 큰 베어링은 방향 전환 시 에너지 손실과 응답 지연을 유발한다.

고속 AMR에서는 캐스터 플러터 억제가 중요한 목표가 된다. 이를 위해 스위블 반경, 휠 직경, 감쇠 특성(Damping Characteristic), 질량 분포(Mass Distribution)를 함께 최적화한다.

페이로드 분배도 시스템 차원에서 고려해야 한다. 아무리 우수한 캐스터를 사용하더라도 무게중심이 크게 이동하면 기대한 성능을 얻을 수 없다. 따라서 캐스터 선정은 반드시 전체 섀시 설계와 통합적으로 수행되어야 한다.

최근 산업용 AMR 개발에서는 캐스터 시스템도 정밀 시뮬레이션과 실험 검증을 통해 최적화되고 있다. 캐스터 기하학, 하중 분배, 바닥 상태, 차량 동역학의 상호작용은 매우 복잡하기 때문이다.

결국 성공적인 캐스터 선정은 하중 용량, 기동성, 진동 성능, 내구성, 에너지 효율, 유지보수성을 균형 있게 맞추는 과정이다. 캐스터는 수동 부품이지만 이동 로봇 전체 거동에 큰 영향을 주므로 단순한 보조 바퀴가 아닌 핵심 섀시 구성 요소(Core Chassis Component)로 다루어져야 한다.

특히 힐스로보틱스(Hills Robotics)의 500kg\~1500kg급 산업용 AMR에서는 전체 하중의 약 15\~25% 수준을 캐스터가 지지하도록 설계하고, 휠 직경은 최소 200\~300mm 이상, 고하중 PU 캐스터 또는 산업용 중량 캐스터를 적용하는 것이 안정성, 내구성, 정밀도 측면에서 유리하다. 또한 1000kg 이상급에서는 단순 캐스터 구조보다 액티브 캐스터(Active Caster) 또는 스티어 구동(Steer Drive) 구조로 전환하는 것이 장기적으로 더 효율적인 설계가 될 수 있다.

##  

## 04 Load Distribution

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Static Load Distribution Calculation

Static Load Distribution Calculation is one of the most important engineering activities in the design of Autonomous Mobile Robots (AMRs). Before analyzing motion, acceleration, or dynamic behavior, engineers must first understand how the total vehicle weight is distributed among the wheels, drive modules, casters, suspension systems, and structural frame under stationary conditions. A correct static load distribution analysis forms the foundation for wheel selection, motor sizing, bearing design, structural strength calculations, traction analysis, and overall vehicle stability.

In its simplest form, static load distribution is governed by the principles of static equilibrium. When a robot is stationary, the sum of all vertical reaction forces generated by the wheels must equal the total gravitational force acting on the vehicle. Simultaneously, the sum of moments around any reference point must equal zero. These two conditions ensure that the vehicle remains balanced without rotating or tipping.

The total vehicle weight consists of multiple components including the chassis, batteries, motors, controllers, sensors, payload modules, safety equipment, and any customer-installed accessories. Each component contributes to the overall center of gravity (CG), and the location of this center of gravity determines how the load is distributed among the wheel contact points.

For a simple four-wheel vehicle, the load on each wheel can be determined by treating the robot as a rigid body supported at four contact locations. The reaction forces are calculated by considering the distances between the center of gravity and each wheel. When the center of gravity is located exactly at the geometric center of the vehicle, the load tends to be distributed evenly among all wheels. However, in real industrial robots, the center of gravity rarely coincides with the geometric center.

Battery packs often represent a significant portion of total vehicle mass. Large battery modules positioned near the rear of the chassis shift the center of gravity rearward. Similarly, robotic manipulators, lifting systems, inspection equipment, and payloads can significantly alter load distribution. As a result, some wheels may experience substantially higher loading than others.

Uneven static load distribution can create several operational challenges. Wheels carrying excessive load experience increased rolling resistance, higher bearing stress, accelerated tire wear, and greater structural fatigue. Conversely, lightly loaded wheels may provide insufficient traction and become susceptible to slipping under acceleration or braking.

Load distribution directly influences traction capability because the maximum friction force available at a wheel is proportional to the normal force acting on that wheel. In Differential Drive systems, maintaining adequate load on the drive wheels is particularly important. If too much weight is transferred to passive casters or support wheels, available traction decreases and vehicle performance deteriorates.

The analysis also affects wheel diameter selection and wheel material selection. Heavily loaded wheels may require larger diameters, stronger hubs, reinforced bearings, and higher-capacity tire materials. Small design errors in load estimation can result in premature component failures and unexpected maintenance requirements.

Static load distribution is especially critical for heavy-duty industrial AMRs carrying payloads of several hundred kilograms or more. As payload increases, structural deflection becomes increasingly important. The frame itself may deform slightly under load, altering the actual distribution of forces compared to theoretical calculations. Engineers therefore frequently combine analytical calculations with Finite Element Analysis (FEA) to evaluate real-world behavior.

Another important consideration is floor flatness. Static load calculations typically assume a perfectly rigid vehicle operating on a perfectly flat surface. In practice, manufacturing tolerances, floor irregularities, wheel compliance, and structural flexibility create deviations from ideal conditions. Suspension systems or compliant wheel designs are often introduced to maintain stable contact across all wheels.

The center of gravity height also plays an indirect role in static loading. Although height does not directly affect vertical force distribution under static conditions, it significantly influences vehicle stability and determines how dynamic loads will be transferred during motion.

Industrial AMR designers frequently use load distribution maps during the conceptual design phase. These maps visualize wheel loads under different payload configurations and help engineers optimize component placement. Batteries, controllers, sensors, and payload interfaces are often repositioned to achieve more balanced loading conditions.

Ultimately, static load distribution calculation is far more than a theoretical exercise. It serves as the starting point for nearly every mechanical and dynamic analysis performed during AMR development. Accurate load distribution improves traction, reduces component wear, enhances energy efficiency, increases structural reliability, and provides a stable foundation for all subsequent vehicle design activities.

---

### 4.2 Dynamic Load Eccentricity Consideration

While static load distribution provides the foundation for vehicle design, real AMRs rarely operate under purely static conditions. During acceleration, braking, turning, obstacle crossing, lifting operations, and payload handling, the load distribution continuously changes. These changes are commonly referred to as dynamic load transfer, and one of the most important causes of dynamic load transfer is load eccentricity.

Dynamic Load Eccentricity refers to the condition in which the center of gravity is offset from the ideal geometric center of the vehicle or shifts during operation. This offset generates additional moments and force imbalances that affect wheel loading, traction, stability, and vehicle handling characteristics. Understanding and controlling load eccentricity is essential for achieving safe and reliable operation in industrial environments.

The concept can be understood by considering a payload placed at the center of a robot versus one placed near an edge. When the payload is centered, wheel loads remain relatively balanced. When the payload is shifted forward, backward, or sideways, the center of gravity moves accordingly. This movement changes the reaction forces acting on each wheel and creates an eccentric loading condition.

Dynamic eccentricity becomes even more significant when the vehicle begins moving. During acceleration, inertial forces act through the center of gravity. Because the center of gravity is located above the floor, these forces create pitching moments that transfer load between front and rear wheels.

When the vehicle accelerates forward, load shifts toward the rear. During braking, load transfers toward the front. The magnitude of this transfer depends on acceleration level, vehicle mass, wheelbase length, and center of gravity height.

The relationship can be expressed conceptually as:

Load Transfer ∝ (Mass × Acceleration × CG Height) / Wheelbase

This equation highlights the primary factors influencing dynamic load transfer. Higher acceleration, larger vehicle mass, and elevated center of gravity all increase load transfer effects.

Lateral load transfer occurs during turning maneuvers. As the robot follows a curved path, centrifugal effects create lateral forces that shift load from the inner wheels to the outer wheels. Vehicles carrying elevated payloads experience significantly larger lateral load transfers due to their higher center of gravity.

Steer Drive and Differential Drive systems respond differently to dynamic eccentricity. Differential Drive robots often experience increased wheel slip when heavily loaded wheels carry most of the traction demand. Steer Drive systems generally distribute forces more effectively because wheel orientations align with the desired motion path.

Payload variability introduces additional complexity. Industrial AMRs frequently transport objects with varying mass distributions. A pallet loaded symmetrically behaves differently from one carrying a concentrated load near one corner. Consequently, wheel loads may vary dramatically between missions.

Mobile manipulators represent a particularly challenging case. When a robotic arm extends outward, the center of gravity shifts continuously. The resulting eccentric loads can significantly alter wheel reactions and stability margins. In extreme cases, improper load management may create tipping hazards.

Obstacle crossing generates additional dynamic load eccentricity. When a wheel climbs over a floor gap, threshold, or ramp, vehicle attitude changes temporarily. This alters the effective center of gravity position relative to the wheel contact points and produces transient load redistribution.

Dynamic load eccentricity directly affects traction performance. Wheels experiencing reduced normal force provide less frictional capability and become more susceptible to slip. This influences acceleration performance, braking distance, localization accuracy, and path-tracking precision.

Battery placement, payload placement, and component layout therefore become important design decisions. Engineers often position heavy components near the geometric center of the chassis and as low as possible to minimize dynamic load transfer. This approach improves stability and reduces sensitivity to eccentric loading.

Simulation tools such as multibody dynamics software are commonly used to analyze dynamic eccentricity. These models evaluate wheel loads under acceleration, braking, turning, and obstacle-crossing conditions. The resulting data helps engineers optimize chassis geometry, wheel placement, suspension characteristics, and payload configurations.

For heavy-duty industrial AMRs carrying payloads above 500 kg, dynamic load eccentricity becomes one of the dominant design considerations. Small shifts in center of gravity can produce large variations in wheel loading, traction utilization, and structural stress. Consequently, successful heavy-duty AMR design requires careful integration of static load calculations, dynamic load transfer analysis, and center-of-gravity management strategies.

Ultimately, Dynamic Load Eccentricity Consideration bridges the gap between idealized static models and real-world vehicle behavior. By understanding how loads shift during operation, engineers can design robots that maintain stability, traction, accuracy, and reliability across a wide range of operating conditions and payload scenarios.

### 4.1 정적 하중 분배 계산(Static Load Distribution Calculation)

정적 하중 분배 계산(Static Load Distribution Calculation)은 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)의 기계 설계에서 가장 중요한 기초 해석 중 하나이다. 차량의 운동, 가속, 동적 거동을 분석하기 전에 먼저 차량 전체 중량이 휠(Wheel), 구동 모듈(Drive Module), 캐스터(Caster), 서스펜션(Suspension), 프레임(Frame)에 어떻게 분배되는지를 정확하게 이해해야 한다. 올바른 정적 하중 분배 해석은 휠 선정, 모터 용량 산정, 베어링 설계, 구조 강도 계산, 접지력(Traction) 분석, 차량 안정성 평가의 출발점이 된다.

정적 하중 분배는 기본적으로 정적 평형(Static Equilibrium)의 원리를 따른다. 차량이 정지 상태에 있을 때 모든 휠이 지면에 가하는 반력(Reaction Force)의 총합은 차량 전체 중량과 동일해야 한다. 또한 임의의 기준점에 대한 모멘트(Moment)의 합도 0이 되어야 한다. 이러한 조건이 만족되어야 차량이 기울어지거나 회전하지 않고 안정적으로 유지될 수 있다.

차량 총중량은 여러 구성 요소의 합으로 이루어진다. 프레임, 배터리(Battery), 모터(Motor), 제어기(Controller), 센서(Sensor), 페이로드(Payload), 안전 장비(Safety Equipment), 고객 장착 장비(Customer Equipment) 등이 모두 포함된다. 각 부품은 전체 무게중심(Center of Gravity, CG)에 영향을 주며, 이 무게중심의 위치가 휠별 하중 분배를 결정한다.

예를 들어 4륜 구조의 차량에서는 각 휠 접촉점을 지지점으로 하는 강체(Rigid Body) 모델을 적용할 수 있다. 무게중심이 차량 중심에 정확히 위치하면 각 휠이 거의 동일한 하중을 받게 된다. 그러나 실제 산업용 AMR에서는 무게중심이 차량 중심에 정확히 위치하는 경우가 드물다.

배터리 팩은 일반적으로 차량 중량의 상당 부분을 차지한다. 대용량 배터리가 후방에 배치되면 무게중심은 뒤쪽으로 이동하게 된다. 또한 로봇팔(Robot Arm), 리프터(Lifter), 검사 장비(Inspection Equipment), CAD2SCAN과 같은 상부 장비가 탑재되면 무게중심은 특정 방향으로 크게 이동할 수 있다.

불균형한 정적 하중 분배는 다양한 문제를 발생시킨다. 과도한 하중이 걸리는 휠은 구름 저항(Rolling Resistance)이 증가하고 베어링 응력(Bearing Stress)이 커지며 타이어 마모(Tire Wear)와 구조 피로(Structural Fatigue)가 가속된다. 반대로 하중이 적은 휠은 충분한 접지력을 확보하지 못해 가속 및 제동 시 슬립(Slip)이 발생하기 쉽다.

하중 분배는 접지력에도 직접적인 영향을 미친다. 마찰력(Friction Force)은 수직 하중(Normal Force)에 비례하기 때문이다. 특히 차동 구동(Differential Drive) 차량에서는 구동 휠에 충분한 하중이 걸려야 한다. 만약 지나치게 많은 하중이 캐스터나 보조 휠에 분산되면 추진력이 감소하고 등판 성능과 제동 성능이 저하될 수 있다.

정적 하중 분배는 휠 직경(Wheel Diameter) 및 휠 재질(Tire Material) 선정에도 영향을 준다. 높은 하중을 받는 휠은 더 큰 직경, 더 강한 허브(Hub), 고하중 베어링, 강화된 타이어 재질이 필요할 수 있다. 초기 하중 계산이 부정확하면 예상보다 빠른 부품 고장이 발생할 수 있다.

500kg 이상의 중량급 산업용 AMR에서는 정적 하중 분배가 더욱 중요해진다. 하중이 증가할수록 프레임 변형(Frame Deflection)이 발생할 수 있으며, 실제 하중 분배는 단순 계산 결과와 달라질 수 있다. 따라서 엔지니어는 정적 계산뿐 아니라 유한요소해석(FEA, Finite Element Analysis)을 함께 수행하여 실제 응력과 변형을 검토한다.

바닥 평탄도(Floor Flatness)도 중요한 요소이다. 대부분의 계산은 완전히 평탄한 바닥을 가정하지만 실제 환경에서는 바닥 요철, 제작 공차, 휠 탄성(Wheel Compliance), 프레임 유연성(Frame Flexibility)이 존재한다. 이를 보완하기 위해 서스펜션 시스템이나 탄성 휠 구조가 적용되기도 한다.

무게중심 높이(CG Height)는 정적 하중 분배에 직접 영향을 주지는 않지만 차량 안정성에 중요한 역할을 한다. 높은 무게중심은 향후 가속, 감속, 회전 시 발생하는 동적 하중 이동(Dynamic Load Transfer)을 증가시킨다.

실제 산업용 AMR 개발에서는 다양한 페이로드 조건에 대한 하중 분배 맵(Load Distribution Map)을 작성한다. 이를 통해 배터리, 제어기, 센서, 인터페이스 장비의 위치를 최적화하고 균형 잡힌 하중 분배를 달성한다.

결국 정적 하중 분배 계산은 단순한 구조 해석이 아니라 AMR 전체 설계의 출발점이다. 정확한 하중 분배는 접지력 향상, 마모 감소, 에너지 효율 향상, 구조 신뢰성 확보, 그리고 장기적인 유지보수 비용 절감에 기여한다.

---

### 4.2 동적 하중 편심 고려(Dynamic Load Eccentricity Consideration)

정적 하중 분배는 설계의 기초를 제공하지만 실제 AMR은 거의 항상 동적 환경(Dynamic Environment)에서 운용된다. 차량이 가속(Acceleration), 감속(Braking), 회전(Turning), 장애물 통과(Obstacle Crossing), 리프팅(Lifting), 물체 운반(Payload Handling)을 수행할 때 하중 분포는 지속적으로 변한다. 이러한 현상을 동적 하중 이동(Dynamic Load Transfer)이라고 하며, 그 핵심 원인 중 하나가 하중 편심(Load Eccentricity)이다.

동적 하중 편심(Dynamic Load Eccentricity)은 무게중심이 차량의 이상적인 기하학적 중심(Geometric Center)에서 벗어나 있거나 운행 중 이동하는 현상을 의미한다. 이러한 편심은 추가적인 모멘트(Moment)를 발생시키며 휠 하중, 접지력, 안정성, 조향 특성에 영향을 준다. 따라서 산업용 AMR에서 하중 편심을 이해하고 제어하는 것은 매우 중요하다.

예를 들어 페이로드가 차량 중앙에 위치한 경우와 한쪽 끝에 위치한 경우를 비교해 보자. 중앙 적재 시에는 하중이 비교적 균등하게 분배된다. 반면 페이로드가 앞쪽, 뒤쪽 또는 측면으로 이동하면 무게중심도 함께 이동하여 각 휠에 작용하는 하중이 달라진다.

차량이 움직이기 시작하면 편심 효과는 더욱 커진다. 가속 시에는 관성력(Inertial Force)이 무게중심을 통해 작용한다. 무게중심은 지면보다 높은 위치에 있기 때문에 피칭 모멘트(Pitching Moment)가 발생하며 전후 방향 하중 이동이 일어난다.

차량이 전진 가속하면 하중은 후방으로 이동하고, 제동 시에는 전방으로 이동한다. 이 이동량은 차량 질량(Mass), 가속도(Acceleration), 휠베이스(Wheelbase), 무게중심 높이에 의해 결정된다.

개념적으로 다음과 같이 표현할 수 있다.

하중 이동 ∝ (질량 × 가속도 × 무게중심 높이) / 휠베이스

이 식은 동적 하중 이동을 증가시키는 주요 요소를 보여준다. 높은 가속도, 큰 질량, 높은 무게중심은 모두 하중 이동을 증가시킨다.

회전 시에는 횡방향 하중 이동(Lateral Load Transfer)이 발생한다. 차량이 곡선을 따라 움직일 때 원심력(Centrifugal Effect)에 의해 하중이 안쪽 휠에서 바깥쪽 휠로 이동한다. 특히 무게중심이 높은 차량은 이러한 현상이 더욱 크게 나타난다.

차동 구동과 스티어 구동은 동적 편심에 대해 서로 다른 특성을 가진다. 차동 구동은 특정 휠에 하중이 집중되면 슬립이 증가하기 쉽다. 반면 스티어 구동은 휠이 실제 이동 방향에 정렬되므로 하중 분배와 힘 전달이 상대적으로 효율적이다.

페이로드 변화도 큰 영향을 준다. 산업용 AMR은 항상 동일한 물체를 운반하지 않는다. 균일하게 적재된 팔레트(Pallet)와 한쪽에 무게가 집중된 팔레트는 전혀 다른 하중 분포를 만든다. 따라서 휠 하중은 작업마다 크게 달라질 수 있다.

모바일 매니퓰레이터(Mobile Manipulator)는 더욱 복잡한 사례이다. 로봇팔이 앞으로 뻗거나 측면으로 회전하면 무게중심이 지속적으로 이동한다. 이 과정에서 특정 휠에 과도한 하중이 집중될 수 있으며, 심한 경우 전복(Tipping) 위험도 발생한다.

장애물 통과 역시 편심을 증가시킨다. 차량이 턱, 경사로(Ramp), 바닥 틈새(Floor Gap)를 넘을 때 차체 자세(Vehicle Attitude)가 변화하며 무게중심의 상대 위치도 달라진다. 이로 인해 순간적인 하중 재분배(Transient Load Redistribution)가 발생한다.

동적 하중 편심은 접지력에도 직접적인 영향을 준다. 수직 하중이 감소한 휠은 마찰력을 충분히 생성하지 못하기 때문에 슬립이 발생하기 쉽다. 이는 가속 성능, 제동 거리, 위치 정확도, 경로 추종 성능에 영향을 미친다.

따라서 배터리, 제어기, 모터, 페이로드 인터페이스의 위치 선정은 매우 중요하다. 일반적으로 무거운 부품은 가능한 한 차량 중심에 가깝고 낮은 위치에 배치하여 무게중심 이동을 최소화한다.

현대 산업용 AMR 개발에서는 다물체 동역학(Multibody Dynamics) 시뮬레이션을 활용하여 동적 편심을 분석한다. 가속, 감속, 회전, 장애물 통과 조건에서 휠 하중 변화를 계산하고 이를 바탕으로 프레임 구조, 휠 위치, 서스펜션 특성, 페이로드 배치를 최적화한다.

특히 500kg 이상의 중량급 산업용 AMR에서는 동적 하중 편심이 설계를 결정하는 핵심 요소 중 하나이다. 무게중심이 수 cm만 이동해도 휠 하중과 구조 응력이 크게 달라질 수 있기 때문이다.

결국 동적 하중 편심 고려는 이상적인 정적 모델과 실제 차량 거동 사이의 차이를 연결하는 중요한 과정이다. 이를 정확히 이해하면 다양한 운용 조건에서도 안정성(Stability), 접지력(Traction), 위치 정확도(Localization Accuracy), 신뢰성(Reliability)을 유지할 수 있는 산업용 AMR을 설계할 수 있다. 특히 힐스로보틱스(Hills Robotics)의 500kg, 1000kg, 1500kg급 플랫폼에서는 정적 하중 계산만으로는 충분하지 않으며, 반드시 동적 하중 이동과 무게중심 관리(CG Management)를 함께 고려해야 한다. 이는 스티어 구동(Steer Drive) 플랫폼의 효율성과 정밀도를 극대화하는 핵심 설계 요소가 된다.

##  

## 05 Vibration Considerations

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Drive System Vibration Sources

Vibration is an unavoidable phenomenon in every mobile robotic system. Even when an Autonomous Mobile Robot (AMR) operates on a smooth industrial floor, multiple mechanical, electrical, and structural mechanisms continuously generate vibration energy. These vibrations propagate through the chassis, payload deck, sensor mounting structures, and electronic subsystems. Understanding the origin of these vibrations is essential because excessive vibration can reduce localization accuracy, shorten component lifespan, degrade payload performance, and negatively affect overall vehicle reliability.

One of the primary vibration sources in an AMR is the drive motor itself. Electric motors generate torque through electromagnetic interactions between the stator and rotor. Although modern brushless motors are highly efficient and smooth, they still produce periodic electromagnetic forces. These forces create torque ripple, which appears as small oscillations in output torque. The magnitude of torque ripple depends on motor design, pole count, controller algorithms, and operating conditions.

Motor control strategies also contribute to vibration generation. Pulse Width Modulation (PWM) switching introduces high-frequency electrical excitation into the motor system. While most of these frequencies are beyond the range of human perception, they can excite structural resonances within lightweight chassis components. Advanced motor controllers often employ field-oriented control and optimized switching strategies to minimize these effects.

Gearboxes represent another major vibration source. Most industrial AMRs use planetary gearboxes, helical gear reducers, or harmonic drive systems to increase output torque. During operation, gear teeth continuously engage and disengage, creating periodic excitation forces known as gear mesh frequencies. Manufacturing tolerances, backlash, tooth profile errors, and wear can amplify these vibrations over time.

Bearing systems contribute additional vibration components. Rolling element bearings generate characteristic vibration frequencies related to ball pass frequencies, cage frequencies, and rotational speeds. Under ideal conditions these vibrations are minimal, but improper lubrication, contamination, misalignment, or wear can significantly increase vibration levels.

Wheel-ground interaction is often the dominant vibration source in practical industrial environments. Even seemingly smooth floors contain expansion joints, small cracks, surface waviness, coating irregularities, and embedded debris. Every wheel crossing such discontinuities generates impact forces that propagate through the robot structure. The frequency and amplitude of these impacts depend on wheel diameter, tire material, vehicle speed, payload, and floor quality.

Differential Drive systems may generate additional vibration due to wheel scrubbing during turning. Since the wheels cannot align with the instantaneous turning direction, lateral slipping occurs at the contact patch. This slipping produces friction-induced vibration and can contribute to uneven tire wear. Steer Drive systems generally reduce this effect because the wheel orientation follows the desired motion trajectory.

Omni-wheel and mecanum-wheel systems introduce unique vibration mechanisms. The segmented roller structure of these wheels creates periodic variations in contact conditions as the wheel rotates. Each roller transition generates a small impact event, resulting in characteristic vibration patterns that are often absent in conventional wheels.

Structural flexibility also plays an important role. Every frame possesses natural frequencies and mode shapes. When excitation frequencies generated by motors, gearboxes, wheels, or payload equipment approach these natural frequencies, resonance may occur. Resonance amplifies vibration amplitudes significantly and can cause accelerated fatigue damage.

Payload equipment frequently introduces additional vibration sources. Robotic manipulators, lifting systems, conveyor modules, pumps, compressors, cooling fans, and inspection equipment all contribute their own dynamic excitations. In many industrial applications, payload-generated vibration can exceed the vibration originating from the mobile platform itself.

Environmental influences must also be considered. Floor quality variations, ramps, thresholds, uneven loading conditions, and external impacts create disturbances that excite the vehicle structure. Even nearby industrial equipment can transmit vibration through the floor into the robot.

Sensor systems are particularly sensitive to vibration. Cameras may experience image blur, LiDAR systems may suffer measurement noise, IMUs may exhibit increased drift, and precision inspection equipment may lose measurement accuracy. As AMRs become increasingly dependent on perception and localization technologies, vibration control becomes more critical than ever.

Modern AMR engineering therefore treats vibration as a system-level challenge rather than an isolated mechanical issue. Designers must identify all major vibration sources, characterize their frequency content, evaluate structural resonances, and develop appropriate mitigation strategies. Through careful integration of motors, gearboxes, wheels, frame structures, and isolation systems, vibration levels can be reduced sufficiently to ensure reliable and accurate operation throughout the robot's service life.

---

### 5.2 Passive Isolation Mount Design

Passive Isolation Mount Design is one of the most widely used approaches for controlling vibration in Autonomous Mobile Robots. Unlike active vibration control systems that require sensors, actuators, and real-time feedback algorithms, passive isolation systems rely on mechanical elements such as elastomers, springs, damping materials, and compliant structures to reduce vibration transmission. Their simplicity, reliability, low cost, and maintenance-free operation make them particularly attractive for industrial AMR applications.

The primary objective of a passive isolation mount is to prevent vibration energy from propagating from a vibration source to a sensitive subsystem. In a typical AMR, vibration sources include drive motors, gearboxes, wheels, pumps, cooling fans, and payload equipment. Sensitive components often include cameras, LiDARs, IMUs, computing systems, battery modules, and precision inspection sensors.

The fundamental principle of vibration isolation can be understood using a simple mass-spring-damper model. In this model, the isolated component is represented by a mass, while the isolation mount provides spring stiffness and damping characteristics. When vibration is applied to the base structure, the mount acts as a mechanical filter that attenuates transmitted motion.

A key design parameter is the natural frequency of the isolation system. Effective vibration isolation occurs when the excitation frequency is significantly higher than the natural frequency of the mounted subsystem. Under these conditions, the mount reduces transmitted vibration amplitudes rather than amplifying them.

The natural frequency depends primarily on the supported mass and mount stiffness. Softer mounts generally produce lower natural frequencies and better high-frequency isolation. However, excessively soft mounts may introduce excessive movement, positioning errors, and reduced structural stability. Therefore, engineers must carefully balance isolation performance against mechanical rigidity requirements.

Elastomeric mounts are among the most common passive isolation solutions in industrial robotics. Materials such as natural rubber, silicone rubber, neoprene, polyurethane, and thermoplastic elastomers provide both stiffness and damping in a single component. Their compact size and simple installation make them attractive for AMR applications.

Rubber isolation mounts are frequently used for motor controllers, edge computers, battery systems, and sensor assemblies. These mounts effectively attenuate high-frequency vibration while maintaining sufficient structural support. However, material aging, temperature variation, and long-term creep must be considered during design.

Spring-based isolation systems are often employed when lower natural frequencies are required. Coil springs provide excellent isolation performance for larger masses but typically require supplemental damping elements to prevent excessive oscillation. Without damping, resonance amplification can become problematic.

Wire-rope isolators are another specialized passive isolation technology commonly used in harsh industrial environments. These devices consist of stainless-steel cable loops that provide both elasticity and damping. They are highly durable, resistant to environmental exposure, and capable of operating across a wide temperature range.

Sensor isolation represents one of the most critical applications of passive mounts in AMRs. Cameras require stable optical alignment to maintain image quality. LiDAR systems require vibration control to preserve ranging accuracy. IMUs are particularly sensitive because vibration can introduce measurement noise that degrades localization and navigation performance.

Payload isolation is equally important for mobile inspection systems. Equipment such as metrology sensors, laser scanners, machine vision systems, and high-precision inspection instruments often require vibration levels significantly lower than those experienced by the vehicle chassis. Dedicated isolation platforms are frequently integrated into the payload deck to meet these requirements.

Mount placement is another crucial consideration. The effectiveness of an isolation system depends not only on mount properties but also on its location relative to the center of gravity of the supported component. Poor mount placement may introduce rocking modes, rotational oscillations, and uneven load sharing.

Finite Element Analysis and modal analysis are commonly used to optimize isolation designs. Engineers evaluate structural mode shapes, natural frequencies, damping ratios, and vibration transmission paths before selecting isolation hardware. Experimental validation using accelerometers and vibration measurements is often performed to confirm design performance.

As industrial AMRs increasingly incorporate advanced perception systems, AI computing platforms, precision sensors, and complex payloads, vibration management becomes a critical engineering discipline. Passive isolation mounts provide a practical and cost-effective solution for controlling vibration, improving sensor accuracy, extending component lifespan, enhancing reliability, and ensuring stable operation across a wide range of industrial environments.

In modern AMR design, passive isolation should not be viewed as an optional accessory added late in development. Instead, it should be integrated into the chassis architecture from the earliest design stages. Properly engineered isolation systems enable higher navigation accuracy, improved payload performance, reduced maintenance requirements, and greater overall system robustness, particularly in heavy-duty industrial robots operating under demanding real-world conditions.

### 5.1 구동 시스템 진동 발생원(Drive System Vibration Sources)

진동(Vibration)은 모든 이동 로봇 시스템에서 피할 수 없는 물리적 현상이다. 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)이 매우 평탄한 산업용 바닥 위를 주행하더라도 다양한 기계적(Mechanical), 전기적(Electrical), 구조적(Structural) 원인에 의해 지속적으로 진동이 발생한다. 이러한 진동은 차체(Chassis), 페이로드 데크(Payload Deck), 센서 마운트(Sensor Mount), 전자장치(Electronics) 등 차량 전체로 전달된다. 과도한 진동은 위치추정 정확도(Localization Accuracy)를 저하시키고, 부품 수명을 단축시키며, 검사 장비 성능을 떨어뜨리고, 전체 시스템 신뢰성(Reliability)을 감소시킨다. 따라서 진동 발생 원인을 정확히 이해하는 것은 산업용 AMR 설계에서 매우 중요한 과제이다.

가장 기본적인 진동 발생원은 구동 모터(Drive Motor)이다. 전기 모터는 고정자(Stator)와 회전자(Rotor) 사이의 전자기적 상호작용(Electromagnetic Interaction)을 통해 토크를 생성한다. 최신 브러시리스 모터(Brushless Motor)는 매우 부드럽게 동작하지만 완전히 일정한 토크를 발생시키지는 않는다. 전자기 구조의 특성상 토크 리플(Torque Ripple)이 발생하며, 이는 미세한 진동의 형태로 나타난다.

모터 제어 방식도 진동 발생에 영향을 준다. 대부분의 산업용 모터는 PWM(Pulse Width Modulation)을 사용하여 구동된다. PWM 스위칭은 고주파 전기적 자극을 발생시키며, 이러한 주파수가 차량 구조물의 고유진동수(Natural Frequency)와 일치할 경우 구조 공진(Structural Resonance)이 발생할 수 있다. 이를 줄이기 위해 최신 모터 제어기는 FOC(Field Oriented Control)와 최적화된 스위칭 알고리즘을 사용한다.

감속기(Gearbox)는 또 다른 주요 진동 발생원이다. 산업용 AMR은 일반적으로 유성 감속기(Planetary Gearbox), 헬리컬 감속기(Helical Reducer), 하모닉 드라이브(Harmonic Drive)를 사용한다. 기어 치형(Gear Tooth)이 지속적으로 맞물리고 분리되면서 기어 메시 주파수(Gear Mesh Frequency)가 발생한다. 제조 공차(Manufacturing Tolerance), 백래시(Backlash), 치형 오차(Profile Error), 마모(Wear)는 이러한 진동을 더욱 증폭시킬 수 있다.

베어링(Bearing)도 진동을 생성한다. 볼 베어링(Ball Bearing)이나 롤러 베어링(Roller Bearing)은 회전 중 특정 고유 주파수를 발생시키며, 윤활 부족(Lubrication Deficiency), 오염(Contamination), 정렬 불량(Misalignment), 마모가 발생하면 진동 수준이 급격히 증가할 수 있다.

실제 산업 환경에서는 휠과 바닥의 상호작용(Wheel-Ground Interaction)이 가장 큰 진동 발생원이 되는 경우가 많다. 산업용 바닥은 완전히 평탄하지 않으며 익스팬션 조인트(Expansion Joint), 균열(Crack), 코팅 불균일성(Coating Irregularity), 작은 이물질(Debris) 등이 존재한다. 휠이 이러한 요소를 통과할 때마다 충격 하중(Impact Load)이 발생하며 차량 전체에 전달된다.

차동 구동(Differential Drive)은 회전 시 추가적인 진동을 발생시킬 수 있다. 휠이 실제 회전 경로와 정렬되지 못하기 때문에 횡방향 스크러빙(Lateral Scrubbing)이 발생하며, 이 과정에서 마찰 진동(Friction-Induced Vibration)이 생성된다. 스티어 구동(Steer Drive)은 휠 방향이 실제 이동 방향과 일치하므로 이러한 진동을 크게 줄일 수 있다.

옴니 휠(Omni Wheel)과 메카넘 휠(Mecanum Wheel)은 특유의 진동 특성을 가진다. 롤러(Roller) 구조가 반복적으로 지면과 접촉하기 때문에 휠 회전 중 주기적인 충격이 발생한다. 따라서 일반 휠에서는 나타나지 않는 독특한 진동 패턴이 생성된다.

프레임 자체도 진동 특성에 영향을 준다. 모든 구조물은 고유진동수와 모드 형상(Mode Shape)을 가진다. 모터, 감속기, 휠에서 발생한 진동 주파수가 프레임의 고유진동수와 일치하면 공진이 발생하며 진동 진폭이 크게 증가한다. 이는 피로 파손(Fatigue Failure)과 구조 손상의 원인이 될 수 있다.

페이로드 장비(Payload Equipment)도 진동 발생원이 될 수 있다. 로봇팔(Robot Arm), 리프터(Lifter), 컨베이어(Conveyor), 펌프(Pump), 냉각 팬(Cooling Fan), 검사 장비(Inspection Equipment)는 각각 독립적인 진동을 발생시킨다. 실제 산업 현장에서는 이러한 상부 장비의 진동이 차량 자체 진동보다 더 큰 경우도 많다.

주변 환경(Environment) 역시 영향을 준다. 경사로(Ramp), 문턱(Threshold), 불균일 적재(Uneven Loading), 외부 충격(External Impact)은 모두 차량 구조를 자극하는 외란(Disturbance)이 된다. 심지어 주변 생산 설비에서 발생한 진동이 바닥을 통해 로봇에 전달되기도 한다.

센서 시스템(Sensor System)은 진동에 특히 민감하다. 카메라(Camera)는 영상 흔들림(Image Blur)이 발생할 수 있고, LiDAR는 거리 측정 노이즈(Ranging Noise)가 증가할 수 있으며, IMU는 드리프트(Drift)가 증가하여 위치추정 정확도가 저하될 수 있다.

따라서 현대 AMR 설계에서는 진동을 단순한 기계 문제로 보지 않는다. 모터, 감속기, 휠, 프레임, 센서, 페이로드를 포함한 전체 시스템 관점(System-Level Perspective)에서 접근해야 한다. 주요 진동원을 식별하고 주파수 특성을 분석한 후 적절한 저감 전략(Mitigation Strategy)을 적용해야만 장기간 안정적인 운용이 가능하다.

---

### 5.2 수동 절연 마운트 설계(Passive Isolation Mount Design)

수동 절연 마운트(Passive Isolation Mount)는 산업용 AMR에서 가장 널리 사용되는 진동 저감 기술 중 하나이다. 능동 진동 제어(Active Vibration Control)가 센서, 액추에이터(Actuator), 실시간 제어 알고리즘을 필요로 하는 반면, 수동 절연 시스템은 스프링(Spring), 고무(Elastomer), 감쇠 재료(Damping Material), 탄성 구조(Compliant Structure)를 이용하여 진동 전달을 감소시킨다. 구조가 단순하고 신뢰성이 높으며 유지보수가 거의 필요하지 않기 때문에 산업용 AMR에서 매우 많이 사용된다.

수동 절연 마운트의 기본 목적은 진동원이 생성한 에너지가 민감한 부품으로 전달되는 것을 차단하는 것이다. 일반적인 AMR에서는 모터, 감속기, 휠, 펌프, 냉각 팬, 검사 장비가 진동원 역할을 하며, 카메라, LiDAR, IMU, 엣지 컴퓨터(Edge Computer), 배터리 시스템, 정밀 센서 등이 보호 대상이 된다.

수동 절연 시스템은 질량-스프링-댐퍼 모델(Mass-Spring-Damper Model)로 설명할 수 있다. 보호 대상 장비는 질량(Mass)으로 표현되며, 절연 마운트는 스프링 강성(Spring Stiffness)과 감쇠(Damping)를 제공한다. 외부 진동이 입력되면 절연 마운트는 기계적 필터(Mechanical Filter) 역할을 수행하여 전달되는 진동을 감소시킨다.

가장 중요한 설계 변수는 고유진동수(Natural Frequency)이다. 일반적으로 진동원의 주파수가 절연 시스템의 고유진동수보다 충분히 높을 때 효과적인 진동 절연이 가능하다. 이 경우 마운트는 진동을 증폭하지 않고 감쇠시킨다.

고유진동수는 지지 질량과 마운트 강성에 의해 결정된다. 부드러운 마운트는 더 낮은 고유진동수를 가지므로 고주파 진동 절연에 유리하다. 그러나 지나치게 부드러우면 장비가 과도하게 움직여 위치 오차(Position Error)와 구조 불안정성이 발생할 수 있다.

탄성체 마운트(Elastomer Mount)는 가장 일반적인 수동 절연 방식이다. 천연 고무(Natural Rubber), 실리콘 고무(Silicone Rubber), 네오프렌(Neoprene), 폴리우레탄(Polyurethane) 등이 사용된다. 이들은 스프링과 댐퍼 역할을 동시에 수행할 수 있다.

고무 마운트(Rubber Mount)는 모터 컨트롤러(Motor Controller), 엣지 컴퓨터, 배터리 팩, 센서 모듈 등에 널리 적용된다. 고주파 진동을 효과적으로 줄일 수 있지만 장기간 사용 시 재료 노화(Material Aging), 온도 변화, 크리프(Creep)를 고려해야 한다.

스프링 기반 절연 시스템(Spring Isolation System)은 더 낮은 고유진동수가 필요한 경우 사용된다. 코일 스프링(Coil Spring)은 우수한 절연 성능을 제공하지만 자체 감쇠 능력이 부족하기 때문에 추가적인 댐퍼가 필요하다.

와이어 로프 아이솔레이터(Wire Rope Isolator)는 산업 환경에서 널리 사용되는 특수 절연 장치이다. 스테인리스 와이어 로프(Stainless Steel Wire Rope)를 이용하여 탄성과 감쇠를 동시에 제공하며, 내구성이 매우 높고 온도 변화에도 강하다.

센서 절연(Sensor Isolation)은 AMR에서 매우 중요하다. 카메라는 안정적인 영상 품질을 유지해야 하며, LiDAR는 거리 측정 정확도를 유지해야 한다. 특히 IMU는 진동 노이즈에 매우 민감하기 때문에 적절한 절연 설계가 필수적이다.

검사 장비(Inspection Equipment)를 탑재한 모바일 검사 로봇(Mobile Inspection Robot)에서는 페이로드 절연(Payload Isolation)이 더욱 중요하다. 레이저 스캐너(Laser Scanner), 비전 검사 장비(Machine Vision System), 계측 장비(Metrology Equipment)는 매우 낮은 진동 환경을 요구한다. 따라서 별도의 절연 플랫폼(Isolation Platform)이 적용되는 경우가 많다.

마운트 위치(Mount Placement)도 중요한 설계 요소이다. 절연 마운트는 단순히 좋은 재료를 사용하는 것만으로 충분하지 않다. 지지 대상 장비의 무게중심 근처에 적절하게 배치되어야 하며, 그렇지 않으면 록킹 모드(Rocking Mode)와 회전 진동(Rotational Oscillation)이 발생할 수 있다.

현대 산업용 AMR에서는 유한요소해석(FEA)과 모달 해석(Modal Analysis)을 통해 절연 시스템을 설계한다. 구조 모드(Structural Mode), 고유진동수, 감쇠비(Damping Ratio), 진동 전달 경로(Transmission Path)를 분석하여 최적의 절연 구조를 선정한다.

특히 힐스로보틱스(Hills Robotics)가 개발하는 CAD2SCAN AMR, GPR 검사 로봇, Mobile Manipulator와 같은 고정밀 플랫폼에서는 수동 절연 마운트가 필수 요소이다. 카메라, LiDAR, IMU, GPU 컴퓨터, 검사 장비를 적절히 절연하지 않으면 위치 정확도와 검사 성능이 크게 저하될 수 있다.

결론적으로 수동 절연 마운트는 단순한 부가 장치가 아니라 차세대 산업용 AMR의 핵심 설계 요소이다. 적절한 절연 설계는 센서 정확도 향상, 장비 수명 연장, 유지보수 비용 절감, 검사 품질 향상, 전체 시스템 신뢰성 증대로 이어진다. 특히 500kg, 1000kg, 1500kg급 중량 산업용 AMR에서는 초기 섀시 설계 단계부터 절연 구조를 통합적으로 고려하는 것이 매우 중요하다.
