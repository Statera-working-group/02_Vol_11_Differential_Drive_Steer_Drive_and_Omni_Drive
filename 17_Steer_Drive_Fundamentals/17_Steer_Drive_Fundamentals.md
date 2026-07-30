**Differential Drive & Steer Drive Engineering**


# Chapter 17 Steer Drive Fundamentals

##  

## 01 Steer drive principle steering axis and drive axis separation

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Separation of Steering Axis and Drive Axis

The fundamental concept of a steer drive system lies in the physical and functional separation of the steering axis and the drive axis. Unlike differential drive systems, where the same wheel simultaneously generates propulsion and turning by varying the rotational speeds of the left and right wheels, a steer drive system assigns these two functions to independent mechanisms. This architectural separation allows each wheel module to determine its own steering direction while independently controlling its driving torque, resulting in significantly higher maneuverability, positioning accuracy, and dynamic flexibility.

The steering axis is responsible for determining the orientation of the wheel relative to the robot chassis. A dedicated steering actuator rotates the entire wheel assembly around a vertical axis, enabling the wheel to point toward virtually any desired direction. Once the desired steering angle has been established, a separate drive motor generates the traction force necessary to propel the robot in that direction. Because steering and propulsion are mechanically isolated, each actuator can be optimized for its own purpose without compromising the performance of the other.

This separation fundamentally changes how motion is generated. In a differential drive robot, turning requires intentional speed differences between the left and right wheels, inevitably producing tire scrubbing, lateral slip, and rotational energy losses. During sharp turns, significant friction is generated because the wheels are forced to slide sideways against the floor. This not only increases tire wear but also limits positioning accuracy and smoothness of motion, particularly for heavy industrial platforms.

In contrast, a steer drive module aligns the wheel orientation with the intended direction of travel before applying traction. Since the wheel rolls along its natural rolling direction rather than being dragged sideways, lateral tire slip is greatly reduced. Rolling resistance remains the dominant friction component, allowing smoother acceleration, lower energy consumption, and considerably less mechanical wear. These characteristics become increasingly important as payload increases beyond several hundred kilograms.

The mechanical implementation of steering-drive separation typically consists of a steering bearing, steering gearbox, steering motor, drive motor, reduction gearbox, wheel hub, and encoder system. The steering bearing supports the entire vertical load while allowing continuous rotation around the steering axis. The drive motor is mounted concentrically or offset depending on the mechanical design philosophy and transfers torque through an integrated gearbox directly to the wheel. Absolute encoders continuously measure steering orientation, while incremental or absolute encoders on the drive motor provide wheel velocity and travel distance feedback.

Modern steer drive modules often employ hollow-shaft structures to simplify cable routing and improve structural rigidity. Electrical wiring for motors, encoders, brakes, and sensors passes through the center of the steering axis, minimizing cable twisting during repeated steering motions. Some manufacturers incorporate slip rings or rotary joints to enable unlimited steering rotation, whereas others impose steering angle limits of approximately ±180 degrees to simplify cable management and improve reliability.

The separation of steering and drive axes also enables advanced motion planning algorithms. Since steering direction and propulsion are independently controllable variables, the robot controller can calculate steering angles that minimize unnecessary rotation while simultaneously optimizing wheel velocities. Instead of simply commanding translational and rotational velocities, the controller solves a complete inverse kinematics problem in which every wheel receives an optimized steering target and drive velocity. This greatly expands the feasible motion space compared with conventional non-holonomic vehicles.

Another major advantage is the reduction of internal mechanical stress during low-speed precision maneuvers. Heavy industrial AMRs frequently perform docking operations with positioning tolerances below ±20 mm. Differential drive robots often struggle to achieve such repeatability because final alignment requires repeated skid-based corrections. A steer drive robot, however, simply rotates its steering modules to align with the required direction and performs smooth linear corrections without generating excessive side loads. This capability is particularly valuable in automated charging stations, machine tending, pallet transfer, semiconductor manufacturing, and automated inspection systems where repeatable positioning is essential.

Steering-drive separation also improves dynamic stability during acceleration and deceleration. Because the wheel orientation continuously follows the planned trajectory, lateral tire forces remain relatively small even when carrying heavy payloads exceeding one ton. Lower lateral forces reduce vibration transmission into the chassis, decrease structural fatigue, and improve sensor stability for cameras, LiDARs, and precision inspection equipment mounted on the vehicle.

The architecture further enhances redundancy and fault tolerance. Since each steering module contains its own steering and propulsion actuators, failures can often be isolated to a single module without immediately disabling the entire vehicle. Advanced control algorithms may redistribute torque among the remaining modules to maintain limited mobility until maintenance can be performed. Such distributed functionality contributes to higher operational availability in industrial environments where production downtime carries substantial economic costs.

From a control perspective, steering-drive separation introduces additional complexity because steering angle synchronization must be coordinated with wheel velocity generation. Every steering movement must reach its target orientation before significant driving torque is applied to avoid unnecessary tire scrub or transient instability. Consequently, modern steer drive systems rely on high-speed real-time communication networks such as EtherCAT to synchronize multiple servo drives with sub-millisecond timing accuracy. This precise coordination enables smooth transitions between forward motion, lateral movement, diagonal travel, and zero-radius rotation while maintaining consistent vehicle dynamics.

Ultimately, separating the steering axis from the drive axis transforms the mobile robot from a simple non-holonomic vehicle into a highly flexible motion platform capable of executing complex trajectories with exceptional precision. The additional mechanical complexity is compensated by substantial improvements in maneuverability, tire life, positioning repeatability, energy efficiency, and operational versatility, making steer drive systems the preferred solution for medium- and heavy-duty industrial AMRs.

---

### 1.2 Independent Module Configuration

A defining characteristic of modern steer drive systems is the adoption of independently controlled wheel modules. Rather than constructing the vehicle around a centralized drivetrain with mechanical linkages, each wheel assembly is designed as a fully integrated electromechanical module capable of performing steering, propulsion, sensing, braking, and local control functions independently. This modular architecture provides exceptional scalability, simplifies mechanical integration, and enables sophisticated motion capabilities that would be difficult or impossible to achieve using conventional drive systems.

Each independent module generally consists of a steering servo motor, steering gearbox, steering bearing assembly, drive motor, planetary or harmonic reduction gearbox, wheel hub, brake mechanism, steering encoder, drive encoder, temperature sensors, and communication interface. These components are packaged into a compact unit that can be mounted directly onto the robot chassis with standardized mechanical and electrical interfaces. Because every module is self-contained, manufacturers can reuse the same module design across multiple robot models with different payload capacities or chassis dimensions.

The modular approach significantly simplifies product development. Instead of designing an entirely new drivetrain for every robot size, engineers can select an appropriate number of standardized modules and integrate them into different chassis configurations. Four-module layouts dominate industrial AMRs because they provide excellent stability, load distribution, and omnidirectional motion capability. Six-wheel or eight-wheel configurations can also be realized using the same design philosophy for very heavy autonomous transport platforms carrying several tons of payload.

Independent modules enable complete decentralization of vehicle motion generation. Each wheel independently determines its steering angle and drive speed according to commands generated by the central motion controller. The controller continuously calculates the desired motion of the entire robot, decomposes that motion into individual wheel commands using inverse kinematic equations, and distributes synchronized reference values to every module through a deterministic real-time communication network.

One of the greatest benefits of this architecture is its flexibility. The same hardware can execute a wide variety of motion patterns simply by changing software parameters. During conventional forward driving, all steering modules align parallel to the longitudinal axis while the drive motors rotate at identical speeds. During crab motion, every wheel turns to the same steering angle so that the entire vehicle translates sideways without changing orientation. During zero-radius rotation, each module points tangentially to a virtual circle centered within the chassis while the drive motors rotate at coordinated speeds to generate pure rotational motion. Diagonal translation combines synchronized steering and propulsion to move simultaneously along both longitudinal and lateral directions.

Independent module configuration also improves load distribution across the chassis. Because every module actively contributes to propulsion, the available traction force is shared among multiple wheels instead of concentrating stress on only two drive wheels. This balanced distribution reduces tire loading, minimizes floor pressure, improves climbing performance on ramps, and enhances stability during acceleration and braking. The architecture is particularly advantageous for heavy industrial robots carrying expensive payloads such as semiconductor equipment, precision inspection systems, automotive battery packs, or large manufacturing components.

Mechanical maintenance benefits substantially from modularization. Individual wheel modules can often be replaced without dismantling the entire chassis, reducing maintenance time and minimizing production downtime. Preventive maintenance schedules become easier to implement because identical spare modules can be stocked and exchanged rapidly in the field. This modular replacement philosophy also reduces lifecycle costs by simplifying inventory management and shortening repair procedures.

Independent modules further facilitate scalability across product families. A manufacturer may employ identical steering modules in robots ranging from 500 kg payload platforms to 1.5-ton heavy-duty systems, differing primarily in gearbox ratios, wheel diameters, motor ratings, and structural reinforcement. Such component standardization reduces engineering effort, manufacturing cost, certification complexity, and software validation time while increasing production volume for common parts.

The distributed architecture naturally complements modern industrial communication technologies. EtherCAT is widely adopted because it provides deterministic synchronization among multiple servo drives with extremely low communication latency. Each module operates as an intelligent EtherCAT slave capable of executing local servo loops while receiving high-level commands from the central motion controller. This layered control structure combines centralized trajectory planning with decentralized actuator execution, achieving both computational efficiency and high dynamic performance.

Safety is also enhanced by independent module configuration. Each module can monitor its own motor temperature, encoder status, brake condition, communication integrity, and electrical current. Diagnostic information is continuously transmitted to the supervisory controller, allowing predictive maintenance algorithms to identify abnormal operating conditions before failures occur. In the event of a fault, affected modules can enter a controlled safe state while the remaining modules continue operating under degraded functionality, depending on system design and applicable safety requirements.

From a manufacturing perspective, standardized modules shorten assembly time because electrical wiring, gearbox alignment, encoder calibration, and brake adjustment are completed before installation onto the vehicle chassis. Final assembly primarily involves mounting the modules, connecting power and communication cables, and performing software calibration. This modular manufacturing process improves production consistency and facilitates automated quality inspection.

As industrial AMRs continue evolving toward higher payload capacities and greater autonomy, independent steer drive modules are becoming the preferred architectural foundation for next-generation mobile robots. Their combination of mechanical flexibility, software scalability, maintenance efficiency, precise motion control, and system reliability provides a robust platform capable of supporting increasingly demanding industrial applications. For heavy-duty autonomous vehicles requiring precise positioning, multidirectional movement, and long-term operational durability, the independent module configuration represents one of the most effective engineering solutions currently available.

---

### 1.1 조향축(Steering Axis)과 구동축(Drive Axis)의 분리 (Separation of Steering Axis and Drive Axis)

스티어 드라이브(Steer Drive) 시스템의 가장 근본적인 개념은 **조향축(Steering Axis)**과 **구동축(Drive Axis)**을 기계적으로 그리고 기능적으로 완전히 분리하는 것이다. 차동 구동(Differential Drive) 시스템에서는 동일한 바퀴가 추진력과 조향 기능을 동시에 수행하며, 좌우 바퀴의 회전 속도 차이를 이용하여 방향을 변경한다. 반면 스티어 드라이브 시스템에서는 이 두 기능을 서로 독립된 메커니즘에 할당한다. 이러한 구조적 분리는 각 바퀴 모듈이 자신의 조향 방향을 자유롭게 결정하면서 동시에 독립적으로 구동 토크를 생성할 수 있도록 하여 훨씬 높은 기동성, 위치 정밀도 및 동적 유연성을 제공한다.

조향축은 바퀴가 차체에 대해 어떤 방향을 향할 것인지를 결정하는 역할을 담당한다. 전용 조향 액추에이터는 바퀴 전체를 수직축을 중심으로 회전시키며 원하는 각도로 조향한다. 이후 별도의 구동 모터가 해당 방향으로 추진력을 발생시켜 차량을 이동시킨다. 조향과 구동이 완전히 독립되어 있기 때문에 각각의 액추에이터는 자신의 목적에 맞게 최적화될 수 있으며, 서로의 성능을 저하시킬 필요가 없다.

이러한 구조는 이동 방식 자체를 근본적으로 변화시킨다. 차동 구동에서는 회전을 위해 좌우 바퀴의 속도 차이를 반드시 발생시켜야 하며, 이 과정에서 타이어 미끄러짐(Skid), 횡방향 슬립(Lateral Slip), 회전 에너지 손실이 발생한다. 특히 급회전 시에는 바퀴가 바닥을 옆으로 끌리면서 움직이므로 상당한 마찰력이 발생하고, 이는 타이어 마모를 증가시키며 위치 정밀도를 떨어뜨리는 원인이 된다. 이러한 문제는 중량이 증가할수록 더욱 심각해진다.

반면 스티어 드라이브는 먼저 바퀴를 이동하려는 방향으로 정확하게 조향한 후 추진력을 발생시킨다. 따라서 바퀴는 자신의 회전 방향 그대로 굴러가기 때문에 횡방향 미끄러짐이 크게 감소한다. 마찰의 대부분은 구름 저항(Rolling Resistance)으로 제한되며, 보다 부드러운 가속과 감속이 가능하고 에너지 소비도 감소한다. 또한 기계적인 마모가 현저히 줄어들기 때문에 수백 킬로그램 이상의 산업용 AMR에서는 매우 큰 장점으로 작용한다.

기계적인 구성은 일반적으로 조향 베어링(Steering Bearing), 조향 기어박스(Steering Gearbox), 조향 모터(Steering Motor), 구동 모터(Drive Motor), 감속기(Reduction Gearbox), 휠 허브(Wheel Hub), 엔코더(Encoder) 등으로 이루어진다. 조향 베어링은 차량의 수직 하중을 지지하면서도 조향축을 중심으로 회전할 수 있도록 한다. 구동 모터는 감속기를 거쳐 직접 바퀴에 토크를 전달하며, 조향축과 동축 구조(Coaxial Structure) 또는 오프셋 구조(Offset Structure)로 설계될 수 있다. 절대형 엔코더(Absolute Encoder)는 조향 각도를 지속적으로 측정하고, 구동 모터에는 증분형 엔코더(Incremental Encoder) 또는 절대형 엔코더가 장착되어 속도와 이동 거리를 계산한다.

최근의 스티어 드라이브 모듈은 중공축(Hollow Shaft) 구조를 많이 채택한다. 모터, 브레이크, 엔코더 및 각종 센서의 케이블을 조향축 내부로 통과시켜 반복적인 조향에도 케이블 꼬임을 최소화할 수 있기 때문이다. 일부 제조사는 슬립링(Slip Ring)이나 회전 조인트(Rotary Joint)를 적용하여 무한 회전을 지원하며, 다른 시스템은 케이블 신뢰성을 높이기 위해 약 ±180도의 조향 범위를 사용하는 경우도 있다.

조향축과 구동축을 분리하면 보다 진보된 운동 계획(Motion Planning) 알고리즘을 적용할 수 있다. 제어기는 각 바퀴의 조향각과 회전 속도를 독립적으로 계산하여 불필요한 조향 회전을 최소화하면서도 최적의 이동 경로를 생성한다. 즉 단순히 선속도와 각속도를 명령하는 것이 아니라 각 바퀴에 대해 최적의 조향각과 구동 속도를 계산하는 역기구학(Inverse Kinematics) 문제를 실시간으로 해결하게 된다. 그 결과 기존의 비홀로노믹(Non-Holonomic) 차량보다 훨씬 넓은 운동 자유도를 확보할 수 있다.

또한 저속 정밀 제어에서도 매우 큰 장점을 가진다. 산업용 AMR은 ±20 mm 이하의 도킹(Docking) 정밀도를 요구하는 경우가 많다. 차동 구동은 최종 위치를 맞추기 위해 반복적으로 미끄러짐을 이용한 보정을 수행해야 하지만, 스티어 드라이브는 바퀴 방향을 원하는 방향으로 회전시킨 후 직선 이동만으로 미세한 위치 보정을 수행할 수 있다. 이러한 특성은 자동 충전기(Auto Charging Station), 공작기계 로딩(Machine Tending), 팔레트 이송(Pallet Transfer), 반도체 제조(Semiconductor Manufacturing), 자동 검사 시스템(Automated Inspection System) 등에서 매우 중요한 장점이 된다.

조향과 구동의 분리는 가속과 감속 시의 동적 안정성도 향상시킨다. 바퀴가 항상 계획된 이동 방향을 향하고 있기 때문에 횡력이 크게 감소하며, 1톤 이상의 중량물을 운반할 때에도 진동 전달이 줄어든다. 이는 차체 피로를 감소시키고 카메라(Camera), 라이다(LiDAR), 정밀 검사 장비 등의 안정성을 향상시키는 효과를 가져온다.

독립적인 구조는 시스템의 신뢰성과 고장 허용성(Fault Tolerance)도 향상시킨다. 각 모듈은 자신의 조향과 구동 기능을 모두 가지고 있기 때문에 하나의 모듈에 문제가 발생하더라도 나머지 모듈이 제한적인 이동 기능을 유지하도록 설계할 수 있다. 이러한 분산 구조는 생산 라인의 가동 중단 시간을 최소화하는 데 중요한 역할을 한다.

제어 측면에서는 조향과 구동을 동시에 동기화해야 하므로 시스템이 다소 복잡해진다. 각 바퀴는 목표 조향각에 먼저 도달한 후 충분한 구동 토크를 발생시켜야 타이어 미끄러짐을 최소화할 수 있다. 이를 위해 대부분의 산업용 스티어 드라이브 시스템은 이더캣(EtherCAT)과 같은 고속 실시간 통신망을 사용하여 서브밀리초(Sub-millisecond) 수준의 정밀한 동기화를 수행한다. 이러한 정밀한 제어 덕분에 전진, 후진, 크랩 주행(Crab Motion), 대각선 이동(Diagonal Motion), 제자리 회전(Zero Radius Rotation)을 매우 부드럽게 수행할 수 있다.

결국 조향축과 구동축의 분리는 단순한 이동 차량을 다양한 방향으로 자유롭게 움직일 수 있는 고성능 이동 플랫폼으로 변화시키는 핵심 기술이다. 비록 기계 구조는 복잡해지지만 기동성, 타이어 수명, 위치 반복 정밀도, 에너지 효율, 유지보수성 및 산업 적용 범위가 크게 향상되므로, 중대형 산업용 AMR에서는 가장 널리 채택되는 구동 방식으로 자리 잡고 있다.

---

### 1.2 독립 모듈 구성 (Independent Module Configuration)

현대 스티어 드라이브 시스템의 가장 큰 특징 가운데 하나는 **독립 모듈 구성(Independent Module Configuration)**을 채택한다는 점이다. 기존 차량처럼 하나의 중앙 구동계를 여러 바퀴가 공유하는 방식이 아니라, 각각의 바퀴를 하나의 완전한 전기·기계 통합 모듈(Electromechanical Module)로 설계한다. 각 모듈은 조향, 구동, 제동, 센싱 및 로컬 제어 기능을 모두 독립적으로 수행할 수 있으며, 이러한 구조는 높은 확장성, 우수한 유지보수성 및 뛰어난 운동 성능을 제공한다.

각 독립 모듈은 일반적으로 조향 서보 모터(Steering Servo Motor), 조향 기어박스(Steering Gearbox), 조향 베어링(Steering Bearing), 구동 모터(Drive Motor), 유성 감속기(Planetary Gearbox) 또는 하모닉 감속기(Harmonic Gearbox), 휠 허브(Wheel Hub), 브레이크(Brake), 조향 엔코더(Steering Encoder), 구동 엔코더(Drive Encoder), 온도 센서(Temperature Sensor), 통신 인터페이스(Communication Interface) 등을 하나의 패키지로 통합한다. 이 모듈은 표준화된 기계 및 전기 인터페이스를 통해 차체(Frame)에 직접 장착된다.

이러한 모듈화는 제품 개발을 크게 단순화한다. 제조사는 새로운 플랫폼을 설계할 때마다 새로운 구동계를 개발할 필요 없이 동일한 모듈을 다양한 차체 크기와 적재 용량에 맞추어 반복 사용할 수 있다. 대부분의 산업용 AMR은 네 개의 모듈을 사용하지만, 수 톤급 물류 차량에서는 여섯 개 또는 여덟 개의 동일한 모듈을 사용하는 구조도 쉽게 구현할 수 있다.

독립 모듈은 차량의 운동을 완전히 분산된 방식으로 생성한다. 중앙 제어기는 차량 전체의 목표 움직임을 계산한 후 이를 역기구학(Inverse Kinematics)을 이용하여 각 바퀴의 조향각과 속도로 변환한다. 이후 모든 모듈은 이더캣(EtherCAT)과 같은 실시간 통신망을 통해 동기화된 명령을 받아 자신의 동작을 수행한다.

이 구조의 가장 큰 장점은 동일한 하드웨어로 매우 다양한 움직임을 구현할 수 있다는 것이다. 일반적인 직진에서는 모든 바퀴가 전방을 향하고 동일한 속도로 회전한다. 크랩 주행에서는 모든 바퀴가 동일한 각도로 회전하여 차체 방향을 유지한 채 측면으로 이동한다. 제자리 회전에서는 각 바퀴가 차량 중심을 향하는 접선 방향으로 조향되고 서로 다른 속도로 회전하여 차체만 회전한다. 대각선 이동에서는 조향과 속도를 동시에 제어하여 하나의 연속된 움직임을 생성한다.

독립 모듈은 하중 분산에도 큰 장점을 제공한다. 모든 바퀴가 추진력을 생성하므로 특정 바퀴에 하중이 집중되지 않으며, 접지력이 균등하게 분배된다. 이는 경사로 주행 능력을 향상시키고 제동 안정성을 높이며 바닥에 전달되는 압력을 감소시킨다. 특히 반도체 장비, 정밀 검사 장비, 자동차 배터리 및 대형 제조 부품과 같은 고가의 중량물을 운반하는 산업용 AMR에서는 매우 중요한 설계 요소이다.

유지보수 측면에서도 모듈화는 큰 이점을 제공한다. 고장이 발생한 모듈만 빠르게 교체할 수 있으므로 전체 차량을 분해할 필요가 없다. 또한 동일한 예비 모듈을 재고로 보유할 수 있어 유지보수 시간이 단축되고 운영 비용도 감소한다.

독립 모듈은 제품군(Product Family)의 확장에도 매우 유리하다. 동일한 모듈을 기반으로 감속비, 휠 직경, 모터 출력 및 구조 강성만 변경하면 500 kg급부터 1.5톤 이상의 중량 플랫폼까지 다양한 제품을 개발할 수 있다. 이러한 표준화(Standardization)는 개발 비용과 생산 비용을 줄이고 인증(Certification) 및 소프트웨어 검증 과정도 단순화한다.

이러한 구조는 현대 산업용 통신 시스템과도 매우 잘 결합된다. 대부분의 시스템은 이더캣(EtherCAT)을 사용하여 여러 개의 서보 드라이브를 매우 낮은 지연 시간으로 동기화한다. 각 모듈은 독립적인 서보 제어를 수행하는 지능형 슬레이브(Intelligent Slave) 역할을 수행하며, 중앙 제어기는 전체 경로 계획(Trajectory Planning)과 운동 생성만 담당한다. 이러한 계층형 제어 구조(Hierarchical Control Structure)는 계산 효율성과 운동 성능을 동시에 향상시킨다.

안전성 또한 크게 향상된다. 각 모듈은 모터 온도, 엔코더 상태, 브레이크 상태, 통신 오류, 전류 등을 지속적으로 감시하며, 이상이 발생하면 진단 정보를 중앙 제어기로 전달한다. 예지보전(Predictive Maintenance) 알고리즘은 이러한 데이터를 분석하여 실제 고장이 발생하기 전에 이상 징후를 발견할 수 있으며, 일부 시스템은 고장 모듈만 안전 상태(Safe State)로 전환한 뒤 나머지 모듈만으로 제한적인 운행을 계속 수행할 수도 있다.

생산 공정에서도 모듈화는 큰 효과를 가져온다. 모터 배선, 감속기 조립, 엔코더 보정 및 브레이크 조정이 모두 모듈 단계에서 완료되므로 최종 조립은 차체에 모듈을 장착하고 전원 및 통신 케이블만 연결하면 된다. 따라서 생산 품질이 균일해지고 자동화된 품질 검사도 용이해진다.

산업용 AMR이 점점 더 높은 적재 용량과 높은 자율성을 요구하는 방향으로 발전함에 따라, 독립 스티어 드라이브 모듈은 차세대 이동 로봇의 핵심 아키텍처로 자리 잡고 있다. 기계적 유연성, 소프트웨어 확장성, 유지보수 효율성, 정밀한 운동 제어 및 높은 신뢰성을 동시에 제공하는 이 구조는 앞으로의 고성능 산업용 자율주행 플랫폼에서 가장 중요한 설계 방식 중 하나가 될 것으로 예상된다.

##  

## 02 Drive and steering separation

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Drive Motor Role

The drive motor is the primary source of propulsion in a steer drive system and is responsible for generating the tractive force that moves the mobile robot. Unlike differential drive systems, where the same wheel simultaneously contributes to both propulsion and steering through speed differences between the left and right wheels, a steer drive system clearly separates these responsibilities. The steering motor determines the wheel orientation, while the drive motor produces the torque required to move the vehicle in the commanded direction. This functional separation allows each actuator to be optimized independently, resulting in higher efficiency, improved controllability, and superior overall vehicle performance.

The most fundamental responsibility of the drive motor is to convert electrical energy into mechanical torque. Electrical power supplied from the battery is processed by the motor driver through precise current regulation before being delivered to the motor windings. The resulting electromagnetic torque is transmitted through the reduction gearbox to the wheel hub, producing the traction force necessary to propel the robot. The magnitude of this traction force directly determines the robot\'s ability to accelerate, climb slopes, transport heavy payloads, and maintain stable motion under varying operating conditions.

Since the steering mechanism continuously aligns the wheel with the desired travel direction, the drive motor operates primarily under rolling conditions rather than sliding conditions. Consequently, nearly all of the motor torque contributes directly to forward propulsion instead of being wasted overcoming lateral tire scrub. This significantly improves drivetrain efficiency compared with differential drive platforms, particularly during low-speed maneuvering and precision positioning operations.

Modern steer drive systems almost exclusively employ servo motors or high-performance brushless DC motors as drive actuators. Servo motors are particularly well suited for industrial autonomous mobile robots because they provide excellent torque density, wide speed control range, high positioning accuracy, and rapid dynamic response. Permanent magnet synchronous motors are frequently selected for medium and heavy-duty applications because they maintain high efficiency across a broad operating range while delivering stable torque at both low and high rotational speeds.

The drive motor must satisfy several distinct operating conditions throughout the robot\'s mission cycle. During startup, it must generate sufficient peak torque to overcome static friction and inertial resistance. During normal transportation, it must provide stable continuous torque while maintaining energy efficiency. During acceleration, it must rapidly increase wheel speed without introducing excessive vibration or wheel slip. During deceleration, it must either dissipate kinetic energy through braking or recover energy through regenerative braking when supported by the motor driver and battery management system.

Motor sizing therefore requires careful consideration of multiple performance parameters. Engineers evaluate the total moving mass, desired acceleration, maximum vehicle speed, rolling resistance, slope climbing requirements, drivetrain efficiency, safety factors, and duty cycle before selecting an appropriate motor. Peak torque capability is generally determined by the worst-case acceleration or ramp-climbing scenario, while continuous torque is based on sustained operating conditions over extended mission durations.

One important characteristic of the drive motor is its contribution to vehicle stability. Since every steer drive module independently generates propulsion, the central controller distributes the required traction force among multiple drive motors. Instead of relying on only two powered wheels, as in differential drive systems, a four-wheel steer drive distributes driving torque across all modules. This balanced force distribution improves traction, reduces individual wheel loading, minimizes tire wear, and enhances stability during both acceleration and braking.

The drive motor also plays a significant role in maintaining path tracking accuracy. Small differences in wheel velocity among individual modules can gradually accumulate into positioning errors if left uncompensated. High-resolution motor encoders continuously measure rotational speed and travel distance, allowing closed-loop servo controllers to maintain extremely accurate wheel velocity. Feedback from encoders is combined with inertial measurement units, LiDAR localization systems, visual localization, or simultaneous localization and mapping algorithms to achieve highly accurate navigation over long travel distances.

Another essential function of the drive motor is enabling smooth motion transitions. Industrial AMRs frequently switch between transportation mode, precision docking mode, inspection mode, and charging mode. Each operating mode requires different acceleration limits, velocity profiles, and torque characteristics. During high-speed transportation, the drive motor emphasizes efficiency and smooth acceleration. During final docking operations, the controller commands extremely low wheel speeds while maintaining high torque resolution, allowing the robot to position itself within millimeter-level tolerances without oscillation or overshoot.

Thermal performance is another critical aspect of drive motor operation. Heavy-duty autonomous mobile robots often transport payloads exceeding one ton while operating continuously for many hours. Such applications generate substantial heat inside the motor windings and permanent magnets. Excessive temperature reduces motor efficiency, accelerates insulation aging, and may permanently damage magnetic materials. Therefore, thermal sensors embedded within the motor continuously monitor winding temperature and communicate with the motor controller. When thermal limits are approached, torque derating or temporary speed reduction strategies are automatically applied to protect the hardware while maintaining safe operation.

Energy efficiency has become an increasingly important design objective for modern industrial AMRs. Every watt consumed by the drive motor directly affects battery capacity requirements, operating time, and charging frequency. High-efficiency motors with optimized magnetic circuits, precision bearings, and low-loss power electronics significantly reduce overall energy consumption. Advanced field-oriented control algorithms further improve efficiency by minimizing current losses while maintaining precise torque production across the entire speed range.

Safety functions are closely integrated with the drive motor as well. Modern industrial servo drives incorporate certified safety functions such as Safe Torque Off, Safe Stop 1, Safely Limited Speed, and Safe Brake Control. During emergency conditions, the drive motor immediately ceases torque generation while coordinated braking mechanisms safely decelerate the vehicle without compromising stability. Integration of these safety functions is essential for compliance with international machinery safety standards governing autonomous industrial vehicles.

The drive motor additionally contributes to predictive maintenance through continuous condition monitoring. Parameters including motor current, winding temperature, vibration level, encoder quality, bearing condition, and operating hours are recorded throughout the robot\'s lifetime. These data allow maintenance software to identify gradual degradation before functional failures occur, reducing unexpected downtime and improving overall fleet availability.

As industrial mobile robots continue evolving toward higher payload capacities and greater operational autonomy, the importance of the drive motor extends far beyond simple propulsion. It becomes an intelligent actuator responsible for force generation, energy management, safety implementation, thermal regulation, diagnostic monitoring, and precision motion execution. The drive motor therefore represents one of the most critical components within the steer drive architecture, directly influencing productivity, reliability, positioning accuracy, and total lifecycle cost.

---

### 2.2 Steering Motor Role

The steering motor is the actuator responsible for controlling the orientation of each steer drive module. While the drive motor generates propulsion, the steering motor determines the direction in which that propulsion is applied. This clear functional separation is one of the defining characteristics of steer drive architecture and enables motion capabilities that cannot be achieved by conventional differential drive systems. By continuously adjusting the steering angle of each wheel, the steering motor allows the robot to execute forward travel, reverse movement, crab motion, diagonal translation, and zero-radius rotation with exceptional precision.

The primary function of the steering motor is to rotate the wheel assembly around the vertical steering axis. Unlike automotive steering systems, which often rely on mechanical linkages connecting multiple wheels, each steer drive module possesses its own independent steering actuator. Every steering motor receives an individual steering angle command from the central controller and rotates the wheel until the measured angle precisely matches the target value. Once the desired orientation has been achieved, the drive motor produces propulsion in the aligned direction.

Steering accuracy directly influences overall vehicle positioning accuracy. Even a small steering angle error can produce noticeable lateral deviation after traveling several meters. For example, an angular error of only one degree may introduce several centimeters of positioning error during long-distance travel. Consequently, industrial steer drive systems employ high-resolution absolute encoders capable of measuring steering orientation with extremely fine angular resolution. Closed-loop servo control continuously compensates for disturbances, mechanical backlash, bearing compliance, and external loading to maintain accurate steering alignment throughout operation.

The steering motor typically operates under different dynamic requirements than the drive motor. Instead of generating continuous propulsion torque, it must repeatedly accelerate, decelerate, and precisely position the steering mechanism. Fast steering response improves maneuverability by reducing the transition time between different motion modes. However, excessively aggressive steering motion may generate unnecessary vibration or mechanical stress. Therefore, steering controllers employ carefully optimized motion profiles that balance response speed with smoothness and mechanical durability.

Torque requirements for the steering motor depend primarily on tire-floor friction, steering bearing preload, payload distribution, wheel diameter, and gearbox characteristics. During stationary steering, the motor must overcome the friction generated between the tire and floor while supporting the vertical vehicle load. For heavy industrial AMRs carrying payloads exceeding one ton, this steering resistance can become substantial. Designers therefore select appropriate gearbox reduction ratios and servo motors capable of delivering sufficient torque while maintaining accurate position control.

The steering motor enables one of the most distinctive features of steer drive systems: omnidirectional maneuverability using conventional wheels. During crab motion, all steering motors rotate their wheels to the same angle so that the robot translates laterally while maintaining constant orientation. During diagonal movement, every wheel adopts a common steering angle corresponding to the desired travel direction. During zero-radius rotation, each steering module points tangentially toward a virtual circle centered within the robot chassis, allowing the vehicle to rotate about its own center without translational displacement.

Coordinated steering synchronization is essential for smooth vehicle operation. Since four steering motors simultaneously determine the orientation of four independent wheel modules, all steering angles must reach their commanded positions within extremely small timing tolerances. Modern industrial systems therefore utilize deterministic communication protocols such as EtherCAT, allowing synchronized servo updates with sub-millisecond precision. This synchronization ensures that the drive motors only begin generating significant traction after the steering modules have reached their intended orientations.

Mechanical design considerations strongly influence steering motor performance. Many steer drive modules employ harmonic gearboxes or high-precision planetary gearboxes to achieve high reduction ratios with minimal backlash. Low backlash is particularly important because steering errors immediately translate into positioning errors during precision docking operations. High-rigidity bearing assemblies further improve steering stability by minimizing elastic deformation under heavy loads.

Absolute encoders are almost universally employed in steering systems because they preserve angle information even after power interruption. Unlike incremental encoders, absolute encoders eliminate the need for homing procedures during startup, enabling faster system initialization and preventing orientation errors after emergency shutdowns. Continuous angle feedback also allows the controller to detect abnormal steering behavior, excessive backlash, or unexpected mechanical resistance.

Energy consumption of the steering motor differs substantially from that of the drive motor. During long straight-line travel, steering motors consume relatively little energy because steering angles remain nearly constant. Their highest power demand occurs during transitions between motion modes, such as changing from forward travel to crab motion or rotating all wheels before precision docking. Consequently, steering motors generally contribute a smaller percentage of the overall vehicle energy budget despite their critical functional importance.

Safety functions are equally important within the steering subsystem. Loss of steering control may cause significant trajectory deviation or collision risk, particularly in confined industrial environments. Therefore, steering motors continuously monitor encoder signals, motor currents, servo position errors, communication status, and brake conditions. If abnormal behavior is detected, the system immediately enters a predefined safe state that prevents uncontrolled steering motion while coordinating with the drive motors to safely stop the vehicle.

Predictive maintenance strategies increasingly rely on steering motor diagnostic data. Servo current trends, steering torque demand, positioning accuracy, gearbox vibration, encoder quality indicators, and bearing friction measurements provide valuable insight into long-term mechanical health. Maintenance software analyzes these parameters to estimate component wear and recommend service before functional degradation affects robot performance.

From a system integration perspective, the steering motor represents the component that transforms a conventional wheeled platform into a highly maneuverable autonomous vehicle. Its ability to orient each wheel independently allows sophisticated motion planning algorithms to exploit the full kinematic capability of the steer drive architecture. Whether transporting heavy industrial payloads, performing precision machine loading, docking with automated charging stations, or positioning high-value inspection equipment, the steering motor provides the directional intelligence that makes precise multidirectional motion possible.

As autonomous mobile robots continue demanding higher positioning accuracy, greater payload capacity, and increasingly flexible navigation, steering motor technology will remain a key enabling factor. Improvements in servo bandwidth, encoder resolution, gearbox precision, communication synchronization, and intelligent diagnostics will further enhance maneuverability, reliability, and operational efficiency, reinforcing the steering motor\'s central role within next-generation steer drive systems.

---

### 2.1 구동 모터의 역할 (Drive Motor Role)

구동 모터(Drive Motor)는 스티어 드라이브(Steer Drive) 시스템에서 추진력을 생성하는 핵심 구동원이며, 이동 로봇을 실제로 움직이게 하는 가장 중요한 액추에이터이다. 차동 구동(Differential Drive)에서는 동일한 바퀴가 추진과 조향을 동시에 수행하기 위해 좌우 바퀴의 속도 차이를 이용하지만, 스티어 드라이브에서는 이러한 기능을 명확하게 분리한다. 조향 모터(Steering Motor)는 바퀴의 방향을 결정하고, 구동 모터는 그 방향으로 추진력을 발생시키는 역할만 수행한다. 이러한 기능적 분리는 각각의 액추에이터를 독립적으로 최적화할 수 있게 하며, 시스템 전체의 효율성, 제어 성능 및 주행 품질을 크게 향상시킨다.

구동 모터의 가장 기본적인 역할은 전기 에너지(Electrical Energy)를 기계적 토크(Mechanical Torque)로 변환하는 것이다. 배터리(Battery)에서 공급된 전력은 모터 드라이버(Motor Driver)의 정밀한 전류 제어를 거쳐 모터 권선(Winding)에 전달되고, 발생한 전자기 토크(Electromagnetic Torque)는 감속기(Reduction Gearbox)를 통해 휠 허브(Wheel Hub)로 전달된다. 최종적으로 바퀴는 노면과의 접촉을 통해 견인력(Traction Force)을 발생시키며 차량을 이동시킨다. 이 견인력은 차량의 가속 성능, 경사로 주행 능력, 중량물 운반 능력 및 다양한 환경에서의 주행 안정성을 결정하는 가장 중요한 요소이다.

스티어 드라이브에서는 조향 시스템이 먼저 바퀴를 목표 방향으로 정확하게 회전시키기 때문에 구동 모터는 대부분 순수한 구름 운동(Rolling Motion) 상태에서 추진력을 생성한다. 따라서 발생한 토크의 대부분이 실제 추진에 사용되며, 횡방향 마찰이나 타이어 끌림(Tire Scrub)에 소비되는 에너지가 크게 감소한다. 이는 특히 저속 정밀 주행이나 반복적인 도킹(Docking) 작업에서 차동 구동보다 훨씬 높은 구동 효율을 제공한다.

현대의 산업용 스티어 드라이브는 대부분 서보 모터(Servo Motor) 또는 고성능 브러시리스 직류 모터(Brushless DC Motor, BLDC)를 구동 모터로 사용한다. 특히 서보 모터는 높은 토크 밀도(Torque Density), 넓은 속도 제어 범위, 뛰어난 위치 제어 성능 및 빠른 응답 특성을 제공하기 때문에 산업용 자율주행 이동로봇(AMR)에 가장 많이 적용된다. 중량급 플랫폼에서는 영구자석 동기 모터(Permanent Magnet Synchronous Motor, PMSM)가 많이 사용되며, 저속과 고속 모두에서 안정적인 토크와 높은 효율을 유지할 수 있다.

구동 모터는 로봇의 운행 과정에서 다양한 조건을 만족해야 한다. 출발 시에는 정지 마찰(Static Friction)과 관성(Inertia)을 극복하기 위한 높은 순간 토크(Peak Torque)가 필요하며, 일반 주행에서는 높은 효율의 연속 토크(Continuous Torque)를 안정적으로 공급해야 한다. 가속 시에는 빠른 속도 증가를 지원하면서도 진동과 휠 슬립(Wheel Slip)을 최소화해야 하고, 감속 시에는 제동(Braking) 또는 회생 제동(Regenerative Braking)을 통해 운동 에너지를 효과적으로 처리해야 한다.

따라서 모터 선정(Motor Sizing)은 다양한 요소를 종합적으로 고려하여 이루어진다. 설계자는 총 이동 질량(Total Moving Mass), 목표 가속도(Target Acceleration), 최고 속도(Maximum Speed), 구름 저항(Rolling Resistance), 경사로 등판 조건(Slope Climbing Requirement), 구동계 효율(Drivetrain Efficiency), 안전 계수(Safety Factor), 운전 사이클(Duty Cycle) 등을 분석한 후 적절한 모터를 선정한다. 최대 토크는 최악의 운행 조건을 기준으로 결정되고, 연속 토크는 장시간 운행 조건을 기준으로 계산된다.

구동 모터는 차량의 주행 안정성에도 중요한 역할을 수행한다. 스티어 드라이브에서는 모든 바퀴가 독립적으로 추진력을 생성하기 때문에 중앙 제어기(Central Controller)는 필요한 견인력을 여러 개의 구동 모터에 균등하게 분배한다. 차동 구동처럼 두 개의 바퀴만 추진력을 담당하는 것이 아니라 네 개 이상의 바퀴가 동시에 구동에 참여하므로 접지력이 향상되고, 각 바퀴에 걸리는 하중이 감소하며, 타이어 마모도 줄어든다. 또한 가속과 감속 과정에서도 차량의 안정성이 크게 향상된다.

구동 모터는 경로 추종(Path Tracking) 성능에도 직접적인 영향을 준다. 각 바퀴의 속도에 작은 오차가 발생하면 장거리 주행 시 누적되어 위치 오차(Position Error)가 커질 수 있다. 이를 방지하기 위해 고해상도 엔코더(High Resolution Encoder)가 모터의 회전 속도와 이동 거리를 지속적으로 측정하며, 폐루프 제어(Closed Loop Control)를 통해 매우 정확한 속도 제어를 수행한다. 또한 엔코더 정보는 관성측정장치(IMU), 라이다 위치 인식(LiDAR Localization), 비전 기반 위치 인식(Visual Localization), 동시적 위치 추정 및 지도 작성(SLAM)과 융합되어 장거리에서도 높은 위치 정밀도를 유지한다.

구동 모터는 다양한 운행 모드 간의 전환도 담당한다. 산업용 AMR은 일반 운송 모드(Transportation Mode), 정밀 도킹 모드(Precision Docking Mode), 검사 모드(Inspection Mode), 자동 충전 모드(Charging Mode)를 반복적으로 수행한다. 각 모드마다 요구되는 가속도, 속도 및 토크 특성이 다르므로 제어기는 이에 맞는 속도 프로파일(Velocity Profile)을 생성한다. 고속 이동에서는 에너지 효율과 부드러운 가속을 우선하며, 정밀 도킹에서는 매우 낮은 속도에서도 높은 토크 분해능(Torque Resolution)을 유지하여 진동이나 오버슈트(Overshoot) 없이 밀리미터 수준의 위치 제어를 수행한다.

열 관리(Thermal Management)는 구동 모터에서 매우 중요한 요소이다. 1톤 이상의 중량물을 수 시간 동안 운반하는 산업용 AMR에서는 권선과 영구자석 내부에 상당한 열이 발생한다. 과도한 온도는 효율을 저하시킬 뿐 아니라 절연 재료의 수명을 단축시키고 자석 성능을 영구적으로 손상시킬 수도 있다. 이를 방지하기 위해 모터 내부에는 온도 센서(Temperature Sensor)가 내장되어 있으며, 온도가 허용 범위에 접근하면 제어기가 토크 제한(Torque Derating)이나 속도 감소를 자동으로 수행하여 시스템을 보호한다.

최근에는 에너지 효율도 매우 중요한 설계 목표가 되고 있다. 구동 모터에서 소비되는 전력은 배터리 용량과 운행 시간 및 충전 주기를 직접 결정한다. 따라서 자기 회로(Magnetic Circuit)를 최적화하고 정밀 베어링(Precision Bearing)과 저손실 전력 변환기를 적용하여 에너지 손실을 최소화한다. 또한 벡터 제어(Field-Oriented Control, FOC) 알고리즘을 사용하여 전류 손실을 줄이고 전 속도 영역에서 일정한 토크를 유지한다.

안전 기능(Safety Function)도 구동 모터와 긴밀하게 통합된다. 최신 산업용 서보 드라이브는 안전 토크 차단(Safe Torque Off, STO), 안전 정지 1(Safe Stop 1, SS1), 안전 속도 제한(Safely Limited Speed, SLS), 안전 브레이크 제어(Safe Brake Control, SBC) 등의 기능을 제공한다. 비상 상황에서는 구동 토크를 즉시 제거하고 브레이크와 연계하여 차량을 안전하게 정지시킴으로써 국제 산업 안전 규격을 만족한다.

또한 구동 모터는 예지보전(Predictive Maintenance)의 핵심 데이터도 제공한다. 모터 전류, 권선 온도, 진동, 엔코더 상태, 베어링 상태 및 누적 운전 시간을 지속적으로 기록하여 점진적인 성능 저하를 조기에 발견할 수 있다. 이를 통해 예상치 못한 고장을 줄이고 전체 차량의 가동률을 향상시킬 수 있다.

산업용 AMR이 점점 더 높은 적재 용량과 높은 자율성을 요구하게 되면서 구동 모터는 단순히 바퀴를 회전시키는 장치가 아니라 추진력 생성, 에너지 관리, 안전 기능, 열 관리, 상태 진단 및 정밀 운동 제어를 모두 수행하는 지능형 액추에이터(Intelligent Actuator)로 발전하고 있다. 따라서 구동 모터는 스티어 드라이브 시스템의 성능과 신뢰성을 결정하는 가장 핵심적인 구성 요소 중 하나라고 할 수 있다.

---

### 2.2 조향 모터의 역할 (Steering Motor Role)

조향 모터(Steering Motor)는 스티어 드라이브 시스템에서 각 바퀴의 방향을 결정하는 핵심 액추에이터이다. 구동 모터가 추진력을 생성한다면, 조향 모터는 그 추진력이 어느 방향으로 전달될 것인지를 결정한다. 이러한 기능의 명확한 분리는 스티어 드라이브 구조를 차동 구동과 구별하는 가장 중요한 특징이며, 기존 이동 로봇에서는 구현하기 어려웠던 다양한 이동 방식을 가능하게 한다. 조향 모터는 각 바퀴의 조향각(Steering Angle)을 지속적으로 제어하여 전진, 후진, 크랩 주행(Crab Motion), 대각선 이동(Diagonal Movement), 제자리 회전(Zero Radius Rotation)을 높은 정밀도로 수행할 수 있도록 한다.

조향 모터의 가장 기본적인 역할은 바퀴 전체를 수직 방향의 조향축(Steering Axis)을 중심으로 회전시키는 것이다. 일반 자동차처럼 여러 바퀴를 하나의 기계식 링크(Mechanical Linkage)로 연결하는 것이 아니라, 스티어 드라이브에서는 각 바퀴가 독립적인 조향 액추에이터를 가진다. 중앙 제어기에서 전달된 목표 조향각(Target Steering Angle)에 따라 각각의 조향 모터가 자신의 바퀴를 정확한 각도로 회전시키며, 목표 위치에 도달한 후 구동 모터가 추진력을 생성한다.

조향 정확도는 차량의 위치 정밀도를 직접 결정한다. 조향각이 아주 작은 오차만 발생하더라도 수 미터를 이동하면 수 센티미터 이상의 위치 오차가 누적될 수 있다. 따라서 산업용 스티어 드라이브는 매우 높은 분해능을 가지는 절대형 엔코더(Absolute Encoder)를 사용하여 조향각을 실시간으로 측정한다. 폐루프 서보 제어(Closed-loop Servo Control)는 외부 충격, 기계적 백래시(Backlash), 베어링 변형 및 하중 변화 등을 지속적으로 보정하여 항상 정확한 조향 상태를 유지한다.

조향 모터는 구동 모터와는 다른 동적 특성을 가진다. 추진력을 지속적으로 발생시키는 것이 아니라 조향 장치를 반복적으로 가속하고 감속하면서 매우 정확한 위치에 정지해야 한다. 빠른 조향 응답은 이동 모드 전환 시간을 줄여 기동성을 향상시키지만, 지나치게 빠른 움직임은 진동과 기계적 충격을 증가시킬 수 있다. 따라서 제어기는 응답 속도와 부드러운 움직임 사이의 균형을 고려한 최적의 조향 프로파일(Steering Motion Profile)을 생성한다.

조향 모터가 필요한 토크는 타이어와 바닥 사이의 마찰, 조향 베어링의 예압(Preload), 차량 하중 분포, 바퀴 직경 및 감속기 특성에 의해 결정된다. 특히 차량이 정지한 상태에서 조향을 수행하는 경우에는 타이어와 노면 사이의 큰 마찰력을 극복해야 하므로 상당한 토크가 요구된다. 1톤 이상의 중량급 AMR에서는 이러한 조향 저항이 매우 커지기 때문에 적절한 감속비와 충분한 토크를 가지는 서보 모터를 선정해야 한다.

조향 모터는 스티어 드라이브 시스템이 전방향 이동(Omnidirectional Motion)을 구현할 수 있게 하는 핵심 요소이다. 크랩 주행에서는 모든 조향 모터가 동일한 각도로 회전하여 차량이 방향을 바꾸지 않고 측면으로 이동한다. 대각선 이동에서는 모든 바퀴가 목표 이동 방향에 맞게 동일한 각도를 형성한다. 제자리 회전에서는 각 바퀴가 차량 중심을 향하는 접선 방향으로 조향되어 차량이 자신의 중심축을 기준으로 회전하게 된다.

여러 개의 조향 모터는 매우 정밀한 동기화(Synchronization)가 요구된다. 네 개의 조향 모터가 서로 다른 위치에 있지만 동일한 시간에 목표 각도에 도달해야만 차량이 원하는 방향으로 부드럽게 움직일 수 있다. 이를 위해 대부분의 산업용 시스템은 이더캣(EtherCAT)과 같은 결정론적 실시간 통신(Deterministic Real-time Communication)을 사용하며, 서브밀리초(Sub-millisecond) 수준의 정밀도로 모든 조향 모터를 동기화한다. 또한 구동 모터는 조향이 완료된 이후에만 충분한 추진력을 발생시켜 타이어 마모와 슬립을 최소화한다.

기계 구조 역시 조향 성능에 큰 영향을 미친다. 많은 스티어 드라이브 모듈은 하모닉 감속기(Harmonic Gearbox) 또는 고정밀 유성 감속기(High Precision Planetary Gearbox)를 사용하여 높은 감속비와 매우 작은 백래시를 동시에 확보한다. 백래시가 작을수록 조향 오차가 줄어들며, 이는 정밀 도킹이나 검사 작업에서 매우 중요한 요소가 된다. 또한 높은 강성을 가진 베어링 구조는 중량 하중에서도 조향축의 변형을 최소화하여 정확한 위치 제어를 가능하게 한다.

조향 시스템에는 대부분 절대형 엔코더가 사용된다. 절대형 엔코더는 전원이 차단되더라도 현재의 조향각 정보를 유지하므로, 시스템 재시작 시 별도의 원점 복귀(Homing) 과정이 필요하지 않다. 따라서 초기화 시간이 짧아지고 비상 정지 이후에도 정확한 조향 상태를 유지할 수 있다. 또한 지속적인 각도 피드백을 통해 백래시 증가나 기계적 이상 현상을 조기에 감지할 수 있다.

에너지 소비 측면에서 조향 모터는 구동 모터와 다른 특성을 가진다. 장거리 직선 주행에서는 조향각이 거의 변하지 않기 때문에 소비 전력이 매우 작다. 가장 많은 전력을 사용하는 경우는 전진에서 크랩 주행으로 전환하거나, 정밀 도킹을 위해 모든 바퀴를 동시에 회전시키는 순간이다. 따라서 전체 차량 소비 전력에서 차지하는 비율은 비교적 작지만 기능적인 중요성은 매우 크다.

안전성 역시 조향 시스템에서 매우 중요한 요소이다. 조향 기능이 상실되면 차량이 계획된 경로를 벗어나거나 충돌 위험이 발생할 수 있다. 따라서 조향 모터는 엔코더 신호, 전류, 위치 오차, 통신 상태 및 브레이크 상태를 지속적으로 감시한다. 이상이 발생하면 시스템은 즉시 안전 상태(Safe State)로 전환하여 조향을 정지시키고 구동 모터와 연계하여 차량을 안전하게 정지시킨다.

최근에는 조향 모터 역시 예지보전의 중요한 데이터 공급원이 되고 있다. 서보 전류, 조향 토크, 위치 정밀도, 감속기 진동, 엔코더 품질 및 베어링 마찰 상태 등을 지속적으로 분석하여 마모 정도를 예측하고, 실제 고장이 발생하기 전에 유지보수를 수행할 수 있도록 지원한다.

시스템 통합(System Integration)의 관점에서 보면 조향 모터는 일반적인 이동 플랫폼을 고기동성 자율주행 차량으로 변화시키는 핵심 요소이다. 각 바퀴를 독립적으로 원하는 방향으로 조향할 수 있기 때문에 다양한 운동 계획(Motion Planning) 알고리즘을 적용할 수 있으며, 중량물 운반, 정밀 설비 로딩, 자동 충전 도킹 및 고가의 검사 장비 위치 제어와 같은 다양한 산업 현장에서 뛰어난 성능을 발휘한다.

앞으로 산업용 AMR이 더욱 높은 위치 정밀도와 더 큰 적재 용량, 그리고 더욱 유연한 주행 성능을 요구하게 될수록 조향 모터 기술의 중요성은 더욱 커질 것이다. 서보 응답 성능, 엔코더 분해능, 감속기 정밀도, 실시간 통신 및 지능형 진단 기술의 발전은 차세대 스티어 드라이브 시스템의 기동성, 신뢰성 및 운영 효율을 지속적으로 향상시키는 핵심 요소가 될 것이다.

##  

## 03 Independent wheel control

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 4WS 4WD Independent Control Principle

The defining characteristic of a modern steer drive platform is its ability to independently control both the steering angle and driving torque of every wheel. This architecture is commonly referred to as Four-Wheel Steering and Four-Wheel Drive (4WS 4WD), where each wheel module functions as an autonomous mechatronic subsystem capable of executing steering, propulsion, sensing, and braking independently while remaining synchronized with the other modules. Unlike conventional automotive steering systems that rely on mechanical steering linkages or differential drive systems that achieve turning through wheel speed differences, a 4WS 4WD platform determines vehicle motion by coordinating four completely independent steering and drive actuators through real-time control algorithms.

In a 4WS 4WD system, every wheel module contains its own steering servo motor, drive motor, reduction gearbox, steering bearing, encoder, brake, and communication interface. Each module continuously receives steering angle commands and wheel velocity commands from the central motion controller. These commands are generated through inverse kinematic calculations based on the desired translational and rotational motion of the vehicle. Because each wheel receives its own optimized command, the robot is capable of generating virtually any motion permitted by its kinematic constraints without relying on tire skidding or mechanical steering mechanisms.

The independence of each wheel module significantly expands the available motion space. During straight-line travel, all steering motors align their wheels parallel to the longitudinal axis while the drive motors rotate at identical speeds. During curved motion, each wheel adopts a unique steering angle that corresponds to the instantaneous center of rotation while the drive motors generate different wheel velocities according to their respective turning radii. This coordinated behavior allows every wheel to roll naturally along its own trajectory, minimizing lateral tire forces and reducing rolling resistance.

One of the greatest engineering advantages of independent wheel control is the elimination of mechanical coupling between steering modules. Traditional steering systems often use tie rods, steering racks, or hydraulic linkages that constrain the motion of multiple wheels. Any mechanical backlash, compliance, or manufacturing tolerance affects the entire steering system. In contrast, steer drive modules communicate electronically rather than mechanically. Steering synchronization is achieved entirely through software and high-speed communication networks, enabling significantly greater flexibility in both vehicle design and control strategy.

The central controller continuously executes a hierarchical control architecture. At the highest level, mission planning generates global trajectories based on navigation objectives. Motion planning converts these trajectories into desired vehicle velocities expressed as longitudinal velocity, lateral velocity, and angular velocity. The kinematic controller then transforms these vehicle-level commands into individual steering angles and wheel rotational speeds for each module. Finally, local servo controllers within each wheel module precisely regulate motor torque and steering position using high-frequency feedback loops. This layered architecture separates high-level decision making from low-level actuator control while maintaining deterministic system behavior.

Independent control requires extremely accurate synchronization among all wheel modules. Even small timing errors between steering and propulsion commands can generate undesirable transient forces, wheel slip, or oscillatory vehicle motion. Therefore, industrial steer drive platforms commonly employ EtherCAT-based real-time communication capable of synchronizing multiple servo drives with sub-millisecond timing precision. Distributed clocks ensure that steering angle updates and wheel velocity commands are executed simultaneously throughout the entire vehicle, producing smooth coordinated motion under rapidly changing operating conditions.

The drive motors also operate independently but cooperatively. Rather than assigning fixed torque values to individual wheels, the motion controller dynamically distributes traction forces according to vehicle dynamics, payload distribution, floor conditions, and steering geometry. If one wheel experiences reduced traction due to contamination or uneven flooring, torque can be redistributed to other wheels without compromising overall vehicle stability. This adaptive traction management significantly improves reliability in industrial environments where floor conditions cannot always be guaranteed.

Feedback plays an equally important role in independent wheel control. Every steering module continuously reports steering angle, wheel velocity, motor current, encoder position, temperature, brake status, and diagnostic information to the central controller. These measurements allow the controller to compare actual wheel behavior with the expected kinematic model. Any discrepancies resulting from wheel slip, encoder failure, excessive backlash, or actuator degradation can be detected immediately and compensated using adaptive control algorithms.

Independent wheel control also simplifies scalability. The same control architecture can be extended from four-wheel platforms to six-wheel or eight-wheel heavy-duty autonomous vehicles with only minor modifications to the kinematic model. Since each module behaves as an identical functional unit, additional modules can simply be incorporated into the vehicle model while maintaining the same distributed control philosophy. This modular scalability is particularly attractive for manufacturers developing product families covering multiple payload classes.

Safety is deeply integrated into the independent control framework. Each wheel module independently monitors servo health, communication integrity, motor temperature, encoder validity, and brake functionality. If abnormalities are detected, the faulty module immediately enters a predefined safe operating state while notifying the supervisory controller. Depending on the severity of the fault, the vehicle may continue operating with degraded functionality or execute a controlled emergency stop. Such distributed fault management improves operational reliability and reduces the probability of catastrophic failures.

The architecture also facilitates predictive maintenance. Historical data collected from each steering module provide valuable insight into actuator health, gearbox wear, bearing degradation, and encoder performance. Machine learning algorithms increasingly analyze these long-term datasets to predict maintenance requirements before failures occur. As industrial fleets continue expanding, predictive maintenance based on independently monitored wheel modules becomes an important contributor to reducing lifecycle costs and maximizing fleet availability.

Overall, the 4WS 4WD independent control principle represents one of the most advanced motion architectures currently employed in industrial autonomous mobile robots. By replacing mechanical steering linkages with electronically synchronized intelligent wheel modules, the system achieves exceptional maneuverability, scalability, precision, and reliability while providing a flexible foundation for increasingly autonomous industrial transportation platforms.

---

### 3.2 Achieving Holonomic Motion

One of the most significant advantages of steer drive technology is its ability to achieve holonomic motion while utilizing conventional industrial wheels. Holonomic motion refers to the capability of independently controlling translational movement along both the longitudinal and lateral directions while simultaneously controlling rotational motion around the vertical axis. Unlike non-holonomic vehicles, whose motion is constrained by wheel orientation, a holonomic steer drive robot can move freely in virtually any direction without requiring intermediate steering maneuvers or unnecessary vehicle rotation.

The realization of holonomic motion is fundamentally based on the independent steering and driving capabilities of each wheel module. Because every wheel can simultaneously select its own steering angle and propulsion speed, the vehicle is no longer restricted to following paths aligned with its longitudinal axis. Instead, the central motion controller computes an optimal steering configuration that directly aligns every wheel with the desired velocity vector. Once steering alignment has been completed, the drive motors generate propulsion in precisely the required direction.

Vehicle motion is typically represented using three independent degrees of freedom on a two-dimensional plane: longitudinal velocity, lateral velocity, and angular velocity. These three variables completely describe the desired motion of the vehicle. The inverse kinematic solver transforms this three-dimensional motion command into four steering angles and four wheel rotational velocities corresponding to the individual steer drive modules. Since eight independent actuator outputs are generated from three vehicle-level motion variables, multiple feasible steering configurations may exist for the same desired motion. Modern optimization algorithms therefore select steering solutions that minimize steering rotation, reduce energy consumption, or maximize motion smoothness.

Forward and reverse driving represent the simplest forms of holonomic motion. All steering modules align parallel to the longitudinal axis while wheel velocities remain identical. Because each wheel rolls directly along its intended direction, rolling efficiency remains extremely high. Unlike differential drive systems, steering corrections during long-distance travel do not require continuous speed differences between left and right wheels, resulting in smoother trajectories and reduced tire wear.

Crab motion demonstrates one of the most distinctive capabilities of holonomic steer drive systems. During crab movement, every steering module rotates to an identical steering angle, allowing the entire vehicle to translate laterally while maintaining constant orientation. This motion is particularly valuable when docking alongside production equipment, aligning with storage racks, positioning large workpieces, or navigating narrow industrial aisles where rotational clearance is limited.

Diagonal movement combines longitudinal and lateral translation simultaneously. Rather than executing separate forward and sideways motions sequentially, the robot directly follows the desired diagonal trajectory by steering every wheel toward the resultant velocity vector. Eliminating intermediate maneuvers shortens travel distance, reduces cycle time, and improves overall operational efficiency within automated manufacturing environments.

Zero-radius rotation constitutes another essential holonomic capability. During this maneuver, every steering module rotates such that its rolling direction becomes tangential to a virtual circle centered at the vehicle\'s geometric center. Each drive motor generates wheel velocity proportional to its distance from the center of rotation, allowing the robot to rotate in place without any translational displacement. This maneuver greatly simplifies navigation in confined workspaces and enables precise orientation adjustments before docking or manipulation tasks.

Achieving truly smooth holonomic motion requires continuous steering optimization. Since abrupt steering angle changes may introduce unnecessary delays and increase mechanical wear, the controller predicts future trajectory segments and gradually reorients wheel modules before major direction changes occur. Model Predictive Control and trajectory optimization algorithms are increasingly employed to minimize steering acceleration, reduce actuator energy consumption, and maintain passenger- or payload-friendly motion profiles.

Synchronization between steering and drive commands is critically important during holonomic transitions. The controller must ensure that steering modules reach their target orientations before substantial propulsion torque is generated. If propulsion begins prematurely, temporary lateral tire forces may appear, producing undesirable vibration or wheel slip. High-speed deterministic communication networks therefore coordinate steering completion with drive torque activation to guarantee smooth motion transitions.

Holonomic motion also significantly improves positioning accuracy. Because lateral corrections can be performed directly without rotating the entire vehicle, final alignment errors are corrected using short linear adjustments rather than repeated rotational maneuvers. This capability is especially valuable for precision docking applications requiring positioning tolerances within ±20 millimeters or better. Automated charging stations, machine tending systems, semiconductor equipment, and optical inspection platforms all benefit from this highly accurate multidirectional positioning capability.

Despite its advantages, holonomic motion introduces additional computational complexity. The controller must continuously solve inverse kinematic equations, optimize steering configurations, synchronize multiple servo axes, compensate for actuator delays, and monitor wheel slip under varying operating conditions. Furthermore, steering optimization must consider physical limitations including maximum steering speed, wheel acceleration, mechanical interference, cable routing constraints, and actuator torque limits. Modern industrial processors, real-time operating systems, and high-bandwidth fieldbus communication make these computational requirements practical for today\'s autonomous mobile robots.

Sensor fusion further enhances holonomic performance. Wheel encoders provide local odometry information, inertial measurement units estimate rotational dynamics, LiDAR localization corrects accumulated position error, and vision systems verify final docking accuracy. Combining these sensor measurements within probabilistic state estimation frameworks allows the robot to maintain highly accurate multidirectional navigation even in dynamic industrial environments.

As autonomous mobile robots continue expanding into heavy manufacturing, semiconductor production, warehouse automation, aerospace assembly, and precision inspection, holonomic motion becomes increasingly valuable. The ability to move directly toward any target position while independently controlling orientation substantially reduces travel time, increases positioning precision, minimizes tire wear, and improves operational flexibility. Consequently, achieving holonomic motion through independently controlled steer drive modules has become one of the defining technologies of next-generation industrial autonomous mobile robot platforms.

### 3.1 4륜 조향·4륜 구동 독립 제어 원리 (4WS 4WD Independent Control Principle)

현대 스티어 드라이브(Steer Drive) 플랫폼의 가장 큰 특징은 모든 바퀴의 **조향각(Steering Angle)**과 **구동 토크(Driving Torque)**를 각각 독립적으로 제어할 수 있다는 점이다. 이러한 구조를 일반적으로 **4륜 조향·4륜 구동(4WS 4WD, Four-Wheel Steering & Four-Wheel Drive)**이라 부르며, 각 바퀴 모듈은 조향(Steering), 구동(Drive), 센싱(Sensing), 제동(Braking)을 모두 수행하는 독립적인 메카트로닉스(Mechatronics) 시스템으로 구성된다. 기존 자동차와 같이 기계식 조향 링크(Mechanical Steering Linkage)를 사용하는 방식이나, 좌우 바퀴의 속도 차이만으로 방향을 바꾸는 차동 구동(Differential Drive)과 달리, 4WS 4WD 시스템은 네 개의 조향 모터와 네 개의 구동 모터를 실시간으로 동시에 제어하여 원하는 움직임을 생성한다.

각 바퀴 모듈에는 조향 서보 모터(Steering Servo Motor), 구동 모터(Drive Motor), 감속기(Reduction Gearbox), 조향 베어링(Steering Bearing), 엔코더(Encoder), 브레이크(Brake) 및 통신 인터페이스(Communication Interface)가 독립적으로 구성된다. 중앙 운동 제어기(Central Motion Controller)는 차량 전체의 목표 움직임을 계산한 후 역기구학(Inverse Kinematics)을 이용하여 각 바퀴의 조향각과 회전 속도를 개별적으로 산출한다. 따라서 각각의 바퀴는 서로 다른 조향각과 속도를 가지면서도 전체적으로는 하나의 자연스럽고 안정적인 움직임을 만들어낸다.

독립 제어 구조는 차량이 사용할 수 있는 운동 공간(Motion Space)을 획기적으로 확대한다. 직진 주행에서는 모든 바퀴가 차량의 진행 방향과 평행하게 정렬되고 동일한 속도로 회전한다. 곡선 주행에서는 각 바퀴가 자신의 회전 반경에 맞는 조향각과 속도를 갖게 된다. 즉, 각 바퀴는 자신만의 궤적(Trajectory)을 따라 자연스럽게 굴러가기 때문에 횡방향 미끄러짐(Lateral Slip)이 거의 발생하지 않으며, 구름 저항(Rolling Resistance)도 최소화된다.

독립 휠 제어의 가장 큰 장점은 기계식 연결 장치(Mechanical Coupling)가 필요 없다는 점이다. 기존 자동차의 조향 시스템은 타이로드(Tie Rod), 랙 앤 피니언(Rack and Pinion), 유압 링크(Hydraulic Linkage) 등을 사용하여 여러 바퀴를 동시에 움직인다. 이러한 구조에서는 작은 백래시(Backlash)나 조립 오차가 전체 조향 성능에 영향을 미친다. 반면 스티어 드라이브에서는 모든 조향 모듈이 전기적으로 연결되며, 고속 실시간 통신망을 통해 소프트웨어적으로 동기화된다. 따라서 기계적인 제약 없이 훨씬 자유로운 차량 설계와 다양한 제어 알고리즘을 적용할 수 있다.

중앙 제어기는 계층형 제어 구조(Hierarchical Control Architecture)를 사용한다. 가장 상위 계층에서는 임무 계획(Mission Planning)이 전체 이동 경로를 생성한다. 이후 운동 계획(Motion Planning)은 차량의 목표 선속도(Longitudinal Velocity), 횡속도(Lateral Velocity), 각속도(Angular Velocity)를 계산한다. 운동학 제어기(Kinematic Controller)는 이 정보를 이용하여 각 바퀴의 조향각과 회전 속도를 산출하며, 마지막으로 각 바퀴 내부의 서보 제어기(Local Servo Controller)가 모터 토크와 조향 위치를 고속 폐루프 제어(Closed-loop Control)로 정밀하게 제어한다. 이러한 계층 구조는 상위 의사결정과 하위 액추에이터 제어를 효율적으로 분리하면서도 안정적인 시스템 동작을 유지한다.

독립 제어에서는 모든 바퀴의 동기화(Synchronization)가 매우 중요하다. 조향과 구동 명령 사이에 작은 시간 오차만 발생해도 순간적인 횡력이 발생하거나 바퀴 슬립(Wheel Slip), 차량 진동 및 자세 불안정이 발생할 수 있다. 이를 방지하기 위해 산업용 스티어 드라이브는 대부분 이더캣(EtherCAT) 기반의 실시간 통신을 사용하며, 서브밀리초(Sub-millisecond) 수준의 정밀한 시간 동기화를 수행한다. 분산 클록(Distributed Clock)은 모든 조향각과 속도 명령이 동시에 실행되도록 보장하여 매우 부드러운 차량 움직임을 구현한다.

구동 모터 또한 독립적으로 동작하지만 협력(Cooperative Control)을 기반으로 제어된다. 중앙 제어기는 바닥 상태, 적재 하중, 조향각 및 차량 동역학을 고려하여 각 바퀴에 필요한 견인력을 실시간으로 분배한다. 만약 특정 바퀴의 접지력이 감소하거나 노면이 오염되어 미끄러짐이 발생하면, 다른 바퀴에 토크를 재분배하여 차량 전체의 안정성을 유지한다. 이러한 적응형 견인력 제어(Adaptive Traction Management)는 실제 산업 현장에서 매우 중요한 기능이다.

피드백(Feedback)은 독립 제어 시스템의 핵심 요소이다. 각 바퀴 모듈은 조향각, 바퀴 속도, 모터 전류, 엔코더 위치, 온도, 브레이크 상태 및 각종 진단 정보를 중앙 제어기로 지속적으로 전송한다. 제어기는 실제 동작과 이상적인 운동학 모델을 비교하여 슬립, 엔코더 이상, 백래시 증가 또는 액추에이터 성능 저하를 즉시 감지하고 적응형 제어 알고리즘을 이용하여 보정한다.

독립 휠 제어는 플랫폼의 확장성(Scalability)도 매우 우수하다. 동일한 제어 구조를 이용하여 4륜 플랫폼뿐 아니라 6륜 또는 8륜 중량급 자율주행 차량으로도 쉽게 확장할 수 있다. 각 모듈이 동일한 기능을 수행하는 표준 모듈(Standard Module)이기 때문에 운동학 모델만 변경하면 새로운 플랫폼에도 동일한 제어 방식을 그대로 적용할 수 있다. 이러한 모듈화는 다양한 적재 용량을 가지는 제품군(Product Family)을 개발하는 제조사에게 매우 큰 장점을 제공한다.

안전성(Safety) 또한 독립 제어 구조에 깊이 통합되어 있다. 각 바퀴는 자신의 서보 상태, 통신 상태, 모터 온도, 엔코더 신호 및 브레이크 상태를 독립적으로 감시한다. 이상이 발생하면 해당 모듈은 즉시 안전 상태(Safe State)로 전환되고 중앙 제어기에 이를 보고한다. 상황에 따라 차량은 제한된 기능으로 운행을 계속하거나 안전하게 비상 정지(Emergency Stop)를 수행할 수 있다. 이러한 분산형 고장 관리(Distributed Fault Management)는 시스템의 신뢰성과 가동률을 크게 향상시킨다.

또한 독립 휠 제어는 예지보전(Predictive Maintenance)에도 매우 적합하다. 각 모듈에서 수집되는 장기간의 운전 데이터는 액추에이터 상태, 감속기 마모, 베어링 열화 및 엔코더 성능을 분석하는 데 활용된다. 최근에는 머신러닝(Machine Learning) 기반 분석 기법을 적용하여 실제 고장이 발생하기 전에 유지보수 시점을 예측하는 기술도 활발히 적용되고 있다.

결국 4WS 4WD 독립 제어 원리는 현재 산업용 AMR에서 가장 진보된 이동 제어 기술 가운데 하나이다. 기계식 조향 장치를 전자적으로 동기화된 지능형 휠 모듈(Intelligent Wheel Module)로 대체함으로써 뛰어난 기동성, 확장성, 정밀도 및 신뢰성을 동시에 확보할 수 있으며, 차세대 고중량 자율주행 이동 플랫폼의 핵심 기술로 자리 잡고 있다.

---

### 3.2 홀로노믹 이동 구현 (Achieving Holonomic Motion)

스티어 드라이브 기술의 가장 큰 장점 중 하나는 일반 산업용 바퀴를 사용하면서도 **홀로노믹 이동(Holonomic Motion)**을 구현할 수 있다는 점이다. 홀로노믹 이동이란 차량이 전후 방향뿐 아니라 좌우 방향으로도 자유롭게 이동할 수 있으며, 동시에 회전 운동까지 독립적으로 수행할 수 있는 이동 특성을 의미한다. 일반적인 비홀로노믹(Non-Holonomic) 차량은 바퀴의 방향에 의해 이동이 제한되지만, 홀로노믹 스티어 드라이브는 차량의 방향을 변경하지 않고도 원하는 방향으로 즉시 이동할 수 있다.

홀로노믹 이동의 핵심은 각 바퀴가 독립적으로 조향과 구동을 수행할 수 있다는 점이다. 모든 바퀴는 자신의 조향각과 회전 속도를 자유롭게 결정할 수 있기 때문에 차량은 더 이상 차체의 전방 방향으로만 움직일 필요가 없다. 중앙 운동 제어기는 목표 이동 방향을 계산하고, 각 바퀴가 그 방향으로 정확하게 정렬되도록 조향각을 계산한다. 이후 모든 구동 모터가 해당 방향으로 추진력을 발생시키면서 차량은 원하는 방향으로 직접 이동한다.

차량의 움직임은 일반적으로 세 개의 자유도(Degree of Freedom)로 표현된다. 전후 방향 속도(Longitudinal Velocity), 좌우 방향 속도(Lateral Velocity), 회전 속도(Angular Velocity)가 그것이다. 이 세 가지 변수만으로 차량의 모든 평면 운동을 표현할 수 있으며, 역기구학(Inverse Kinematics)은 이를 네 개의 조향각과 네 개의 바퀴 속도로 변환한다. 차량의 운동 변수는 세 개이지만 실제 제어해야 하는 액추에이터는 여덟 개이므로 동일한 움직임을 구현하는 여러 가지 조향 구성이 존재할 수 있다. 따라서 현대의 제어 알고리즘은 조향 회전량 최소화, 에너지 절감 또는 가장 부드러운 움직임을 기준으로 최적의 조향 구성을 선택한다.

전진과 후진은 가장 기본적인 홀로노믹 이동 형태이다. 모든 바퀴는 차량의 진행 방향과 평행하게 정렬되며 동일한 속도로 회전한다. 차동 구동처럼 좌우 속도 차이를 이용한 지속적인 보정이 필요하지 않기 때문에 장거리 이동에서도 매우 부드러운 주행과 높은 에너지 효율을 유지할 수 있다.

크랩 주행(Crab Motion)은 홀로노믹 스티어 드라이브의 대표적인 기능이다. 모든 바퀴가 동일한 조향각으로 회전하여 차량의 방향은 유지한 채 좌우로 평행 이동한다. 이러한 기능은 생산 설비 옆으로 접근하거나, 선반(Rack) 앞에 정밀하게 위치하거나, 좁은 통로에서 회전 공간 없이 이동해야 하는 경우 매우 유용하다.

대각선 이동(Diagonal Movement)은 전후 이동과 좌우 이동을 동시에 수행하는 방식이다. 차량은 별도의 회전이나 방향 전환 없이 목표 방향으로 직접 이동할 수 있으며, 중간 동작이 필요 없으므로 이동 거리와 작업 시간이 모두 단축된다. 이는 자동화 생산 라인의 생산성을 크게 향상시키는 요소이다.

제자리 회전(Zero Radius Rotation)은 또 하나의 중요한 홀로노믹 기능이다. 각 바퀴는 차량 중심을 기준으로 하는 가상의 원에 접하는 방향으로 조향되고, 각 구동 모터는 자신의 반경에 비례한 속도로 회전한다. 그 결과 차량은 위치를 이동하지 않고 자신의 중심축을 기준으로 회전할 수 있다. 이러한 기능은 매우 좁은 공간에서 방향을 전환하거나 정밀 도킹 전에 차량 자세를 미세하게 조정할 때 매우 효과적이다.

홀로노믹 이동을 부드럽게 구현하기 위해서는 지속적인 조향 최적화(Steering Optimization)가 필요하다. 급격한 조향 변화는 응답 시간을 증가시키고 기계적인 마모를 유발할 수 있기 때문에 제어기는 앞으로의 경로를 예측하여 미리 조향각을 변경한다. 최근에는 모델 예측 제어(Model Predictive Control, MPC)와 궤적 최적화(Trajectory Optimization)를 적용하여 조향 가속도를 최소화하고 에너지 소비를 줄이며, 적재 화물에도 충격이 적은 부드러운 움직임을 생성한다.

조향과 구동의 동기화 역시 매우 중요하다. 모든 조향 모듈이 목표 각도에 도달하기 전에 추진력이 발생하면 순간적인 횡방향 힘이 발생하여 진동과 슬립이 증가할 수 있다. 따라서 실시간 통신망은 조향 완료 시점과 구동 토크 발생 시점을 정밀하게 일치시켜 매우 자연스러운 운동 전환을 구현한다.

홀로노믹 이동은 위치 정밀도(Positioning Accuracy)도 크게 향상시킨다. 측면 보정이 필요한 경우 차량 전체를 회전시키지 않고도 짧은 직선 이동만으로 위치를 수정할 수 있기 때문에 반복적인 회전 보정이 필요하지 않다. 이러한 특성은 ±20 mm 이하의 정밀도를 요구하는 자동 충전기(Auto Charging Station), 공작기계 자동 로딩(Machine Tending), 반도체 제조 장비(Semiconductor Equipment), 광학 검사 시스템(Optical Inspection System) 등에서 매우 큰 장점을 제공한다.

물론 홀로노믹 이동은 높은 계산 성능을 요구한다. 제어기는 지속적으로 역기구학을 계산하고, 최적의 조향 구성을 선택하며, 여러 개의 서보축을 동기화하고, 액추에이터의 지연 시간과 바퀴 슬립까지 보정해야 한다. 또한 최대 조향 속도, 바퀴 가속도, 기계적 간섭, 케이블 배선 한계 및 모터 토크 한계와 같은 물리적 제약도 함께 고려해야 한다. 최근의 산업용 프로세서와 실시간 운영체제(Real-time Operating System), 고속 필드버스(Fieldbus)는 이러한 복잡한 계산을 충분히 실시간으로 처리할 수 있다.

센서 융합(Sensor Fusion)은 홀로노믹 성능을 더욱 향상시킨다. 휠 엔코더는 오도메트리(Odometry)를 제공하고, 관성측정장치(IMU)는 회전 운동을 측정하며, 라이다 위치 인식(LiDAR Localization)은 누적 위치 오차를 보정한다. 또한 비전 시스템(Vision System)은 최종 도킹 위치를 검증한다. 이러한 센서 데이터를 확률 기반 상태 추정(State Estimation) 알고리즘으로 융합하면 복잡한 산업 환경에서도 매우 높은 위치 정확도를 유지할 수 있다.

산업용 AMR이 중공업, 반도체 제조, 물류 자동화, 항공우주 조립 및 정밀 검사 분야로 확대될수록 홀로노믹 이동의 중요성은 더욱 커지고 있다. 차량은 원하는 위치로 가장 짧은 경로를 따라 직접 이동하면서도 방향을 독립적으로 유지할 수 있으므로 이동 시간이 단축되고 위치 정밀도는 향상되며 타이어 마모와 에너지 소비도 감소한다. 따라서 독립적으로 제어되는 스티어 드라이브 모듈을 이용한 홀로노믹 이동은 차세대 산업용 자율주행 이동로봇 플랫폼을 대표하는 핵심 기술 가운데 하나로 평가되고 있다.

##  

## 04 Motion types

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Forward and Reverse

Forward and reverse motion represents the most fundamental operating mode of a steer drive mobile robot. Although this movement appears similar to that of conventional wheeled vehicles, the underlying steering and propulsion mechanisms are fundamentally different because every wheel module operates independently. In a steer drive architecture, forward and reverse travel are achieved by aligning all steering modules parallel to the vehicle\'s longitudinal axis while synchronizing the rotational speed of every drive motor. Since all wheels roll in the same direction without requiring differential wheel speeds, the vehicle experiences minimal lateral tire slip, resulting in highly efficient propulsion and excellent trajectory stability.

During forward motion, the central motion controller generates a desired longitudinal velocity while maintaining zero lateral velocity and zero angular velocity. The inverse kinematic solver calculates identical steering angles for all wheel modules, typically aligned with the body reference frame. Once the steering motors confirm that all wheel modules have reached the commanded orientation, synchronized velocity commands are transmitted to the drive motors. Each drive motor generates propulsion proportional to the requested vehicle speed while continuously compensating for small disturbances caused by floor irregularities, payload shifts, or rolling resistance variations. This coordinated operation enables smooth acceleration and deceleration while minimizing mechanical stress throughout the drivetrain.

Reverse motion follows the same control principle but reverses the direction of wheel rotation. Depending on the steering optimization algorithm, the controller may either maintain the existing steering orientation and reverse the drive motor rotation or rotate every steering module by 180 degrees while keeping the drive motors rotating in the forward direction. Modern steer drive controllers automatically select the strategy requiring the least steering movement to reduce transition time and improve operational efficiency. This optimization becomes particularly important in applications involving frequent direction changes such as warehouse logistics, machine tending, and automated pallet transport.

One significant advantage of steer drive forward and reverse motion is the elimination of unnecessary tire scrubbing. Differential drive systems continuously introduce slight speed differences between left and right wheels to maintain straight trajectories, causing cumulative tire wear and energy loss. In contrast, steer drive platforms rely on steering angle correction rather than wheel speed imbalance. Every wheel naturally follows the commanded direction, reducing rolling resistance and extending tire service life. This characteristic becomes increasingly valuable for heavy-duty autonomous mobile robots carrying payloads exceeding one ton, where tire wear and drivetrain efficiency directly influence operational cost.

Maintaining precise straight-line travel requires continuous sensor feedback and closed-loop control. Wheel encoders measure rotational speed, steering encoders verify wheel orientation, inertial measurement units detect yaw deviations, and localization systems such as LiDAR-based SLAM or RTK positioning provide global position updates. Sensor fusion algorithms continuously compare the actual vehicle trajectory with the planned path and generate small steering corrections whenever deviations are detected. Rather than relying solely on wheel speed differences, the controller subtly adjusts steering angles to maintain an accurate heading while preserving efficient rolling motion.

Dynamic load distribution also influences forward and reverse driving performance. As the vehicle accelerates or decelerates, weight transfer alters the normal force acting on each wheel. Advanced traction management algorithms monitor motor currents and wheel slip indicators to redistribute driving torque among the wheel modules. By maintaining balanced traction across all wheels, the system minimizes localized tire loading and improves stability during high-acceleration maneuvers or when traversing uneven industrial flooring.

Safety functions remain fully active throughout forward and reverse operation. Collision avoidance systems continuously monitor the surrounding environment using safety LiDARs, cameras, ultrasonic sensors, and radar. If obstacles are detected, the motion controller smoothly reduces vehicle speed according to predefined safety profiles before initiating controlled braking if necessary. Safe Torque Off, Safe Limited Speed, and Safe Brake Control functions are integrated into the drive system to ensure compliance with industrial safety standards while maintaining predictable vehicle behavior.

Forward and reverse motion also serve as the foundation for more complex maneuvers. Every advanced motion type---including crab movement, diagonal travel, and zero-radius rotation---is ultimately generated through coordinated modifications of steering orientation and wheel velocity originating from this basic driving mode. Consequently, optimizing straight-line propulsion directly improves the performance, efficiency, and precision of all higher-level motion behaviors within the steer drive architecture.

---

### 4.2 Zero Radius Rotation

Zero-radius rotation is one of the most distinctive capabilities of a steer drive platform and represents a major advantage over conventional non-holonomic vehicles. This maneuver allows the mobile robot to rotate about its own geometric center without producing any translational displacement. Unlike differential drive robots, which rotate by intentionally generating opposite wheel speeds and allowing tire scrubbing, steer drive robots achieve pure rotational motion by precisely orienting every wheel tangentially to a virtual circle centered within the vehicle before generating synchronized wheel velocities.

The execution of zero-radius rotation begins with steering optimization. The inverse kinematic controller calculates the required steering angle for every wheel based on its position relative to the vehicle center. Each steering module rotates until the wheel rolling direction becomes tangent to the desired rotational path. Since the wheels are aligned with their natural rolling direction, rotational motion is achieved through rolling rather than sliding, greatly reducing tire wear and mechanical losses.

Once all steering modules have reached their commanded orientations, the drive motors generate rotational velocities proportional to their distance from the center of rotation. Wheels positioned farther from the rotational center travel longer circular paths and therefore require higher linear velocities. Conversely, wheels closer to the center rotate more slowly while maintaining synchronized angular motion. The resulting wheel motions produce a pure rotational moment that turns the entire vehicle without changing its global position.

This maneuver provides exceptional maneuverability within confined industrial environments. Automated guided vehicles frequently operate between densely packed machinery, warehouse shelving, production cells, or narrow maintenance corridors where conventional turning radii are insufficient. Zero-radius rotation enables precise orientation adjustments without requiring additional maneuvering space, significantly reducing navigation complexity and shortening travel time.

The dynamic stability of zero-radius rotation depends heavily on synchronization accuracy among all steering and drive modules. Small steering angle errors can generate undesired lateral forces that disturb rotational stability. Similarly, unequal drive motor velocities may shift the effective center of rotation away from the geometric center, introducing unintended translational movement. High-speed deterministic communication systems such as EtherCAT synchronize all steering and propulsion commands with sub-millisecond precision, ensuring smooth rotational behavior even during rapid maneuvering.

Rotational inertia becomes particularly important for heavy industrial AMRs carrying large payloads. As payload mass and moment of inertia increase, greater drive torque is required to initiate and stop rotational motion. Motion controllers therefore employ jerk-limited acceleration profiles that gradually increase angular velocity while minimizing dynamic loading on the drivetrain and transported equipment. Smooth rotational profiles reduce structural vibration, improve passenger or payload safety, and extend component service life.

Sensor feedback plays a central role during zero-radius rotation. Steering encoders continuously verify wheel orientation while wheel encoders measure rotational velocity. Inertial measurement units monitor yaw rate and angular acceleration, providing immediate feedback regarding rotational dynamics. Simultaneously, external localization systems validate the absence of unintended translational displacement, allowing adaptive corrections whenever rotational accuracy deviates from the desired trajectory.

Zero-radius rotation is particularly valuable during precision docking applications. Before aligning with charging stations, production equipment, automated storage systems, or inspection fixtures, the robot often requires accurate orientation adjustment while maintaining its existing position. Rotating in place eliminates unnecessary translational corrections and simplifies final positioning, contributing to docking repeatability within ±20 millimeters or better.

Energy efficiency is another advantage of steer drive rotational motion. Because the wheels roll naturally along circular trajectories instead of sliding sideways, frictional energy losses remain relatively low. Reduced tire scrub decreases power consumption, lowers motor heating, and extends wheel lifetime compared with skid-steering systems performing similar maneuvers.

From an engineering perspective, zero-radius rotation demonstrates the fundamental strength of independently controlled steering and propulsion. By coordinating steering geometry with precisely synchronized wheel velocities, the steer drive platform transforms rotational movement from a friction-dominated process into a highly efficient rolling motion. This capability significantly enhances maneuverability, operational flexibility, and positioning accuracy, making zero-radius rotation one of the defining features of modern industrial steer drive autonomous mobile robots.

---

### 4.3 Crab Motion (Lateral Movement)

Crab motion, often referred to as lateral movement, enables a steer drive vehicle to translate sideways while maintaining a constant body orientation. This capability distinguishes steer drive systems from conventional wheeled vehicles, which generally require body rotation before changing lateral position. Crab motion is achieved by rotating every steering module to an identical steering angle while commanding identical wheel velocities, allowing the entire platform to move parallel to itself.

The control process begins by specifying a desired lateral velocity with zero longitudinal velocity and zero angular velocity. The inverse kinematic algorithm calculates identical steering orientations for all wheel modules, typically ninety degrees relative to the vehicle\'s forward direction when performing pure lateral translation. Once steering alignment has been completed, the drive motors generate synchronized propulsion, causing the robot to move sideways without rotating.

One of the greatest benefits of crab motion is the ability to perform precise lateral positioning in confined workspaces. Manufacturing equipment, storage racks, machine tools, conveyor systems, and automated charging stations often require vehicles to approach from the side while preserving their orientation. Instead of executing multiple forward, reverse, and turning maneuvers, the robot simply shifts laterally into the required position. This direct movement significantly shortens cycle time and reduces navigation complexity.

Maintaining body orientation during lateral movement is particularly advantageous when transporting sensitive payloads. Large workpieces, semiconductor equipment, optical instruments, and inspection systems frequently require stable orientation to prevent vibration or alignment errors. Crab motion eliminates unnecessary rotational acceleration, reducing inertial disturbances transmitted to the payload and improving operational precision.

The success of crab motion depends heavily on steering synchronization. Since all wheel modules must maintain identical steering angles throughout the maneuver, even small orientation differences may generate internal forces or unintended rotational moments. Continuous feedback from steering encoders allows the controller to compensate for mechanical tolerances, actuator delays, and external disturbances, preserving accurate lateral translation.

Floor conditions strongly influence lateral motion quality. Because every wheel rolls perpendicular to the vehicle\'s original forward direction, variations in floor friction or uneven surfaces may introduce asymmetric rolling resistance among wheel modules. Adaptive traction control continuously monitors motor currents and wheel velocities, redistributing torque whenever localized slip or excessive resistance is detected. This adaptive behavior ensures stable lateral motion across diverse industrial environments.

Crab motion is also frequently combined with visual servoing during final alignment operations. Cameras or LiDAR sensors measure the remaining lateral positioning error relative to docking targets or production equipment. The controller then performs very small sideways corrections without altering vehicle orientation, achieving highly accurate alignment suitable for automated loading, unloading, charging, or inspection tasks.

Safety considerations remain important during lateral movement because surrounding personnel may not anticipate sideways vehicle motion. Modern industrial AMRs therefore integrate multidirectional obstacle detection systems that monitor the complete perimeter of the vehicle regardless of travel direction. Dynamic safety zones automatically adjust according to current motion direction and vehicle speed, ensuring safe operation even when moving laterally.

Crab motion ultimately represents one of the most practical demonstrations of steer drive flexibility. By enabling direct sideways translation while preserving vehicle orientation, it greatly improves operational efficiency, positioning precision, and workspace utilization. Applications ranging from semiconductor manufacturing to automotive assembly increasingly rely on this capability to maximize productivity within densely populated industrial environments.

---

### 4.4 Diagonal Movement

Diagonal movement represents the ability of a steer drive robot to travel simultaneously in both longitudinal and lateral directions without requiring intermediate steering maneuvers. Rather than decomposing a desired path into separate forward and sideways motions, the robot directly follows the resultant velocity vector through coordinated steering and propulsion. This capability minimizes travel distance, shortens mission time, and improves overall operational efficiency.

The principle of diagonal movement relies on inverse kinematic computation of the desired resultant velocity. The motion controller receives target longitudinal and lateral velocity components together with any desired rotational velocity. It then calculates the optimal steering angle and wheel speed for every wheel module such that the combined traction forces produce the specified vehicle motion. Every steering module aligns with the resultant velocity vector while each drive motor generates the corresponding propulsion force.

Because the wheels roll directly in the intended travel direction, diagonal movement avoids the repeated acceleration and deceleration associated with sequential motion planning. Eliminating unnecessary intermediate maneuvers reduces energy consumption, decreases mechanical wear, and shortens cycle times. This benefit becomes increasingly significant in high-throughput industrial automation where thousands of repetitive transport operations occur every day.

Diagonal movement also enhances navigation flexibility. Dynamic obstacle avoidance algorithms frequently generate temporary trajectory modifications that require simultaneous changes in longitudinal and lateral motion. Instead of stopping and reorienting the vehicle, the steer drive platform smoothly transitions into the new diagonal path while maintaining continuous forward progress. This capability enables fluid navigation through crowded industrial environments with moving personnel, forklifts, or other autonomous vehicles.

Steering optimization plays a critical role in achieving efficient diagonal movement. Multiple steering configurations may satisfy the same resultant velocity vector, particularly when steering modules are capable of rotating beyond ±180 degrees. Optimization algorithms evaluate candidate solutions according to criteria such as minimum steering displacement, lowest energy consumption, reduced transition time, or minimal actuator wear before selecting the optimal configuration.

Continuous synchronization between steering and propulsion ensures that every wheel contributes appropriately to the desired motion. Steering encoders verify angular alignment while wheel encoders regulate rotational speed. Real-time communication networks coordinate all actuator updates, preventing transient steering mismatches that could introduce lateral tire forces or unwanted rotational motion.

Payload dynamics become increasingly important during diagonal travel, particularly for heavy autonomous mobile robots. Since longitudinal and lateral accelerations occur simultaneously, the combined inertial forces acting on the payload may exceed those experienced during pure straight-line motion. Motion controllers therefore employ jerk-limited trajectory generation and adaptive acceleration constraints based on payload characteristics, ensuring stable transportation without excessive vibration or load shifting.

Sensor fusion further improves diagonal movement accuracy. Wheel odometry estimates short-term vehicle displacement, inertial sensors measure translational and rotational acceleration, while external localization systems correct accumulated positioning error. The combined state estimate enables highly accurate tracking of diagonal trajectories over extended travel distances despite sensor noise and wheel slip.

Industrial applications frequently exploit diagonal movement to optimize workspace utilization. Automated warehouses, semiconductor fabrication facilities, aerospace assembly lines, and flexible manufacturing cells often contain complex layouts where direct diagonal travel minimizes path length. Reducing unnecessary turns not only increases productivity but also decreases drivetrain wear and battery energy consumption.

Diagonal movement illustrates the full capability of independently controlled steer drive modules. By simultaneously controlling steering orientation and propulsion for every wheel, the robot can directly execute complex trajectories that would otherwise require multiple sequential maneuvers. This capability enhances maneuverability, positioning precision, operational efficiency, and overall system flexibility, reinforcing the steer drive architecture as one of the most advanced mobility solutions available for modern industrial autonomous mobile robots.

---

### 4.1 전진 및 후진 (Forward and Reverse)

전진 및 후진(Forward and Reverse)은 스티어 드라이브(Steer Drive) 이동 로봇의 가장 기본적인 주행 방식이다. 외형적으로는 일반 차량과 유사해 보이지만, 내부의 조향 및 추진 메커니즘은 근본적으로 다르다. 스티어 드라이브에서는 모든 바퀴가 독립적으로 조향과 구동을 수행하기 때문에, 차량은 보다 높은 효율과 안정성을 유지하면서 직선 주행을 수행할 수 있다. 전진과 후진은 모든 조향 모듈이 차량의 종방향(Longitudinal Direction)과 평행하게 정렬된 상태에서, 모든 구동 모터가 동일한 속도로 회전함으로써 구현된다. 모든 바퀴는 동일한 방향으로 자연스럽게 굴러가기 때문에 횡방향 슬립(Lateral Slip)이 거의 발생하지 않으며, 매우 높은 추진 효율과 우수한 직진 안정성을 확보할 수 있다.

전진 주행에서는 중앙 운동 제어기(Central Motion Controller)가 종방향 속도(Longitudinal Velocity)는 원하는 값으로 설정하고, 횡방향 속도(Lateral Velocity)와 각속도(Angular Velocity)는 모두 0으로 유지한다. 역기구학(Inverse Kinematics) 계산기는 모든 조향 모듈에 동일한 조향각을 계산하며, 일반적으로 차체의 진행 방향과 일치하도록 설정한다. 이후 모든 조향 모터가 목표 각도에 도달했음을 확인하면, 구동 모터에 동일한 속도 명령이 전달된다. 각 구동 모터는 목표 속도에 비례하는 추진력을 생성하며, 바닥 상태나 적재 하중 변화, 구름 저항의 차이를 지속적으로 보정하여 안정적인 주행을 유지한다. 이러한 협조 제어(Coordinated Control)를 통해 차량은 부드러운 가속과 감속을 수행하면서도 구동계에 전달되는 기계적 충격을 최소화할 수 있다.

후진 역시 동일한 원리를 따른다. 가장 단순한 방법은 구동 모터의 회전 방향만 반대로 변경하는 것이다. 그러나 현대의 스티어 드라이브 시스템은 조향 최적화(Steering Optimization) 알고리즘을 적용하여 보다 효율적인 방식을 선택한다. 경우에 따라서는 조향 모듈을 180도 회전시킨 후 구동 모터를 정방향으로 회전시키는 것이 더 빠를 수도 있으며, 반대로 조향각을 그대로 유지하고 모터의 회전 방향만 반전시키는 것이 더 효율적일 수도 있다. 제어기는 두 가지 방법 가운데 조향 회전량이 가장 적은 방식을 선택하여 전환 시간을 줄이고 에너지 소비를 최소화한다. 이러한 기능은 창고 물류, 자동 팔레트 운반, 공작기계 로딩과 같이 빈번한 방향 전환이 필요한 산업 현장에서 매우 효과적이다.

스티어 드라이브 방식은 직진 주행 시 불필요한 타이어 끌림(Tire Scrubbing)이 거의 발생하지 않는다는 큰 장점을 가진다. 차동 구동은 직진을 유지하기 위해 좌우 바퀴 속도를 지속적으로 미세 조정하며, 이 과정에서 누적되는 마찰과 마모가 발생한다. 반면 스티어 드라이브는 조향각을 직접 보정하여 진행 방향을 유지하기 때문에 모든 바퀴가 자신의 회전 방향 그대로 굴러가며, 구름 저항과 에너지 손실이 크게 감소한다. 특히 1톤 이상의 중량물을 운반하는 산업용 AMR에서는 이러한 차이가 타이어 수명과 운영 비용에 매우 큰 영향을 미친다.

정확한 직선 주행을 유지하기 위해서는 지속적인 센서 피드백(Sensor Feedback)과 폐루프 제어(Closed-loop Control)가 필요하다. 휠 엔코더(Wheel Encoder)는 바퀴의 회전 속도를 측정하고, 조향 엔코더(Steering Encoder)는 조향각을 확인한다. 관성측정장치(IMU)는 차량의 요(Yaw) 변화를 감지하며, 라이다 기반 SLAM이나 RTK 위치 측정 시스템은 전역 위치를 지속적으로 갱신한다. 센서 융합(Sensor Fusion) 알고리즘은 실제 이동 경로와 계획된 경로를 비교하여 오차가 발생하면 조향각을 미세하게 수정한다. 이 과정에서 좌우 바퀴의 속도를 변화시키지 않고 조향각만으로 경로를 보정하기 때문에 높은 효율과 우수한 직진성을 동시에 확보할 수 있다.

가속과 감속 시에는 하중 이동(Weight Transfer)이 발생하여 각 바퀴에 작용하는 수직 하중이 변화한다. 이에 따라 견인력도 달라질 수 있으므로, 고급 견인력 관리(Traction Management) 알고리즘은 모터 전류와 슬립 정보를 분석하여 구동 토크를 실시간으로 재분배한다. 이를 통해 모든 바퀴의 접지력을 균등하게 유지하고, 고속 가속이나 경사로 주행에서도 안정적인 움직임을 확보할 수 있다.

전진과 후진 주행에서도 안전 기능(Safety Function)은 항상 활성화되어 있다. 안전 라이다(Safety LiDAR), 카메라(Camera), 초음파 센서(Ultrasonic Sensor), 레이더(Radar)는 주변 환경을 지속적으로 감시하며, 장애물이 감지되면 제어기는 미리 정의된 감속 프로파일에 따라 속도를 줄이고 필요 시 안전하게 차량을 정지시킨다. 또한 안전 토크 차단(STO), 안전 속도 제한(SLS), 안전 브레이크 제어(SBC) 기능이 함께 동작하여 국제 산업 안전 규격을 만족하는 안전한 운행을 보장한다.

전진과 후진은 단순한 기본 주행 기능을 넘어 모든 고급 운동의 기반이 된다. 크랩 주행(Crab Motion), 대각선 이동(Diagonal Movement), 제자리 회전(Zero Radius Rotation)과 같은 모든 복합 운동은 결국 전진·후진 주행을 기반으로 조향 방향과 바퀴 속도를 조합하여 생성된다. 따라서 직선 주행 성능을 최적화하는 것은 스티어 드라이브 전체 시스템의 성능을 향상시키는 가장 중요한 요소 가운데 하나이다.

---

### 4.2 제자리 회전 (Zero Radius Rotation)

제자리 회전(Zero Radius Rotation)은 스티어 드라이브 플랫폼을 가장 잘 대표하는 운동 방식 중 하나이며, 기존 비홀로노믹(Non-Holonomic) 차량과 가장 큰 차이를 보여주는 기능이다. 이 동작은 차량의 위치를 이동시키지 않은 채 자신의 기하학적 중심(Geometric Center)을 기준으로 회전하는 기능이다. 차동 구동은 좌우 바퀴를 반대 방향으로 회전시켜 타이어를 미끄러뜨리면서 회전하지만, 스티어 드라이브는 모든 바퀴를 가상의 회전 원(Virtual Rotation Circle)에 접하는 방향으로 조향한 뒤 자연스럽게 굴러가도록 하여 회전을 수행한다.

제자리 회전은 먼저 조향 최적화(Steering Optimization) 과정을 수행한다. 역기구학 제어기는 차량 중심을 기준으로 각 바퀴의 위치를 계산한 후, 모든 바퀴가 회전 원의 접선 방향(Tangential Direction)을 향하도록 조향각을 산출한다. 각 조향 모듈은 목표 각도까지 회전하며, 이후 구동 모터가 회전 운동을 시작한다. 모든 바퀴는 자신의 진행 방향 그대로 굴러가기 때문에 불필요한 횡방향 마찰이 거의 발생하지 않으며, 회전 효율도 매우 높다.

조향이 완료되면 각 구동 모터는 차량 중심으로부터 자신의 거리에 비례하는 속도로 회전한다. 중심에서 먼 바퀴일수록 더 긴 원주를 이동하므로 더 높은 선속도(Linea Velocity)가 필요하고, 중심에 가까운 바퀴는 상대적으로 느린 속도로 회전한다. 이러한 속도 분포는 순수한 회전 모멘트(Rotational Moment)를 생성하여 차량이 위치를 이동하지 않고 회전하도록 만든다.

이 기능은 좁은 산업 환경에서 매우 큰 장점을 제공한다. 자동화 생산라인, 물류 창고, 반도체 제조 설비 등에서는 차량이 회전할 수 있는 공간이 매우 제한적이다. 일반 차량은 회전을 위해 상당한 회전 반경(Turning Radius)이 필요하지만, 제자리 회전은 추가 공간 없이 방향만 변경할 수 있으므로 이동 효율이 크게 향상된다.

회전의 안정성은 모든 조향 및 구동 모듈의 정밀한 동기화에 달려 있다. 조향각에 작은 오차만 있어도 횡력이 발생하고, 구동 속도가 서로 일치하지 않으면 차량 중심이 이동하는 현상이 발생할 수 있다. 따라서 이더캣(EtherCAT)과 같은 실시간 통신망은 서브밀리초 수준으로 모든 모듈을 동기화하여 매우 안정적인 회전 운동을 구현한다.

중량물이 탑재된 산업용 AMR에서는 회전 관성(Rotational Inertia)이 매우 중요한 요소이다. 적재 질량과 관성 모멘트(Moment of Inertia)가 증가할수록 회전을 시작하거나 정지하기 위해 더 큰 토크가 필요하다. 이를 위해 제어기는 저크 제한(Jerk-limited) 가속 프로파일을 사용하여 회전 속도를 점진적으로 증가시키고 감소시킨다. 이러한 부드러운 제어는 적재 화물에 전달되는 충격을 줄이고, 차량 구조물의 피로를 감소시키며, 장비 수명을 연장한다.

회전 중에도 다양한 센서가 지속적으로 동작한다. 조향 엔코더는 각도를 확인하고, 휠 엔코더는 회전 속도를 측정하며, IMU는 각속도와 각가속도를 실시간으로 측정한다. 외부 위치 인식 시스템은 차량이 회전만 수행하고 실제 위치는 이동하지 않았는지를 검증하며, 필요 시 오차를 자동으로 보정한다.

제자리 회전은 정밀 도킹(Precision Docking)에서도 매우 유용하다. 자동 충전기, 생산 설비, 검사 장비 앞에서는 차량의 위치는 그대로 유지한 채 방향만 정확하게 맞추는 경우가 많다. 이러한 경우 제자리 회전은 불필요한 위치 이동 없이 방향만 조정할 수 있어 최종 정렬 시간을 크게 줄여준다.

에너지 효율 측면에서도 제자리 회전은 장점이 있다. 바퀴가 자연스럽게 굴러가면서 회전하기 때문에 차동 구동처럼 슬립에 의한 에너지 손실이 거의 발생하지 않는다. 따라서 전력 소비와 모터 발열이 감소하고 타이어 수명도 크게 향상된다.

결국 제자리 회전은 독립 조향과 독립 구동의 장점을 가장 잘 보여주는 운동 방식이다. 조향과 추진을 정밀하게 조합함으로써 차량은 매우 높은 기동성과 정밀도, 에너지 효율을 동시에 확보할 수 있으며, 현대 산업용 AMR에서 가장 중요한 이동 기능 가운데 하나로 자리 잡고 있다.

---

### 4.3 크랩 주행(측면 이동) (Crab Motion, Lateral Movement)

크랩 주행(Crab Motion)은 차량의 방향을 유지한 채 좌우 방향으로 평행 이동하는 기능이다. 이는 일반적인 자동차나 차동 구동 차량에서는 구현하기 어려운 스티어 드라이브만의 대표적인 이동 방식이다. 모든 조향 모듈이 동일한 각도로 회전하고, 모든 구동 모터가 동일한 속도로 회전함으로써 차량 전체가 게처럼 옆으로 이동하게 된다.

크랩 주행에서는 종방향 속도는 0이고, 횡방향 속도만 존재하며, 회전 속도 역시 0으로 유지된다. 역기구학 알고리즘은 모든 바퀴를 일반적으로 차량 진행 방향에서 90도 회전시키고, 동일한 속도로 추진력을 발생시킨다. 그 결과 차량은 차체 방향을 바꾸지 않은 채 원하는 방향으로 측면 이동한다.

이 기능은 산업 현장에서 매우 유용하다. 생산 설비 옆으로 접근하거나, 자동 창고 선반에 정밀하게 정렬하거나, 좁은 통로에서 회전 공간 없이 위치를 수정해야 하는 경우 차량은 여러 번의 전진과 후진 없이 단순히 옆으로 이동하여 목표 위치에 도달할 수 있다. 이는 작업 시간을 줄이고 생산성을 크게 향상시킨다.

크랩 주행은 민감한 화물을 운반할 때에도 장점이 크다. 대형 반도체 장비, 광학 검사 장비, 정밀 측정 장비는 차량이 회전하면 관성력이 발생하여 장비 정렬에 영향을 줄 수 있다. 측면 이동은 차량의 방향을 유지한 채 이동하기 때문에 회전에 따른 충격과 진동을 최소화할 수 있다.

모든 바퀴는 동일한 조향각을 유지해야 하므로 조향 동기화가 매우 중요하다. 작은 각도 차이만 발생해도 차량 내부에 불필요한 응력이 발생하거나 원치 않는 회전이 발생할 수 있다. 따라서 조향 엔코더의 지속적인 피드백과 폐루프 제어를 이용하여 모든 바퀴의 방향을 항상 동일하게 유지한다.

바닥 상태 역시 측면 이동에 큰 영향을 미친다. 바닥 마찰이나 평탄도가 일정하지 않으면 바퀴마다 구름 저항이 달라질 수 있다. 이를 보완하기 위해 적응형 견인력 제어는 각 모터의 전류와 속도를 분석하여 필요한 경우 토크를 자동으로 재분배한다.

크랩 주행은 비전 기반 서보 제어(Visual Servoing)와도 자주 결합된다. 카메라와 라이다는 최종 위치 오차를 측정하고, 차량은 매우 작은 측면 이동만으로 정밀한 위치를 맞춘다. 따라서 자동 충전기, 생산 설비 및 검사 장비와의 정밀 정렬에 매우 적합하다.

측면 이동은 작업자가 예상하지 못하는 방향으로 차량이 움직일 수 있으므로 안전성도 매우 중요하다. 현대 산업용 AMR은 이동 방향과 관계없이 차량 전체 주변을 감시하는 다방향 장애물 감지 시스템을 사용하며, 이동 방향에 따라 안전 보호 영역(Safety Zone)을 동적으로 변경하여 충돌 위험을 최소화한다.

크랩 주행은 차량 방향을 유지한 채 원하는 위치로 직접 이동할 수 있는 매우 효율적인 기능이며, 제한된 공간에서 작업 효율과 위치 정밀도를 크게 향상시키는 스티어 드라이브의 대표적인 장점이다.

---

### 4.4 대각선 이동 (Diagonal Movement)

대각선 이동(Diagonal Movement)은 차량이 전후 방향과 좌우 방향을 동시에 이동하는 기능이다. 일반 차량처럼 먼저 직진한 후 방향을 바꾸는 것이 아니라, 원하는 목표 방향으로 직접 이동한다. 이러한 방식은 이동 거리를 줄이고 작업 시간을 단축하며, 산업 자동화 시스템의 생산성을 크게 향상시킨다.

중앙 제어기는 목표 종방향 속도와 횡방향 속도를 동시에 입력받으며, 필요에 따라 회전 속도도 함께 고려한다. 역기구학 알고리즘은 이 세 가지 운동 성분을 조합하여 각 바퀴의 최적 조향각과 회전 속도를 계산한다. 모든 바퀴는 결과 속도 벡터(Resultant Velocity Vector)를 향하도록 조향되고, 구동 모터는 해당 방향으로 추진력을 생성한다.

대각선 이동은 여러 번의 가속과 감속을 반복하지 않기 때문에 에너지 효율이 높다. 불필요한 중간 동작이 제거되므로 이동 시간이 단축되고, 타이어 마모와 기계적 충격도 감소한다. 하루 수천 번의 반복 작업이 이루어지는 산업 현장에서는 이러한 효율 향상이 매우 큰 경제적 효과를 가져온다.

복잡한 환경에서의 경로 계획(Path Planning)에서도 대각선 이동은 큰 장점을 제공한다. 장애물을 회피해야 하는 경우 차량은 멈추거나 회전하지 않고도 새로운 대각선 경로를 따라 자연스럽게 이동할 수 있다. 따라서 작업자의 이동이나 다른 차량과의 교차 상황에서도 매우 유연한 주행이 가능하다.

대각선 이동에서는 조향 최적화가 매우 중요하다. 동일한 이동 방향이라도 여러 가지 조향 구성이 가능하기 때문에 제어기는 조향 회전량, 에너지 소비, 전환 시간 및 액추에이터 마모를 종합적으로 고려하여 가장 효율적인 조향 구성을 선택한다.

조향과 구동의 지속적인 동기화 역시 필수적이다. 조향 엔코더는 모든 바퀴의 방향을 확인하고, 휠 엔코더는 회전 속도를 제어하며, 실시간 통신망은 모든 액추에이터를 동시에 제어하여 불필요한 횡력이나 차량 회전을 방지한다.

중량물을 운반하는 경우에는 대각선 이동 중 종방향과 횡방향 가속도가 동시에 발생하므로 적재 화물에 작용하는 관성력이 증가한다. 이를 방지하기 위해 제어기는 저크 제한(Jerk Limitation)과 적응형 가속도 제어를 적용하여 화물의 흔들림과 진동을 최소화한다.

센서 융합 역시 대각선 이동의 정밀도를 높인다. 휠 오도메트리(Odometry), IMU, 라이다 위치 인식 및 비전 센서 데이터를 융합하여 차량은 장거리 이동에서도 높은 위치 정확도를 유지한다.

자동 창고, 반도체 공장, 항공우주 조립 라인 및 스마트 팩토리에서는 대각선 이동을 이용하여 가장 짧은 경로를 따라 이동할 수 있다. 회전 횟수가 감소하고 이동 거리가 줄어들기 때문에 작업 시간이 단축되고, 배터리 소비와 타이어 마모도 감소한다.

결국 대각선 이동은 스티어 드라이브 플랫폼의 독립 조향과 독립 구동 능력을 가장 효율적으로 활용하는 이동 방식이다. 차량은 원하는 방향으로 즉시 이동할 수 있으며, 기동성, 위치 정밀도, 에너지 효율 및 생산성을 동시에 향상시킬 수 있다. 이러한 특성은 차세대 산업용 자율주행 이동로봇(AMR)이 다양한 제조 및 물류 환경에서 높은 성능을 발휘할 수 있도록 하는 핵심 기술 가운데 하나이다.

##  

## 05 Industrial applications

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Precision Docking Applications

Precision docking represents one of the most important industrial applications of steer drive technology. As autonomous mobile robots become increasingly integrated into automated manufacturing, semiconductor production, logistics, pharmaceutical processing, and precision inspection systems, the ability to repeatedly position a vehicle within millimeter-level tolerances has become a fundamental requirement. Unlike conventional mobile platforms that rely primarily on differential steering and skid-based corrections, steer drive robots achieve precise docking by independently controlling the steering angle and propulsion of every wheel module. This capability allows the robot to approach docking stations from virtually any direction while minimizing unnecessary vehicle rotation, tire slip, and positioning error.

The docking process typically consists of several sequential phases. During long-distance navigation, the robot follows a globally planned path generated by the fleet management system. As the vehicle approaches the target workstation, the navigation controller gradually transitions from global localization to local positioning using increasingly accurate sensor information. At intermediate distances, LiDAR-based localization, natural feature matching, or reflector-based navigation provides centimeter-level positioning accuracy. During the final approach, high-resolution cameras, laser displacement sensors, AprilTags, QR markers, or three-dimensional vision systems perform fine alignment. The steer drive controller combines these sensor measurements with wheel encoder and inertial measurement unit data to continuously refine the vehicle\'s pose estimation before issuing precise steering and velocity commands.

One of the greatest advantages of steer drive platforms during docking is the ability to perform direct lateral corrections. Conventional non-holonomic vehicles frequently require multiple forward and backward maneuvers combined with repeated rotations to eliminate positioning errors. Each corrective maneuver introduces additional uncertainty due to wheel slip and accumulated odometry error. A steer drive robot, however, can simply execute crab motion or diagonal movement while maintaining its orientation, allowing positional errors to be corrected directly. This significantly shortens docking time while improving repeatability and reducing mechanical wear.

Independent steering control also improves orientation accuracy. Many industrial processes require not only accurate position but also highly precise angular alignment. Automated charging stations, machine loading systems, robotic workcells, and precision inspection equipment often specify orientation tolerances below one degree. Since every steering module independently controls wheel orientation, the vehicle can perform extremely small angular adjustments without disturbing its translational position. Zero-radius rotation combined with low-speed steering control enables precise orientation correction immediately before docking is completed.

The drive motors contribute equally to docking precision by generating smooth, low-speed propulsion with high torque resolution. Instead of approaching the target using abrupt acceleration and braking, servo-controlled drive motors execute carefully optimized velocity profiles with limited jerk and gradual deceleration. This minimizes vibration throughout the vehicle and prevents oscillatory behavior near the final docking position. High-resolution encoders continuously monitor wheel displacement, allowing closed-loop controllers to regulate movement with sub-millimeter precision under appropriate sensor conditions.

Sensor fusion forms the technological foundation of precision docking. Wheel odometry provides short-term motion estimation, while inertial sensors compensate for temporary wheel slip and dynamic disturbances. LiDAR localization corrects accumulated positioning errors over longer travel distances, and vision systems perform high-precision alignment during the final docking phase. Some industrial applications further incorporate force sensors or compliant mechanical guides to absorb small residual positioning errors after physical contact with the docking fixture. Combining multiple sensing modalities significantly improves reliability under varying lighting conditions, floor contamination, or environmental disturbances.

Precision docking is particularly important in semiconductor manufacturing, where autonomous mobile robots transport wafer carriers between processing equipment. Even small positioning errors may interrupt automated loading sequences or damage expensive production assets. Similar requirements exist within automotive manufacturing, where mobile robots deliver heavy battery packs or body components to robotic assembly stations. In pharmaceutical production, accurate docking ensures sterile material transfer between automated processing units while minimizing human intervention. Inspection robots carrying high-resolution optical instruments also depend on repeatable docking to maintain calibration and measurement consistency.

Mechanical design contributes substantially to docking performance. High-rigidity chassis structures minimize structural deformation under heavy payloads, while precision steering bearings reduce compliance during low-speed motion. Low-backlash gearboxes improve steering accuracy, and integrated electromagnetic brakes stabilize wheel modules after positioning has been completed. Some industrial systems additionally employ passive centering mechanisms or tapered mechanical guides that compensate for residual positioning errors during the final engagement process.

Communication latency and control synchronization become increasingly important as positioning accuracy improves. Real-time industrial networks such as EtherCAT synchronize steering commands, drive motor control, encoder feedback, and sensor measurements with deterministic timing. Coordinated multi-axis control prevents transient wheel misalignment that could otherwise generate unwanted lateral forces or rotational disturbances during final positioning.

Safety remains an essential consideration throughout the docking procedure. Because docking frequently occurs in close proximity to expensive machinery and human operators, vehicle speed is progressively reduced as the target is approached. Dynamic safety zones shrink according to vehicle velocity, while obstacle detection systems continuously monitor the docking area. If unexpected obstacles or personnel enter the protected region, the motion controller immediately suspends docking and initiates a controlled stop without compromising vehicle stability.

As industrial automation continues advancing toward fully autonomous manufacturing environments, precision docking will become increasingly important. Higher production throughput, tighter dimensional tolerances, automated charging infrastructure, robotic machine tending, and intelligent manufacturing systems all require mobile robots capable of repeatedly achieving highly accurate positioning. Steer drive technology provides the independent steering, multidirectional mobility, and closed-loop motion control necessary to satisfy these demanding industrial requirements while maintaining high efficiency, reliability, and operational safety.

---

### 5.2 Confined Space Maneuvering Applications

Confined space maneuvering is another major application area in which steer drive technology demonstrates clear advantages over conventional mobile robot architectures. Modern manufacturing facilities, warehouses, semiconductor fabrication plants, pharmaceutical cleanrooms, and automated distribution centers are designed to maximize equipment density and floor utilization. As available maneuvering space becomes increasingly limited, autonomous mobile robots must navigate narrow aisles, crowded production cells, and complex machinery layouts while maintaining both safety and operational efficiency. The multidirectional mobility provided by steer drive systems makes them particularly well suited for these demanding environments.

Traditional differential drive vehicles often require substantial free space to change direction because turning involves coordinated forward motion combined with rotational movement. Even though differential drive platforms can theoretically perform zero-radius turns, repeated skid-based rotation introduces tire wear, floor abrasion, and positioning uncertainty. Furthermore, repositioning within confined spaces frequently requires multiple forward and reverse maneuvers before the desired orientation can be achieved. These additional movements increase travel time, reduce productivity, and create unnecessary traffic congestion in busy industrial facilities.

Steer drive robots overcome these limitations through independent control of every steering and drive module. Since each wheel can be oriented independently, the vehicle is capable of translating sideways, moving diagonally, or rotating about its own center without requiring additional clearance. Motion planning algorithms select the most efficient combination of steering angles and wheel velocities to reach the desired position while minimizing unnecessary body movement. This flexibility significantly reduces the geometric space required for navigation compared with conventional wheeled platforms.

Narrow aisle warehouses represent one of the most common confined-space applications. Storage density continues increasing as logistics operators seek to maximize inventory capacity within limited building footprints. Autonomous mobile robots transporting pallets or containers must travel through aisles only slightly wider than the vehicle itself while accurately stopping at designated storage locations. Crab motion enables direct lateral alignment with storage racks, eliminating repeated steering corrections. Diagonal movement shortens travel distance between adjacent storage positions, while zero-radius rotation allows rapid orientation changes at aisle intersections without occupying excessive floor space.

Semiconductor fabrication facilities present even more stringent spatial constraints. Expensive manufacturing equipment is densely arranged inside cleanrooms where floor area is extremely valuable. Mobile robots transporting wafer carriers must navigate between processing tools while avoiding contamination-sensitive equipment. The smooth rolling motion of steer drive platforms minimizes vibration and particle generation compared with skid-steering vehicles. Their ability to reposition laterally without body rotation further reduces collision risk when operating near high-value manufacturing assets.

Automotive production lines also benefit from confined-space maneuverability. Heavy autonomous mobile robots frequently transport battery packs, vehicle subassemblies, engines, or body components between robotic assembly stations. These production cells often contain industrial robots, safety fences, conveyors, and automated tooling that leave little room for vehicle maneuvering. Steer drive robots can approach assembly fixtures from optimized directions, perform lateral alignment, rotate in place when necessary, and depart along the shortest feasible trajectory without interrupting surrounding production activities.

Machine tending applications provide another excellent example. Mobile robots delivering raw materials or collecting finished products must position themselves precisely beside CNC machines, laser cutters, injection molding equipment, or additive manufacturing systems. Confined spaces around these machines rarely permit large turning radii. Independent wheel control allows the vehicle to execute highly efficient positioning maneuvers while maintaining sufficient clearance from machine structures and safety barriers.

Hospitals and pharmaceutical manufacturing facilities similarly require maneuverability within restricted environments. Autonomous transport robots navigate narrow corridors, elevators, laboratories, and sterile processing rooms where frequent interaction with personnel occurs. Smooth multidirectional motion enables the robot to avoid obstacles efficiently while minimizing disruption to surrounding human activity. The ability to shift laterally also simplifies docking with automated cabinets, medication dispensing systems, and laboratory workstations.

Effective confined-space operation depends heavily on sophisticated perception and motion planning algorithms. High-resolution LiDAR sensors continuously map surrounding obstacles while stereo cameras identify dynamic objects such as pedestrians or forklifts. Simultaneous Localization and Mapping algorithms maintain accurate vehicle localization despite limited navigation space. Model Predictive Control generates dynamically feasible trajectories that respect steering limitations, wheel acceleration constraints, and safety margins while exploiting the full multidirectional capability of the steer drive system.

Trajectory optimization becomes particularly important in dense industrial environments. Instead of minimizing travel distance alone, modern motion planners simultaneously optimize travel time, energy consumption, steering activity, collision risk, and passenger or payload comfort. Smooth steering transitions reduce actuator wear, while minimizing unnecessary steering reversals extends component service life and decreases maintenance requirements.

Safety systems remain continuously active throughout confined-space operation. Since obstacles may appear unexpectedly within short distances, steer drive robots employ adaptive speed control that automatically reduces vehicle velocity as available clearance decreases. Dynamic safety fields generated by safety LiDARs adjust according to vehicle speed and travel direction, ensuring adequate stopping distance under all operating conditions. If unexpected obstructions are detected, multidirectional braking capability enables rapid yet stable emergency stops without compromising vehicle control.

As industrial facilities continue pursuing higher automation density and improved space utilization, confined-space maneuverability will become an increasingly valuable capability. The combination of independent wheel control, holonomic motion, precise steering synchronization, advanced perception, and intelligent trajectory optimization enables steer drive robots to operate efficiently within environments that would be difficult or impractical for conventional mobile platforms. Consequently, steer drive technology is expected to play an increasingly central role in next-generation smart factories, automated warehouses, semiconductor manufacturing, pharmaceutical production, and other advanced industrial systems requiring high productivity within limited physical space.

---

### 5.1 정밀 도킹 적용 사례 (Precision Docking Applications)

정밀 도킹(Precision Docking)은 스티어 드라이브(Steer Drive) 기술이 가장 큰 효과를 발휘하는 산업 응용 분야 가운데 하나이다. 자율주행 이동로봇(AMR)이 자동화 제조, 반도체 생산, 물류 자동화, 제약 공정 및 정밀 검사 시스템에 점점 더 많이 적용되면서, 차량을 반복적으로 밀리미터 수준의 오차 내에서 정확하게 위치시키는 능력이 필수적인 요구사항이 되었다. 기존의 이동 플랫폼은 차동 조향(Differential Steering)과 바퀴의 미끄러짐(Skid)을 이용하여 최종 위치를 보정하는 경우가 많지만, 스티어 드라이브는 모든 바퀴의 조향각과 추진력을 독립적으로 제어함으로써 훨씬 높은 정밀도의 도킹을 수행할 수 있다. 이러한 특성 덕분에 차량은 어느 방향에서든 도킹 스테이션(Docking Station)에 접근할 수 있으며, 불필요한 차량 회전과 타이어 슬립을 최소화하면서 높은 위치 정확도를 유지할 수 있다.

정밀 도킹 과정은 일반적으로 여러 단계로 구성된다. 먼저 장거리 이동 구간에서는 플릿 관리 시스템(Fleet Management System)이 생성한 전역 경로(Global Path)를 따라 이동한다. 차량이 목표 설비에 가까워질수록 전역 위치 인식(Global Localization)에서 국부 위치 인식(Local Positioning)으로 제어 방식이 전환된다. 중간 거리에서는 라이다 기반 위치 인식(LiDAR Localization), 자연 특징 매칭(Natural Feature Matching), 반사판 기반 위치 인식(Reflector Navigation) 등을 이용하여 센티미터 수준의 위치 정확도를 확보한다. 마지막 접근 단계에서는 고해상도 카메라(High-resolution Camera), 레이저 변위 센서(Laser Displacement Sensor), 에이프릴태그(AprilTag), QR 마커(QR Marker), 3차원 비전 시스템(3D Vision System) 등을 활용하여 미세한 위치와 자세를 정렬한다. 스티어 드라이브 제어기는 이러한 센서 데이터를 휠 엔코더(Wheel Encoder)와 관성측정장치(IMU)의 정보와 융합하여 차량의 자세(Pose)를 지속적으로 보정하고, 최종적으로 매우 정밀한 조향 및 속도 명령을 생성한다.

스티어 드라이브의 가장 큰 장점은 **직접적인 측면 위치 보정(Direct Lateral Correction)**이 가능하다는 것이다. 일반적인 비홀로노믹 차량은 위치 오차를 줄이기 위해 여러 번의 전진과 후진, 그리고 반복적인 회전 동작을 수행해야 한다. 이러한 반복 동작은 휠 슬립과 오도메트리(Odometry) 오차를 증가시키고 도킹 시간을 길게 만든다. 반면 스티어 드라이브는 크랩 주행(Crab Motion)이나 대각선 이동(Diagonal Movement)을 이용하여 차량의 방향을 유지한 채 측면 위치만 직접 수정할 수 있다. 따라서 최종 위치 보정 시간이 크게 단축되고 반복 위치 정밀도(Repeatability)는 향상되며, 타이어와 기계 부품의 마모도 줄어든다.

독립 조향(Independent Steering)은 자세 정렬(Orientation Alignment)에도 큰 장점을 제공한다. 많은 산업 공정에서는 위치뿐만 아니라 차량의 방향도 매우 정확해야 한다. 자동 충전 시스템(Auto Charging System), 공작기계 자동 로딩(Machine Tending), 로봇 작업 셀(Robotic Workcell), 정밀 검사 장비는 대부분 1도 이하의 자세 오차를 요구한다. 스티어 드라이브는 모든 바퀴를 독립적으로 제어하므로 차량의 위치를 거의 변경하지 않고도 매우 작은 각도 보정을 수행할 수 있다. 제자리 회전(Zero Radius Rotation)과 저속 조향 제어(Low-speed Steering Control)를 결합하면 도킹 직전에 매우 정밀한 자세 조정이 가능하다.

구동 모터(Drive Motor) 역시 도킹 정밀도에 중요한 역할을 한다. 서보 제어(Servo Control)를 사용하는 구동 모터는 낮은 속도에서도 높은 토크 분해능(Torque Resolution)을 유지할 수 있으며, 갑작스러운 가속이나 급제동 없이 매우 부드러운 속도 프로파일(Velocity Profile)을 생성한다. 저크(Jerk)를 제한한 감속 제어는 차량 전체의 진동을 줄이고, 도킹 직전 발생할 수 있는 진동이나 오버슈트(Overshoot)를 방지한다. 또한 고해상도 엔코더는 바퀴의 이동량을 지속적으로 측정하여 적절한 센서 환경에서는 서브밀리미터(Sub-millimeter) 수준의 위치 제어도 가능하게 한다.

정밀 도킹의 핵심 기술은 **센서 융합(Sensor Fusion)**이다. 휠 오도메트리는 단기적인 이동량을 계산하고, IMU는 바퀴 슬립이나 외란을 보정한다. 라이다 기반 위치 인식은 장거리 이동에서 누적되는 오차를 제거하며, 비전 시스템(Vision System)은 최종 도킹 단계에서 매우 높은 위치 정렬 성능을 제공한다. 일부 산업용 시스템은 여기에 힘 센서(Force Sensor)나 순응형 기계 가이드(Compliant Mechanical Guide)를 추가하여, 물리적 접촉 이후에도 남아 있는 미세한 위치 오차를 자동으로 보정한다. 이처럼 다양한 센서를 결합하면 조명 변화, 바닥 오염, 환경 변화에도 안정적인 도킹 성능을 유지할 수 있다.

정밀 도킹은 다양한 산업 분야에서 매우 중요한 역할을 수행한다. 반도체 제조에서는 웨이퍼 캐리어(Wafer Carrier)를 공정 장비 사이로 운반하는 AMR이 밀리미터 수준의 정밀도로 정렬되어야 한다. 자동차 제조에서는 대형 배터리 팩이나 차체 부품을 로봇 조립 셀에 정확히 공급해야 하며, 작은 위치 오차도 생산 공정을 중단시킬 수 있다. 제약 공정에서는 무균 환경(Sterile Environment)을 유지하면서 자동 설비 간에 자재를 이송하기 위해 정밀 도킹이 필요하다. 또한 광학 검사 장비를 탑재한 이동 로봇은 반복적인 정밀 위치 정렬을 통해 검사 결과의 일관성과 장비 교정을 유지한다.

기계 구조(Mechanical Design)도 도킹 성능에 큰 영향을 준다. 강성이 높은 차체는 중량 하중에서도 변형을 최소화하며, 정밀 조향 베어링은 저속 주행 시 발생하는 구조적 유연성을 줄여준다. 백래시가 작은 감속기는 조향 오차를 최소화하고, 전자식 브레이크(Electromagnetic Brake)는 도킹 완료 후 바퀴를 안정적으로 고정한다. 일부 시스템은 테이퍼 형태의 기계식 가이드(Tapered Mechanical Guide)를 추가하여 남아 있는 미세한 위치 오차를 자동으로 흡수하기도 한다.

통신 지연과 제어 동기화(Control Synchronization)도 매우 중요하다. 이더캣(EtherCAT)과 같은 실시간 산업용 네트워크는 조향 명령, 구동 모터 제어, 엔코더 피드백 및 센서 데이터를 결정론적(Deterministic) 시간에 동기화한다. 이러한 다축 동기 제어는 최종 도킹 단계에서 발생할 수 있는 순간적인 바퀴 오정렬을 방지하고, 불필요한 횡력과 자세 변화를 최소화한다.

도킹 과정에서는 안전(Safety) 역시 중요한 요소이다. 차량은 고가의 설비나 작업자와 매우 가까운 거리에서 움직이므로, 목표에 접근할수록 속도를 점진적으로 줄인다. 또한 이동 속도에 따라 동적으로 안전 영역(Dynamic Safety Zone)을 조정하며, 장애물 감지 시스템은 도킹 영역을 지속적으로 감시한다. 예기치 않은 작업자나 장애물이 감지되면 차량은 즉시 도킹을 중단하고 안정적으로 정지한다.

스마트 팩토리(Smart Factory)가 더욱 고도화될수록 정밀 도킹의 중요성은 더욱 커질 것이다. 생산성 향상, 자동 충전, 공작기계 자동 로딩, 무인 검사 및 완전 자동화 생산 시스템은 모두 높은 위치 반복 정밀도를 요구한다. 스티어 드라이브는 독립 조향, 전방향 이동(Holonomic Motion), 폐루프 제어 및 고정밀 센서 융합을 기반으로 이러한 요구를 만족시키는 가장 효과적인 이동 플랫폼이라고 할 수 있다.

---

### 5.2 협소 공간 기동 적용 사례 (Confined Space Maneuvering Applications)

협소 공간 기동(Confined Space Maneuvering)은 스티어 드라이브 기술이 기존 이동 로봇보다 뛰어난 성능을 발휘하는 또 하나의 대표적인 응용 분야이다. 현대의 제조 공장, 물류 창고, 반도체 클린룸(Cleanroom), 제약 생산시설 및 자동화 물류센터는 제한된 공간 안에서 최대한 많은 설비를 배치하기 위해 매우 높은 공간 활용률(Space Utilization)을 추구한다. 그 결과 자율주행 이동로봇은 좁은 통로, 밀집된 생산 셀, 복잡한 설비 사이를 안전하고 효율적으로 이동해야 한다. 스티어 드라이브의 전방향 이동 능력은 이러한 환경에서 매우 큰 장점을 제공한다.

기존 차동 구동 차량은 방향을 변경하기 위해 회전과 전진을 동시에 수행해야 하므로 상당한 여유 공간이 필요하다. 이론적으로는 제자리 회전도 가능하지만, 실제로는 바퀴를 미끄러뜨리면서 회전하기 때문에 타이어 마모, 바닥 손상 및 위치 오차가 발생한다. 또한 좁은 공간에서 위치를 수정하기 위해 여러 번의 전진과 후진을 반복해야 하는 경우가 많으며, 이는 이동 시간을 증가시키고 다른 차량과의 혼잡을 유발한다.

스티어 드라이브는 이러한 문제를 독립 조향과 독립 구동을 통해 해결한다. 모든 바퀴가 독립적으로 조향되므로 차량은 좌우 이동, 대각선 이동, 제자리 회전을 자유롭게 수행할 수 있으며, 추가적인 회전 공간이 거의 필요하지 않다. 운동 계획(Motion Planning) 알고리즘은 목표 위치까지 이동하기 위한 가장 효율적인 조향각과 바퀴 속도를 계산하여 불필요한 차량 움직임을 최소화한다. 결과적으로 동일한 작업을 훨씬 작은 공간에서 수행할 수 있다.

좁은 통로 창고(Narrow Aisle Warehouse)는 이러한 기술이 가장 많이 적용되는 분야이다. 창고 운영자는 저장 밀도를 높이기 위해 통로 폭을 최소화하려고 하며, AMR은 차량 폭보다 약간 넓은 공간만을 이용하여 팔레트와 자재를 운반해야 한다. 크랩 주행은 선반과의 측면 정렬을 매우 쉽게 수행할 수 있게 하며, 대각선 이동은 인접한 저장 위치 사이를 가장 짧은 거리로 이동하게 한다. 또한 제자리 회전은 교차로에서 추가 공간 없이 방향을 변경할 수 있게 하여 전체 이동 효율을 높인다.

반도체 제조 시설에서는 공간 제약이 더욱 심하다. 고가의 공정 장비가 매우 밀집되어 있으며, 클린룸 내부에서는 미세한 진동과 입자 발생도 최소화해야 한다. 스티어 드라이브는 바퀴를 미끄러뜨리지 않고 자연스럽게 굴러가기 때문에 진동과 파티클(Particle) 발생이 적으며, 차량을 회전시키지 않고도 측면 위치를 수정할 수 있어 장비와의 충돌 위험도 줄어든다.

자동차 생산라인에서도 협소 공간 기동은 매우 중요하다. 중량급 AMR은 배터리 팩, 엔진, 차체 부품 등을 로봇 조립 셀로 운반하는데, 작업 공간은 산업용 로봇, 컨베이어, 안전 펜스 및 각종 설비로 둘러싸여 있다. 스티어 드라이브는 최적의 방향으로 접근하고, 측면 이동으로 정렬하며, 필요하면 제자리 회전을 수행한 후 가장 짧은 경로로 작업 공간을 빠져나갈 수 있다. 이 과정에서 주변 생산 활동을 거의 방해하지 않는다.

공작기계 자동 로딩(Machine Tending) 역시 대표적인 적용 사례이다. CNC, 레이저 절단기, 사출성형기 및 적층 제조(Additive Manufacturing) 장비는 주변 공간이 매우 좁다. 스티어 드라이브는 최소한의 회전 공간으로 설비 옆에 정확하게 위치할 수 있으며, 기계 구조물과 안전 펜스 사이에서도 높은 정밀도로 이동할 수 있다.

병원과 제약 공장에서도 협소 공간 기동은 중요한 기능이다. 이동 로봇은 좁은 복도, 엘리베이터, 실험실 및 무균 작업 공간을 이동하면서 사람과 지속적으로 상호작용해야 한다. 스티어 드라이브는 방향을 크게 바꾸지 않고도 장애물을 회피할 수 있으며, 약품 보관함이나 자동 분배 장치와도 매우 정밀하게 정렬할 수 있다.

협소 공간 주행을 위해서는 고성능 인식 기술이 필수적이다. 고해상도 라이다는 주변 환경을 실시간으로 스캔하고, 스테레오 카메라는 작업자나 지게차와 같은 동적 장애물을 인식한다. SLAM 알고리즘은 좁은 공간에서도 정확한 위치를 유지하며, 모델 예측 제어(MPC)는 조향 한계, 바퀴 가속도 및 안전 거리를 고려하여 가장 적합한 경로를 생성한다.

최신 경로 계획 알고리즘은 단순히 이동 거리를 줄이는 것에 그치지 않는다. 이동 시간, 에너지 소비, 조향 횟수, 충돌 위험 및 적재 화물의 안정성까지 동시에 최적화한다. 부드러운 조향 전환은 액추에이터의 마모를 줄이고, 불필요한 조향 반전을 최소화하여 유지보수 비용도 감소시킨다.

안전 시스템은 협소 공간에서 더욱 중요한 역할을 한다. 장애물이 매우 가까운 거리에서 나타날 수 있기 때문에 차량은 주변 공간에 따라 속도를 자동으로 조절한다. 안전 라이다는 이동 방향과 속도에 따라 안전 영역을 동적으로 변경하며, 예상치 못한 장애물이 감지되면 차량은 즉시 안정적으로 정지한다.

산업 현장이 점점 더 높은 공간 활용률과 자동화를 추구할수록 협소 공간 기동 능력의 중요성은 더욱 커질 것이다. 독립 휠 제어, 홀로노믹 이동(Holonomic Motion), 정밀 조향 동기화, 고성능 센서 융합 및 지능형 경로 최적화를 결합한 스티어 드라이브 플랫폼은 기존 이동 플랫폼으로는 어려웠던 환경에서도 높은 생산성과 안전성을 동시에 제공할 수 있다. 따라서 스티어 드라이브는 차세대 스마트 팩토리, 자동 창고, 반도체 제조, 제약 생산 및 첨단 산업 자동화 시스템의 핵심 이동 기술로 더욱 널리 활용될 것으로 전망된다.
