## 01 What Is A Mobile Robot Drive System

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Definition and Role

---

### 1.2 Drive System Component Overview

---

### 1.3 Industrial Requirements

---

### 1.1 정의와 역할 (Definition and Role)

---

모바일 로봇 구동 시스템(Mobile Robot Drive System)은 모바일 로봇의 움직임을 생성하고 제어하기 위한 기계(Mechanical), 전기(Electrical), 전자(Electronic), 소프트웨어(Software) 기술의 통합체이다. 이는 저장된 에너지를 실제 이동 운동으로 변환하는 핵심 시스템으로서, 로봇이 환경 속에서 이동하고, 화물을 운반하며, 작업을 수행하고, 주변 설비와 상호작용할 수 있도록 지원한다. 물류창고(Warehouse), 제조공장(Manufacturing Facility), 병원(Hospital), 공항(Airport), 농업 현장(Agricultural Field), 광산(Mining Site), 실외 자율주행 환경(Outdoor Autonomous Environment) 등 어떠한 환경에서 운영되더라도 구동 시스템은 로봇의 이동성을 제공하는 가장 기본적인 기반 기술이다.

구동 시스템은 자동차의 파워트레인(Powertrain)에 비유할 수 있다. 자동차가 엔진 출력을 바퀴의 회전력으로 변환하여 차량을 움직이는 것처럼, 로봇 구동 시스템은 전기에너지를 기계적 운동으로 변환하여 이동을 가능하게 한다. 그러나 모바일 로봇은 단순한 이동 수단이 아니라 자율성(Autonomy)과 정밀성(Precision)을 요구하기 때문에, 자동차보다 훨씬 높은 수준의 제어 기술과 센서 융합 기술이 필요하다.

구동 시스템의 가장 기본적인 역할은 운동 생성(Motion Generation)이다. 배터리(Battery)에 저장된 전기에너지는 전동기(Electric Motor)에 의해 회전 운동으로 변환되며, 이 회전력은 감속기(Gearbox), 샤프트(Shaft), 바퀴(Wheel), 트랙(Track), 조향 장치(Steering Mechanism) 등을 통해 로봇의 이동력으로 전달된다. 이 과정에서 로봇의 최고 속도(Maximum Speed), 가속도(Acceleration), 제동 성능(Braking Performance), 회전 성능(Turning Performance)이 결정된다.

구동 시스템은 이동뿐만 아니라 자율주행 성능에도 직접적인 영향을 미친다. 상위 제어기(Higher-Level Controller)와 경로 계획기(Path Planner)가 생성한 이동 명령은 구동 시스템에 전달되고, 구동 시스템은 이를 실제 바퀴 속도(Wheel Velocity), 조향각(Steering Angle), 차량 궤적(Vehicle Trajectory)으로 변환한다. 이를 통해 로봇은 목표 지점으로 이동하고, 장애물을 회피하며, 충전 스테이션(Charging Station)에 정밀하게 도킹(Docking)할 수 있다.

또한 구동 시스템은 안정성(Stability)과 기동성(Maneuverability)을 유지하는 역할을 수행한다. 좁은 통로에서 운영되는 실내 자율이동로봇(AMR, Autonomous Mobile Robot)은 작은 회전 반경(Turning Radius)이 중요하지만, 대형 실외 자율주행 플랫폼은 험지 주행 능력(Terrain Mobility)과 적재 안정성(Payload Stability)이 중요하다. 따라서 구동 시스템의 구조는 로봇의 활용 목적에 따라 달라질 수 있다.

구동 시스템은 인지(Perception)와 행동(Action)을 연결하는 실행 계층(Execution Layer)이기도 하다. 라이다(LiDAR), 카메라(Camera), 관성측정장치(IMU, Inertial Measurement Unit), 엔코더(Encoder), GNSS 수신기 등의 센서가 주변 환경과 차량 상태를 측정하면, 제어 소프트웨어(Control Software)는 이를 기반으로 이동 명령을 생성한다. 구동 시스템은 이러한 명령을 실제 물리적 움직임으로 구현하는 최종 실행 장치이다.

안전성(Safety) 또한 매우 중요한 역할이다. 현대의 모바일 로봇은 사람과 같은 공간에서 협업하는 경우가 많기 때문에 비상 정지(Emergency Stop), 속도 제한(Speed Limitation), 충돌 완화(Collision Mitigation), 고장 감지(Fault Detection), 안전 제동(Safe Braking) 기능을 반드시 제공해야 한다. 따라서 구동 시스템은 단순히 움직이는 장치가 아니라 안전한 움직임을 보장하는 시스템이기도 하다.

최근에는 인공지능(AI, Artificial Intelligence), 예지보전(Predictive Maintenance), 상태 모니터링(Health Monitoring), 클라우드 연결성(Cloud Connectivity) 기술이 구동 시스템에 통합되고 있다. 이를 통해 시스템은 자신의 상태를 분석하고 성능을 최적화하며 잠재적인 고장을 사전에 예측할 수 있게 되었다. 결과적으로 현대의 모바일 로봇 구동 시스템은 단순한 모터와 바퀴의 조합이 아니라 지능형 사이버 물리 시스템(Intelligent Cyber-Physical System)으로 진화하고 있다.

### 1.2 구동 시스템 구성 요소 개요 (Drive System Component Overview)

---

모바일 로봇 구동 시스템은 여러 개의 하위 시스템(Sub-System)이 유기적으로 결합되어 구성된다. 이러한 하위 시스템은 전력 공급(Power Delivery), 구동(Actuation), 센싱(Sensing), 제어(Control), 통신(Communication), 소프트웨어(Software) 계층으로 구분할 수 있다. 각 구성 요소는 독립적인 역할을 수행하지만, 모든 요소가 긴밀하게 협력해야 안정적이고 정밀한 이동 성능을 달성할 수 있다.

전원 시스템(Power Subsystem)은 구동 시스템의 에너지 공급원이다. 일반적으로 배터리(Battery), 배터리 관리 시스템(BMS, Battery Management System), 전력 분배 장치(PDU, Power Distribution Unit), 퓨즈(Fuse), 차단기(Circuit Breaker), DC/DC 컨버터(DC/DC Converter)로 구성된다. 최근 산업용 모바일 로봇에서는 리튬이온 배터리(Lithium-Ion Battery)와 리튬인산철 배터리(LFP Battery)가 널리 사용된다. BMS는 전압(Voltage), 전류(Current), 온도(Temperature), 충전 상태(State of Charge)를 실시간으로 감시하여 안전한 운영을 보장한다.

구동 시스템(Actuation Subsystem)은 전기에너지를 실제 운동으로 변환한다. 주요 구성 요소는 모터(Motor), 모터 드라이버(Motor Driver), 감속기(Gearbox), 전달 장치(Transmission), 샤프트(Shaft), 커플링(Coupling), 바퀴(Wheel), 트랙(Track), 조향 장치(Steering Assembly) 등이다. 최근에는 브러시리스 DC 모터(BLDC Motor)가 높은 효율과 긴 수명으로 인해 가장 널리 사용된다. 감속기는 모터의 고속 회전을 저속 고토크 운동으로 변환하여 중량물을 운반할 수 있도록 한다.

센싱 시스템(Sensing Subsystem)은 폐루프 제어(Closed-Loop Control)를 위한 피드백 정보를 제공한다. 엔코더(Encoder)는 바퀴의 회전 위치와 속도를 측정하고, IMU는 가속도(Acceleration), 각속도(Angular Velocity), 자세(Orientation)를 측정한다. 전류 센서(Current Sensor)는 모터 부하 상태를 감시하며, 온도 센서(Temperature Sensor)는 과열 여부를 확인한다. 고급 시스템에서는 토크 센서(Torque Sensor), 힘 센서(Force Sensor), 진동 센서(Vibration Sensor) 등이 추가되어 진단 및 예지보전에 활용된다.

제어 시스템(Control Subsystem)은 구동 시스템의 두뇌 역할을 수행한다. 모터 컨트롤러(Motor Controller), 임베디드 프로세서(Embedded Processor), 실시간 제어기(Real-Time Controller), 안전 제어기(Safety Controller), 모션 제어 소프트웨어(Motion Control Software) 등이 포함된다. 이들은 속도 제어(Velocity Control), 위치 제어(Position Control), 토크 제어(Torque Control)를 수행하며, 다수의 구동 모듈을 통합적으로 관리한다.

통신 시스템(Communication Infrastructure)은 모든 구성 요소를 연결한다. CAN, CAN FD, EtherCAT, Ethernet, RS-485, Serial Interface와 같은 산업용 통신 프로토콜이 널리 사용된다. 실시간 통신(Real-Time Communication)은 정밀한 모션 제어를 위해 필수적이며, 센서와 제어기, 구동기 사이의 데이터를 지연 없이 전달해야 한다.

소프트웨어 계층(Software Layer)은 전체 시스템의 동작을 조율한다. 운동학(Kinematics), 경로 추종(Path Following), 상태 추정(State Estimation), 진단(Diagnostics), 안전 감시(Safety Monitoring) 알고리즘이 이 계층에서 동작한다. 최근에는 ROS 2(Robot Operating System 2)가 이러한 소프트웨어 통합의 표준 플랫폼으로 활용되고 있다.

결국 모바일 로봇 구동 시스템은 센서가 상태를 측정하고, 제어기가 이를 분석하며, 구동기가 실제 운동을 수행하는 폐루프 구조를 형성한다. 이 구조가 지속적으로 반복되면서 로봇은 높은 정밀도와 안정성을 유지할 수 있다.

### 1.3 산업적 요구사항 (Industrial Requirements)

산업용 모바일 로봇은 일반 소비자용 로봇보다 훨씬 더 높은 수준의 성능과 신뢰성을 요구받는다. 따라서 구동 시스템은 단순히 이동 기능만 제공하는 것이 아니라 다양한 산업 환경에서 지속적으로 운영될 수 있는 수준의 품질과 내구성을 확보해야 한다.

가장 중요한 요구사항 중 하나는 정밀도(Accuracy)이다. 자동화 창고(Automated Warehouse), 반도체 공장(Semiconductor Factory), 제조 라인(Manufacturing Line)에서는 로봇이 수 밀리미터(Millimeter) 수준의 오차로 정지해야 하는 경우가 많다. 컨베이어(Conveyor)와의 정렬, 자동 충전 스테이션과의 도킹, 로봇팔(Manipulator) 작업을 위한 위치 맞춤 등에 높은 정밀도가 요구된다. 이를 위해 고해상도 엔코더(High-Resolution Encoder), 정밀 제어 알고리즘(Precision Control Algorithm), 강성 높은 기계 구조(Rigid Mechanical Structure)가 필요하다.

신뢰성(Reliability)은 산업용 로봇에서 가장 중요한 평가 요소 중 하나이다. 많은 공장에서는 로봇이 하루 20시간 이상, 연중무휴로 운영된다. 따라서 구동 시스템은 진동(Vibration), 충격(Shock), 먼지(Dust), 습도(Humidity), 온도 변화(Temperature Variation)와 같은 가혹한 환경을 견딜 수 있어야 한다. MTBF(Mean Time Between Failure)를 높이는 것은 운영 비용 절감의 핵심 요소이다.

안전성(Safety)은 현대 산업용 로봇에서 필수 요구사항이다. 사람과 협업하는 환경에서는 비상 정지(Emergency Stop), 안전 제동(Safe Braking), 속도 감시(Speed Monitoring), 장애 감지(Fault Detection), 기능 안전(Functional Safety)이 필수적으로 구현되어야 한다. ISO 3691-4, ISO 13849, IEC 61508과 같은 국제 표준은 이러한 안전 설계의 기준을 제공한다.

에너지 효율(Energy Efficiency)은 배터리 기반 로봇에서 특히 중요하다. 효율이 높은 모터, 최적화된 감속비(Gear Ratio), 저마찰 구조(Low-Friction Design), 회생 제동(Regenerative Braking)은 배터리 사용 시간을 연장하고 운영 비용을 절감한다. 물류센터와 같은 대규모 운영 환경에서는 이러한 차이가 연간 수천만 원 이상의 비용 차이로 이어질 수 있다.

확장성(Scalability) 역시 제조사 관점에서 매우 중요하다. 동일한 플랫폼을 기반으로 50kg, 100kg, 250kg, 500kg, 1000kg급 로봇을 개발할 수 있다면 개발 비용과 유지보수 비용을 크게 줄일 수 있다. 따라서 모듈형 아키텍처(Modular Architecture)가 산업용 로봇 설계의 핵심 개념으로 자리잡고 있다.

유지보수성(Maintainability)도 중요한 요소이다. 산업 현장에서는 장비를 빠르게 수리하고 복구할 수 있어야 한다. 따라서 구성 요소는 쉽게 접근 가능해야 하며, 진단 기능(Diagnostic Function)과 원격 모니터링(Remote Monitoring) 기능을 제공해야 한다. 최근에는 예지보전(Predictive Maintenance)을 통해 고장이 발생하기 전에 부품을 교체하는 방식이 널리 사용되고 있다.

미래의 구동 시스템은 인공지능(AI), 머신러닝(Machine Learning), 디지털 트윈(Digital Twin), 엣지 컴퓨팅(Edge Computing)과 더욱 긴밀하게 통합될 것으로 예상된다. 이러한 기술은 로봇이 스스로 성능을 최적화하고, 에너지 사용을 줄이며, 잠재적인 문제를 사전에 예측하도록 지원한다. 따라서 산업용 모바일 로봇 구동 시스템은 단순한 이동 장치를 넘어 지능형 이동 인프라(Intelligent Mobility Infrastructure)로 발전하고 있다.

## 02 Drive System Evolution

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 AGV Era: Chain, Conveyor, and Fixed Path Systems

---

### 2.2 First Generation AMR: Differential Drive and SLAM

---

### 2.3 Second Generation AMR: Precision Heavy-Duty Steer Drive

### 2.1 AGV 시대: 체인, 컨베이어, 고정 경로 시스템

---

모바일 로봇 구동 시스템(Mobile Robot Drive System)의 발전은 현대적인 자율주행 로봇보다 훨씬 이전부터 시작되었다. 초기 산업용 이동 운반 시스템은 주로 무인운반차(AGV, Automated Guided Vehicle)로 분류되었으며, 제조 공장(Manufacturing Plant), 물류창고(Warehouse), 유통센터(Distribution Center)에서 반복적인 물류 이송 작업(Material Handling Task)을 자동화하기 위해 개발되었다. 이 시기의 구동 시스템은 정해진 위치에서 다른 위치로 물체를 이동시키는 것이 핵심 목표였으며, 자율성(Autonomy)이나 환경 인지(Environmental Awareness)는 거의 고려되지 않았다.

초기의 AGV는 대부분 고정 경로(Fixed Path)를 기반으로 동작하였다. 일부 시스템은 바닥에 설치된 레일(Rail)이나 기계식 가이드(Mechanical Guide)를 따라 이동하였으며, 생산 라인에서는 체인 컨베이어(Chain Conveyor)와 트롤리(Trolley)를 이용하여 물품을 운반하였다. 이러한 방식은 안정적이었지만 생산 라인 변경 시 대규모 시설 공사가 필요하다는 단점이 있었다.

이후 전자기 유도(Electromagnetic Guidance) 방식이 등장하였다. 바닥 아래에 매설된 유도선(Guidance Wire)에 전류를 흘려 전자기장을 형성하고, AGV에 장착된 센서가 이를 감지하여 경로를 추종하였다. 이 방식은 높은 신뢰성을 제공했지만, 경로를 변경하기 위해서는 바닥을 다시 시공해야 했기 때문에 유연성이 부족했다.

다음 단계에서는 자기 테이프(Magnetic Tape)와 광학 유도(Optical Guidance)가 도입되었다. 자기 테이프는 바닥 표면에 부착할 수 있어 설치가 용이했고, 광학 유도는 라인(Line), 반사 테이프(Reflective Tape), 마커(Marker)를 인식하여 경로를 따라 이동하는 방식이었다. 이러한 기술은 설치 비용을 줄였지만 여전히 외부 인프라(Infrastructure)에 의존한다는 한계를 가지고 있었다.

AGV의 구동 시스템은 비교적 단순했다. 대부분 차동 구동(Differential Drive) 또는 기본 조향 장치(Steering Mechanism)와 산업용 DC 모터(Industrial DC Motor), 감속기(Gearbox)를 사용하였다. 이동 경로가 이미 정해져 있었기 때문에 복잡한 모션 제어(Motion Control)는 필요하지 않았으며, 속도 유지와 경로 추종이 주요 기능이었다.

AGV의 가장 큰 장점은 예측 가능성(Predictability)이었다. 공장 엔지니어는 차량 경로, 교차로, 정차 위치, 작업 순서를 정확하게 정의할 수 있었으며, 이를 통해 생산 라인 자동화를 효율적으로 구현할 수 있었다. 자동차 공장(Automotive Factory), 전자제품 공장(Electronics Assembly Plant), 대형 물류센터(Logistics Center)에서는 이러한 특성 덕분에 AGV가 널리 보급되었다.

그러나 AGV는 여러 한계를 가지고 있었다. 경로 변경이 어렵고, 확장성이 낮으며, 장애물 회피 능력(Obstacle Avoidance Capability)이 부족했다. 경로 상에 장애물이 발생하면 대부분 정지 후 작업자의 개입을 기다려야 했다. 따라서 변화가 많은 환경에서는 운영 효율이 떨어질 수밖에 없었다.

그럼에도 불구하고 AGV 시대는 현대 모바일 로봇 산업의 기초를 마련하였다. 전기 구동(Electric Drive), 모터 제어(Motor Control), 산업용 통신(Industrial Communication), 안전 시스템(Safety System), 플릿 관리(Fleet Management) 개념 등은 모두 AGV 시대에 정립된 기술들이다. 오늘날의 AMR은 AGV의 한계를 극복한 진화형 시스템이라 볼 수 있다.

### 2.2 1세대 AMR: 차동 구동과 SLAM

---

모바일 로봇 구동 시스템의 첫 번째 큰 혁신은 자율이동로봇(AMR, Autonomous Mobile Robot)의 등장과 함께 이루어졌다. AGV가 외부 인프라에 의존했다면, AMR은 스스로 주변 환경을 인식하고 경로를 결정할 수 있도록 설계되었다. 이는 구동 시스템 설계 철학 자체를 변화시키는 중요한 전환점이었다.

1세대 AMR을 가능하게 한 핵심 기술은 동시 위치추정 및 지도작성(SLAM, Simultaneous Localization and Mapping)이었다. SLAM은 로봇이 이동하면서 주변 환경의 지도를 생성하고 동시에 자신의 위치를 추정하는 기술이다. 라이다(LiDAR), 카메라(Camera), 엔코더(Encoder), 관성측정장치(IMU) 등의 센서를 활용하여 실시간으로 환경을 인식할 수 있게 되었다.

이 시기의 대표적인 구동 방식은 차동 구동(Differential Drive)이었다. 차동 구동은 좌우에 배치된 두 개의 독립 구동 바퀴를 사용하며, 각 바퀴의 속도를 다르게 제어하여 회전을 수행한다. 양쪽 바퀴가 같은 속도로 회전하면 직진하고, 속도 차이가 발생하면 회전한다. 반대 방향으로 회전시키면 제자리 회전(Zero Radius Turn)도 가능하다.

차동 구동은 구조가 단순하고 제작 비용이 낮으며 유지보수가 쉽다는 장점을 가지고 있었다. 또한 좁은 공간에서 뛰어난 기동성(Maneuverability)을 제공하기 때문에 물류창고, 병원, 공장과 같은 실내 환경에 매우 적합했다.

SLAM의 도입은 구동 시스템에도 큰 변화를 가져왔다. 이제 구동 시스템은 단순히 모터를 돌리는 장치가 아니라 인지(Perception), 위치추정(Localization), 경로 계획(Path Planning), 모션 제어(Motion Control)와 긴밀하게 연결된 시스템이 되었다. 센서와 컴퓨터, 모터 컨트롤러 사이의 실시간 데이터 교환이 필수적인 요소가 되었다.

이후 모션 제어 기술이 발전하면서 오도메트리 보정(Odometry Correction), 센서 융합(Sensor Fusion), 예측 제어(Predictive Control), 적응형 속도 제어(Adaptive Velocity Control) 등의 기술이 적용되었다. 이를 통해 경로 추종 성능과 주행 안정성이 크게 향상되었다.

하지만 차동 구동은 몇 가지 한계를 가지고 있었다. 정밀한 위치 정렬이 필요한 작업에서는 오차가 누적되기 쉽고, 바퀴 미끄러짐(Wheel Slip)이나 바닥 상태 변화에 민감했다. 또한 무거운 하중(Payload)이 증가할수록 조향 성능과 정밀도가 저하되는 문제가 발생했다.

그럼에도 불구하고 1세대 AMR은 산업 자동화에 혁명적인 변화를 가져왔다. 고정 인프라 없이도 자율주행이 가능해졌으며, 장애물 회피(Dynamic Obstacle Avoidance), 동적 경로 재계획(Dynamic Replanning), 대규모 플릿 운영(Fleet Operation)이 가능해졌다. 차동 구동과 SLAM의 조합은 현재까지도 가장 널리 사용되는 실내 AMR 구조 중 하나이다.

### 2.3 2세대 AMR: 정밀 고하중 스티어 드라이브

산업 현장의 요구 수준이 높아지면서 2세대 AMR 구동 시스템이 등장하게 되었다. 1세대 AMR이 자율주행을 가능하게 했다면, 2세대 AMR은 더 높은 정밀도(Precision), 더 큰 적재 능력(Payload Capacity), 더 우수한 안정성(Stability)을 목표로 발전하였다. 이러한 변화의 중심에는 스티어 드라이브(Steer Drive)가 있었다.

스티어 드라이브는 추진(Propulsion)과 조향(Steering)을 분리한 구조를 가진다. 각 구동 모듈은 구동 모터(Traction Motor)와 조향 모터(Steering Motor)를 독립적으로 가지고 있으며, 이를 통해 바퀴 방향과 추진력을 각각 정밀하게 제어할 수 있다.

이 구조의 가장 큰 장점은 높은 위치 정밀도(Positioning Accuracy)이다. 컨베이어(Conveyor), 자동 창고(ASRS, Automated Storage and Retrieval System), 기계 설비(Machine Tool), 충전 스테이션(Charging Station)과의 정렬에서는 수 밀리미터 수준의 오차만 허용되는 경우가 많다. 스티어 드라이브는 바퀴 방향을 직접 제어하기 때문에 차동 구동보다 훨씬 정확한 경로 추종(Path Tracking)이 가능하다.

고하중 운송(Heavy Payload Transportation) 역시 중요한 발전 요인이었다. 산업 현장에서는 수백 킬로그램에서 수 톤(Ton)에 이르는 물체를 운반해야 하는 경우가 많다. 차동 구동은 무거운 하중이 걸릴수록 회전 성능이 저하될 수 있지만, 스티어 드라이브는 하중과 관계없이 안정적인 조향 성능을 유지할 수 있다.

정밀 스티어 드라이브의 발전은 센서와 제어 기술의 발전과도 밀접하게 연관되어 있다. 절대형 엔코더(Absolute Encoder), EtherCAT 기반 모션 네트워크(Motion Network), 고성능 모터 컨트롤러, 실시간 제어 플랫폼(Real-Time Computing Platform)이 등장하면서 바퀴 각도와 속도를 매우 정밀하게 제어할 수 있게 되었다.

2세대 AMR은 안전성 측면에서도 크게 향상되었다. 기능 안전(Functional Safety), 이중화 센서(Redundant Sensor), 안전 제동(Safe Braking), 예측 진단(Predictive Diagnostics) 기술이 적용되면서 사람과 함께 작업하는 환경에서도 높은 수준의 안전성을 제공할 수 있게 되었다.

또한 대규모 플릿 운영(Fleet Operation)을 위한 요구사항도 스티어 드라이브 발전을 촉진하였다. 수십 대에서 수백 대의 로봇이 동시에 운영되는 환경에서는 모든 차량이 예측 가능한 방식으로 움직여야 한다. 스티어 드라이브는 더 부드럽고 안정적인 이동을 제공하여 교통 관리(Traffic Management)와 경로 최적화(Path Optimization)를 용이하게 한다.

오늘날 정밀 고하중 AMR은 반도체 공장(Semiconductor Factory), 자동차 공장(Automotive Factory), 배터리 공장(Battery Manufacturing Facility), 항공우주 산업(Aerospace Industry), 대형 물류센터(Large-Scale Warehouse) 등에서 핵심 자동화 장비로 활용되고 있다.

결과적으로 2세대 AMR은 단순한 자율 운반 장비를 넘어 지능형 물류 플랫폼(Intelligent Material Flow Platform)으로 진화하고 있다. 차동 구동이 실내 AMR 시대를 열었다면, 스티어 드라이브는 고정밀·고하중·대규모 자율 물류 시대를 여는 핵심 기술이라고 할 수 있다. 특히 향후 힐스로보틱스(Hills Robotics)가 추진하는 500kg, 1000kg, 1500kg급 실내 AMR과 실외 자율주행 플랫폼에서는 스티어 드라이브가 사실상 표준 아키텍처(Standard Architecture)가 될 가능성이 매우 높다.

## 03 Industrial AMR Examples

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Light Class (50 to 200 kg) Examples

---

### 3.2 Mid Class (200 to 750 kg) Examples

---

### 3.3 Heavy Class (750 kg and Above) Examples

### 3.1 경량급 AMR 사례 (50\~200kg)

---

경량급 자율이동로봇(AMR, Autonomous Mobile Robot)은 일반적으로 50kg에서 200kg 수준의 적재 능력(Payload Capacity)을 가지며, 현재 산업 현장에서 가장 널리 보급된 모바일 로봇 분야를 구성하고 있다. 이러한 로봇은 경량 물류 운송(Light Material Transportation), 생산라인 자재 공급(Line-side Replenishment), 병원 물류(Hospital Logistics), 실험실 자동화(Laboratory Automation), 전자상거래 물류(E-commerce Fulfillment), 사무실 배송(Office Delivery) 등의 목적으로 활용된다. 비교적 작은 크기와 낮은 도입 비용, 그리고 빠른 구축 가능성 덕분에 자동화를 처음 도입하는 기업들이 가장 많이 선택하는 로봇 유형이다.

경량급 AMR은 주로 실내 환경(Indoor Environment)에서 운영되며 적재 능력보다는 기동성(Maneuverability), 유연성(Flexibility), 안전성(Safety)을 우선적으로 고려하여 설계된다. 일반적인 크기는 폭 500\~900mm, 길이 700\~1200mm 정도이며, 사람이 사용하는 통로와 작업 공간을 자유롭게 이동할 수 있도록 설계된다.

대부분의 경량급 AMR은 차동 구동(Differential Drive) 구조를 사용한다. 차동 구동은 제자리 회전(Zero Radius Turn)이 가능하고 구조가 단순하여 제조 비용이 낮다. 또한 유지보수가 쉬워 물류창고(Warehouse), 병원(Hospital), 공장(Factory)과 같은 협소한 공간에서 높은 효율성을 제공한다. 일반적으로 브러시리스 DC 모터(BLDC Motor)와 유성감속기(Planetary Gearbox)가 사용된다.

항법 시스템(Navigation System)은 대부분 라이다 기반 SLAM(LiDAR-based SLAM), 비전 SLAM(Visual SLAM), 또는 하이브리드 위치추정(Hybrid Localization)을 사용한다. 2D 라이다(2D LiDAR)가 가장 널리 사용되며, 일부 고급 모델은 깊이 카메라(Depth Camera), 초음파 센서(Ultrasonic Sensor), IMU를 추가하여 인식 성능을 향상시킨다.

이러한 로봇은 선반(Shelf), 카트(Cart), 빈(Bin), 랙(Rack), 협업 작업대(Collaborative Workstation)와 결합되어 사용된다. 물류창고에서는 상품 컨테이너를 이동시키고, 병원에서는 의약품과 검체를 운반하며, 제조 공장에서는 생산 자재와 반제품(Work-In-Progress)을 공급한다.

전자상거래 물류센터(E-commerce Fulfillment Center)에서 사용하는 피킹 로봇(Picking Robot), 병원 물류 로봇(Hospital Logistics Robot), 반도체 공장 물류 로봇(Semiconductor Logistics Robot) 등이 대표적인 사례이다. 일반적으로 100kg에서 150kg 수준의 적재 능력을 가지며, 수십 대에서 수백 대 규모의 플릿(Fleet)으로 운영된다.

경량급 AMR의 가장 큰 장점은 빠른 구축 속도와 높은 확장성(Scalability)이다. 또한 전력 소비가 적고 기계적 부하가 낮기 때문에 유지보수 비용도 상대적으로 저렴하다.

반면 적재 능력의 한계로 인해 중량 산업 물류에는 적합하지 않다. 작은 바퀴 구조 때문에 요철(Uneven Floor), 경사로(Ramp), 실외 환경(Outdoor Environment)에 취약하며 배터리 용량도 제한적이다. 그럼에도 불구하고 경량급 AMR은 현재 실내 자동화 시장에서 가장 큰 비중을 차지하며, 많은 기업들이 자율주행 로봇을 도입하는 첫 단계로 활용하고 있다.

### 3.2 중형급 AMR 사례 (200\~750kg)

---

중형급 AMR은 200kg에서 750kg 수준의 적재 능력을 가진 로봇으로, 경량 물류 로봇과 고하중 산업용 로봇 사이를 연결하는 핵심 시장을 형성하고 있다. 최근 스마트 팩토리(Smart Factory)와 인더스트리 4.0(Industry 4.0)의 확산에 따라 가장 빠르게 성장하는 분야 중 하나로 평가받고 있다.

현대 제조 공장은 팔레트(Pallet), 생산 자재(Production Material), 반조립품(Subassembly), 완제품(Finished Product)을 작업 공정 간에 자동으로 이동시키는 시스템을 요구한다. 중형급 AMR은 이러한 요구를 충족하면서도 기존 AGV보다 훨씬 높은 유연성을 제공한다.

중형급 AMR부터는 스티어 드라이브(Steer Drive) 구조가 본격적으로 도입되기 시작한다. 하중이 증가할수록 차동 구동의 정밀도와 효율이 떨어지기 때문에, 추진(Traction)과 조향(Steering)을 분리한 구조가 선호된다. 일부 시스템은 듀얼 스티어 드라이브(Dual Steer Drive)를 사용하며, 고급 모델은 4륜 조향(Four-Wheel Steering) 구조를 적용한다.

센서 구성도 더욱 복잡해진다. 다중 라이다(Multiple LiDAR), 3D 비전 센서(3D Vision Sensor), 스테레오 카메라(Stereo Camera), 안전 스캐너(Safety Scanner), 이중화 위치추정 시스템(Redundant Localization System)이 적용된다. 센서 융합(Sensor Fusion)을 통해 보다 높은 신뢰성과 정밀도를 제공한다.

일반적인 중형급 AMR은 자체 중량이 250kg에서 800kg 정도이며, 적재 능력은 최대 750kg 수준이다. 폭은 800\~1500mm, 길이는 1000\~2000mm 수준으로 설계된다. 배터리 용량도 수 kWh 수준 이상으로 증가하여 장시간 연속 운행이 가능하다.

자동차 공장(Automotive Factory)에서는 부품과 모듈을 생산 셀 간에 운송하고, 전자 제조 공장(Electronics Manufacturing Facility)에서는 자재 보충(Material Replenishment)에 활용된다. 제약 공장(Pharmaceutical Facility)에서는 무균 물류(Sterile Material Transport)에 사용되며, 물류센터에서는 팔레트 운반(Pallet Movement)과 주문 통합(Order Consolidation)에 활용된다.

많은 중형급 AMR은 자동 리프팅 장치(Automatic Lift Module), 컨베이어 인터페이스(Conveyor Interface), 로봇팔 통합(Robot Arm Integration), 자동 도킹 시스템(Automatic Docking System)을 지원한다. 이를 통해 단순 운송 수단이 아니라 이동형 작업 플랫폼(Mobile Work Platform)으로 활용된다.

중형급 AMR은 기존 지게차(Forklift)의 역할을 상당 부분 대체할 수 있다는 점에서 높은 경제적 가치를 가진다. 인력 운송 작업을 줄이고 안전성을 향상시키며 생산성을 높이는 효과를 제공한다.

다만 적재 중량이 증가할수록 차체 강성(Structural Rigidity), 제동 성능(Braking Performance), 타이어 수명(Tire Durability), 배터리 에너지 밀도(Energy Density) 등이 중요한 설계 요소가 된다. 그럼에도 불구하고 중형급 AMR은 현대 제조업과 물류 산업에서 가장 중요한 자동화 장비 중 하나로 자리잡고 있다.

### 3.3 고하중급 AMR 사례 (750kg 이상)

고하중급 AMR은 750kg 이상의 적재 능력을 가진 산업용 자율주행 로봇으로, 현재 모바일 로봇 기술의 최상위 분야를 구성한다. 일반적으로 1톤(Ton), 2톤, 5톤 이상의 화물을 운반할 수 있으며, 기존의 지게차(Forklift), 견인 차량(Tugger Vehicle), 수동 운반 장비를 대체하는 역할을 수행한다.

고하중급 AMR의 등장은 스마트 팩토리(Smart Factory)와 완전 자동화 물류 시스템(Autonomous Material Flow System)에 대한 요구 증가와 함께 이루어졌다. 자동차 제조(Automotive Manufacturing), 배터리 생산(Battery Manufacturing), 항공우주(Aerospace), 반도체(Semiconductor), 중장비 제조(Heavy Machinery Production) 산업에서는 수백 kg에서 수 톤에 이르는 고가의 부품을 안전하게 이동시켜야 한다.

이러한 요구를 충족하기 위해 고하중급 AMR은 대부분 정밀 스티어 드라이브(Precision Steer Drive)를 채택한다. 4륜 조향(Four-Wheel Steering), 다축 구동(Multi-Axle Drive), 독립 휠 모듈(Independent Wheel Module), 관절형 조향(Articulated Steering) 구조가 널리 사용된다.

차량 자체 중량은 수백 kg에서 수 톤에 이르며, 적재 능력은 1000kg에서 5000kg 이상까지 확장될 수 있다. 이를 위해 고토크 모터(High-Torque Motor), 산업용 감속기(Industrial Gearbox), 강화 섀시(Reinforced Chassis), 고하중 서스펜션(Heavy-Duty Suspension)이 적용된다.

위치추정(Localization)과 항법(Navigation) 기술도 매우 높은 수준을 요구한다. 수 톤의 화물을 운반하는 경우 수 cm의 오차도 큰 문제가 될 수 있기 때문이다. 따라서 고해상도 라이다(High-Resolution LiDAR), 비전 위치추정(Vision Localization), 절대 위치 시스템(Absolute Positioning System), 고급 센서 융합 기술이 적용된다.

안전성은 가장 중요한 설계 요소 중 하나이다. 2톤 이상의 화물을 적재한 로봇은 매우 큰 운동 에너지(Kinetic Energy)를 가지므로, 충돌 회피(Collision Avoidance), 비상 제동(Emergency Braking), 기능 안전(Functional Safety), 이중화 안전 제어기(Redundant Safety Controller)가 필수적으로 적용된다.

배터리 시스템 역시 대형화된다. 일반적으로 10kWh에서 50kWh 이상의 배터리가 사용되며, 자동 충전(Auto Charging) 또는 배터리 교체(Battery Swapping)를 통해 24시간 운영이 가능하도록 설계된다.

대표적인 적용 사례로는 전기차 배터리 팩(Battery Pack) 운송, 항공기 부품(Aircraft Component) 이동, 반도체 장비(Semiconductor Equipment) 이송, 대형 물류센터의 팔레트 물류(Pallet Logistics), 중장비 제조 공정 등이 있다.

향후 산업용 모바일 로봇 시장은 점점 더 고하중급 플랫폼 중심으로 발전할 가능성이 높다. 인공지능(AI), 디지털 트윈(Digital Twin), 예지보전(Predictive Maintenance), 플릿 최적화(Fleet Optimization)가 통합되면서 이러한 로봇은 단순 운송 장비를 넘어 공장 전체의 물류를 관리하는 지능형 인프라(Intelligent Infrastructure)로 진화할 것이다.

특히 향후 힐스로보틱스(Hills Robotics)가 추진하고 있는 1000kg, 1500kg, 2000kg급 실내 AMR과 실외 자율주행 플랫폼은 바로 이러한 고하중급 AMR 시장에 해당한다. 이 분야는 향후 스마트 제조(Smart Manufacturing)와 자율 물류(Autonomous Logistics)의 핵심 기술 영역이 될 것으로 전망된다.

## 04 Drive System Classification

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Differential Drive

---

### 4.2 Steer Drive

---

### 4.3 Mecanum Drive

---

### 4.4 Omni Drive Wheel Types and Configurations

### 4.1 차동 구동(Differential Drive)

---

차동 구동(Differential Drive)은 현대 이동 로봇(Mobile Robot)과 자율주행 이동로봇(AMR, Autonomous Mobile Robot)에서 가장 널리 사용되는 구동 구조이다. 이 방식은 좌측 바퀴와 우측 바퀴의 속도 차이를 이용하여 이동 방향을 결정하는 원리에 기반한다. 양쪽 바퀴가 동일한 속도로 회전하면 직진하고, 속도 차이가 발생하면 곡선 주행을 하게 된다. 또한 양쪽 바퀴가 서로 반대 방향으로 같은 속도로 회전하면 제자리 회전(Zero-Radius Turn)이 가능하다.

일반적인 차동 구동 플랫폼은 두 개의 구동 바퀴(Drive Wheel)와 하나 이상의 캐스터 휠(Caster Wheel)로 구성된다. 구동을 위해 두 개의 모터만 필요하므로 기계 구조가 매우 단순하며 제조 비용도 낮다. 부품 수가 적기 때문에 유지보수가 쉽고 고장 가능성이 낮아 높은 신뢰성을 확보할 수 있다. 이러한 이유로 물류 로봇(Logistics Robot), 병원 배송 로봇(Hospital Delivery Robot), 창고 이송 시스템(Warehouse Transport System), 교육용 로봇(Educational Robot) 등에 널리 사용된다.

운동학(Kinematics) 관점에서 차동 구동은 비홀로노믹 시스템(Non-Holonomic System)으로 분류된다. 즉, 로봇은 원하는 방향으로 즉시 이동할 수 없으며 측면 이동(Lateral Motion)이 불가능하다. 측면 방향으로 이동하기 위해서는 먼저 회전한 후 전진 또는 후진을 수행해야 한다. 이러한 제약은 기동성을 감소시키지만 제어 알고리즘(Control Algorithm)을 단순화하고 계산 부담을 줄이는 장점도 제공한다.

차동 구동의 회전 특성은 순간 회전 중심(ICC, Instantaneous Center of Curvature) 개념으로 설명할 수 있다. 좌우 바퀴의 속도 비율에 따라 ICC 위치가 달라지며, 직진 시에는 무한대에 위치하고 제자리 회전 시에는 차량 중심에 위치한다. 이러한 모델은 주행 제어, 오도메트리(Odometry), 경로 계획(Path Planning)의 기반이 된다.

차동 구동의 가장 큰 장점 중 하나는 경량 및 중량급 플랫폼으로의 확장성이 우수하다는 점이다. 일반적으로 50kg에서 500kg 수준의 페이로드(Payload)를 가지는 AMR에서는 충분한 성능을 제공할 수 있다. 그러나 수백 kg 이상의 중량으로 증가하면 여러 가지 한계가 나타난다. 회전 시 바퀴 방향이 고정되어 있기 때문에 바닥과의 마찰로 인해 스크러빙(Scrubbing)이 발생하며, 이는 타이어 마모, 바닥 손상, 에너지 손실, 위치 정밀도 저하를 유발한다.

750kg 이상 또는 1톤 이상의 중량급 AMR에서는 가속, 감속 및 회전 과정에서 슬립(Slip)이 크게 증가한다. 차량 질량이 증가할수록 비홀로노믹 제약을 극복하기 위한 마찰력이 증가하기 때문이다. 이러한 이유로 많은 중량급 산업용 AMR 제조사들은 정밀 도킹(Precision Docking)과 고중량 운반이 필요한 경우 스티어 구동(Steer Drive) 방식으로 전환하고 있다.

그럼에도 불구하고 차동 구동은 단순성, 경제성, 높은 신뢰성이 요구되는 환경에서 여전히 매우 경쟁력 있는 솔루션이다. 최근에는 라이다 기반 위치추정(LiDAR-based Localization), 비전 내비게이션(Vision Navigation), 센서 융합(Sensor Fusion) 기술과 결합되어 다양한 산업 환경에서 안정적인 자율주행 성능을 제공하고 있다.

### 4.2 스티어 구동(Steer Drive)

---

스티어 구동(Steer Drive)은 차동 구동의 한계를 극복하기 위해 개발된 보다 고급형 이동 로봇 구동 구조이다. 각 바퀴 모듈에는 구동 모터(Drive Motor)와 조향 모터(Steering Motor)가 각각 존재하며, 구동 기능과 조향 기능이 분리되어 독립적으로 제어된다.

차동 구동과 달리 스티어 구동은 이동 전에 바퀴 방향을 목표 이동 방향에 맞게 조정할 수 있다. 따라서 불필요한 횡방향 마찰이 크게 감소하며 에너지 효율도 향상된다. 이러한 특성 덕분에 스티어 구동은 1톤 이상의 고중량 AMR에서 특히 많이 사용된다.

현대 산업용 스티어 구동 AMR은 대부분 4륜 조향(4WS, Four Wheel Steering)과 4륜 구동(4WD, Four Wheel Drive)을 채택한다. 각각의 바퀴를 독립적으로 제어할 수 있기 때문에 직진, 후진, 대각선 이동, 크랩 이동(Crab Motion), 제자리 회전과 같은 다양한 주행 모드를 구현할 수 있다.

특히 크랩 이동은 생산 라인이나 설비 근처에서 매우 유용하다. 로봇이 자세를 유지한 상태로 측면 이동할 수 있기 때문에 좁은 공간에서도 효율적인 작업이 가능하다. 이러한 특성은 검사 장비, 협동 로봇(Collaborative Robot), 자동 도킹 시스템 등에 매우 적합하다.

운동학적으로 스티어 구동은 홀로노믹(Holonomic) 시스템에 가까운 특성을 가진다. 엄밀한 의미에서 완전한 홀로노믹 구조는 아닐 수 있지만, 실제 운용에서는 거의 동일한 수준의 자유로운 이동이 가능하다. 따라서 복잡한 공장 환경이나 좁은 통로에서도 뛰어난 기동성을 제공한다.

반면 기계 구조는 상당히 복잡하다. 각 모듈마다 조향 기구, 기어박스(Gearbox), 엔코더(Encoder), 베어링(Bearing), 제어기(Controller)가 필요하므로 제조 비용이 증가한다. 또한 유지보수와 초기 설계 난이도도 차동 구동보다 훨씬 높다.

제어 복잡성 또한 증가한다. 네 개 이상의 조향축과 구동축을 동시에 동기화해야 하며, 작은 조향 오차도 위치 오차로 이어질 수 있다. 이러한 이유로 산업용 시스템에서는 이더캣(EtherCAT) 기반의 실시간 통신 네트워크가 널리 사용된다.

스티어 구동의 가장 큰 장점은 높은 위치 정밀도이다. 자동차 공장이나 반도체 공장에서는 ±20mm 이하의 정밀 도킹을 요구하는 경우가 많다. 스티어 구동은 슬립을 최소화하고 정밀한 접근 제어가 가능하기 때문에 이러한 요구사항을 만족시킬 수 있다.

현재 500kg 이상에서 수 톤급까지의 산업용 AMR 시장에서는 스티어 구동이 빠르게 표준으로 자리잡고 있다. 초기 비용은 높지만 높은 정밀도, 낮은 바닥 마모, 우수한 내구성, 뛰어난 기동성 덕분에 장기적인 운영 효율이 우수하다.

### 4.3 메카넘 구동(Mecanum Drive)

---

메카넘 구동(Mecanum Drive)은 로봇이 자세를 변경하지 않고도 모든 방향으로 이동할 수 있도록 설계된 대표적인 전방향 이동(Omnidirectional Motion) 기술이다. 메카넘 휠(Mecanum Wheel)의 가장 큰 특징은 바퀴 둘레에 약 45도 각도로 배치된 자유 회전 롤러(Roller)를 사용한다는 점이다.

이 롤러 구조는 바퀴가 회전할 때 힘을 여러 방향으로 분해한다. 네 개의 메카넘 휠을 적절히 제어하면 전진, 후진, 좌우 이동, 대각선 이동, 회전을 모두 수행할 수 있다. 따라서 로봇은 방향을 바꾸지 않고도 원하는 위치로 직접 이동할 수 있다.

메카넘 구동은 홀로노믹 구동(Holonomic Drive)으로 분류된다. 평면 상에서 X축 속도, Y축 속도, 회전 속도를 독립적으로 제어할 수 있기 때문이다. 이러한 특성은 매우 높은 기동성을 제공한다.

측면 이동 능력은 메카넘 구동의 가장 큰 장점이다. 반도체 공장, 전자 제조 공장, 연구실, 자동화 설비와 같이 공간이 제한된 환경에서는 측면 이동만으로도 작업 효율을 크게 향상시킬 수 있다.

그러나 이러한 장점에는 대가가 따른다. 구동력이 롤러를 통해 전달되기 때문에 일부 에너지가 손실된다. 따라서 동일한 중량을 이동시키기 위해 차동 구동보다 더 큰 모터가 필요할 수 있다.

또한 롤러가 바닥과 반복적으로 접촉하면서 다각형 주행 효과(Polygon Effect)가 발생한다. 이로 인해 진동(Vibration)과 소음(Noise)이 증가하며 승차감도 저하된다. 특히 속도가 증가할수록 이러한 현상은 더욱 두드러진다.

바닥 상태 역시 성능에 큰 영향을 준다. 바닥이 고르지 않거나 이물질이 존재하면 롤러 슬립이 발생하고 위치 정밀도가 저하된다. 따라서 메카넘 구동은 일반적으로 평탄하고 깨끗한 실내 환경에서 사용된다.

이러한 제약에도 불구하고 메카넘 구동은 이동형 매니퓰레이터(Mobile Manipulator), 반도체 웨이퍼 이송 로봇(Wafer Transport Robot), 협동 작업 로봇 등 높은 기동성이 요구되는 응용 분야에서 매우 효과적인 솔루션으로 활용되고 있다.

### 4.4 옴니 구동 휠 종류 및 구성(Omni Drive Wheel Types and Configurations)

옴니 구동(Omni Drive)은 자유 회전 롤러를 활용하여 전방향 이동을 구현하는 구동 방식 전체를 의미한다. 메카넘 휠도 옴니 구동의 한 종류로 볼 수 있지만, 옴니 구동은 다양한 휠 구조와 배치 방식을 포함하는 더 넓은 개념이다.

일반적인 옴니 휠(Omni Wheel)은 롤러가 약 90도 방향으로 배치되어 있다. 이 롤러는 구동 방향의 힘은 전달하면서 수직 방향으로는 자유롭게 회전할 수 있다. 여러 개의 옴니 휠을 조합하면 로봇은 자유로운 방향 이동이 가능해진다.

대표적인 구성 중 하나는 3륜 옴니 구성(Three-Wheel Omni Configuration)이다. 세 개의 휠을 120도 간격으로 배치하여 전방향 이동을 구현한다. 구조가 단순하고 구동기가 적게 필요하기 때문에 교육용 로봇, 서비스 로봇, 경량 산업용 플랫폼에 많이 사용된다.

4륜 옴니 구성(Four-Wheel Omni Configuration)은 보다 높은 안정성과 하중 지지 능력을 제공한다. 사각형 구조로 휠을 배치하기 때문에 하중 분산이 우수하며 동적 안정성도 향상된다. 따라서 중량이 증가하는 산업용 플랫폼에서 널리 사용된다.

메카넘 휠 역시 옴니 구동의 특수 형태로 볼 수 있다. 45도 롤러를 사용하는 메카넘 휠은 X형(X-Type) 또는 O형(O-Type) 배열로 구성되며, 롤러 방향에 따라 힘 분포와 주행 특성이 달라진다.

옴니 구동의 가장 큰 장점은 뛰어난 기동성이다. 회전 없이 원하는 방향으로 이동할 수 있으며 경로 계획(Path Planning)도 단순해진다. 특히 협소한 공간에서 매우 높은 작업 효율을 제공한다.

그러나 바닥 품질에 대한 민감도가 높다. 롤러 마모는 위치 정밀도와 효율을 저하시킬 수 있으며 정기적인 유지보수가 필요하다. 또한 롤러에 집중되는 접촉 응력(Contact Stress) 때문에 고중량 응용 분야에서는 한계가 존재한다.

일반적으로 수백 kg 이상의 고중량 AMR에서는 스티어 구동이 내구성과 효율 측면에서 더 우수한 선택이 된다. 반면 경량 및 중량급 플랫폼에서는 옴니 구동이 탁월한 기동성을 제공한다.

결국 차동 구동(Differential Drive), 스티어 구동(Steer Drive), 메카넘 구동(Mecanum Drive), 옴니 구동(Omni Drive)은 각각 다른 목적을 가진 기술이다. 차동 구동은 단순성과 경제성을, 스티어 구동은 정밀도와 고중량 운반 능력을, 메카넘 및 옴니 구동은 최고의 기동성과 전방향 이동 능력을 제공한다. 따라서 실제 산업용 AMR 설계에서는 요구되는 페이로드(Payload), 위치 정밀도(Positioning Accuracy), 작업 공간 제약, 유지보수 전략 등을 종합적으로 고려하여 적절한 구동 방식을 선택해야 한다.

## 05 Drive System Selection Guide

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Payload Based Primary Classification

---

### 5.2 Precision Based Secondary Classification

---

### 5.3 How to Use This Manual

### 5.1 적재중량 기반 1차 분류

---

모바일 로봇의 구동 시스템(Drive System)을 선택할 때 가장 먼저 고려해야 할 요소는 적재중량(Payload)이다. 적재중량은 모터 크기(Motor Sizing), 감속기 설계(Gearbox Design), 바퀴 구성(Wheel Configuration), 차체 강성(Structural Rigidity), 에너지 소비(Energy Consumption), 제동 성능(Braking Performance), 안전 요구사항(Safety Requirement), 그리고 전체 차량 아키텍처(Vehicle Architecture)에 직접적인 영향을 미친다. 따라서 산업용 로봇에서는 적재중량을 가장 우선적인 분류 기준으로 사용하는 것이 일반적이다.

적재중량 기반 분류는 설계 과정을 단순화하는 데 큰 도움이 된다. 일반적으로 경량급(Light Class) 로봇은 50kg에서 200kg 정도의 적재 능력을 가진다. 이러한 로봇은 물류창고(Warehouse), 병원(Hospital), 실험실(Laboratory), 서비스 로봇(Service Robot), 경량 제조 환경(Light Manufacturing Environment)에서 주로 활용된다. 적재 하중이 크지 않기 때문에 차동 구동(Differential Drive)이 비용, 구조 단순성, 기동성 측면에서 가장 적합한 선택이 되는 경우가 많다. 전력 소비도 적고 유지보수 비용도 낮다.

중형급(Mid Class) 로봇은 약 200kg에서 750kg 수준의 적재 능력을 가진다. 이 영역에서는 구동 시스템 선택이 보다 복잡해진다. 적재 하중이 증가하면서 바퀴에 전달되는 하중과 견인력(Traction Force), 구조적 응력(Structural Stress)이 증가하기 때문이다. 이 경우 차동 구동도 일부 적용 가능하지만, 스티어 드라이브(Steer Drive)가 점차 선호되는 구조가 된다. 독립적인 조향 제어를 통해 안정성과 경로 추종 성능을 향상시킬 수 있으며, 타이어 마모 감소와 에너지 효율 향상 효과도 얻을 수 있다.

고하중급(Heavy Class) 로봇은 750kg 이상의 적재 능력을 가진다. 이 영역에서는 차량 동역학(Vehicle Dynamics), 제동 시스템(Braking System), 안전 인증(Safety Certification), 구조 설계(Structural Engineering)가 매우 중요한 요소가 된다. 무거운 하중은 가속과 감속, 회전 시 큰 관성력(Inertial Force)을 발생시키므로 스티어 드라이브가 사실상 표준 구조가 된다. 4륜 스티어 드라이브(Four-Wheel Steer Drive), 듀얼 스티어 모듈(Dual Steer Module), 다축 조향(Multi-Axle Steering) 등이 주로 사용된다.

적재중량은 전원 시스템(Power System)의 설계에도 직접적인 영향을 미친다. 경량급 로봇은 일반적으로 1\~3kWh 수준의 배터리를 사용하지만, 중형급은 3\~10kWh, 고하중급은 10\~50kWh 이상의 대용량 배터리가 필요할 수 있다.

또한 적재중량은 단순히 숫자상의 무게만 의미하지 않는다. 적재물의 무게 중심(Center of Gravity), 하중 분포(Load Distribution), 동적 하중 변화(Dynamic Load Variation), 바닥 상태(Floor Condition)도 모두 고려해야 한다. 예를 들어 동일한 500kg 적재물이라도 낮고 넓게 배치된 경우와 높고 집중적으로 적재된 경우는 차량 거동이 완전히 달라질 수 있다.

실제 산업 현장에서는 적재중량을 먼저 정의한 후 위치 정밀도(Positioning Accuracy), 작업 환경(Environment), 항법 방식(Navigation Method), 운영 조건(Operation Condition)을 검토하는 순서가 가장 효율적이다. 이러한 접근 방식은 설계 복잡성을 줄이고 최적의 구동 시스템을 선택하는 데 도움을 준다.

### 5.2 정밀도 기반 2차 분류

---

적재중량이 1차 분류 기준이라면, 위치 정밀도(Positioning Accuracy)는 2차 분류 기준이 된다. 동일한 적재 능력을 가진 두 개의 로봇이라도 요구되는 정밀도 수준에 따라 전혀 다른 구동 시스템을 선택해야 할 수 있다. 따라서 적재중량으로 후보군을 결정한 이후에는 반드시 정밀도 기반 분류를 수행해야 한다.

산업 현장에서 요구되는 정밀도 수준은 매우 다양하다. 단순 물류 이송은 수 cm 수준의 오차를 허용할 수 있지만, 반도체 제조(Semiconductor Manufacturing), 배터리 조립(Battery Assembly), 정밀 검사(Precision Inspection), 자동 도킹(Automatic Docking)과 같은 작업은 수 mm 또는 1mm 이하의 정밀도를 요구하기도 한다.

저정밀도(Low Precision) 응용 분야는 일반적으로 ±20mm 이상의 위치 오차를 허용한다. 물류창고 운송, 재고 이동, 병원 물류, 일반 자재 운반 등이 대표적인 사례이다. 이러한 환경에서는 차동 구동이 충분한 성능을 제공하며, 위치 정밀도는 주로 라이다(LiDAR), 카메라(Camera), SLAM 알고리즘에 의해 결정된다.

중정밀도(Medium Precision) 응용 분야는 ±5\~20mm 수준의 정확도를 요구한다. 생산라인 자재 공급(Line-side Material Delivery), 자동 팔레트 운송(Pallet Transport), 제조 지원 시스템 등이 여기에 속한다. 이 수준부터는 스티어 드라이브의 장점이 뚜렷하게 나타난다. 조향각을 직접 제어하기 때문에 경로 추종 오차(Path Tracking Error)가 감소하고 반복 정밀도(Repeatability)가 향상된다.

고정밀도(High Precision) 응용 분야는 ±5mm 이하, 경우에 따라 ±1mm 이하의 위치 정밀도를 요구한다. 반도체 공장, 자동 설비 로딩 시스템(Machine Loading System), 배터리 생산라인, 계측 장비(Metrology Equipment) 등이 대표적이다. 이러한 환경에서는 스티어 드라이브가 사실상 필수적이며, 비전 유도(Vision Guidance), 레이저 위치 측정(Laser Positioning), 마커 기반 위치 보정(Fiducial Marker Tracking) 등의 추가 기술이 함께 사용된다.

정밀도 분류에서는 절대 정확도(Absolute Accuracy)뿐 아니라 반복 정밀도(Repeatability)도 중요하다. 산업 현장에서는 항상 같은 위치에 도달하는 능력이 매우 중요하다. 반복적으로 ±2mm 이내를 유지하는 로봇이 가끔 ±1mm를 달성하지만 변동성이 큰 로봇보다 더 높은 가치를 가질 수 있다.

또한 정밀도는 환경 조건의 영향을 크게 받는다. 바닥 평탄도(Floor Flatness), 타이어 마모(Tire Wear), 온도 변화(Temperature Variation), 진동(Vibration), 적재 하중 변화(Payload Variation) 등이 모두 위치 오차에 영향을 미친다. 따라서 실제 운영 환경을 고려한 설계가 필수적이다.

결국 적재중량 기반 분류와 정밀도 기반 분류를 함께 적용함으로써 적절한 구동 시스템을 보다 효율적으로 선택할 수 있다. 이러한 2단계 분류 방법은 현대 산업용 모바일 로봇 설계의 핵심 방법론으로 활용되고 있다.

### 5.3 이 매뉴얼의 활용 방법

본 매뉴얼은 모바일 로봇 구동 시스템(Mobile Robot Drive System)을 이해하고, 평가하고, 설계하고, 선택하기 위한 체계적인 엔지니어링 참고서(Engineering Reference)로 작성되었다. 단순히 구동 기술을 나열하는 것이 아니라 실제 산업 현장에서 의사결정을 수행하는 과정을 중심으로 구성되어 있다. 따라서 독자는 기초 개념부터 실제 시스템 설계까지 단계적으로 학습할 수 있다.

먼저 모바일 로봇 구동 시스템의 역사적 발전 과정(Historical Evolution)을 이해하는 것이 중요하다. AGV(Automated Guided Vehicle)에서 AMR(Autonomous Mobile Robot)로 발전한 과정과 각각의 기술적 한계를 이해하면 현재의 구동 시스템이 왜 이러한 구조를 가지게 되었는지 이해할 수 있다.

그 다음에는 차동 구동(Differential Drive), 스티어 드라이브(Steer Drive), 메카넘 드라이브(Mecanum Drive), 옴니 드라이브(Omni Drive)의 특성과 차이점을 학습해야 한다. 각 구동 방식은 서로 다른 장점과 단점을 가지고 있으며 적용 분야도 다르다.

이후 적재중량 기반 분류(Payload Classification)를 수행한다. 설계 대상 로봇이 어느 정도의 적재 능력을 요구하는지 정의하면 후보 구동 시스템을 크게 줄일 수 있다. 이는 구동 시스템 선택 과정의 첫 번째 필터 역할을 한다.

다음 단계에서는 위치 정밀도(Positioning Accuracy)를 평가한다. 적재중량만으로는 적절한 구동 방식을 결정할 수 없기 때문이다. 정밀도와 반복 정밀도 요구사항을 정의함으로써 후보 시스템을 더욱 구체화할 수 있다.

이후 환경 조건(Environmental Conditions)을 분석해야 한다. 실내 창고(Indoor Warehouse), 반도체 클린룸(Cleanroom), 병원(Hospital), 실외 물류 야드(Outdoor Logistics Yard), 농업 환경(Agricultural Environment), 중공업 시설(Heavy Industry Facility)은 각각 다른 구동 시스템 요구사항을 가진다.

안전 요구사항(Safety Requirement)도 반드시 검토해야 한다. 사람과 협업하는 환경에서는 기능 안전(Functional Safety), 비상 정지(Emergency Stop), 충돌 회피(Collision Avoidance), 안전 제동(Safe Braking)이 필수적이다.

본 매뉴얼은 특정 구동 방식을 절대적으로 우수하다고 판단하지 않는다. 모든 구동 시스템은 비용(Cost), 복잡도(Complexity), 정밀도(Precision), 효율(Efficiency), 적재 능력(Payload Capacity), 유지보수성(Maintainability) 사이의 균형점에 존재한다. 따라서 가장 중요한 것은 특정 응용 분야에 가장 적합한 구동 방식을 선택하는 것이다.

특히 힐스로보틱스(Hills Robotics)와 같이 50kg, 100kg, 250kg, 500kg, 1000kg, 1500kg급 플랫폼을 동시에 개발하는 경우에는 플랫폼 공통화(Platform Standardization)와 모듈화(Modularization)가 매우 중요하다. 모터, 감속기, 제어기, 배터리, 소프트웨어를 최대한 공유함으로써 개발 비용을 줄이고 유지보수성을 향상시킬 수 있다.

결론적으로 본 매뉴얼은 단순한 기술 설명서가 아니라 의사결정 지원 프레임워크(Decision Support Framework)이다. 시스템 아키텍트(System Architect), 기구 설계자(Mechanical Engineer), 제어 엔지니어(Control Engineer), 프로젝트 매니저(Project Manager)가 공통된 기준으로 구동 시스템을 선택하고 설계할 수 있도록 지원하는 것이 본 매뉴얼의 궁극적인 목적이다.
