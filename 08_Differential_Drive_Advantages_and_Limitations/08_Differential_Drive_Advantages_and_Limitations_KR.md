## 01 Cost Advantages

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Cost is one of the most important factors when selecting a drive system for an industrial Autonomous Mobile Robot (AMR). Although performance, positioning accuracy, payload capacity, and maneuverability are critical technical considerations, the final decision in many real-world projects is strongly influenced by total ownership cost. In many logistics, manufacturing, warehouse, and inspection applications, differential drive systems continue to dominate the market largely because they provide the lowest cost solution while delivering sufficient performance for most operational requirements.

A differential drive robot uses two independently driven wheels and one or more passive caster wheels. This architecture is mechanically simple, electrically efficient, and relatively easy to control. By contrast, steer drive systems require dedicated steering actuators, steering gearboxes, steering encoders, additional motor controllers, and sophisticated synchronization algorithms. As a result, the initial purchase cost and long-term maintenance cost of steer drive platforms are significantly higher.

The cost advantage of differential drive becomes especially apparent when developing robots in the payload range below approximately 500 kg. In this range, the additional precision and maneuverability provided by steer drive systems often do not justify the increased hardware and engineering costs. Consequently, many successful commercial AMRs utilize differential drive architectures because they offer the best balance between functionality and affordability.

From an engineering perspective, cost advantages originate from multiple sources. The mechanical structure is simpler, the number of actuators is lower, wiring complexity is reduced, software development effort is minimized, and maintenance requirements are easier to manage. These benefits accumulate throughout the entire product lifecycle, reducing both capital expenditure and operational expenditure.

The economic impact becomes even more significant when robots are deployed in fleets. A small difference in unit cost may be negligible for a single robot, but it becomes substantial when deploying dozens or hundreds of units. Therefore, understanding the cost advantages of differential drive systems is essential for selecting the most economically viable platform architecture.

---

### 1.1 Component Unit Price Comparison: Differential Drive vs Steer Drive

---

### 1.2 Maintenance Cost Comparison

---

비용(Cost)은 산업용 자율주행 모바일 로봇(Autonomous Mobile Robot, AMR)의 구동 방식을 선택할 때 가장 중요한 요소 중 하나이다. 물론 성능(Performance), 위치 정밀도(Positioning Accuracy), 적재 능력(Payload Capacity), 기동성(Maneuverability)도 중요한 기술적 요소이지만, 실제 산업 현장에서는 총 소유 비용(Total Cost of Ownership, TCO)이 최종 의사결정에 큰 영향을 미친다.

차동 구동(Differential Drive)은 대부분의 물류, 제조, 창고, 검사 분야에서 여전히 가장 널리 사용되는 방식이다. 이는 충분한 성능을 제공하면서도 가장 낮은 비용으로 구현할 수 있기 때문이다.

차동 구동 로봇은 두 개의 구동 바퀴(Drive Wheel)와 하나 이상의 캐스터 휠(Caster Wheel)로 구성된다. 구조가 단순하고 전기 시스템이 간결하며 제어 알고리즘도 비교적 쉽다. 반면 조향 구동(Steer Drive)은 조향 액추에이터(Steering Actuator), 조향 감속기(Steering Gearbox), 조향 엔코더(Steering Encoder), 추가 모터 드라이버(Motor Driver), 그리고 복잡한 동기화 제어(Synchronization Control)를 필요로 한다. 따라서 초기 구매 비용과 유지보수 비용 모두 차동 구동보다 높아진다.

특히 500kg 이하의 AMR에서는 이러한 차이가 더욱 두드러진다. 이 구간에서는 조향 구동이 제공하는 높은 정밀도와 기동성이 추가 비용을 정당화하기 어려운 경우가 많다. 따라서 많은 상용 AMR이 차동 구동 방식을 채택하고 있다.

비용 우위는 단순히 부품 수가 적다는 의미만이 아니다. 기계 구조(Mechanical Structure), 전기 구조(Electrical Architecture), 소프트웨어 개발 비용(Software Development Cost), 유지보수 비용(Maintenance Cost)까지 전체 수명주기(Lifecycle)에 걸쳐 비용 절감 효과를 제공한다.

특히 플릿(Fleet) 단위로 수십 대 또는 수백 대를 운영하는 경우에는 로봇 한 대당 몇 백만 원 수준의 비용 차이가 전체 프로젝트에서는 수억 원 이상의 차이로 확대될 수 있다. 따라서 구동 방식 선택 시 비용 구조를 정확히 이해하는 것은 매우 중요하다.

### 1.1 부품 단가 비교(Component Unit Price Comparison: Differential Drive vs Steer Drive)

---

차동 구동이 가지는 가장 직접적인 비용상의 장점은 하드웨어 구성 요소(Hardware Components)를 비교해 보면 쉽게 확인할 수 있다. 차동 구동은 최소한의 능동 부품(Active Component)만 사용하여 원하는 이동 성능을 구현하도록 설계되었다.

일반적인 차동 구동 로봇은 두 개의 구동 모터(Drive Motor), 두 개의 모터 드라이버(Motor Driver), 두 개의 엔코더(Encoder), 그리고 하나 이상의 수동 캐스터 휠(Passive Caster Wheel)만으로 구성된다. 방향 전환은 좌우 바퀴의 속도 차이를 이용해 구현되므로 별도의 조향 장치가 필요하지 않다.

반면 조향 구동 로봇은 각 바퀴에 대해 구동 기능과 조향 기능을 모두 갖추어야 한다. 예를 들어 4WS(4-Wheel Steering) 플랫폼에서는 각 바퀴마다 구동 모터, 조향 모터, 조향 감속기, 조향 엔코더, 구동 엔코더, 제어 회로가 필요하다.

즉, 단순히 모터 개수만 비교해도 차동 구동은 2개, 조향 구동은 8개 수준까지 증가할 수 있다.

모터 비용만 보더라도 큰 차이가 발생한다. 차동 구동은 고출력 모터 2개만 사용하면 되지만, 조향 구동은 구동 모터 4개와 조향 모터 4개가 필요하다. 조향 모터가 상대적으로 작다고 하더라도 전체 액추에이터 비용은 크게 증가한다.

모터 드라이버 역시 동일한 차이를 보인다. 차동 구동은 보통 2축 제어만 필요하지만, 조향 구동은 8축 이상의 제어 채널이 필요하다. 이는 제어기 비용 증가뿐 아니라 전원 분배(Power Distribution), 배선(Wiring), 통신 구조(Communication Architecture) 복잡성 증가로 이어진다.

기계 구조에서도 비용 차이는 상당하다. 차동 구동은 단순한 바퀴와 감속기 구조만 필요하지만, 조향 구동은 정밀 베어링(Bearing), 조향 기어박스, 회전 하우징(Rotary Housing), 고강성 구조물 등을 필요로 한다.

엔코더 비용도 증가한다. 차동 구동은 바퀴 회전량 측정만 수행하면 되지만, 조향 구동은 조향 각도 측정을 위한 절대형 엔코더(Absolute Encoder)가 추가적으로 필요하다.

전기 시스템(Electrical System) 역시 복잡해진다. 추가 모터와 센서 때문에 배선, 커넥터(Connector), 통신 노드(Communication Node), 보호 회로(Protection Circuit)의 수가 증가한다.

소프트웨어 개발 비용도 무시할 수 없다. 차동 구동은 ROS2와 다양한 산업용 제어 프레임워크에서 이미 성숙한 라이브러리가 제공된다. 반면 조향 구동은 복잡한 역기구학(Inverse Kinematics), 조향 동기화 알고리즘(Steering Synchronization Algorithm), 캘리브레이션(Calibration), 안전 기능(Safety Function) 등을 추가로 개발해야 한다.

전체 시스템 관점에서 보면 동일한 적재 능력을 가진 로봇이라도 차동 구동 플랫폼은 조향 구동 대비 약 30\~60% 정도 낮은 제조 원가를 가지는 경우가 많다. 정확한 수치는 적재 중량과 성능 요구사항에 따라 달라지지만 비용 우위는 거의 항상 존재한다.

따라서 500kg 이하의 경량 및 중형 AMR에서는 부품 단가 측면에서 차동 구동이 매우 강력한 경쟁력을 가진다.

### 1.2 유지보수 비용 비교(Maintenance Cost Comparison)

초기 구매 비용도 중요하지만 실제 산업 현장에서는 유지보수 비용(Maintenance Cost)이 더욱 중요할 수 있다. AMR은 일반적으로 5년에서 10년 이상 운영되기 때문에 전체 수명주기 비용은 초기 구매 비용보다 훨씬 커지는 경우가 많다.

이러한 측면에서 차동 구동은 조향 구동보다 매우 큰 유지보수상의 장점을 가진다.

가장 큰 이유는 기계 구조의 단순성(Mechanical Simplicity)이다. 차동 구동은 움직이는 부품 수가 적고 능동 부품도 최소화되어 있다. 구동 모터 두 개만 관리하면 되기 때문에 고장 발생 가능성이 상대적으로 낮다.

캐스터 휠은 대부분 수동 구조이므로 주기적인 점검과 교체만 수행하면 된다. 반면 조향 구동은 조향 모터, 조향 감속기, 조향 베어링, 절대형 엔코더, 케이블 관리 장치(Cable Management Mechanism) 등을 지속적으로 관리해야 한다.

마모(Wear)와 관련된 유지보수도 차이가 크다. 조향 감속기는 지속적으로 회전하며 백래시(Backlash), 윤활유 열화(Lubrication Degradation), 베어링 마모(Bearing Wear)가 발생한다. 차동 구동은 이러한 구성 요소 자체가 존재하지 않는다.

전기 시스템 유지보수도 더 간단하다. 모터와 센서 수가 적기 때문에 케이블, 커넥터, 통신 노드의 수도 적다. 따라서 문제 발생 시 진단(Diagnostics)과 수리가 훨씬 쉽다.

캘리브레이션 비용도 중요한 차이를 만든다. 차동 구동은 주기적으로 바퀴 직경 보정과 엔코더 스케일 팩터 정도만 확인하면 된다. 그러나 조향 구동은 조향 각도 보정, 휠 정렬(Wheel Alignment), 엔코더 동기화, 다축 협조 제어(Multi-Axis Coordination) 검증 등이 필요하다.

예비 부품(Spare Parts) 관리 비용도 차이가 크다. 차동 구동은 구동 모터, 엔코더, 드라이버, 캐스터 휠 정도만 보유하면 되지만, 조향 구동은 추가적으로 조향 모터, 조향 감속기, 조향 엔코더, 베어링 모듈 등을 보유해야 한다.

신뢰성(Reliability) 측면에서도 차동 구동이 유리한 경우가 많다. 일반적으로 부품 수가 적을수록 MTBF(Mean Time Between Failures, 평균 고장 간격)는 증가한다. 추가적인 모터, 센서, 통신 노드, 커넥터는 모두 새로운 고장 가능성을 의미하기 때문이다.

다운타임(Downtime) 비용 역시 중요하다. 조향 모듈이 고장나면 분해, 교체, 재조립, 재보정 과정을 거쳐야 하므로 복구 시간이 길어진다. 반면 차동 구동은 구조가 단순하여 수리가 훨씬 빠르게 진행될 수 있다.

이러한 차이는 플릿 규모가 커질수록 더욱 확대된다. 예를 들어 100대의 로봇을 운영하는 경우, 로봇 한 대당 연간 유지보수 비용이 조금만 차이 나더라도 전체 운영 비용은 수천만 원에서 수억 원 수준까지 차이가 발생할 수 있다.

결국 500kg 이하 물류 AMR이나 일반 산업용 AMR에서는 차동 구동이 가장 낮은 총 소유 비용(TCO)을 제공하는 경우가 많다. 낮은 초기 비용, 단순한 구조, 적은 유지보수 인력, 높은 신뢰성, 적은 예비 부품 재고는 모두 차동 구동이 산업 현장에서 오랫동안 주류 구조로 사용되는 이유이다.

따라서 차동 구동의 경제적 장점은 단순히 구매 시점의 가격 경쟁력에만 있는 것이 아니라, 로봇의 전체 수명주기에 걸쳐 지속적으로 비용 절감 효과를 제공한다는 점에 있다.

## 02 Control Simplicity

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Control simplicity is one of the most significant advantages of differential drive mobile robots. While many modern robotic platforms pursue increasingly sophisticated steering mechanisms, multi-axis coordination systems, and advanced vehicle dynamics control strategies, differential drive systems continue to dominate large segments of the industrial AMR market because of their straightforward control architecture. In many practical applications, simplicity is not a limitation but rather a strategic advantage that reduces development cost, improves reliability, shortens deployment time, and simplifies long-term maintenance.

A differential drive robot achieves motion using only two independently controlled drive wheels. By varying the rotational speeds of the left and right wheels, the robot can move forward, backward, rotate in place, and follow curved trajectories. This simple principle eliminates the need for steering actuators, steering synchronization algorithms, wheel alignment calibration, and complex vehicle kinematic models.

The simplicity of the control system affects every layer of the robot architecture. Motion planning becomes easier because the kinematic model is straightforward. Velocity control requires only two wheel speed commands. Odometry calculations are relatively simple and computationally efficient. Diagnostics and troubleshooting procedures are also easier because fewer interacting subsystems exist.

In industrial environments, simplicity often translates directly into reliability. A system with fewer components and fewer control loops generally contains fewer potential failure points. This characteristic is especially valuable in manufacturing facilities where robot downtime can directly impact production throughput and operational efficiency.

Control simplicity also reduces engineering effort. Development teams can focus on navigation, perception, fleet management, and application-specific functionality rather than spending significant resources on complex vehicle control algorithms. For many logistics, warehouse, inspection, and material-handling applications, the performance provided by a differential drive system is entirely sufficient.

As a result, differential drive remains one of the most widely adopted drive architectures in industrial robotics, not because it is technologically limited, but because it often provides the most practical balance between functionality, cost, reliability, and implementation complexity.

---

### 2.1 Conditions Where Simple Controllers Suffice

---

### 2.2 Ease of ROS2 Implementation

---

제어 단순성(Control Simplicity)은 차동 구동(Differential Drive) 모바일 로봇이 가지는 가장 큰 장점 중 하나이다. 최근의 로봇 플랫폼들은 더욱 복잡한 조향 메커니즘(Steering Mechanism), 다축 협조 제어(Multi-Axis Coordination), 고급 차량 동역학 제어(Vehicle Dynamics Control)를 적용하고 있지만, 산업용 AMR 시장에서는 여전히 차동 구동 방식이 가장 널리 사용되고 있다. 이는 단순성이 기술적 한계가 아니라 오히려 개발 비용 절감, 신뢰성 향상, 개발 기간 단축, 유지보수 용이성이라는 강력한 장점으로 작용하기 때문이다.

차동 구동 로봇은 두 개의 독립 구동 바퀴(Drive Wheel)만으로 이동을 구현한다. 좌우 바퀴의 회전 속도를 다르게 제어함으로써 직진, 후진, 제자리 회전(Zero Radius Turn), 곡선 주행을 모두 수행할 수 있다. 이러한 구조는 별도의 조향 액추에이터(Steering Actuator), 조향 동기화 알고리즘(Steering Synchronization Algorithm), 휠 정렬(Wheel Alignment), 복잡한 차량 운동학(Vehicle Kinematics)을 필요로 하지 않는다.

제어 구조의 단순성은 로봇 전체 아키텍처에 영향을 미친다. 경로 계획(Path Planning)은 단순해지고, 속도 제어는 좌우 바퀴 속도만 제어하면 되며, 오도메트리(Odometry) 계산도 비교적 간단하다. 또한 진단(Diagnostics)과 문제 해결(Troubleshooting) 과정도 훨씬 쉬워진다.

산업 현장에서 단순성은 곧 신뢰성(Reliability)으로 이어진다. 구성 요소 수가 적고 제어 루프(Control Loop)가 적을수록 잠재적인 고장 지점(Failure Point)도 감소한다. 이는 생산 설비의 가동률(Uptime)이 중요한 제조 환경에서 매우 큰 장점이다.

또한 개발 조직 입장에서도 제어 단순성은 중요한 의미를 가진다. 엔지니어들은 복잡한 차량 제어 알고리즘 개발보다 내비게이션(Navigation), 인지(Perception), 플릿 관리(Fleet Management), 응용 기능(Application Function)에 더 많은 자원을 투입할 수 있다.

결과적으로 차동 구동은 기술적으로 부족해서가 아니라 기능성(Functionality), 비용(Cost), 신뢰성(Reliability), 개발 난이도(Implementation Complexity) 사이에서 가장 현실적인 균형을 제공하기 때문에 산업용 AMR 분야에서 가장 널리 사용되는 구조 중 하나가 되었다.

### 2.1 단순한 제어기로 충분한 조건(Conditions Where Simple Controllers Suffice)

---

차동 구동 시스템이 오랫동안 널리 사용되는 가장 큰 이유 중 하나는 많은 산업 현장에서 복잡한 제어 알고리즘이 실제로 필요하지 않기 때문이다. 상당수의 산업용 응용에서는 비교적 단순한 제어기(Simple Controller)만으로도 요구 성능을 충분히 만족시킬 수 있다.

대부분의 실내 산업용 AMR은 0.5m/s에서 2.0m/s 수준의 비교적 낮은 속도로 운행된다. 이러한 속도 영역에서는 차량 동역학(Vehicle Dynamics)이 비교적 안정적이며 관성(Inertia)의 영향도 제한적이다. 따라서 복잡한 모델 기반 제어(Model-Based Control) 없이도 안정적인 주행이 가능하다.

창고 물류(Warehouse Logistics)는 대표적인 예이다. AMR은 팔레트(Pallet), 컨테이너(Container), 자재(Material)를 정해진 위치 사이에서 운반한다. 바닥은 대부분 평탄하고, 이동 경로도 명확하게 정의되어 있다. 이러한 환경에서는 PI 속도 제어기(PI Speed Controller)와 PID 위치 제어기(PID Position Controller)만으로도 매우 우수한 성능을 얻을 수 있다.

산업용 검사 로봇(Inspection Robot) 역시 마찬가지이다. 검사 작업은 일반적으로 고속 주행보다는 정밀한 위치 제어와 반복 정밀도(Repeatability)를 요구한다. 로봇은 검사 지점까지 이동하고 정지한 후 측정을 수행한다. 따라서 복잡한 적응 제어(Adaptive Control)나 예측 제어(Predictive Control)가 필요하지 않은 경우가 많다.

저속 주행(Low-Speed Operation)은 제어를 더욱 단순하게 만든다. 속도가 낮으면 바퀴 슬립(Wheel Slip)이 감소하고 차량 동특성도 완만해진다. 결과적으로 안정성 여유(Stability Margin)가 증가하여 고급 제어 알고리즘 없이도 충분한 성능을 확보할 수 있다.

적재 하중(Payload)이 일정한 경우에도 단순 제어기가 효과적이다. 적재 상태가 크게 변하지 않으면 차량 동특성 역시 거의 일정하게 유지된다. 이러한 경우에는 고정 게인(Fixed Gain)을 사용하는 PI 또는 PID 제어기만으로도 전체 운행 범위를 안정적으로 제어할 수 있다.

실내 환경의 예측 가능성(Predictability)도 중요한 요소이다. 공장과 물류센터는 일반적으로 평탄한 바닥, 제한된 경사도, 일정한 조명 조건을 제공한다. 자동차 자율주행 차량처럼 다양한 노면 상태, 기상 조건, 급격한 환경 변화에 대응할 필요가 없기 때문에 제어 구조를 단순하게 유지할 수 있다.

단순 제어기는 시운전(Commissioning) 과정에서도 장점을 제공한다. PI 또는 PID 제어기는 대부분의 엔지니어와 유지보수 인력이 익숙하게 다룰 수 있다. 튜닝(Tuning)이 쉽고 시스템 거동을 직관적으로 이해할 수 있기 때문에 문제 발생 시 원인 분석도 간단하다.

계산 효율성(Computational Efficiency) 역시 큰 장점이다. 단순 제어기는 프로세서 부하가 매우 낮다. 따라서 저가형 임베디드 프로세서(Embedded Processor)에서도 충분히 실행할 수 있으며, 남는 연산 자원을 인공지능(AI), 비전(Vision), SLAM, 통신(Communication)에 활용할 수 있다.

심지어 1톤 이상의 고중량 산업용 AMR에서도 고전 제어(Classical Control)가 여전히 사용되는 경우가 많다. 적재 하중이 증가하더라도 차량 구조가 안정적이라면 PI 및 PID 제어만으로도 충분한 성능을 확보할 수 있기 때문이다.

물론 고속 자율주행 차량, 고기동 조향 구동 플랫폼(Steer Drive Platform), 오프로드 자율주행 시스템(Off-Road Autonomous System)과 같은 분야에서는 MPC(Model Predictive Control), 적응 제어, 비선형 제어(Nonlinear Control)가 필요할 수 있다.

그러나 대부분의 산업용 차동 구동 AMR에서는 단순 제어기가 성능과 비용 측면에서 가장 합리적인 선택이 된다.

### 2.2 ROS2 구현 용이성(Ease of ROS2 Implementation)

차동 구동 시스템의 또 다른 중요한 장점은 ROS2(Robot Operating System 2) 환경에서 구현하기 매우 쉽다는 점이다. ROS2는 현재 로봇 산업에서 가장 널리 사용되는 소프트웨어 프레임워크로, 통신(Middleware), 하드웨어 추상화(Hardware Abstraction), 내비게이션(Navigation), 센서 통합(Sensor Integration) 기능을 제공한다.

차동 구동 로봇은 ROS2와 매우 잘 맞는다. 실제로 ROS와 ROS2 생태계의 상당수 패키지는 차동 구동 플랫폼을 기준으로 개발되었다고 해도 과언이 아니다.

차동 구동 제어는 기본적으로 두 개의 명령만 필요하다. 좌측 바퀴 속도(Left Wheel Velocity)와 우측 바퀴 속도(Right Wheel Velocity)이다. ROS2는 이러한 구조를 직접 지원하는 표준 메시지(Message)와 인터페이스(Interface)를 제공한다.

대표적으로 \`geometry_msgs/Twist\` 메시지는 선속도(Linear Velocity)와 각속도(Angular Velocity)를 정의하며, 이는 차동 구동 로봇의 기본 제어 입력으로 사용된다.

차량 속도를 바퀴 속도로 변환하는 과정도 매우 단순하다. 차동 구동 운동학(Differential Drive Kinematics)은 휠 반경(Wheel Radius)과 휠베이스(Wheelbase)만 알면 쉽게 계산할 수 있다.

ROS2는 이러한 기능을 위해 \`ros2_control\` 프레임워크를 제공한다. 특히 \`differential_drive_controller\` 패키지는 속도 제어, 엔코더 통합, 오도메트리 계산, 상태 정보 발행(Publishing) 기능을 기본적으로 지원한다.

따라서 개발자는 복잡한 소프트웨어를 새로 작성하지 않고도 기본적인 차동 구동 시스템을 빠르게 구축할 수 있다.

오도메트리 구현도 간단하다. 좌우 엔코더 데이터를 이용하여 위치와 자세(Pose)를 계산하고, ROS2 표준 오도메트리 메시지(Odometry Message)와 TF(Transformation) 시스템을 통해 다른 노드(Node)와 공유할 수 있다.

Navigation2(Nav2) 프레임워크 역시 차동 구동에 최적화되어 있다. Nav2는 경로 계획(Path Planning), 경로 추종(Path Following), 장애물 회피(Obstacle Avoidance), 행동 트리(Behavior Tree), 웨이포인트 내비게이션(Waypoint Navigation) 등을 제공한다.

차동 구동 AMR은 대부분의 Nav2 기능을 별도의 수정 없이 바로 사용할 수 있다.

시뮬레이션(Simulation) 환경에서도 큰 장점이 있다. Gazebo, Ignition Gazebo, NVIDIA Isaac Sim 등 대부분의 로봇 시뮬레이터는 기본적으로 차동 구동 플러그인(Differential Drive Plugin)을 제공한다.

따라서 실제 하드웨어를 제작하기 전에 제어 알고리즘과 내비게이션 성능을 충분히 검증할 수 있다.

하드웨어 통합(Hardware Integration)도 상대적으로 쉽다. 대부분의 산업용 모터 드라이버는 속도 제어 인터페이스를 제공하며, 이는 차동 구동 구조와 자연스럽게 연결된다. ROS2 하드웨어 추상화 계층을 사용하면 엔코더, IMU, 모터 드라이버, 안전 컨트롤러(Safety Controller)를 표준 방식으로 통합할 수 있다.

또한 커뮤니티 지원(Community Support)이 매우 풍부하다. 차동 구동은 전 세계적으로 가장 많이 사용되는 로봇 플랫폼이기 때문에 튜토리얼(Tutorial), 오픈소스(Open Source), 예제 프로젝트(Example Project), 기술 문서(Document)가 매우 많다.

이로 인해 신규 개발자 교육과 기술 전수(Knowledge Transfer)도 용이하다.

반면 조향 구동은 전용 운동학 모델, 조향 동기화 알고리즘, 캘리브레이션 절차, 맞춤형 ROS2 컨트롤러를 추가로 개발해야 하는 경우가 많다. 따라서 소프트웨어 복잡성이 크게 증가한다.

결과적으로 차동 구동은 단순한 기계 구조뿐 아니라 ROS2 기반 소프트웨어 개발 측면에서도 매우 큰 장점을 가진다. 단순한 운동학, 성숙한 ROS2 지원, 풍부한 오픈소스 생태계, 쉬운 하드웨어 통합 덕분에 개발 기간과 비용을 크게 줄일 수 있다.

이러한 이유로 현재도 많은 산업용 AMR 제조사들은 차동 구동을 단순한 저가 솔루션이 아니라 가장 효율적인 ROS2 기반 로봇 플랫폼 아키텍처로 선택하고 있다.

## 03 Skid Effects

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Skid effects are among the most important phenomena affecting the performance, efficiency, and durability of differential drive mobile robots. While differential drive systems are widely appreciated for their mechanical simplicity and low cost, they inherently generate wheel slip and skidding during certain maneuvers. Unlike steer-drive vehicles, which align wheel orientation with the direction of travel, differential drive robots achieve turning motion by creating a velocity difference between the left and right wheels. This method inevitably introduces lateral tire forces and localized slip conditions, particularly during rotational movements.

In industrial AMRs, skid effects influence several critical performance metrics, including odometry accuracy, path-following precision, energy consumption, tire lifetime, drivetrain loading, and floor surface wear. The severity of skid effects depends on vehicle geometry, payload distribution, floor material, tire characteristics, operating speed, and motion control strategy.

During normal straight-line motion, wheel slip is typically minimal because both drive wheels rotate at nearly identical speeds and follow parallel trajectories. However, when the robot performs a turning maneuver, especially a zero-radius rotation, each wheel follows a different path. Since the wheels cannot freely align themselves with the turning direction, lateral forces develop between the tire and floor surface. These forces generate localized sliding motion known as skidding.

The consequences of skidding are not always negative. In fact, differential drive robots rely on controlled skidding to achieve turning motion. The challenge is not eliminating skid effects entirely but managing them effectively so that they do not significantly degrade performance or accelerate component wear.

The magnitude of skid effects varies considerably across applications. Lightweight indoor service robots operating at low speeds may experience negligible consequences, while heavy industrial AMRs carrying loads exceeding one ton can generate substantial tire stress and floor interaction forces during turning operations.

Modern robot designers therefore devote significant attention to skid analysis. Through proper wheel selection, tire material optimization, chassis design, motion planning, and control tuning, skid-related problems can be reduced without sacrificing maneuverability.

Understanding the mechanisms that cause wheel slip and tire wear is essential for designing reliable differential drive platforms. Effective skid management improves localization accuracy, extends component lifetime, reduces maintenance requirements, and enhances overall operational efficiency.

---

### 3.1 Slip Occurrence Condition Analysis

---

### 3.2 Tire Wear Patterns

---

스키드 효과(Skid Effects)는 차동 구동(Differential Drive) 모바일 로봇의 성능, 효율성, 내구성에 영향을 미치는 매우 중요한 현상이다. 차동 구동은 구조가 단순하고 비용이 낮다는 장점이 있지만, 회전 시 본질적으로 바퀴 슬립(Wheel Slip)과 스키딩(Skidding)을 발생시킨다. 조향 구동(Steer Drive) 차량은 바퀴 방향을 이동 방향에 맞추어 회전하지만, 차동 구동은 좌우 바퀴 속도 차이를 이용하여 방향을 바꾸기 때문에 회전 과정에서 필연적으로 횡방향 힘(Lateral Force)과 미끄러짐이 발생한다.

산업용 AMR에서 스키드 효과는 오도메트리 정확도(Odometry Accuracy), 경로 추종 성능(Path Following Performance), 에너지 소비(Energy Consumption), 타이어 수명(Tire Lifetime), 구동계 하중(Drivetrain Loading), 바닥 마모(Floor Wear) 등에 직접적인 영향을 미친다. 스키드의 크기는 차량 형상(Vehicle Geometry), 적재 하중(Payload), 바닥 재질(Floor Material), 타이어 특성(Tire Characteristics), 주행 속도(Speed), 제어 전략(Control Strategy)에 따라 달라진다.

직선 주행에서는 일반적으로 슬립이 거의 발생하지 않는다. 좌우 바퀴가 거의 동일한 속도로 회전하며 평행한 경로를 따라 이동하기 때문이다. 그러나 회전이 시작되면 상황이 달라진다. 특히 제자리 회전(Zero Radius Turn) 시에는 좌우 바퀴가 서로 다른 방향으로 움직이게 되며, 바퀴 방향은 고정되어 있기 때문에 이동 방향과 바퀴 방향이 일치하지 않는다. 이로 인해 타이어와 바닥 사이에서 횡방향 힘이 발생하고 일부 접촉면은 미끄러지게 된다.

흥미로운 점은 스키드가 반드시 나쁜 현상만은 아니라는 것이다. 차동 구동은 원래 스키딩을 이용해 회전하는 구조이다. 따라서 중요한 것은 스키드를 완전히 제거하는 것이 아니라 적절하게 관리하여 성능 저하와 마모 증가를 최소화하는 것이다.

스키드의 영향은 적용 분야에 따라 크게 달라진다. 소형 서비스 로봇은 낮은 속도와 낮은 하중 때문에 큰 문제가 발생하지 않을 수 있다. 반면 1톤 이상의 산업용 AMR은 회전 시 상당한 타이어 응력(Tire Stress)과 바닥 반력을 발생시킨다.

현대 AMR 설계에서는 스키드 분석을 매우 중요하게 다룬다. 적절한 휠 선정(Wheel Selection), 타이어 재질(Tire Material), 섀시 설계(Chassis Design), 경로 계획(Motion Planning), 제어 튜닝(Control Tuning)을 통해 스키드의 부정적 영향을 줄일 수 있다.

슬립과 타이어 마모가 어떻게 발생하는지를 이해하는 것은 신뢰성 높은 차동 구동 플랫폼을 설계하기 위한 필수 조건이다. 적절한 스키드 관리는 위치 정확도 향상, 부품 수명 연장, 유지보수 비용 절감, 운영 효율 향상으로 이어진다.

### 3.1 슬립 발생 조건 분석(Slip Occurrence Condition Analysis)

---

휠 슬립(Wheel Slip)은 바퀴 표면의 움직임과 실제 차량의 움직임이 일치하지 않을 때 발생한다. 일반적으로 슬립은 접지력 상실(Traction Loss)로 이해되지만, 실제로는 다양한 조건에서 발생하며 매우 작은 마이크로 슬립(Micro Slip)부터 심각한 미끄러짐까지 여러 형태로 나타난다.

차동 구동 로봇에서 가장 흔한 슬립 원인은 회전 동작(Rotational Motion)이다. 제자리 회전 시 좌우 바퀴는 반대 방향으로 회전한다. 하지만 바퀴 방향은 고정되어 있기 때문에 실제 회전 궤적과 바퀴 방향이 일치하지 않는다. 결과적으로 타이어는 횡방향 변형(Lateral Deformation)을 일으키고 일부 영역은 바닥 위를 미끄러지게 된다.

슬립의 크기는 타이어와 바닥 사이의 마찰계수(Coefficient of Friction)에 크게 의존한다. 마찰력이 높은 바닥에서는 더 큰 횡방향 힘이 발생하고, 타이어 내부에 더 많은 응력이 축적된다. 반면 마찰력이 낮은 바닥에서는 쉽게 미끄러지지만 제어성이 떨어질 수 있다.

차량 중량(Vehicle Weight)도 중요한 요소이다. 적재 하중이 증가하면 타이어에 작용하는 수직 하중(Normal Force)이 증가한다. 이에 따라 마찰력도 증가하며 회전 시 더 큰 타이어 변형과 응력이 발생한다. 따라서 고중량 AMR은 경량 로봇보다 스키드와 관련된 문제가 더 크게 나타난다.

가속과 감속도 슬립을 유발한다. 모터 토크(Motor Torque)가 접지력보다 커지면 바퀴는 회전하지만 차량은 그만큼 움직이지 못한다. 이는 급가속, 급제동, 또는 미끄러운 바닥에서 자주 발생한다.

바닥 조건(Floor Condition) 역시 매우 중요하다. 광택 콘크리트(Polished Concrete), 에폭시 바닥(Epoxy Floor), 금속판(Metal Plate), 세라믹 타일(Ceramic Tile), 젖은 바닥(Wet Surface)은 모두 다른 마찰 특성을 가진다. 동일한 로봇이라도 바닥 재질에 따라 전혀 다른 슬립 특성을 보일 수 있다.

바닥의 요철(Uneven Floor)도 영향을 준다. 확장 조인트(Expansion Joint), 케이블 덮개(Cable Protector), 작은 이물질(Debris)만으로도 바퀴 하중이 순간적으로 변화할 수 있다. 이 경우 한쪽 바퀴만 슬립이 발생하여 방향 오차(Heading Error)와 오도메트리 오차(Odometry Drift)가 증가한다.

적재 하중 분포(Payload Distribution) 역시 중요하다. 이상적으로는 좌우 바퀴에 동일한 하중이 분배되어야 한다. 그러나 한쪽에 무게가 집중되면 좌우 바퀴의 접지 조건이 달라지고 슬립 특성도 달라진다. 결과적으로 경로 오차가 증가할 수 있다.

타이어 재질(Tire Compound)도 슬립 발생에 영향을 준다. 부드러운 고무는 높은 접지력을 제공하지만 회전 시 더 큰 변형을 발생시킨다. 반면 단단한 재질은 변형이 적지만 진동이 증가하고 접지력이 감소할 수 있다.

제어 전략(Control Strategy)도 중요한 요소이다. 급격한 속도 변화나 높은 가속도를 명령하는 제어기는 슬립 발생 확률을 높인다. 반대로 저크 제한(Jerk Limiting), 부드러운 가속도 프로파일(Smooth Acceleration Profile), 적응형 속도 제어(Adaptive Velocity Control)는 슬립을 줄일 수 있다.

최신 산업용 AMR은 IMU와 엔코더 데이터를 비교하여 슬립을 감지하는 경우가 많다. 이러한 센서 융합(Sensor Fusion)을 통해 슬립 발생 여부를 판단하고 오도메트리 보정(Odometry Compensation)에 활용한다.

슬립 발생 조건을 정확히 이해하는 것은 매우 중요하다. 슬립은 위치 정확도, 경로 추종 성능, 에너지 소비, 타이어 수명에 직접적인 영향을 미치기 때문이다. 적절한 설계와 제어를 통해 불필요한 슬립을 줄이면서도 차동 구동의 우수한 기동성을 유지할 수 있다.

### 3.2 타이어 마모 패턴(Tire Wear Patterns)

타이어 마모(Tire Wear)는 바퀴와 바닥 사이의 반복적인 접촉에 의해 발생하며, 차동 구동 모바일 로봇에서 가장 중요한 유지보수 항목 중 하나이다. 차동 구동은 회전 시 의도적으로 스키딩을 발생시키기 때문에 일반 자동차와는 다른 마모 특성을 가진다.

직선 주행에서는 마모가 비교적 균일하게 발생한다. 바퀴는 거의 순수 구름 운동(Pure Rolling Motion)을 수행하며 마찰에 의한 마모가 천천히 진행된다.

그러나 회전 시에는 상황이 달라진다. 회전 과정에서 타이어 접촉면(Contact Patch)에 횡방향 힘이 발생하고 일부 영역은 바닥과 상대 운동을 하게 된다. 이로 인해 국부적인 마찰과 마모가 발생한다.

차동 구동 로봇에서 가장 흔한 마모 형태는 가장자리 마모(Edge Wear)이다. 회전 시 타이어 외곽 부분이 중앙부보다 더 큰 횡방향 응력을 받기 때문이다. 시간이 지나면 타이어 단면 형상이 변형되며 접지 특성도 변화하게 된다.

또 다른 특징은 비대칭 마모(Asymmetric Wear)이다. 적재 하중이 불균형하거나 특정 방향으로 회전하는 횟수가 많을 경우 좌우 타이어의 마모 속도가 달라질 수 있다. 이는 결국 바퀴 직경 차이(Wheel Diameter Difference)를 유발하고 오도메트리 정확도를 저하시킨다.

회전 빈도가 높은 환경에서는 마모 속도가 크게 증가한다. 좁은 통로(Narrow Aisle), 밀집 창고(Dense Warehouse), 반복 검사 환경에서는 하루 수백 회 이상의 회전이 발생할 수 있으며, 타이어 교체 주기(Tire Replacement Interval)가 매우 중요한 유지보수 요소가 된다.

바닥 상태도 마모에 직접적인 영향을 준다. 거친 콘크리트는 부드러운 에폭시 바닥보다 훨씬 큰 마모를 발생시킨다. 또한 금속 분진(Metal Shavings), 모래(Sand), 먼지(Dust) 등의 이물질은 마모를 가속화한다.

차량 중량 역시 매우 중요하다. 적재 하중이 증가할수록 접촉 압력(Contact Pressure)이 증가한다. 따라서 1톤 이상의 산업용 AMR은 소형 서비스 로봇보다 훨씬 빠른 타이어 마모를 경험하게 된다.

타이어 재질은 마모 특성과 접지 성능을 동시에 결정한다. 부드러운 재질은 높은 접지력을 제공하지만 빠르게 마모된다. 단단한 재질은 수명이 길지만 접지력이 낮고 진동 전달이 증가한다. 따라서 응용 분야에 따라 적절한 타이어 재질을 선택해야 한다.

온도(Temperature)도 마모에 영향을 준다. 장시간 운행 시 타이어 내부 온도가 상승하며 고무 특성이 변화한다. 이는 노화(Aging)를 가속화하고 마찰 특성에도 영향을 미친다.

산업 현장에서는 정기적인 타이어 점검(Tire Inspection)이 매우 중요하다. 타이어 직경, 두께, 마모 균형 상태를 측정하면 성능 저하를 사전에 발견할 수 있다. 최근에는 예측 유지보수(Predictive Maintenance)를 통해 타이어 상태를 자동으로 추정하는 시스템도 등장하고 있다.

타이어 마모는 단순히 유지보수 비용 문제에만 그치지 않는다. 바퀴 직경 변화는 오도메트리 계산에 직접적인 영향을 미친다. 따라서 마모가 진행될수록 위치 오차가 증가하고 경로 추종 성능도 저하될 수 있다.

결과적으로 산업용 AMR에서 타이어 마모 관리는 전체 시스템 최적화의 중요한 부분이다. 적절한 타이어 선정, 균형 잡힌 하중 분배, 부드러운 제어 전략, 정기적인 유지보수를 통해 타이어 수명을 연장하고 안정적인 내비게이션 성능을 유지할 수 있다. 차동 구동 AMR이 점점 더 높은 하중과 복잡한 환경에서 사용됨에 따라 타이어 마모와 스키드 특성에 대한 이해는 더욱 중요해지고 있다.

## 04 Precision Limitations

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Precision is one of the most frequently discussed topics when comparing differential drive and steer drive mobile robots. While differential drive systems offer significant advantages in cost, simplicity, reliability, and ease of implementation, they also possess inherent limitations in positioning accuracy due to their kinematic structure. These limitations become increasingly important when robots are required to perform precision docking, automated charging, machine loading, robotic handoff operations, or industrial inspection tasks where positioning errors directly affect process quality.

The fundamental challenge arises from the way differential drive robots generate motion. Steering is achieved by controlling speed differences between the left and right wheels rather than by physically aligning wheel orientation with the intended direction of travel. Consequently, turning maneuvers inevitably introduce wheel slip, tire deformation, and odometry drift. These effects accumulate over time and influence final positioning accuracy.

In many logistics applications, positioning errors of several centimeters are entirely acceptable. However, industrial automation systems often require repeatable docking accuracy within a few centimeters or even millimeters. Under such conditions, understanding the precision limitations of differential drive systems becomes essential for determining whether additional sensors, localization systems, or mechanical guidance mechanisms are required.

It is important to recognize that positioning precision is not determined solely by the drive mechanism. Sensor quality, localization architecture, control algorithms, floor conditions, payload distribution, mechanical tolerances, and environmental characteristics all contribute to final docking performance. A well-designed differential drive robot equipped with advanced localization systems can often outperform a poorly designed steer-drive platform.

Nevertheless, drive architecture establishes the fundamental limits of achievable performance. Steer drive systems generally experience less wheel slip during turning and can maintain more consistent geometric motion. Differential drive systems require additional compensation mechanisms to achieve comparable levels of precision.

Modern industrial AMRs therefore frequently combine differential drive architectures with sensor fusion, LiDAR localization, vision-based docking systems, fiducial markers, laser reflectors, and precision alignment techniques. These technologies significantly extend practical positioning performance beyond what encoder-based odometry alone can achieve.

The question is therefore not whether differential drive robots can achieve high precision, but rather under what conditions they can achieve it and how their ultimate limits compare with steer-drive alternatives.

---

### 4.1 Feasibility Study for Achieving ±20 mm Docking

---

### 4.2 Quantitative Precision Limit Comparison vs Steer Drive

---

정밀도(Precision)는 차동 구동(Differential Drive)과 조향 구동(Steer Drive)을 비교할 때 가장 많이 논의되는 주제 중 하나이다. 차동 구동은 비용(Cost), 구조 단순성(Simplicity), 신뢰성(Reliability), 구현 용이성(Ease of Implementation) 측면에서 큰 장점을 제공하지만, 운동학적 구조(Kinematic Structure)로 인해 본질적인 위치 정밀도 한계도 존재한다.

이러한 한계는 정밀 도킹(Precision Docking), 자동 충전(Auto Charging), 설비 로딩(Machine Loading), 로봇 간 인계(Robotic Handoff), 산업용 검사(Industrial Inspection)와 같이 위치 오차가 공정 품질에 직접적인 영향을 주는 응용 분야에서 더욱 중요하게 나타난다.

차동 구동 로봇은 좌우 바퀴 속도 차이를 이용하여 방향을 변경한다. 즉, 조향 휠처럼 바퀴 방향 자체를 변경하는 것이 아니라 속도 차이를 이용해 회전하기 때문에 회전 과정에서 바퀴 슬립(Wheel Slip), 타이어 변형(Tire Deformation), 오도메트리 드리프트(Odometry Drift)가 필연적으로 발생한다.

일반적인 물류 환경에서는 수 cm 수준의 위치 오차가 허용될 수 있다. 그러나 산업 자동화 환경에서는 수 mm에서 수 cm 수준의 반복 정밀도(Repeatability)가 요구되는 경우가 많다. 이때 차동 구동의 정밀도 한계를 정확하게 이해하고 추가 센서나 보정 기술이 필요한지 판단해야 한다.

중요한 점은 위치 정밀도가 구동 방식만으로 결정되는 것이 아니라는 점이다. 센서 품질(Sensor Quality), 위치 추정(Localization), 제어 알고리즘(Control Algorithm), 바닥 상태(Floor Condition), 적재 하중(Payload), 기계 공차(Mechanical Tolerance), 작업 환경(Environment) 등이 모두 영향을 미친다.

실제로 우수하게 설계된 차동 구동 로봇은 부실하게 설계된 조향 구동 로봇보다 더 높은 정밀도를 달성할 수도 있다.

그럼에도 불구하고 구동 구조는 성능의 근본적인 한계를 결정한다. 조향 구동은 회전 시 슬립이 적고 보다 이상적인 기하학적 운동(Geometric Motion)을 수행할 수 있기 때문에 기본적으로 더 높은 정밀도를 제공한다.

최근 산업용 AMR은 이러한 차동 구동의 한계를 극복하기 위해 LiDAR 기반 위치 추정(LiDAR Localization), 비전 도킹(Vision Docking), AprilTag, 레이저 리플렉터(Laser Reflector), IMU 융합(IMU Fusion), 센서 융합(Sensor Fusion) 등을 적극 활용하고 있다.

따라서 오늘날의 핵심 질문은 "차동 구동이 정밀 도킹이 가능한가?"가 아니라 "어떤 조건에서 가능한가?" 그리고 "조향 구동과 비교했을 때 어느 정도의 차이가 존재하는가?"에 가깝다.

### 4.1 ±20mm 도킹 달성 가능성 검토(Feasibility Study for Achieving ±20mm Docking)

---

±20mm 도킹 정밀도는 산업 자동화 분야에서 매우 자주 요구되는 기준이다. 자동 충전 스테이션(Automatic Charging Station), 설비 자동 로딩(Machine Tending), 로봇 간 자재 이송(Material Transfer), 이동형 검사 시스템(Mobile Inspection System) 등은 일반적으로 ±20mm 수준의 정렬 정확도를 요구한다.

처음에는 차동 구동 로봇으로 ±20mm 정밀도를 달성하는 것이 어려워 보일 수 있다. 바퀴 슬립, 엔코더 오차, 오도메트리 누적 오차가 지속적으로 발생하기 때문이다.

만약 로봇이 휠 엔코더(Wheel Encoder) 기반 오도메트리만 사용한다면 장거리 이동 후 ±20mm 이내의 정확도를 지속적으로 유지하는 것은 현실적으로 매우 어렵다. 바퀴 직경 오차, 바닥 요철, 작은 방향 오차만으로도 쉽게 ±20mm를 초과할 수 있다.

그러나 실제 산업용 AMR은 단순 오도메트리만 사용하지 않는다. 대부분 다단계 위치 추정(Multi-Layer Localization Architecture)을 적용한다.

첫 번째 계층은 전역 위치 추정(Global Localization)이다. LiDAR SLAM, 레이저 리플렉터, QR 코드, 비전 랜드마크 등을 사용하여 공장 전체에서 현재 위치를 추정한다. 일반적으로 ±20\~50mm 수준의 위치 정확도를 제공한다.

두 번째 계층은 지역 정밀 보정(Local Refinement)이다. 로봇이 목표 지점 근처에 접근하면 보다 정밀한 센서가 활성화된다. 레이저 스캐너(Laser Scanner), 비전 카메라(Vision Camera), Depth Camera, AprilTag, Reflector Target 등을 이용하여 상대 위치를 정밀하게 측정한다.

세 번째 계층은 최종 도킹 제어(Final Docking Control)이다. 마지막 수 cm 구간에서는 실시간 센서 피드백을 이용하여 위치를 지속적으로 수정한다. 이 단계에서는 절대 위치가 아니라 상대 위치(Relative Position)를 사용하기 때문에 훨씬 높은 정밀도를 달성할 수 있다.

실제 산업 현장 사례를 보면 적절한 센서와 위치 추정 시스템을 적용한 차동 구동 AMR은 ±20mm 도킹을 안정적으로 달성할 수 있다.

특히 공장 환경에서는 ±5mm\~±15mm 수준의 반복 정밀도를 달성하는 사례도 흔하게 존재한다.

성공 여부를 결정하는 주요 요소는 다음과 같다.

바닥 품질(Floor Quality)은 매우 중요하다. 바닥이 고르지 못하면 예측하기 어려운 바퀴 거동이 발생한다.

타이어 상태(Tire Condition)도 중요하다. 마모된 타이어는 유효 직경(Effective Diameter)을 변화시켜 정밀도를 저하시킨다.

적재 하중(Payload Variation)은 차량 동특성을 변화시켜 정지 위치 오차를 증가시킬 수 있다.

센서 설치 위치와 캘리브레이션 품질(Calibration Quality) 역시 매우 중요하다.

제어 전략(Control Strategy)도 큰 영향을 미친다. 부드러운 속도 프로파일(Smooth Velocity Profile), 저속 접근(Low-Speed Approach), 적응형 게인 제어(Adaptive Gain Control), 폐루프 도킹 제어(Closed-Loop Docking Control)는 모두 정밀도 향상에 기여한다.

특히 1000kg 이상의 고중량 산업용 AMR에서도 ±20mm 도킹은 충분히 가능하다. 다만 차량 강성(Mechanical Rigidity), 센서 품질, 제어 튜닝에 더 많은 주의가 필요하다.

결론적으로 현대 산업 환경에서 차동 구동 로봇의 ±20mm 도킹은 충분히 실현 가능하다. 다만 이는 엔코더만으로 달성되는 것이 아니라 고성능 위치 추정 및 도킹 센서의 도움을 받아야 한다.

### 4.2 조향 구동 대비 정량적 정밀도 한계 비교(Quantitative Precision Limit Comparison vs Steer Drive)

차동 구동과 조향 구동을 정량적으로 비교하면 위치 정밀도 측면에서 몇 가지 중요한 차이가 나타난다.

차동 구동은 회전 과정에서 필연적으로 바퀴 슬립이 발생한다. 이상적인 바닥 조건에서도 타이어 변형과 횡방향 힘이 발생하며, 이는 명령된 움직임(Commanded Motion)과 실제 움직임(Actual Motion) 사이의 차이를 만든다.

반면 조향 구동은 바퀴 방향이 이동 방향과 일치하기 때문에 대부분의 회전이 순수 구름 운동(Pure Rolling Motion)으로 이루어진다. 따라서 슬립이 적고 운동학 모델(Kinematic Model)에 더 가깝게 움직인다.

만약 두 시스템이 엔코더 기반 오도메트리만 사용한다고 가정하면 차이는 상당히 커진다.

일반적인 산업용 차동 구동 로봇은 수십 m 주행 후 수 cm 수준의 위치 오차를 누적할 수 있다.

반면 동일 조건의 조향 구동 로봇은 상대적으로 더 작은 오차를 보인다.

예를 들어 실내 환경에서 50m 이동 후를 비교하면 다음과 같은 수준이 일반적이다.

차동 구동은 약 ±30\~100mm 수준의 누적 오차가 발생할 수 있다.

조향 구동은 약 ±10\~50mm 수준의 오차를 보이는 경우가 많다.

방향 오차(Heading Error)도 비슷한 경향을 보인다. 차동 구동은 좌우 바퀴 직경 차이와 마모에 민감하기 때문에 방향 오차가 더 빠르게 누적된다.

그러나 LiDAR SLAM, Visual SLAM, Reflector Navigation과 같은 고급 위치 추정 시스템을 적용하면 상황은 크게 달라진다.

이 경우 누적 오차는 지속적으로 보정되므로 두 구조 모두 cm 수준의 내비게이션 정확도를 달성할 수 있다.

실제로 산업 현장에서 중요한 것은 이동 중 오차보다 최종 도킹 성능(Docking Performance)이다.

센서 기반 도킹 시스템을 적용하면 차동 구동은 일반적으로 ±10\~20mm 정도의 반복 정밀도를 달성할 수 있다.

고성능 시스템은 이보다 더 높은 정밀도를 제공하기도 한다.

조향 구동은 보통 ±5\~15mm 수준의 반복 정밀도를 달성할 수 있다.

이는 최종 정렬 단계에서 슬립이 적고 차량 운동이 보다 예측 가능하기 때문이다.

차이는 반복적인 방향 전환이 많은 환경에서 더욱 뚜렷해진다. 차동 구동은 회전이 많아질수록 슬립이 누적되지만 조향 구동은 상대적으로 일정한 기하학적 특성을 유지한다.

그러나 이러한 차이가 항상 중요한 것은 아니다.

물류 이송(Logistics Transport), 자동 충전(Auto Charging), 순회 검사(Inspection), 일반 제조 자동화(Manufacturing Automation)에서는 ±20mm 수준이면 대부분 충분하다.

이 경우 차동 구동의 비용 절감 효과와 구조 단순성이 정밀도 차이보다 훨씬 큰 가치를 제공한다.

반면 반도체 제조(Semiconductor Manufacturing), 초정밀 장비 정렬(Ultra-Precision Alignment), 서브 센티미터(Sub-Centimeter) 수준의 반복 정밀도가 요구되는 특수 공정에서는 조향 구동이 유리할 수 있다.

현대 산업용 AMR에서 LiDAR, IMU, 비전 도킹, 센서 융합 기술을 적용하면 실제 성능 차이는 생각보다 크지 않다.

실제 최종 성능은 구동 방식 자체보다 센서 아키텍처(Sensor Architecture), 위치 추정 시스템(Localization System), 제어 알고리즘(Control Algorithm)에 더 크게 좌우되는 경우가 많다.

따라서 조향 구동은 이론적으로 더 높은 정밀도 한계를 가지지만, 차동 구동 역시 산업 현장에서 요구되는 대부분의 정밀도 요구사항, 특히 ±20mm 도킹 요구사항을 충분히 만족할 수 있다.

결과적으로 많은 산업용 AMR 프로젝트에서는 추가 비용과 복잡성을 감수하면서 조향 구동을 선택하기보다, 차동 구동에 고성능 위치 추정 및 도킹 기술을 결합하는 것이 더 경제적이고 실용적인 솔루션이 되는 경우가 많다.

## 05 Heavy Load Limitations

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Heavy load operation represents one of the most important challenges for differential drive mobile robots. While differential drive architectures offer significant advantages in cost, simplicity, maintainability, and software implementation, their performance characteristics change substantially as payload increases. As robot mass grows, wheel-ground interaction forces become larger, tire deformation increases, drivetrain stress rises, and skid-related effects become more pronounced. Consequently, there is a practical payload range beyond which differential drive systems become increasingly difficult to justify when compared with steer-drive alternatives.

The limitation is not simply a matter of motor power. Modern servo motors can easily generate sufficient torque to move several tons. The more fundamental issue is the ability to maintain accurate motion control, efficient energy usage, acceptable tire life, predictable localization performance, and long-term mechanical reliability under high loading conditions.

In differential drive systems, turning requires a velocity difference between the left and right wheels. As payload increases, the friction force between tires and floor surfaces also increases. During turning maneuvers, especially zero-radius rotations, large lateral forces develop within the tire contact patch. These forces create increased tire wear, higher power consumption, greater mechanical stress, and more significant odometry errors.

Industrial users often assume that increasing motor size alone can solve heavy-load challenges. However, larger motors merely address propulsion requirements. They do not eliminate the fundamental geometric and friction-related characteristics of differential drive motion. In fact, as robot mass increases, some of these effects become more severe.

For this reason, many industrial robot manufacturers utilize differential drive architectures for light and medium payload classes while gradually transitioning toward steer-drive architectures as payload requirements increase. The exact transition point varies according to application requirements, floor conditions, duty cycles, positioning accuracy targets, and economic considerations.

Understanding the practical limitations of differential drive under heavy loading conditions is essential for selecting the appropriate drive architecture. A well-designed differential drive robot can successfully transport loads exceeding 1000 kg in certain environments, while a poorly selected architecture may experience excessive maintenance costs and reduced operational efficiency. Therefore, payload capacity must always be evaluated together with operational requirements rather than as an isolated specification.

---

### 5.1 Load Limit Experimental Data

---

### 5.2 Criteria for Transitioning to Steer Drive Above 500 kg

---

고하중 운용(Heavy Load Operation)은 차동 구동(Differential Drive) 모바일 로봇이 직면하는 가장 중요한 기술적 과제 중 하나이다. 차동 구동은 비용(Cost), 구조 단순성(Simplicity), 유지보수성(Maintainability), 소프트웨어 구현 용이성(Ease of Software Implementation) 측면에서 뛰어난 장점을 제공하지만, 적재 하중(Payload)이 증가할수록 성능 특성이 크게 변화한다.

로봇 질량(Mass)이 증가하면 바퀴와 바닥 사이의 접촉력(Wheel-Ground Interaction Force)이 커지고, 타이어 변형(Tire Deformation)이 증가하며, 구동계 응력(Drivetrain Stress)이 높아지고, 스키드(Skid) 현상도 더욱 심해진다. 결과적으로 일정 수준 이상의 하중에서는 차동 구동보다 조향 구동(Steer Drive)이 더 적합한 경우가 많아진다.

이러한 한계는 단순히 모터 출력(Motor Power)의 문제가 아니다. 현대 서보 모터는 수 톤의 하중도 충분히 이동시킬 수 있는 토크(Torque)를 생성할 수 있다. 그러나 진정한 문제는 높은 하중 상태에서도 위치 정밀도(Position Accuracy), 에너지 효율(Energy Efficiency), 타이어 수명(Tire Life), 오도메트리 정확도(Odometry Accuracy), 기계적 신뢰성(Mechanical Reliability)을 유지할 수 있는가에 있다.

차동 구동은 좌우 바퀴 속도 차이를 이용해 회전한다. 적재 하중이 증가할수록 타이어와 바닥 사이의 마찰력(Friction Force)이 증가한다. 특히 제자리 회전(Zero Radius Turn) 시에는 접촉면(Contact Patch)에 큰 횡방향 힘(Lateral Force)이 발생하며, 이는 타이어 마모, 전력 소비 증가, 구동계 응력 증가, 오도메트리 오차 증가로 이어진다.

산업 현장에서는 종종 모터를 더 크게 사용하면 문제가 해결된다고 생각하지만, 이는 추진력(Propulsion Force) 문제만 해결할 뿐이다. 차동 구동의 근본적인 기하학적 특성(Geometric Characteristics)과 마찰 특성(Friction Characteristics)은 여전히 존재한다.

이러한 이유로 많은 산업용 로봇 제조사들은 경량 및 중형 AMR에서는 차동 구동을 사용하고, 적재 하중이 증가할수록 조향 구동으로 전환하는 전략을 선택한다. 다만 전환 시점은 적재 하중만으로 결정되지 않으며, 작업 환경, 정밀도 요구사항, 운용 패턴(Duty Cycle), 경제성 등을 종합적으로 고려해야 한다.

따라서 고하중 환경에서 차동 구동의 실질적인 한계를 이해하는 것은 매우 중요하다. 잘 설계된 차동 구동 로봇은 1000kg 이상의 하중도 운반할 수 있지만, 부적절한 구조를 선택하면 유지보수 비용 증가와 운영 효율 저하로 이어질 수 있다.

### 5.1 적재 하중 한계 실험 데이터(Load Limit Experimental Data)

---

산업용 모바일 로봇을 대상으로 수행된 다양한 실험 결과를 보면, 차동 구동의 성능은 적재 하중 증가에 따라 점진적으로 변화하는 것으로 나타난다. 이러한 변화는 특정 시점에서 갑자기 발생하는 것이 아니라 하중 증가에 따라 서서히 나타난다.

약 200kg 이하의 적재 하중에서는 차동 구동이 매우 우수한 성능을 보인다. 기동성(Maneuverability)이 뛰어나고, 타이어 마모가 적으며, 오도메트리 성능도 안정적이다. 또한 구동계에 가해지는 응력도 상대적으로 작다.

200kg에서 500kg 구간에서는 여전히 대부분의 산업 환경에서 차동 구동이 효과적으로 동작한다. 그러나 회전 시 발생하는 스키드 힘(Skid Force)이 점차 증가하기 시작한다. 타이어 마모율(Tire Wear Rate)은 바닥 상태와 회전 빈도에 더 민감해지며, IMU와 센서 융합(Sensor Fusion)을 통한 오도메트리 보정의 중요성이 커진다.

실험 결과를 보면 회전에 필요한 토크는 하중 증가에 비례하여 단순 증가하지 않는다. 예를 들어 500kg 적재 차량이 250kg 적재 차량보다 정확히 두 배의 회전력을 요구하는 것은 아니다. 타이어 변형과 마찰 효과가 비선형적으로 증가하기 때문에 회전 시 필요한 힘은 더욱 빠르게 증가한다.

500kg에서 1000kg 구간에 진입하면 여러 가지 문제가 눈에 띄게 증가한다. 특히 거친 콘크리트 바닥(Rough Concrete Floor)이나 빈번한 회전이 발생하는 환경에서는 타이어 마모가 크게 증가한다.

제자리 회전은 매우 큰 횡방향 힘을 발생시키며, 타이어 수명을 단축시키고 전력 소비도 증가시킨다.

플릿 운영(Fleet Operation) 데이터에서도 이러한 현상이 확인된다. 이 구간에서는 타이어 교체 주기(Tire Replacement Interval)가 눈에 띄게 짧아지며, 타이어 직경 변화가 오도메트리 정확도에 미치는 영향도 커진다.

전력 소비(Power Consumption) 측면에서도 흥미로운 결과가 나타난다. 직선 주행에서는 에너지 사용량이 비교적 하중에 비례하여 증가한다. 그러나 회전 시에는 마찰과 타이어 변형을 극복하기 위해 훨씬 많은 에너지가 필요하므로 소비 전력이 비례 이상으로 증가한다.

1000kg 이상의 하중에서도 차동 구동은 기술적으로 가능하다. 실제로 1500kg, 2000kg 이상의 적재 능력을 가진 차동 구동 AMR도 존재한다. 그러나 이러한 시스템은 일반적으로 낮은 속도, 고품질 바닥, 체계적인 유지보수 프로그램을 전제로 한다.

실험 결과에 따르면 고중량 차동 구동 로봇은 직선 주행보다 회전 시 구동계에 더 큰 응력이 발생한다. 따라서 베어링(Bearing), 감속기(Gearbox), 휠 허브(Wheel Hub), 섀시(Chassis)는 충분한 안전율(Safety Factor)을 고려하여 설계되어야 한다.

또한 적재 하중이 증가할수록 슬립 발생 빈도도 증가한다. 따라서 LiDAR SLAM, Reflector Navigation, Visual Marker, IMU Fusion과 같은 고급 위치 추정 시스템의 중요성이 더욱 커진다.

결론적으로 실험 데이터는 차동 구동이 명확한 하중 한계를 가지는 것이 아니라, 하중 증가에 따라 성능이 점진적으로 저하된다는 사실을 보여준다. 따라서 높은 하중일수록 더 많은 설계 노력과 유지보수 전략이 필요하다.

### 5.2 500kg 이상에서 조향 구동 전환 기준(Criteria for Transitioning to Steer Drive Above 500kg)

차동 구동에서 조향 구동으로 전환해야 하는 시점을 단순히 적재 하중만으로 판단해서는 안 된다. 산업계에서는 흔히 500kg을 기준점으로 언급하지만, 실제 전환 시점은 다양한 요소에 의해 결정된다.

가장 중요한 요소 중 하나는 회전 빈도(Turning Frequency)이다. 만약 로봇이 대부분 직선 주행을 수행하고 가끔 완만한 회전만 한다면, 500kg 이상의 하중에서도 차동 구동이 충분히 실용적일 수 있다.

반면 좁은 통로(Narrow Aisle), 혼잡한 창고(High-Density Warehouse), 빈번한 제자리 회전이 필요한 환경에서는 500kg 이하에서도 조향 구동이 유리할 수 있다.

위치 정밀도 요구사항도 중요한 기준이다. 차동 구동은 고성능 위치 추정 기술을 사용하면 매우 우수한 도킹 성능을 달성할 수 있다. 그러나 고하중 상태에서 반복적으로 높은 정렬 정밀도를 요구하는 응용에서는 조향 구동이 더 안정적인 결과를 제공할 수 있다.

바닥 상태(Floor Condition)도 매우 중요하다. 에폭시 바닥(Epoxy Floor)과 같이 평탄하고 마찰 특성이 일정한 환경에서는 차동 구동이 유리하다. 반면 거친 콘크리트, 확장 조인트, 요철이 많은 환경에서는 타이어 마모와 유지보수 비용이 급격히 증가할 수 있으며, 이 경우 조향 구동의 장점이 커진다.

운용 시간(Duty Cycle)도 고려해야 한다. 하루 8시간 운행하는 로봇과 24시간 연속 운행하는 로봇은 전혀 다른 유지보수 특성을 가진다. 고가동률(High Utilization) 환경에서는 조향 구동의 낮은 타이어 마모율과 높은 에너지 효율이 큰 장점이 된다.

적재물의 형태와 무게 중심(Center of Gravity)도 중요하다. 중앙에 균형 있게 적재되는 경우는 문제가 적지만, 높은 하중 중심(High Center of Gravity), 편하중(Off-Center Load), 동적 하중(Dynamic Load)이 존재하는 경우에는 조향 구동이 더 안정적일 수 있다.

실무적으로는 약 500kg 이하에서는 특별한 이유가 없는 한 차동 구동을 우선 고려하는 것이 일반적이다. 이 구간에서는 차동 구동이 성능, 비용, 유지보수 측면에서 가장 우수한 균형을 제공한다.

500kg에서 1000kg 구간은 의사결정 구간(Decision Zone)으로 볼 수 있다. 이 범위에서는 차동 구동과 조향 구동 모두 가능하며, 유지보수 비용, 타이어 교체 주기, 에너지 소비, 위치 정밀도 등을 포함한 총 소유 비용(TCO) 분석이 필요하다.

1000kg 이상이 되면 조향 구동의 매력이 점점 커진다. 스키드 감소, 타이어 수명 향상, 예측 가능한 차량 거동, 향상된 기동성이 추가 비용을 정당화하는 경우가 많다.

1500kg에서 2000kg 이상의 고중량 영역에서는 많은 산업용 로봇 제조사들이 조향 구동을 선호한다. 특히 빈번한 회전, 고정밀 작업, 24시간 연속 운전이 필요한 경우에는 더욱 그렇다.

물론 예외도 존재한다. 일부 산업용 운반 로봇은 2000kg 이상의 하중에서도 차동 구동을 사용한다. 이는 회전 빈도가 낮고 구조 단순성을 최우선으로 고려하기 때문이다.

따라서 적재 하중만을 기준으로 구동 방식을 선택하는 것은 바람직하지 않다. 총 소유 비용(TCO), 운용 시간, 바닥 조건, 정밀도 요구사항, 플릿 규모, 유지보수 전략 등을 함께 고려해야 한다.

결론적으로 산업계에서 자주 언급되는 500kg 기준은 절대적인 기술적 한계가 아니다. 이는 조향 구동을 검토하기 시작해야 하는 의사결정 시작점(Starting Point of Decision)으로 이해하는 것이 더 적절하다.

실제 구동 방식의 선택은 단순한 하중 수치가 아니라 로봇이 수행해야 하는 전체 운영 목표(Operation Objective)를 기반으로 결정되어야 한다.
