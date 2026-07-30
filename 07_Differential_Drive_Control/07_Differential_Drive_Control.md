**Differential Drive & Steer Drive Engineering**


# Chapter 07 Differential Drive Control

##  

## 01 Drive Control Architecture

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Drive control architecture is the foundation of every differential-drive mobile robot. Regardless of whether the robot is a small 50 kg logistics AMR or a heavy industrial platform carrying more than one ton of payload, the quality of the drive control architecture directly affects motion stability, positioning accuracy, safety, energy efficiency, and overall system reliability. Modern industrial AMRs no longer rely on simple motor control loops. Instead, they implement a layered control structure that separates mission planning, motion planning, vehicle control, and motor-level control into independent but interconnected subsystems. This approach allows engineers to develop, validate, and maintain complex robotic systems while ensuring scalability and fault isolation.

The drive control architecture must also support communication between numerous distributed devices, including motor drivers, encoders, safety controllers, battery management systems, LiDAR sensors, IMUs, cameras, and industrial I/O modules. As AMR performance requirements continue to increase, especially in precision docking and heavy-load transportation applications, the control architecture becomes a critical design factor rather than merely a software implementation detail.

---

### 1.1 Hierarchical Control Structure

The hierarchical control structure is the most widely adopted architecture in modern industrial robotics because it allows complex control functions to be divided into manageable layers. Each layer has a specific responsibility and communicates with adjacent layers through clearly defined interfaces.

At the highest level is the mission control layer. This layer receives commands from fleet management systems, manufacturing execution systems, warehouse management systems, or human operators. The mission layer is responsible for deciding what the robot should accomplish rather than how the robot should physically move. Typical mission commands include transporting materials between stations, performing inspections, docking at charging stations, or executing predefined production tasks.

Below the mission layer is the navigation and path planning layer. This layer converts mission objectives into a sequence of navigable paths. The planner utilizes maps, obstacle information, traffic rules, and localization data to generate safe and efficient trajectories. For differential drive robots, this layer typically generates target linear and angular velocities that respect vehicle kinematic constraints.

The next layer is the motion control layer. This layer acts as a bridge between navigation algorithms and low-level motor controllers. The motion controller calculates the wheel velocities required to achieve the desired vehicle motion. In a differential drive robot, the target vehicle velocity is converted into left and right wheel velocity commands through inverse kinematic calculations. The motion controller also performs trajectory tracking, velocity limiting, acceleration management, and jerk reduction to ensure smooth operation.

Below the motion controller is the drive controller layer. This layer is responsible for regulating individual wheel behavior. Each motor receives velocity or torque commands and attempts to follow those commands accurately. The drive controller usually executes at a much higher frequency than the navigation controller. While navigation updates may occur at 10 Hz to 50 Hz, motor control loops often operate at frequencies between 1 kHz and 20 kHz.

Within the drive controller, multiple nested control loops are commonly implemented. The innermost loop is typically a current control loop. Current control directly regulates motor torque because motor torque is proportional to current. This loop must operate at very high frequencies to respond quickly to load disturbances.

Outside the current loop is the velocity control loop. The velocity controller compares the target wheel speed with the measured wheel speed and adjusts motor current accordingly. Most industrial servo drives implement PI control algorithms for velocity regulation because they provide stable and accurate speed control under varying loads.

The outermost loop is often a position control loop. Position control is particularly important for precise docking operations and low-speed positioning tasks. The controller continuously compares the desired position with encoder feedback and generates velocity references for the lower-level velocity controller.

Sensor feedback plays a critical role throughout the hierarchical structure. Encoders provide wheel position and velocity measurements. IMUs provide angular velocity and acceleration information. LiDAR systems contribute localization and obstacle detection data. Vision systems provide environmental perception and docking guidance. All sensor information is fused to improve control accuracy and robustness.

One major advantage of the hierarchical architecture is modularity. Engineers can modify the navigation algorithm without redesigning motor controllers. Similarly, motor hardware can be upgraded without changing fleet management software. This separation significantly reduces development complexity and supports long-term system maintenance.

Fault isolation is another important benefit. If a navigation module encounters an error, motor controllers can continue maintaining safe operation. Likewise, if communication with the fleet management server is interrupted, local motion controllers can safely stop the robot without affecting lower-level stability.

In heavy-duty industrial AMRs, hierarchical control structures become even more important because multiple subsystems must operate simultaneously. A one-ton inspection robot may require synchronized control of drive motors, steering actuators, sensor platforms, robotic manipulators, and safety systems. Without a structured hierarchy, system complexity rapidly becomes unmanageable.

As robotic systems continue evolving toward autonomous fleets and AI-driven operation, hierarchical control architectures remain the preferred engineering approach because they provide scalability, maintainability, reliability, and safety across a wide range of industrial applications.

---

### 1.2 EtherCAT vs CANopen

Communication networks form the backbone of a drive control architecture. Even the most sophisticated control algorithms cannot achieve high performance if information cannot be exchanged reliably and deterministically between controllers and actuators. Among industrial robot communication technologies, EtherCAT and CANopen are two of the most commonly used fieldbus protocols.

CANopen is built upon the Controller Area Network (CAN) standard. Originally developed for automotive applications, CAN became popular in industrial automation due to its simplicity, robustness, and low implementation cost. CANopen adds higher-level communication services, device profiles, and object dictionaries that standardize communication among industrial devices.

A CANopen network typically operates at speeds up to 1 Mbps. Devices communicate through message arbitration, where message priority determines bus access. This architecture works well for systems with moderate bandwidth requirements and relatively slow update rates.

For small and medium-sized differential drive AMRs, CANopen often provides sufficient performance. Typical applications include robots carrying payloads below 500 kg, operating at speeds under 2 m/s, and requiring moderate positioning accuracy. CANopen networks are widely supported by motor drivers, battery management systems, sensors, and safety devices, making integration relatively straightforward.

One of CANopen\'s major advantages is cost efficiency. Hardware requirements are modest, cabling is simple, and configuration tools are widely available. For many commercial AMRs, CANopen offers an attractive balance between performance and cost.

However, CANopen also has limitations. Network bandwidth is relatively low compared to modern industrial Ethernet technologies. As the number of nodes increases, communication latency becomes less predictable. Synchronization accuracy is also limited, which can affect multi-axis motion control applications.

EtherCAT was developed specifically to overcome these limitations. EtherCAT is an Ethernet-based fieldbus that provides extremely high-speed and deterministic communication. Unlike conventional Ethernet networks, EtherCAT processes data while packets pass through each node. This architecture minimizes communication delays and maximizes bandwidth utilization.

EtherCAT networks commonly operate at 100 Mbps, which is one hundred times faster than a typical CANopen network. More importantly, EtherCAT provides deterministic timing behavior. Every device receives data at precisely predictable intervals, enabling highly synchronized control.

For advanced AMRs, EtherCAT offers significant advantages. High-frequency control loops can exchange information with minimal latency. Multiple drive axes can be synchronized with microsecond-level precision. Sensor fusion systems can receive time-aligned data from multiple sources. Complex robotic platforms with numerous actuators can operate as a coordinated system.

In steer-drive AMRs, EtherCAT is often considered essential. A four-wheel independent steering system may require synchronization of eight servo axes, including four drive motors and four steering motors. Achieving smooth crab motion, zero-radius turning, and precision docking would be extremely difficult without deterministic communication.

EtherCAT also supports distributed clocks, allowing all devices on the network to share a common time reference. This capability is valuable for motion control, data logging, sensor synchronization, and safety applications.

From a system architecture perspective, EtherCAT enables centralized control strategies where a master controller coordinates all devices in real time. CANopen systems often rely more heavily on distributed intelligence because communication bandwidth is more limited.

The trade-off is increased complexity and cost. EtherCAT devices are generally more expensive than CANopen devices. Configuration procedures can be more sophisticated, and engineering teams require greater expertise in industrial Ethernet technologies. Network diagnostics and troubleshooting may also demand specialized tools.

For lightweight logistics robots, CANopen remains a practical and economical solution. For heavy-duty industrial AMRs, high-precision inspection robots, autonomous mobile manipulators, and advanced steer-drive platforms, EtherCAT increasingly becomes the preferred choice due to its superior synchronization, bandwidth, and deterministic performance.

In modern industrial robotics, the selection between EtherCAT and CANopen is not simply a communication decision. It is a strategic architectural decision that influences achievable control performance, scalability, future expansion capability, and overall system competitiveness. As AMRs evolve toward higher payloads, tighter positioning tolerances, and increasingly autonomous operation, EtherCAT continues to gain prominence as the communication backbone of next-generation robotic drive control systems.

구동 제어 아키텍처(Drive Control Architecture)는 모든 차동 구동형(Differential Drive) 모바일 로봇의 핵심 기반이다. 50kg급 물류 AMR부터 1톤 이상의 고중량 산업용 플랫폼까지, 구동 제어 구조의 품질은 주행 안정성, 위치 정밀도, 안전성, 에너지 효율, 그리고 시스템 전체 신뢰성을 결정한다. 현대 산업용 AMR은 단순한 모터 제어 루프만으로 동작하지 않는다. 대신 미션(Mission), 경로 계획(Path Planning), 차량 제어(Vehicle Control), 모터 제어(Motor Control)를 계층적으로 분리한 구조를 사용한다. 이러한 방식은 시스템 복잡도를 효과적으로 관리하면서 유지보수성과 확장성을 크게 향상시킨다.

또한 구동 제어 아키텍처는 모터 드라이버(Motor Driver), 엔코더(Encoder), 안전 제어기(Safety Controller), 배터리 관리 시스템(Battery Management System, BMS), LiDAR, IMU, 카메라(Camera), 산업용 입출력(I/O) 장치와 같은 다양한 구성요소 간의 통신을 지원해야 한다. 최근 산업용 AMR은 정밀 도킹(Precision Docking)과 고중량 운반 능력을 요구받고 있기 때문에 제어 아키텍처는 단순한 소프트웨어 구조가 아니라 전체 시스템 성능을 결정하는 핵심 설계 요소로 인식되고 있다.

---

### 1.1 계층형 제어 구조(Hierarchical Control Structure)

계층형 제어 구조(Hierarchical Control Structure)는 현대 산업용 로봇에서 가장 널리 사용되는 제어 아키텍처이다. 이는 복잡한 제어 기능을 여러 계층으로 나누어 각 계층이 명확한 역할을 수행하도록 설계된다.

가장 상위에는 미션 제어 계층(Mission Control Layer)이 존재한다. 이 계층은 플릿 관리 시스템(Fleet Management System), 제조 실행 시스템(Manufacturing Execution System, MES), 창고 관리 시스템(Warehouse Management System, WMS), 또는 작업자로부터 명령을 수신한다. 미션 계층은 로봇이 무엇을 해야 하는지를 결정하며, 어떻게 움직일 것인지는 하위 계층에 위임한다. 예를 들어 자재 운반, 자동 검사, 충전 스테이션 도킹, 생산 공정 지원 등의 작업이 여기에 해당한다.

그 아래에는 내비게이션 및 경로 계획 계층(Navigation and Path Planning Layer)이 위치한다. 이 계층은 미션 목표를 실제 이동 가능한 경로로 변환한다. 지도(Map), 장애물 정보, 교통 규칙, 위치 추정 결과를 활용하여 안전하고 효율적인 경로를 생성한다. 차동 구동 로봇에서는 일반적으로 선속도(Linear Velocity)와 각속도(Angular Velocity) 목표값을 생성한다.

다음은 모션 제어 계층(Motion Control Layer)이다. 이 계층은 내비게이션 알고리즘과 모터 제어기 사이의 중간 역할을 수행한다. 목표 차량 속도를 좌측 및 우측 바퀴 속도로 변환하는 역기구학(Inverse Kinematics) 계산을 수행하며, 궤적 추종(Trajectory Tracking), 속도 제한(Velocity Limiting), 가속도 관리(Acceleration Management), 저크 감소(Jerk Reduction) 등의 기능도 담당한다.

그 아래에는 구동 제어 계층(Drive Controller Layer)이 존재한다. 이 계층은 개별 바퀴의 동작을 직접 제어한다. 각 모터는 목표 속도 또는 토크(Torque) 명령을 수신하고 이를 정확하게 추종한다. 일반적으로 모션 제어기는 10\~50Hz 정도로 동작하지만, 모터 제어 루프는 1kHz\~20kHz 수준의 훨씬 높은 주기로 동작한다.

구동 제어기 내부에는 여러 개의 중첩 제어 루프(Nested Control Loop)가 존재한다. 가장 안쪽에는 전류 제어 루프(Current Control Loop)가 위치한다. 모터 토크는 전류에 비례하기 때문에 전류 제어는 사실상 토크 제어와 동일한 의미를 가진다. 이 루프는 외란(Disturbance)에 빠르게 대응하기 위해 매우 높은 주파수로 동작한다.

그 외부에는 속도 제어 루프(Velocity Control Loop)가 존재한다. 속도 제어기는 목표 속도와 실제 속도를 비교하여 필요한 전류를 계산한다. 대부분의 산업용 서보 드라이브(Servo Drive)는 PI 제어기(Proportional-Integral Controller)를 사용하여 속도를 제어한다.

가장 바깥쪽에는 위치 제어 루프(Position Control Loop)가 존재한다. 이는 정밀 도킹이나 저속 위치 결정 작업에서 매우 중요하다. 위치 오차를 계산하여 목표 속도를 생성하고 이를 하위 속도 제어기에 전달한다.

센서 피드백(Sensor Feedback)은 전체 계층 구조에서 핵심적인 역할을 수행한다. 엔코더는 바퀴 위치와 속도를 측정하고, IMU는 각속도와 가속도 정보를 제공한다. LiDAR는 위치 추정(Localization)과 장애물 탐지를 담당하며, 비전 시스템(Vision System)은 환경 인식과 정밀 정렬 기능을 제공한다. 이러한 센서 데이터는 융합(Sensor Fusion)을 통해 보다 정확한 제어 성능을 제공한다.

계층형 구조의 가장 큰 장점은 모듈성(Modularity)이다. 예를 들어 내비게이션 알고리즘을 변경하더라도 모터 제어기를 수정할 필요가 없으며, 반대로 모터 하드웨어를 교체하더라도 상위 소프트웨어는 그대로 사용할 수 있다. 따라서 시스템 유지보수와 확장이 매우 용이하다.

또 다른 장점은 고장 격리(Fault Isolation)이다. 내비게이션 계층에 문제가 발생하더라도 모터 제어기는 안정적으로 동작할 수 있으며, 플릿 서버와의 통신이 끊어지더라도 로봇은 안전 정지(Safe Stop)를 수행할 수 있다.

특히 1톤 이상의 고중량 산업용 AMR에서는 계층형 구조의 중요성이 더욱 커진다. 이러한 플랫폼은 구동 모터, 조향 모듈(Steering Module), 검사 장비, 센서 플랫폼, 로봇 암(Robot Arm), 안전 시스템 등을 동시에 제어해야 한다. 계층형 구조가 없다면 시스템 복잡도는 급격히 증가하여 개발과 유지보수가 사실상 불가능해진다.

향후 AI 기반 자율주행 시스템과 대규모 플릿 운영 환경에서도 계층형 제어 구조는 확장성(Scalability), 유지보수성(Maintainability), 신뢰성(Reliability), 안전성(Safety)을 제공하는 가장 효과적인 접근 방식으로 계속 활용될 것이다.

---

### 1.2 이더캣(EtherCAT) 대 CANopen

통신 네트워크(Communication Network)는 구동 제어 아키텍처의 핵심 요소이다. 아무리 우수한 제어 알고리즘을 사용하더라도 제어기와 구동 장치 간에 정보를 정확하고 안정적으로 전달할 수 없다면 원하는 성능을 얻을 수 없다. 산업용 로봇 분야에서는 EtherCAT과 CANopen이 가장 널리 사용되는 필드버스(Fieldbus) 기술이다.

CANopen은 CAN(Controller Area Network)을 기반으로 만들어진 프로토콜이다. 원래 자동차 산업을 위해 개발된 CAN은 높은 신뢰성과 낮은 비용 덕분에 산업 자동화 분야에서도 널리 사용되었다. CANopen은 여기에 장치 프로파일(Device Profile), 객체 사전(Object Dictionary), 통신 서비스(Communication Service)를 추가하여 산업용 장치 간의 표준화된 통신을 제공한다.

CANopen 네트워크는 일반적으로 최대 1Mbps 수준의 통신 속도를 제공한다. 여러 장치가 하나의 버스를 공유하며 메시지 우선순위(Message Priority)에 따라 통신 순서가 결정된다. 이러한 구조는 비교적 낮은 대역폭 요구사항과 완만한 제어 주기를 가진 시스템에 적합하다.

소형 또는 중형 차동 구동 AMR에서는 CANopen만으로도 충분한 경우가 많다. 예를 들어 500kg 이하의 물류 AMR이나 2m/s 이하 속도로 운행하는 플랫폼에서는 CANopen이 안정적인 성능을 제공할 수 있다. 또한 대부분의 모터 드라이버, BMS, 센서 장비들이 CANopen을 지원하기 때문에 통합 작업도 비교적 쉽다.

CANopen의 가장 큰 장점은 비용 효율성(Cost Efficiency)이다. 하드웨어 비용이 낮고 배선 구조가 단순하며 개발 경험을 가진 엔지니어도 많다. 따라서 상용 AMR에서는 여전히 매우 널리 사용된다.

하지만 CANopen에는 한계도 존재한다. 네트워크 대역폭이 제한적이며 장치 수가 증가할수록 통신 지연(Latency)이 증가한다. 또한 정확한 시간 동기화(Time Synchronization)가 어려워 다축 제어(Multi-Axis Control)에서는 성능 제한이 발생할 수 있다.

EtherCAT은 이러한 문제를 해결하기 위해 개발된 산업용 이더넷(Industrial Ethernet) 기반 통신 기술이다. EtherCAT은 데이터 프레임이 각 노드를 통과하는 과정에서 실시간으로 데이터를 처리하는 독특한 구조를 사용한다. 따라서 매우 높은 통신 효율과 낮은 지연 시간을 제공한다.

EtherCAT은 일반적으로 100Mbps 속도로 동작하며 이는 CANopen보다 약 100배 빠른 수준이다. 더욱 중요한 것은 결정론적 통신(Deterministic Communication)을 제공한다는 점이다. 모든 장치는 정확히 예측 가능한 시점에 데이터를 수신하므로 정밀 제어가 가능하다.

고성능 산업용 AMR에서는 EtherCAT이 매우 큰 장점을 제공한다. 고주파 제어 루프를 안정적으로 운용할 수 있으며, 여러 구동축을 마이크로초(μs) 수준으로 동기화할 수 있다. 또한 다양한 센서 데이터를 시간적으로 정렬하여 처리할 수 있다.

특히 조향 구동(Steer Drive) AMR에서는 EtherCAT이 사실상 필수 기술로 간주된다. 4WS(4-Wheel Steering) 기반 플랫폼은 4개의 구동 모터와 4개의 조향 모터를 동시에 제어해야 하며, 크랩 모션(Crab Motion), 제로 반경 회전(Zero Radius Turn), 정밀 도킹을 구현하기 위해서는 매우 높은 동기화 성능이 요구된다.

EtherCAT은 분산 클럭(Distributed Clock) 기능도 제공한다. 이를 통해 네트워크 내 모든 장치가 동일한 기준 시간을 공유할 수 있으며, 이는 모션 제어(Motion Control), 센서 동기화(Sensor Synchronization), 데이터 로깅(Data Logging), 안전 시스템(Safety System)에서 매우 중요한 역할을 한다.

시스템 구조 관점에서 EtherCAT은 중앙 집중형 제어(Centralized Control)를 가능하게 한다. 하나의 중앙 제어기가 모든 장치를 실시간으로 관리할 수 있기 때문이다. 반면 CANopen은 상대적으로 대역폭이 낮아 각 장치에 더 많은 로컬 제어 기능을 분산시키는 경우가 많다.

그러나 EtherCAT은 CANopen보다 복잡성과 비용이 높다. 장치 가격이 비싸고, 네트워크 구성 및 진단에도 더 높은 수준의 전문성이 요구된다.

결과적으로 소형 물류 AMR에서는 CANopen이 경제적이고 충분한 선택이 될 수 있다. 반면 고중량 산업용 AMR, 정밀 검사 로봇, 모바일 매니퓰레이터(Mobile Manipulator), 그리고 ±20mm 이하 정밀 도킹을 목표로 하는 조향 구동 플랫폼에서는 EtherCAT이 사실상 표준적인 선택이 되고 있다.

오늘날 산업용 로봇에서 EtherCAT과 CANopen의 선택은 단순한 통신 프로토콜 결정이 아니다. 이는 전체 시스템 성능, 확장성, 향후 업그레이드 가능성, 그리고 제품 경쟁력을 결정하는 중요한 아키텍처 설계 결정이라고 할 수 있다. 특히 힐스로보틱스(Hills Robotics)가 개발 중인 500kg\~1.5톤급 산업용 AMR 플랫폼에서는 EtherCAT 기반 아키텍처가 중장기적으로 더 적합한 선택이 될 가능성이 높다.

##  

## 02 Speed Control

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Speed control is one of the most fundamental functions in a differential drive mobile robot. Regardless of whether the robot is a small logistics platform operating in a warehouse or a heavy industrial AMR transporting loads above one ton, stable and accurate wheel speed control directly determines motion smoothness, path tracking accuracy, energy efficiency, and overall system reliability. The speed controller acts as the bridge between high-level motion commands and the physical motor drive system. It receives target wheel velocities generated by the motion controller and continuously adjusts motor torque to minimize the difference between commanded and actual wheel speed.

In industrial robotics, speed control is typically implemented within the servo drive itself and operates at a significantly higher update rate than navigation or trajectory planning layers. While navigation controllers may operate at frequencies between 10 Hz and 50 Hz, speed control loops commonly execute at frequencies between 500 Hz and several kilohertz. This high execution rate allows the controller to react quickly to load disturbances, friction changes, slope variations, payload shifts, and wheel-ground interaction effects.

A well-designed speed control system must achieve several objectives simultaneously. It must respond rapidly to command changes, maintain stability under varying loads, minimize steady-state error, suppress oscillations, and provide smooth acceleration and deceleration behavior. These requirements become increasingly important in industrial environments where robots frequently operate near humans, expensive equipment, and production machinery.

Modern differential drive AMRs generally employ closed-loop speed control based on encoder feedback. Wheel encoders continuously measure actual rotational speed, and this information is compared against the desired reference velocity. The resulting error becomes the basis for corrective control actions. Various control strategies exist, including proportional-integral-derivative control, model predictive control, adaptive control, and intelligent control approaches. However, the vast majority of industrial systems still rely on PI-based speed control due to its simplicity, robustness, and proven effectiveness.

The performance of speed control has a direct influence on higher-level functions. Poor speed control leads to trajectory tracking errors, localization drift, increased wheel slip, excessive motor heating, and degraded docking accuracy. Conversely, a properly tuned speed controller allows the navigation layer to operate more effectively because commanded motions are executed predictably and consistently.

In heavy-duty AMRs carrying payloads exceeding 500 kg, speed control becomes even more critical because system inertia increases significantly. Larger inertia means greater resistance to acceleration and deceleration changes. Without proper speed regulation, the robot may overshoot velocity commands, experience oscillatory behavior, or generate excessive mechanical stress on the drivetrain.

For these reasons, speed control is often considered the foundation upon which all higher-level vehicle control functions are built. Before advanced navigation algorithms can achieve their desired performance, the underlying wheel speed regulation system must first be accurate, stable, and robust.

---

### 2.1 PI Speed Controller Design

The PI speed controller is the most commonly used speed regulation algorithm in industrial servo systems and mobile robots. Its widespread adoption is due to its balance between simplicity, computational efficiency, robustness, and control performance. Despite the availability of more advanced control methods, PI control remains the industry standard for wheel speed regulation in differential drive robots.

The fundamental purpose of the PI controller is to minimize the speed error between the target wheel velocity and the measured wheel velocity. The controller continuously calculates this error and generates an output command that drives the motor toward the desired operating point.

The proportional component of the controller responds directly to the instantaneous speed error. When a large error exists, the proportional term generates a correspondingly large corrective action. This behavior allows the controller to react quickly to changes in velocity commands and external disturbances. Increasing proportional gain generally improves responsiveness and reduces rise time. However, excessive proportional gain can introduce oscillations, instability, and mechanical vibration.

The integral component accumulates speed error over time. Even if the proportional term significantly reduces error, small residual errors may remain due to friction, load disturbances, or motor nonlinearities. The integral term gradually compensates for these residual errors until the steady-state speed error approaches zero. This characteristic is particularly important in mobile robots because maintaining accurate wheel speed over long travel distances directly affects odometry accuracy.

The design process usually begins with development of a simplified motor model. Engineers analyze motor inertia, gearbox characteristics, wheel dynamics, friction effects, and expected payload conditions. Based on these parameters, initial gain values are selected through analytical methods, simulation, or empirical tuning.

One commonly used tuning approach involves increasing proportional gain until the system approaches oscillatory behavior. The gain is then reduced to a stable value, after which integral gain is gradually introduced to eliminate residual steady-state error. This process often requires iterative refinement under actual operating conditions.

In differential drive robots, each wheel typically possesses an independent PI speed controller. The left and right wheels may experience different loading conditions due to floor irregularities, uneven payload distribution, or turning maneuvers. Independent control allows each wheel to compensate for local disturbances while maintaining overall vehicle stability.

Speed controller performance is commonly evaluated using several criteria. Rise time measures how quickly the wheel reaches the commanded velocity. Settling time indicates how rapidly oscillations disappear after a speed change. Overshoot quantifies the extent to which actual speed exceeds the desired value. Steady-state error measures long-term tracking accuracy. Disturbance rejection capability evaluates the controller's response to unexpected load changes.

For heavy industrial AMRs, tuning becomes more challenging because vehicle inertia changes significantly depending on payload. A robot carrying no load behaves differently from the same robot transporting 1000 kg. Some advanced systems therefore implement gain scheduling techniques, allowing controller parameters to adapt according to operating conditions.

Another important consideration is interaction with lower-level current control loops. In most servo systems, the speed controller generates torque or current commands rather than directly controlling motor voltage. The current controller then executes these commands with high bandwidth. Proper coordination between current and speed loops ensures stable multi-loop operation.

When properly designed, a PI speed controller provides reliable, predictable, and accurate wheel speed regulation across a wide range of operating conditions. Its proven performance explains why it remains the dominant speed control method in industrial mobile robotics.

---

### 2.2 Feedforward Compensation

Although PI controllers provide excellent speed regulation, they inherently operate as feedback systems. Feedback control reacts after an error occurs. When a velocity command changes suddenly, the controller must first observe the resulting error before generating corrective action. This reactive behavior introduces unavoidable response delays.

Feedforward compensation addresses this limitation by predicting the required control effort before significant speed error develops. Instead of relying solely on error correction, feedforward control estimates the torque needed to achieve the desired motion and applies this command proactively.

In mobile robots, feedforward compensation is especially valuable because many motion commands are predictable. The desired velocity, acceleration, and trajectory are already known before motion begins. This information can be used to estimate the motor torque required to produce the requested movement.

The simplest feedforward implementation is velocity feedforward. In this approach, motor commands are generated directly from the target speed reference. When the desired wheel velocity increases, the controller immediately applies additional torque without waiting for speed error to develop.

A more advanced approach incorporates acceleration feedforward. Since acceleration requires force and force requires torque, knowledge of the desired acceleration allows the controller to estimate inertial torque requirements. This capability becomes particularly beneficial for heavy-load AMRs where vehicle inertia dominates system behavior.

Feedforward compensation can also account for rolling resistance, drivetrain friction, gear efficiency losses, and slope-induced gravitational forces. For example, when a robot begins climbing a ramp, additional torque is required to overcome gravity. A feedforward model can anticipate this requirement and apply corrective torque before wheel speed begins to decrease.

The interaction between feedback and feedforward control is often described as complementary. Feedforward control handles predictable system behavior, while feedback control corrects modeling errors and unexpected disturbances. Neither method alone is sufficient. Feedforward models are never perfectly accurate because real-world systems contain uncertainties, parameter variations, and nonlinear effects. Feedback control remains necessary to compensate for these inaccuracies.

One major benefit of feedforward compensation is improved trajectory tracking performance. Because corrective action is applied proactively, velocity commands are followed more accurately. Overshoot is reduced, settling time decreases, and overall motion smoothness improves. This enhancement becomes particularly important during docking operations, where precise speed regulation influences final positioning accuracy.

Another advantage is reduced control effort from the feedback controller. Since feedforward control performs much of the required work, the PI controller experiences smaller error signals. This reduction can improve stability margins and decrease the likelihood of oscillatory behavior.

In industrial AMRs operating at high payloads, feedforward compensation often enables significant performance improvements without requiring major increases in controller gain. Instead of aggressively tuning the PI controller, engineers can use feedforward models to achieve faster responses while preserving stability.

Modern robotic systems frequently integrate multiple feedforward components simultaneously. Velocity feedforward, acceleration feedforward, friction compensation, slope compensation, and payload-dependent compensation may all contribute to the final motor command. Combined with a well-tuned PI controller, these techniques produce highly responsive and accurate speed control performance.

As industrial mobile robots continue to demand greater precision, higher payload capacity, and smoother motion quality, feedforward compensation has become a standard feature of advanced drive control systems. Together with PI feedback control, it forms the foundation of high-performance wheel speed regulation in modern differential drive AMRs.

속도 제어(Speed Control)는 차동 구동(Differential Drive) 모바일 로봇에서 가장 기본적이면서도 중요한 제어 기능 중 하나이다. 소형 물류 AMR부터 1톤 이상의 고중량 산업용 AMR까지, 바퀴 속도를 얼마나 정확하고 안정적으로 제어할 수 있는지가 주행 안정성, 경로 추종 정확도, 에너지 효율, 그리고 시스템 전체 신뢰성을 결정한다.

속도 제어기는 상위 모션 제어기(Motion Controller)와 실제 모터 시스템 사이의 연결 역할을 수행한다. 모션 제어기로부터 목표 바퀴 속도(Target Wheel Velocity)를 전달받고, 실제 바퀴 속도와 비교하여 오차를 최소화하도록 모터 토크(Motor Torque)를 조절한다.

산업용 로봇에서는 일반적으로 속도 제어가 서보 드라이브(Servo Drive) 내부에서 수행되며, 내비게이션(Navigation)이나 경로 계획(Path Planning)보다 훨씬 높은 주기로 동작한다. 내비게이션 제어기가 보통 10\~50Hz 정도로 동작하는 반면, 속도 제어 루프는 500Hz에서 수 kHz 수준으로 실행된다. 이러한 고속 제어는 부하 변화, 마찰 변화, 경사면 주행, 적재물 이동, 바퀴와 바닥 간의 접촉 변화 등에 신속하게 대응할 수 있도록 한다.

우수한 속도 제어 시스템은 여러 목표를 동시에 만족해야 한다. 목표 속도에 빠르게 도달해야 하며, 다양한 하중 조건에서도 안정성을 유지해야 하고, 정상 상태 오차(Steady-State Error)를 최소화해야 한다. 또한 진동(Oscillation)을 억제하면서 부드러운 가속 및 감속 특성을 제공해야 한다. 이러한 특성은 사람과 함께 작업하는 산업 현장에서 특히 중요하다.

현대 AMR은 대부분 엔코더(Encoder) 기반의 폐루프 제어(Closed-Loop Control)를 사용한다. 엔코더가 측정한 실제 속도를 목표 속도와 비교하여 오차를 계산하고, 이를 기반으로 제어 명령을 생성한다. 속도 제어에는 PID 제어(PID Control), 모델 예측 제어(Model Predictive Control, MPC), 적응 제어(Adaptive Control) 등 다양한 방법이 존재하지만, 실제 산업 현장에서는 PI 제어(Proportional-Integral Control)가 가장 널리 사용된다.

속도 제어 성능은 상위 시스템에도 직접적인 영향을 준다. 속도 제어가 불안정하면 경로 추종 오차(Path Tracking Error)가 증가하고, 위치 추정(Odometry) 오차가 누적되며, 바퀴 슬립(Slip)이 증가하고, 도킹 정밀도도 저하된다. 반대로 속도 제어가 우수하면 내비게이션 시스템은 보다 정확하게 동작할 수 있으며, 로봇의 움직임을 예측하기 쉬워진다.

특히 500kg 이상의 고중량 AMR에서는 관성(Inertia)이 매우 커지기 때문에 속도 제어의 중요성이 더욱 증가한다. 큰 관성은 가속과 감속을 어렵게 만들며, 적절한 속도 제어가 없으면 목표 속도를 초과하거나 진동이 발생할 수 있다. 또한 구동계(Drivetrain)에 과도한 기계적 스트레스가 발생할 수도 있다.

결과적으로 속도 제어는 모든 상위 제어 기능의 기반이 된다. 아무리 뛰어난 자율주행 알고리즘을 적용하더라도 바퀴 속도를 정확하게 제어할 수 없다면 원하는 수준의 성능을 달성하기 어렵다.

---

### 2.1 PI 속도 제어기 설계(PI Speed Controller Design)

PI 속도 제어기(PI Speed Controller)는 산업용 서보 시스템과 모바일 로봇에서 가장 널리 사용되는 속도 제어 알고리즘이다. 단순한 구조를 가지면서도 높은 성능과 우수한 안정성을 제공하기 때문에 현재까지도 산업 현장의 표준으로 사용되고 있다.

PI 제어기의 기본 목적은 목표 속도와 실제 속도 사이의 오차를 최소화하는 것이다. 제어기는 지속적으로 속도 오차를 계산하고, 이를 기반으로 모터에 전달할 제어 명령을 생성한다.

비례 항(Proportional Term)은 현재 순간의 속도 오차에 비례하여 동작한다. 오차가 크면 큰 제어 출력을 생성하고, 오차가 작으면 작은 출력을 생성한다. 따라서 비례 제어는 빠른 응답 특성을 제공한다. 비례 게인(Proportional Gain)을 증가시키면 응답 속도는 향상되지만 지나치게 높으면 진동과 불안정성이 발생할 수 있다.

적분 항(Integral Term)은 오차를 시간에 따라 누적하여 계산한다. 비례 제어만 사용할 경우 작은 오차가 지속적으로 남을 수 있는데, 적분 제어는 이러한 정상 상태 오차를 제거하는 역할을 수행한다.

모바일 로봇에서는 장시간 이동 중에도 바퀴 속도를 정확하게 유지해야 한다. 작은 속도 오차가 누적되면 수 미터 이상의 위치 오차로 이어질 수 있기 때문에 적분 항은 매우 중요한 역할을 수행한다.

PI 제어기 설계는 일반적으로 모터 모델(Motor Model) 분석에서 시작된다. 엔지니어는 모터 관성(Motor Inertia), 감속기(Gearbox) 특성, 바퀴 동역학(Wheel Dynamics), 마찰(Friction), 예상 적재 하중 등을 고려하여 초기 게인을 결정한다.

실제 튜닝(Tuning) 과정에서는 비례 게인을 점진적으로 증가시켜 시스템이 진동하기 직전의 값을 찾는다. 이후 안정적인 수준으로 약간 낮춘 다음 적분 게인을 추가하여 잔여 오차를 제거한다. 이러한 과정은 실제 운행 조건에서 반복적으로 수행된다.

차동 구동 로봇에서는 좌측 바퀴와 우측 바퀴가 각각 독립적인 PI 제어기를 가진다. 바닥 상태나 적재물 배치에 따라 좌우 바퀴의 부하가 달라질 수 있기 때문이다. 독립 제어 구조를 통해 각 바퀴는 개별적으로 외란을 보상하면서 전체 차량의 안정성을 유지할 수 있다.

PI 속도 제어기의 성능은 여러 기준으로 평가된다. 상승 시간(Rise Time)은 목표 속도에 도달하는 시간을 의미한다. 정착 시간(Settling Time)은 속도 변화 후 진동이 사라질 때까지 걸리는 시간이다. 오버슈트(Overshoot)는 실제 속도가 목표 속도를 초과하는 정도를 나타낸다. 정상 상태 오차는 장기적인 추종 정확도를 의미한다.

고중량 산업용 AMR에서는 적재물에 따라 관성이 크게 변하기 때문에 PI 제어기 설계가 더욱 어려워진다. 무부하 상태와 1000kg 적재 상태는 전혀 다른 동적 특성을 가진다. 따라서 일부 고급 시스템은 게인 스케줄링(Gain Scheduling)을 적용하여 운행 조건에 따라 PI 게인을 자동으로 변경한다.

또한 PI 속도 제어기는 일반적으로 하위의 전류 제어 루프(Current Control Loop)와 함께 사용된다. 속도 제어기는 직접 전압을 제어하는 것이 아니라 토크 또는 전류 명령을 생성하고, 전류 제어기가 이를 실행한다. 이러한 다중 루프 구조(Multi-Loop Structure)는 높은 응답성과 안정성을 동시에 제공한다.

적절하게 설계된 PI 속도 제어기는 다양한 운행 환경에서도 안정적이고 정확한 속도 제어를 제공한다. 이러한 이유로 PI 제어는 현재도 산업용 모바일 로봇에서 가장 널리 사용되는 속도 제어 방식으로 자리 잡고 있다.

---

### 2.2 피드포워드 보상(Feedforward Compensation)

PI 제어기는 매우 우수한 성능을 제공하지만 본질적으로 피드백 제어(Feedback Control) 방식이다. 즉 오차가 발생한 이후에야 이를 수정할 수 있다. 목표 속도가 갑자기 변경되면 제어기는 먼저 오차를 감지한 뒤에야 대응할 수 있기 때문에 일정한 지연이 발생한다.

피드포워드 보상(Feedforward Compensation)은 이러한 한계를 극복하기 위해 사용된다. 피드포워드 제어는 오차가 발생하기 전에 필요한 제어량을 미리 예측하여 적용한다.

모바일 로봇에서는 목표 속도, 목표 가속도, 이동 경로가 이미 알려져 있기 때문에 이를 활용하여 필요한 모터 토크를 사전에 계산할 수 있다.

가장 단순한 형태는 속도 피드포워드(Velocity Feedforward)이다. 목표 속도 값으로부터 직접 모터 제어 출력을 생성하여 속도 변화에 즉시 대응한다.

더 발전된 방식은 가속도 피드포워드(Acceleration Feedforward)이다. 가속도를 만들기 위해서는 힘이 필요하며, 힘을 만들기 위해서는 토크가 필요하다. 따라서 목표 가속도를 알고 있다면 필요한 토크를 미리 계산할 수 있다.

이러한 방식은 특히 고중량 AMR에서 매우 효과적이다. 차량 관성이 크기 때문에 단순 PI 제어만으로는 원하는 응답 속도를 얻기 어려운 경우가 많다.

피드포워드 보상은 마찰(Friction), 구동계 손실(Drivetrain Loss), 감속기 효율(Gear Efficiency), 경사면 중력 영향(Gravity Effect)까지 고려할 수 있다.

예를 들어 로봇이 경사로를 오르기 시작하면 중력 때문에 추가 토크가 필요하다. 피드포워드 모델은 이를 사전에 예측하여 필요한 토크를 미리 공급할 수 있다. 결과적으로 속도 저하 없이 안정적인 주행이 가능해진다.

피드백 제어와 피드포워드 제어는 서로 보완적인 관계를 가진다. 피드포워드는 예측 가능한 동작을 처리하고, 피드백은 모델 오차와 외란을 보상한다.

피드포워드만 사용하는 것은 현실적으로 불가능하다. 실제 시스템은 항상 모델 오차(Model Error), 비선형성(Nonlinearity), 파라미터 변화(Parameter Variation)를 포함하기 때문이다. 따라서 피드백 제어는 반드시 필요하다.

피드포워드 보상의 가장 큰 장점 중 하나는 궤적 추종 성능(Trajectory Tracking Performance)을 향상시킨다는 점이다. 미리 필요한 제어량을 제공하기 때문에 속도 변화에 더욱 빠르게 대응할 수 있다. 오버슈트는 감소하고 정착 시간은 짧아지며 전체적인 주행 품질도 향상된다.

또한 PI 제어기의 부담을 줄여준다. 피드포워드가 대부분의 제어 작업을 수행하기 때문에 PI 제어기는 작은 오차만 보정하면 된다. 이는 안정성 향상과 진동 감소로 이어진다.

고중량 산업용 AMR에서는 PI 게인을 과도하게 높이지 않고도 높은 응답성을 얻을 수 있다는 점에서 매우 큰 장점을 가진다.

현대 산업용 로봇에서는 속도 피드포워드, 가속도 피드포워드, 마찰 보상(Friction Compensation), 경사 보상(Slope Compensation), 적재 하중 보상(Payload Compensation) 등을 동시에 사용하는 경우가 많다.

결과적으로 PI 피드백 제어(PI Feedback Control)와 피드포워드 보상은 현대 AMR 구동 제어 시스템의 핵심 구성 요소이다. 두 기술이 결합될 때 고정밀, 고응답, 고안정성의 속도 제어가 가능해지며, 이는 산업용 차동 구동 AMR의 성능을 결정하는 중요한 기반이 된다.

##  

## 03 Position Control

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Position control is one of the most important functions in a differential drive mobile robot because it directly determines where the robot ultimately stops, docks, or performs a task. While speed control regulates how fast the wheels rotate, position control ensures that the robot reaches the intended destination with the required level of accuracy. In industrial environments, positioning performance affects charging station docking, material transfer operations, inspection alignment, machine loading, collaborative robot interaction, and many other mission-critical functions.

A mobile robot continuously receives target positions generated by navigation systems, fleet management software, or predefined task sequences. The position control system compares the target position with the actual robot position and generates corrective motion commands to reduce the error. These commands are then translated into velocity references and eventually into motor torque commands through lower-level control loops.

In a typical industrial AMR, position control operates as the outermost layer of a multi-loop control architecture. The position controller generates desired velocity commands, the velocity controller regulates wheel speed, and the current controller manages motor torque production. This hierarchical approach allows each control layer to focus on a specific aspect of motion control while maintaining overall system stability.

The importance of position control becomes increasingly evident as accuracy requirements increase. For general warehouse transportation, positioning errors of several centimeters may be acceptable. However, precision docking applications often require repeatability better than ±20 mm. Automated charging stations, robotic arm handoff operations, inspection equipment alignment, and production line integration frequently demand even tighter tolerances.

Position control performance depends on many factors. Accurate sensor feedback is essential because the controller must know the robot\'s current position. Odometry, IMU data, LiDAR localization, vision-based localization, and absolute reference markers may all contribute to determining the robot's actual position. Mechanical factors such as wheel slip, floor conditions, drivetrain backlash, and payload-induced deformation can also affect positioning accuracy.

A major challenge in mobile robotics is that position errors accumulate over time. Small velocity tracking errors can gradually grow into large position deviations. Therefore, position control systems must continuously compensate for these errors and ensure long-term accuracy. This requirement becomes particularly important for large industrial facilities where robots travel hundreds of meters during normal operation.

Modern industrial robots often combine position control with localization systems that provide global position references. Instead of relying solely on wheel encoders, advanced AMRs use sensor fusion techniques to improve positioning reliability. As a result, the position controller receives more accurate state estimates and can achieve higher levels of precision.

Position control is therefore not simply a motion function. It is a critical capability that determines whether the robot can successfully perform its intended industrial tasks. A well-designed position control system enables precise docking, repeatable operation, improved safety, and greater productivity across a wide range of applications.

---

### 3.1 PID Position Controller

The PID position controller is one of the most widely used position regulation algorithms in industrial automation and robotics. PID stands for Proportional, Integral, and Derivative control, representing three independent mechanisms that work together to reduce position error and improve system performance.

The primary objective of the PID controller is to minimize the difference between the target position and the actual position. This difference is known as position error. By continuously monitoring the error and applying corrective actions, the controller drives the robot toward the desired location.

The proportional component generates an output that is directly proportional to the position error. If the robot is far from the target position, the proportional term produces a large corrective action. As the robot approaches the target, the control effort decreases. This characteristic provides rapid response and intuitive behavior. However, proportional control alone typically leaves a residual steady-state error and may not achieve the desired level of positioning precision.

The integral component accumulates position error over time. If a small error persists for an extended period, the integral term gradually increases until sufficient corrective action is generated. This mechanism eliminates steady-state error and improves final positioning accuracy. In industrial docking applications, the integral term often plays an important role in achieving millimeter-level repeatability.

The derivative component responds to the rate of change of position error. Instead of focusing solely on current error magnitude, it predicts future behavior based on error trends. If the robot is approaching the target too quickly, the derivative term applies damping action that reduces overshoot and oscillation. This predictive capability improves stability and shortens settling time.

In a differential drive AMR, the PID position controller typically generates velocity commands rather than directly controlling motors. The position controller operates as an outer loop that produces target velocities for the speed controller. This arrangement allows each control layer to operate at an appropriate frequency and simplifies controller tuning.

Tuning a PID controller requires balancing responsiveness and stability. Increasing proportional gain improves responsiveness but may introduce oscillation. Increasing integral gain improves accuracy but can cause slow oscillations or integral windup. Increasing derivative gain improves damping but may amplify measurement noise.

Several tuning methods are commonly used in industrial robotics. Empirical tuning remains popular because it allows engineers to observe actual system behavior under realistic operating conditions. Analytical methods based on dynamic models can provide initial gain estimates, while simulation tools allow extensive validation before deployment.

Heavy-duty AMRs introduce additional tuning challenges because system dynamics vary significantly with payload. A robot carrying 100 kg behaves differently from the same platform carrying 1000 kg. To address this issue, some systems employ gain scheduling, adaptive control, or model-based compensation techniques that adjust controller behavior according to operating conditions.

Position controllers are often evaluated using performance metrics such as rise time, settling time, overshoot, steady-state error, and repeatability. In industrial environments, repeatability is often more important than absolute accuracy because docking stations and production equipment are designed around predictable robot behavior.

Modern industrial robots frequently combine PID control with trajectory generation algorithms. Instead of commanding abrupt position changes, smooth trajectories are generated with controlled acceleration and deceleration profiles. This approach reduces mechanical stress, improves passenger comfort for transported loads, and enhances overall system reliability.

Despite the development of advanced control techniques such as Model Predictive Control and Adaptive Control, PID controllers remain dominant because they provide an excellent balance between simplicity, robustness, computational efficiency, and practical performance.

---

### 3.2 Absolute Encoder Utilization

Position control performance depends heavily on the quality of position feedback. Among the various sensing technologies available, the absolute encoder has become one of the most important devices for industrial mobile robotics because it provides direct and unambiguous position information.

Unlike incremental encoders, which measure relative movement through pulse counting, absolute encoders provide a unique position value for every shaft angle. This means the encoder always knows its actual position, even after power loss or system restart. As soon as power is restored, the controller can immediately determine the shaft position without performing homing procedures.

This capability offers significant advantages in industrial applications. Mobile robots often operate continuously in production environments where minimizing downtime is essential. If a power interruption occurs, an absolute encoder allows the system to resume operation quickly without requiring manual intervention or recalibration.

Absolute encoders are commonly installed on motor shafts, gearbox outputs, steering mechanisms, lifting actuators, and other motion-control components. In differential drive robots, they may be used to measure wheel rotation directly or indirectly through motor shaft monitoring.

Single-turn absolute encoders provide unique position information within one mechanical revolution. Multi-turn absolute encoders extend this capability by tracking multiple revolutions, making them suitable for applications involving large travel distances or gear reduction systems.

Position controllers benefit greatly from absolute encoder feedback because accurate position information reduces uncertainty. The controller can calculate position error more precisely and generate more effective corrective actions. Improved feedback quality directly translates into better positioning accuracy and repeatability.

Another major advantage is improved startup behavior. Incremental encoder systems typically require homing operations after power-up. During homing, the robot moves until it reaches a reference marker, establishing a known position. This process consumes time and may create operational constraints. Absolute encoders eliminate this requirement because the reference position is inherently available.

Absolute encoders also enhance safety. In emergency stop situations, the controller can accurately determine actuator positions immediately after system recovery. This capability reduces the risk of unexpected movements and supports safe restart procedures.

Modern industrial networks such as EtherCAT, CANopen, and industrial Ethernet protocols frequently support direct integration of absolute encoder data. High-resolution digital communication improves measurement accuracy and simplifies system architecture.

For precision docking applications, absolute encoders play a crucial role in achieving repeatable final positioning. Small encoder errors can translate into significant vehicle position errors, especially when accumulated over long travel distances. High-resolution absolute encoders reduce these errors and improve control system confidence.

In heavy industrial AMRs, absolute encoders are often combined with additional sensors such as IMUs, LiDAR systems, vision systems, and GNSS receivers. Sensor fusion techniques integrate these data sources to create highly accurate state estimates. The position controller then uses these estimates to achieve reliable and repeatable operation under varying environmental conditions.

As industrial robots continue to demand greater accuracy, reliability, and autonomy, absolute encoders have become a standard component of advanced position control systems. Their ability to provide immediate, precise, and persistent position information makes them indispensable for modern mobile robotics and high-performance industrial automation.

위치 제어(Position Control)는 모바일 로봇이 최종적으로 어디에 정지하고, 도킹(Docking)하며, 작업을 수행하는지를 결정하는 핵심 기능이다. 속도 제어(Speed Control)가 바퀴의 회전 속도를 제어한다면, 위치 제어는 로봇이 목표 위치(Target Position)에 정확하게 도달하도록 보장한다. 산업 현장에서는 위치 제어 성능이 충전 스테이션 도킹, 자재 이송, 검사 장비 정렬, 설비 로딩, 협동 로봇(Collaborative Robot) 연계 작업 등 다양한 응용 분야의 성공 여부를 결정한다.

모바일 로봇은 내비게이션 시스템(Navigation System), 플릿 관리 시스템(Fleet Management System), 또는 작업 시퀀스(Task Sequence)로부터 목표 위치를 전달받는다. 위치 제어 시스템은 현재 위치와 목표 위치를 비교하여 위치 오차(Position Error)를 계산하고, 이 오차를 줄이기 위한 제어 명령을 생성한다. 생성된 명령은 속도 제어기(Velocity Controller)와 전류 제어기(Current Controller)를 거쳐 최종적으로 모터 토크(Motor Torque)로 변환된다.

일반적인 산업용 AMR에서는 위치 제어가 다중 루프 제어 구조(Multi-Loop Control Structure)의 가장 바깥쪽 루프를 구성한다. 위치 제어기는 목표 속도를 생성하고, 속도 제어기는 바퀴 속도를 제어하며, 전류 제어기는 모터 토크를 생성한다. 이러한 계층형 구조(Hierarchical Structure)는 각 제어 계층이 자신의 역할에 집중할 수 있도록 하면서 전체 시스템의 안정성을 유지한다.

위치 제어의 중요성은 요구 정밀도가 높아질수록 더욱 커진다. 일반적인 물류 운송에서는 수 센티미터 정도의 오차가 허용될 수 있지만, 정밀 도킹(Precision Docking)에서는 ±20mm 이하의 반복 정밀도(Repeatability)가 요구된다. 자동 충전 시스템(Auto Charging System), 로봇 암(Robot Arm)과의 작업 인계, 검사 장비 위치 정렬 등은 더욱 높은 수준의 정밀도를 필요로 한다.

위치 제어 성능은 여러 요소에 의해 영향을 받는다. 우선 위치 제어기는 현재 위치를 정확히 알아야 하므로 센서 피드백(Sensor Feedback)의 품질이 매우 중요하다. 오도메트리(Odometry), IMU, LiDAR 기반 위치 추정(Localization), 비전 기반 위치 인식(Vision Localization), 절대 위치 마커(Absolute Reference Marker) 등이 모두 현재 위치 계산에 활용될 수 있다.

또한 바퀴 슬립(Wheel Slip), 바닥 상태(Floor Condition), 감속기 백래시(Gearbox Backlash), 적재 하중에 의한 구조 변형(Structural Deformation) 등 기계적인 요소들도 위치 정확도에 영향을 준다.

모바일 로봇의 가장 큰 특징 중 하나는 위치 오차가 시간이 지남에 따라 누적된다는 점이다. 작은 속도 오차라도 장시간 이동하면 큰 위치 오차로 발전할 수 있다. 따라서 위치 제어 시스템은 지속적으로 이러한 오차를 보상하여 장거리 운행에서도 높은 정확도를 유지해야 한다.

현대 산업용 AMR은 휠 엔코더(Wheel Encoder)만 사용하는 것이 아니라 다양한 센서를 융합하는 센서 융합(Sensor Fusion) 기술을 적용한다. 이를 통해 보다 정확한 위치 정보를 얻고, 결과적으로 위치 제어기의 성능을 향상시킨다.

결국 위치 제어는 단순히 로봇을 움직이는 기능이 아니라, 산업 현장에서 로봇이 실제 업무를 성공적으로 수행할 수 있도록 하는 핵심 기술이다. 우수한 위치 제어 시스템은 정밀 도킹, 반복 작업, 안전성 향상, 생산성 향상을 가능하게 한다.

---

### 3.1 PID 위치 제어기(PID Position Controller)

PID 위치 제어기(PID Position Controller)는 산업 자동화와 로봇 분야에서 가장 널리 사용되는 위치 제어 알고리즘이다. PID는 비례(Proportional), 적분(Integral), 미분(Derivative)의 세 가지 제어 요소를 의미하며, 이들이 함께 동작하여 위치 오차를 최소화한다.

PID 제어기의 기본 목표는 목표 위치와 실제 위치 사이의 차이를 줄이는 것이다. 이 차이를 위치 오차(Position Error)라고 하며, 제어기는 지속적으로 이를 계산하여 보정 동작을 수행한다.

비례 항(Proportional Term)은 현재 위치 오차에 비례한 제어 출력을 생성한다. 로봇이 목표 위치에서 멀리 떨어져 있으면 큰 제어 출력을 생성하고, 가까워질수록 제어 출력을 줄인다. 따라서 빠른 응답성을 제공하지만, 비례 제어만으로는 정상 상태 오차(Steady-State Error)가 남는 경우가 많다.

적분 항(Integral Term)은 오차를 시간에 따라 누적하여 계산한다. 작은 오차가 장시간 지속되면 적분 값이 증가하면서 이를 제거하기 위한 추가 제어력을 생성한다. 따라서 최종 위치 정확도를 향상시키고 정상 상태 오차를 제거하는 데 중요한 역할을 수행한다.

산업용 도킹 시스템에서는 적분 항이 밀리미터(mm) 수준의 반복 정밀도를 달성하는 데 매우 중요한 역할을 한다.

미분 항(Derivative Term)은 오차 변화율(Error Rate of Change)에 반응한다. 현재 오차뿐 아니라 오차가 얼마나 빠르게 변하는지를 고려하기 때문에 미래 동작을 예측하는 효과를 가진다. 로봇이 목표 위치에 너무 빠르게 접근할 경우 미분 항은 제동 효과(Damping Effect)를 제공하여 오버슈트(Overshoot)와 진동(Oscillation)을 줄인다.

차동 구동 AMR에서는 PID 위치 제어기가 일반적으로 직접 모터를 제어하지 않는다. 대신 목표 속도(Velocity Reference)를 생성하고, 속도 제어기가 이를 추종하도록 한다. 이러한 다중 루프 구조는 각 제어 계층의 역할을 분리하여 설계를 단순화하고 안정성을 향상시킨다.

PID 튜닝(Tuning)은 응답성과 안정성의 균형을 맞추는 과정이다. 비례 게인(Proportional Gain)을 높이면 응답은 빨라지지만 진동 위험이 증가한다. 적분 게인(Integral Gain)을 높이면 정확도는 향상되지만 저주파 진동이 발생할 수 있다. 미분 게인(Derivative Gain)을 높이면 안정성이 증가하지만 센서 노이즈(Noise)에 민감해질 수 있다.

산업용 로봇에서는 경험 기반 튜닝(Empirical Tuning)이 널리 사용된다. 실제 환경에서 시스템 반응을 관찰하면서 게인을 조정하기 때문이다. 또한 시뮬레이션(Simulation)과 동역학 모델(Dynamic Model)을 이용한 초기 설계도 자주 활용된다.

고중량 AMR에서는 적재 하중에 따라 시스템 동특성이 크게 달라진다. 동일한 로봇이라도 100kg 적재 상태와 1000kg 적재 상태는 완전히 다른 거동을 보인다. 이를 해결하기 위해 게인 스케줄링(Gain Scheduling), 적응 제어(Adaptive Control), 모델 기반 보상(Model-Based Compensation) 등의 기법이 사용되기도 한다.

위치 제어기는 일반적으로 상승 시간(Rise Time), 정착 시간(Settling Time), 오버슈트(Overshoot), 정상 상태 오차, 반복 정밀도(Repeatability) 등의 성능 지표로 평가된다. 산업 현장에서는 절대 정확도(Absolute Accuracy)보다 반복 정밀도가 더 중요한 경우가 많다.

현대 AMR은 PID 제어와 함께 궤적 생성(Trajectory Generation) 기능을 결합하는 경우가 많다. 목표 위치를 갑자기 변경하는 대신 가속도와 감속도가 제한된 부드러운 경로를 생성하여 기계적 스트레스를 줄이고 전체 시스템 신뢰성을 향상시킨다.

MPC(Model Predictive Control)와 적응 제어 등 고급 알고리즘이 등장했음에도 불구하고 PID 제어기는 단순성, 안정성, 계산 효율성, 실용성을 모두 만족하기 때문에 여전히 산업용 위치 제어의 표준으로 사용되고 있다.

---

### 3.2 절대형 엔코더 활용(Absolute Encoder Utilization)

위치 제어 성능은 위치 피드백(Position Feedback)의 품질에 크게 의존한다. 다양한 위치 센서 중에서도 절대형 엔코더(Absolute Encoder)는 산업용 모바일 로봇에서 가장 중요한 위치 측정 장치 중 하나로 자리 잡고 있다.

증분형 엔코더(Incremental Encoder)는 펄스(Pulse)를 카운트하여 상대적인 이동량을 측정한다. 반면 절대형 엔코더는 회전축의 각도마다 고유한 위치 값을 제공한다. 따라서 전원이 꺼지더라도 현재 위치 정보를 잃어버리지 않는다.

전원이 다시 인가되면 제어기는 즉시 현재 위치를 알 수 있으며, 별도의 원점 복귀(Homing) 작업이 필요하지 않다.

이러한 특성은 산업 환경에서 매우 큰 장점을 제공한다. 생산 라인은 정지 시간이 최소화되어야 하며, 전원 장애 이후 빠른 복구가 중요하다. 절대형 엔코더는 시스템이 즉시 정상 운전 상태로 복귀할 수 있도록 지원한다.

절대형 엔코더는 모터 축(Motor Shaft), 감속기 출력축(Gearbox Output Shaft), 조향 메커니즘(Steering Mechanism), 리프팅 액추에이터(Lifting Actuator) 등 다양한 곳에 설치된다. 차동 구동 로봇에서는 바퀴 회전량을 직접 측정하거나 모터 회전량을 통해 간접적으로 위치를 계산하는 데 사용된다.

단일 회전 절대형 엔코더(Single-Turn Absolute Encoder)는 한 바퀴 이내에서 절대 위치를 제공한다. 다중 회전 절대형 엔코더(Multi-Turn Absolute Encoder)는 여러 회전까지 추적할 수 있어 장거리 이동 시스템이나 고감속 기어 시스템에 적합하다.

절대형 엔코더는 위치 제어기의 정확도를 크게 향상시킨다. 위치 오차를 보다 정확하게 계산할 수 있기 때문에 제어기의 보정 동작도 더욱 효과적으로 수행된다. 결과적으로 위치 정확도와 반복 정밀도가 향상된다.

또 다른 장점은 시동(Start-Up) 과정의 단순화이다. 증분형 엔코더 시스템은 전원이 켜질 때마다 원점 복귀를 수행해야 하지만, 절대형 엔코더는 이러한 과정이 필요 없다.

절대형 엔코더는 안전성(Safety) 향상에도 기여한다. 비상 정지(Emergency Stop) 이후에도 현재 위치를 정확하게 알 수 있기 때문에 예기치 않은 움직임 없이 안전하게 재시작할 수 있다.

현대 산업용 네트워크인 EtherCAT, CANopen, 산업용 이더넷(Industrial Ethernet)은 절대형 엔코더 데이터를 직접 지원한다. 디지털 통신을 통해 높은 해상도(Resolution)와 높은 정확도를 유지할 수 있으며, 시스템 구조도 단순화된다.

정밀 도킹 시스템에서는 절대형 엔코더가 매우 중요한 역할을 한다. 작은 엔코더 오차라도 장거리 이동 시 수 센티미터 이상의 위치 오차로 확대될 수 있다. 고해상도 절대형 엔코더는 이러한 누적 오차를 줄이고 제어 시스템의 신뢰성을 향상시킨다.

고중량 산업용 AMR에서는 절대형 엔코더를 IMU, LiDAR, 비전 시스템(Vision System), GNSS 수신기와 함께 사용하는 경우가 많다. 센서 융합을 통해 매우 정확한 상태 추정(State Estimation)을 수행하고, 위치 제어기는 이를 기반으로 안정적이고 반복 가능한 동작을 수행한다.

산업용 로봇이 더욱 높은 정밀도와 자율성을 요구함에 따라 절대형 엔코더는 사실상 필수적인 구성 요소가 되었다. 전원 상태와 관계없이 지속적으로 정확한 위치 정보를 제공할 수 있다는 점에서, 절대형 엔코더는 현대 모바일 로봇 위치 제어 시스템의 핵심 센서라고 할 수 있다.

##  

## 04 Path Following

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Path following is one of the most important capabilities in an autonomous mobile robot because it directly determines how accurately the robot can move along a planned trajectory. While localization determines where the robot is and path planning determines where the robot should go, path following is responsible for continuously generating control commands that keep the robot on the desired path. In a differential drive robot, path following algorithms convert position and orientation errors into appropriate linear and angular velocity commands, allowing the robot to move smoothly toward its destination while minimizing deviations from the planned trajectory.

In industrial AMRs, path following performance directly affects operational efficiency, docking accuracy, traffic flow management, safety, and overall mission success. A robot that cannot accurately follow a path may experience increased travel times, excessive wheel wear, localization drift, and positioning errors. These problems become more significant in environments where robots share space with workers, machinery, and other autonomous vehicles.

The challenge of path following arises from the fact that real-world environments are rarely perfect. Floor conditions vary, wheel slip occurs, payload distributions change, and sensor measurements contain noise. Furthermore, differential drive robots are non-holonomic systems, meaning they cannot move directly sideways. Therefore, path following algorithms must account for the robot's kinematic constraints while continuously correcting errors.

A typical path-following system receives a trajectory from the navigation layer. This trajectory consists of a sequence of waypoints or a continuous path defined in the global coordinate frame. The controller continuously compares the robot's current position and orientation with the desired path and calculates steering corrections. The resulting velocity commands are then sent to lower-level motion and motor controllers.

An effective path-following controller must satisfy several requirements. It should provide stable convergence to the path, smooth steering behavior, low computational complexity, robustness against disturbances, and compatibility with real-time execution. The controller must also balance responsiveness and stability. Excessive correction can produce oscillatory motion, while insufficient correction can lead to large tracking errors.

Two of the most widely used path-following algorithms in mobile robotics are the Pure Pursuit Algorithm and the Stanley Controller. Both methods have been successfully deployed in industrial AMRs, autonomous vehicles, agricultural robots, and research platforms. Although they pursue the same objective, their operating principles differ significantly, resulting in different strengths and weaknesses.

The selection of a path-following algorithm depends on application requirements, operating speed, positioning accuracy targets, computational resources, and environmental conditions. Understanding the characteristics of these algorithms is essential for designing high-performance differential drive robots capable of reliable autonomous navigation.

---

### 4.1 Pure Pursuit Algorithm

The Pure Pursuit Algorithm is one of the oldest and most widely adopted path-following methods in mobile robotics. Its popularity stems from its simplicity, intuitive operation, computational efficiency, and reliable performance in a wide range of applications.

The basic concept of Pure Pursuit is inspired by how humans naturally steer vehicles. Instead of attempting to follow every point on a path precisely, the controller continuously selects a target point located a certain distance ahead of the robot. This distance is known as the lookahead distance. The robot then generates steering commands that guide it toward this target point.

The controller repeatedly performs three fundamental steps. First, it identifies the robot's current position. Second, it finds a lookahead point on the desired path. Third, it calculates the curvature required for the robot to reach that point. This curvature is then converted into angular velocity commands appropriate for a differential drive platform.

One of the most important parameters in the Pure Pursuit algorithm is the lookahead distance. A short lookahead distance causes the robot to respond aggressively to path deviations. This improves tracking accuracy but may introduce oscillations and unstable motion. A long lookahead distance produces smoother trajectories and greater stability but may increase tracking error, particularly around sharp corners.

Adaptive lookahead techniques are often employed in industrial AMRs. At low speeds, shorter lookahead distances improve positioning accuracy and docking performance. At higher speeds, larger lookahead distances improve stability and passenger comfort for transported payloads.

The geometric nature of Pure Pursuit makes it easy to implement. The controller requires only the robot's current position and a representation of the desired path. No complex dynamic models are necessary. This simplicity makes Pure Pursuit highly attractive for embedded systems with limited computational resources.

Another advantage is its robustness. Because the controller continuously updates the target point as the robot moves, small localization errors and environmental disturbances are naturally corrected over time. The algorithm also performs well in smooth path-following scenarios commonly encountered in warehouses, factories, and logistics facilities.

However, Pure Pursuit is not without limitations. The algorithm primarily focuses on geometric path tracking rather than minimizing cross-track error directly. Consequently, performance can degrade when navigating tight curves, sharp corners, or highly dynamic environments. Tracking errors may become noticeable if the lookahead distance is not properly tuned.

At very high speeds, Pure Pursuit may exhibit overshoot during aggressive turns because the controller continuously aims toward future points on the path rather than explicitly minimizing lateral deviation. This behavior can produce wider turning trajectories than desired.

Despite these limitations, Pure Pursuit remains one of the most commonly used path-following algorithms in industrial mobile robots. Its low computational requirements, intuitive tuning process, and reliable behavior make it particularly suitable for differential drive AMRs operating in structured indoor environments.

In many commercial systems, Pure Pursuit is integrated with additional motion planning layers, velocity constraints, obstacle avoidance systems, and localization modules. This combination enables practical and robust autonomous navigation while maintaining implementation simplicity.

For industrial robots performing logistics transport, automated material handling, and routine inspection tasks, Pure Pursuit often provides an excellent balance between performance and engineering complexity.

---

### 4.2 Stanley Controller

The Stanley Controller is another widely recognized path-following algorithm and became particularly famous through its successful application in autonomous vehicle competitions. Unlike Pure Pursuit, which focuses on pursuing a future target point, the Stanley Controller directly minimizes the robot's lateral deviation from the desired path.

The controller was originally developed for autonomous driving applications where maintaining accurate lane positioning at relatively high speeds was critical. Since then, it has been adapted for use in mobile robots, agricultural vehicles, mining equipment, and various industrial automation systems.

The Stanley Controller combines two primary error components. The first is heading error, which represents the difference between the robot's orientation and the desired path direction. The second is cross-track error, which measures the lateral distance between the robot and the path.

The controller calculates a steering correction that simultaneously reduces both errors. The heading error term aligns the robot's orientation with the path direction, while the cross-track error term pulls the robot back toward the path whenever lateral deviations occur.

One of the major strengths of the Stanley Controller is its ability to maintain precise path tracking. Because it explicitly considers cross-track error, the robot actively minimizes lateral deviations rather than simply pursuing future waypoints. This characteristic often results in tighter path adherence compared with Pure Pursuit.

The control law includes a gain parameter that determines how aggressively the controller responds to lateral deviations. Higher gains increase correction strength and improve convergence speed. However, excessively high gains may introduce oscillatory behavior, especially at low speeds. Proper gain tuning is therefore essential for achieving stable operation.

The Stanley Controller also incorporates vehicle speed into its calculations. At higher speeds, steering corrections become smoother to avoid excessive control actions. At lower speeds, stronger corrections can be applied because vehicle stability constraints are less severe. This adaptive behavior contributes to robust performance across a wide operating range.

In differential drive robots, the steering commands generated by the Stanley Controller are converted into angular velocity references. These references are then combined with linear velocity commands to produce left and right wheel speed targets.

Compared with Pure Pursuit, the Stanley Controller generally provides superior path accuracy, particularly in situations involving curved paths and significant lateral disturbances. It is often favored in applications requiring tight trajectory tracking and precise navigation.

However, the Stanley Controller can be more sensitive to localization noise because cross-track error calculations rely heavily on accurate position estimates. Poor localization performance may lead to unstable control actions or excessive steering corrections. For this reason, high-quality localization systems are often paired with Stanley-based navigation.

Another consideration is computational complexity. Although still relatively lightweight compared with advanced optimization-based controllers, Stanley requires more geometric calculations than Pure Pursuit. Modern industrial computers easily handle this workload, but it remains a factor in embedded implementations.

In practical industrial AMRs, the Stanley Controller is particularly attractive for applications requiring high positioning accuracy, narrow aisle navigation, precision docking approaches, and repeatable motion near production equipment. Its ability to maintain close adherence to planned trajectories often translates directly into improved operational efficiency and reduced positioning error.

Many advanced autonomous systems combine Stanley control with velocity planning, obstacle avoidance, localization fusion, and trajectory optimization. When properly integrated, the Stanley Controller provides highly accurate and robust path-following performance suitable for demanding industrial robotics applications.

As autonomous mobile robots continue evolving toward higher precision and greater autonomy, the Stanley Controller remains one of the most effective and widely adopted path-following solutions available for differential drive platforms.

경로 추종(Path Following)은 자율주행 모바일 로봇에서 가장 중요한 기능 중 하나이다. 위치 추정(Localization)이 현재 위치를 결정하고 경로 계획(Path Planning)이 목적지까지의 경로를 생성한다면, 경로 추종은 생성된 경로를 실제 로봇이 얼마나 정확하게 따라갈 수 있는지를 결정한다. 특히 차동 구동(Differential Drive) 로봇에서는 현재 위치와 목표 경로 사이의 오차를 지속적으로 계산하고, 이를 선속도(Linear Velocity)와 각속도(Angular Velocity) 명령으로 변환하여 로봇을 원하는 경로로 유도한다.

산업용 AMR에서 경로 추종 성능은 작업 효율성, 도킹 정확도, 공장 내 교통 흐름, 안전성, 그리고 전체 미션 성공률에 직접적인 영향을 미친다. 경로를 정확하게 따라가지 못하는 로봇은 이동 시간이 증가하고, 타이어 마모가 커지며, 위치 오차가 누적되고, 최종 정밀도도 저하된다. 이러한 문제는 사람, 설비, 다른 로봇과 함께 작업하는 산업 환경에서 더욱 중요해진다.

경로 추종이 어려운 이유는 실제 환경이 이상적이지 않기 때문이다. 바닥 상태가 일정하지 않고, 바퀴 슬립(Wheel Slip)이 발생하며, 적재 하중이 변화하고, 센서 데이터에는 항상 노이즈(Noise)가 포함된다. 또한 차동 구동 로봇은 비홀로노믹 시스템(Non-Holonomic System)이므로 옆 방향으로 직접 이동할 수 없다. 따라서 경로 추종 알고리즘은 이러한 운동학적 제약(Kinematic Constraint)을 고려하면서도 경로 오차를 지속적으로 보정해야 한다.

일반적인 경로 추종 시스템은 내비게이션 계층으로부터 경로 정보를 전달받는다. 경로는 웨이포인트(Waypoint) 집합 또는 연속적인 곡선 형태로 표현된다. 제어기는 현재 위치와 목표 경로를 비교하여 조향 보정(Steering Correction)을 계산하고, 이를 하위 속도 제어기와 모터 제어기에 전달한다.

우수한 경로 추종 알고리즘은 안정적인 경로 수렴(Stability), 부드러운 조향 특성(Smooth Steering), 낮은 계산 복잡도(Low Computational Complexity), 외란에 대한 강인성(Robustness), 그리고 실시간 처리 능력을 제공해야 한다. 또한 지나치게 공격적인 제어는 진동을 유발하고, 너무 보수적인 제어는 큰 추종 오차를 발생시키므로 적절한 균형이 필요하다.

현재 모바일 로봇 분야에서 가장 널리 사용되는 경로 추종 알고리즘은 퓨어 퍼슈트 알고리즘(Pure Pursuit Algorithm)과 스탠리 제어기(Stanley Controller)이다. 두 방법 모두 동일한 목표를 추구하지만 동작 원리가 다르기 때문에 각각 장점과 단점을 가진다.

어떤 알고리즘을 선택할지는 주행 속도, 요구 정밀도, 계산 자원, 운용 환경 등에 따라 달라진다. 따라서 각 알고리즘의 특성을 이해하는 것은 고성능 차동 구동 로봇을 설계하는 데 매우 중요하다.

---

### 4.1 퓨어 퍼슈트 알고리즘(Pure Pursuit Algorithm)

퓨어 퍼슈트 알고리즘(Pure Pursuit Algorithm)은 모바일 로봇 분야에서 가장 오래되고 널리 사용되는 경로 추종 알고리즘 중 하나이다. 구조가 단순하고 직관적이며 계산량이 적기 때문에 산업용 AMR에서 매우 많이 활용된다.

퓨어 퍼슈트의 기본 개념은 사람이 자동차를 운전하는 방식과 유사하다. 차량은 현재 위치만 바라보지 않고 일정 거리 앞을 바라보며 조향한다. 퓨어 퍼슈트 역시 현재 위치에서 일정 거리 앞에 있는 목표점을 선택하고, 그 점을 향해 이동하도록 조향 명령을 생성한다.

이때 사용되는 핵심 파라미터가 전방 주시 거리(Lookahead Distance)이다. 알고리즘은 현재 위치를 기준으로 경로 상에서 Lookahead Distance 만큼 떨어진 목표점을 찾는다. 이후 로봇이 해당 지점으로 이동할 수 있도록 필요한 곡률(Curvature)을 계산한다.

퓨어 퍼슈트는 반복적으로 세 가지 과정을 수행한다. 먼저 현재 로봇 위치를 계산한다. 다음으로 목표 경로에서 전방 주시 지점을 선택한다. 마지막으로 해당 지점에 도달하기 위한 곡률을 계산하여 각속도 명령을 생성한다.

Lookahead Distance는 알고리즘 성능을 결정하는 가장 중요한 요소이다. 전방 주시 거리가 짧으면 경로 오차에 매우 민감하게 반응한다. 따라서 추종 정확도는 향상되지만 진동이 증가할 수 있다. 반대로 전방 주시 거리가 길면 경로는 더욱 부드러워지지만 급격한 곡선에서는 오차가 증가할 수 있다.

이를 해결하기 위해 산업용 AMR에서는 적응형 전방 주시 거리(Adaptive Lookahead Distance)를 사용하는 경우가 많다. 저속에서는 짧은 Lookahead Distance를 사용하여 정밀도를 높이고, 고속에서는 긴 Lookahead Distance를 사용하여 안정성을 향상시킨다.

퓨어 퍼슈트의 가장 큰 장점은 구현이 매우 쉽다는 점이다. 복잡한 차량 동역학 모델(Vehicle Dynamics Model)이 필요하지 않으며 현재 위치와 목표 경로만 있으면 동작할 수 있다. 따라서 임베디드 시스템(Embedded System)에서도 쉽게 구현 가능하다.

또한 외란에 대한 강인성이 높다. 경로를 따라 이동하면서 목표점을 지속적으로 업데이트하기 때문에 작은 위치 오차나 외부 환경 변화는 자연스럽게 보정된다. 창고, 공장, 물류센터와 같은 구조화된 환경에서는 매우 안정적인 성능을 제공한다.

하지만 퓨어 퍼슈트에도 한계가 있다. 경로와의 횡방향 오차(Cross-Track Error)를 직접 최소화하는 것이 아니라 목표점을 추종하는 방식이기 때문에 급격한 곡선이나 복잡한 경로에서는 성능이 저하될 수 있다.

특히 고속 주행에서는 곡선 구간에서 오버슈트(Overshoot)가 발생할 수 있으며, 경로를 넓게 돌아가는 현상이 나타날 수 있다.

그럼에도 불구하고 퓨어 퍼슈트는 계산량이 적고 튜닝이 쉽고 안정성이 높기 때문에 현재도 산업용 차동 구동 AMR에서 가장 널리 사용되는 경로 추종 알고리즘 중 하나이다.

물류 운송, 자재 이송, 공장 순회 검사와 같은 일반적인 산업 응용에서는 성능과 개발 난이도 사이에서 매우 우수한 균형을 제공한다.

---

### 4.2 스탠리 제어기(Stanley Controller)

스탠리 제어기(Stanley Controller)는 자율주행 차량 분야에서 널리 알려진 경로 추종 알고리즘이다. 특히 DARPA Grand Challenge에서 성공적으로 사용되면서 유명해졌으며, 이후 모바일 로봇, 농업용 차량, 광산 장비, 산업용 AMR 등 다양한 분야에 적용되고 있다.

스탠리 제어기의 가장 큰 특징은 미래 목표점을 추종하는 것이 아니라 경로와의 횡방향 오차(Cross-Track Error)를 직접 최소화한다는 점이다.

스탠리 제어기는 두 가지 주요 오차를 사용한다. 첫 번째는 헤딩 오차(Heading Error)이다. 이는 로봇의 현재 방향과 경로의 진행 방향 사이의 차이를 의미한다. 두 번째는 횡방향 오차(Cross-Track Error)이다. 이는 로봇과 경로 사이의 수직 거리를 의미한다.

제어기는 이 두 오차를 동시에 줄일 수 있는 조향 명령을 계산한다. 헤딩 오차는 로봇 방향을 경로 방향에 맞추고, 횡방향 오차는 로봇을 경로 중심으로 끌어당기는 역할을 수행한다.

스탠리 제어기의 가장 큰 장점은 높은 경로 추종 정확도이다. 횡방향 오차를 직접 제어하기 때문에 퓨어 퍼슈트보다 경로 중심선을 더욱 정확하게 유지할 수 있다.

특히 곡선 구간이나 외란이 존재하는 환경에서도 높은 정확도를 유지할 수 있으며, 좁은 통로(Narrow Aisle) 주행이나 정밀 도킹 접근 단계에서 매우 우수한 성능을 보여준다.

스탠리 제어기에는 제어 게인(Control Gain)이 존재하며, 이 값은 횡방향 오차에 얼마나 강하게 반응할지를 결정한다. 게인이 높으면 빠르게 경로로 복귀하지만 진동이 발생할 수 있다. 게인이 너무 낮으면 응답이 느려져 추종 오차가 증가한다.

또한 스탠리 제어기는 차량 속도를 고려한다. 고속에서는 보다 부드러운 조향을 수행하여 안정성을 유지하고, 저속에서는 강한 보정 동작을 수행하여 정확도를 향상시킨다.

차동 구동 로봇에서는 스탠리 제어기가 생성한 조향 명령을 각속도 명령으로 변환하고, 이를 선속도와 결합하여 좌우 바퀴 속도 목표값을 계산한다.

퓨어 퍼슈트와 비교하면 스탠리 제어기는 일반적으로 더 높은 경로 정확도를 제공한다. 특히 곡선 경로나 측면 외란이 존재하는 상황에서는 더욱 우수한 성능을 보인다.

그러나 위치 추정 정확도에 대한 의존성이 높다는 단점도 있다. 횡방향 오차 계산이 정확한 위치 정보를 필요로 하기 때문에 위치 추정 오차가 크면 불안정한 조향 명령이 생성될 수 있다.

따라서 스탠리 제어기는 일반적으로 고성능 위치 추정(Localization) 시스템과 함께 사용된다. LiDAR 기반 SLAM, 비전 기반 위치 추정, RTK-GNSS 등의 정밀 위치 시스템과 결합하면 매우 우수한 성능을 얻을 수 있다.

계산 복잡도 측면에서는 퓨어 퍼슈트보다 약간 복잡하지만, 현대 산업용 컴퓨터에서는 부담이 거의 없다.

산업용 AMR에서는 좁은 통로 주행, 정밀 도킹, 생산 설비 주변 작업, 반복 정밀도가 중요한 응용 분야에서 스탠리 제어기가 자주 사용된다. 경로 중심선을 정확하게 유지할 수 있기 때문에 작업 효율성과 위치 정확도를 동시에 향상시킬 수 있다.

최근의 고성능 자율주행 시스템은 스탠리 제어기를 속도 계획(Velocity Planning), 장애물 회피(Obstacle Avoidance), 센서 융합(Sensor Fusion), 궤적 최적화(Trajectory Optimization)와 결합하여 사용한다. 이러한 통합 시스템은 높은 정밀도와 강인성을 제공하며, 차세대 산업용 AMR의 핵심 경로 추종 기술로 활용되고 있다.

##  

## 05 Odometry Compensation

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Odometry compensation is a critical component of mobile robot navigation because it directly addresses one of the fundamental limitations of encoder-based localization. While wheel encoders provide a simple and cost-effective method for estimating robot position, odometry calculations inevitably accumulate errors over time. Even small inaccuracies in wheel speed measurements, wheel diameter assumptions, encoder resolution, or vehicle geometry can gradually grow into significant positioning errors after long travel distances. As a result, a robot that initially appears to be accurately localized may eventually deviate substantially from its true position if no compensation mechanisms are applied.

In a differential drive robot, odometry is typically calculated by integrating the rotational motion of the left and right wheels. By estimating the distance traveled by each wheel and applying the vehicle\'s kinematic model, the robot computes its current position and orientation. This process works well over short distances and controlled environments. However, real-world operating conditions introduce many sources of error that reduce odometry accuracy.

Wheel slip is one of the most significant contributors to odometry drift. During acceleration, braking, turning, or operation on low-friction surfaces, the actual motion of the robot may differ from the motion inferred from wheel rotation measurements. The encoder may report wheel movement even when the vehicle is partially slipping, causing incorrect position updates. Similarly, uneven floor surfaces, debris, expansion joints, and ramps can alter wheel-ground interaction characteristics.

Mechanical imperfections also contribute to odometry errors. Small differences in wheel diameter, tire wear, manufacturing tolerances, gearbox backlash, bearing friction, and chassis deformation can create systematic biases. Although each individual error source may be small, their cumulative effect becomes increasingly significant as travel distance increases.

Environmental factors introduce additional challenges. Temperature variations can influence tire characteristics and mechanical dimensions. Payload changes alter vehicle dynamics and wheel loading conditions. Heavy industrial AMRs carrying several hundred kilograms may exhibit different odometry characteristics under loaded and unloaded conditions.

Because odometry errors accumulate continuously, compensation techniques are essential for maintaining acceptable localization accuracy. Modern mobile robots employ a combination of calibration procedures, bias correction methods, sensor fusion algorithms, and external reference measurements to mitigate drift. Rather than relying exclusively on wheel encoders, advanced systems integrate IMUs, LiDAR-based localization, vision systems, GNSS receivers, fiducial markers, and map-based correction methods.

Odometry compensation does not eliminate errors entirely. Instead, it reduces error growth rates and periodically corrects accumulated drift. The goal is to maintain sufficiently accurate position estimates for navigation, obstacle avoidance, docking, and mission execution.

In industrial applications, effective odometry compensation improves path-following performance, docking repeatability, fleet coordination, safety margins, and operational efficiency. Without compensation, even highly accurate motion controllers may eventually fail to achieve required positioning precision due to localization drift. Consequently, odometry compensation has become an indispensable component of modern AMR control architectures.

---

### 5.1 Encoder Bias Correction

Encoder bias correction is one of the most fundamental odometry compensation techniques used in differential drive mobile robots. The objective is to identify and eliminate systematic errors that originate from wheel encoders, drivetrain components, and vehicle geometry. Unlike random errors, systematic errors produce predictable deviations that can be measured, modeled, and corrected.

One common source of systematic error is wheel diameter mismatch. Even if two wheels are manufactured to nominally identical specifications, small dimensional differences inevitably exist. As the robot travels, these differences cause one wheel to cover slightly more distance than the other for the same number of encoder counts. Over time, this discrepancy produces heading errors and trajectory deviations.

Tire wear further exacerbates the problem. Wheels gradually lose material during operation, altering effective rolling diameters. Because wear rates may differ between wheels, odometry performance can degrade progressively unless periodic recalibration is performed.

Wheelbase estimation errors represent another important source of bias. The kinematic model of a differential drive robot assumes a specific distance between the left and right wheels. If the actual wheelbase differs from the assumed value, rotational motion calculations become inaccurate. Even small wheelbase errors can generate substantial orientation drift during repeated turning maneuvers.

Encoder resolution limitations also contribute to measurement inaccuracies. Low-resolution encoders introduce quantization effects that reduce measurement precision, particularly at low speeds. Although higher-resolution encoders improve accuracy, residual errors may still exist due to signal processing delays, electrical noise, and mechanical imperfections.

Encoder bias correction typically begins with calibration experiments. The robot is commanded to execute predefined trajectories such as straight-line motion, circular motion, square paths, or figure-eight patterns. The resulting odometry estimates are compared with ground-truth measurements obtained from external localization systems. Differences between expected and observed behavior are then analyzed to identify systematic biases.

Calibration coefficients can be introduced to compensate for wheel diameter variations. Separate scaling factors may be applied to the left and right wheel encoder measurements, ensuring that measured distances more accurately reflect actual vehicle motion. Similarly, wheelbase correction factors can be applied to improve rotational accuracy.

Advanced industrial systems often perform periodic recalibration during maintenance intervals. Because tire wear, payload changes, and mechanical aging gradually alter system characteristics, calibration parameters must be updated over time. Some robots even perform self-calibration procedures by comparing odometry data with external localization references during normal operation.

Bias correction significantly improves odometry performance because systematic errors are often responsible for the majority of long-term drift. By removing predictable inaccuracies at their source, subsequent sensor fusion algorithms can operate more effectively and require less aggressive correction.

For industrial AMRs operating in warehouses, factories, and logistics centers, encoder bias correction represents a cost-effective method for improving localization accuracy without requiring additional hardware. Although it cannot eliminate all odometry errors, it forms an essential foundation for reliable navigation performance.

---

### 5.2 IMU Assisted Correction

While encoder bias correction addresses systematic wheel-related errors, many odometry inaccuracies originate from dynamic effects that cannot be fully compensated through calibration alone. Wheel slip, rapid acceleration, uneven terrain, collisions, and transient disturbances introduce errors that vary continuously during operation. To address these challenges, modern mobile robots frequently employ IMU-assisted odometry correction.

An Inertial Measurement Unit (IMU) typically contains gyroscopes, accelerometers, and sometimes magnetometers. These sensors provide measurements of angular velocity, linear acceleration, and orientation-related information. Unlike wheel encoders, IMUs directly measure vehicle motion rather than inferring motion from wheel rotation. This complementary characteristic makes IMUs highly valuable for odometry compensation.

The gyroscope is particularly important in differential drive robots because it provides direct measurements of rotational velocity. During turning maneuvers, the gyroscope can accurately estimate heading changes even when wheel slip occurs. If encoder-based odometry reports a rotation that differs from the gyroscope measurement, the discrepancy may indicate slippage or other motion estimation errors.

Accelerometers provide additional information regarding vehicle dynamics. Although acceleration measurements are generally noisier than encoder data and difficult to integrate directly into long-term position estimates, they can help identify transient events such as impacts, sudden braking, or abnormal motion behavior.

IMU-assisted correction is typically implemented through sensor fusion algorithms. Instead of relying solely on encoder measurements, the localization system combines information from both encoders and the IMU to produce a more reliable state estimate. Common fusion approaches include Complementary Filters, Extended Kalman Filters (EKF), Unscented Kalman Filters (UKF), and factor graph optimization methods.

The Extended Kalman Filter is particularly popular in industrial AMRs. The filter predicts robot motion using encoder-based odometry and then corrects this prediction using IMU measurements. Because each sensor possesses different strengths and weaknesses, the fusion process generates estimates that are more accurate than either sensor could provide individually.

One major advantage of IMU-assisted correction is improved robustness during wheel slip events. For example, if the robot accelerates rapidly on a smooth floor, wheel encoders may overestimate vehicle motion. The IMU can detect inconsistencies between expected and measured rotational behavior, allowing the filter to reduce reliance on encoder data during the slip event.

IMU correction also improves short-term orientation accuracy. Since heading errors directly influence position estimates, even small improvements in orientation estimation can significantly reduce long-term localization drift. This benefit becomes especially important in large industrial facilities where robots travel long distances between localization updates.

Industrial environments often contain challenging operating conditions such as ramps, uneven surfaces, transitions between floor materials, and varying payload configurations. IMU-assisted correction provides valuable resilience against these disturbances by continuously monitoring actual vehicle dynamics.

Modern industrial AMRs frequently integrate IMU-assisted odometry with higher-level localization systems such as LiDAR SLAM, visual localization, GNSS, or fiducial marker tracking. In these architectures, encoder and IMU fusion provide accurate short-term motion estimation, while external localization systems periodically eliminate accumulated drift.

As autonomous mobile robots continue advancing toward higher accuracy and greater autonomy, IMU-assisted correction has become a standard component of professional navigation systems. Its ability to complement encoder measurements, detect dynamic errors, and improve localization robustness makes it one of the most effective odometry compensation techniques available for differential drive robots.

오도메트리 보정(Odometry Compensation)은 모바일 로봇 내비게이션에서 매우 중요한 기능이다. 이는 엔코더 기반 위치 추정(Encoder-Based Localization)이 가지는 근본적인 한계를 보완하기 위해 사용된다. 휠 엔코더(Wheel Encoder)는 로봇 위치를 추정하는 가장 간단하고 경제적인 방법이지만, 오도메트리 계산은 시간이 지남에 따라 오차가 지속적으로 누적되는 특징을 가진다. 바퀴 직경, 엔코더 분해능(Resolution), 차량 기하학적 구조, 속도 측정 오차와 같은 작은 오차들이 장거리 주행 후에는 상당한 위치 오차로 확대될 수 있다.

차동 구동(Differential Drive) 로봇에서는 좌측 및 우측 바퀴의 회전량을 기반으로 이동 거리와 방향 변화를 계산한다. 이를 통해 현재 위치와 자세(Pose)를 추정하지만, 실제 환경에서는 다양한 오차 요인이 존재하기 때문에 계산된 위치와 실제 위치 사이에 차이가 발생한다.

바퀴 슬립(Wheel Slip)은 오도메트리 오차의 가장 큰 원인 중 하나이다. 가속, 감속, 회전, 저마찰 바닥에서의 주행 시 바퀴 회전량과 실제 이동 거리가 일치하지 않을 수 있다. 엔코더는 바퀴가 회전했다고 보고하지만 실제 차량은 미끄러지고 있을 수 있기 때문에 잘못된 위치 정보가 생성된다.

기계적인 요인도 중요한 영향을 미친다. 바퀴 직경 차이, 타이어 마모(Tire Wear), 제조 공차(Manufacturing Tolerance), 감속기 백래시(Gearbox Backlash), 베어링 마찰(Bearing Friction), 프레임 변형(Frame Deformation) 등은 모두 시스템적인 오차(Systematic Error)를 유발한다.

환경 조건 역시 오도메트리 성능에 영향을 준다. 온도 변화는 타이어 특성과 기계 구조에 영향을 미치며, 적재 하중 변화는 차량 동특성과 바퀴 접지력을 변화시킨다. 특히 수백 kg 이상의 고중량 산업용 AMR은 적재 여부에 따라 완전히 다른 오도메트리 특성을 보일 수 있다.

이러한 오차는 시간이 지남에 따라 계속 누적되기 때문에 보정 기술이 반드시 필요하다. 현대 AMR은 단순히 엔코더에 의존하지 않고, IMU(Inertial Measurement Unit), LiDAR 기반 위치 추정, 비전 시스템(Vision System), GNSS 수신기, 마커(Marker), 지도 기반 보정(Map-Based Correction) 등을 함께 사용하여 오차를 줄인다.

오도메트리 보정의 목적은 모든 오차를 제거하는 것이 아니다. 현실적으로 이는 불가능하다. 대신 오차 증가 속도를 최소화하고, 누적된 오차를 주기적으로 수정하여 내비게이션 성능을 유지하는 것이 목표이다.

산업 현장에서 효과적인 오도메트리 보정은 경로 추종(Path Following) 성능 향상, 도킹 반복 정밀도 향상, 플릿 협업(Fleet Coordination) 안정성 향상, 안전성 증대, 생산성 향상으로 이어진다. 따라서 오도메트리 보정은 현대 산업용 AMR 아키텍처에서 필수적인 기술 요소로 간주된다.

---

### 5.1 엔코더 바이어스 보정(Encoder Bias Correction)

엔코더 바이어스 보정(Encoder Bias Correction)은 차동 구동 모바일 로봇에서 가장 기본적이고 중요한 오도메트리 보정 기법 중 하나이다. 이 방법의 목적은 휠 엔코더, 구동계(Drivetrain), 차량 기하학적 구조에서 발생하는 시스템적인 오차(Systematic Error)를 찾아 제거하는 것이다.

랜덤 오차(Random Error)는 예측하기 어렵지만, 시스템 오차는 반복적으로 동일한 방향으로 발생하기 때문에 측정과 모델링을 통해 보정할 수 있다.

가장 흔한 원인은 바퀴 직경 불일치(Wheel Diameter Mismatch)이다. 동일한 규격의 바퀴라 하더라도 실제 제조 과정에서는 미세한 차이가 존재한다. 이로 인해 동일한 엔코더 카운트(Encoder Count)가 발생하더라도 실제 이동 거리는 좌우 바퀴에서 다르게 나타날 수 있다. 결과적으로 로봇은 직진해야 할 상황에서도 조금씩 한쪽으로 방향이 틀어지게 된다.

타이어 마모(Tire Wear)는 이러한 문제를 더욱 심화시킨다. 시간이 지남에 따라 타이어는 점차 마모되며 유효 직경(Effective Diameter)이 감소한다. 좌우 바퀴의 마모 정도가 다르면 오도메트리 오차는 더욱 커진다.

또 다른 주요 원인은 휠베이스 오차(Wheelbase Estimation Error)이다. 차동 구동 모델은 좌우 바퀴 중심 간 거리를 알고 있다고 가정한다. 그러나 실제 휠베이스가 설계값과 다르면 회전 운동 계산이 부정확해진다. 특히 반복적인 회전 동작에서는 작은 오차도 큰 방향 오차로 누적된다.

엔코더 분해능(Encoder Resolution)의 한계도 영향을 미친다. 저분해능 엔코더는 특히 저속 영역에서 양자화 오차(Quantization Error)를 발생시킨다. 고분해능 엔코더를 사용하면 개선되지만 전기적 노이즈와 신호 처리 지연 등으로 인해 여전히 일부 오차가 존재한다.

엔코더 바이어스 보정은 일반적으로 캘리브레이션(Calibration) 과정에서 시작된다. 로봇은 직선 주행, 원형 주행, 사각형 경로, 8자 경로(Figure-Eight Path)와 같은 표준 경로를 따라 이동한다. 이후 외부 위치 측정 시스템이 제공하는 실제 위치와 오도메트리 결과를 비교하여 오차를 분석한다.

분석 결과를 바탕으로 보정 계수(Calibration Coefficient)가 계산된다. 예를 들어 좌우 바퀴에 서로 다른 스케일 팩터(Scale Factor)를 적용하여 실제 이동 거리와 계산된 이동 거리를 일치시킬 수 있다. 또한 휠베이스 보정 계수를 적용하여 회전 계산 정확도를 향상시킬 수 있다.

산업용 AMR에서는 정기 유지보수 과정에서 재보정(Recalibration)을 수행하는 경우가 많다. 타이어 마모, 기계 노후화, 적재 조건 변화가 지속적으로 발생하기 때문이다.

일부 고급 시스템은 자가 보정(Self-Calibration) 기능도 제공한다. LiDAR SLAM 또는 비전 위치 추정 결과와 오도메트리를 비교하여 주행 중 자동으로 보정 계수를 업데이트한다.

엔코더 바이어스 보정은 비교적 저비용으로 구현할 수 있으면서도 장기적인 오도메트리 성능을 크게 향상시킨다. 비록 모든 오차를 제거할 수는 없지만, 정확한 내비게이션을 위한 필수 기반 기술이라고 할 수 있다.

---

### 5.2 IMU 기반 보정(IMU Assisted Correction)

엔코더 바이어스 보정이 시스템 오차를 제거하는 역할을 한다면, IMU 기반 보정(IMU Assisted Correction)은 주행 중 발생하는 동적 오차(Dynamic Error)를 보완하는 역할을 수행한다.

실제 주행 환경에서는 바퀴 슬립, 급가속, 급감속, 울퉁불퉁한 바닥, 충돌, 진동 등 다양한 외란이 발생한다. 이러한 현상은 사전에 완벽히 예측할 수 없기 때문에 단순한 캘리브레이션만으로는 해결할 수 없다.

IMU(Inertial Measurement Unit)는 일반적으로 자이로스코프(Gyroscope), 가속도계(Accelerometer), 그리고 경우에 따라 자기계(Magnetometer)를 포함한다. IMU는 바퀴 회전량을 기반으로 움직임을 추정하는 엔코더와 달리 실제 차량의 운동 상태를 직접 측정한다.

특히 자이로스코프는 차동 구동 로봇에서 매우 중요한 역할을 수행한다. 자이로는 차량의 각속도(Angular Velocity)를 직접 측정할 수 있기 때문에 회전 동작 시 매우 유용하다.

예를 들어 로봇이 회전할 때 엔코더 기반 오도메트리는 특정 각도만큼 회전했다고 계산할 수 있다. 그러나 자이로가 측정한 실제 회전량이 다르다면 이는 슬립 또는 기타 오차가 발생했음을 의미한다.

가속도계는 차량의 선형 가속도(Linear Acceleration)를 측정한다. 장기적인 위치 계산에는 노이즈가 많아 직접 사용하기 어렵지만, 충돌, 급제동, 급가속, 비정상 동작 감지에는 매우 유용하다.

IMU 기반 보정은 일반적으로 센서 융합(Sensor Fusion)을 통해 구현된다. 엔코더와 IMU를 독립적으로 사용하는 것이 아니라 두 센서의 정보를 결합하여 보다 정확한 위치 추정 결과를 생성한다.

대표적인 센서 융합 기법으로는 상보 필터(Complementary Filter), 확장 칼만 필터(Extended Kalman Filter, EKF), 무향 칼만 필터(Unscented Kalman Filter, UKF), 팩터 그래프 최적화(Factor Graph Optimization) 등이 있다.

산업용 AMR에서는 EKF가 가장 널리 사용된다. EKF는 엔코더 기반 오도메트리를 이용하여 위치를 예측(Prediction)하고, IMU 측정값을 이용하여 이를 수정(Correction)한다. 결과적으로 두 센서의 장점을 결합한 보다 정확한 위치 추정이 가능해진다.

IMU 보정의 가장 큰 장점은 슬립 상황에서 강력한 성능을 발휘한다는 점이다. 예를 들어 매끄러운 바닥에서 급가속이 발생하면 엔코더는 실제보다 더 많은 이동 거리를 계산할 수 있다. 그러나 IMU는 실제 차량의 움직임을 측정하므로 이러한 오류를 감지하고 보정할 수 있다.

또한 IMU는 방향 추정(Heading Estimation)의 정확도를 크게 향상시킨다. 방향 오차는 위치 오차로 직접 연결되기 때문에 작은 방향 오차 감소만으로도 전체 위치 정확도를 크게 개선할 수 있다.

대규모 공장이나 물류센터처럼 장거리 이동이 많은 환경에서는 이러한 효과가 더욱 중요해진다.

현대 산업용 AMR은 IMU 기반 오도메트리를 LiDAR SLAM, 비전 위치 추정, GNSS, AprilTag, QR 마커 기반 위치 추정 등과 함께 사용한다. 이 경우 엔코더와 IMU는 단기적인 위치 추정을 담당하고, 외부 위치 시스템은 장기 누적 오차를 제거하는 역할을 수행한다.

자율주행 기술이 발전함에 따라 IMU 기반 보정은 사실상 산업용 AMR의 표준 기능이 되었다. 엔코더의 한계를 보완하고, 슬립과 외란에 강인한 위치 추정을 제공하며, 전체 내비게이션 성능을 향상시키는 가장 효과적인 오도메트리 보정 기술 중 하나로 평가받고 있다.
