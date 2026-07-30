## 01 KUKA KMR iiwa

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

The KUKA KMR iiwa represents one of the earliest commercially successful examples of a fully integrated mobile manipulator that combines omnidirectional mobility with collaborative robotic manipulation. Rather than treating the mobile base and robotic arm as two independent machines, the KMR iiwa was designed as a unified robotic system in which locomotion, manipulation, perception, safety, and control are tightly integrated. This architecture allows the robot to autonomously transport itself to different workstations, precisely position its mobile platform, and immediately perform manipulation tasks without human intervention. As manufacturing systems continue to evolve toward highly flexible production and mass customization, this concept has become an important reference architecture for next-generation industrial mobile manipulators.

Unlike traditional industrial robots that remain permanently fixed to the floor, mobile manipulators extend the robot workspace from a static volume into an entire factory. The KMR iiwa combines a Mecanum-wheel omnidirectional platform with the lightweight collaborative LBR iiwa robotic arm. The omnidirectional base provides three independent planar degrees of freedom consisting of longitudinal velocity, lateral velocity, and rotational velocity, while the manipulator contributes seven additional articulated joints. Together they form a highly redundant robotic system capable of positioning tools from numerous orientations while simultaneously optimizing robot posture, collision avoidance, energy consumption, and workspace accessibility.

The integration between mobility and manipulation fundamentally changes production system design. Conventional manufacturing lines require workpieces to be transported between fixed robotic cells by conveyors or automated guided vehicles. In contrast, the KMR iiwa brings the robot directly to the workpiece, significantly reducing infrastructure complexity and increasing manufacturing flexibility. Production equipment can therefore be rearranged with minimal modification whenever product variants or manufacturing processes change. This flexibility is particularly valuable in low-volume, high-mix manufacturing environments where frequent production reconfiguration is economically advantageous.

Accurate localization forms the foundation of mobile manipulation. The mobile base continuously estimates its position using multiple sensing modalities including wheel encoders, laser scanners, inertial sensors, and environmental landmarks. Sensor fusion algorithms combine these measurements to estimate vehicle pose with high confidence while simultaneously compensating for wheel slip, floor irregularities, and accumulated odometric drift. Once the robot approaches its target workstation, fine positioning algorithms further reduce residual localization error before manipulation begins. This hierarchical localization strategy allows the mobile manipulator to achieve repeatable positioning performance that satisfies industrial assembly and inspection requirements.

Safety represents another defining characteristic of the KMR iiwa architecture. The lightweight LBR iiwa manipulator incorporates joint torque sensors that detect unexpected contact with people or obstacles. Simultaneously, the mobile platform continuously monitors its surrounding environment using laser safety scanners capable of detecting nearby personnel and obstacles. Motion speed, acceleration, and allowable operating zones are automatically adjusted according to human proximity. These integrated safety functions enable safe human-robot collaboration without requiring conventional physical safety fencing, thereby increasing production flexibility and workspace utilization.

Control architecture for the KMR iiwa differs substantially from conventional fixed-base robots. Mobile base control, manipulator control, navigation, perception, safety supervision, and task execution operate simultaneously under coordinated software supervision. Modern implementations increasingly employ model predictive control, optimization-based motion planning, digital twins, and artificial intelligence to coordinate whole-body motion. Rather than optimizing only manipulator trajectories, the complete robot---including both wheels and arm---is treated as a unified kinematic system whose redundancy can be exploited to improve precision, avoid obstacles, reduce energy consumption, and maximize productivity.

The KMR iiwa has significantly influenced the development of autonomous industrial robotics. Many modern mobile manipulators produced by various manufacturers now adopt similar architectural principles involving omnidirectional mobility, collaborative manipulation, autonomous navigation, sensor fusion, and integrated safety. As artificial intelligence, cloud robotics, digital twins, and high-performance perception systems continue to mature, future mobile manipulators are expected to become increasingly autonomous, adaptive, and capable of performing sophisticated manufacturing operations with minimal human supervision.

---

### 1.1 Mecanum Based Mobile Manipulator Architecture

---

### 1.2 Precision Positioning Performance in Production Line

---

KUKA KMR iiwa는 전방향 이동성(Omnidirectional Mobility)과 협동 로봇 매니퓰레이션(Collaborative Robotic Manipulation)을 하나의 시스템으로 완전히 통합한 최초의 상용 이동형 매니퓰레이터(Mobile Manipulator) 가운데 가장 대표적인 사례이다. 이 시스템은 이동 플랫폼(Mobile Base)과 로봇 암(Robotic Arm)을 서로 독립된 장비로 취급하지 않고, 이동(Locomotion), 조작(Manipulation), 인식(Perception), 안전(Safety), 제어(Control)를 하나의 통합된 로봇 시스템으로 설계하였다. 이러한 구조를 통해 로봇은 공장 내 여러 작업 지점으로 자율적으로 이동한 후, 이동 플랫폼을 정밀하게 위치시키고 즉시 작업을 수행할 수 있다. 제조 산업이 대량 맞춤 생산(Mass Customization)과 유연 생산(Flexible Manufacturing)으로 발전하면서 이러한 개념은 차세대 산업용 이동형 매니퓰레이터의 대표적인 아키텍처로 자리 잡고 있다.

기존 산업용 로봇은 바닥에 고정되어 제한된 작업 공간에서만 작업을 수행하였다. 반면 KUKA KMR iiwa는 메카넘 휠(Mecanum Wheel) 기반의 전방향 이동 플랫폼과 LBR iiwa 협동 로봇(Collaborative Robot)을 결합하여, 작업 공간을 공장 전체로 확장하였다. 이동 플랫폼은 종방향 속도(Longitudinal Velocity), 횡방향 속도(Lateral Velocity), 회전 속도(Rotational Velocity)의 3자유도(3 Degrees of Freedom)를 제공하며, 로봇 암은 7개의 관절 자유도(7 Degrees of Freedom)를 가진다. 따라서 전체 시스템은 총 10자유도의 고중복성(Redundant) 로봇 시스템을 구성하며, 공구(Tool)의 자세를 다양하게 변경하면서도 충돌 회피(Collision Avoidance), 에너지 절감(Energy Efficiency), 작업 공간 활용성(Workspace Accessibility)을 동시에 최적화할 수 있다.

이동성과 조작 기능의 통합은 생산 시스템 설계 방식 자체를 변화시켰다. 기존 생산 라인은 컨베이어(Conveyor)나 자동운반차(AGV)를 이용하여 작업물을 고정된 로봇 셀(Robot Cell) 사이로 이동시켰다. 그러나 KMR iiwa는 작업물 대신 로봇이 직접 작업 위치로 이동한다. 따라서 생산 설비를 더욱 유연하게 재배치할 수 있으며, 제품 변경(Product Variant)이나 공정 변경(Process Change)이 발생하더라도 설비 변경 비용을 크게 줄일 수 있다. 특히 다품종 소량 생산(High-Mix Low-Volume Manufacturing)에서는 이러한 유연성이 매우 큰 경제적 장점을 제공한다.

정확한 위치 추정(Localization)은 이동형 매니퓰레이터의 핵심 기술이다. 이동 플랫폼은 엔코더(Encoder), 레이저 스캐너(Laser Scanner), IMU(Inertial Measurement Unit), 환경 기준점(Environmental Landmark) 등을 이용하여 자신의 위치를 지속적으로 추정한다. 센서 융합(Sensor Fusion)은 휠 슬립(Wheel Slip), 바닥 요철(Floor Irregularity), 누적 오도메트리 오차(Odometry Drift)를 보정하면서 높은 신뢰도의 위치를 계산한다. 목표 작업 지점에 접근하면 추가적인 정밀 위치 보정(Fine Positioning)이 수행되어 남아 있는 위치 오차를 최소화한 후 실제 작업이 시작된다. 이러한 계층형 위치 추정(Hierarchical Localization)은 산업용 조립 및 검사에서 요구되는 반복 정밀도를 만족시킨다.

안전성(Safety)은 KMR iiwa를 대표하는 또 다른 특징이다. LBR iiwa 로봇은 각 관절에 토크 센서(Joint Torque Sensor)를 내장하여 사람이나 장애물과의 예기치 않은 접촉을 감지한다. 동시에 이동 플랫폼은 레이저 안전 스캐너(Laser Safety Scanner)를 이용하여 주변 사람과 장애물을 지속적으로 감시한다. 사람과의 거리에 따라 이동 속도, 가속도, 작업 가능 영역이 자동으로 조정되며, 별도의 안전 펜스(Safety Fence) 없이도 협동 작업(Human-Robot Collaboration)이 가능하다. 이러한 안전 기능은 생산 설비의 공간 활용도를 높이고 공장의 유연성을 향상시킨다.

KMR iiwa의 제어 구조(Control Architecture)는 기존 산업용 로봇과 크게 다르다. 이동 플랫폼 제어, 로봇 암 제어, 자율주행(Navigation), 환경 인식(Perception), 안전 감시(Safety Supervision), 작업 수행(Task Execution)이 하나의 통합 소프트웨어에서 동시에 수행된다. 최근에는 모델 예측 제어(MPC, Model Predictive Control), 최적화 기반 모션 계획(Optimization-based Motion Planning), 디지털 트윈(Digital Twin), 인공지능(AI)을 이용하여 이동 플랫폼과 로봇 암 전체를 하나의 운동학 시스템으로 제어한다. 즉, 바퀴와 로봇 암을 별도로 제어하는 것이 아니라 하나의 전체 시스템으로 최적화함으로써 위치 정밀도, 충돌 회피, 에너지 절감, 생산성을 동시에 향상시키고 있다.

KMR iiwa는 이후 등장한 다양한 산업용 이동형 매니퓰레이터에 큰 영향을 주었다. 현재 많은 제조사의 이동형 로봇은 전방향 이동, 협동 매니퓰레이션, 자율주행, 센서 융합, 통합 안전 기술을 동일한 철학으로 설계하고 있다. 앞으로 인공지능, 클라우드 로보틱스(Cloud Robotics), 디지털 트윈, 고성능 인식 시스템이 발전함에 따라 이동형 매니퓰레이터는 더욱 높은 자율성과 적응성을 가지며, 최소한의 인간 개입으로 복잡한 제조 작업을 수행하는 방향으로 발전할 것으로 예상된다.

### 1.1 메카넘 기반 이동형 매니퓰레이터 아키텍처 (Mecanum Based Mobile Manipulator Architecture)

---

KUKA KMR iiwa의 가장 큰 특징은 메카넘 휠(Mecanum Wheel)을 사용하는 이동 플랫폼과 협동 로봇 암을 하나의 통합 시스템으로 설계한 것이다. 일반적인 시스템은 이동 플랫폼과 로봇 암을 단순히 작업 순서(Task Sequencing)로 연결하지만, KMR iiwa는 두 시스템을 하나의 로봇 메커니즘으로 취급한다. 이러한 설계 철학은 자율주행(Navigation), 조작(Manipulation), 위치 정밀도(Positioning Accuracy), 충돌 회피(Collision Avoidance), 작업 효율(Operation Efficiency)을 동시에 최적화할 수 있도록 한다.

이동 플랫폼은 차체 네 모서리에 설치된 네 개의 독립 구동 메카넘 휠로 구성된다. 각 휠에는 휠 둘레에 대해 약 45도로 장착된 패시브 롤러(Passive Roller)가 배치되어 있다. 각 휠의 회전 속도를 독립적으로 제어함으로써 종방향 이동, 횡방향 이동, 회전 운동을 자유롭게 조합할 수 있으며, 별도의 조향 장치 없이도 원하는 방향으로 이동할 수 있다. 따라서 로봇은 어떤 방향에서도 작업 지점에 접근하면서 로봇 암의 자세를 유지할 수 있다.

이동 플랫폼 위에는 LBR iiwa 협동 로봇 암이 장착된다. 7자유도 로봇 암은 동일한 작업 위치에 대해 여러 가지 관절 자세를 생성할 수 있는 운동학적 중복성(Kinematic Redundancy)을 제공한다. 이동 플랫폼의 3자유도와 결합하면 전체 시스템은 총 10자유도를 가지게 된다. 이러한 중복성은 작업 공간을 크게 확장하며, 특이점(Singularity) 회피, 관절 한계(Joint Limit) 회피, 충돌 회피, 조작성(Manipulability), 에너지 효율을 동시에 최적화할 수 있도록 한다.

소프트웨어 아키텍처는 이러한 기계 구조를 계층적으로 제어한다. 상위 계층(Mission Planning)은 생산 목표와 작업 순서를 결정한다. 내비게이션 계획(Global Navigation Planning)은 공장 전체에서 충돌 없는 경로를 생성한다. 지역 경로 계획(Local Motion Planning)은 주변 장애물과 환경 변화에 따라 실시간으로 경로를 수정한다. 전신 모션 계획(Whole-body Motion Planning)은 이동 플랫폼의 휠 속도와 로봇 암의 관절 궤적을 동시에 계산하여 안정성을 유지하면서 작업을 수행한다.

위치 추정(Localization)은 여러 센서를 동시에 사용한다. 엔코더는 단기적인 이동량을 계산하고, 레이저 스캐너는 환경 지도를 생성하며, IMU는 차량 자세를 추정한다. 또한 비전 마커(Visual Marker)나 카메라는 작업 지점에서 고정밀 도킹 정보를 제공한다. 센서 융합 알고리즘은 이러한 정보를 통합하여 휠 슬립이나 일부 센서 성능 저하가 발생하더라도 높은 위치 정확도를 유지한다.

통신 구조(Communication Architecture)도 매우 중요하다. 실시간 필드버스(Fieldbus)는 휠 제어기, 로봇 관절, 안전 센서, 배터리 관리 시스템(BMS, Battery Management System), 온보드 컴퓨터(Onboard Computer)를 동기화한다. 결정론적 통신(Deterministic Communication)은 센서 인식, 경로 계획, 제어 명령 사이의 지연을 최소화하여 복잡한 작업에서도 이동 플랫폼과 로봇 암이 정확하게 협조하도록 한다. 최근에는 산업용 이더넷(Industrial Ethernet), TSN(Time-Sensitive Networking), ROS 2 DDS(Data Distribution Service)가 이러한 역할을 수행하고 있다.

메카넘 기반 구조의 또 다른 장점은 모듈화(Modularity)이다. 이동 플랫폼, 로봇 암, 엔드이펙터(End-effector), 배터리, 컴퓨팅 시스템, 센서를 각각 독립적으로 업그레이드할 수 있다. 따라서 동일한 플랫폼을 이용하여 공작기계 로딩(Machine Tending), 품질 검사(Quality Inspection), 물류 운반(Material Transport), 조립(Assembly), 팔레타이징(Palletizing), 실험실 자동화(Laboratory Automation), 협업 생산(Collaborative Manufacturing) 등 다양한 작업에 적용할 수 있다.

이러한 메카넘 기반 이동형 매니퓰레이터 구조는 이동성과 조작 기능을 하나의 지능형 로봇 시스템으로 통합한 대표적인 사례이며, 현재 대부분의 산업용 이동형 매니퓰레이터가 참고하는 표준 아키텍처가 되었다.

### 1.2 생산 라인에서의 정밀 위치 결정 성능 (Precision Positioning Performance in Production Line)

정밀 위치 결정(Precision Positioning)은 생산 라인에서 작업하는 이동형 매니퓰레이터의 가장 중요한 성능 가운데 하나이다. 일반적인 AMR은 자재를 운반하는 것이 주요 목적이지만, 이동형 매니퓰레이터는 조립(Assembly), 검사(Inspection), 공작기계 로딩(Machine Loading), 공구 교환(Tool Exchange), 협동 작업(Collaborative Manipulation)을 수행하기 위해 매우 높은 위치 정확도가 요구된다. KUKA KMR iiwa는 전역 위치 추정(Global Localization), 지역 위치 보정(Local Refinement), 센서 융합(Sensor Fusion), 적응형 제어(Adaptive Motion Control)를 결합한 다단계 위치 결정 전략을 적용하여 이러한 요구 사항을 만족한다.

장거리 이동(Long-distance Navigation)에서는 이동 플랫폼이 레이저 기반 위치 추정(Laser Localization), 엔코더 오도메트리(Encoder Odometry), IMU를 이용하여 공장 전체에서 안정적으로 이동한다. 그러나 아무리 정밀한 전역 위치 추정이라도 장거리 이동에서는 작은 위치 오차가 누적될 수 있으며, 실제 조립 작업은 이보다 훨씬 높은 정밀도를 요구한다.

따라서 작업 위치에 가까워지면 정밀 위치 보정(Fine Positioning)이 수행된다. 레이저 특징점(Laser Feature), 비전 마커(Fiducial Marker), 카메라 기반 기준점(Visual Landmark), 설비 기준 좌표(Machine Reference)를 이용하여 남아 있는 위치 오차를 줄인다. 최종 위치 정렬에서는 메카넘 휠의 측면 이동(Lateral Motion)을 적극 활용한다. 차량은 회전하지 않고도 좌우로 미세하게 이동할 수 있기 때문에 조향 구동(Steer Drive)보다 더 빠르고 높은 반복 정밀도로 설비와 정렬할 수 있다.

로봇 암의 보정(Calibration)도 위치 정밀도 향상에 중요한 역할을 한다. 이동 플랫폼 좌표계(Base Frame), 로봇 암 좌표계, 공구 중심점(TCP, Tool Center Point), 작업물 좌표계 사이의 정확한 변환 관계를 보정한다. 또한 온도 변화(Thermal Expansion), 구조 변형(Mechanical Compliance), 적재 하중 변화(Payload Variation), 장기간 사용에 따른 구조 변화(Structural Drift)를 지속적으로 보상한다. 고분해능 엔코더와 토크 센서는 작업 중에도 높은 위치 정확도와 유연한 힘 제어를 동시에 제공한다.

산업 현장에서는 절대 위치 정확도보다 반복 정밀도(Repeatability)가 더욱 중요하다. 생산 라인은 동일한 작업을 하루에도 수천 번 반복한다. 절대 위치에 약간의 오차가 존재하더라도 반복성이 우수하면 비전 시스템이나 힘 제어 시스템이 쉽게 보정할 수 있다. 따라서 이동형 매니퓰레이터는 절대 위치 정확도보다 **도킹 반복성(Docking Repeatability)**, **안정적인 좌표 변환(Coordinate Transformation)**, **일관된 접근 궤적(Repeatable Approach Trajectory)**을 더욱 중요하게 설계한다.

환경 조건(Environmental Condition)은 위치 성능에 직접적인 영향을 준다. 바닥 평탄도(Floor Flatness), 휠 마모(Wheel Wear), 적재 하중 분포(Payload Distribution), 진동(Vibration), 조명(Lighting), 장애물 밀도(Obstacle Density)는 모두 위치 추정 성능을 변화시킨다. 적응형 제어는 이러한 환경 변화를 지속적으로 추정하여 차량 속도, 가속도, 슬립 보상, 센서 가중치(Sensor Weighting)를 자동으로 조정함으로써 위치 정확도를 유지한다.

최근에는 인공지능을 이용한 위치 제어도 활발히 적용되고 있다. 머신러닝은 휠 마모를 예측하고 반복적으로 발생하는 위치 오차를 학습하며, 과거 운행 데이터를 이용하여 도킹 경로를 최적화한다. 디지털 트윈은 실제 생산 라인에 적용하기 전에 다양한 환경에서 위치 성능을 시뮬레이션하고, 예지보전은 구동계의 열화를 조기에 발견하여 위치 성능 저하를 방지한다.

KUKA KMR iiwa가 제시한 이러한 위치 결정 철학은 현재 대부분의 산업용 이동형 매니퓰레이터가 채택하고 있는 표준 방식이 되었다. 최신 시스템은 초정밀 전역 위치 추정만을 의존하지 않고, **계층형 위치 추정(Hierarchical Localization)**, **적응형 위치 보정(Adaptive Refinement)**, **지능형 보정(Intelligent Calibration)**, **환경 인식(Environment Awareness)**을 통합하여 높은 반복 정밀도를 확보한다. 이러한 접근 방식은 고정형 산업용 로봇이 제공하지 못하는 이동성과 유연성을 유지하면서도, 자동화 생산 라인에서 요구되는 높은 정밀도와 생산성을 동시에 만족시키고 있다.

## 02 Clearpath Ridgeback

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

The Clearpath Ridgeback is one of the most widely adopted omnidirectional autonomous mobile robot (AMR) platforms in robotics research, academic laboratories, industrial prototyping, and flexible automation development. Unlike production-oriented mobile robots that are optimized for a single application, the Ridgeback was intentionally designed as a highly configurable research platform capable of supporting a broad spectrum of experimental hardware, robotic manipulators, perception systems, and autonomous software architectures. Its omnidirectional mobility, open software ecosystem, modular mechanical structure, and native integration with the Robot Operating System (ROS) have made it a standard reference platform for research involving autonomous navigation, mobile manipulation, human-robot interaction, multi-robot coordination, warehouse automation, and AI-based robotic systems.

The Ridgeback employs a four-wheel omnidirectional drive system utilizing independently driven omni wheels positioned symmetrically around the chassis. This configuration provides three fully controllable planar degrees of freedom consisting of longitudinal translation, lateral translation, and rotation about the vertical axis. Unlike conventional differential-drive robots that require heading changes before lateral repositioning, the Ridgeback can move directly in any direction while maintaining a constant orientation. This capability significantly simplifies autonomous docking, collaborative manipulation, laboratory automation, and experimental validation where precise vehicle positioning is required.

One of the defining characteristics of the Ridgeback is its modularity. The upper payload deck is intentionally designed as an open mechanical interface capable of accommodating industrial robot arms, collaborative manipulators, LiDAR systems, RGB-D cameras, stereo vision sensors, computing hardware, battery expansion modules, communication devices, and custom experimental equipment. Researchers can therefore transform the same mobile platform into a warehouse transporter, autonomous inspection robot, collaborative mobile manipulator, laboratory automation system, or autonomous logistics platform without redesigning the base vehicle. This flexibility has contributed significantly to the platform\'s popularity among universities and industrial research organizations.

The electrical and computing architecture of the Ridgeback further supports rapid experimentation. Multiple power interfaces provide regulated outputs for external hardware, while Ethernet, USB, CAN, serial communication, and wireless networking enable seamless integration of diverse sensing and computing modules. High-performance onboard computers execute localization, navigation, perception, manipulation, and artificial intelligence algorithms simultaneously. Because the hardware architecture follows modular engineering principles, users may upgrade processors, graphics hardware, storage devices, and communication systems independently according to project requirements.

Autonomous navigation represents another major strength of the Ridgeback platform. Laser scanners, inertial measurement units, wheel encoders, cameras, and optional GNSS receivers cooperate through sensor fusion algorithms to provide reliable localization under diverse indoor and semi-structured environments. Simultaneous Localization and Mapping (SLAM), adaptive localization, dynamic obstacle avoidance, and autonomous path planning operate within the standard ROS navigation framework while remaining extensible for advanced research. Consequently, researchers can concentrate on algorithm development instead of low-level vehicle integration.

The Ridgeback has become particularly important in the field of mobile manipulation. Numerous laboratories combine the mobile base with robotic arms such as Universal Robots, Kinova, Kinova Gen3, Franka Emika Panda, or other collaborative manipulators. The resulting systems investigate coordinated whole-body motion planning, manipulation under mobility constraints, visual servoing, grasp planning, human-robot collaboration, and autonomous assembly. Since the omnidirectional base provides unrestricted planar motion, manipulator redundancy increases substantially, enabling sophisticated optimization algorithms that simultaneously consider arm posture, vehicle motion, collision avoidance, manipulability, and energy efficiency.

Artificial intelligence research increasingly utilizes the Ridgeback as an experimental platform for physical AI. Deep reinforcement learning, imitation learning, semantic mapping, visual navigation, multimodal perception, embodied AI, and autonomous task planning can all be evaluated using a standardized hardware platform supported by extensive ROS software libraries. This combination of open hardware, modular architecture, and mature software infrastructure has established the Ridgeback as one of the most influential research platforms in modern autonomous robotics.

---

### 2.1 Omni Drive for Research and Flexible Automation

---

### 2.2 ROS2 Integration Case

---

Clearpath Ridgeback은 연구용 로보틱스(Research Robotics), 대학 연구실(Academic Laboratory), 산업용 프로토타이핑(Industrial Prototyping), 유연 자동화(Flexible Automation) 개발 분야에서 가장 널리 사용되는 전방향 이동 자율이동로봇(AMR, Autonomous Mobile Robot) 플랫폼 가운데 하나이다. 특정 산업용 애플리케이션(Application)에 최적화된 상용 로봇과 달리, Ridgeback은 다양한 실험 장비, 로봇 매니퓰레이터(Robotic Manipulator), 인식 시스템(Perception System), 자율주행 소프트웨어를 자유롭게 장착할 수 있도록 설계된 개방형(Open Architecture) 연구 플랫폼이다. 전방향 이동성(Omnidirectional Mobility), 개방형 소프트웨어(Open Software Ecosystem), 모듈형 기계 구조(Modular Mechanical Structure), 그리고 ROS(Robot Operating System)와의 높은 호환성 덕분에 자율주행(Autonomous Navigation), 이동형 매니퓰레이션(Mobile Manipulation), 인간-로봇 상호작용(Human-Robot Interaction), 다중 로봇 협업(Multi-Robot Coordination), 창고 자동화(Warehouse Automation), 인공지능(AI) 기반 로봇 연구의 대표적인 플랫폼으로 자리 잡고 있다.

Ridgeback은 차체 네 모서리에 독립적으로 구동되는 네 개의 옴니 휠(Omni Wheel)을 배치한 전방향 구동 시스템을 사용한다. 이를 통해 종방향 이동(Longitudinal Translation), 횡방향 이동(Lateral Translation), 회전(Rotation)의 3자유도(3 Degrees of Freedom)를 완전히 독립적으로 제어할 수 있다. 일반적인 차동 구동(Differential Drive) 차량이 측면 이동을 위해 반드시 방향 전환을 해야 하는 것과 달리, Ridgeback은 차량의 자세를 유지한 채 원하는 방향으로 직접 이동할 수 있다. 이러한 특성은 정밀 도킹(Precision Docking), 협업 매니퓰레이션(Collaborative Manipulation), 연구실 자동화(Laboratory Automation), 다양한 실험 환경에서 매우 큰 장점을 제공한다.

Ridgeback의 가장 큰 특징 가운데 하나는 뛰어난 모듈성(Modularity)이다. 상부 적재 플랫폼(Payload Deck)은 산업용 로봇 암, 협동 로봇(Collaborative Manipulator), LiDAR, RGB-D 카메라, 스테레오 비전(Stereo Vision), 산업용 컴퓨터(Industrial Computer), 배터리 확장 모듈(Battery Expansion Module), 통신 장치(Communication Device), 사용자 정의 장비(Custom Experimental Equipment)를 자유롭게 장착할 수 있도록 설계되어 있다. 따라서 동일한 플랫폼을 창고 운반 로봇(Warehouse Transporter), 검사 로봇(Inspection Robot), 이동형 매니퓰레이터(Mobile Manipulator), 연구용 플랫폼, 자율 물류 시스템(Autonomous Logistics Platform) 등 다양한 용도로 활용할 수 있다.

전기 시스템(Electrical Architecture)과 컴퓨팅 구조(Computing Architecture) 역시 연구 목적에 맞게 매우 유연하게 설계되어 있다. 여러 종류의 전원 인터페이스(Power Interface)는 외부 장비에 안정적인 전원을 공급하며, Ethernet, USB, CAN, Serial Communication, Wireless Network는 다양한 센서와 컴퓨터를 쉽게 연결할 수 있도록 지원한다. 고성능 온보드 컴퓨터(Onboard Computer)는 위치 추정(Localization), 자율주행(Navigation), 인식(Perception), 매니퓰레이션(Manipulation), 인공지능(AI) 알고리즘을 동시에 실행할 수 있으며, 필요에 따라 GPU나 저장장치(Storage)를 자유롭게 업그레이드할 수 있다.

자율주행 역시 Ridgeback의 중요한 장점이다. 레이저 스캐너(Laser Scanner), IMU(Inertial Measurement Unit), 엔코더(Encoder), 카메라(Camera), GNSS(Optional GNSS Receiver) 등을 센서 융합(Sensor Fusion)으로 통합하여 안정적인 위치 추정(Localization)을 수행한다. SLAM(Simultaneous Localization and Mapping), 적응형 위치 추정(Adaptive Localization), 동적 장애물 회피(Dynamic Obstacle Avoidance), 자율 경로 계획(Path Planning)은 ROS Navigation Framework와 자연스럽게 통합되어 있으며, 연구자는 차량 제어보다 알고리즘 개발에 더욱 집중할 수 있다.

Ridgeback은 이동형 매니퓰레이션 분야에서도 널리 활용된다. 많은 연구실에서는 Universal Robots, Kinova, Kinova Gen3, Franka Emika Panda와 같은 협동 로봇을 Ridgeback 위에 장착하여 사용한다. 이러한 시스템은 전신 모션 계획(Whole-body Motion Planning), 이동 중 조작(Manipulation under Mobility Constraints), 비전 서보잉(Visual Servoing), 그립 계획(Grasp Planning), 협동 작업(Human-Robot Collaboration), 자율 조립(Autonomous Assembly) 등을 연구하는 데 사용된다. 전방향 이동 플랫폼은 측면 이동이 자유롭기 때문에 로봇 암의 작업 공간을 크게 확장하고, 자세 최적화(Posture Optimization), 충돌 회피(Collision Avoidance), 조작성(Manipulability), 에너지 효율(Energy Efficiency)을 동시에 향상시킬 수 있다.

최근에는 인공지능 기반 물리 AI(Physical AI) 연구에서도 Ridgeback이 널리 활용되고 있다. 심층 강화학습(Deep Reinforcement Learning), 모방 학습(Imitation Learning), 의미 지도(Semantic Mapping), 비전 기반 자율주행(Visual Navigation), 멀티모달 인식(Multimodal Perception), 체화 AI(Embodied AI), 자율 작업 계획(Autonomous Task Planning) 등을 검증하기 위한 대표적인 연구 플랫폼으로 사용되고 있다. 개방형 하드웨어(Open Hardware), 모듈형 구조(Modular Architecture), ROS 기반 소프트웨어 생태계는 Ridgeback을 현대 자율주행 로보틱스 연구에서 가장 영향력 있는 플랫폼 가운데 하나로 만들었다.

### 2.1 연구 및 유연 자동화를 위한 전방향 구동 (Omni Drive for Research and Flexible Automation)

---

Clearpath Ridgeback의 전방향 구동 구조는 특정 산업용 작업만을 위해 설계된 것이 아니라 다양한 연구와 실험을 수행할 수 있도록 설계되었다. 연구용 플랫폼은 센서, 소프트웨어, 로봇 암, 적재 장비, 연구 목적이 지속적으로 바뀌기 때문에 생산용 로봇과는 요구 사항이 다르다. Ridgeback은 이러한 환경을 고려하여 개방성(Openness), 모듈성(Modularity), 확장성(Configurability)을 유지하면서 안정적인 전방향 이동을 제공하도록 설계되었다.

기계 구조는 네 개의 독립 구동 옴니 휠을 차체 아래에 대칭적으로 배치한 구조이다. 각 휠에는 자유롭게 회전하는 패시브 롤러가 장착되어 있어 구동 방향에서는 충분한 추진력을 제공하면서도 횡방향 이동을 자유롭게 수행할 수 있다. 네 개의 휠 속도를 독립적으로 제어함으로써 직진, 측면 이동, 회전을 자유롭게 조합할 수 있으며, 차동 구동(Differential Drive)이나 애커만 조향(Ackermann Steering) 차량에서 발생하는 조향 제약 없이 다양한 자율주행 알고리즘을 연구할 수 있다.

유연 자동화(Flexible Automation)는 작업 환경이 지속적으로 변화하는 제조 공장을 대상으로 한다. 작업 셀(Workstation)의 위치, 생산 순서, 물류 흐름이 계속 변경되는 환경에서는 기존의 고정 자동화(Fixed Automation)가 많은 설비 변경을 요구한다. 그러나 전방향 이동 플랫폼은 로봇이 작업 위치를 자유롭게 이동할 수 있으므로 생산 설비를 쉽게 재배치할 수 있다. 측면 이동은 도킹(Docking), 좁은 통로(Narrow Aisle) 이동, 팔레트 운반(Pallet Handling), 연구실 자동화(Laboratory Automation), 협업 제조(Collaborative Manufacturing)를 매우 효율적으로 수행하게 해준다.

연구 환경에서는 모듈형 적재 구조(Modular Payload Interface)의 장점이 더욱 크다. 산업용 로봇 암, 검사 장비, 의료 장비, 적층 제조(Additive Manufacturing), 과학 장비(Scientific Instrumentation), 자율 검사 시스템 등을 동일한 플랫폼에 쉽게 장착할 수 있다. 전원 공급과 통신 인터페이스도 표준화(Standardized Interface)되어 있으므로 기본 차량을 변경하지 않고도 다양한 실험을 수행할 수 있다. 이러한 이유로 하나의 Ridgeback 플랫폼이 수년 동안 여러 연구 프로젝트에서 반복적으로 활용되는 경우가 많다.

소프트웨어의 유연성도 매우 뛰어나다. 연구자는 위치 추정 알고리즘(Localization Algorithm), 자율주행(Navigation Planner), 인식 시스템(Perception Pipeline), 인공지능 프레임워크(AI Framework), 모션 제어기(Motion Controller), 통신 미들웨어(Communication Middleware)를 자유롭게 변경하면서도 동일한 하드웨어를 계속 사용할 수 있다. 하드웨어와 소프트웨어가 분리된 구조이므로 새로운 알고리즘을 매우 빠르게 검증할 수 있으며, ROS 기반 구조는 다른 로봇 플랫폼으로의 이식성(Portability)도 매우 우수하다.

전방향 이동은 이동형 매니퓰레이션에도 큰 장점을 제공한다. 차량은 조향 없이도 측면 이동을 수행할 수 있으므로 로봇 암이 작업하는 동안 차량도 동시에 위치를 조정할 수 있다. 따라서 전신 모션 계획(Whole-body Motion Planning)은 차량과 로봇 암을 동시에 최적화하여 더욱 부드러운 궤적(Trajectory), 높은 조작성(Manipulability), 특이점 회피(Singularity Avoidance), 넓은 작업 공간을 제공한다.

교육용 플랫폼으로서의 가치도 매우 높다. 학생들은 하나의 Ridgeback 플랫폼만으로 운동학(Kinematics), 동역학(Dynamics), 위치 추정(Localization), 센서 융합(Sensor Fusion), 경로 계획(Path Planning), 제어(Control Theory), 매니퓰레이션(Manipulation), 컴퓨터 비전(Computer Vision), 머신러닝(Machine Learning), 인간-로봇 상호작용(Human-Robot Interaction), 클라우드 로보틱스(Cloud Robotics), 플릿 관리(Fleet Management), 디지털 트윈(Digital Twin) 등을 모두 연구할 수 있다. 이러한 뛰어난 활용성 덕분에 Ridgeback은 세계적으로 가장 널리 사용되는 연구 플랫폼 가운데 하나가 되었다.

### 2.2 ROS2 통합 사례 (ROS2 Integration Case)

Clearpath Ridgeback이 연구 및 산업 분야에서 널리 사용되는 가장 큰 이유 가운데 하나는 ROS(Robot Operating System), 특히 ROS2와의 뛰어난 통합성이다. 최근 로봇 시스템은 점점 더 분산화(Distributed), 모듈화(Modular), 실시간화(Real-time)되고 있으며, ROS2는 이러한 요구 사항을 만족하는 대표적인 소프트웨어 프레임워크가 되었다. Ridgeback은 ROS2 기반 자율주행 시스템을 구현하는 대표적인 표준 플랫폼으로 활용되고 있다.

소프트웨어 구조는 계층형(Layered Architecture)으로 구성된다. 가장 하위 계층은 휠 모터(Wheel Motor), 엔코더, IMU, 배터리(Battery), 비상 정지(Emergency Stop), 통신 장치를 제어하는 하드웨어 드라이버(Hardware Driver)이다. 그 위에는 ROS2 노드(Node)가 위치하여 위치 추정(Localization), 지도 작성(Mapping), 자율주행(Navigation), 인식(Perception), 매니퓰레이션(Manipulation), 진단(Diagnostics), 작업 수행(Mission Execution)을 담당한다. 각각의 노드는 DDS(Data Distribution Service)를 통해 통신하며, 여러 대의 컴퓨터와 클라우드 서버 간에도 안정적으로 데이터를 공유할 수 있다.

ROS2는 기존 ROS보다 훨씬 뛰어난 실시간성(Real-time Determinism)을 제공한다. QoS(Quality of Service), Lifecycle Node, Secure Communication, Distributed Execution 등의 기능을 통해 산업용 로봇에서도 높은 신뢰성을 제공한다. Ridgeback은 이러한 기능을 활용하여 이동 제어(Motion Control), 위치 추정(Localization), 안전 감시(Safety Monitoring), 인식(Perception), 매니퓰레이션(Manipulation)을 동시에 수행하면서도 안정적인 실시간 통신을 유지한다. 특히 이동 플랫폼과 로봇 암을 동시에 제어하는 이동형 매니퓰레이션에서는 이러한 결정론적 통신이 매우 중요하다.

자율주행은 ROS2 통합의 대표적인 사례이다. 엔코더, IMU, LiDAR, Visual Odometry, GNSS 정보를 위치 추정 노드(Localization Node)가 융합하여 차량의 위치를 계산한다. 전역 경로 계획(Global Planner)은 충돌 없는 경로를 생성하고, 지역 경로 계획(Local Planner)은 움직이는 장애물을 피해 실시간으로 경로를 수정한다. 최근에는 Behavior Tree가 상위 작업 제어(Task Sequencing)를 담당하여 더욱 유연한 작업 수행이 가능해지고 있다.

이동형 매니퓰레이션 역시 ROS2 통합의 대표적인 사례이다. Ridgeback은 MoveIt 2와 직접 연동되어 이동 플랫폼과 로봇 암을 하나의 시스템으로 제어한다. 전신 모션 계획은 휠 운동학(Wheel Kinematics), 로봇 관절(Joint Limit), 충돌 모델(Collision Geometry), 작업 공간(Workspace), 작업 목표(Task Objective)를 동시에 고려하여 최적의 움직임을 계산한다. 따라서 차량과 로봇 암을 별도로 제어하는 방식보다 훨씬 높은 작업 효율을 얻을 수 있다.

클라우드 및 엣지 컴퓨팅(Cloud & Edge Computing)도 ROS2 생태계의 중요한 부분이다. Ridgeback은 엣지 로봇(Edge Robot)으로 동작하면서 클라우드 서버와 연결되어 의미 지도(Semantic Mapping), AI 추론(AI Inference), 디지털 트윈(Digital Twin), 플릿 관리(Fleet Coordination), 장기 데이터 관리(Long-term Data Management)를 수행한다. DDS 기반 구조는 계산 작업을 차량 내부 컴퓨터, 엣지 서버, 클라우드 서버 사이에서 자유롭게 분산시킬 수 있도록 한다.

결과적으로 Ridgeback은 현대 ROS2 시스템 구조를 가장 잘 보여주는 대표적인 플랫폼이 되었다. 전방향 이동성, 모듈형 하드웨어, 표준화된 소프트웨어 인터페이스, 분산 통신, 활발한 오픈소스 커뮤니티(Open-source Community)를 기반으로 연구자와 산업 개발자는 매우 빠르게 자율주행 로봇을 개발할 수 있다. 앞으로 ROS2가 산업 표준으로 더욱 확산됨에 따라 Ridgeback은 차세대 **자율이동로봇(AMR)**, **이동형 매니퓰레이터(Mobile Manipulator)**, **AI 네이티브 로봇(AI-native Robot)** 개발을 위한 대표적인 기준 플랫폼으로 계속 활용될 것으로 전망된다.

## 03 SEER SRC series Mecanum

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

The SEER SRC Series represents one of the most advanced commercial implementations of Mecanum-wheel Autonomous Mobile Robots (AMRs) designed specifically for precision industrial logistics and semiconductor manufacturing. Unlike general-purpose warehouse robots, the SRC Series has been engineered to satisfy the demanding requirements of cleanroom operation, precision positioning, continuous 24/7 production, and high-value material transportation. The combination of omnidirectional mobility, intelligent fleet management, precision localization, and industrial-grade reliability enables the SRC Series to operate efficiently in environments where productivity and contamination control are equally critical.

The platform utilizes a four-wheel Mecanum drive configuration in which each wheel is independently powered by a servo motor and equipped with high-resolution encoders. The forty-five-degree passive rollers mounted around each wheel generate independent longitudinal and lateral force components, allowing the robot to perform holonomic motion with three controllable planar degrees of freedom. Forward, backward, lateral, diagonal, and rotational movements can be executed simultaneously without changing vehicle orientation. This capability significantly reduces maneuvering time inside narrow cleanroom aisles and enables rapid alignment with processing equipment, storage racks, automated docking stations, and load transfer interfaces.

Mechanical architecture emphasizes structural rigidity and vibration isolation. The chassis is designed to minimize frame deformation under varying payload conditions while maintaining accurate wheel geometry throughout continuous operation. Precision-machined aluminum structures, optimized load paths, and finite element analysis are commonly employed to achieve high stiffness-to-weight ratios. Internal component placement also considers center-of-gravity optimization, thermal balance, cable routing, and maintenance accessibility. Battery modules, industrial computers, servo amplifiers, and communication hardware are distributed carefully to preserve vehicle stability during multidirectional acceleration.

Localization and navigation rely upon multiple complementary sensing technologies. Two-dimensional LiDAR scanners provide simultaneous localization and mapping capabilities while laser reflectors or natural feature localization improve repeatability inside structured production facilities. Wheel encoder odometry supplies continuous short-term motion estimation, whereas inertial measurement units compensate for transient wheel slip and rotational disturbances. Vision-based localization and precision docking cameras may further refine positioning accuracy near production equipment requiring millimeter-level alignment.

The SRC Series also incorporates comprehensive industrial communication architecture. EtherCAT, industrial Ethernet, wireless communication, fleet management software, manufacturing execution systems, warehouse management systems, and semiconductor material handling controllers exchange information continuously. Real-time coordination enables traffic management, dynamic mission scheduling, automatic charging, predictive maintenance, and production optimization. Integration with higher-level factory control systems allows mobile robots to become active participants within fully digital manufacturing environments rather than operating as isolated transport vehicles.

Safety architecture combines functional safety with collaborative operation. Multiple laser safety scanners continuously monitor the surrounding environment, generating configurable warning zones and protective stop regions. Safety PLCs supervise emergency stop circuits, drive controllers, battery systems, communication status, and sensor diagnostics. Dynamic speed reduction according to environmental conditions improves both operational efficiency and human safety while preserving smooth material transport.

Artificial intelligence increasingly enhances operational performance. Fleet-wide operational data are analyzed to optimize traffic flow, charging schedules, maintenance planning, localization robustness, and energy consumption. Digital twins simulate factory layouts and evaluate mission scheduling before deployment, reducing commissioning time and improving production efficiency. These technologies collectively establish the SEER SRC Series as an advanced mobile robotics platform suitable for the increasingly demanding requirements of semiconductor manufacturing and high-precision industrial automation.

---

### 3.1 Mecanum Wheel AMR in Semiconductor Fab

---

### 3.2 Vibration Management in Cleanroom Environment

---

SEER SRC 시리즈(SEER SRC Series)는 정밀 산업 물류(Precision Industrial Logistics)와 반도체 제조(Semiconductor Manufacturing)를 위해 개발된 가장 발전된 상용 메카넘 휠(Mecanum Wheel) 기반 자율이동로봇(AMR, Autonomous Mobile Robot) 가운데 하나이다. 일반적인 창고용 AMR와 달리 SRC 시리즈는 클린룸(Cleanroom) 운용, 정밀 위치 결정(Precision Positioning), 연속적인 24시간 생산(Continuous 24/7 Production), 그리고 고가치 소재(High-value Material)의 운반을 만족하도록 설계되었다. 전방향 이동성(Omnidirectional Mobility), 지능형 플릿 관리(Intelligent Fleet Management), 정밀 위치 추정(Localization), 산업용 수준의 신뢰성(Industrial-grade Reliability)을 결합하여 생산성과 오염 제어(Contamination Control)가 동시에 요구되는 환경에서 매우 효율적으로 운용될 수 있다.

플랫폼은 네 개의 메카넘 휠을 사용하는 4륜 독립 구동(Four-wheel Independent Drive) 구조를 채택하고 있다. 각 휠은 서보 모터(Servo Motor)와 고분해능 엔코더(High-resolution Encoder)에 의해 독립적으로 제어된다. 휠 둘레에는 약 45도로 배치된 패시브 롤러(Passive Roller)가 장착되어 있으며, 이를 통해 종방향(Longitudinal)과 횡방향(Lateral) 힘을 동시에 생성할 수 있다. 결과적으로 차량은 자세를 변경하지 않고도 전진, 후진, 측면 이동, 대각선 이동, 회전을 자유롭게 수행할 수 있다. 이러한 특성은 좁은 클린룸 통로에서 방향 전환 시간을 크게 줄이고, 공정 장비(Process Equipment), 자동 도킹 스테이션(Docking Station), 저장 랙(Storage Rack), 이송 인터페이스(Load Transfer Interface)와의 정밀 정렬을 매우 빠르게 수행하도록 한다.

기계 구조(Mechanical Architecture)는 높은 강성(Structural Rigidity)과 진동 절연(Vibration Isolation)에 중점을 두고 설계된다. 차체는 다양한 적재 조건에서도 변형이 최소화되도록 설계되며, 지속적인 운행 중에도 휠 기하학(Wheel Geometry)이 유지된다. 고정밀 알루미늄 구조(Precision-machined Aluminum Structure), 최적화된 하중 전달 구조(Optimized Load Path), 유한요소해석(Finite Element Analysis)이 일반적으로 적용된다. 또한 배터리(Battery), 산업용 컴퓨터(Industrial Computer), 서보 드라이브(Servo Amplifier), 통신 장치(Communication Hardware)는 무게중심(Center of Gravity), 열 균형(Thermal Balance), 케이블 배치(Cable Routing), 유지보수 편의성을 고려하여 배치된다.

위치 추정(Localization)과 자율주행(Navigation)은 다양한 센서를 융합하여 수행된다. 2D LiDAR는 SLAM(Simultaneous Localization and Mapping)을 수행하며, 레이저 리플렉터(Laser Reflector)나 자연 특징(Natural Feature)을 이용하여 반복 위치 정밀도를 향상시킨다. 휠 엔코더는 단거리 이동을 지속적으로 계산하며, IMU(Inertial Measurement Unit)는 순간적인 슬립(Wheel Slip)과 회전 오차(Rotational Disturbance)를 보정한다. 작업 장비 근처에서는 비전 기반 위치 추정(Vision-based Localization)과 정밀 도킹 카메라(Precision Docking Camera)를 이용하여 밀리미터 수준의 위치 정렬을 수행한다.

SRC 시리즈는 산업용 통신 구조(Industrial Communication Architecture)도 완전히 통합되어 있다. EtherCAT, 산업용 이더넷(Industrial Ethernet), 무선 통신(Wireless Communication), 플릿 관리 시스템(Fleet Management System), 제조 실행 시스템(MES, Manufacturing Execution System), 창고 관리 시스템(WMS, Warehouse Management System), 반도체 물류 제어 시스템이 실시간으로 데이터를 교환한다. 이를 통해 교통 제어(Traffic Management), 작업 스케줄링(Mission Scheduling), 자동 충전(Auto Charging), 예지보전(Predictive Maintenance), 생산 최적화(Production Optimization)를 동시에 수행할 수 있다.

안전 구조(Safety Architecture)는 기능 안전(Functional Safety)과 협업 운용(Collaborative Operation)을 동시에 고려한다. 여러 개의 레이저 안전 스캐너(Laser Safety Scanner)가 주변 환경을 지속적으로 감시하며, 경고 영역(Warning Zone)과 보호 정지 영역(Protective Stop Zone)을 동적으로 생성한다. 안전 PLC(Safety PLC)는 비상 정지(Emergency Stop), 서보 드라이브, 배터리, 통신 상태, 센서 이상을 지속적으로 감시한다. 또한 주변 환경에 따라 속도를 자동으로 조절하여 생산성과 안전성을 동시에 확보한다.

최근에는 인공지능(AI)이 SRC 시리즈의 성능을 더욱 향상시키고 있다. 플릿 전체에서 수집되는 운행 데이터를 분석하여 교통 흐름, 충전 일정, 유지보수 계획, 위치 추정 안정성, 에너지 소비를 최적화한다. 디지털 트윈(Digital Twin)은 실제 공장에 적용하기 전에 공장 배치와 작업 계획을 시뮬레이션하여 구축 시간을 줄이고 생산성을 높인다. 이러한 기술은 SRC 시리즈를 반도체 공장과 고정밀 산업 자동화를 위한 대표적인 AMR 플랫폼으로 만들고 있다.

### 3.1 반도체 공장의 메카넘 휠 AMR (Mecanum Wheel AMR in Semiconductor Fab)

---

반도체 제조 공장(Semiconductor Fabrication Facility)은 자율이동로봇에게 가장 까다로운 환경 가운데 하나이다. 매우 높은 위치 정밀도(Positioning Accuracy), 지속적인 신뢰성(Continuous Reliability), 오염 제어(Contamination Control), 그리고 생산 중단 없는 운용(Uninterrupted Production)이 동시에 요구된다. SEER SRC 시리즈는 메카넘 휠 기반 전방향 이동과 정밀 위치 추정, 고정밀 모션 제어, 클린룸 대응 설계를 결합하여 이러한 요구 사항을 만족시킨다.

반도체 생산은 노광(Lithography), 증착(Deposition), 식각(Etching), 세정(Cleaning), 계측(Metrology), 검사(Inspection), 저장(Storage) 등 수백 개의 공정으로 구성된다. 웨이퍼 캐리어(Wafer Carrier)는 이러한 장비 사이를 매우 정확하게 이동해야 하며, 운반 과정에서 진동(Vibration), 오염(Contamination), 지연(Delay)을 최소화해야 한다.

기존에는 천장 반송 시스템(OHT, Overhead Hoist Transport)이나 AGV가 주로 사용되었지만, 메카넘 휠 AMR는 별도의 고정 인프라 없이 자유롭게 이동할 수 있기 때문에 훨씬 높은 유연성을 제공한다.

메카넘 휠의 가장 큰 장점은 측면 이동(Lateral Motion)이다. 차량이 회전하지 않고도 장비의 로드 포트(Load Port)에 직접 접근할 수 있기 때문에 도킹 시간이 짧아지고 반복 정밀도(Repeatability)가 향상된다. 반도체 장비는 주변 공간이 매우 협소하기 때문에 이러한 측면 이동 기능은 생산성을 크게 향상시킨다. 또한 여러 대의 로봇이 좁은 클린룸 통로에서도 플릿 관리(Fleet Management)를 통해 효율적으로 동시에 운행할 수 있다.

정밀 위치 추정은 반도체 응용에서 필수 요소이다. LiDAR 기반 SLAM은 공장 전체에서 차량 위치를 계산하고, 엔코더는 단거리 이동을 계산하며, IMU는 순간적인 외란을 보정한다. 장비 근처에서는 비전 마커(Fiducial Marker), 레이저 리플렉터, 정밀 도킹 센서를 이용하여 위치 오차를 밀리미터 수준까지 줄인다. 이러한 계층형 위치 추정(Hierarchical Localization)은 웨이퍼 이송 과정의 높은 반복 정밀도를 보장한다.

클린룸 적합성(Cleanroom Compatibility)도 매우 중요하다. 모든 기계 부품은 파티클(Particle) 발생을 최소화하도록 선택되며, 윤활유 누출(Lubricant Leakage)과 가스 방출(Outgassing)을 줄이는 재질을 사용한다. 휠 재질도 에폭시 바닥(Epoxy Floor)에서 충분한 접지력을 확보하면서 마모를 최소화하도록 설계된다. 외부 표면은 청소가 쉽도록 매끄럽게 설계되어 먼지 축적을 방지한다.

운용 신뢰성 또한 핵심 요소이다. 반도체 생산은 연중무휴(24/7)로 운영되기 때문에 예측 가능한 유지보수와 높은 가동률이 필수적이다. 이를 위해 중복 센서(Redundant Sensor), 예지보전(Predictive Maintenance), 배터리 상태 관리(Battery Health Monitoring), 자동 충전(Auto Charging), 원격 진단(Remote Diagnostics), 플릿 모니터링(Fleet Supervision)이 적용된다. AI는 장기간 운행 데이터를 분석하여 부품 열화를 예측하고 생산 중단을 최소화한다.

향후 스마트 반도체 공장에서는 AMR가 MES, 디지털 트윈, 생산 스케줄러, AI 최적화 시스템과 직접 연결되어 단순한 운반 장비가 아닌 생산 시스템의 핵심 자원(Intelligent Manufacturing Resource)으로 발전할 것으로 예상된다.

### 3.2 클린룸 환경에서의 진동 관리 (Vibration Management in Cleanroom Environment)

진동 관리(Vibration Management)는 메카넘 휠 AMR가 반도체 클린룸에서 운용될 때 가장 중요한 기술 과제 가운데 하나이다. 전방향 이동은 뛰어난 기동성을 제공하지만, 패시브 롤러가 반복적으로 바닥과 접촉하는 구조 때문에 본질적으로 주기적인 진동(Periodic Vibration)이 발생한다. 이러한 진동은 반도체 제품, 정밀 장비, 계측 시스템에 영향을 줄 수 있으므로 철저한 제어가 필요하다.

가장 큰 진동 발생 원인은 롤러 전환(Roller Transition)이다. 휠이 회전하면서 각 롤러가 반복적으로 바닥과 접촉하고 분리되며, 이 과정에서 유효 반경(Effective Wheel Radius)과 접촉 강성(Contact Stiffness)이 지속적으로 변한다. 이러한 변화는 일정한 가진 주파수(Excitation Frequency)를 발생시키며, 속도가 높아질수록 진동 크기도 증가한다. 바닥 요철(Floor Irregularity), 롤러 마모(Roller Wear), 제작 공차(Manufacturing Tolerance), 적재 하중 변화(Payload Variation)는 이러한 진동을 더욱 증폭시킨다.

기계 설계는 첫 번째 진동 저감 방법이다. 고정밀 휠 제작은 롤러 간 형상 오차를 최소화하며, 폴리우레탄(Polyurethane)과 같은 적절한 롤러 재질은 충격을 흡수하면서도 치수 안정성을 유지한다. 또한 차체 강성(Chassis Stiffness)을 최적화하여 구조 공진(Structural Resonance)이 발생하지 않도록 설계한다.

서스펜션(Suspension)도 중요한 역할을 한다. 스프링과 댐퍼(Spring-Damper)를 이용한 패시브 서스펜션은 바닥 요철에서도 지속적인 접지력을 유지하여 충격을 줄인다. 일부 고급 시스템은 각 휠을 독립적으로 지지하여 적재 하중을 균등하게 분산시키고 진동 전달을 줄인다. 이러한 구조는 위치 추정 정확도(Localization Accuracy)도 함께 향상시킨다.

모션 제어(Motion Control) 역시 진동 감소에 크게 기여한다. 가속도 프로파일(Acceleration Profile)은 구조 공진을 피하도록 설계되며, 부드러운 궤적 생성(Smooth Trajectory Generation)은 토크 변화를 최소화한다. 적응형 속도 제어(Adaptive Speed Control)는 진동 수준이 높아지면 자동으로 속도를 낮추며, 피드포워드 보상(Feedforward Compensation)은 순간적인 토크 변화를 줄여 차량의 진동을 감소시킨다.

센서를 이용한 진동 모니터링도 점점 중요해지고 있다. 차체에 장착된 가속도계(Accelerometer)는 운행 중 구조 진동을 지속적으로 측정한다. 주파수 분석(Frequency-domain Analysis)은 롤러 마모, 베어링 열화, 휠 불균형, 바닥 요철을 조기에 발견할 수 있도록 해준다. 머신러닝은 이러한 진동 데이터를 유지보수 이력과 연계하여 예지보전을 수행한다.

클린룸 환경에서는 바닥 특성도 함께 고려되어야 한다. 에폭시 바닥은 높은 평탄도를 제공하지만, 장기간 사용에 따른 마모나 열팽창(Thermal Expansion), 바닥 이음부(Joint) 등도 진동에 영향을 준다. 반도체 장비는 수백 마이크로미터 이하의 반복 정밀도를 요구하기 때문에 작은 바닥 변화도 중요한 요소가 된다. 따라서 최근에는 바닥 지도(Digital Floor Map)에 위치 정보뿐 아니라 진동 특성까지 함께 저장하여 진동이 큰 구간을 우회하는 기술도 적용되고 있다.

미래의 클린룸 AMR는 진동 제어를 지능형 이동 시스템(Intelligent Mobility System)에 통합할 것으로 예상된다. 바닥 상태, 휠 마모, 적재 하중, 차체 응답을 실시간으로 분석하여 적응형 서스펜션(Adaptive Suspension), 가변 속도 계획(Variable Speed Planning), 능동 진동 제어(Active Vibration Compensation), 예지보전(Predictive Maintenance)을 하나의 시스템으로 통합하게 될 것이다. 이러한 기술은 차세대 반도체 공장에서 요구하는 높은 정밀도, 청정도, 운용 신뢰성을 더욱 향상시킬 것으로 기대된다.

## 04 Custom platform narrow-aisle application

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Modern manufacturing facilities and distribution centers increasingly demand autonomous mobile robots capable of operating efficiently within extremely narrow aisles while maintaining high payload capacity, precise positioning, and reliable navigation. Conventional vehicle architectures often struggle in such environments because steering maneuvers require additional clearance, resulting in inefficient path planning and reduced storage density. Custom omnidirectional mobile platforms, particularly those employing omni wheels or Mecanum wheels, provide an effective solution by enabling unrestricted planar motion without requiring large turning radii. Designing such platforms, however, requires careful consideration of mechanical constraints, wheel selection, payload distribution, localization accuracy, and operational safety.

A narrow-aisle autonomous mobile robot must simultaneously satisfy conflicting design objectives. The platform should be as compact as possible to maximize maneuverability, yet sufficiently rigid to support heavy payloads without excessive structural deformation. Wheelbase dimensions directly influence stability, turning performance, and obstacle clearance. A smaller footprint improves maneuverability but reduces static stability, particularly when transporting elevated or asymmetrically distributed loads. Engineers therefore optimize chassis geometry using finite element analysis and dynamic simulations to achieve an appropriate balance between compactness and mechanical robustness.

Wheel selection plays a decisive role in determining overall system performance. Mecanum wheels provide excellent multidirectional mobility but introduce additional vibration due to periodic roller transitions. Conventional omni wheels generally produce smoother motion under certain operating conditions but may provide lower lateral force capability depending on roller geometry. Wheel diameter influences obstacle traversal, rolling resistance, and achievable vehicle speed, while roller material determines traction, wear characteristics, particle generation, and vibration transmission. Polyurethane rollers often represent the preferred compromise for indoor industrial applications because they combine low floor damage, good wear resistance, and effective vibration damping.

Localization becomes increasingly challenging within narrow aisles because surrounding structures may partially occlude environmental features. Multi-sensor localization therefore combines wheel odometry, inertial measurement units, two-dimensional or three-dimensional LiDAR, cameras, and artificial landmarks to maintain accurate positioning. Navigation software continuously evaluates obstacle clearance while generating smooth trajectories that minimize unnecessary steering corrections. Real-time sensor fusion compensates for wheel slip, encoder error, and temporary sensor degradation, ensuring reliable autonomous operation even within densely populated warehouse environments.

Payload configuration strongly affects vehicle dynamics. Heavy loads raise the center of gravity and increase wheel contact forces, thereby influencing traction, suspension behavior, braking performance, and structural deformation. Mechanical designers therefore position batteries, computing hardware, and payload interfaces strategically to maintain balanced weight distribution. Dynamic load transfer during acceleration, deceleration, and lateral translation must also be considered because uneven wheel loading can reduce localization accuracy and increase roller wear.

Operational safety remains a primary design objective. Laser safety scanners, depth cameras, ultrasonic sensors, emergency stop systems, and functional safety controllers continuously monitor surrounding personnel and obstacles. Speed adaptation algorithms reduce vehicle velocity automatically when aisle width decreases or pedestrian activity increases. Fleet management software further coordinates multiple robots operating simultaneously within shared narrow corridors, preventing congestion and optimizing transportation efficiency.

The development of custom narrow-aisle platforms increasingly incorporates digital engineering methodologies. Digital twins simulate traffic flow, wheel loading, localization accuracy, battery consumption, and vibration characteristics before physical prototypes are constructed. Artificial intelligence analyzes operational data collected during field trials to optimize routing strategies, maintenance intervals, and motion control parameters. Consequently, modern custom omnidirectional platforms achieve higher productivity, improved reliability, and lower lifecycle cost than earlier generations while operating safely within increasingly compact industrial environments.

---

### 4.1 Design Constraints and Wheel Selection Process

---

### 4.2 Performance KPIs and Lessons Learned

---

현대의 제조 공장(Manufacturing Facility)과 물류센터(Distribution Center)는 매우 좁은 통로(Narrow Aisle)에서도 높은 적재 능력(Payload Capacity), 정밀한 위치 결정(Precision Positioning), 안정적인 자율주행(Reliable Navigation)을 유지할 수 있는 자율이동로봇(AMR, Autonomous Mobile Robot)을 요구하고 있다. 기존의 조향 방식 차량은 회전을 위해 충분한 공간이 필요하기 때문에 협소한 환경에서는 이동 효율이 떨어지고 저장 밀도(Storage Density)도 제한된다. 이에 비해 옴니 휠(Omni Wheel)이나 메카넘 휠(Mecanum Wheel)을 사용하는 전방향 이동 플랫폼(Omnidirectional Mobile Platform)은 큰 회전 반경 없이 자유로운 평면 이동(Planar Motion)이 가능하므로 이러한 문제를 효과적으로 해결할 수 있다. 그러나 이러한 플랫폼을 설계하기 위해서는 기계적 제약(Mechanical Constraints), 휠 선정(Wheel Selection), 적재 하중 분배(Payload Distribution), 위치 추정(Localization Accuracy), 운용 안전성(Operational Safety) 등을 종합적으로 고려해야 한다.

협소 통로용 AMR는 서로 상충되는 여러 설계 목표를 동시에 만족해야 한다. 플랫폼은 최대한 작아야 높은 기동성(Maneuverability)을 확보할 수 있지만, 동시에 무거운 적재물을 운반하기 위해 충분한 구조 강성(Structural Rigidity)을 가져야 한다. 휠베이스(Wheelbase)는 안정성(Stability), 회전 성능(Turning Performance), 장애물 통과 성능(Obstacle Clearance)에 직접적인 영향을 준다. 차체 크기를 줄이면 기동성은 향상되지만 높은 적재물이나 편심 하중(Asymmetric Load)을 운반할 때는 정적 안정성(Static Stability)이 감소할 수 있다. 따라서 설계자는 유한요소해석(FEA, Finite Element Analysis)과 동적 시뮬레이션(Dynamic Simulation)을 활용하여 차체 크기와 구조적 강성 사이의 최적 균형을 찾는다.

휠 선정은 전체 시스템 성능을 결정하는 핵심 요소이다. 메카넘 휠은 뛰어난 전방향 이동성을 제공하지만 롤러 전환(Roller Transition) 때문에 진동이 증가한다. 일반적인 옴니 휠은 일부 조건에서 더욱 부드러운 주행이 가능하지만 롤러 구조에 따라 횡방향 추진력이 다소 낮을 수 있다. 휠 직경(Wheel Diameter)은 장애물 통과 능력, 구름 저항(Rolling Resistance), 최고 속도(Maximum Speed)에 영향을 미치며, 롤러 재질(Roller Material)은 접지력(Traction), 내마모성(Wear Resistance), 파티클 발생(Particle Generation), 진동 전달(Vibration Transmission)에 영향을 준다. 실내 산업 환경에서는 폴리우레탄(Polyurethane) 롤러가 바닥 손상을 줄이고 진동 감쇠 능력이 우수하여 가장 많이 사용된다.

협소 통로에서는 위치 추정도 더욱 어려워진다. 주변 구조물이 LiDAR나 카메라의 시야를 부분적으로 가릴 수 있기 때문이다. 따라서 엔코더(Encoder), IMU(Inertial Measurement Unit), 2D·3D LiDAR, 카메라(Camera), 인공 기준점(Artificial Landmark)을 동시에 사용하는 다중 센서 위치 추정(Multi-sensor Localization)이 적용된다. 자율주행 소프트웨어는 장애물과의 여유 공간(Clearance)을 지속적으로 계산하면서 불필요한 조향을 줄이는 부드러운 경로(Smooth Trajectory)를 생성한다. 센서 융합(Sensor Fusion)은 휠 슬립(Wheel Slip), 엔코더 오차, 센서 성능 저하를 실시간으로 보정하여 협소한 공간에서도 안정적인 자율주행을 유지한다.

적재 하중(Payload)은 차량 동역학(Vehicle Dynamics)에 큰 영향을 준다. 무거운 하중은 무게중심(Center of Gravity)을 높이고 휠 접지력을 변화시키며, 제동 성능(Braking Performance), 서스펜션 거동(Suspension Behavior), 구조 변형(Structural Deformation)에 영향을 준다. 따라서 배터리(Battery), 산업용 컴퓨터(Industrial Computer), 적재 인터페이스(Payload Interface)는 균형 잡힌 하중 분포를 유지하도록 배치된다. 또한 가속, 감속, 측면 이동 시 발생하는 동적 하중 이동(Dynamic Load Transfer)도 고려해야 하며, 그렇지 않으면 위치 추정 오차와 롤러 마모가 증가할 수 있다.

운용 안전성은 가장 중요한 설계 목표 가운데 하나이다. 레이저 안전 스캐너(Laser Safety Scanner), 깊이 카메라(Depth Camera), 초음파 센서(Ultrasonic Sensor), 비상 정지(Emergency Stop), 기능 안전 제어기(Functional Safety Controller)는 주변 사람과 장애물을 지속적으로 감시한다. 통로가 좁아지거나 작업자가 가까워지면 속도를 자동으로 감소시키는 속도 적응 알고리즘(Speed Adaptation Algorithm)이 적용된다. 플릿 관리(Fleet Management)는 여러 대의 로봇이 동시에 협소한 통로를 사용하는 경우 교통 혼잡(Congestion)을 방지하고 전체 물류 효율을 향상시킨다.

최근에는 디지털 엔지니어링(Digital Engineering)이 이러한 플랫폼 개발의 핵심이 되고 있다. 디지털 트윈(Digital Twin)은 실제 시제품을 제작하기 전에 교통 흐름(Traffic Flow), 휠 하중(Wheel Loading), 위치 정확도(Localization Accuracy), 배터리 소비(Battery Consumption), 진동 특성(Vibration Characteristics)을 시뮬레이션한다. 이후 실제 운행 데이터(Field Trial Data)는 인공지능(AI)에 의해 분석되어 경로 계획(Routing Strategy), 유지보수(Maintenance Interval), 모션 제어(Motion Control)를 지속적으로 개선한다. 이러한 접근 방식은 협소 통로용 맞춤형 플랫폼이 더 높은 생산성(Productivity), 신뢰성(Reliability), 경제성(Lifecycle Cost)을 달성하도록 한다.

### 4.1 설계 제약 조건과 휠 선정 과정 (Design Constraints and Wheel Selection Process)

---

협소 통로용 전방향 이동 AMR를 설계하는 첫 번째 단계는 플랫폼 전체 구조를 결정하는 핵심 설계 제약 조건을 정의하는 것이다. 일반적인 개방 공간(Open Space)에서 사용하는 이동 로봇과 달리, 협소 통로용 로봇은 차량보다 불과 몇 센티미터 넓은 공간에서 운행하는 경우가 많다. 따라서 기계(Mechanics), 전기(Electrical), 제어(Control) 시스템 모두가 이동성(Mobility), 적재 능력(Payload), 안정성(Stability), 정밀도(Precision), 안전성(Safety)을 동시에 만족하도록 최적화되어야 한다.

가장 먼저 고려해야 할 요소는 차량 크기(Vehicle Dimensions)이다. 차량 폭(Maximum Platform Width)은 통로 폭(Aisle Width)과 안전 여유 공간(Safety Clearance)에 의해 결정된다. 설계자는 위치 추정 오차(Localization Uncertainty), 제작 공차(Manufacturing Tolerance), 휠 변형(Wheel Deformation), 장애물 회피(Obstacle Avoidance)를 고려하여 추가적인 여유 공간을 확보한다. 차량 길이(Vehicle Length)는 적재물 형상(Payload Geometry), 휠베이스 안정성(Wheelbase Stability), 이동 성능을 함께 고려하여 결정된다. 전방향 이동은 회전 반경 제약을 제거하지만, 지나치게 긴 차체는 대각선 이동 시 충돌 위험을 증가시킬 수 있다.

적재 능력은 구조 설계의 기본 기준이 된다. 정적 적재 능력(Static Payload Capacity)은 차체 강도(Chassis Strength), 휠 하중(Wheel Load Rating), 베어링(Bearing), 차축(Axle), 서스펜션(Suspension)의 크기를 결정한다. 또한 동적 하중(Dynamic Payload)은 제동 성능, 가속 한계, 구조 피로(Fatigue)에 영향을 준다. 유한요소해석은 최대 적재 조건에서 응력 분포를 분석하고 불필요한 중량을 줄이는 데 활용된다.

휠 선정은 설계 과정에서 가장 중요한 단계 가운데 하나이다. 메카넘 휠은 뛰어난 전방향 이동을 제공하지만 롤러 접촉으로 인한 진동이 증가한다. 옴니 휠은 일부 응용에서는 더 부드러운 움직임을 제공하지만 힘 전달 특성이 다를 수 있다. 설계자는 휠 직경(Wheel Diameter), 롤러 각도(Roller Angle), 롤러 경도(Roller Hardness), 적재 용량(Load Capacity), 베어링 품질(Bearing Quality), 제조 정밀도(Manufacturing Precision)를 종합적으로 비교한다. 큰 휠은 장애물 통과 능력이 우수하지만 차체 높이와 회전 관성(Rotational Inertia)이 증가하며, 작은 휠은 차체를 낮출 수 있지만 바닥 요철에 더욱 민감하다.

바닥 환경(Floor Condition)도 휠 선택에 중요한 영향을 준다. 반도체 공장의 에폭시 바닥은 파티클 발생이 적고 진동 감쇠 성능이 우수한 폴리우레탄 롤러가 적합하다. 창고의 콘크리트 바닥은 높은 내마모성과 큰 적재 능력이 요구된다. 또한 화학적 내성(Chemical Compatibility), 정전기 방전(ESD, Electrostatic Discharge), 클린룸 인증(Cleanroom Certification), 환경 내구성(Environmental Durability)도 응용 분야에 따라 고려해야 한다.

휠이 결정되면 구동 시스템(Drive System)을 설계한다. 모터 토크(Motor Torque), 감속비(Reduction Ratio), 엔코더 분해능(Encoder Resolution), 서보 대역폭(Servo Bandwidth)은 가속 성능, 위치 정밀도, 연속 운전을 만족해야 한다. 각 휠은 독립적인 서보 제어를 수행하며, EtherCAT이나 CANopen과 같은 산업용 통신은 위치 추정, 안전 제어, 자율주행과 동기화된다.

마지막 단계는 설계 검증(Design Validation)이다. 디지털 트윈은 휠 하중, 진동, 위치 정밀도, 에너지 소비를 미리 예측한다. 이후 실제 프로토타입을 이용한 시험을 통해 예측 결과를 검증하고, 휠 선택, 서스펜션, 위치 추정 알고리즘, 제어기를 반복적으로 개선한다. 이러한 체계적인 설계 과정을 통해 협소 통로에 최적화된 AMR가 완성된다.

### 4.2 성능 KPI와 개발 과정에서 얻은 교훈 (Performance KPIs and Lessons Learned)

협소 통로용 맞춤형 전방향 이동 AMR의 성능은 정량적인 핵심 성능 지표(KPI, Key Performance Indicator)를 이용하여 평가해야 한다. KPI는 서로 다른 플랫폼을 객관적으로 비교하고 성능 한계를 분석하며 차세대 플랫폼을 지속적으로 개선하는 기준이 된다.

이동 성능(Mobility Performance)은 가장 기본적인 평가 항목이다. 최대 전진 속도(Maximum Forward Velocity), 측면 속도(Lateral Velocity), 회전 속도(Rotational Velocity), 가속 성능(Acceleration), 제동 거리(Braking Distance), 최소 통과 폭(Minimum Operating Clearance), 도킹 시간(Docking Time) 등이 대표적인 KPI이다. 협소 통로에서는 특히 측면 이동 정확도(Lateral Positioning Accuracy)가 매우 중요하며, 이는 팔레트 취급과 장비 도킹의 핵심 성능이 된다.

위치 정확도(Positioning Accuracy)와 반복 정밀도(Repeatability)도 매우 중요한 평가 요소이다. 절대 위치 오차(Absolute Localization Error)는 공장 전체에서의 위치 정확도를 나타내며, 반복 정밀도는 동일한 위치에서 반복 작업을 수행할 때의 일관성을 나타낸다. 산업 현장에서는 절대 위치보다 반복 정밀도가 더욱 중요한 경우가 많다. 또한 휠 슬립, 바닥 요철, 센서 가림(Sensor Occlusion), 이동 장애물 환경에서도 위치 추정이 얼마나 안정적으로 유지되는지(Localization Robustness)도 중요한 KPI이다.

기계적 신뢰성(Mechanical Reliability)은 진동 수준(Vibration Level), 휠 마모(Wheel Wear), 베어링 수명(Bearing Lifetime), 구동 효율(Drivetrain Efficiency), 구조 피로(Structural Fatigue), 유지보수 주기(Maintenance Frequency)를 통해 평가된다. 가속도계는 차체 진동을 측정하고, 롤러 마모는 누적 운행 거리에 따라 기록된다. 모터 전류(Motor Current), 베어링 온도(Bearing Temperature), 감속기 효율(Gearbox Efficiency), 에너지 소비(Energy Consumption)는 구동계의 건강 상태를 나타내며, 최근에는 이러한 데이터를 하나의 건강 지수(Health Index)로 통합하여 예지보전에 활용한다.

운용 생산성(Operational Productivity)도 핵심 KPI이다. 작업 완료 시간(Mission Completion Time), 시간당 운송량(Transportation Throughput), 플릿 활용률(Fleet Utilization), 배터리 지속 시간(Battery Endurance), 충전 효율(Charging Efficiency), 교통 혼잡(Congestion), 비상 상황에서의 자율 복구(Autonomous Recovery) 등이 생산성을 결정한다. 플릿 관리 시스템은 이러한 데이터를 지속적으로 분석하여 작업 배분(Task Allocation)과 경로 계획(Route Planning)을 최적화하며, AI는 반복적으로 발생하는 비효율을 찾아 더욱 효율적인 운영 전략을 제안한다.

안전성(Safety Performance) 역시 반드시 정량적으로 평가해야 한다. 장애물 검출 정확도(Obstacle Detection Reliability), 비상 정지 거리(Emergency Stopping Distance), 안전 스캐너 감시 범위(Safety Scanner Coverage), 충돌 회피 성공률(Collision Avoidance Success Rate), 기능 안전 진단(Function Safety Diagnostics)이 대표적인 KPI이다. 특히 협소 통로에서는 작업자와 로봇이 같은 공간을 공유하기 때문에 인간-로봇 협업(Human-Robot Interaction)에 대한 평가가 매우 중요하다.

실제 개발 과정에서는 몇 가지 중요한 교훈이 반복적으로 확인되었다. 첫째, **휠 선정(Wheel Selection)은 진동, 위치 추정, 유지보수, 에너지 소비, 적재 능력 등 거의 모든 성능에 영향을 미치는 가장 중요한 요소**이다. 둘째, **위치 추정의 안정성은 개별 센서보다 센서 융합(Sensor Fusion)의 품질에 더 크게 좌우된다.** 셋째, **차체 강성(Chassis Stiffness)과 하중 분포(Weight Distribution)는 특히 고하중 운반 시 반복 정밀도에 결정적인 영향을 미친다.** 넷째, **예지보전(Predictive Maintenance)은 성능이 저하되기 전에 부품 열화를 발견하여 생애주기 비용(Lifecycle Cost)을 크게 절감한다.** 마지막으로 **디지털 트윈(Digital Twin)과 실제 현장 검증(Field Validation)을 결합한 개발 방법은 기계 설계, 자율주행 알고리즘, 운영 전략을 가장 효율적으로 최적화할 수 있는 방법**임이 확인되었다.

이러한 경험은 협소 통로용 AMR의 성공이 하나의 기술만을 최적화해서 이루어지는 것이 아니라, **기계(Mechanics), 제어(Control), 센서(Sensing), 소프트웨어(Software), 안전(Safety), 경제성(Operational Economics)**을 하나의 통합 시스템으로 설계해야 가능하다는 점을 보여준다. 앞으로 제조 산업이 더욱 유연한 생산 시스템(Flexible Manufacturing System)으로 발전함에 따라, KPI 기반 설계(KPI-driven Design Methodology)는 차세대 고성능 전방향 이동 AMR 개발의 핵심 방법론으로 계속 활용될 것이다.

## 05 Hills Robotics omni drive evaluation

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

The development of an omnidirectional mobile robot requires significantly more than selecting a wheel type or integrating a holonomic drive controller. A successful industrial platform must satisfy mechanical robustness, localization accuracy, payload capability, safety compliance, lifecycle cost, maintainability, and long-term operational reliability simultaneously. During the development of the Hills Robotics omnidirectional platform, extensive engineering evaluations were performed to determine whether an omni-drive architecture could satisfy the diverse operational requirements expected from next-generation autonomous mobile robots. These evaluations were not limited to laboratory demonstrations but were intended to support future deployment in semiconductor manufacturing, precision logistics, collaborative production, intelligent warehouses, healthcare facilities, and autonomous industrial inspection.

The evaluation process adopted a complete systems engineering methodology. Rather than analyzing individual components independently, the mechanical structure, wheel configuration, drive system, localization algorithms, perception sensors, navigation software, fleet management, and operational safety were assessed as one integrated robotic platform. Digital simulations using multi-body dynamics, finite element structural analysis, and thermal analysis were combined with prototype testing to validate engineering assumptions before hardware optimization. This approach reduced development risk while allowing multiple design alternatives to be compared objectively using quantitative performance indicators.

Mechanical performance represented one of the primary evaluation categories. Various chassis geometries, wheelbase dimensions, suspension configurations, and payload distributions were investigated to determine their influence on structural rigidity, wheel-ground contact stability, vibration transmission, and overall vehicle durability. Special attention was given to maintaining equal wheel loading because uneven load distribution directly affects localization accuracy, wheel wear, and motion repeatability. Lightweight yet rigid aluminum structures combined with modular payload interfaces were selected to maximize both flexibility and structural performance while simplifying future product customization.

Motion performance was evaluated under representative industrial operating conditions. Forward motion, lateral translation, diagonal movement, rotational maneuvers, obstacle avoidance, narrow-aisle navigation, and precision docking were repeatedly tested using multiple payload conditions. Omnidirectional mobility demonstrated substantial productivity advantages within confined industrial environments because lateral positioning eliminated unnecessary steering maneuvers. Docking operations required significantly less time than conventional steering vehicles while maintaining highly repeatable positioning performance suitable for automated manufacturing applications.

Localization accuracy formed another major evaluation objective. Wheel encoder odometry, inertial measurement units, LiDAR-based localization, visual fiducial markers, and sensor fusion algorithms were integrated into a hierarchical positioning framework. Experimental measurements confirmed that localization performance depended not only upon sensor quality but also upon chassis stiffness, wheel contact consistency, vibration levels, and floor conditions. Continuous wheel-ground contact provided by optimized suspension systems significantly improved localization repeatability while reducing accumulated odometry drift.

Operational economics were evaluated from a lifecycle perspective rather than considering only initial hardware cost. Wheel maintenance intervals, roller replacement frequency, bearing lifetime, energy consumption, spare parts inventory, service accessibility, software maintainability, and fleet scalability were all included in the assessment. Predictive maintenance supported by onboard diagnostics and cloud-based analytics demonstrated considerable potential for reducing unexpected downtime and extending component lifetime. Consequently, lifecycle cost analysis became an essential decision criterion alongside technical performance.

Throughout the evaluation process, several practical engineering lessons emerged. Omnidirectional mobility provided outstanding maneuverability and productivity inside structured indoor environments but required careful consideration of floor quality, vibration control, and wheel maintenance. High-quality localization depended upon integrated mechanical and software optimization rather than isolated sensor improvements. Digital twin simulation proved extremely valuable for reducing prototype iterations, while modular system architecture significantly simplified future product expansion. These findings established a strong engineering foundation for selecting appropriate drive architectures across different Hills Robotics product families.

Ultimately, the evaluation demonstrated that no single drive technology represents the optimal solution for every industrial application. Instead, drive architecture should always be selected according to operational requirements including payload, operating environment, positioning precision, maintenance strategy, infrastructure constraints, and total cost of ownership. This philosophy has become one of the core engineering principles guiding future autonomous mobile robot development within Hills Robotics.

---

### 5.1 Evaluation Criteria and Test Results

---

### 5.2 Decision Rationale vs Steer Drive Adoption

---

전방향 이동 로봇(Omnidirectional Mobile Robot)의 개발은 단순히 휠 종류(Wheel Type)를 선택하거나 전방향 구동 제어기(Holonomic Drive Controller)를 적용하는 것만으로 완성되지 않는다. 실제 산업용 플랫폼은 기계적 강성(Mechanical Robustness), 위치 추정 정확도(Localization Accuracy), 적재 능력(Payload Capability), 안전 규격 준수(Safety Compliance), 생애주기 비용(Lifecycle Cost), 유지보수성(Maintainability), 장기적인 운용 신뢰성(Long-term Operational Reliability)을 동시에 만족해야 한다. Hills Robotics는 차세대 자율이동로봇(AMR)을 개발하는 과정에서 전방향 구동(Omni Drive) 아키텍처가 이러한 다양한 산업 요구사항을 충족할 수 있는지를 검증하기 위해 매우 광범위한 엔지니어링 평가를 수행하였다. 이 평가는 단순한 연구실 수준의 성능 검증이 아니라 반도체 제조(Semiconductor Manufacturing), 정밀 물류(Precision Logistics), 협업 생산(Collaborative Manufacturing), 스마트 창고(Intelligent Warehouse), 의료 시설(Healthcare Facility), 산업용 자율 검사(Industrial Inspection)까지 고려한 실제 산업 적용을 목표로 수행되었다.

평가 과정은 시스템 엔지니어링(Systems Engineering) 방법론을 기반으로 진행되었다. 기계 구조(Mechanical Structure), 휠 구성(Wheel Configuration), 구동 시스템(Drive System), 위치 추정 알고리즘(Localization Algorithm), 인식 센서(Perception Sensor), 자율주행 소프트웨어(Navigation Software), 플릿 관리(Fleet Management), 안전 시스템(Operational Safety)을 각각 개별적으로 평가하지 않고 하나의 통합된 로봇 플랫폼으로 분석하였다. 또한 다물체 동역학(Multi-body Dynamics), 유한요소 구조해석(Finite Element Analysis), 열 해석(Thermal Analysis)을 포함한 디지털 시뮬레이션과 실제 시제품 평가를 병행하여 설계 가정을 검증하였다. 이러한 접근은 개발 위험을 줄이고 다양한 설계 대안을 객관적인 성능 지표를 이용하여 비교할 수 있도록 하였다.

기계적 성능(Mechanical Performance)은 가장 중요한 평가 항목 가운데 하나였다. 다양한 차체 형상(Chassis Geometry), 휠베이스(Wheelbase), 서스펜션(Suspension), 적재 하중 분포(Payload Distribution)를 비교하여 구조 강성(Structural Rigidity), 휠 접지 안정성(Wheel-Ground Contact Stability), 진동 전달(Vibration Transmission), 차량 내구성(Durability)에 미치는 영향을 분석하였다. 특히 네 개의 휠에 동일한 하중이 분배되도록 하는 것이 매우 중요하였다. 하중 불균형은 위치 추정 오차(Localization Error), 휠 마모(Wheel Wear), 반복 정밀도(Motion Repeatability)를 직접적으로 저하시켰기 때문이다. 최종적으로 경량 알루미늄 구조(Lightweight Aluminum Structure)와 모듈형 적재 인터페이스(Modular Payload Interface)를 적용하여 높은 강성과 향후 플랫폼 확장성을 동시에 확보하였다.

주행 성능(Motion Performance)은 실제 산업 환경을 모사한 다양한 조건에서 평가되었다. 전진(Forward Motion), 측면 이동(Lateral Translation), 대각선 이동(Diagonal Motion), 회전(Rotational Motion), 장애물 회피(Obstacle Avoidance), 협소 통로 주행(Narrow Aisle Navigation), 정밀 도킹(Precision Docking)을 여러 적재 조건에서 반복적으로 시험하였다. 그 결과 전방향 이동은 협소한 실내 환경에서 매우 큰 생산성 향상을 제공하였다. 특히 측면 이동을 이용한 도킹은 조향 구동(Steer Drive)에 비해 불필요한 방향 전환이 없어 훨씬 빠른 작업 수행과 높은 반복 정밀도를 제공하였다.

위치 추정(Localization Accuracy)은 또 하나의 핵심 평가 항목이었다. 휠 엔코더 오도메트리(Wheel Encoder Odometry), IMU(Inertial Measurement Unit), LiDAR 기반 위치 추정(LiDAR Localization), 비전 마커(Visual Fiducial Marker), 센서 융합(Sensor Fusion)을 계층형 위치 추정(Hierarchical Positioning Framework)으로 통합하였다. 실험 결과는 위치 추정 성능이 센서의 성능뿐 아니라 차체 강성, 휠 접지력, 진동 수준, 바닥 상태에도 크게 영향을 받는다는 사실을 보여주었다. 최적화된 서스펜션은 지속적인 접지력을 유지하여 오도메트리 누적 오차를 감소시키고 반복 정밀도를 크게 향상시켰다.

경제성(Economics)은 초기 구매 비용이 아니라 생애주기 비용(Lifecycle Cost) 관점에서 평가하였다. 휠 교체 주기(Wheel Maintenance Interval), 롤러 교체(Roller Replacement), 베어링 수명(Bearing Lifetime), 에너지 소비(Energy Consumption), 예비 부품 관리(Spare Parts Inventory), 유지보수 접근성(Service Accessibility), 소프트웨어 유지관리성(Software Maintainability), 플릿 확장성(Fleet Scalability)을 모두 포함하였다. 또한 온보드 진단(Onboard Diagnostics)과 클라우드 분석(Cloud Analytics)을 이용한 예지보전(Predictive Maintenance)은 계획되지 않은 다운타임을 크게 줄이고 부품 수명을 연장하는 효과를 확인하였다. 따라서 생애주기 비용은 기술 성능과 함께 핵심 의사결정 요소가 되었다.

평가 과정에서는 여러 중요한 엔지니어링 교훈도 도출되었다. 전방향 이동은 구조화된 실내 환경에서 매우 뛰어난 기동성과 생산성을 제공하지만, 바닥 품질(Floor Quality), 진동 제어(Vibration Control), 롤러 유지보수(Roller Maintenance)를 충분히 고려해야 한다는 점이 확인되었다. 또한 고품질 위치 추정은 단순히 센서를 고성능으로 교체하는 것이 아니라 기계 구조와 소프트웨어를 함께 최적화해야 가능하다는 점도 확인되었다. 디지털 트윈은 시제품 제작 횟수를 줄이는 데 매우 효과적이었으며, 모듈형 아키텍처는 향후 제품군 확장(Product Family Expansion)에 큰 장점을 제공하였다. 이러한 결과는 Hills Robotics의 다양한 AMR 제품군에 적합한 구동 방식을 선택하는 중요한 기술적 기반이 되었다.

최종적으로 이번 평가는 **모든 산업 환경에서 하나의 구동 방식이 최적일 수는 없으며**, 적재 하중, 운용 환경, 위치 정밀도, 유지보수 전략, 설치 환경, 총소유비용(TCO, Total Cost of Ownership)을 종합적으로 고려하여 구동 방식을 선택해야 한다는 결론을 도출하였다. 이러한 철학은 앞으로 Hills Robotics의 차세대 자율이동로봇 개발에서 가장 중요한 설계 원칙 가운데 하나가 될 것이다.

### 5.1 평가 기준과 시험 결과 (Evaluation Criteria and Test Results)

---

Hills Robotics 전방향 이동 플랫폼의 평가는 주관적인 운용 경험이 아니라 **정량적인 성능 지표(Measurable Performance Criteria)**를 기반으로 수행되었다. 모든 하위 시스템은 반복 가능한 실험실 시험(Laboratory Experiment), 시뮬레이션(Simulation Analysis), 실제 산업 환경 시험(Industrial Operating Scenario)을 통해 평가되었다. 목적은 단순한 기능 검증이 아니라 다양한 산업 분야에서 장기간 운용 가능한 플랫폼인지를 확인하는 것이었다.

기계적 평가는 구조 강성(Structural Rigidity), 휠 하중 분포(Wheel Load Distribution), 서스펜션 성능(Suspension Performance), 진동 특성(Vibration Characteristics)을 중심으로 수행되었다. 유한요소해석은 최대 적재 조건에서 차체 변형을 예측하였으며, 실제 스트레인 게이지(Strain Gauge)를 이용한 계측으로 시뮬레이션 결과를 검증하였다. 특히 네 개의 휠에 균일한 하중이 분배되는 것이 매우 중요하였으며, 작은 하중 편차도 위치 오차와 휠 마모를 증가시키는 것으로 확인되었다. 최적화된 차체 보강 구조는 차량 중량을 크게 증가시키지 않으면서 구조 변형을 최소화하였다.

주행 성능은 최고 속도(Maximum Forward Speed), 측면 이동 정확도(Lateral Translation Accuracy), 대각선 이동(Diagonal Motion), 회전 성능(Rotational Maneuverability), 가속 성능(Acceleration), 제동 거리(Braking Distance), 최소 통과 폭(Minimum Turning Clearance)을 기준으로 평가되었다. 특히 협소 통로 도킹 시험(Narrow Aisle Docking Test)은 전방향 이동의 가장 큰 장점을 보여주었다. 측면 이동을 활용함으로써 조향 구동 차량에서 필요한 방향 수정이나 반복적인 조향 동작 없이 빠르고 정확한 도킹이 가능하였다.

위치 추정 평가는 엔코더 오도메트리, IMU, LiDAR 위치 추정, 비전 마커를 함께 사용하였다. 에폭시 바닥(Epoxy Floor), 코팅 콘크리트(Coated Concrete), 일반 산업용 바닥(Warehouse Floor) 등 다양한 환경에서 반복 시험을 수행하였다. 시험 결과 위치 추정의 반복 정밀도는 센서 자체의 성능보다 **휠 접지력(Wheel-Ground Contact)**과 **진동 억제(Vibration Suppression)**에 더욱 크게 영향을 받는 것으로 확인되었다. 최적화된 서스펜션은 접지력을 일정하게 유지하여 장거리 주행에서도 누적 위치 오차를 크게 감소시켰다.

적재 성능은 정적 하중(Static Payload)과 동적 하중(Dynamic Payload)을 모두 평가하였다. 무게중심이 설계 범위 내에 있는 경우 차량 안정성은 매우 우수하였다. 그러나 적재물이 높아질 경우 급가속과 급제동에서 차체 롤(Body Roll)이 증가하고 일부 휠의 접지력이 감소하였다. 따라서 적재 위치와 데크 구조(Payload Deck Design)가 매우 중요한 요소임이 확인되었다. 또한 모듈형 적재 인터페이스는 다양한 산업 장비를 쉽게 장착하면서도 균형 잡힌 하중 분포를 유지할 수 있도록 하였다.

신뢰성 평가는 장시간 내구 시험(Endurance Test), 휠 마모(Wheel Wear), 베어링 온도(Bearing Temperature), 모터 전류(Motor Current), 배터리 충방전(Battery Cycling), 환경 스트레스(Environmental Stress)를 중심으로 수행되었다. 가속 수명 시험(Accelerated Lifecycle Test)은 진동 분석과 모터 진단을 이용한 예지보전이 실제 고장 발생 이전에 부품 열화를 감지할 수 있음을 보여주었다. 이는 예기치 않은 유지보수를 줄이고 플릿 가동률(Fleet Availability)을 크게 향상시키는 결과를 가져왔다.

소프트웨어 평가는 자율주행 안정성(Autonomous Navigation Robustness), 장애물 회피(Obstacle Avoidance), 플릿 협업(Fleet Coordination), 위치 추정 복구(Localization Recovery), 통신 신뢰성(Communication Reliability), 작업 수행(Mission Execution)을 대상으로 수행되었다. AI 기반 진단은 이상 운행 패턴을 자동으로 탐지하였으며, 클라우드 기반 데이터 분석은 유지보수 일정과 플릿 운영 전략을 최적화하였다. 또한 디지털 트윈은 실제 시험 결과와 매우 높은 일치도를 보여 향후 플랫폼 개발의 신뢰성을 크게 향상시켰다.

종합적으로 시험 결과는 전방향 이동 플랫폼이 **뛰어난 기동성(Excellent Maneuverability)**, **높은 도킹 반복 정밀도(Highly Repeatable Docking)**, **유연한 적재 인터페이스(Flexible Payload Integration)**, **안정적인 자율주행(Reliable Autonomous Navigation)**을 제공함을 확인하였다. 반면 바닥 품질, 진동 관리, 롤러 유지보수, 고하중 운반은 지속적으로 고려해야 할 중요한 설계 요소로 확인되었다.

### 5.2 조향 구동 채택과의 비교 및 의사결정 근거 (Decision Rationale vs Steer Drive Adoption)

종합적인 엔지니어링 평가를 수행한 결과, Hills Robotics는 **전방향 구동(Omnidirectional Drive)**과 **조향 구동(Steer Drive)** 가운데 어느 하나가 모든 산업 환경에서 절대적으로 우수한 방식은 아니라는 결론을 내렸다. 두 구동 방식은 각각 서로 다른 장점을 가지고 있으며, 적용 분야에 따라 최적의 선택이 달라진다. 따라서 Hills Robotics는 모든 제품에 하나의 구동 방식을 적용하는 것이 아니라 **응용 분야(Application-oriented Drive Selection)**에 따라 적합한 구동 방식을 선택하는 전략을 채택하였다.

전방향 구동은 구조화된 실내 환경에서 매우 뛰어난 성능을 보였다. 반도체 공장, 전자 제조, 연구실 자동화, 병원 물류, 협업 생산, 정밀 조립과 같이 **좁은 공간에서 반복적인 도킹과 측면 이동이 필요한 환경**에서는 매우 큰 생산성 향상을 제공하였다. 측면 이동은 불필요한 조향을 제거하여 작업 시간을 단축하고 생산 설비와의 정렬을 매우 효율적으로 수행하였다.

그러나 평가 과정에서는 몇 가지 한계도 확인되었다. 옴니 휠과 메카넘 휠은 패시브 롤러의 반복적인 접촉 때문에 속도가 증가할수록 진동이 증가하였다. 또한 바닥 상태는 위치 정확도, 승차감, 유지보수 비용에 매우 큰 영향을 주었다. 롤러와 베어링은 지속적인 반복 하중을 받기 때문에 유지보수 빈도도 증가하였다. 고하중 환경에서는 이러한 특성이 더욱 크게 나타났으며, 접촉 응력과 구조 하중도 함께 증가하였다.

반면 조향 구동은 전혀 다른 특성을 보여주었다. 일반 산업용 타이어는 넓은 접촉면을 가지므로 **접지력(Traction)**이 우수하고, **구름 저항(Rolling Resistance)**이 낮으며, **진동(Vibration)**이 적고, **에너지 효율(Energy Efficiency)**이 높았다. 실외 환경, 거친 콘크리트 바닥, 경사로, 물류 야드, 산업 현장에서는 측면 이동보다 장애물 통과 능력과 내구성이 더욱 중요하기 때문에 조향 구동이 훨씬 적합하였다. 또한 고하중 운반에서도 구조 강성과 유지보수 측면에서 조향 구동이 더욱 유리하였다.

생애주기 비용 분석(Lifecycle Cost Analysis) 역시 이러한 결과를 뒷받침하였다. 전방향 이동은 협소한 실내 환경에서 매우 높은 생산성을 제공하지만, 조향 구동은 유지보수 비용이 낮고 휠 수명이 길며 에너지 소비가 적고 장기적인 신뢰성이 높았다. 따라서 단순한 이동 성능이 아니라 생산성 향상과 유지보수 비용을 함께 고려한 종합적인 경제성 평가가 필요하였다.

이러한 결과를 바탕으로 Hills Robotics는 **이원화 플랫폼 전략(Dual-platform Strategy)**을 수립하였다. 전방향 이동 플랫폼은 **정밀 실내 자동화(Precision Indoor Automation)**, **협소 통로 작업(Narrow Aisle Operation)**, **반복 도킹(Frequent Docking)**과 같은 환경에 적용한다. 반면 조향 구동 플랫폼은 **실외 자율주행(Outdoor Autonomous Vehicles)**, **고하중 물류(Heavy Payload Logistics)**, **농업 로봇(Agricultural Robotics)**, **사회기반시설 점검(Infrastructure Inspection)**, **장거리 이동(Long-distance Navigation)** 등 강인성(Robustness), 효율(Efficiency), 내구성(Durability)이 더욱 중요한 분야에 적용한다.

이러한 의사결정은 Hills Robotics의 핵심 시스템 엔지니어링 철학(Systems Engineering Philosophy)을 잘 보여준다. 즉, 모든 제품에서 가장 높은 기동성을 추구하는 것이 아니라 **기계 성능(Mechanical Performance)**, **위치 추정 안정성(Localization Robustness)**, **생애주기 비용(Lifecycle Cost)**, **안전성(Operational Safety)**, **유지보수성(Maintainability)**, **고객 생산성(Customer Productivity)**을 종합적으로 고려하여 가장 적합한 구동 방식을 선택하는 것이다.

향후에는 인공지능(AI), 디지털 트윈(Digital Twin), 능동 서스펜션(Active Suspension), 적응형 제어(Adaptive Control)가 발전함에 따라 두 구동 방식의 장점을 결합한 새로운 플랫폼이 등장할 가능성도 있다. 그러나 현재 산업 환경에서는 **응용 분야에 최적화된 구동 방식 선택(Application-driven Drivetrain Selection)**이 기술적·경제적으로 가장 합리적인 전략이며, Hills Robotics는 이러한 방향을 기반으로 차세대 산업용 자율이동로봇 플랫폼을 지속적으로 개발해 나갈 계획이다.
