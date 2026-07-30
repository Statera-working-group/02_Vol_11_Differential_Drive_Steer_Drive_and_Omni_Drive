**Differential Drive & Steer Drive Engineering**


# Chapter 10 Differential Drive Case Studies

##  

## 01 OMRON LD-250

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

The OMRON LD-250 is one of the most widely recognized Autonomous Mobile Robot (AMR) platforms used in industrial logistics, manufacturing automation, and warehouse material transportation. Developed as part of OMRON\'s intelligent mobile robotics portfolio, the LD-250 combines mature navigation technology, proven safety systems, and reliable fleet management software into a commercially successful mobile platform capable of transporting payloads up to 250 kg. Rather than focusing on experimental technologies, the LD-250 emphasizes industrial reliability, continuous operation, ease of deployment, and seamless integration with factory automation systems.

The platform has become a benchmark for evaluating indoor logistics robots because it demonstrates how careful mechanical design, robust navigation, and industrial-grade software can produce a highly reliable commercial AMR. Many robotics developers study the LD-250 to understand practical engineering decisions that have been validated through thousands of installations worldwide. Although newer platforms now offer larger payload capacities and more powerful computing resources, the LD-250 remains an excellent reference architecture for medium-duty indoor mobile robots.

The design philosophy behind the LD-250 prioritizes operational simplicity and long-term reliability. Every subsystem, including the mechanical chassis, drive system, battery architecture, safety sensors, localization system, and fleet management interface, has been optimized to minimize maintenance while maximizing productivity. Rather than pursuing maximum speed or extreme payload capacity, the platform focuses on delivering predictable performance under continuous industrial operation.

The robot employs natural feature navigation based primarily on LiDAR localization, eliminating the need for magnetic tape or floor-mounted guidance infrastructure. This significantly reduces installation cost while allowing flexible route modification through software. Fleet management software coordinates multiple robots, optimizes traffic flow, prevents congestion, and enables automatic task allocation within manufacturing facilities.

From an engineering perspective, the LD-250 demonstrates how balanced system integration often produces better commercial success than maximizing individual subsystem performance. Mechanical simplicity, reliable electrical architecture, proven safety certification, and robust software integration together create a platform capable of operating continuously with minimal human intervention.

Understanding the architecture of the OMRON LD-250 provides valuable insight into industrial AMR design principles that remain applicable to many modern mobile robot platforms, including those developed for logistics, manufacturing, inspection, and factory automation.

---

### 1.1 Platform Overview and Selection Rationale

The OMRON LD-250 was developed to address one of the most common industrial automation challenges: reliable transportation of medium-weight materials between production stations without requiring fixed conveyor systems or manual material handling. By automating repetitive transportation tasks, the platform improves manufacturing flexibility while reducing labor requirements and operational costs.

The robot is designed around a payload capacity of approximately 250 kg, positioning it between lightweight logistics robots and heavy-duty industrial transport vehicles. This payload range is particularly well suited for transporting totes, pallets, component carts, electronic assemblies, packaging materials, and work-in-process inventory throughout manufacturing facilities.

One of the primary reasons for selecting the LD-250 is its mature navigation technology. Unlike Automated Guided Vehicles (AGVs) that require magnetic tape, embedded wires, or reflective markers, the LD-250 utilizes simultaneous localization based on natural environmental features detected by onboard LiDAR sensors. This infrastructure-free navigation dramatically reduces installation complexity and allows rapid modification of transportation routes as factory layouts evolve.

Another important advantage is its integrated fleet management capability. Multiple robots can operate simultaneously while sharing navigation maps and dynamically coordinating their movements. Traffic management algorithms reduce congestion, prevent deadlocks, and optimize task scheduling, allowing efficient utilization of large robot fleets within complex manufacturing environments.

Industrial safety represents another significant selection criterion. The platform incorporates certified laser safety scanners, emergency stop systems, obstacle detection algorithms, and speed reduction strategies that enable safe human-robot collaboration without requiring complete physical separation. Compliance with international industrial safety standards facilitates deployment in mixed human-robot workplaces.

The LD-250 also offers straightforward integration with Manufacturing Execution Systems (MES), Warehouse Management Systems (WMS), Enterprise Resource Planning (ERP), and programmable logic controllers (PLCs). Standard communication interfaces allow the robot to become part of larger factory automation architectures rather than functioning as an isolated transport device.

Maintenance considerations further contribute to platform selection. Modular mechanical assemblies, standardized electrical components, diagnostic software, and remote monitoring capabilities simplify servicing while reducing downtime. Battery replacement, wheel maintenance, and software updates can be performed efficiently without extensive disassembly.

From a business perspective, the LD-250 provides an attractive balance between payload capability, deployment flexibility, operational reliability, and lifecycle cost. Rather than maximizing individual specifications, the platform demonstrates how carefully optimized engineering decisions can create a commercially successful industrial AMR suitable for a wide range of manufacturing applications.

---

### 1.2 Mechanical Design Key Points

The mechanical design of the OMRON LD-250 reflects a strong emphasis on structural simplicity, stability, maintainability, and continuous industrial operation. Every aspect of the chassis architecture has been optimized to provide reliable performance under demanding factory conditions while minimizing maintenance requirements.

The robot utilizes a compact, low-profile chassis that maintains a low center of gravity. This configuration improves stability during acceleration, deceleration, and turning while allowing the platform to operate safely beneath industrial workstations and transport carts. Low vehicle height also improves visibility for nearby personnel and facilitates integration into existing manufacturing layouts.

A differential drive configuration forms the basis of vehicle propulsion. Two independently controlled drive wheels generate both forward motion and steering through differential wheel speed control. Passive caster wheels provide additional support while maintaining mechanical simplicity. This architecture reduces the number of moving components compared with steering-drive systems, improving reliability and lowering maintenance costs.

The chassis structure typically consists of welded steel or high-strength structural components designed to withstand continuous industrial loading. Finite Element Analysis (FEA) is commonly applied during development to ensure adequate stiffness while minimizing overall vehicle weight. High structural rigidity reduces vibration and improves navigation accuracy by maintaining consistent sensor alignment.

Wheel selection represents another important design consideration. Industrial-grade polyurethane-coated wheels provide an effective compromise between traction, durability, floor protection, and noise reduction. Wheel diameter is selected to balance obstacle-climbing capability with overall vehicle stability.

Battery placement significantly influences vehicle dynamics. The battery pack is positioned near the geometric center of the chassis and close to the floor, minimizing center-of-gravity movement as payload changes. This arrangement improves turning stability and reduces dynamic load transfer during acceleration and braking.

Internal mechanical layout prioritizes accessibility. Major service components including batteries, motor drivers, communication modules, cooling systems, and safety electronics are arranged to facilitate rapid maintenance and replacement. Modular design minimizes service time while reducing operational downtime.

Protective covers shield sensitive components from dust, debris, accidental impacts, and routine industrial contamination. Mechanical design also considers cable routing, connector protection, vibration isolation, and airflow for thermal management.

Overall, the mechanical architecture demonstrates that successful industrial robot design depends not on mechanical complexity but on careful optimization of structural efficiency, component accessibility, durability, and manufacturability.

---

### 1.3 Performance KPIs and Results

Performance evaluation of the OMRON LD-250 extends far beyond maximum speed or payload capacity. Industrial AMRs are typically assessed using Key Performance Indicators (KPIs) that reflect productivity, reliability, operational efficiency, safety, and lifecycle cost under real manufacturing conditions.

Payload capacity is one of the most obvious KPIs. The LD-250 is designed to transport loads up to approximately 250 kg while maintaining stable navigation performance. This payload capability supports a broad range of industrial material handling applications without requiring oversized vehicle structures.

Navigation accuracy represents another critical performance indicator. Using LiDAR-based localization and natural feature navigation, the robot achieves highly repeatable positioning suitable for docking with workstations, conveyors, charging stations, and material transfer points. Consistent positioning accuracy enables reliable automated workflow integration.

Availability is particularly important in industrial production environments. High system uptime minimizes production interruptions and improves return on investment. Reliable electrical architecture, robust mechanical components, and mature software contribute to excellent long-term operational availability across continuous multi-shift operation.

Fleet productivity provides another valuable KPI. Rather than evaluating a single robot, industrial users often measure the throughput of multiple coordinated robots operating simultaneously. Efficient traffic management, dynamic task allocation, and automatic charging scheduling significantly improve overall fleet utilization.

Safety performance is evaluated through obstacle detection reliability, emergency stopping capability, human interaction safety, and compliance with international safety standards. Consistent safe operation is essential for mixed human-robot manufacturing environments.

Energy efficiency has become increasingly important as operating costs receive greater attention. Efficient motor control, regenerative braking, optimized motion planning, and intelligent charging management reduce overall energy consumption while extending battery operating time.

Maintenance performance is commonly measured using Mean Time Between Failures (MTBF), Mean Time To Repair (MTTR), and scheduled maintenance intervals. Modular design and remote diagnostics reduce maintenance effort while increasing operational availability.

Scalability represents another practical KPI. The LD-250 platform supports gradual fleet expansion without requiring fundamental infrastructure modifications. Additional robots can be integrated into existing fleet management systems with minimal disruption.

Overall deployment experience demonstrates that the LD-250 achieves commercial success not because it maximizes individual performance metrics, but because it provides consistently balanced performance across navigation accuracy, reliability, safety, maintainability, fleet coordination, and operational efficiency. These characteristics have established the platform as one of the most influential reference designs in the evolution of industrial autonomous mobile robots.

OMRON LD-250는 산업 물류(Industrial Logistics), 제조 자동화(Manufacturing Automation), 창고 내 자재 운반(Material Transportation) 분야에서 가장 널리 알려진 자율주행 모바일 로봇(Autonomous Mobile Robot, AMR) 플랫폼 중 하나이다. OMRON의 지능형 모바일 로봇(Intelligent Mobile Robotics) 제품군으로 개발된 LD-250은 최대 약 250kg의 적재 하중(Payload)을 운반할 수 있으며, 성숙한 내비게이션 기술(Navigation Technology), 검증된 안전 시스템(Safety System), 신뢰성 높은 플릿 관리 소프트웨어(Fleet Management Software)를 결합하여 상업적으로 성공한 플랫폼이다. 이 플랫폼은 새로운 기술을 실험적으로 적용하기보다는 산업 현장에서 요구되는 신뢰성(Reliability), 연속 운전(Continuous Operation), 구축 용이성(Ease of Deployment), 그리고 공장 자동화 시스템과의 통합성을 최우선으로 고려하여 설계되었다.

LD-250는 기계 설계(Mechanical Design), 자율주행(Local Navigation), 산업용 소프트웨어(Industrial Software)를 균형 있게 통합한 대표적인 사례로 평가받고 있다. 전 세계 수많은 공장에 설치되어 실제 생산 현장에서 검증되었기 때문에, 많은 로봇 개발자들이 산업용 AMR 설계 원칙을 학습하기 위한 기준 플랫폼(Reference Platform)으로 활용하고 있다. 최근에는 더 높은 적재 하중과 강력한 컴퓨팅 성능을 갖춘 플랫폼이 등장하고 있지만, LD-250는 중형 실내 물류 로봇(Medium-Duty Indoor Mobile Robot)의 대표적인 설계 기준으로 여전히 높은 가치를 가진다.

LD-250의 설계 철학은 단순하면서도 신뢰성 높은 시스템을 구축하는 데 있다. 기계 구조(Mechanical Chassis), 구동 시스템(Drive System), 배터리 시스템(Battery Architecture), 안전 센서(Safety Sensor), 위치 추정(Localization), 플릿 관리 인터페이스(Fleet Management Interface) 등 모든 요소는 유지보수를 최소화하면서 생산성을 극대화하도록 최적화되어 있다. 최고 속도나 최대 적재 하중보다 지속적인 산업 현장 운용에서 예측 가능한 성능을 제공하는 것이 목표이다.

이 플랫폼은 LiDAR 기반 자연 특징 내비게이션(Natural Feature Navigation)을 사용하여 자기 테이프(Magnetic Tape)나 바닥 가이드(Floor Guide) 없이 자율주행을 수행한다. 이를 통해 설치 비용을 줄이고, 공장 레이아웃 변경 시에도 소프트웨어 수정만으로 경로를 쉽게 변경할 수 있다. 또한 플릿 관리 소프트웨어는 여러 대의 로봇을 동시에 제어하여 교통 흐름(Traffic Flow)을 최적화하고 충돌을 방지하며 작업을 효율적으로 분배한다.

공학적인 관점에서 LD-250는 특정 부품의 성능을 극대화하기보다는 기계 구조, 전기 시스템, 안전 인증, 소프트웨어 통합을 균형 있게 최적화하여 높은 상업적 성공을 달성한 사례이다. 이러한 설계 철학은 물류, 제조, 검사, 공장 자동화 등 다양한 산업용 AMR 개발에서도 여전히 중요한 참고 기준이 되고 있다.

---

### 1.1 플랫폼 개요 및 선정 이유(Platform Overview and Selection Rationale)

OMRON LD-250는 공장 내에서 중량 자재를 자동으로 운반하기 위해 개발된 산업용 AMR이다. 기존 컨베이어(Conveyor)나 작업자의 수작업(Material Handling)에 의존하지 않고 생산 공정 간 자재를 자동으로 이동시켜 생산 유연성(Flexibility)을 높이고 인건비를 절감하는 것이 주요 목적이다.

최대 약 250kg의 적재 능력은 소형 물류 로봇과 대형 운반 차량 사이의 중간 영역을 담당한다. 부품 박스(Tote), 전자 부품(Electronic Assembly), 공정 중 재고(Work-in-Process), 포장 자재(Packaging Material), 소형 카트(Component Cart) 등을 운반하기에 적합하다.

LD-250가 높은 평가를 받는 가장 큰 이유는 성숙한 자율주행 기술이다. 기존의 AGV(Automated Guided Vehicle)는 자기 테이프나 매설 와이어(Embedded Wire), 반사 마커(Reflective Marker)와 같은 별도의 인프라가 필요했지만, LD-250는 LiDAR가 주변 환경의 자연 특징(Natural Feature)을 인식하여 위치를 추정한다. 따라서 별도의 바닥 공사가 필요 없으며, 생산 라인이 변경되어도 지도(Map)만 수정하면 새로운 경로를 쉽게 설정할 수 있다.

또 다른 중요한 장점은 플릿 관리(Fleet Management) 기능이다. 여러 대의 로봇이 하나의 지도를 공유하면서 동시에 운행할 수 있으며, 교통 관리 알고리즘(Traffic Management Algorithm)이 충돌과 병목 현상을 방지한다. 또한 작업(Task)을 자동으로 분배하여 전체 물류 효율을 향상시킨다.

산업 안전성(Safety)도 중요한 선정 이유이다. LD-250는 안전 레이저 스캐너(Safety Laser Scanner), 비상 정지(Emergency Stop), 장애물 감지(Obstacle Detection), 속도 제한(Speed Reduction) 기능을 제공하여 사람과 함께 작업하는 환경에서도 안전하게 운용될 수 있다. 또한 국제 산업 안전 규격을 만족하여 다양한 제조 현장에 쉽게 적용할 수 있다.

공장 자동화 시스템과의 연동성도 우수하다. 제조 실행 시스템(Manufacturing Execution System, MES), 창고 관리 시스템(Warehouse Management System, WMS), 전사적 자원 관리(Enterprise Resource Planning, ERP), PLC(Programmable Logic Controller)와 표준 통신 인터페이스(Standard Communication Interface)를 통해 쉽게 연결할 수 있다. 따라서 단순한 운반 로봇이 아니라 공장 자동화 시스템의 일부로 통합된다.

유지보수성(Maintainability)도 뛰어나다. 모듈형 기계 구조(Modular Mechanical Assembly), 표준 전기 부품(Standard Electrical Component), 진단 소프트웨어(Diagnostic Software), 원격 모니터링(Remote Monitoring)을 통해 유지보수를 쉽게 수행할 수 있다. 배터리 교체, 바퀴 교환, 소프트웨어 업데이트도 빠르게 진행할 수 있어 시스템 가동 중단 시간을 최소화한다.

비즈니스 측면에서도 LD-250는 적재 능력, 구축 용이성, 신뢰성, 운영 비용 사이에서 매우 우수한 균형을 제공한다. 특정 사양을 극대화하기보다 실제 산업 환경에서 가장 중요한 요소들을 최적화하여 성공적인 산업용 AMR 플랫폼으로 자리 잡았다.

---

### 1.2 기계 설계 핵심 요소(Mechanical Design Key Points)

OMRON LD-250의 기계 설계(Mechanical Design)는 구조적 단순성(Structural Simplicity), 안정성(Stability), 유지보수성(Maintainability), 산업 현장의 연속 운전을 목표로 설계되었다.

차체(Chassis)는 낮은 높이(Low Profile)와 낮은 무게 중심(Low Center of Gravity)을 갖도록 설계되어 있다. 이러한 구조는 가속, 감속, 회전 시 안정성을 높이며 작업대나 카트 아래를 통과하기 쉽도록 한다. 또한 차량 높이가 낮아 작업자의 시야를 방해하지 않고 기존 생산 설비와의 통합도 용이하다.

구동 방식은 차동 구동(Differential Drive)을 사용한다. 좌우 두 개의 구동 바퀴(Drive Wheel)가 각각 독립적으로 제어되며, 속도 차이를 이용하여 조향(Steering)을 수행한다. 보조 캐스터 휠(Passive Caster Wheel)은 차량을 지지하면서 구조를 단순하게 유지한다. 스티어 드라이브(Steer Drive)에 비해 움직이는 부품 수가 적어 신뢰성이 높고 유지보수가 간단하다.

차체 구조는 일반적으로 용접 강판(Welded Steel Structure)이나 고강도 구조재(High-Strength Structural Material)를 사용한다. 설계 단계에서는 유한요소해석(Finite Element Analysis, FEA)을 적용하여 충분한 강성을 확보하면서도 차량 무게를 최소화한다. 높은 강성은 진동을 줄이고 센서 위치를 안정적으로 유지하여 자율주행 정확도를 높인다.

바퀴(Wheel)는 내구성과 바닥 보호를 모두 고려하여 산업용 폴리우레탄(Polyurethane) 재질을 사용하는 경우가 많다. 바퀴 직경은 장애물 통과 성능과 차량 안정성을 함께 고려하여 결정된다.

배터리(Battery)는 차체 중심부의 낮은 위치에 배치된다. 이를 통해 적재 하중이 변화하더라도 무게 중심 이동을 최소화하고 회전 및 제동 안정성을 향상시킨다.

내부 부품 배치도 유지보수를 고려하여 설계되었다. 배터리, 모터 드라이버(Motor Driver), 통신 장치, 냉각 장치, 안전 제어기 등을 쉽게 접근할 수 있도록 배치하여 교체와 점검 시간을 줄인다.

외부 커버(Protective Cover)는 먼지, 이물질, 충격으로부터 내부 장치를 보호하며, 케이블 배선(Cable Routing), 커넥터 보호(Connector Protection), 진동 절연(Vibration Isolation), 공기 흐름(Airflow)도 함께 고려하여 설계되어 있다.

LD-250의 기계 구조는 복잡한 메커니즘보다 구조 효율성(Structural Efficiency), 유지보수성, 내구성(Durability), 생산성(Manufacturability)을 최적화하는 것이 산업용 AMR 설계의 핵심이라는 점을 잘 보여준다.

---

### 1.3 성능 KPI 및 운용 결과(Performance KPIs and Results)

OMRON LD-250의 성능 평가는 단순히 최고 속도(Maximum Speed)나 적재 하중(Payload Capacity)만으로 이루어지지 않는다. 산업용 AMR은 생산성(Productivity), 신뢰성(Reliability), 운영 효율(Operation Efficiency), 안전성(Safety), 유지보수성(Maintainability) 등을 종합적으로 평가하는 핵심 성과 지표(Key Performance Indicator, KPI)를 기준으로 평가된다.

적재 능력은 가장 기본적인 KPI이다. LD-250는 약 250kg의 화물을 안정적으로 운반할 수 있으며, 다양한 제조 및 물류 환경에서 충분한 운반 성능을 제공한다.

자율주행 정확도(Navigation Accuracy)는 또 다른 중요한 KPI이다. LiDAR 기반 자연 특징 위치 추정(Localization)을 이용하여 작업대(Workstation), 컨베이어, 자동 충전기(Auto Charging Station), 자재 이송 지점(Material Transfer Point)에 높은 반복 정밀도(Repeatability)로 도킹(Docking)할 수 있다.

가동률(Availability)은 산업 현장에서 매우 중요한 지표이다. 높은 시스템 가동률은 생산 중단을 줄이고 투자 대비 수익(Return on Investment)을 높인다. LD-250는 검증된 기계 구조, 안정적인 전기 시스템, 성숙한 소프트웨어를 기반으로 장기간 다교대(Multi-Shift) 운전에서도 높은 가동률을 유지한다.

플릿 생산성(Fleet Productivity)도 중요한 평가 요소이다. 단일 로봇이 아니라 여러 대의 로봇이 동시에 작업할 때 전체 처리량(Throughput)이 얼마나 향상되는지를 평가한다. 교통 제어(Traffic Management), 작업 분배(Task Allocation), 자동 충전 스케줄(Auto Charging Schedule)을 통해 플릿 전체의 생산성을 극대화한다.

안전 성능(Safety Performance)은 장애물 감지 신뢰성(Obstacle Detection Reliability), 비상 정지(Emergency Stop), 사람과의 협업(Human-Robot Collaboration), 국제 안전 규격 준수 여부를 포함한다. 산업 현장에서는 사람과 로봇이 함께 작업하기 때문에 이러한 안전 성능이 매우 중요하다.

에너지 효율(Energy Efficiency)도 최근 중요한 KPI가 되었다. 고효율 모터 제어(Efficient Motor Control), 회생 제동(Regenerative Braking), 최적 경로 계획(Optimized Motion Planning), 지능형 충전 관리(Intelligent Charging Management)를 통해 에너지 소비를 줄이고 운행 시간을 늘릴 수 있다.

유지보수 성능(Maintenance Performance)은 평균 고장 간격(Mean Time Between Failures, MTBF), 평균 수리 시간(Mean Time To Repair, MTTR), 정기 유지보수 주기(Maintenance Interval) 등을 기준으로 평가된다. LD-250는 모듈형 설계와 원격 진단 기능을 통해 유지보수 시간을 크게 단축하였다.

확장성(Scalability)도 중요한 성능 지표이다. LD-250는 기존 플릿 관리 시스템에 새로운 로봇을 쉽게 추가할 수 있어 공장 규모가 커져도 시스템을 효율적으로 확장할 수 있다.

종합적으로 LD-250는 특정 성능 하나를 극대화한 플랫폼이 아니라 자율주행 정확도, 신뢰성, 안전성, 유지보수성, 플릿 관리, 운영 효율을 균형 있게 최적화한 산업용 AMR이다. 이러한 균형 잡힌 설계 철학이 LD-250를 산업용 자율주행 로봇 분야의 대표적인 기준 플랫폼으로 자리 잡게 한 가장 큰 이유라고 할 수 있다.

##  

## 02 MiR250

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

The MiR250 represents one of the most successful examples of modern Autonomous Mobile Robot (AMR) development for collaborative industrial logistics. Developed by Mobile Industrial Robots (MiR), the platform was designed to automate repetitive material transportation tasks while operating safely alongside human workers. Unlike traditional Automated Guided Vehicles (AGVs), which depend on fixed guidance infrastructure such as magnetic tape or embedded wires, the MiR250 employs advanced Natural Feature SLAM (Simultaneous Localization and Mapping) technology to navigate dynamically changing industrial environments. This infrastructure-free navigation capability significantly reduces deployment cost while providing exceptional flexibility for manufacturing facilities, warehouses, laboratories, and hospitals.

The MiR250 occupies an important position within the medium-payload AMR market. With a payload capacity of approximately 250 kg, compact dimensions, and high maneuverability, it is capable of transporting components, containers, pallets, and work-in-process materials between production stations without interrupting normal factory operations. The platform emphasizes rapid deployment, ease of integration, and collaborative operation rather than maximum payload or vehicle speed.

One of the defining characteristics of the MiR250 is its modular architecture. The mobile base functions as a standardized transportation platform capable of supporting a wide variety of upper modules, including conveyor systems, collaborative robot arms, pallet lifts, shelving systems, inspection stations, and custom automation equipment. This flexibility allows a single mobile platform to perform multiple industrial functions while minimizing development cost.

The platform integrates multiple perception sensors including LiDAR, safety laser scanners, wheel encoders, inertial sensors, and onboard computing resources to continuously estimate its position while detecting dynamic obstacles. Advanced navigation software generates collision-free paths that adapt in real time to people, forklifts, carts, and other moving objects within the environment. Fleet management software further coordinates multiple robots, optimizing traffic flow and task allocation across large manufacturing facilities.

Another major strength of the MiR250 lies in its software ecosystem. Open interfaces enable communication with Manufacturing Execution Systems (MES), Warehouse Management Systems (WMS), Enterprise Resource Planning (ERP), programmable logic controllers (PLCs), and cloud-based monitoring platforms. This connectivity allows the robot to participate as an intelligent component within Industry 4.0 manufacturing environments.

From an engineering perspective, the MiR250 demonstrates how modern AMRs combine mechanical simplicity, advanced perception algorithms, intelligent software, and standardized interfaces to create flexible industrial automation platforms. Its success has established important design principles that continue to influence the development of collaborative mobile robots throughout the robotics industry.

---

### 2.1 Collaborative Robot Integration Case

One of the most significant applications of the MiR250 is its integration with collaborative robots (Cobots) to create mobile manipulation systems capable of performing both transportation and manipulation tasks. This integration represents a major evolution in industrial automation because it combines autonomous mobility with flexible robotic manipulation, enabling a single system to perform multiple operations without requiring fixed automation infrastructure.

Traditional industrial robots are permanently installed at fixed workstations. Although they provide excellent positioning accuracy and repeatability, their workspace is limited to the reach of the manipulator. Whenever production layouts change or additional workstations must be served, expensive reinstallation is often required.

By mounting a collaborative robot onto the MiR250 platform, the robot gains mobility while maintaining manipulation capability. Instead of waiting for materials to arrive, the robot itself travels autonomously between workstations, performs manipulation tasks, and proceeds to the next assignment. This significantly increases equipment utilization and manufacturing flexibility.

A typical mobile manipulation system consists of the MiR250 mobile base, a six-axis collaborative robot arm, an end effector, onboard computing hardware, safety controllers, power management modules, and communication interfaces. The mobile platform provides transportation and localization, while the collaborative robot performs tasks such as machine tending, pick-and-place operations, assembly assistance, inspection, barcode scanning, quality verification, packaging, or laboratory sample handling.

Mechanical integration requires careful consideration of payload distribution and structural rigidity. The collaborative robot introduces additional mass above the vehicle chassis, raising the center of gravity. Engineers must therefore optimize manipulator placement, battery location, and chassis stiffness to maintain vehicle stability during acceleration, deceleration, and turning.

Dynamic interaction between the manipulator and mobile platform also becomes an important design consideration. Rapid arm movements generate reaction forces that influence vehicle stability and localization accuracy. Motion planning algorithms frequently coordinate manipulator motion with vehicle motion to minimize dynamic disturbances.

Localization accuracy is particularly critical during manipulation tasks. Although the mobile base may navigate with centimeter-level accuracy, many manipulation operations require millimeter-level positioning. Vision systems, fiducial markers, force sensors, laser alignment devices, or local coordinate calibration methods are commonly employed to compensate for residual positioning errors after docking.

Power management becomes increasingly important because the collaborative robot significantly increases overall energy consumption. Battery sizing must consider propulsion power, manipulator operation, onboard computing, sensors, and auxiliary equipment simultaneously. Intelligent energy management software monitors battery state and schedules automatic charging without interrupting production.

Safety architecture becomes considerably more sophisticated in mobile manipulation systems. The mobile base and collaborative robot each possess independent safety systems that must operate cooperatively. Emergency stop functions, protective speed monitoring, safety-rated monitored stop, collision detection, workspace monitoring, and human presence detection are integrated into a unified safety framework compliant with industrial safety standards.

Software integration represents another key engineering challenge. The mobile robot navigation system, manipulator controller, machine interfaces, production scheduling software, and fleet management system must exchange information continuously. Standard industrial communication protocols such as OPC UA, Ethernet/IP, Modbus TCP, REST APIs, and ROS interfaces simplify interoperability among these subsystems.

Numerous industrial applications demonstrate the effectiveness of this architecture. Mobile manipulators transport raw materials to CNC machines, load and unload workpieces automatically, perform visual inspections using onboard cameras, collect finished products, and deliver them to storage or packaging stations. In electronics manufacturing, collaborative mobile robots assemble components, transport printed circuit boards, and perform automated testing. Pharmaceutical laboratories employ mobile manipulators for sample transportation and automated laboratory procedures while minimizing human exposure to hazardous materials.

The integration of collaborative robots with the MiR250 demonstrates how mobility dramatically extends the usefulness of robotic manipulation. Instead of automating isolated workstations, manufacturers can deploy flexible robotic systems capable of adapting to changing production requirements. This approach reduces capital investment, improves equipment utilization, shortens deployment time, and supports increasingly flexible manufacturing strategies associated with Industry 4.0.

---

### 2.2 Natural Feature SLAM Application

Natural Feature SLAM is one of the defining technologies that distinguishes modern Autonomous Mobile Robots from traditional Automated Guided Vehicles. Rather than following predefined physical guidance infrastructure, the MiR250 continuously constructs and updates an internal map of its surroundings using naturally occurring environmental features. This capability enables flexible navigation within complex industrial environments where layouts frequently change.

SLAM, or Simultaneous Localization and Mapping, solves two interconnected problems simultaneously. The robot must determine its own position while simultaneously constructing a map of an unknown environment. Because accurate localization depends on the map and accurate mapping depends on localization, sophisticated probabilistic estimation algorithms continuously solve both problems together.

The MiR250 primarily relies on high-resolution LiDAR sensors for localization. During an initial mapping procedure, the robot scans walls, machinery, pillars, storage racks, doorways, and other permanent structural features throughout the facility. These features become stable landmarks within the robot\'s environmental map.

Unlike vision-based localization, LiDAR is relatively insensitive to lighting variations. Industrial facilities often experience changing illumination, shadows, reflections, and varying operating schedules. Laser-based sensing provides robust geometric information independent of ambient lighting conditions, making it particularly well suited for manufacturing environments.

During normal operation, each incoming LiDAR scan is compared with the stored environmental map. Advanced scan-matching algorithms estimate the robot\'s position by minimizing differences between measured and predicted environmental geometry. Wheel encoder information and inertial measurements provide additional motion estimates that improve localization robustness during rapid movement or temporary sensor occlusion.

Probabilistic filters such as particle filters or graph optimization algorithms continuously combine sensor observations while accounting for measurement uncertainty. This probabilistic framework allows accurate localization even when portions of the environment become temporarily obstructed by people, pallets, forklifts, or moving equipment.

Natural Feature SLAM offers significant advantages over infrastructure-dependent navigation systems. Route modifications require only software updates rather than physical changes to factory floors. Production lines can be rearranged rapidly without reinstalling magnetic tape or guide wires. Temporary obstacles can be bypassed automatically while maintaining accurate localization.

Dynamic obstacle handling is another important capability. While permanent structural features contribute to localization, moving objects are identified and excluded from map matching. Separate obstacle detection algorithms generate collision-free trajectories that safely avoid pedestrians and industrial vehicles without corrupting the underlying map.

Map maintenance represents an ongoing engineering consideration. Although most structural features remain stable, industrial facilities gradually evolve over time. New machinery, storage racks, walls, or workstations may alter the environment sufficiently to require partial map updates. Modern mapping software supports efficient map modification without requiring complete remapping of the facility.

Localization performance depends heavily on environmental characteristics. Facilities containing distinctive geometric features generally provide excellent localization accuracy. Conversely, long empty corridors, highly repetitive storage aisles, or large featureless spaces may reduce localization robustness. Additional artificial landmarks or complementary sensing technologies may be introduced where necessary.

The MiR250 frequently combines LiDAR localization with other sensing modalities including wheel odometry, inertial measurement units, safety laser scanners, and optional vision systems. Sensor fusion improves robustness under challenging operating conditions while reducing sensitivity to individual sensor failures.

Natural Feature SLAM has fundamentally transformed industrial mobile robotics by eliminating the infrastructure constraints associated with traditional AGVs. The technology enables rapid deployment, flexible factory reconfiguration, scalable fleet expansion, and reduced installation cost while maintaining reliable autonomous navigation. As industrial environments continue to demand greater flexibility and adaptability, Natural Feature SLAM remains one of the most important enabling technologies for next-generation collaborative mobile robotics.

MiR250는 현대 산업용 협업 물류(Collaborative Industrial Logistics)를 대표하는 가장 성공적인 자율주행 모바일 로봇(Autonomous Mobile Robot, AMR) 플랫폼 가운데 하나이다. Mobile Industrial Robots(MiR)가 개발한 이 플랫폼은 작업자와 동일한 작업 공간에서 안전하게 운용되면서 반복적인 자재 운반(Material Transportation)을 자동화하기 위해 설계되었다. 자기 테이프(Magnetic Tape)나 매설 와이어(Embedded Wire)와 같은 고정된 안내 인프라에 의존하는 기존 AGV(Automated Guided Vehicle)와 달리, MiR250은 자연 특징 SLAM(Natural Feature SLAM, Simultaneous Localization and Mapping)을 이용하여 끊임없이 변화하는 산업 환경에서도 자율적으로 이동한다. 이러한 인프라가 필요 없는(Infrastructure-Free) 자율주행 방식은 구축 비용을 크게 절감하며 제조 공장, 물류 창고, 연구소, 병원 등 다양한 환경에서 높은 유연성을 제공한다.

MiR250는 중형 적재 하중(Medium Payload) 시장에서 중요한 위치를 차지하고 있다. 약 250kg의 적재 능력(Payload Capacity), 작은 차체(Compact Dimensions), 우수한 기동성(High Maneuverability)을 바탕으로 부품(Component), 컨테이너(Container), 팔레트(Pallet), 공정 중 재고(Work-in-Process)를 생산 공정 사이에서 안정적으로 운반할 수 있다. 이 플랫폼은 최고 속도나 최대 적재 능력을 추구하기보다는 빠른 구축(Rapid Deployment), 높은 통합성(Ease of Integration), 그리고 사람과 함께 작업하는 협업 환경(Collaborative Operation)에 중점을 두고 설계되었다.

MiR250의 가장 큰 특징 가운데 하나는 모듈형 아키텍처(Modular Architecture)이다. 이동 플랫폼(Mobile Base)은 표준 운반 플랫폼(Standard Transportation Platform) 역할을 수행하며, 상부에는 컨베이어(Conveyor), 협동로봇(Collaborative Robot), 팔레트 리프트(Pallet Lift), 선반(Shelving System), 검사 장비(Inspection Station), 맞춤형 자동화 장치(Custom Automation Equipment) 등을 자유롭게 장착할 수 있다. 따라서 하나의 플랫폼으로 다양한 산업 자동화 작업을 수행할 수 있으며 개발 비용과 유지보수 비용을 절감할 수 있다.

MiR250는 LiDAR, 안전 레이저 스캐너(Safety Laser Scanner), 휠 엔코더(Wheel Encoder), 관성 측정 장치(Inertial Measurement Unit, IMU), 산업용 컴퓨터(Onboard Computing)를 통합하여 자신의 위치를 지속적으로 추정한다. 동시에 사람, 지게차(Forklift), 운반 카트(Cart)와 같은 이동 장애물을 실시간으로 인식하고 충돌을 피하는 경로를 생성한다. 플릿 관리 시스템(Fleet Management System)은 여러 대의 로봇을 동시에 제어하며 교통 흐름(Traffic Flow)과 작업 할당(Task Allocation)을 최적화한다.

또한 MiR250는 개방형 소프트웨어(Open Software Ecosystem)를 제공하여 제조 실행 시스템(Manufacturing Execution System, MES), 창고 관리 시스템(Warehouse Management System, WMS), 전사적 자원 관리(Enterprise Resource Planning, ERP), PLC(Programmable Logic Controller), 클라우드 기반 모니터링 시스템(Cloud Monitoring Platform)과 쉽게 연동된다. 이러한 연결성은 MiR250를 단순한 운반 로봇이 아니라 스마트 팩토리(Smart Factory)를 구성하는 핵심 요소로 만들어 준다.

공학적인 관점에서 MiR250는 단순한 기계 구조, 고성능 인식 알고리즘(Perception Algorithm), 지능형 소프트웨어(Intelligent Software), 표준 인터페이스(Standard Interface)를 결합하여 매우 유연한 산업용 AMR 플랫폼을 구현한 대표적인 사례이다. 이러한 설계 철학은 오늘날 협업형 모바일 로봇(Collaborative Mobile Robot) 개발의 중요한 기준이 되고 있다.

---

### 2.1 협동로봇 통합 사례(Collaborative Robot Integration Case)

MiR250의 가장 대표적인 응용 분야는 협동로봇(Collaborative Robot, Cobot)과의 통합이다. 이를 통해 이동성과 조작 기능(Manipulation)을 동시에 갖춘 모바일 매니퓰레이터(Mobile Manipulator)를 구현할 수 있다. 이러한 시스템은 자율주행과 로봇 조작을 하나의 플랫폼에서 수행함으로써 기존의 고정형 자동화 설비보다 훨씬 높은 생산 유연성을 제공한다.

기존 산업용 로봇(Industrial Robot)은 고정된 작업 셀(Work Cell)에 설치되어 일정한 범위 안에서만 작업할 수 있다. 위치 반복 정밀도(Repeatability)는 매우 우수하지만 작업 공간이 제한되며 생산 라인이 변경될 경우 재설치 비용이 크게 발생한다.

반면 협동로봇을 MiR250 위에 탑재하면 이동성과 작업 능력을 동시에 확보할 수 있다. 로봇은 작업물을 기다리지 않고 스스로 작업 위치까지 이동하여 작업을 수행한 후 다음 공정으로 이동한다. 이를 통해 장비 활용률(Utilization)을 높이고 생산 공정의 유연성을 크게 향상시킬 수 있다.

일반적인 모바일 매니퓰레이터 시스템은 MiR250 플랫폼, 6축 협동로봇(Six-Axis Collaborative Robot), 엔드 이펙터(End Effector), 산업용 컴퓨터, 안전 제어기(Safety Controller), 전원 관리 시스템(Power Management System), 통신 인터페이스(Communication Interface)로 구성된다. 이동 플랫폼은 자율주행과 위치 추정을 담당하고 협동로봇은 기계 가공기(Machine Tool) 로딩 및 언로딩, Pick-and-Place 작업, 조립(Assembly), 검사(Inspection), 바코드 스캔(Barcode Scanning), 품질 검사(Quality Verification), 포장(Packaging), 실험실 시료 처리(Laboratory Sample Handling) 등을 수행한다.

기계적인 통합(Mechanical Integration)에서는 무게 중심(Center of Gravity) 관리가 매우 중요하다. 협동로봇이 상부에 설치되면 차량의 무게 중심이 높아지므로 배터리 위치(Battery Placement), 차체 강성(Structural Rigidity), 매니퓰레이터 위치를 최적화하여 가속과 회전 시 차량 안정성을 확보해야 한다.

협동로봇의 빠른 움직임은 차량에 반작용력(Reaction Force)을 발생시킨다. 따라서 매니퓰레이터와 이동 플랫폼의 움직임을 동시에 계획하는 협조 제어(Coordinated Motion Planning)가 필요하다. 이를 통해 차량 흔들림을 줄이고 위치 추정 정확도를 향상시킬 수 있다.

작업 정밀도도 중요한 요소이다. MiR250의 자율주행 정밀도는 센티미터 수준이지만, 많은 조작 작업은 밀리미터 수준의 정밀도를 요구한다. 따라서 도킹(Docking) 이후에는 비전 시스템(Vision System), 기준 마커(Fiducial Marker), 힘 센서(Force Sensor), 레이저 정렬(Laser Alignment), 좌표 보정(Local Coordinate Calibration) 등을 이용하여 추가적인 위치 보정을 수행한다.

전력 관리(Power Management)도 복잡해진다. 협동로봇은 추진 시스템 외에 상당한 전력을 소비하므로 배터리는 구동 모터, 협동로봇, 컴퓨터, 센서, 보조 장치를 모두 고려하여 설계해야 한다. 또한 에너지 관리 소프트웨어(Energy Management Software)는 배터리 상태를 지속적으로 감시하며 작업에 영향을 주지 않는 시점에 자동 충전을 수행한다.

안전 시스템(Safety Architecture)은 더욱 정교해진다. 이동 플랫폼과 협동로봇은 각각 독립적인 안전 시스템을 가지고 있으며, 이를 하나의 통합 안전 구조(Unified Safety Framework)로 구성해야 한다. 비상 정지(Emergency Stop), 안전 속도 감시(Protective Speed Monitoring), 안전 정지(Safety-Rated Monitored Stop), 충돌 감지(Collision Detection), 작업 공간 감시(Workspace Monitoring), 작업자 감지(Human Presence Detection) 등이 모두 통합되어야 한다.

소프트웨어 통합도 핵심 기술이다. 자율주행 시스템, 협동로봇 제어기, 생산 설비 인터페이스, 작업 스케줄러, 플릿 관리 시스템은 OPC UA, Ethernet/IP, Modbus TCP, REST API, ROS와 같은 산업용 통신 프로토콜을 이용하여 지속적으로 데이터를 교환한다.

실제 산업 현장에서는 이러한 모바일 매니퓰레이터가 CNC 공작기계에 원자재를 공급하고 완성품을 회수하며, 비전 검사를 수행하거나 자동 포장 작업을 수행하고 있다. 전자 산업에서는 PCB(Printed Circuit Board)를 운반하면서 조립과 검사까지 수행하고 있으며, 제약 산업에서는 위험 물질 노출을 최소화하면서 시료 운반과 실험실 자동화를 수행하고 있다.

MiR250와 협동로봇의 결합은 기존 고정형 자동화를 이동형 자동화(Mobile Automation)로 확장한 대표적인 사례이다. 이는 생산 설비의 활용률을 높이고 투자 비용을 절감하며, 산업용 제조 환경을 더욱 유연하게 만드는 중요한 기술로 평가받고 있다.

---

### 2.2 자연 특징 SLAM 적용(Natural Feature SLAM Application)

자연 특징 SLAM(Natural Feature SLAM)은 현대 AMR를 기존 AGV와 구별하는 가장 핵심적인 기술이다. MiR250는 별도의 바닥 인프라 없이 주변 환경의 자연적인 구조물을 이용하여 자신의 위치를 추정하고 동시에 환경 지도를 생성한다. 이러한 기술 덕분에 생산 라인이 자주 변경되는 공장에서도 매우 높은 유연성을 제공할 수 있다.

SLAM(Simultaneous Localization and Mapping)은 위치 추정(Localization)과 지도 작성(Mapping)을 동시에 수행하는 기술이다. 로봇은 자신의 위치를 알아야 지도를 만들 수 있지만, 반대로 지도가 있어야 자신의 위치를 정확히 계산할 수 있다. 이러한 두 문제를 동시에 해결하기 위해 확률 기반 알고리즘(Probabilistic Estimation Algorithm)이 지속적으로 계산을 수행한다.

MiR250는 주로 고해상도 LiDAR를 이용하여 위치를 추정한다. 초기 지도 작성 과정에서는 벽(Wall), 기둥(Column), 기계(Machinery), 랙(Storage Rack), 출입구(Doorway) 등 공장의 고정 구조물을 스캔하여 환경 지도를 생성한다. 이러한 구조물은 로봇이 항상 참조할 수 있는 랜드마크(Landmark)가 된다.

LiDAR 기반 위치 추정은 카메라 기반 방식보다 조명 변화(Lighting Variation)에 영향을 적게 받는다. 공장은 시간에 따라 조명이 바뀌고 그림자가 생기며 반사가 발생하기 때문에, 레이저 기반 측정은 이러한 환경에서도 안정적인 기하학적 정보를 제공한다.

운행 중에는 현재 LiDAR 스캔 데이터를 저장된 지도와 비교하는 스캔 매칭(Scan Matching)을 수행한다. 이를 통해 로봇은 자신의 위치를 지속적으로 계산한다. 휠 오도메트리(Wheel Odometry)와 IMU 데이터는 추가적인 이동 정보를 제공하여 빠른 움직임이나 일시적인 센서 가림 현상에서도 안정적인 위치 추정을 가능하게 한다.

입자 필터(Particle Filter), 그래프 최적화(Graph Optimization)와 같은 확률 기반 알고리즘은 여러 센서의 정보를 통합하면서 측정 오차를 함께 고려한다. 따라서 작업자, 지게차, 팔레트와 같이 일시적으로 주변 환경이 가려져도 높은 위치 추정 정확도를 유지할 수 있다.

자연 특징 SLAM의 가장 큰 장점은 별도의 인프라가 필요 없다는 점이다. 생산 라인이 변경되더라도 자기 테이프를 다시 설치할 필요가 없으며, 소프트웨어에서 경로만 수정하면 새로운 환경에 쉽게 대응할 수 있다. 또한 일시적인 장애물도 자동으로 우회하면서 자율주행을 계속 수행할 수 있다.

동적 장애물 처리(Dynamic Obstacle Handling)도 중요한 기능이다. 사람, 지게차, 운반 차량과 같은 이동 물체는 지도 작성에서 제외되며, 별도의 장애물 회피 알고리즘(Obstacle Avoidance Algorithm)이 실시간으로 새로운 경로를 생성한다. 따라서 원래 지도는 유지하면서도 안전하게 이동할 수 있다.

지도 관리(Map Maintenance)도 지속적으로 이루어진다. 공장의 구조는 시간이 지나면서 새로운 설비나 랙이 추가될 수 있기 때문에 일부 영역은 지도 업데이트(Map Update)가 필요하다. 최신 SLAM 소프트웨어는 전체 지도를 다시 만들지 않고 변경된 부분만 수정할 수 있다.

위치 추정 성능은 환경 특성(Environment Characteristics)에 따라 달라진다. 벽, 기둥, 설비와 같은 특징점이 풍부한 환경에서는 매우 높은 정확도를 제공하지만, 긴 복도나 반복적인 랙 구조처럼 특징이 부족한 환경에서는 정확도가 다소 감소할 수 있다. 이러한 경우에는 인공 랜드마크(Artificial Landmark)나 추가 센서를 함께 사용하는 경우도 있다.

MiR250는 LiDAR뿐 아니라 오도메트리(Odometry), IMU, 안전 레이저 스캐너, 필요에 따라 비전 센서(Vision Sensor)를 함께 사용하는 센서 융합(Sensor Fusion)을 적용한다. 이를 통해 센서 하나에 문제가 발생하더라도 안정적인 자율주행을 유지할 수 있다.

자연 특징 SLAM은 기존 AGV의 가장 큰 제약이었던 인프라 의존성을 제거함으로써 산업용 모바일 로봇의 발전을 크게 앞당겼다. 빠른 구축(Rapid Deployment), 공장 레이아웃 변경(Flexible Factory Reconfiguration), 플릿 확장(Scalable Fleet Expansion), 구축 비용 절감(Reduced Installation Cost)을 동시에 실현하면서도 높은 자율주행 성능을 유지할 수 있기 때문에, 오늘날 차세대 산업용 협업 모바일 로봇의 핵심 기술로 자리 잡고 있다.

##  

## 03 MiR600

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

The MiR600 represents a significant evolution in the design of industrial Autonomous Mobile Robots (AMRs), extending the payload capability of the MiR product family from light-duty logistics toward heavy industrial material handling. With a rated payload capacity of approximately 600 kg, the platform addresses applications involving pallet transportation, heavy component delivery, machine feeding, warehouse automation, and manufacturing logistics. Unlike smaller AMRs that primarily transport lightweight containers or work-in-process materials, the MiR600 must manage substantially larger inertial loads, increased traction requirements, higher structural stresses, and more demanding safety constraints while maintaining reliable autonomous navigation.

One of the most interesting engineering characteristics of the MiR600 is that it continues to employ a differential drive architecture despite operating in a payload range where many competing industrial vehicles begin transitioning toward steer-drive or omnidirectional steering systems. This design decision offers several advantages including mechanical simplicity, lower manufacturing cost, reduced maintenance requirements, proven control algorithms, and high drivetrain reliability. However, increasing payload introduces new engineering challenges associated with tire wear, turning resistance, floor loading, docking precision, and dynamic stability.

As vehicle mass increases, the physical limitations of differential drive become progressively more apparent. During zero-radius turns, differential drive requires one wheel to rotate faster than the other while the passive caster wheels continuously reorient themselves. Because the wheels cannot align with the instantaneous direction of travel, lateral slip inevitably occurs between the tire and floor surface. This phenomenon generates additional rolling resistance, increases power consumption, accelerates tire wear, and introduces small positioning errors.

The effects become increasingly significant as payload increases because the normal force acting on each tire rises proportionally with vehicle weight. Higher normal force increases frictional resistance during turning, requiring larger motor torque and generating greater mechanical stress throughout the drivetrain. At the same time, precise docking operations become more sensitive to wheel deformation, floor irregularities, and accumulated odometry errors.

Despite these challenges, the MiR600 demonstrates that differential drive remains technically viable within the 600 kg payload class when supported by appropriate mechanical design, high-quality localization, intelligent motion planning, and advanced fleet management software. Rather than relying solely on wheel odometry, the robot continuously corrects positioning errors using LiDAR-based localization and obstacle-aware path planning. Intelligent motion control also minimizes unnecessary aggressive turning, reducing mechanical stress and improving energy efficiency.

From a system engineering perspective, the MiR600 provides valuable insight into the practical performance limits of differential drive technology. It illustrates both the strengths and limitations of extending a mechanically simple drive architecture into increasingly demanding industrial applications. The platform therefore serves as an excellent case study for determining when differential drive remains economically advantageous and when steer-drive architectures become more appropriate.

---

### 3.1 600 kg Class Differential Drive Limitation Analysis

The differential drive mechanism has become the dominant propulsion architecture for indoor AMRs because of its mechanical simplicity, excellent reliability, compact packaging, and relatively low manufacturing cost. However, increasing vehicle payload fundamentally changes the mechanical behavior of the drivetrain. The MiR600 provides an excellent opportunity to analyze how differential drive performance evolves as payload approaches the 600 kg class.

A differential drive system consists of two independently controlled drive wheels positioned along a common axle and one or more passive caster wheels supporting the remaining vehicle weight. Vehicle steering is achieved entirely through differences in wheel rotational speed. Forward motion occurs when both drive wheels rotate at equal speed, while turning is generated by commanding different wheel velocities.

At low payloads, this mechanism performs exceptionally well. Tire deformation remains limited, rolling resistance is relatively low, and motors can easily generate the required steering torque. However, increasing payload produces several nonlinear effects that gradually reduce overall system performance.

The first limitation involves tire-ground interaction. During differential steering, the drive wheels experience lateral slip because their rolling direction cannot perfectly match the instantaneous vehicle trajectory. As payload increases, normal force acting on each tire also increases. Higher normal force generates larger frictional forces that resist lateral motion. Consequently, turning requires substantially greater motor torque than straight-line driving.

Caster wheel behavior introduces additional complexity. Passive caster wheels continuously rotate to align with changing travel direction. During rapid direction changes or zero-radius rotation, caster wheels momentarily resist reorientation, creating transient steering disturbances and additional energy loss. Larger payloads amplify these effects because greater vertical loading increases caster rolling resistance.

Energy consumption also rises significantly during turning. While straight-line driving primarily overcomes rolling resistance, differential steering must additionally overcome tire scrubbing and caster reorientation forces. Repeated turning therefore consumes disproportionately more energy than linear travel, reducing battery operating time in environments containing frequent directional changes.

Mechanical wear represents another important consideration. Continuous lateral tire slip accelerates tread wear compared with steer-drive systems where wheels remain aligned with vehicle motion. Bearings, gearboxes, and drivetrain components also experience higher cyclic loading due to repeated steering torque reversals. Preventive maintenance intervals may therefore become shorter as payload increases.

Localization accuracy is indirectly affected by these mechanical phenomena. Wheel odometry assumes pure rolling motion, but lateral slip violates this assumption. Small odometry errors accumulate over time, particularly during frequent turning. Fortunately, modern LiDAR localization continuously corrects accumulated drift, preventing long-term navigation degradation.

Docking precision also becomes increasingly challenging. Heavy payloads produce greater structural deformation, wheel compliance, and suspension deflection. Small mechanical deflections combine with tire slip to introduce positioning errors during final approach. Vision systems, laser alignment, fiducial markers, or local localization refinement are therefore frequently employed to achieve millimeter-level docking accuracy.

Floor conditions significantly influence performance. Highly polished concrete, epoxy coatings, uneven expansion joints, and contaminated surfaces all alter friction characteristics. Differential drive generally performs best on smooth, clean, high-friction industrial floors where tire slip remains predictable.

Despite these limitations, the MiR600 demonstrates that differential drive remains a practical solution within the 600 kg payload category when combined with robust mechanical engineering, advanced localization, intelligent motion planning, and appropriate operating procedures. Nevertheless, these observations also indicate that the economic and technical advantages of differential drive gradually diminish as payload continues to increase.

---

### 3.2 Case Study Evaluating Transition to Steer Drive

Determining the appropriate payload threshold for transitioning from differential drive to steer-drive architecture represents one of the most important design decisions in heavy-duty AMR development. The MiR600 provides an informative reference platform because it operates near the upper practical limit where differential drive remains commercially competitive while simultaneously revealing circumstances in which steer-drive systems become increasingly advantageous.

Steer-drive architecture differs fundamentally from differential drive because each drive module actively controls both wheel rotation and steering angle. Rather than forcing tires to slip laterally during turning, steer-drive wheels continuously align themselves with the desired direction of travel. This alignment substantially reduces tire scrubbing, steering resistance, and mechanical wear.

When payload increases beyond approximately 500--800 kg, several engineering tradeoffs become increasingly apparent. Differential drive continues to offer lower initial cost, fewer moving components, simpler control algorithms, and easier maintenance. However, these benefits are gradually offset by increasing tire wear, higher energy consumption during turning, reduced maneuvering efficiency under heavy loads, and greater sensitivity to floor conditions.

A comparative engineering evaluation illustrates these differences clearly. During continuous warehouse operation involving frequent ninety-degree turns, a differential-drive vehicle experiences repeated lateral tire slip at every corner. Each turning event generates friction losses proportional to vehicle weight. A steer-drive platform, by contrast, performs the same maneuver with minimal lateral tire motion because wheel orientation continuously follows the desired trajectory.

Docking accuracy also improves with steer-drive systems. Because wheel alignment matches vehicle motion, path tracking errors caused by tire scrubbing are significantly reduced. This characteristic becomes increasingly valuable for automated pallet handling, machine loading, precision docking, and robotic manipulation applications requiring highly repeatable positioning.

Energy efficiency similarly favors steer-drive at higher payloads. Reduced tire scrubbing lowers steering resistance, decreasing motor torque demand during maneuvering. Over extended operating periods involving thousands of daily turns, cumulative energy savings become significant, partially offsetting the higher initial investment required for steer-drive hardware.

Mechanical complexity, however, increases substantially. Each steer-drive module requires an additional steering actuator, steering gearbox, position encoder, bearings, wiring, and control electronics. Software complexity also grows because steering angle and wheel speed must be coordinated continuously using more sophisticated kinematic algorithms. Maintenance procedures become correspondingly more demanding.

Reliability considerations therefore depend strongly on application characteristics. In relatively simple transportation tasks involving long straight travel and moderate turning frequency, differential drive often provides superior lifecycle economics due to its mechanical simplicity. Conversely, facilities requiring continuous maneuvering in confined spaces, precise docking, or transportation of heavy payloads may recover the higher investment of steer-drive through improved productivity and reduced maintenance costs.

The MiR600 illustrates that no universal payload threshold exists for transitioning to steer-drive. Instead, the decision should consider multiple engineering factors including payload, duty cycle, turning frequency, docking precision requirements, floor conditions, energy efficiency objectives, maintenance capability, total cost of ownership, and future scalability.

For many industrial applications, differential drive remains economically attractive up to approximately 500--700 kg when navigation accuracy is supported by modern LiDAR localization and intelligent software. Beyond this range, especially above 800--1000 kg or in applications requiring sub-centimeter docking accuracy and intensive maneuvering, steer-drive systems increasingly provide superior long-term technical and economic performance.

Consequently, the MiR600 serves as an important transitional reference in industrial AMR evolution. It demonstrates both the remarkable capability of modern differential-drive platforms and the engineering indicators that suggest when future heavy-duty robot designs should begin adopting steer-drive architectures. Understanding this transition enables system designers to select propulsion technologies that best balance cost, reliability, efficiency, maintainability, and operational performance for specific industrial applications.

MiR600는 산업용 자율주행 모바일 로봇(Autonomous Mobile Robot, AMR)의 발전 과정에서 중요한 이정표가 되는 플랫폼이다. MiR 제품군 가운데 적재 능력(Payload Capacity)을 약 600kg 수준까지 확장하여 중량 자재 운반(Heavy Material Handling), 팔레트 운송(Pallet Transportation), 공작기계 공급(Machine Feeding), 창고 자동화(Warehouse Automation), 제조 물류(Manufacturing Logistics)와 같은 응용 분야를 목표로 개발되었다. 소형 AMR가 부품 박스나 공정 중 재고(Work-in-Process)를 운반하는 수준이었다면, MiR600는 훨씬 큰 관성(Inertia), 높은 구동력(Traction), 증가된 구조 하중(Structural Load), 더욱 엄격한 안전 요구사항을 만족하면서 안정적인 자율주행을 수행해야 한다.

MiR600의 가장 흥미로운 설계 특징 가운데 하나는 600kg급이라는 비교적 높은 적재 하중에서도 차동 구동(Differential Drive)을 유지하고 있다는 점이다. 일반적으로 이 정도 하중에서는 스티어 드라이브(Steer Drive)나 전방향 조향(Omnidirectional Steering) 구조로 전환하는 사례가 많지만, MiR600는 차동 구동을 유지함으로써 기계 구조의 단순성(Mechanical Simplicity), 제조 비용 절감(Lower Manufacturing Cost), 유지보수성(Maintainability), 검증된 제어 알고리즘(Proven Control Algorithm), 높은 신뢰성(Reliability)을 확보하였다. 반면 적재 하중이 증가함에 따라 타이어 마모(Tire Wear), 회전 저항(Turning Resistance), 바닥 하중(Floor Loading), 도킹 정밀도(Docking Precision), 동적 안정성(Dynamic Stability)과 같은 새로운 공학적 과제가 발생한다.

차량 질량(Vehicle Mass)이 증가할수록 차동 구동의 물리적 한계가 점차 뚜렷하게 나타난다. 제자리 회전(Zero-Radius Turn) 시 좌우 바퀴는 서로 다른 속도로 회전하며, 캐스터 휠(Passive Caster Wheel)은 지속적으로 방향을 변경한다. 이 과정에서 바퀴는 실제 이동 방향과 완전히 일치하지 못하므로 횡방향 미끄러짐(Lateral Slip)이 발생한다. 이러한 현상은 회전 저항을 증가시키고 에너지 소비(Energy Consumption)를 높이며 타이어 마모를 가속시키고 위치 오차(Positioning Error)를 발생시킨다.

이러한 영향은 적재 하중이 증가할수록 더욱 커진다. 차량 무게가 증가하면 타이어에 작용하는 수직 하중(Normal Force)이 증가하고, 그 결과 회전 시 발생하는 마찰력이 커진다. 따라서 더 큰 모터 토크(Motor Torque)가 필요하며 구동계(Drivetrain)에 작용하는 기계적 응력(Mechanical Stress)도 증가한다. 또한 휠 변형(Wheel Deformation), 바닥의 미세한 요철(Floor Irregularity), 오도메트리 오차(Odometry Error)가 누적되어 정밀 도킹에도 영향을 미치게 된다.

그럼에도 불구하고 MiR600는 우수한 기계 설계(Mechanical Design), LiDAR 기반 위치 추정(Localization), 지능형 경로 계획(Intelligent Motion Planning), 플릿 관리 소프트웨어(Fleet Management Software)를 결합함으로써 600kg급에서도 차동 구동이 충분히 실용적일 수 있음을 보여준다. 바퀴 오도메트리만 사용하는 것이 아니라 LiDAR 기반 위치 보정을 지속적으로 수행하며, 급격한 회전을 최소화하는 주행 알고리즘을 적용하여 기계적 부담과 에너지 소비를 줄이고 있다.

시스템 공학(System Engineering) 관점에서 MiR600는 차동 구동이 어느 수준까지 경제성과 기술적 경쟁력을 유지할 수 있는지를 보여주는 매우 중요한 사례이다. 동시에 어느 시점부터 스티어 드라이브가 더욱 적합한 선택이 되는지를 판단할 수 있는 기준도 함께 제시하고 있다.

---

### 3.1 600kg급 차동 구동 한계 분석(600kg Class Differential Drive Limitation Analysis)

차동 구동(Differential Drive)은 구조가 단순하고 신뢰성이 높으며 제어가 비교적 쉽기 때문에 실내 AMR에서 가장 널리 사용되는 구동 방식이다. 그러나 적재 하중이 증가하면 차량의 기계적 거동(Mechanical Behavior)이 크게 달라진다. MiR600는 이러한 변화를 분석하기 위한 매우 좋은 사례이다.

차동 구동은 좌우 두 개의 구동 바퀴(Drive Wheel)와 하나 이상의 캐스터 휠(Passive Caster Wheel)로 구성된다. 좌우 바퀴의 속도 차이를 이용하여 조향(Steering)을 수행한다. 두 바퀴가 동일한 속도로 회전하면 직진하고, 서로 다른 속도로 회전하면 회전한다.

적재 하중이 낮을 때에는 이러한 구조가 매우 효율적이다. 타이어 변형(Tire Deformation)이 작고 회전 저항도 낮으며 모터가 충분한 조향 토크를 생성할 수 있기 때문이다. 그러나 적재 하중이 증가하면 여러 가지 비선형적인 현상(Nonlinear Effects)이 나타난다.

가장 먼저 나타나는 문제는 타이어와 바닥 사이의 상호작용(Tire-Ground Interaction)이다. 차동 조향에서는 바퀴가 실제 진행 방향과 일치하지 못하기 때문에 횡방향 미끄러짐(Lateral Slip)이 발생한다. 차량이 무거워질수록 타이어에 작용하는 수직 하중(Normal Force)이 증가하고, 이에 따라 횡방향 마찰력도 커진다. 결국 동일한 회전을 수행하기 위해 더 큰 토크가 필요하게 된다.

캐스터 휠의 거동(Caster Behavior)도 영향을 미친다. 캐스터는 이동 방향이 바뀔 때마다 스스로 방향을 회전시켜야 한다. 특히 제자리 회전이나 급격한 방향 전환에서는 캐스터가 순간적으로 저항을 발생시키며 추가적인 에너지 손실을 유발한다. 적재 하중이 증가할수록 이러한 현상은 더욱 심해진다.

에너지 소비(Energy Consumption)도 증가한다. 직진에서는 주로 구름 저항(Rolling Resistance)만 극복하면 되지만, 회전 시에는 타이어 미끄러짐과 캐스터 회전 저항까지 모두 극복해야 한다. 따라서 회전이 많은 공장 환경에서는 직선 주행보다 훨씬 많은 에너지가 소비되며 배터리 운용 시간이 감소하게 된다.

기계적 마모(Mechanical Wear) 역시 증가한다. 지속적인 횡방향 미끄러짐은 스티어 드라이브보다 타이어 마모를 빠르게 진행시킨다. 또한 베어링(Bearing), 감속기(Gearbox), 구동축(Drivetrain)에도 반복적인 하중 변화가 발생하여 유지보수 주기가 짧아질 수 있다.

위치 추정(Localization)에도 간접적인 영향을 준다. 휠 오도메트리(Wheel Odometry)는 바퀴가 순수하게 굴러간다고 가정하지만, 실제로는 횡방향 미끄러짐이 발생하므로 오도메트리 오차가 누적된다. 특히 회전이 반복되는 환경에서는 오차가 빠르게 증가한다. 다행히 MiR600는 LiDAR 기반 위치 추정을 지속적으로 수행하여 이러한 누적 오차를 보정한다.

정밀 도킹(Docking Precision)도 어려워진다. 차량이 무거워질수록 차체 변형(Structural Deformation), 타이어 탄성(Tire Compliance), 서스펜션 변형(Suspension Deflection)이 증가한다. 이러한 미세한 변형이 타이어 미끄러짐과 함께 누적되어 최종 위치 오차를 발생시킨다. 따라서 비전 시스템(Vision System), 레이저 정렬(Laser Alignment), 기준 마커(Fiducial Marker), 국부 위치 보정(Local Localization Refinement)을 추가적으로 사용하는 경우가 많다.

바닥 조건(Floor Condition)도 중요한 변수이다. 에폭시(Epoxy) 바닥, 콘크리트(Concrete), 팽창 이음부(Expansion Joint), 오염된 바닥은 모두 마찰 계수(Friction Coefficient)를 변화시킨다. 차동 구동은 마찰 특성이 일정한 깨끗한 산업용 바닥에서 가장 안정적인 성능을 발휘한다.

MiR600는 이러한 한계에도 불구하고 견고한 기계 설계, 고정밀 LiDAR 위치 추정, 지능형 경로 계획을 결합함으로써 600kg급에서도 차동 구동이 충분히 실용적일 수 있음을 보여준다. 그러나 이러한 분석은 적재 하중이 더욱 증가할 경우 차동 구동의 경제성과 기술적 장점이 점차 감소한다는 점도 함께 보여준다.

---

### 3.2 스티어 드라이브 전환 평가 사례(Case Study Evaluating Transition to Steer Drive)

차동 구동에서 스티어 드라이브(Steer Drive)로 언제 전환해야 하는가는 중대형 AMR 개발에서 가장 중요한 설계 의사결정 가운데 하나이다. MiR600는 차동 구동이 상업적으로 경쟁력을 유지할 수 있는 상한선에 가까운 플랫폼이면서도, 동시에 스티어 드라이브의 필요성이 나타나는 시점을 분석할 수 있는 좋은 사례이다.

스티어 드라이브는 차동 구동과 근본적으로 다른 구조를 가진다. 각각의 구동 모듈이 구동(Driving)과 조향(Steering)을 모두 수행하며, 바퀴는 항상 이동 방향과 동일한 방향으로 정렬된다. 따라서 회전 시 횡방향 미끄러짐이 거의 발생하지 않으며 타이어 마모와 회전 저항이 크게 감소한다.

적재 하중이 약 500\~800kg 수준에 도달하면 여러 가지 공학적 트레이드오프(Engineering Trade-off)가 나타난다. 차동 구동은 여전히 초기 비용(Initial Cost)이 낮고 구조가 단순하며 유지보수가 쉽다는 장점을 가진다. 그러나 적재 하중이 증가할수록 타이어 마모, 회전 시 에너지 소비, 바닥 조건의 영향, 도킹 정밀도 저하 등의 문제가 점차 커진다.

창고에서 반복적으로 90도 회전을 수행하는 작업을 예로 들면 차동 구동은 모든 회전마다 타이어가 횡방향으로 미끄러진다. 차량이 무거울수록 이러한 마찰 손실은 더욱 커진다. 반면 스티어 드라이브는 바퀴가 항상 진행 방향으로 정렬되므로 횡방향 미끄러짐이 거의 발생하지 않는다.

도킹 정밀도(Docking Precision)도 스티어 드라이브가 유리하다. 바퀴가 이동 방향과 일치하기 때문에 타이어 미끄러짐으로 인한 경로 오차(Path Tracking Error)가 크게 감소한다. 이러한 특성은 자동 팔레트 이송(Automated Pallet Handling), 공작기계 로딩(Machine Loading), 정밀 검사(Precision Inspection), 모바일 매니퓰레이터(Mobile Manipulator)와 같이 높은 반복 정밀도가 요구되는 작업에서 매우 중요한 장점이 된다.

에너지 효율(Energy Efficiency) 역시 스티어 드라이브가 우수하다. 횡방향 마찰이 줄어들기 때문에 회전 시 필요한 모터 토크가 감소하며, 장기간 반복 운전에서는 상당한 에너지 절감 효과를 얻을 수 있다. 이러한 절감 효과는 초기 장비 비용 증가를 어느 정도 상쇄할 수 있다.

그러나 스티어 드라이브는 구조가 훨씬 복잡하다. 각각의 바퀴마다 조향 모터(Steering Motor), 조향 감속기(Steering Gearbox), 엔코더(Position Encoder), 베어링, 케이블, 제어기(Control Electronics)가 추가된다. 또한 제어 알고리즘도 훨씬 복잡해지며 유지보수 난이도 역시 증가한다.

따라서 어떤 방식이 더 우수한지는 운용 환경(Application Characteristics)에 따라 달라진다. 직선 주행이 많고 회전이 적은 환경에서는 차동 구동이 여전히 가장 경제적인 선택이다. 반면 좁은 공간에서 빈번한 회전이 요구되거나 높은 도킹 정밀도와 중량 운반이 필요한 환경에서는 스티어 드라이브가 장기적으로 더 우수한 성능과 경제성을 제공할 수 있다.

MiR600는 스티어 드라이브로 전환해야 하는 절대적인 적재 하중이 존재하지 않는다는 사실을 잘 보여준다. 실제 설계에서는 적재 하중(Payload), 작업 주기(Duty Cycle), 회전 빈도(Turning Frequency), 요구 정밀도(Docking Precision), 바닥 상태(Floor Condition), 에너지 효율(Energy Efficiency), 유지보수 능력(Maintenance Capability), 총 소유 비용(Total Cost of Ownership, TCO), 향후 확장성(Scalability)을 종합적으로 고려하여 결정해야 한다.

일반적인 산업용 AMR에서는 LiDAR 기반 위치 추정과 지능형 제어 소프트웨어를 함께 사용할 경우 약 **500\~700kg** 수준까지는 차동 구동이 충분한 경제성을 가진다. 그러나 **800\~1000kg 이상**의 고중량 플랫폼이나 **±10\~20mm 이하의 정밀 도킹**, 빈번한 회전 작업이 요구되는 경우에는 스티어 드라이브가 장기적으로 더 우수한 기술적·경제적 선택이 될 가능성이 높다.

결국 MiR600는 산업용 AMR 발전 과정에서 매우 중요한 전환점(Transition Platform)이라고 할 수 있다. 이 플랫폼은 차동 구동이 어디까지 확장될 수 있는지를 보여주는 동시에, 어떤 조건에서 차세대 고중량 AMR가 스티어 드라이브를 채택해야 하는지를 명확하게 제시하는 대표적인 사례이다. 이러한 분석은 향후 고하중 산업용 AMR를 설계하는 엔지니어가 비용(Cost), 신뢰성(Reliability), 효율(Efficiency), 유지보수성(Maintainability), 성능(Performance) 사이에서 최적의 구동 방식을 선택하는 데 매우 중요한 기준이 된다.

##  

## 04 MiR1350

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

The MiR1350 represents one of the most ambitious applications of differential-drive technology in industrial Autonomous Mobile Robots (AMRs). Designed for automated pallet transportation with payloads reaching approximately 1,350 kg, the platform extends the practical operating range of differential-drive systems into a payload class that has traditionally been dominated by steer-drive vehicles, Automated Guided Vehicles (AGVs), or forklift-based automation. Its development demonstrates how advances in localization, motion planning, safety systems, and mechanical engineering have significantly expanded the capabilities of differential-drive architectures while simultaneously exposing their physical limitations.

Unlike smaller AMRs that primarily transport lightweight materials, the MiR1350 must safely handle large inertial loads, substantial wheel-ground contact forces, demanding duty cycles, and precise pallet docking operations. The engineering challenge is no longer limited to generating sufficient propulsion force. Instead, vehicle stability, structural rigidity, tire durability, drivetrain efficiency, thermal performance, braking capability, localization robustness, and operational safety all become tightly coupled system-level design considerations.

The MiR1350 adopts a heavy-duty differential-drive platform because this architecture continues to offer several important advantages. The mechanical structure remains relatively simple, containing fewer moving parts than steer-drive systems. The absence of steering actuators reduces manufacturing complexity, lowers maintenance requirements, and improves long-term mechanical reliability. Mature differential-drive control algorithms are well understood within the robotics industry, allowing proven software frameworks to be reused across multiple product generations.

However, increasing payload beyond one ton introduces engineering constraints that become progressively more difficult to overcome. Tire deformation under high vertical loads increases rolling resistance and affects odometry accuracy. Differential steering inevitably generates lateral tire slip, leading to accelerated tread wear and greater energy consumption during frequent turning. Structural deflection becomes more noticeable as payload increases, influencing docking precision and long-term fatigue life. Motor torque requirements grow substantially during acceleration and rotation, demanding larger motors, higher-current motor controllers, stronger gearboxes, and more capable battery systems.

Rather than relying solely on mechanical improvements, the MiR1350 addresses many of these challenges through system integration. High-quality LiDAR localization continuously compensates for odometry drift. Intelligent trajectory planning minimizes unnecessary rotation and reduces tire scrubbing. Fleet management software optimizes travel paths to decrease turning frequency, while automatic charging systems maintain operational availability despite increased energy consumption. This integrated engineering approach allows differential-drive technology to remain commercially competitive even within the heavy-duty logistics segment.

The MiR1350 therefore serves as an important engineering reference for evaluating both the feasibility and practical limitations of one-ton-class differential-drive AMRs. It illustrates how modern software, sensing technologies, and mechanical optimization can significantly extend the useful operating range of differential drive, while simultaneously highlighting the conditions under which alternative propulsion architectures become increasingly attractive.

---

### 4.1 Feasibility and Limits of 1 Ton Class Differential Drive

Designing a differential-drive AMR capable of transporting payloads exceeding one ton represents a significant engineering challenge because several physical limitations scale nonlinearly with vehicle weight. The MiR1350 demonstrates that one-ton-class differential drive is technically achievable, but only through careful optimization of mechanical design, drivetrain selection, localization technology, and operational strategy.

The fundamental operating principle of differential drive remains unchanged regardless of payload. Two independently driven wheels generate both propulsion and steering through differences in rotational speed, while passive caster wheels support the remaining vehicle weight. This simplicity provides excellent reliability and reduces mechanical complexity compared with steer-drive systems.

As payload approaches or exceeds one ton, however, the contact mechanics between the tires and floor become the dominant engineering concern. Increased vehicle mass raises the normal force acting on each drive wheel, thereby increasing friction. During differential steering, lateral tire slip becomes unavoidable because the wheels cannot continuously align themselves with the instantaneous direction of motion. The resulting friction significantly increases steering resistance.

Motor sizing therefore becomes considerably more demanding. Straight-line propulsion remains relatively efficient because only rolling resistance must be overcome. During turning, however, motors must additionally overcome tire scrubbing forces, caster reorientation resistance, and increased drivetrain friction. Peak motor torque requirements during low-speed rotation may substantially exceed those observed during straight-line travel.

The drivetrain must also withstand significantly higher mechanical loading. Gearboxes experience larger transmitted torques, bearings carry greater radial loads, and wheel hubs are subjected to increased bending moments. Fatigue life calculations become particularly important because industrial AMRs often operate continuously across multiple shifts for many years.

Structural stiffness plays an increasingly important role at this payload level. Small chassis deflections under heavy loads may alter wheel alignment, sensor calibration, and docking accuracy. Finite Element Analysis (FEA) is therefore extensively used to optimize frame stiffness while minimizing unnecessary weight. Weld quality, structural reinforcement, and load distribution become critical design considerations.

Wheel selection becomes another limiting factor. Tire material, diameter, width, and compliance directly influence traction, rolling resistance, vibration isolation, and wear characteristics. Larger wheel diameters improve obstacle negotiation but increase vehicle height and center of gravity. Wider tires reduce ground pressure but increase steering resistance during differential turning. Engineers must carefully balance these competing requirements.

Localization technology becomes increasingly important because wheel odometry alone cannot maintain sufficient accuracy under heavy loads. Tire deformation, floor irregularities, and lateral slip introduce cumulative positioning errors. High-frequency LiDAR localization, inertial measurement units, and sensor fusion continuously correct these errors, allowing accurate navigation despite imperfect wheel-ground interaction.

Docking precision presents another engineering challenge. Heavy pallet handling often requires positioning accuracy better than ±20 mm. Differential-drive vehicles may achieve this accuracy through local localization refinement, vision-assisted docking, laser alignment systems, or mechanical guide structures that compensate for residual navigation errors.

Operational environment strongly influences feasibility. Differential drive performs best on smooth, high-friction industrial floors with moderate turning frequency. Applications involving continuous tight maneuvering, uneven surfaces, ramps, or contaminated floors place significantly greater demands on the drivetrain.

The MiR1350 demonstrates that one-ton-class differential drive is technically feasible when supported by advanced localization, robust mechanical engineering, intelligent control software, and carefully selected operating conditions. Nevertheless, it also reveals that the performance margin gradually decreases as payload continues to increase, indicating that differential drive eventually approaches its practical engineering limits.

---

### 4.2 Design Trade-offs

The development of a one-ton-class AMR inevitably involves numerous engineering trade-offs because improvements in one subsystem frequently introduce compromises elsewhere. The MiR1350 provides an excellent example of how successful industrial robot design depends on balancing performance, cost, reliability, maintainability, safety, and operational efficiency rather than maximizing any single specification.

One of the most significant trade-offs involves drivetrain architecture. Differential drive offers lower mechanical complexity, fewer actuators, reduced maintenance requirements, and mature control software. In contrast, steer-drive systems provide superior maneuverability, lower tire wear, higher energy efficiency during turning, and improved docking precision. Selecting between these architectures requires evaluating not only technical performance but also lifecycle economics.

Structural design presents another important compromise. Increasing chassis stiffness improves localization accuracy, docking repeatability, and long-term durability. However, additional structural reinforcement increases vehicle weight, which in turn raises energy consumption, reduces battery operating time, and increases floor loading. Engineers therefore seek optimized structures that maximize stiffness-to-weight ratio rather than absolute stiffness.

Battery sizing introduces additional design considerations. Larger battery capacity extends operating time and reduces charging frequency, but also increases vehicle mass, cost, charging duration, and structural loading. Conversely, smaller batteries reduce weight but require more frequent opportunity charging and may limit productivity during continuous operation.

Motor selection requires balancing continuous power capability against efficiency and thermal performance. Oversized motors easily satisfy peak torque demands but operate inefficiently during normal conditions and increase overall system cost. Smaller motors improve efficiency and reduce weight but may experience thermal overload during intensive maneuvering or steep acceleration.

Wheel design also involves multiple competing objectives. Softer tire compounds improve traction and reduce vibration but wear more rapidly. Harder compounds provide longer service life but reduce grip and may increase localization errors on uneven floors. Tire width similarly affects both ground pressure and steering resistance.

Control software plays a crucial role in mitigating many mechanical compromises. Intelligent path planning reduces unnecessary rotations, thereby decreasing tire wear and energy consumption. Smooth acceleration profiles reduce drivetrain loading and improve passenger safety when transporting sensitive equipment. Adaptive speed control balances productivity with mechanical longevity.

Maintenance strategy influences component selection. Highly modular systems simplify servicing and reduce downtime but may increase manufacturing cost due to additional connectors, interfaces, and structural complexity. Fully integrated designs minimize weight and cost but complicate field maintenance and component replacement.

Economic considerations frequently dominate commercial product development. Although steer-drive systems may deliver superior technical performance, differential-drive platforms often provide lower total cost of ownership in applications involving moderate maneuvering and predictable operating environments. Initial investment, maintenance costs, spare parts inventory, technician training, and operational efficiency must all be considered together.

Scalability represents another strategic trade-off. A differential-drive platform may be extended from 250 kg to approximately one ton using largely similar software architecture, control algorithms, and manufacturing processes. Transitioning to steer-drive frequently requires substantial redesign of mechanical systems, control software, safety architecture, and maintenance procedures. Manufacturers therefore carefully evaluate whether incremental improvements to existing differential-drive platforms provide greater commercial value than introducing entirely new vehicle architectures.

The MiR1350 demonstrates that engineering decisions should always be evaluated from a complete system perspective rather than focusing on individual subsystem optimization. Successful heavy-duty AMR development depends upon balancing mechanical simplicity, localization accuracy, energy efficiency, maintenance requirements, operational flexibility, and economic viability. While differential drive continues to provide compelling advantages within certain payload ranges, increasing operational demands gradually shift the optimal balance toward more sophisticated propulsion architectures. This transition illustrates the importance of systems engineering in modern industrial robotics, where long-term reliability and lifecycle performance often outweigh maximum theoretical capability.

MiR1350는 산업용 자율주행 모바일 로봇(Autonomous Mobile Robot, AMR) 분야에서 차동 구동(Differential Drive) 기술을 가장 적극적으로 확장한 대표적인 플랫폼 가운데 하나이다. 약 **1,350kg급 적재 하중(Payload Capacity)** 을 지원하는 이 플랫폼은 기존에 스티어 드라이브(Steer Drive), AGV(Automated Guided Vehicle), 또는 자동화 지게차(Forklift Automation)가 담당하던 중량 팔레트(Pallet) 운송 영역까지 차동 구동 기술을 확장하였다. MiR1350의 개발은 위치 추정(Localization), 경로 계획(Motion Planning), 안전 시스템(Safety System), 기계 설계(Mechanical Engineering)의 발전이 차동 구동의 활용 범위를 얼마나 크게 넓힐 수 있는지를 보여주는 대표적인 사례이며, 동시에 물리적인 한계(Physical Limitation) 역시 명확하게 보여준다.

소형 AMR가 단순히 부품이나 공정 중 재고(Work-in-Process)를 운반하는 수준이었다면, MiR1350는 훨씬 큰 관성(Inertia), 높은 바퀴-노면 접촉력(Wheel-Ground Contact Force), 장시간 연속 운전(Long Duty Cycle), 고정밀 팔레트 도킹(Pallet Docking)을 동시에 만족해야 한다. 따라서 설계의 핵심은 단순히 추진력(Propulsion Force)을 확보하는 것이 아니라 차량 안정성(Vehicle Stability), 구조 강성(Structural Rigidity), 타이어 내구성(Tire Durability), 구동계 효율(Drivetrain Efficiency), 열 관리(Thermal Performance), 제동 성능(Braking Performance), 위치 추정 정확도(Localization Accuracy), 안전성(Safety)을 하나의 시스템(System)으로 통합하는 것이다.

MiR1350가 차동 구동을 유지한 이유는 여전히 많은 장점을 가지고 있기 때문이다. 차동 구동은 스티어 드라이브보다 기계 구조(Mechanical Structure)가 단순하며, 조향 액추에이터(Steering Actuator)가 필요하지 않아 제조 비용과 유지보수 비용을 줄일 수 있다. 또한 수년간 산업 현장에서 검증된 제어 알고리즘(Control Algorithm)을 그대로 활용할 수 있으며 장기적인 신뢰성(Long-Term Reliability)도 우수하다.

그러나 적재 하중이 1톤을 넘어가면 새로운 공학적 문제가 점차 커진다. 높은 수직 하중으로 인해 타이어 변형(Tire Deformation)이 증가하고, 이는 구름 저항(Rolling Resistance)과 오도메트리 오차(Odometry Error)를 증가시킨다. 차동 조향 과정에서는 필연적으로 횡방향 미끄러짐(Lateral Tire Slip)이 발생하며, 이는 타이어 마모(Tire Wear)를 빠르게 증가시키고 회전 시 에너지 소비(Energy Consumption)를 크게 높인다. 또한 차체 변형(Structural Deflection)은 도킹 정밀도(Docking Precision)와 장기적인 피로 수명(Fatigue Life)에 영향을 준다. 가속과 회전 시 요구되는 모터 토크(Motor Torque)가 크게 증가하므로 더욱 강력한 모터(Motor), 고전류 드라이버(Motor Driver), 감속기(Gearbox), 대용량 배터리(Battery)가 필요하다.

MiR1350는 이러한 문제를 단순히 기계 설계만으로 해결하지 않는다. 고정밀 LiDAR 기반 위치 추정은 오도메트리 오차를 지속적으로 보정하며, 지능형 경로 계획(Intelligent Trajectory Planning)은 불필요한 회전을 줄여 타이어 마모를 감소시킨다. 플릿 관리 시스템(Fleet Management System)은 회전 횟수를 최소화하는 경로를 선택하고, 자동 충전(Auto Charging)을 통해 증가한 에너지 소비를 보완한다. 즉 기계 설계(Mechanical Design), 센서(Sensor), 제어(Control), 소프트웨어(Software)를 통합하는 시스템 엔지니어링(System Engineering)이 차동 구동을 1톤 이상까지 확장시키는 핵심 기술이 되었다.

MiR1350는 따라서 **1톤급 차동 구동 AMR가 실제 산업 현장에서 어느 정도까지 구현 가능한지를 보여주는 매우 중요한 기준 플랫폼(Reference Platform)** 이며, 동시에 차동 구동이 점차 물리적 한계에 접근하고 있음을 보여주는 대표적인 사례이기도 하다.

---

### 4.1 1톤급 차동 구동의 가능성과 한계(Feasibility and Limits of 1 Ton Class Differential Drive)

1톤 이상의 적재 하중을 운반하는 차동 구동 AMR를 설계하는 것은 매우 어려운 공학적 과제이다. 차량 무게가 증가할수록 여러 가지 물리적 현상이 선형적으로 증가하지 않고 비선형적(Nonlinear)으로 커지기 때문이다. MiR1350는 이러한 조건에서도 차동 구동이 구현 가능함을 보여주지만, 동시에 그 한계도 명확하게 보여준다.

차동 구동의 기본 원리는 변하지 않는다. 좌우 두 개의 구동 바퀴(Drive Wheel)가 서로 다른 회전 속도를 만들어 추진과 조향을 동시에 수행하며, 나머지 하중은 캐스터 휠(Passive Caster Wheel)이 지지한다. 이러한 구조는 단순하고 신뢰성이 높으며 유지보수가 쉽다는 장점을 가진다.

그러나 적재 하중이 1톤을 넘어가면 타이어와 바닥(Tire-Ground Contact)의 접촉 특성이 가장 중요한 문제가 된다. 차량 무게가 증가할수록 타이어에 작용하는 수직 하중(Normal Force)이 증가하고, 이에 따라 마찰력(Friction Force)도 커진다. 차동 조향에서는 바퀴가 실제 진행 방향과 일치하지 못하기 때문에 횡방향 미끄러짐이 반드시 발생한다. 이러한 마찰은 회전 저항(Turning Resistance)을 크게 증가시킨다.

모터 선정(Motor Sizing)도 훨씬 어려워진다. 직진에서는 구름 저항만 극복하면 되지만 회전에서는 타이어 스크러빙(Tire Scrubbing), 캐스터 회전 저항(Caster Reorientation Resistance), 구동계 마찰(Drivetrain Friction)까지 극복해야 한다. 특히 저속 회전에서는 직진보다 훨씬 큰 피크 토크(Peak Torque)가 요구된다.

구동계(Drivetrain)의 기계적 하중도 크게 증가한다. 감속기(Gearbox)는 더 큰 토크를 전달해야 하며, 베어링(Bearing)은 높은 반경 방향 하중(Radial Load)을 지지해야 한다. 휠 허브(Wheel Hub)는 더 큰 굽힘 모멘트(Bending Moment)를 받게 되므로 피로 수명(Fatigue Life)을 충분히 고려해야 한다.

차체 강성(Structural Stiffness)은 더욱 중요해진다. 무거운 하중에 의해 발생하는 미세한 차체 변형은 바퀴 정렬(Wheel Alignment), 센서 보정(Sensor Calibration), 도킹 정밀도에 영향을 준다. 따라서 설계 단계에서는 유한요소해석(Finite Element Analysis, FEA)을 적극적으로 활용하여 충분한 강성을 확보하면서도 차량 무게는 최소화해야 한다. 용접 품질(Weld Quality), 보강 구조(Reinforcement), 하중 분산(Load Distribution) 역시 중요한 설계 요소가 된다.

바퀴 선정(Wheel Selection)도 성능을 결정하는 핵심 요소이다. 타이어 재질(Tire Material), 직경(Diameter), 폭(Width), 탄성(Compliance)은 접지력(Traction), 구름 저항, 진동 절연(Vibration Isolation), 마모 특성에 직접적인 영향을 준다. 큰 바퀴는 장애물 통과 성능을 향상시키지만 차량 높이와 무게 중심을 증가시킨다. 넓은 타이어는 접지 압력을 줄이지만 차동 회전 시 조향 저항이 증가한다. 따라서 여러 요소를 균형 있게 설계해야 한다.

위치 추정(Localization)은 더욱 중요해진다. 타이어 변형과 미끄러짐 때문에 휠 오도메트리만으로는 충분한 정확도를 유지할 수 없다. 따라서 LiDAR 위치 추정(LiDAR Localization), IMU, 센서 융합(Sensor Fusion)을 이용하여 오도메트리 오차를 지속적으로 보정해야 한다.

정밀 도킹(Docking Precision)은 또 다른 과제이다. 중량 팔레트 운송에서는 일반적으로 **±20mm 이하**의 위치 정밀도가 요구된다. 이를 위해 비전 기반 도킹(Vision-Assisted Docking), 레이저 정렬(Laser Alignment), 국부 위치 보정(Local Localization Refinement), 기계식 가이드(Mechanical Guide)를 함께 사용하는 경우가 많다.

운용 환경(Operation Environment)도 매우 중요하다. 차동 구동은 평탄하고 마찰 특성이 일정한 산업용 바닥에서 가장 우수한 성능을 발휘한다. 반면 좁은 공간에서 반복적인 회전이 많거나 경사로(Ramp), 요철(Uneven Surface), 오염된 바닥에서는 구동계에 훨씬 큰 부담이 발생한다.

MiR1350는 이러한 조건에서도 차동 구동이 충분히 구현 가능함을 보여주지만, 적재 하중이 계속 증가할수록 성능 여유(Performance Margin)가 점차 줄어들며 차동 구동의 실질적인 한계에 가까워지고 있음을 보여준다.

---

### 4.2 설계 트레이드오프(Design Trade-offs)

1톤급 AMR를 개발하는 과정에서는 하나의 성능을 향상시키면 다른 성능이 희생되는 다양한 설계 트레이드오프(Design Trade-off)가 발생한다. MiR1350는 성능, 비용, 신뢰성, 유지보수성, 안전성, 운영 효율을 균형 있게 설계한 대표적인 사례이다.

가장 중요한 트레이드오프는 구동 방식(Drivetrain Architecture)이다. 차동 구동은 구조가 단순하고 액추에이터 수가 적으며 유지보수가 쉽고 제어 소프트웨어가 성숙해 있다는 장점이 있다. 반면 스티어 드라이브는 회전 효율이 높고 타이어 마모가 적으며 도킹 정밀도가 우수하다. 따라서 어느 방식을 선택할지는 단순한 기술 비교가 아니라 생애주기 비용(Lifecycle Cost)까지 고려해야 한다.

차체 설계(Structural Design)도 중요한 절충 관계를 가진다. 강성을 높이면 위치 추정과 도킹 정확도는 향상되지만 차량 무게가 증가한다. 무게가 증가하면 에너지 소비가 늘어나고 배터리 운용 시간이 감소하며 바닥 하중도 증가한다. 따라서 절대적인 강성이 아니라 **강성 대비 무게(Stiffness-to-Weight Ratio)** 를 최적화하는 것이 중요하다.

배터리 용량(Battery Capacity) 역시 동일한 문제를 가진다. 배터리가 크면 운행 시간이 늘어나지만 차량 무게, 가격, 충전 시간, 구조 하중이 모두 증가한다. 반대로 작은 배터리는 가볍지만 기회 충전(Opportunity Charging)을 자주 수행해야 한다.

모터 선정(Motor Selection)도 절충이 필요하다. 큰 모터는 충분한 토크를 제공하지만 평상시에는 효율이 떨어지고 비용이 증가한다. 작은 모터는 효율은 좋지만 반복적인 회전이나 급가속에서 과열(Thermal Overload)이 발생할 수 있다.

타이어(Tire Design)도 서로 상충되는 요소가 많다. 부드러운 고무는 접지력이 좋고 진동을 줄여주지만 마모가 빠르다. 단단한 고무는 오래 사용할 수 있지만 접지력이 떨어지고 위치 추정 오차가 증가할 수 있다. 타이어 폭 역시 접지 압력과 회전 저항 사이에서 균형을 맞추어야 한다.

제어 소프트웨어(Control Software)는 이러한 기계적 한계를 보완하는 중요한 역할을 한다. 지능형 경로 계획(Intelligent Path Planning)은 불필요한 회전을 줄여 타이어 마모와 에너지 소비를 감소시킨다. 부드러운 가속(Smooth Acceleration)과 감속은 구동계 하중을 줄이고 민감한 화물의 안전성을 향상시킨다.

유지보수 전략(Maintenance Strategy)도 설계에 영향을 준다. 모듈형 설계(Modular Design)는 유지보수를 쉽게 하지만 커넥터와 인터페이스가 증가하여 제조 비용이 상승할 수 있다. 반면 완전 통합형 설계는 가볍고 저렴하지만 현장 수리가 어렵다.

경제성(Economic Consideration)은 실제 제품 개발에서 가장 중요한 요소 가운데 하나이다. 스티어 드라이브가 기술적으로 더 우수하더라도 회전이 많지 않은 일반적인 물류 환경에서는 차동 구동이 총 소유 비용(Total Cost of Ownership, TCO) 측면에서 더 유리한 경우가 많다. 초기 투자비(Initial Investment), 유지보수 비용(Maintenance Cost), 예비 부품(Spare Parts), 기술자 교육(Technician Training), 운영 효율(Operation Efficiency)을 모두 함께 고려해야 한다.

확장성(Scalability)도 중요한 요소이다. 차동 구동 플랫폼은 250kg에서 약 1톤 이상까지 기존 소프트웨어와 제조 공정을 대부분 유지하면서 확장할 수 있다. 반면 스티어 드라이브로 전환하면 기계 구조, 제어 알고리즘, 안전 시스템, 유지보수 체계를 모두 새롭게 설계해야 한다. 따라서 제조사는 기존 플랫폼을 확장하는 것이 더 경제적인지, 완전히 새로운 플랫폼을 개발하는 것이 더 적절한지를 신중하게 판단해야 한다.

MiR1350는 **무거운 산업용 AMR는 단일 부품의 성능이 아니라 전체 시스템(System)을 최적화해야 한다는 사실**을 잘 보여준다. 기계 구조, 위치 추정, 에너지 효율, 유지보수성, 운영 유연성, 경제성을 종합적으로 고려할 때 비로소 성공적인 산업용 AMR가 완성된다. 차동 구동은 여전히 일정한 적재 하중 범위에서는 매우 경쟁력 있는 기술이지만, 하중과 작업 요구사항이 증가할수록 스티어 드라이브가 점차 더 유리해지는 방향으로 설계 균형이 이동하게 된다. 이러한 변화는 현대 산업용 로보틱스에서 **시스템 엔지니어링(System Engineering)** 이 얼마나 중요한지를 보여주는 대표적인 사례이며, 실제 산업 현장에서는 최대 성능보다 **장기적인 신뢰성(Long-Term Reliability)** 과 **생애주기 성능(Lifecycle Performance)** 이 더욱 중요한 설계 기준이 된다는 점을 명확하게 보여준다.

##  

## 05 Hills PB Series

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

The Hills PB Series represents a family of industrial Autonomous Mobile Robot (AMR) platforms developed around a scalable design philosophy that emphasizes modularity, standardized components, and long-term product evolution. Rather than designing every payload class as an entirely independent robot, the PB Series adopts a platform strategy in which multiple payload capacities share common mechanical architecture, electrical systems, software frameworks, and manufacturing processes. This approach significantly reduces development cost, shortens product development cycles, simplifies maintenance, and allows customers to migrate between payload classes with minimal operational disruption.

The PB Series is organized around several payload categories that correspond to different industrial applications. The PB50 targets lightweight logistics, laboratory automation, electronics manufacturing, and small component transportation. The PB100 expands capability toward medium-duty manufacturing logistics while maintaining excellent maneuverability and compact dimensions. Future platforms including PB250 and heavier variants extend the architecture toward pallet transportation, machine tending, warehouse automation, and heavy industrial material handling.

A fundamental design principle of the PB Series is that propulsion architecture should evolve according to payload rather than following a single universal solution. Differential drive provides an excellent balance of simplicity, reliability, cost, and maintainability for lightweight and medium-duty platforms. However, increasing payload gradually shifts engineering priorities toward tire durability, docking precision, maneuverability, drivetrain efficiency, and lifecycle operating cost. Consequently, higher-capacity platforms may require alternative drive architectures such as steer drive while preserving as much platform commonality as possible.

Another distinguishing feature of the PB Series is the integration of modern perception technologies, LiDAR-based localization, sensor fusion, intelligent motion planning, fleet management software, and modular upper-body interfaces. These capabilities allow identical software infrastructure to operate across multiple payload classes while enabling application-specific customization through interchangeable upper modules.

From a systems engineering perspective, the PB Series is intended not merely as a collection of robots but as a unified mobility platform supporting long-term industrial automation strategies. Customers may initially deploy PB50 robots for lightweight logistics and later introduce PB100 or PB250 vehicles while maintaining common software tools, operator training, spare parts strategy, and fleet management systems. This platform continuity reduces total cost of ownership while protecting long-term customer investment.

The PB Series therefore illustrates how successful industrial AMR development depends upon scalable architecture, carefully planned technology transitions, and systematic engineering decisions that balance performance, reliability, maintainability, and future expandability.

---

### 5.1 Design Decision Rationale for PB50 and PB100

The PB50 and PB100 were conceived as the foundation of the Hills PB Series, establishing a standardized platform capable of serving a wide range of indoor industrial automation applications. Rather than maximizing payload or pursuing highly specialized functions, these platforms were designed to provide the optimal balance among mobility, reliability, cost efficiency, ease of manufacturing, and software scalability.

One of the earliest design decisions involved selecting differential drive as the propulsion architecture. Extensive engineering evaluation indicated that payloads within the 50--100 kg range remain well suited to differential drive because tire deformation is limited, steering resistance remains low, drivetrain loading is moderate, and wheel slip has minimal influence on localization accuracy. The architecture also minimizes mechanical complexity by eliminating steering actuators, steering gearboxes, additional encoders, and associated control electronics.

Mechanical simplicity provides several long-term advantages. Fewer moving components reduce manufacturing cost, improve reliability, simplify maintenance procedures, and decrease spare-parts inventory. Standardized drive modules can be shared between multiple product variants, reducing both engineering effort and production cost.

The chassis was designed using a modular structural concept. Battery modules, motor drivers, computing hardware, safety controllers, communication devices, and sensor packages are arranged using standardized mounting interfaces that permit future hardware upgrades without requiring complete mechanical redesign. This modularity significantly shortens future development cycles while supporting rapid customization for customer-specific applications.

Battery architecture also reflects careful systems engineering. Rather than maximizing battery capacity, the design targets practical operating duration while maintaining low vehicle weight and a favorable center of gravity. Opportunity charging strategies further reduce the need for excessively large battery packs, improving both vehicle efficiency and lifecycle economics.

Localization strategy strongly influenced the overall architecture. High-quality LiDAR localization combined with wheel odometry and inertial sensing provides reliable navigation without requiring expensive mechanical precision throughout the drivetrain. Software compensation therefore reduces dependence on extremely tight manufacturing tolerances while maintaining industrial navigation accuracy.

The PB50 and PB100 were also designed with manufacturing scalability in mind. Common structural components, identical electrical architecture, standardized wiring harnesses, unified software frameworks, and shared diagnostic tools reduce production complexity and improve quality consistency. Service technicians require minimal additional training when supporting different payload variants because most subsystems remain fundamentally identical.

Upper-body integration formed another important design objective. Standardized mechanical mounting patterns, electrical power interfaces, Ethernet connectivity, and communication APIs enable rapid integration of conveyors, lifting mechanisms, collaborative robots, inspection equipment, storage racks, and customer-specific automation modules. This flexibility significantly expands application diversity without modifying the mobile platform itself.

Economically, the PB50 and PB100 prioritize total lifecycle value rather than minimum initial purchase price. Lower maintenance requirements, simplified spare-parts management, common software infrastructure, and long service life reduce operating costs while improving fleet reliability. These characteristics make the platforms particularly attractive for manufacturing facilities planning gradual expansion over many years.

Overall, the PB50 and PB100 demonstrate that successful industrial robot design depends on selecting engineering solutions appropriate to the intended payload rather than pursuing unnecessarily complex technologies. Differential drive, modular architecture, standardized interfaces, and scalable software together establish a highly efficient foundation for the entire PB product family.

---

### 5.2 Transition Study for PB250 and Above

As payload requirements increase beyond approximately 250 kg, the engineering priorities governing AMR design begin to change significantly. While many architectural principles established for the PB50 and PB100 remain applicable, increasing vehicle mass introduces new mechanical, electrical, and operational challenges that require careful reevaluation of platform architecture. The PB250 therefore represents a natural transition point within the Hills PB Series.

The first major consideration involves propulsion technology. Differential drive continues to provide excellent reliability and cost advantages within moderate payload ranges, but increasing payload progressively amplifies tire slip, steering resistance, drivetrain loading, and tire wear. These effects become particularly noticeable during frequent turning, precision docking, and continuous industrial operation.

Engineering analysis suggests that payload alone should not determine the transition toward steer drive. Instead, multiple system-level factors must be evaluated simultaneously. These include vehicle payload, duty cycle, turning frequency, required docking accuracy, floor conditions, operational speed, energy efficiency objectives, maintenance capability, and expected lifecycle cost.

For applications involving relatively straight transportation routes with moderate maneuvering frequency, differential drive may remain economically attractive even at payloads approaching 300--500 kg. Advanced LiDAR localization, intelligent path planning, and robust mechanical design can compensate for many limitations associated with wheel slip and odometry error.

However, applications requiring intensive maneuvering, frequent pallet handling, high-precision machine loading, narrow warehouse aisles, or continuous multi-shift operation increasingly favor steer-drive architectures. Active wheel steering minimizes lateral tire slip, reduces steering resistance, improves energy efficiency, enhances docking repeatability, and decreases long-term tire replacement costs.

The PB250 transition study therefore recommends maintaining maximum platform commonality while allowing propulsion architecture to evolve independently. Electrical systems, software frameworks, battery technology, safety architecture, fleet management, localization algorithms, diagnostic tools, and communication interfaces should remain largely identical across the product family. Only propulsion-specific subsystems such as steering actuators, wheel modules, kinematic controllers, and suspension structures require significant redesign.

This modular transition strategy provides substantial commercial advantages. Existing customers familiar with PB50 and PB100 platforms can adopt higher-capacity vehicles without retraining operators or replacing software infrastructure. Fleet management systems can coordinate both differential-drive and steer-drive vehicles simultaneously using common operational procedures.

Future scalability also becomes significantly easier. Once the platform architecture supports both propulsion technologies, additional products including PB500, PB800, PB1200, and heavier industrial transport vehicles can be developed using largely common software and electronic architecture while selecting propulsion systems appropriate for each payload class.

From a manufacturing perspective, standardized interfaces reduce inventory complexity while supporting flexible production lines capable of assembling multiple vehicle variants. Engineering resources can focus on optimizing payload-specific mechanical systems rather than redesigning complete robots for every market segment.

The transition study ultimately concludes that PB250 should not be viewed merely as a larger PB100 but rather as the beginning of a new engineering optimization region where drivetrain selection becomes application-dependent rather than universally standardized. Differential drive remains highly competitive for many medium-duty industrial applications, while steer drive increasingly becomes the preferred solution as payload, maneuvering intensity, precision requirements, and operational complexity continue to increase.

The Hills PB Series therefore adopts a technology roadmap in which propulsion architecture evolves only when justified by measurable engineering and economic benefits, while preserving maximum commonality across the overall platform ecosystem. This strategy supports sustainable product evolution, minimizes customer migration cost, and provides a flexible foundation for future generations of industrial autonomous mobile robots.

Hills PB Series는 확장 가능한 플랫폼(Scalable Platform) 철학을 기반으로 개발된 산업용 자율주행 모바일 로봇(Autonomous Mobile Robot, AMR) 제품군이다. 이 시리즈는 적재 하중(Payload)이 다른 로봇을 각각 별도로 개발하는 방식이 아니라, 공통 기계 구조(Common Mechanical Architecture), 공통 전기 시스템(Common Electrical System), 공통 소프트웨어 프레임워크(Common Software Framework), 공통 제조 공정(Common Manufacturing Process)을 공유하는 플랫폼 전략(Platform Strategy)을 채택하였다. 이러한 접근 방식은 개발 비용을 크게 절감하고 제품 개발 기간을 단축하며 유지보수를 단순화하고, 고객이 적재 하중이 다른 플랫폼으로 확장하더라도 최소한의 운영 변경만으로 시스템을 계속 사용할 수 있도록 한다.

PB Series는 산업 현장의 다양한 응용 분야를 고려하여 여러 개의 적재 하중(Payload Class)으로 구성된다. PB50은 경량 물류(Lightweight Logistics), 연구소 자동화(Laboratory Automation), 전자 산업(Electronics Manufacturing), 소형 부품 운반(Small Component Transportation)을 목표로 한다. PB100은 중형 제조 물류(Medium-Duty Manufacturing Logistics) 영역으로 확장하면서도 높은 기동성(Maneuverability)과 소형 차체(Compact Dimensions)를 유지한다. 향후 PB250 및 그 이상의 플랫폼은 팔레트 운반(Pallet Transportation), 공작기계 공급(Machine Tending), 창고 자동화(Warehouse Automation), 중량 산업 물류(Heavy Industrial Material Handling)까지 적용 범위를 확대하는 것을 목표로 한다.

PB Series의 가장 중요한 설계 원칙 가운데 하나는 **구동 방식(Propulsion Architecture)은 적재 하중에 따라 변화해야 하며, 모든 하중을 하나의 방식으로 해결하려고 해서는 안 된다**는 것이다. 차동 구동(Differential Drive)은 경량 및 중형 플랫폼에서 구조 단순성(Mechanical Simplicity), 높은 신뢰성(Reliability), 낮은 비용(Cost), 우수한 유지보수성(Maintainability)을 동시에 제공한다. 그러나 적재 하중이 증가하면 타이어 내구성(Tire Durability), 도킹 정밀도(Docking Precision), 기동성(Maneuverability), 구동 효율(Drivetrain Efficiency), 생애주기 운영 비용(Lifecycle Operating Cost)이 더욱 중요한 요소가 된다. 따라서 고하중 플랫폼에서는 스티어 드라이브(Steer Drive)와 같은 새로운 구동 방식을 적용하면서도 플랫폼의 공통성(Commonality)은 최대한 유지하는 전략을 채택한다.

PB Series의 또 다른 특징은 최신 인식 기술(Perception Technology), LiDAR 기반 위치 추정(LiDAR Localization), 센서 융합(Sensor Fusion), 지능형 경로 계획(Intelligent Motion Planning), 플릿 관리 시스템(Fleet Management System), 모듈형 상부 인터페이스(Modular Upper Body Interface)를 모두 통합하였다는 점이다. 이러한 구조 덕분에 동일한 소프트웨어 인프라를 여러 적재 하중의 플랫폼에서 공통적으로 사용할 수 있으며, 상부 모듈만 교체하여 고객 맞춤형(Customized Application) 시스템을 쉽게 구성할 수 있다.

시스템 엔지니어링(System Engineering) 관점에서 PB Series는 단순한 로봇 제품군이 아니라 장기간 산업 자동화(Long-Term Industrial Automation)를 위한 통합 이동 플랫폼(Unified Mobility Platform)이다. 고객은 PB50을 이용하여 경량 물류를 시작한 후, 생산량 증가에 따라 PB100, PB250으로 확장하더라도 동일한 소프트웨어, 동일한 플릿 관리 시스템, 동일한 유지보수 체계, 동일한 운영자 교육 체계를 그대로 사용할 수 있다. 이는 총 소유 비용(Total Cost of Ownership, TCO)을 크게 절감하고 고객의 장기적인 투자를 보호하는 중요한 장점이 된다.

결국 Hills PB Series는 **확장 가능한 플랫폼(Scalable Platform)**, **계획적인 기술 전환(Technology Transition)**, **체계적인 시스템 설계(Systematic Engineering)** 를 통해 성능(Performance), 신뢰성(Reliability), 유지보수성(Maintainability), 미래 확장성(Future Expandability)을 동시에 확보한 산업용 AMR 플랫폼으로 설계되었다.

---

### 5.1 PB50 및 PB100 설계 결정 배경(Design Decision Rationale for PB50 and PB100)

PB50과 PB100은 Hills PB Series의 가장 기본이 되는 플랫폼으로 설계되었다. 이들 플랫폼은 특정 기능을 극대화하기보다는 실내 산업 자동화(Indoor Industrial Automation)에서 가장 넓은 범위를 커버할 수 있도록 이동성(Mobility), 신뢰성(Reliability), 경제성(Cost Efficiency), 제조 용이성(Manufacturability), 소프트웨어 확장성(Software Scalability)을 균형 있게 고려하여 개발되었다.

가장 먼저 결정된 사항은 차동 구동(Differential Drive)의 채택이었다. 다양한 설계 검토 결과, **50\~100kg 수준의 적재 하중에서는 차동 구동이 가장 이상적인 구조**라는 결론에 도달하였다. 이 구간에서는 타이어 변형(Tire Deformation)이 매우 작고 회전 저항(Steering Resistance)이 낮으며 구동계(Drivetrain)에 작용하는 하중도 크지 않다. 또한 횡방향 미끄러짐(Lateral Slip)이 위치 추정(Localization)에 미치는 영향도 거의 무시할 수 있다.

차동 구동은 조향 모터(Steering Motor), 조향 감속기(Steering Gearbox), 추가 엔코더(Position Encoder), 조향 제어기(Steering Controller)가 필요하지 않으므로 기계 구조가 매우 단순하다. 이러한 단순성은 장기적으로 여러 가지 장점을 제공한다. 움직이는 부품 수가 적어 제조 비용을 절감할 수 있고, 고장 가능성이 낮아 신뢰성이 높으며, 유지보수도 훨씬 간단하다. 또한 동일한 구동 모듈을 여러 제품에서 공통으로 사용할 수 있어 개발 비용과 생산 비용을 동시에 줄일 수 있다.

차체(Chassis)는 모듈형 구조(Modular Structure)를 채택하였다. 배터리(Battery), 모터 드라이버(Motor Driver), 산업용 컴퓨터(Industrial Computer), 안전 제어기(Safety Controller), 통신 장치(Communication Module), 센서(Sensor)는 모두 표준 장착 인터페이스(Standard Mounting Interface)를 이용하여 구성하였다. 이를 통해 향후 새로운 하드웨어가 등장하더라도 전체 차체를 다시 설계하지 않고 일부 모듈만 교체할 수 있도록 하였다.

배터리 시스템(Battery Architecture) 역시 시스템 엔지니어링 관점에서 최적화하였다. 단순히 운행 시간을 늘리기 위해 배터리 용량을 크게 하는 것이 아니라, 차량 무게를 최소화하고 무게 중심(Center of Gravity)을 낮게 유지하면서도 실제 산업 현장에서 충분한 운용 시간을 확보하는 방향으로 설계하였다. 또한 기회 충전(Opportunity Charging)을 적극 활용하여 과도하게 큰 배터리의 필요성을 줄였다.

위치 추정(Localization) 역시 중요한 설계 요소였다. PB50과 PB100은 LiDAR 기반 위치 추정, 휠 오도메트리(Wheel Odometry), IMU를 결합하여 높은 자율주행 정확도를 확보하였다. 이를 통해 기계적인 정밀도를 지나치게 높이지 않더라도 소프트웨어 보정을 이용하여 산업용 수준의 위치 정확도를 달성할 수 있도록 설계하였다.

제조 확장성(Manufacturing Scalability)도 설계 단계에서 중요한 목표였다. 동일한 차체 부품(Common Structural Components), 동일한 전기 시스템(Common Electrical Architecture), 표준 하네스(Standard Wiring Harness), 공통 소프트웨어(Common Software Framework), 공통 진단 시스템(Common Diagnostic Tool)을 사용하여 여러 제품을 동일한 생산 라인에서 제조할 수 있도록 하였다.

상부 인터페이스(Upper Body Interface)는 또 하나의 핵심 설계 목표였다. 표준 기계 장착면(Standard Mechanical Mounting Pattern), 표준 전원 인터페이스(Power Interface), Ethernet 통신, 표준 API(Application Programming Interface)를 제공하여 컨베이어, 리프터(Lifter), 협동로봇(Collaborative Robot), 검사 장비(Inspection Equipment), 선반(Storage Rack) 등을 쉽게 장착할 수 있도록 하였다. 이를 통해 동일한 이동 플랫폼으로 매우 다양한 산업용 응용 제품을 개발할 수 있다.

경제성(Economics) 측면에서도 PB50과 PB100은 단순한 구매 가격이 아니라 생애주기 가치(Lifecycle Value)를 중요하게 고려하였다. 유지보수 비용 감소, 공통 예비 부품(Common Spare Parts), 공통 소프트웨어, 긴 제품 수명을 통해 장기간 운영 비용을 최소화하도록 설계하였다. 이러한 특성은 향후 수년 동안 점진적으로 플릿(Fleet)을 확장하려는 제조 기업에게 매우 큰 장점을 제공한다.

PB50과 PB100은 **적재 하중에 맞는 가장 합리적인 기술을 선택하는 것이 성공적인 산업용 AMR 설계의 핵심**이라는 점을 잘 보여준다. 차동 구동, 모듈형 구조, 표준 인터페이스, 확장 가능한 소프트웨어는 PB Series 전체를 구성하는 가장 중요한 기반 기술이 되었다.

---

### 5.2 PB250 이상 플랫폼 전환 연구(Transition Study for PB250 and Above)

적재 하중이 **250kg 이상**으로 증가하면 AMR 설계의 우선순위는 크게 변화한다. PB50과 PB100에서 사용한 많은 설계 원칙은 그대로 유지할 수 있지만, 차량 질량(Vehicle Mass)의 증가로 인해 기계적(Mechanical), 전기적(Electrical), 운영적(Operational) 측면에서 새로운 설계 검토가 필요하게 된다. 이러한 이유로 PB250은 Hills PB Series에서 매우 중요한 전환점(Transition Point)이 되는 플랫폼이다.

가장 먼저 검토해야 하는 요소는 구동 방식(Propulsion Technology)이다. 차동 구동은 여전히 높은 신뢰성과 경제성을 제공하지만, 적재 하중이 증가할수록 횡방향 미끄러짐(Lateral Slip), 조향 저항(Steering Resistance), 구동계 하중(Drivetrain Loading), 타이어 마모(Tire Wear)가 빠르게 증가한다. 특히 빈번한 회전, 정밀 도킹, 장시간 연속 운전에서는 이러한 문제가 더욱 크게 나타난다.

PB250 이상의 플랫폼에서는 **적재 하중만으로 구동 방식을 결정해서는 안 된다.** 실제 설계에서는 적재 하중(Payload), 작업 주기(Duty Cycle), 회전 빈도(Turning Frequency), 요구 도킹 정밀도(Docking Accuracy), 바닥 상태(Floor Condition), 운행 속도(Operating Speed), 에너지 효율(Energy Efficiency), 유지보수 능력(Maintenance Capability), 총 소유 비용(Total Cost of Ownership, TCO)을 함께 고려해야 한다.

직선 이동이 많고 회전이 비교적 적은 공장에서는 **300\~500kg 수준까지도 차동 구동이 충분한 경쟁력을 유지할 수 있다.** LiDAR 기반 위치 추정, 지능형 경로 계획, 견고한 기계 설계가 결합되면 타이어 미끄러짐과 오도메트리 오차를 상당 부분 보완할 수 있기 때문이다.

그러나 좁은 통로(Narrow Aisle), 반복적인 팔레트 운반(Pallet Handling), 고정밀 공작기계 로딩(Machine Loading), 다교대 연속 운전(Multi-Shift Continuous Operation)에서는 스티어 드라이브가 점점 더 유리해진다. 스티어 드라이브는 바퀴 방향을 능동적으로 제어하여 횡방향 미끄러짐을 거의 제거할 수 있으므로 회전 저항이 감소하고 에너지 효율이 향상되며 도킹 반복 정밀도도 높아진다. 또한 장기적으로 타이어 교체 비용도 크게 감소한다.

PB250 전환 연구에서는 **플랫폼 공통성(Maximum Platform Commonality)** 을 최대한 유지하면서 구동계만 독립적으로 발전시키는 전략을 권장한다. 전기 시스템(Electrical System), 소프트웨어 프레임워크(Software Framework), 배터리 기술(Battery Technology), 안전 시스템(Safety Architecture), 플릿 관리(Fleet Management), 위치 추정(Localization), 진단 시스템(Diagnostic Tool), 통신 인터페이스(Communication Interface)는 가능한 한 PB50 및 PB100과 동일하게 유지한다. 반면 조향 모듈(Steering Module), 휠 모듈(Wheel Module), 운동학 제어기(Kinematic Controller), 서스펜션(Suspension)과 같은 구동 관련 부품만 새롭게 설계한다.

이러한 모듈형 전환 전략(Modular Transition Strategy)은 상업적으로도 큰 장점을 가진다. 기존 PB50과 PB100을 사용하는 고객은 운영자 교육이나 소프트웨어를 거의 변경하지 않고 PB250 이상의 플랫폼을 추가할 수 있다. 하나의 플릿 관리 시스템에서 차동 구동과 스티어 드라이브를 동시에 운영하는 것도 가능하다.

향후 PB500, PB800, PB1200과 같은 더욱 큰 플랫폼도 동일한 철학으로 개발할 수 있다. 공통 소프트웨어(Common Software), 공통 전자 시스템(Common Electronics), 공통 안전 시스템(Common Safety Architecture)을 유지하면서 적재 하중에 맞는 구동 방식을 선택하는 것이다.

제조 측면에서도 표준 인터페이스(Standard Interface)는 큰 장점을 제공한다. 동일한 생산 라인에서 여러 종류의 차량을 조립할 수 있으며, 예비 부품 관리도 단순해진다. 개발 인력 역시 전체 차량을 새롭게 설계하기보다 적재 하중에 맞는 기계 시스템만 최적화하면 되므로 개발 효율이 크게 향상된다.

결론적으로 PB250은 단순히 PB100을 크게 만든 모델이 아니라, **구동 방식이 응용 분야(Application)에 따라 달라지는 새로운 설계 영역(New Engineering Optimization Region)의 시작점**이다. 차동 구동은 여전히 많은 중형 산업용 물류 환경에서 가장 경제적인 선택이며, 적재 하중과 회전 빈도, 정밀도 요구가 더욱 증가할수록 스티어 드라이브가 점차 더 적합한 선택이 된다.

Hills PB Series는 이러한 기술 로드맵(Technology Roadmap)을 기반으로 **명확한 공학적·경제적 근거가 있을 때만 구동 방식을 발전시키고**, 나머지 플랫폼 생태계(Platform Ecosystem)는 최대한 공통으로 유지하는 전략을 채택한다. 이러한 접근 방식은 제품의 지속적인 진화(Sustainable Product Evolution)를 가능하게 하며, 고객의 시스템 전환 비용(Migration Cost)을 최소화하고, 차세대 산업용 자율주행 모바일 로봇을 위한 유연한 플랫폼 기반(Flexible Platform Foundation)을 제공한다.
