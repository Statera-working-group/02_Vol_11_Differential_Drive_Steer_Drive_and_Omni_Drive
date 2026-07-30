**Differential Drive & Steer Drive Engineering**


# Chapter 18 Steer Drive Kinematics

##  

## 01 Four-wheel steering kinematics

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 4WS Forward Kinematics Equation Derivation

Forward kinematics is one of the fundamental mathematical models governing the motion of a Four-Wheel Steering (4WS) mobile robot. Its primary objective is to determine the actual translational and rotational motion of the vehicle based on the measured steering angles and rotational velocities of all wheel modules. Unlike inverse kinematics, which calculates actuator commands from a desired vehicle motion, forward kinematics estimates the vehicle state using sensor feedback obtained from the steering encoders and drive encoders installed in each independent wheel module. This model serves as the foundation for odometry, localization, sensor fusion, trajectory tracking, and autonomous navigation.

A typical 4WS steer-drive platform consists of four identical wheel modules located at fixed positions relative to the vehicle coordinate frame. Let the vehicle reference frame be defined with its origin at the geometric center of the chassis. The positive x-axis points toward the forward direction of the vehicle, while the positive y-axis points toward the left side of the chassis. Each wheel module i occupies a known position vector (xi, yi), where i ranges from one to four. Every module independently measures its steering angle θi and wheel rotational speed ωi through high-resolution encoders.

The wheel rotational speed is converted into linear wheel velocity by multiplying the angular velocity by the effective wheel radius. Thus, the linear velocity of wheel i is expressed as vi = rωi, where r represents the wheel radius. Since each wheel is constrained to roll along its steering direction, the wheel velocity vector becomes the product of the scalar wheel velocity and the steering direction unit vector. The steering direction is represented by the cosine and sine of the steering angle, producing a two-dimensional velocity vector aligned with the rolling direction of the wheel.

The motion of the entire vehicle can be described by three independent variables: longitudinal velocity Vx, lateral velocity Vy, and yaw rate Ω. These three quantities define the planar rigid-body motion of the robot. According to rigid-body kinematics, the velocity of every wheel is equal to the translational velocity of the vehicle plus the rotational velocity induced by yaw motion. The rotational contribution depends on the distance of the wheel from the vehicle center and is obtained using the cross product between angular velocity and wheel position.

For the ith wheel module, the rigid-body velocity components are therefore expressed as

Vxi = Vx − Ωyi

Vyi = Vy + Ωxi

These equations describe the velocity of the wheel center before considering the steering constraint. Because the wheel cannot generate lateral slip under ideal rolling conditions, its actual velocity must lie along the steering direction. Projecting the rigid-body velocity onto the steering direction yields the rolling constraint

vi = cos(θi)(Vx − Ωyi) + sin(θi)(Vy + Ωxi)

This relationship forms the fundamental forward kinematic equation for each steer-drive module.

Since four independent wheel modules are available, four independent equations are obtained while only three unknown vehicle variables exist. The resulting system is therefore overdetermined. Rather than solving three equations exactly, modern controllers estimate the vehicle motion using all four measurements simultaneously through least-squares optimization. This approach improves robustness against encoder noise, wheel diameter variation, tire deformation, and small steering errors.

The forward kinematic equations may be written compactly in matrix form. Let the measurement vector consist of the four measured wheel velocities, while the unknown state vector contains longitudinal velocity, lateral velocity, and yaw rate. The steering angles and wheel positions define the coefficient matrix relating the measured wheel velocities to the vehicle motion. The system becomes

v = Hx

where v denotes the wheel velocity vector, x represents the vehicle velocity vector, and H is the geometry matrix determined by steering orientation and wheel placement.

Since H generally contains more rows than columns, the vehicle velocity estimate is computed using the Moore--Penrose pseudoinverse

x = (HᵀH)⁻¹Hᵀv

This least-squares solution minimizes the total measurement error while utilizing information from every wheel module. It also provides increased tolerance to individual sensor noise and improves odometry accuracy during long-term operation.

Forward kinematics forms the computational basis of wheel odometry. At every control cycle, the estimated vehicle velocity is numerically integrated to obtain the vehicle pose consisting of x-position, y-position, and heading angle. Because wheel encoder measurements accumulate small systematic and random errors over time, forward kinematics is almost always combined with additional sensing modalities. Inertial Measurement Units provide short-term rotational stability, LiDAR localization corrects accumulated drift, camera-based localization improves global consistency, and GNSS contributes absolute positioning for outdoor applications. Modern autonomous mobile robots therefore employ forward kinematics as one component within a larger multi-sensor localization framework.

Several practical factors influence forward kinematic accuracy. Tire deformation changes the effective rolling radius under heavy loads. Manufacturing tolerances introduce small differences between wheel diameters. Steering backlash creates angular uncertainty, while floor irregularities generate temporary wheel slip. Temperature variations alter tire stiffness, and uneven payload distribution changes wheel loading. Advanced estimation algorithms continuously compensate for these effects using adaptive calibration techniques and probabilistic sensor fusion.

The computational complexity of forward kinematics remains relatively low compared with higher-level planning algorithms. Matrix dimensions are small, allowing real-time computation at servo update rates exceeding one kilohertz. Consequently, forward kinematic estimation is continuously executed within the vehicle controller and provides instantaneous feedback for closed-loop motion control, trajectory tracking, collision avoidance, and state estimation.

As autonomous mobile robots continue demanding higher positioning accuracy and greater operational autonomy, forward kinematics remains one of the essential mathematical foundations of steer-drive motion control. Accurate estimation of vehicle motion directly influences localization quality, navigation performance, path-following precision, and overall system reliability. Therefore, understanding the derivation and implementation of forward kinematic equations is indispensable for designing high-performance Four-Wheel Steering autonomous mobile robots.

---

### 1.2 4WS Inverse Kinematics Equation Derivation

Inverse kinematics performs the complementary function of forward kinematics by calculating the steering angles and wheel velocities required to achieve a desired vehicle motion. Instead of estimating vehicle movement from wheel measurements, inverse kinematics transforms a commanded vehicle velocity into actuator-level commands for every independent steering module. This transformation represents one of the most critical computational processes within a steer-drive control system because it directly determines how each steering motor and drive motor should operate to produce coordinated multidirectional motion.

The desired motion of the vehicle is typically defined by three independent variables: longitudinal velocity Vx, lateral velocity Vy, and yaw rate Ω. These variables completely describe planar rigid-body motion and may originate from a navigation planner, path-following controller, obstacle avoidance algorithm, teleoperation interface, or autonomous mission planner. The objective of inverse kinematics is to convert these vehicle-level commands into steering angles θi and wheel linear velocities vi for each wheel module.

The derivation begins by considering the rigid-body velocity at the location of every wheel. Since the vehicle simultaneously translates and rotates, the local velocity at wheel i is obtained by adding the translational velocity of the chassis to the rotational velocity induced by yaw motion. Using the wheel coordinates (xi, yi), the velocity components become

Vxi = Vx − Ωyi

Vyi = Vy + Ωxi

These expressions describe the desired motion that must be generated by the corresponding wheel module.

The steering angle of each wheel is determined by aligning the wheel with its local velocity vector. Because an ideal wheel rolls only along its own rolling direction, the steering axis must rotate until the wheel becomes tangent to the desired velocity vector. The steering angle is therefore calculated using the two-argument arctangent function

θi = atan2(Vyi, Vxi)

The atan2 formulation automatically selects the correct angular quadrant while avoiding discontinuities that occur with ordinary inverse tangent functions. This representation ensures continuous steering solutions over the complete 360-degree steering range.

Once the steering orientation has been determined, the wheel velocity is obtained from the magnitude of the local velocity vector

vi = √(Vxi² + Vyi²)

This equation represents the linear velocity required for wheel i to generate the commanded vehicle motion. The corresponding motor rotational speed is calculated by dividing the wheel linear velocity by the wheel radius

ωi = vi / r

where r denotes the effective wheel radius.

The resulting inverse kinematic equations simultaneously determine one steering angle and one wheel speed for every wheel module. Since four steering motors and four drive motors exist, the controller produces eight actuator commands during every control cycle. These commands are transmitted through deterministic real-time communication networks such as EtherCAT to the distributed servo drives controlling each independent wheel module.

One important characteristic of steer-drive inverse kinematics is that multiple steering solutions may satisfy the same desired vehicle motion. For example, a wheel can often reach an equivalent rolling direction by rotating 180 degrees while reversing wheel rotation. Modern steering optimization algorithms continuously evaluate alternative solutions and select the one minimizing steering displacement, actuator energy consumption, or transition time. This optimization significantly improves maneuverability during frequent direction changes and reduces unnecessary steering motion.

Special motion cases naturally emerge from the inverse kinematic equations. During pure forward motion, lateral velocity and yaw rate are zero, resulting in identical steering angles aligned with the vehicle axis and equal wheel velocities. During crab motion, longitudinal velocity and yaw rate vanish while lateral velocity remains constant, producing identical steering angles approximately ninety degrees from the forward direction. During zero-radius rotation, translational velocities become zero, causing every steering module to align tangentially with a virtual circle centered within the chassis. During diagonal movement, both longitudinal and lateral velocities remain nonzero, generating steering angles corresponding to the resultant velocity vector.

Real-world implementations require additional constraints beyond the mathematical derivation. Steering motors possess finite angular velocity limits, drive motors have maximum torque capabilities, and wheel acceleration must remain within acceptable dynamic limits. Cable routing restrictions may limit continuous steering rotation, while mechanical interference prevents certain steering configurations. Consequently, inverse kinematic solutions are frequently combined with optimization routines that enforce actuator limitations while preserving the desired vehicle motion as closely as possible.

Dynamic effects also influence practical inverse kinematic control. Abrupt steering angle changes may cause excessive actuator loading or tire slip if drive torque is applied before steering alignment is complete. Therefore, motion controllers coordinate steering completion with propulsion activation through synchronized servo sequencing. Model Predictive Control algorithms increasingly predict future vehicle trajectories and gradually adjust steering angles in advance, reducing transient disturbances and improving overall motion smoothness.

Inverse kinematics additionally forms the basis of higher-level trajectory tracking. Navigation algorithms generate desired velocity commands at every planning cycle, while the inverse kinematic solver continuously converts these commands into actuator references. Feedback controllers subsequently compare measured steering angles and wheel velocities against their desired values, minimizing tracking error through high-frequency closed-loop servo control. This layered architecture separates path planning from low-level actuator execution while maintaining precise vehicle motion.

Sensor feedback further enhances inverse kinematic performance. Steering encoders verify actual steering orientation, drive encoders confirm wheel velocity, inertial sensors monitor rotational dynamics, and external localization systems detect accumulated tracking errors. Adaptive controllers modify future actuator commands whenever deviations are observed, improving robustness against wheel slip, payload variation, mechanical wear, and environmental disturbances.

As industrial autonomous mobile robots increasingly require multidirectional mobility, high positioning accuracy, and efficient navigation in complex environments, inverse kinematics remains one of the most important mathematical tools supporting steer-drive technology. Its ability to translate abstract vehicle motion commands into precisely coordinated actuator commands enables the exceptional maneuverability, flexibility, and precision that distinguish Four-Wheel Steering platforms from conventional mobile robot architectures.

### 1.1 4륜 조향(4WS) 순기구학(Forward Kinematics) 방정식 유도 (4WS Forward Kinematics Equation Derivation)

순기구학(Forward Kinematics)은 **4륜 조향(4WS, Four-Wheel Steering)** 이동로봇의 움직임을 기술하는 가장 기본적인 수학적 모델 가운데 하나이다. 순기구학의 목적은 각 바퀴 모듈에서 측정된 조향각(Steering Angle)과 바퀴 회전 속도(Wheel Rotational Speed)를 이용하여 차량의 실제 선형 속도(Translational Velocity)와 회전 속도(Rotational Velocity)를 계산하는 것이다. 역기구학(Inverse Kinematics)이 원하는 차량 운동으로부터 각 액추에이터의 명령을 계산하는 과정이라면, 순기구학은 각 바퀴의 센서 데이터를 이용하여 차량이 실제 어떻게 움직였는지를 추정하는 과정이다. 이러한 계산은 오도메트리(Odometry), 위치 추정(Localization), 센서 융합(Sensor Fusion), 경로 추종(Path Tracking), 자율주행(Navigation)의 핵심 기반이 된다.

일반적인 4WS 스티어 드라이브 플랫폼은 차체 중심을 기준으로 네 개의 독립적인 휠 모듈을 가진다. 차량 좌표계(Vehicle Coordinate Frame)의 원점은 차체의 기하학적 중심(Geometric Center)에 위치하며, x축은 차량의 전진 방향, y축은 차량의 좌측 방향으로 정의한다. 각 바퀴 모듈은 ((x_i, y_i))라는 고정된 위치 좌표를 가지며, 각각의 모듈은 절대형 엔코더(Absolute Encoder)를 이용하여 자신의 조향각 (\\theta_i)를 측정하고, 구동 엔코더를 이용하여 바퀴의 회전 속도 (\\omega_i)를 측정한다.

바퀴의 회전 속도는 실제 선속도(Linear Velocity)로 변환되어야 한다. 바퀴 반경을 (r)이라고 하면 바퀴의 선속도는 다음과 같이 표현된다.

[

v_i = r\\omega_i

]

여기서 (v_i)는 i번째 바퀴의 선속도이고, (r)은 유효 바퀴 반경(Effective Wheel Radius), (\\omega_i)는 바퀴의 각속도이다.

각 바퀴는 자신의 조향 방향으로만 굴러갈 수 있기 때문에 바퀴의 속도 벡터는 조향 방향 단위벡터와 선속도의 곱으로 표현된다. 조향 방향은 조향각의 코사인(Cosine)과 사인(Sine)을 이용하여 다음과 같이 나타낼 수 있다.

차량 전체의 운동은 세 개의 독립 변수로 표현된다.

\* 종방향 속도(Longitudinal Velocity) (V_x)

\* 횡방향 속도(Lateral Velocity) (V_y)

\* 요 각속도(Yaw Rate) (\\Omega)

이 세 변수는 평면에서 강체(Rigid Body)의 운동을 완전히 표현한다.

강체 운동학(Rigid-body Kinematics)에 따르면 각 바퀴의 실제 속도는 차량 전체의 병진 운동(Translation)에 차량의 회전에 의해 발생하는 속도가 더해진 결과이다. 회전에 의한 속도는 차량 중심으로부터의 거리와 각속도의 외적(Cross Product)에 의해 결정된다.

i번째 바퀴의 속도 성분은 다음과 같이 표현된다.

[

V_{xi}=V_x-\\Omega y_i

]

[

V_{yi}=V_y+\\Omega x_i

]

이 식은 바퀴가 아직 조향 제약을 받지 않은 상태에서의 속도를 의미한다.

그러나 실제 바퀴는 횡방향으로 미끄러지지 않고 자신의 조향 방향으로만 굴러간다. 따라서 위의 속도를 조향 방향으로 투영(Projection)하면 실제 바퀴 속도가 된다.

[

v_i=

\\cos(\\theta_i)(V_x-\\Omega y_i)

\+

\\sin(\\theta_i)(V_y+\\Omega x_i)

]

이 식이 바로 **4WS 순기구학의 기본 방정식**이다.

4개의 독립 바퀴를 사용하면 이러한 식이 네 개 생성된다. 반면 실제 미지수는 (V_x), (V_y), (\\Omega) 세 개뿐이므로 시스템은 **과결정 시스템(Overdetermined System)**이 된다.

현대의 스티어 드라이브 제어기는 세 개의 식만 사용하는 것이 아니라 네 개의 식을 모두 활용하여 최소제곱법(Least Squares Method)으로 차량 속도를 계산한다. 이 방법은 엔코더 노이즈, 바퀴 직경 오차, 타이어 변형, 조향 오차 등에 대해 훨씬 강인한(Robust) 추정을 제공한다.

행렬(Matrix) 형태로 표현하면

[

\\mathbf{v}=\\mathbf{H}\\mathbf{x}

]

여기서

\* (\\mathbf{v}) : 네 개 바퀴 속도 벡터

\* (\\mathbf{x}) : 차량 속도 벡터 ([V_x,V_y,\\Omega]\^T)

\* (\\mathbf{H}) : 조향각과 바퀴 위치로 구성된 기하학 행렬(Geometry Matrix)

이다.

차량 속도는 **무어-펜로즈 의사역행렬(Moore-Penrose Pseudoinverse)**을 이용하여 계산된다.

[

\\mathbf{x}

==========

(\\mathbf{H}\^T\\mathbf{H})\^{-1}

\\mathbf{H}\^T

\\mathbf{v}

]

이 계산은 모든 바퀴의 정보를 동시에 이용하면서 전체 측정 오차를 최소화하는 최적의 차량 속도를 추정한다.

순기구학은 휠 오도메트리(Wheel Odometry)의 핵심이기도 하다. 제어 주기마다 계산된 차량 속도를 적분(Integration)하면 차량의 위치 ((x,y))와 자세(Heading Angle)를 계산할 수 있다. 그러나 엔코더 기반 오도메트리는 시간이 지날수록 오차가 누적되므로 실제 산업용 AMR에서는 IMU, LiDAR 위치 인식(LiDAR Localization), 카메라 기반 위치 인식(Camera Localization), GNSS(Global Navigation Satellite System) 등을 함께 사용하는 센서 융합 방식이 일반적이다.

순기구학의 정확도는 다양한 현실적인 요소의 영향을 받는다. 중량물 적재 시에는 타이어 변형으로 유효 반경이 변화하고, 제조 공차에 의해 바퀴 직경 차이가 발생한다. 조향 감속기의 백래시(Backlash), 노면 요철, 일시적인 휠 슬립, 온도 변화에 따른 타이어 강성 변화, 하중 분포 변화 등도 모두 위치 오차의 원인이 된다. 이러한 문제를 해결하기 위해 최근의 시스템은 적응형 보정(Adaptive Calibration)과 확률 기반 센서 융합(Probabilistic Sensor Fusion)을 적용하여 지속적으로 모델을 수정한다.

순기구학 계산 자체는 비교적 계산량이 적다. 행렬의 크기가 작기 때문에 1 kHz 이상의 서보 제어 주기에서도 실시간 계산이 가능하며, 경로 추종, 충돌 회피, 상태 추정 및 폐루프 운동 제어에 필요한 즉각적인 차량 상태 정보를 제공한다.

결국 4WS 순기구학은 스티어 드라이브 플랫폼의 운동을 이해하는 가장 기본적인 수학적 기반이며, 차량의 위치 추정 정확도, 경로 추종 성능, 자율주행 안정성 및 전체 시스템의 신뢰성을 결정하는 핵심 요소이다. 따라서 고성능 산업용 자율주행 이동로봇을 설계하기 위해서는 순기구학 방정식의 유도 과정과 실제 구현 원리를 충분히 이해하는 것이 매우 중요하다.

---

### 1.2 4륜 조향(4WS) 역기구학(Inverse Kinematics) 방정식 유도 (4WS Inverse Kinematics Equation Derivation)

역기구학(Inverse Kinematics)은 순기구학과 반대되는 역할을 수행한다. 순기구학이 바퀴의 상태로부터 차량의 움직임을 계산한다면, 역기구학은 원하는 차량 운동으로부터 각 바퀴가 가져야 할 조향각과 회전 속도를 계산한다. 다시 말해 차량 수준(Vehicle Level)의 이동 명령을 실제 액추에이터 수준(Actuator Level)의 제어 명령으로 변환하는 과정이다. 이 계산은 스티어 드라이브 제어 시스템에서 가장 중요한 연산 가운데 하나이며, 각 조향 모터와 구동 모터가 어떤 값을 가져야 원하는 이동을 정확하게 구현할 수 있는지를 결정한다.

차량의 목표 운동은 일반적으로 다음의 세 가지 변수로 정의된다.

\* 종방향 속도(Longitudinal Velocity) (V_x)

\* 횡방향 속도(Lateral Velocity) (V_y)

\* 요 각속도(Yaw Rate) (\\Omega)

이 값들은 경로 계획기(Path Planner), 자율주행 알고리즘, 장애물 회피 시스템, 원격 조종(Teleoperation) 또는 미션 계획기(Mission Planner)로부터 생성된다.

역기구학의 목표는 이 세 개의 운동 변수를 각 바퀴의

\* 조향각(Steering Angle)

\* 바퀴 속도(Wheel Velocity)

로 변환하는 것이다.

유도 과정은 순기구학과 동일하게 각 바퀴 위치에서의 강체 운동 속도를 계산하는 것에서 시작한다.

차량이 병진 운동과 회전 운동을 동시에 수행하면 각 바퀴의 속도는

[

V_{xi}=V_x-\\Omega y_i

]

[

V_{yi}=V_y+\\Omega x_i

]

로 표현된다.

조향각은 바퀴가 이 속도 벡터와 정확히 일치하도록 계산되어야 한다.

따라서 조향각은

[

\\theta_i

========

atan2(V_{yi},V_{xi})

]

로 계산된다.

여기서 atan2 함수는 일반적인 arctangent보다 우수하며 360° 전 영역에서 올바른 사분면(Quadrant)을 자동으로 선택한다. 따라서 조향각이 연속적으로 계산되고 갑작스러운 각도 변화가 발생하지 않는다.

조향각이 계산되면 바퀴 속도는 속도 벡터의 크기로부터 계산된다.

[

v_i

===

\\sqrt{V_{xi}\^2+V_{yi}\^2}

]

이 식은 각 바퀴가 만들어야 하는 실제 선속도를 의미한다.

모터 회전 속도는

[

\\omega_i

========

\\frac{v_i}{r}

]

로 계산된다.

여기서

\* (r) : 바퀴 반경

\* (v_i) : 바퀴 선속도

\* (\\omega_i) : 모터 각속도

이다.

결과적으로 역기구학 계산은 제어 주기마다

\* 4개의 조향각

\* 4개의 구동 속도

총 8개의 액추에이터 명령을 생성한다.

이 명령들은 EtherCAT과 같은 결정론적 실시간 통신망을 통해 각 조향 모터와 구동 모터로 전달된다.

스티어 드라이브 역기구학의 특징 가운데 하나는 **동일한 차량 운동을 여러 가지 조향 상태로 구현할 수 있다는 것**이다.

예를 들어

\* 바퀴를 180° 회전시키고

\* 모터 회전 방향을 반대로 하는 것

은 기존 조향 상태와 동일한 운동을 만들어낼 수 있다.

최근의 조향 최적화 알고리즘(Steering Optimization Algorithm)은

\* 조향 회전량 최소화

\* 에너지 소비 최소화

\* 응답 시간 최소화

등을 기준으로 여러 해 가운데 가장 효율적인 해를 선택한다.

역기구학에서는 다양한 특수 운동도 자연스럽게 계산된다.

직진에서는 모든 바퀴의 조향각이 동일하고 속도도 같다.

크랩 주행에서는 모든 바퀴가 약 90° 방향으로 조향된다.

제자리 회전에서는 모든 바퀴가 차량 중심을 기준으로 하는 원의 접선 방향으로 정렬된다.

대각선 이동에서는 종방향 속도와 횡방향 속도가 동시에 존재하므로 각 바퀴는 결과 속도 벡터(Resultant Velocity Vector)를 향하도록 조향된다.

실제 시스템에서는 수학적인 해뿐 아니라 다양한 현실적인 제약도 고려해야 한다.

조향 모터는 최대 회전 속도가 있으며, 구동 모터는 최대 토크를 초과할 수 없다. 바퀴 가속도 제한, 케이블 배선 한계, 기계적 간섭 및 감속기 특성도 함께 고려되어야 한다. 따라서 대부분의 산업용 시스템은 역기구학 계산 이후 최적화 알고리즘을 추가하여 실제 액추에이터의 물리적 한계를 만족시키도록 한다.

동적 특성(Dynamic Characteristics)도 매우 중요하다. 조향이 완료되기 전에 추진력을 발생시키면 타이어 슬립과 큰 횡력이 발생할 수 있다. 따라서 제어기는 조향 완료 여부를 확인한 후 구동 토크를 인가하며, 최근에는 **모델 예측 제어(Model Predictive Control, MPC)**를 이용하여 미래 경로를 예측하고 조향을 미리 수행하는 기술도 많이 사용되고 있다.

역기구학은 상위 경로 추종(Path Tracking)의 핵심 요소이기도 하다. 경로 계획기는 원하는 차량 속도를 생성하고, 역기구학은 이를 액추에이터 명령으로 변환한다. 이후 각 서보 제어기는 실제 조향각과 바퀴 속도를 지속적으로 비교하여 오차를 최소화하는 폐루프 제어를 수행한다. 이러한 계층형 구조(Hierarchical Architecture)는 경로 계획과 실제 구동 제어를 효율적으로 분리하면서도 매우 높은 위치 정확도를 유지한다.

센서 피드백 역시 역기구학의 성능을 향상시키는 중요한 요소이다. 조향 엔코더는 실제 조향각을 확인하고, 구동 엔코더는 바퀴 속도를 측정하며, IMU는 차량의 회전 운동을 감시한다. 또한 라이다와 카메라 기반 위치 인식 시스템은 누적 오차를 지속적으로 보정하며, 적응형 제어기(Adaptive Controller)는 이러한 정보를 이용하여 다음 제어 주기의 조향각과 속도를 자동으로 수정한다.

결국 **4WS 역기구학은 차량 수준의 추상적인 이동 명령을 실제 모터 수준의 정밀한 제어 명령으로 변환하는 핵심 알고리즘**이다. 이 알고리즘 덕분에 스티어 드라이브 플랫폼은 전방향 이동, 높은 위치 정밀도, 우수한 기동성 및 부드러운 운동 성능을 구현할 수 있으며, 이는 기존 이동로봇과 차별화되는 가장 중요한 기술적 기반이 된다.

##  

## 02 Crab motion kinematics

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Full Lateral Motion Equations

Crab motion, also referred to as full lateral motion, is one of the defining capabilities of a Four-Wheel Steering (4WS) steer-drive mobile robot. Unlike conventional non-holonomic vehicles that must rotate before changing their lateral position, a steer-drive platform can translate sideways while maintaining a constant vehicle orientation. This motion is achieved by synchronizing the steering angles and wheel velocities of all independent wheel modules so that every wheel rolls in the same direction. Because no wheel is forced to slide laterally, crab motion provides exceptionally smooth movement, high positioning accuracy, and reduced tire wear, making it highly suitable for precision industrial applications.

The kinematic description of full lateral motion begins with the general planar rigid-body velocity model. The motion of the vehicle is represented by three independent variables: longitudinal velocity (V_x), lateral velocity (V_y), and yaw rate (\\Omega). These variables completely describe the translational and rotational motion of the robot on a two-dimensional plane. During ideal crab motion, the objective is to eliminate both longitudinal translation and rotational movement while maintaining a constant lateral velocity. Therefore, the desired vehicle motion is defined as

V_x = 0

V_y = V_c

\\Omega = 0

where (V_c) denotes the commanded crab velocity.

Substituting these conditions into the rigid-body kinematic equations immediately simplifies the local velocity of every wheel. Since the rotational contribution disappears and no longitudinal motion exists, each wheel experiences exactly the same velocity vector regardless of its position on the chassis. The velocity components become

V_{xi}=0

V_{yi}=V_c

Consequently, every wheel module generates an identical velocity vector directed purely along the lateral axis. Unlike turning maneuvers, where wheel velocities depend on their distances from the instantaneous center of rotation, crab motion requires no differential velocity distribution among the wheels. Every drive motor rotates at the same speed while every steering module maintains the same steering orientation.

The steering direction of each wheel is obtained by aligning the rolling direction with the desired velocity vector. Using the standard inverse kinematic formulation,

\\theta_i = atan2(V_{yi},V_{xi})

the steering angle becomes

\\theta_i = atan2(V_c,0)

For positive lateral motion, this evaluates to approximately ninety degrees, while negative lateral motion corresponds to approximately minus ninety degrees. Thus, all steering modules adopt identical steering angles, enabling the vehicle to translate sideways without changing its heading.

The required wheel velocity is determined from the magnitude of the velocity vector

v_i=\\sqrt{V_{xi}\^2+V_{yi}\^2}

Since longitudinal velocity is zero,

v_i=\|V_c\|

Therefore, every wheel rotates with identical linear velocity, and the corresponding motor angular velocity is calculated using

\\omega_i=\\frac{\|V_c\|}{r}

where (r) is the effective wheel radius.

The resulting mathematical model demonstrates an important characteristic of crab motion: the entire vehicle behaves as if it were undergoing pure translation. Every wheel experience identical velocity magnitude and identical steering orientation. No differential steering geometry is required, no instantaneous center of rotation exists within the finite plane, and no wheel experiences additional rotational velocity components. This symmetry greatly simplifies both motion planning and control implementation.

Although the ideal kinematic equations appear straightforward, practical implementations require continuous correction for disturbances. Small steering angle deviations among individual modules immediately generate unintended yaw moments that gradually rotate the vehicle away from its desired orientation. Likewise, slight wheel diameter differences or unequal floor friction produce velocity mismatches that introduce unwanted rotational drift. Consequently, modern steer-drive controllers continuously monitor steering encoders, wheel encoders, inertial measurement units, and external localization sensors to compensate for these disturbances in real time.

Closed-loop lateral control typically employs hierarchical feedback. The outer loop compares the desired lateral trajectory with the estimated vehicle position obtained through sensor fusion. The inner loop independently regulates steering angle and wheel velocity for each module using high-bandwidth servo controllers. Because every wheel operates independently, extremely small steering corrections can eliminate accumulated positioning errors without interrupting the overall lateral motion.

Dynamic considerations become increasingly important for heavy industrial autonomous mobile robots. During rapid lateral acceleration, inertial forces act perpendicular to the vehicle\'s original longitudinal axis, creating significant load transfer between the left and right wheels. The resulting variation in normal force changes available traction and may influence wheel slip characteristics. Advanced traction control algorithms therefore monitor motor currents and wheel slip indicators to redistribute torque whenever necessary, preserving stable lateral movement even under changing payload conditions.

Energy efficiency represents another advantage of full lateral motion. Since every wheel rolls directly in its steering direction, friction losses remain low compared with skid-steering systems that rely on tire scrubbing for lateral repositioning. Reduced friction decreases motor power consumption, minimizes heat generation, and extends tire lifetime, making crab motion particularly attractive for high-duty-cycle industrial applications.

Full lateral motion is extensively employed in semiconductor manufacturing, automated warehouse systems, machine tending, precision docking, hospital logistics, and pharmaceutical automation. In each of these applications, the ability to reposition the vehicle sideways without rotating substantially improves workspace utilization while reducing maneuvering time. The mathematical simplicity of the crab motion equations combined with the high precision achievable through closed-loop servo control makes full lateral translation one of the most valuable capabilities of modern Four-Wheel Steering autonomous mobile robots.

### 2.2 Crab Angle and Steering Angle Relationship

The relationship between crab angle and steering angle forms one of the fundamental concepts governing lateral motion in steer-drive mobile robots. Although these two quantities are closely related, they describe different physical aspects of vehicle motion. The steering angle represents the orientation of each individual wheel module relative to the vehicle body, whereas the crab angle describes the overall direction of vehicle translation relative to the longitudinal axis of the chassis. Understanding the mathematical relationship between these two angles is essential for deriving accurate kinematic models, implementing trajectory tracking algorithms, and optimizing multidirectional vehicle motion.

The steering angle is defined independently for each wheel module. Let θi denote the steering angle of wheel i measured relative to the forward direction of the vehicle. Positive steering angles are typically measured counterclockwise from the vehicle x-axis according to the right-hand coordinate convention. Because every steering module possesses its own servo actuator, each wheel may assume a unique steering orientation depending on the desired vehicle motion.

The crab angle, denoted by β, is defined as the angle between the actual translational velocity vector of the vehicle and its longitudinal axis. Unlike the steering angle, which is a local wheel variable, the crab angle represents a global vehicle-level motion variable. When the vehicle travels directly forward, the crab angle equals zero degrees. During pure lateral motion, the crab angle approaches ninety degrees. Diagonal motion corresponds to intermediate crab angles between these two limiting cases.

Under ideal crab motion conditions, every steering module adopts exactly the same steering angle. Consequently,

\\theta_1=\\theta_2=\\theta_3=\\theta_4=\\beta

This equation expresses the simplest relationship between steering orientation and vehicle motion. Since all wheels roll in parallel directions without rotational motion, the vehicle translates exactly along the direction defined by the common steering angle.

More generally, the crab angle can be derived directly from the desired vehicle velocity components. Using the longitudinal and lateral velocities,

\\beta=atan2(V_y,V_x)

This equation defines the overall direction of vehicle motion regardless of the individual steering configuration. The inverse kinematic controller subsequently computes steering angles that align the wheel rolling directions with this desired motion vector.

When rotational motion is absent, the steering angle for every wheel equals the crab angle

\\theta_i=\\beta

However, once rotational velocity is introduced, the relationship becomes more complex. Each wheel experiences a different local velocity due to the rotational component of rigid-body motion. The steering angle must therefore compensate for both translational and rotational velocities simultaneously,

\\theta_i=atan2(V_y+\\Omega x_i,;V_x-\\Omega y_i)

while the crab angle remains

\\beta=atan2(V_y,V_x)

This distinction illustrates that the crab angle describes overall vehicle translation, whereas steering angles describe local wheel orientations required to generate that motion.

The difference between steering angle and crab angle increases as yaw rate increases. During pure forward travel or pure crab motion, both angles remain identical because rotational velocity is zero. During turning maneuvers, however, steering angles diverge according to wheel position while the crab angle continues representing the average translational direction of the chassis. Consequently, the crab angle may remain constant even though every steering module continuously changes orientation during coordinated turning.

Steering optimization algorithms frequently exploit this relationship. Because many steer-drive modules can rotate continuously through more than 360 degrees, multiple steering solutions may correspond to the same crab angle. The controller evaluates alternative steering configurations by minimizing steering displacement, actuator energy consumption, transition time, or cable twisting. In many situations, rotating a steering module by 180 degrees while reversing wheel rotation produces an equivalent rolling direction with significantly less steering movement.

Smooth transitions between different crab angles require careful trajectory planning. Sudden changes in crab angle demand rapid steering motion, potentially increasing actuator loading and reducing passenger or payload comfort. Modern motion controllers therefore employ continuous interpolation of crab angle trajectories, allowing steering modules to rotate gradually while preserving smooth vehicle motion. Model Predictive Control algorithms frequently anticipate future trajectory segments and begin steering adjustments before large direction changes occur.

Sensor feedback is essential for maintaining the desired crab angle during operation. Wheel encoders verify propulsion velocity, steering encoders measure actual steering orientation, inertial measurement units monitor vehicle heading, and external localization systems estimate translational direction. Closed-loop controllers continuously compare the measured crab angle with the desired reference, applying small steering corrections whenever discrepancies arise due to wheel slip, floor irregularities, or payload disturbances.

Crab angle estimation also contributes to fault detection. Significant disagreement between predicted crab angle and measured vehicle motion may indicate steering actuator malfunction, encoder failure, tire damage, or excessive wheel slip. Diagnostic software monitors these relationships continuously, allowing predictive maintenance algorithms to identify abnormal system behavior before serious performance degradation occurs.

The mathematical relationship between crab angle and steering angle provides an elegant framework connecting vehicle-level motion planning with wheel-level actuator control. By distinguishing global translational direction from local steering orientation, modern steer-drive controllers achieve highly accurate multidirectional motion while maintaining smooth transitions, efficient actuator utilization, and exceptional positioning precision. As industrial autonomous mobile robots continue expanding into increasingly demanding manufacturing and logistics environments, precise modeling of this relationship will remain an essential component of advanced Four-Wheel Steering control systems.

### 2.1 완전 측면 이동(Full Lateral Motion) 방정식

크랩 주행(Crab Motion)은 완전 측면 이동(Full Lateral Motion)이라고도 하며, 4륜 조향(Four-Wheel Steering, 4WS) 스티어-드라이브(Steer-Drive) 이동 로봇의 가장 대표적인 기능 가운데 하나이다. 일반적인 비홀로노믹(Non-Holonomic) 차량은 측면으로 이동하기 위해 먼저 차체를 회전해야 하지만, 스티어-드라이브 플랫폼은 차체의 방향을 유지한 채 측면으로 평행 이동할 수 있다. 이러한 동작은 모든 독립 휠 모듈(Independent Wheel Module)의 조향각(Steering Angle)과 휠 속도(Wheel Velocity)를 동일하게 동기화하여 모든 바퀴가 같은 방향으로 구르도록 함으로써 구현된다. 바퀴가 측면으로 미끄러질 필요가 없기 때문에 크랩 주행은 매우 부드러운 이동, 높은 위치 정밀도(Positioning Accuracy), 낮은 타이어 마모(Tire Wear)를 제공하며, 정밀 산업 환경에 매우 적합하다.

완전 측면 이동의 운동학(Kinematics)은 일반적인 평면 강체(Planar Rigid-Body) 속도 모델(Velocity Model)에서 시작한다. 차량의 운동은 종방향 속도(Longitudinal Velocity, (V_x)), 횡방향 속도(Lateral Velocity, (V_y)), 요 레이트(Yaw Rate, (\\Omega))의 세 변수로 표현된다. 이 세 변수는 2차원 평면에서 로봇의 병진 운동(Translational Motion)과 회전 운동(Rotational Motion)을 모두 기술한다.

이상적인 크랩 주행에서는 종방향 이동과 회전 운동을 제거하고 일정한 횡방향 속도만 유지하는 것이 목적이다. 따라서 차량의 목표 운동은 다음과 같이 정의된다.

V_x = 0

V_y = V_c

\\Omega = 0

여기서 (V_c)는 명령된 크랩 속도(Commanded Crab Velocity)를 의미한다.

이 조건을 강체 운동학 방정식(Rigid-Body Kinematic Equation)에 대입하면 모든 바퀴의 국부 속도(Local Velocity)가 매우 단순해진다. 회전 성분이 사라지고 종방향 이동도 존재하지 않으므로, 차체 내 위치와 관계없이 모든 바퀴는 동일한 속도 벡터(Velocity Vector)를 가진다. 따라서 각 휠의 속도 성분은 다음과 같이 된다.

V_{xi}=0

V_{yi}=V_c

즉, 모든 휠 모듈은 횡방향 축을 따라 동일한 속도 벡터를 생성한다. 회전 주행에서는 각 바퀴의 속도가 순간 회전 중심(Instantaneous Center of Rotation, ICR)까지의 거리와 위치에 따라 달라지지만, 크랩 주행에서는 모든 바퀴가 동일한 속도로 회전하며 동일한 조향각을 유지한다.

각 바퀴의 조향 방향은 원하는 속도 벡터와 바퀴의 구름 방향(Rolling Direction)이 일치하도록 결정된다. 역운동학(Inverse Kinematics)의 일반식은 다음과 같다.

\\theta_i = atan2(V_{yi},V_{xi})

여기에 위 조건을 적용하면

\\theta_i = atan2(V_c,0)

이 된다.

양의 방향으로 측면 이동하는 경우 조향각은 약 +90°가 되며, 반대 방향으로 이동하는 경우 약 −90°가 된다. 따라서 모든 조향 모듈은 동일한 조향각을 가지게 되며 차량은 차체의 방향을 유지한 채 측면으로 이동한다.

필요한 휠 속도는 속도 벡터의 크기(Magnitude)로부터 계산된다.

v_i=\\sqrt{V_{xi}\^2+V_{yi}\^2}

종방향 속도가 0이므로

v_i=\|V_c\|

가 된다.

즉, 모든 바퀴는 동일한 선속도(Linear Velocity)로 회전하며 모터의 각속도(Angular Velocity)는

\\omega_i=\\frac{\|V_c\|}{r}

로 계산된다. 여기서 (r)은 유효 휠 반경(Effective Wheel Radius)이다.

이 수학적 모델은 크랩 주행의 중요한 특징을 보여준다. 차량 전체는 순수 병진 운동(Pure Translation)을 수행하는 것처럼 동작한다. 모든 바퀴는 동일한 속도 크기와 동일한 조향 방향을 가지며, 차동 조향 기하(Differential Steering Geometry)가 필요하지 않다. 또한 유한 평면 내에 순간 회전 중심(ICR)이 존재하지 않으며, 어느 바퀴도 추가적인 회전 속도 성분을 가지지 않는다. 이러한 대칭성(Symmetry)은 경로 계획(Motion Planning)과 제어 구현(Control Implementation)을 크게 단순화한다.

이상적인 운동학 방정식은 단순하지만 실제 구현에서는 외란(Disturbance)을 지속적으로 보정해야 한다. 각 휠 모듈의 조향각에 작은 오차만 발생해도 의도하지 않은 요 모멘트(Yaw Moment)가 생성되어 차량이 목표 방향에서 조금씩 회전하게 된다. 또한 바퀴 직경의 미세한 차이나 바닥 마찰(Floor Friction)의 불균형도 속도 차이를 유발하여 원치 않는 회전 드리프트(Rotational Drift)를 만든다. 따라서 최신 스티어-드라이브 제어기는 조향 엔코더(Steering Encoder), 휠 엔코더(Wheel Encoder), 관성측정장치(IMU), 외부 위치 인식 센서(Localization Sensor)를 이용하여 이러한 오차를 실시간으로 보정한다.

폐루프 횡방향 제어(Closed-Loop Lateral Control)는 일반적으로 계층적 피드백(Hierarchical Feedback)을 사용한다. 외부 루프(Outer Loop)는 센서 융합(Sensor Fusion)을 통해 추정한 차량 위치와 목표 횡방향 경로를 비교한다. 내부 루프(Inner Loop)는 각 휠 모듈의 조향각과 휠 속도를 고대역폭 서보 제어기(High-Bandwidth Servo Controller)를 이용하여 독립적으로 제어한다. 모든 바퀴가 독립적으로 동작하기 때문에 매우 작은 조향 보정만으로도 전체 측면 이동을 방해하지 않으면서 위치 오차를 제거할 수 있다.

대형 산업용 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)에서는 동역학(Dynamics)이 더욱 중요해진다. 급격한 측면 가속(Lateral Acceleration)이 발생하면 차량의 원래 종축(Longitudinal Axis)에 수직인 방향으로 관성력(Inertial Force)이 작용하여 좌우 바퀴 사이의 하중 이동(Load Transfer)이 발생한다. 이로 인해 수직 하중(Normal Force)이 변하고 접지력(Traction)이 달라져 휠 슬립(Wheel Slip)에 영향을 줄 수 있다. 따라서 고급 트랙션 제어(Traction Control)는 모터 전류(Motor Current)와 슬립 지표(Slip Indicator)를 지속적으로 모니터링하여 필요할 경우 토크(Torque)를 재분배함으로써 적재 하중이 변하더라도 안정적인 측면 이동을 유지한다.

에너지 효율(Energy Efficiency)도 크랩 주행의 중요한 장점이다. 모든 바퀴가 자신의 조향 방향으로 그대로 굴러가기 때문에, 타이어를 강제로 미끄러뜨리는 스키드 조향(Skid Steering) 방식보다 마찰 손실(Friction Loss)이 매우 작다. 마찰 감소는 모터 전력 소비(Power Consumption)를 줄이고 발열(Heat Generation)을 감소시키며 타이어 수명(Tire Lifetime)을 연장한다. 따라서 크랩 주행은 장시간 연속 운전이 필요한 산업용 환경에서 매우 유리하다.

완전 측면 이동은 반도체 제조(Semiconductor Manufacturing), 자동 창고(Automated Warehouse), 공작기계 이송(Machine Tending), 정밀 도킹(Precision Docking), 병원 물류(Hospital Logistics), 제약 자동화(Pharmaceutical Automation) 등에서 널리 활용된다. 이러한 응용에서는 차량을 회전시키지 않고도 측면으로 이동할 수 있기 때문에 작업 공간 활용도가 높아지고 이동 시간이 크게 감소한다. 크랩 주행의 단순한 수학적 모델과 폐루프 서보 제어를 통해 얻을 수 있는 높은 정밀도는 현대 4륜 조향 자율주행 이동 로봇의 가장 중요한 장점 가운데 하나이다.

### 2.2 크랩 각(Crab Angle)과 조향각(Steering Angle)의 관계

크랩 각(Crab Angle)과 조향각(Steering Angle)의 관계는 스티어-드라이브 이동 로봇의 측면 이동을 이해하는 가장 기본적인 개념 가운데 하나이다. 두 각도는 서로 밀접하게 관련되어 있지만 서로 다른 물리적 의미를 가진다. 조향각은 각각의 휠 모듈이 차체에 대해 어느 방향으로 회전되어 있는지를 나타내는 반면, 크랩 각은 차량 전체가 차체의 종축(Longitudinal Axis)에 대해 어느 방향으로 이동하는지를 나타낸다. 이 두 각도의 수학적 관계를 정확하게 이해하는 것은 운동학 모델(Kinematic Model) 유도, 경로 추종(Trajectory Tracking), 다방향 이동(Multidirectional Motion) 최적화에 매우 중요하다.

조향각은 각 휠 모듈마다 독립적으로 정의된다. 휠 (i)의 조향각을 (\\theta_i)라 하면 이는 차량의 전방 방향을 기준으로 측정된다. 일반적으로 오른손 좌표계(Right-Hand Coordinate System)를 사용하여 차량의 x축에서 반시계 방향을 양의 방향으로 정의한다. 각 조향 모듈은 독립적인 서보 액추에이터(Servo Actuator)를 가지므로 원하는 차량 운동에 따라 서로 다른 조향각을 가질 수 있다.

반면 크랩 각 (\\beta)는 차량의 실제 병진 속도 벡터(Translational Velocity Vector)와 차체 종축 사이의 각도로 정의된다. 조향각이 개별 휠의 국부 변수(Local Variable)인 반면, 크랩 각은 차량 전체의 전역 운동 변수(Global Motion Variable)이다. 차량이 직진할 때 크랩 각은 0°이며, 순수 측면 이동에서는 약 90°가 된다. 대각선 이동(Diagonal Motion)은 이 두 값 사이의 중간 각도를 가진다.

이상적인 크랩 주행에서는 모든 조향 모듈이 동일한 조향각을 가진다. 따라서

\\theta_1=\\theta_2=\\theta_3=\\theta_4=\\beta

가 성립한다.

이 식은 조향 방향과 차량 이동 방향 사이의 가장 단순한 관계를 나타낸다. 모든 바퀴가 서로 평행한 방향으로 구르고 차량에 회전 운동이 없기 때문에 차량은 공통 조향각이 가리키는 방향으로 그대로 이동한다.

보다 일반적으로 크랩 각은 차량의 종방향 및 횡방향 속도로부터 직접 계산된다.

\\beta=atan2(V_y,V_x)

이 식은 개별 휠의 조향 상태와 관계없이 차량 전체의 이동 방향을 정의한다. 이후 역운동학 제어기(Inverse Kinematic Controller)는 각 휠의 조향 방향을 이 속도 벡터와 일치하도록 계산한다.

회전 운동이 없는 경우에는

\\theta_i=\\beta

가 성립한다.

그러나 차량에 회전 속도(Rotational Velocity)가 추가되면 상황은 달라진다. 강체 회전(Rigid-Body Rotation)에 의해 각 휠은 서로 다른 국부 속도를 가지게 되므로 조향각은 병진 운동과 회전 운동을 동시에 고려해야 한다.

\\theta_i=atan2(V_y+\\Omega x_i,;V_x-\\Omega y_i)

반면 크랩 각은 여전히

\\beta=atan2(V_y,V_x)

로 정의된다.

즉, 크랩 각은 차량 전체의 이동 방향을 나타내고, 조향각은 그 이동을 실제로 만들어 내기 위해 각 휠이 가져야 하는 방향을 나타낸다.

조향각과 크랩 각의 차이는 요 레이트(Yaw Rate)가 증가할수록 커진다. 순수 직진이나 순수 크랩 주행에서는 회전 운동이 없으므로 두 각은 동일하다. 그러나 회전 주행에서는 휠의 위치에 따라 각 조향각이 서로 달라지며, 크랩 각은 차량 전체의 평균 이동 방향을 계속 나타낸다. 따라서 차량의 크랩 각이 일정하더라도 각 조향 모듈은 지속적으로 서로 다른 방향으로 회전하게 된다.

조향 최적화 알고리즘(Steering Optimization Algorithm)은 이러한 관계를 적극 활용한다. 많은 스티어-드라이브 모듈은 360° 이상 연속 회전할 수 있기 때문에 하나의 크랩 각에 대해 여러 개의 조향 해(Steering Solution)가 존재할 수 있다. 제어기는 조향 이동량(Steering Displacement), 액추에이터 에너지 소비(Energy Consumption), 전환 시간(Transition Time), 케이블 꼬임(Cable Twisting) 등을 고려하여 가장 효율적인 조향 구성을 선택한다. 예를 들어 조향 모듈을 180° 회전시키는 대신 바퀴의 회전 방향을 반대로 바꾸면 동일한 이동 방향을 훨씬 적은 조향 움직임으로 구현할 수 있다.

크랩 각이 연속적으로 변할 때 부드러운 전환(Smooth Transition)을 구현하는 것도 매우 중요하다. 갑작스러운 크랩 각 변화는 조향 모터에 큰 부하를 주고 탑재물(Payload)의 안정성을 저하시킬 수 있다. 따라서 최신 모션 제어기(Motion Controller)는 크랩 각 궤적(Crab Angle Trajectory)을 연속적으로 보간(Interpolation)하여 조향 모듈이 점진적으로 회전하도록 한다. 모델 예측 제어(Model Predictive Control, MPC)는 미래의 경로를 미리 예측하여 큰 방향 변화가 발생하기 전에 조향을 시작하기도 한다.

센서 피드백(Sensor Feedback)은 원하는 크랩 각을 유지하는 데 필수적이다. 휠 엔코더는 추진 속도를 측정하고, 조향 엔코더는 실제 조향각을 측정하며, IMU는 차량의 자세를 추정하고, 외부 위치 인식 시스템(Localization System)은 실제 이동 방향을 계산한다. 폐루프 제어기(Closed-Loop Controller)는 측정된 크랩 각과 목표 크랩 각을 지속적으로 비교하여 휠 슬립, 바닥의 불균일성, 적재물 변화 등으로 발생하는 오차를 실시간으로 보정한다.

크랩 각 추정(Crab Angle Estimation)은 고장 진단(Fault Detection)에도 활용된다. 예측된 크랩 각과 실제 차량 이동 방향 사이에 큰 차이가 발생하면 조향 액추에이터 고장, 엔코더 오류, 타이어 손상, 과도한 휠 슬립 등이 발생했을 가능성이 있다. 진단 소프트웨어(Diagnostic Software)는 이러한 관계를 지속적으로 감시하여 심각한 성능 저하가 발생하기 전에 예지 보전(Predictive Maintenance)을 수행할 수 있도록 한다.

크랩 각과 조향각의 수학적 관계는 차량 수준의 운동 계획(Vehicle-Level Motion Planning)과 휠 수준의 액추에이터 제어(Wheel-Level Actuator Control)를 연결하는 매우 우아한 프레임워크를 제공한다. 차량 전체의 이동 방향과 각 바퀴의 조향 방향을 명확하게 구분함으로써 현대의 스티어-드라이브 제어기는 매우 높은 위치 정밀도(Positioning Precision), 부드러운 방향 전환(Smooth Transition), 효율적인 액추에이터 활용(Efficient Actuator Utilization), 정확한 다방향 이동(Multidirectional Motion)을 동시에 실현할 수 있다. 산업용 자율주행 이동 로봇이 점점 더 복잡한 제조 및 물류 환경으로 확대됨에 따라, 이러한 크랩 각과 조향각의 관계를 정확하게 모델링하는 것은 앞으로도 첨단 4륜 조향 제어 시스템의 핵심 기술로 남을 것이다.

##  

## 03 Zero-radius turn kinematics

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Zero Radius Rotation Conditions

Zero-radius rotation is one of the most distinctive motion capabilities of a Four-Wheel Steering (4WS) steer-drive mobile robot. Unlike conventional wheeled vehicles that require a finite turning radius to change heading, a steer-drive platform can rotate about its own geometric center while maintaining an essentially constant translational position. This maneuver is commonly referred to as in-place rotation or zero-radius turning because the instantaneous center of rotation coincides with the geometric center of the vehicle. Such motion dramatically improves maneuverability in confined industrial environments and has become an essential capability for modern autonomous mobile robots operating in warehouses, semiconductor factories, hospitals, automated production lines, and precision inspection facilities.

The mathematical condition for zero-radius rotation is derived directly from planar rigid-body kinematics. Vehicle motion on a two-dimensional plane is completely described by three independent variables: longitudinal velocity (V_x), lateral velocity (V_y), and yaw rate (\\Omega). During ideal zero-radius rotation, the vehicle does not translate in either the longitudinal or lateral direction. Instead, it generates only rotational motion about its vertical axis. Therefore, the desired motion condition is defined as

[

V_x = 0

]

[

V_y = 0

]

[

\\Omega \\neq 0

]

This condition indicates that the entire vehicle remains stationary in position while continuously changing its orientation.

The velocity experienced by each wheel results entirely from the rotational motion of the chassis. According to rigid-body kinematics, the local velocity components at wheel i located at coordinates ((x_i, y_i)) become

[

V_{xi}=-\\Omega y_i

]

[

V_{yi}=\\Omega x_i

]

These equations show that each wheel velocity depends solely on its distance from the rotational center. Wheels located farther from the center experience greater linear velocities because they travel along larger circular paths during rotation. Conversely, wheels located closer to the rotational center move more slowly while maintaining identical angular velocity.

The steering orientation for every wheel must align with the tangent of its circular trajectory. Consequently, the steering angle is determined by

[

\\theta_i

========

atan2(\\Omega x_i,-\\Omega y_i)

]

Since the angular velocity appears in both numerator and denominator, the steering angle depends only on wheel position rather than rotational speed. Every wheel therefore adopts a unique steering orientation that is tangent to an imaginary circle centered at the vehicle origin. Front and rear wheels on opposite sides of the chassis generally possess different steering angles, although geometrically symmetric vehicles produce correspondingly symmetric steering configurations.

The linear velocity required for each wheel is obtained from the magnitude of its local velocity vector,

[

v_i

===

\\sqrt{V_{xi}\^{2}+V_{yi}\^{2}}

]

Substituting the rigid-body velocity components yields

[

v_i

===

\|\\Omega\|

\\sqrt{x_i\^{2}+y_i\^{2}}

]

This equation demonstrates that wheel velocity is directly proportional to both the commanded angular velocity and the radial distance from the vehicle center. Larger vehicles therefore require higher wheel speeds than compact platforms to achieve the same rotational velocity.

An important characteristic of zero-radius rotation is that no unique finite instantaneous center of rotation exists outside the vehicle body. Instead, the center of rotation coincides exactly with the geometric center of the chassis. Every wheel simultaneously follows its own circular path while remaining tangent to that path. Since rolling occurs without intentional lateral sliding, tire scrub is greatly reduced compared with skid-steering systems that rely on friction to generate rotation.

Real industrial applications rarely satisfy the ideal assumptions perfectly. Manufacturing tolerances, tire deformation, steering backlash, wheel diameter variation, uneven payload distribution, and floor irregularities introduce small deviations from the theoretical model. These imperfections shift the effective center of rotation slightly away from the geometric center, producing unintended translational drift during rotation. High-precision steer-drive controllers continuously compensate for these disturbances using steering encoder feedback, wheel encoders, inertial measurement units, LiDAR localization, and vision-based pose estimation.

Closed-loop rotational control further improves accuracy by comparing the desired yaw rate with the measured rotational velocity obtained from the inertial measurement unit. Small steering corrections are continuously applied to maintain the desired center of rotation while minimizing accumulated positional drift. Sensor fusion algorithms combine wheel odometry with inertial and external localization measurements to estimate the true vehicle pose throughout the maneuver.

Dynamic effects become increasingly important for heavy industrial autonomous mobile robots. As payload mass increases, rotational inertia rises proportionally, requiring greater drive torque to initiate and terminate rotational motion. Abrupt acceleration may introduce structural vibration, load oscillation, or temporary wheel slip. Consequently, modern motion controllers employ jerk-limited rotational profiles that gradually increase angular acceleration while preserving smooth dynamic behavior and minimizing mechanical stress.

Zero-radius rotation also provides significant operational advantages within confined workspaces. The ability to change heading without requiring additional floor space simplifies navigation around densely packed manufacturing equipment, narrow warehouse aisles, automated storage systems, and robotic production cells. Robots carrying large payloads can accurately orient themselves before docking or manipulation tasks without performing repeated forward and reverse repositioning maneuvers. This capability directly improves productivity, reduces travel distance, and increases overall operational efficiency.

From a control perspective, zero-radius rotation represents a special case of the general steer-drive kinematic model in which translational motion is completely eliminated while rotational motion remains active. Although mathematically straightforward, practical implementation requires highly synchronized steering, precise wheel velocity regulation, accurate sensor feedback, and robust disturbance compensation. These conditions collectively enable steer-drive platforms to achieve smooth, precise, and energy-efficient rotational motion that significantly exceeds the maneuverability of conventional wheeled mobile robots.

---

### 3.2 Angular Velocity Control Equations

Angular velocity control constitutes the fundamental control mechanism responsible for regulating rotational motion in a Four-Wheel Steering steer-drive platform. While the kinematic equations determine the steering orientations and wheel velocities required for zero-radius turning, the angular velocity controller ensures that the vehicle follows the desired rotational speed accurately despite disturbances, payload variations, actuator nonlinearities, and changing environmental conditions. Precise angular velocity regulation is essential for trajectory tracking, precision docking, multidirectional navigation, and coordinated fleet operation.

The desired rotational motion is specified by the reference yaw rate

[

\\Omega_d

]

where (\\Omega_d) represents the commanded angular velocity generated by the navigation system or trajectory planner. The actual yaw rate

[

\\Omega_m

]

is measured continuously by the inertial measurement unit or estimated through sensor fusion. The rotational velocity error is therefore defined as

[

e_{\\Omega}

==========

\\Omega_d-\\Omega_m

]

This error represents the difference between desired and measured rotational motion and serves as the primary input to the rotational controller.

Most industrial steer-drive platforms employ Proportional--Integral--Derivative (PID) control for angular velocity regulation. The control law is expressed as

[

u(t)

====

K_Pe_{\\Omega}

\+

K_I

\\int e_{\\Omega}dt

\+

K_D

\\frac{de_{\\Omega}}{dt}

]

where (u(t)) denotes the commanded rotational control effort, and (K_P), (K_I), and (K_D) are the proportional, integral, and derivative gains respectively.

The proportional term generates an immediate response proportional to the rotational error, allowing the controller to react rapidly whenever the measured yaw rate deviates from the reference value. The integral component eliminates steady-state error caused by persistent disturbances such as uneven floor friction or asymmetric payload distribution. The derivative term predicts future error evolution by observing the rate of change of the yaw error, thereby improving damping and reducing overshoot during rapid rotational maneuvers.

The commanded angular velocity must subsequently be converted into individual wheel velocities using the inverse kinematic equations. For wheel i located at radial distance

[

R_i

===

\\sqrt{x_i\^{2}+y_i\^{2}}

]

the desired wheel velocity becomes

[

v_i

===

\\Omega_dR_i

]

and the corresponding motor angular velocity is calculated as

[

\\omega_i

========

\\frac{\\Omega_dR_i}{r}

]

where (r) denotes the effective wheel radius.

These equations indicate that wheels positioned farther from the vehicle center require proportionally higher rotational speeds. Nevertheless, all wheels maintain the same vehicle angular velocity because their linear velocities scale according to their radial positions.

Modern industrial controllers incorporate feedforward compensation in addition to conventional feedback control. Rather than relying solely on measured error, the controller predicts the torque required to overcome vehicle inertia and friction during acceleration. Feedforward control significantly improves transient response during rapid direction changes while reducing the workload of the feedback controller.

Acceleration limiting is another important component of angular velocity control. Sudden changes in rotational velocity generate large inertial forces acting on transported payloads and increase mechanical stress within the steering and drive systems. Motion planners therefore generate jerk-limited angular velocity profiles that smoothly transition between rotational speeds. These profiles minimize vibration, reduce wheel slip, and improve passenger or payload comfort.

Adaptive control techniques further enhance rotational performance under varying operating conditions. Vehicle inertia changes significantly with payload mass, while tire characteristics vary with temperature, wear, and floor material. Adaptive controllers estimate these changing system parameters online and continuously update controller gains to maintain consistent rotational behavior without requiring manual retuning.

Sensor fusion plays an essential role in angular velocity estimation. The inertial measurement unit provides high-frequency rotational measurements but suffers from long-term drift. Wheel odometry offers independent rotational estimates yet becomes inaccurate during wheel slip. LiDAR localization and visual odometry provide globally consistent orientation estimates at lower update frequencies. Extended Kalman Filters or factor graph optimization combine these heterogeneous measurements into a robust estimate of vehicle angular velocity and heading.

Safety functions are tightly integrated into angular velocity control. Maximum allowable rotational velocity depends on payload characteristics, center of gravity, available floor friction, and surrounding environmental constraints. Safety controllers continuously monitor these factors and automatically reduce rotational speed whenever stability margins decrease. Emergency braking functions synchronize all wheel modules to generate stable deceleration while preventing excessive tire slip or uncontrolled vehicle rotation.

Angular velocity regulation also supports coordinated multi-robot operation. Fleet management systems frequently require multiple autonomous mobile robots to perform synchronized rotational maneuvers while sharing confined workspaces. Accurate yaw control enables predictable vehicle behavior, simplifies collision avoidance planning, and improves overall traffic efficiency within automated production environments.

As industrial autonomous mobile robots continue expanding into applications requiring increasingly precise multidirectional mobility, angular velocity control becomes progressively more sophisticated. Advanced control strategies incorporating Model Predictive Control, adaptive estimation, feedforward compensation, and AI-assisted parameter optimization continue improving rotational accuracy, energy efficiency, and dynamic stability. Together with steer-drive kinematics, these control equations establish the mathematical and algorithmic foundation enabling modern Four-Wheel Steering platforms to achieve exceptionally smooth, accurate, and reliable rotational motion in demanding industrial environments.

### 3.1 제로 반경 회전(Zero Radius Rotation) 조건

제로 반경 회전(Zero-Radius Rotation)은 4륜 조향(Four-Wheel Steering, 4WS) 스티어-드라이브(Steer-Drive) 이동 로봇의 가장 대표적인 운동 기능 가운데 하나이다. 일반적인 바퀴형 차량은 방향을 변경하기 위해 일정한 회전 반경(Turning Radius)이 필요하지만, 스티어-드라이브 플랫폼은 차량의 병진 위치(Translational Position)를 거의 유지한 상태에서 자신의 기하학적 중심(Geometric Center)을 기준으로 직접 회전할 수 있다. 이러한 동작은 제자리 회전(In-Place Rotation) 또는 제로 반경 회전이라고 하며, 순간 회전 중심(Instantaneous Center of Rotation, ICR)이 차량의 기하학적 중심과 정확히 일치하기 때문에 붙여진 이름이다. 이러한 회전 방식은 제한된 산업 환경에서 기동성(Maneuverability)을 크게 향상시키며, 창고(Warehouse), 반도체 공장(Semiconductor Factory), 병원(Hospital), 자동화 생산라인(Automated Production Line), 정밀 검사 설비(Precision Inspection Facility)에서 운용되는 현대 자율주행 이동 로봇(Autonomous Mobile Robot, AMR)의 핵심 기능이 되었다.

제로 반경 회전의 수학적 조건은 평면 강체 운동학(Planar Rigid-Body Kinematics)으로부터 직접 유도된다. 2차원 평면에서 차량의 운동은 종방향 속도(Longitudinal Velocity, (V_x)), 횡방향 속도(Lateral Velocity, (V_y)), 요 레이트(Yaw Rate, (\\Omega))의 세 변수로 완전히 표현된다. 이상적인 제로 반경 회전에서는 차량이 종방향이나 횡방향으로 전혀 이동하지 않고, 수직축을 중심으로 회전 운동만 수행한다. 따라서 목표 운동 조건은 다음과 같이 정의된다.

[

V_x = 0

]

[

V_y = 0

]

[

\\Omega \\neq 0

]

이 조건은 차량의 위치는 그대로 유지하면서 자세(Orientation)만 지속적으로 변화함을 의미한다.

각 바퀴에서 발생하는 속도는 차체의 회전 운동에 의해서만 결정된다. 강체 운동학에 따르면, 좌표 ((x_i, y_i))에 위치한 (i)번째 바퀴의 국부 속도(Local Velocity)는 다음과 같이 표현된다.

[

V_{xi}=-\\Omega y_i

]

[

V_{yi}=\\Omega x_i

]

이 식은 각 바퀴의 속도가 오직 회전 중심(Rotational Center)으로부터의 거리에 의해서만 결정됨을 보여준다. 중심에서 멀리 위치한 바퀴는 더 큰 원 궤적(Circular Path)을 따라 이동하므로 더 큰 선속도(Linear Velocity)를 가지며, 중심에 가까운 바퀴는 동일한 각속도(Angular Velocity)를 유지하면서 더 낮은 선속도로 움직인다.

각 바퀴의 조향 방향(Steering Orientation)은 원운동 궤적의 접선 방향(Tangent Direction)과 일치해야 한다. 따라서 조향각(Steering Angle)은 다음과 같이 계산된다.

[

\\theta_i = atan2(\\Omega x_i,-\\Omega y_i)

]

각속도 (\\Omega)는 분자와 분모에 동시에 포함되므로 실제 조향각은 회전 속도가 아니라 바퀴의 위치에만 의존한다. 결과적으로 모든 바퀴는 차량 중심을 기준으로 하는 가상의 원에 접하는 방향으로 각각 다른 조향각을 가진다. 일반적으로 차체의 좌우 또는 전후에 위치한 바퀴는 서로 다른 조향각을 가지지만, 기하학적으로 대칭인 차량에서는 대칭적인 조향 구성을 형성한다.

각 바퀴에 필요한 선속도는 국부 속도 벡터(Local Velocity Vector)의 크기로부터 계산된다.

[

v_i=\\sqrt{V_{xi}\^{2}+V_{yi}\^{2}}

]

이를 위의 강체 운동학 식에 대입하면 다음과 같다.

[

v_i=\|\\Omega\|\\sqrt{x_i\^{2}+y_i\^{2}}

]

이 식은 휠 속도가 차량의 각속도와 차량 중심으로부터의 반경 거리(Radial Distance)에 비례함을 보여준다. 따라서 차량의 크기가 커질수록 동일한 회전 속도를 얻기 위해서는 더 높은 휠 속도가 필요하다.

제로 반경 회전의 가장 중요한 특징은 차량 외부에 유한한 순간 회전 중심(ICR)이 존재하지 않는다는 점이다. 회전 중심은 차량의 기하학적 중심과 정확히 일치하며, 모든 바퀴는 각자의 원 궤적을 따라 움직이면서 항상 접선 방향으로 정렬된다. 또한 바퀴는 의도적인 측면 미끄러짐(Lateral Sliding) 없이 순수 구름 운동(Pure Rolling)을 수행하므로, 회전을 위해 마찰에 의존하는 스키드 조향(Skid Steering) 방식보다 타이어 마모(Tire Scrub)가 크게 감소한다.

실제 산업 환경에서는 이상적인 가정을 완전히 만족하기 어렵다. 제조 공차(Manufacturing Tolerance), 타이어 변형(Tire Deformation), 조향 백래시(Steering Backlash), 휠 직경 편차(Wheel Diameter Variation), 적재 하중 불균형(Uneven Payload Distribution), 바닥의 불균일성(Floor Irregularity)은 모두 이론 모델과의 차이를 발생시킨다. 이러한 요인은 실제 회전 중심을 기하학적 중심에서 약간 벗어나게 하며, 회전 중 원하지 않는 병진 이동(Translational Drift)을 유발한다. 따라서 고정밀 스티어-드라이브 제어기는 조향 엔코더(Steering Encoder), 휠 엔코더(Wheel Encoder), 관성측정장치(IMU), LiDAR 기반 위치 추정(Localization), 비전 기반 자세 추정(Vision-Based Pose Estimation)을 이용하여 이러한 외란을 지속적으로 보정한다.

폐루프 회전 제어(Closed-Loop Rotational Control)는 원하는 요 레이트와 IMU에서 측정한 실제 회전 속도를 비교하여 정확도를 향상시킨다. 제어기는 작은 조향 보정을 지속적으로 수행하여 회전 중심을 유지하고 위치 드리프트를 최소화한다. 또한 센서 융합(Sensor Fusion)은 휠 오도메트리(Wheel Odometry), IMU, 외부 위치 인식 시스템의 정보를 결합하여 회전 중 차량의 실제 자세(Pose)를 정확하게 추정한다.

대형 산업용 자율주행 이동 로봇에서는 동역학(Dynamics)이 더욱 중요해진다. 적재 하중(Payload Mass)이 증가하면 회전 관성(Rotational Inertia)이 증가하여 회전을 시작하거나 멈추기 위해 더 큰 구동 토크(Drive Torque)가 필요하다. 급격한 가속은 구조 진동(Structural Vibration), 적재물 흔들림(Load Oscillation), 일시적인 휠 슬립을 유발할 수 있다. 따라서 최신 모션 제어기는 저크 제한(Jerk-Limited) 회전 프로파일(Profile)을 사용하여 각가속도(Angular Acceleration)를 점진적으로 증가시키고, 부드러운 동적 거동과 낮은 기계적 응력을 유지한다.

제로 반경 회전은 협소한 작업 공간에서도 매우 큰 장점을 제공한다. 추가적인 회전 공간 없이 방향을 변경할 수 있으므로 밀집된 제조 설비, 좁은 창고 통로, 자동 보관 시스템, 로봇 생산 셀 주변에서의 이동이 훨씬 쉬워진다. 또한 대형 적재물을 운반하는 로봇도 전후진을 반복하지 않고 정확한 자세로 도킹(Docking)이나 조작(Manipulation)을 수행할 수 있다. 이러한 특성은 생산성을 향상시키고 이동 거리를 줄이며 전체 작업 효율을 높인다.

제어 관점(Control Perspective)에서 제로 반경 회전은 일반적인 스티어-드라이브 운동학 모델의 특수한 경우이다. 병진 운동은 완전히 제거되고 회전 운동만 존재한다. 수학적으로는 단순하지만 실제 구현에서는 모든 휠의 조향 동기화(Steering Synchronization), 정확한 휠 속도 제어(Wheel Velocity Regulation), 정밀한 센서 피드백(Sensor Feedback), 강건한 외란 보상(Disturbance Compensation)이 반드시 필요하다. 이러한 요소들이 결합되어 스티어-드라이브 플랫폼은 기존 바퀴형 이동 로봇보다 훨씬 뛰어난 부드러움, 정밀도, 에너지 효율을 가진 회전 성능을 달성할 수 있다.

---

### 3.2 각속도(Angular Velocity) 제어 방정식

각속도 제어(Angular Velocity Control)는 4륜 조향(Four-Wheel Steering) 스티어-드라이브 플랫폼의 회전 운동을 제어하는 핵심 메커니즘이다. 운동학 방정식(Kinematic Equation)은 제자리 회전에 필요한 조향각과 휠 속도를 계산하지만, 각속도 제어기는 외란(Disturbance), 적재 하중 변화(Payload Variation), 액추에이터 비선형성(Actuator Nonlinearity), 환경 변화(Environmental Condition)가 존재하더라도 차량이 원하는 회전 속도를 정확하게 추종하도록 만든다. 정밀한 각속도 제어는 경로 추종(Trajectory Tracking), 정밀 도킹(Precision Docking), 다방향 이동(Multidirectional Navigation), 다중 로봇 협업(Coordinated Fleet Operation)에 필수적인 요소이다.

목표 회전 운동은 기준 요 레이트(Reference Yaw Rate)

[

\\Omega_d

]

로 정의된다. 여기서 (\\Omega_d)는 내비게이션 시스템(Navigation System) 또는 경로 계획기(Trajectory Planner)가 생성한 목표 각속도(Commanded Angular Velocity)를 의미한다.

실제 요 레이트는

[

\\Omega_m

]

으로 표현되며, IMU 또는 센서 융합을 통해 지속적으로 측정된다.

따라서 회전 속도 오차는 다음과 같이 정의된다.

[

e_{\\Omega}=\\Omega_d-\\Omega_m

]

이 오차는 목표 회전 속도와 실제 회전 속도의 차이를 의미하며 회전 제어기의 입력으로 사용된다.

대부분의 산업용 스티어-드라이브 플랫폼은 각속도 제어에 PID(Proportional--Integral--Derivative) 제어기를 사용한다. 제어식은 다음과 같다.

[

u(t)=K_Pe_{\\Omega}+K_I\\int e_{\\Omega}dt+K_D\\frac{de_{\\Omega}}{dt}

]

여기서 (u(t))는 회전을 위한 제어 입력(Control Effort)이며, (K_P), (K_I), (K_D)는 각각 비례(Proportional), 적분(Integral), 미분(Derivative) 이득(Gain)이다.

비례 항(Proportional Term)은 회전 오차에 비례하는 즉각적인 제어를 수행하여 실제 요 레이트가 목표값에서 벗어날 경우 빠르게 반응한다. 적분 항(Integral Term)은 바닥 마찰의 불균형이나 적재물의 비대칭과 같은 지속적인 외란으로 발생하는 정상 상태 오차(Steady-State Error)를 제거한다. 미분 항(Derivative Term)은 오차의 변화율을 이용하여 미래 오차를 예측하고 감쇠(Damping)를 향상시키며 급격한 회전에서 오버슈트(Overshoot)를 줄인다.

제어된 각속도는 역운동학(Inverse Kinematics)을 통해 각 바퀴의 속도로 변환된다. 차량 중심으로부터 반경 거리

[

R_i=\\sqrt{x_i\^{2}+y_i\^{2}}

]

에 위치한 (i)번째 바퀴의 목표 선속도는

[

v_i=\\Omega_dR_i

]

이며, 대응하는 모터 각속도는

[

\\omega_i=\\frac{\\Omega_dR_i}{r}

]

로 계산된다.

여기서 (r)은 유효 휠 반경(Effective Wheel Radius)이다.

이 식은 차량 중심에서 멀리 위치한 바퀴일수록 더 높은 회전 속도가 필요함을 의미한다. 그러나 모든 바퀴는 반경 거리에 비례하는 선속도를 가지므로 차량 전체는 동일한 각속도로 회전한다.

현대 산업용 제어기는 일반적인 피드백 제어 외에도 피드포워드 보상(Feedforward Compensation)을 함께 사용한다. 피드백 오차만을 이용하는 대신 차량의 관성과 마찰을 고려하여 필요한 토크를 미리 예측함으로써 급격한 방향 전환 시 응답 속도를 향상시키고 피드백 제어기의 부담을 줄인다.

각가속도 제한(Acceleration Limiting)도 중요한 요소이다. 급격한 회전 속도 변화는 적재물에 큰 관성력을 발생시키고 조향 및 구동 시스템에 높은 기계적 응력을 유발한다. 따라서 모션 계획기는 저크 제한(Jerk-Limited) 각속도 프로파일을 생성하여 회전 속도가 부드럽게 변화하도록 한다. 이러한 프로파일은 진동을 줄이고 휠 슬립을 감소시키며 적재물과 승객의 안정성을 향상시킨다.

적응 제어(Adaptive Control)는 변화하는 운용 조건에서도 회전 성능을 유지하기 위해 사용된다. 적재 하중이 증가하면 차량의 관성이 크게 변하며, 타이어 특성도 온도, 마모, 바닥 재질에 따라 달라진다. 적응 제어기는 이러한 시스템 파라미터를 실시간으로 추정하여 PID 이득을 자동으로 조정함으로써 수동 튜닝 없이도 일정한 회전 성능을 유지한다.

센서 융합(Sensor Fusion)은 각속도 추정에서도 매우 중요하다. IMU는 높은 주기로 회전 속도를 측정하지만 장기적인 드리프트(Drift)가 발생한다. 휠 오도메트리는 독립적인 회전 정보를 제공하지만 휠 슬립 시 오차가 증가한다. LiDAR 기반 위치 추정과 비전 오도메트리(Visual Odometry)는 낮은 주기로 전역 방향(Global Orientation)을 정확하게 제공한다. 확장 칼만 필터(Extended Kalman Filter, EKF)나 팩터 그래프 최적화(Factor Graph Optimization)는 이러한 다양한 센서 정보를 결합하여 강건한 차량의 각속도와 자세를 추정한다.

안전 기능(Safety Function)은 각속도 제어와 긴밀하게 통합된다. 허용 가능한 최대 회전 속도는 적재 하중, 무게 중심(Center of Gravity), 바닥 마찰, 주변 환경에 따라 달라진다. 안전 제어기는 이러한 조건을 지속적으로 감시하며 안정성이 감소하면 자동으로 회전 속도를 제한한다. 또한 비상 제동(Emergency Braking)은 모든 휠을 동시에 제어하여 과도한 슬립이나 제어 불가능한 회전을 방지한다.

각속도 제어는 다중 로봇 협업(Coordinated Multi-Robot Operation)에도 중요한 역할을 한다. 플릿 관리 시스템(Fleet Management System)은 여러 대의 AMR이 좁은 공간에서 동시에 회전 동작을 수행하도록 요구하는 경우가 많다. 정확한 요 제어(Yaw Control)는 차량의 움직임을 예측 가능하게 하여 충돌 회피 계획(Collision Avoidance Planning)을 단순화하고 자동화 생산 환경의 전체 교통 효율을 향상시킨다.

산업용 자율주행 이동 로봇이 점점 더 정밀한 다방향 이동을 요구하는 분야로 확대됨에 따라 각속도 제어도 더욱 발전하고 있다. 모델 예측 제어(Model Predictive Control, MPC), 적응 추정(Adaptive Estimation), 피드포워드 보상(Feedforward Compensation), 인공지능 기반 파라미터 최적화(AI-Assisted Parameter Optimization)를 포함한 첨단 제어 기법은 회전 정밀도, 에너지 효율, 동적 안정성을 지속적으로 향상시키고 있다. 이러한 제어 방정식은 스티어-드라이브 운동학과 함께 현대 4륜 조향 플랫폼이 산업 환경에서 매우 부드럽고 정확하며 신뢰성 높은 회전 성능을 구현할 수 있도록 하는 핵심적인 수학적·알고리즘적 기반을 제공한다.

##  

## 04 Sideways motion

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Pure Lateral Movement Conditions

Pure lateral movement represents one of the defining capabilities of a Four-Wheel Steering (4WS) steer-drive mobile robot and is often referred to as true sideways translation or crab motion. Unlike conventional wheeled vehicles that must first rotate before changing their lateral position, a steer-drive platform can translate directly to the left or right while maintaining an unchanged vehicle orientation. This capability fundamentally changes the way autonomous mobile robots operate within confined industrial environments by eliminating unnecessary steering maneuvers, reducing travel distance, and improving positioning efficiency. Pure lateral movement is extensively employed in semiconductor manufacturing, precision docking, automated warehouse systems, machine tending, hospital logistics, and flexible manufacturing systems where available maneuvering space is extremely limited.

The kinematic conditions governing pure lateral movement originate from the general planar rigid-body motion equations. The motion of a mobile robot is completely described by three independent state variables consisting of longitudinal velocity (V_x), lateral velocity (V_y), and yaw rate (\\Omega). During ideal sideways translation, the vehicle must move exclusively along its lateral axis without experiencing forward motion or rotational displacement. Consequently, the desired motion condition is expressed as

[

V_x = 0

]

[

V_y = V_L

]

[

\\Omega = 0

]

where (V_L) denotes the commanded lateral velocity. These equations specify that the vehicle maintains a constant heading while translating purely sideways.

Substituting these conditions into the rigid-body velocity equations greatly simplifies the velocity distribution experienced by every wheel module. Since rotational velocity is absent and longitudinal translation is eliminated, each wheel receives an identical velocity vector regardless of its position within the chassis. The local velocity components become

[

V_{xi}=0

]

[

V_{yi}=V_L

]

The resulting velocity field is therefore completely uniform across all wheel modules. Unlike turning maneuvers, no velocity gradients exist between the front and rear wheels or between the left and right sides of the vehicle. Every wheel contributes equally to the overall translational motion.

The steering angle required for each wheel is obtained by aligning the rolling direction of the wheel with the desired velocity vector. Applying the inverse kinematic steering equation yields

[

\\theta_i

========

atan2(V_L,0)

]

For positive lateral motion, every steering module aligns at approximately ninety degrees relative to the longitudinal vehicle axis. For movement toward the opposite side, every steering module rotates to approximately negative ninety degrees. Since all wheels share identical steering orientations, the entire platform behaves as a rigid body translating laterally without generating rotational moments.

The required linear velocity for each wheel is determined from the magnitude of the local velocity vector,

[

v_i

===

\\sqrt{V_{xi}\^{2}+V_{yi}\^{2}}

\|V_L\|

]

Accordingly, every drive motor operates at the same rotational speed,

[

\\omega_i

========

\\frac{\|V_L\|}{r}

]

where (r) represents the effective wheel radius. Equal wheel velocities guarantee uniform force generation across the vehicle and prevent unintended rotational disturbances.

Pure lateral movement assumes ideal rolling conditions in which lateral tire slip is negligible. Under these assumptions, every wheel rolls precisely along its steering direction while generating traction only in the commanded direction of travel. Unlike skid-steering systems, no intentional tire scrubbing is required to produce sideways displacement. Consequently, rolling resistance remains relatively low, mechanical wear is minimized, and energy efficiency is significantly improved.

Although the mathematical model appears relatively simple, maintaining ideal lateral motion in practice requires continuous compensation for numerous disturbances. Slight steering angle deviations between wheel modules immediately introduce yaw moments that gradually rotate the vehicle away from its desired heading. Differences in wheel diameter, uneven tire wear, varying floor friction coefficients, payload imbalance, and structural compliance all contribute to unwanted translational and rotational errors. High-precision steer-drive controllers therefore continuously estimate vehicle motion using steering encoders, wheel encoders, inertial measurement units, LiDAR localization, visual localization, and sensor fusion algorithms.

Dynamic behavior also becomes increasingly significant for heavy industrial autonomous mobile robots. Rapid lateral acceleration generates inertial forces acting perpendicular to the original vehicle heading. These forces produce load transfer between the left and right wheels, modifying available traction and potentially increasing wheel slip. Advanced traction management systems monitor motor current, wheel velocity, and estimated tire slip while dynamically redistributing drive torque to preserve stable sideways motion under changing operating conditions.

Pure lateral movement provides substantial operational advantages throughout industrial automation. Automated warehouse robots can reposition precisely beside storage racks without performing multiple steering maneuvers. Semiconductor transport vehicles carrying fragile wafer carriers minimize vibration by avoiding unnecessary rotation. Machine tending robots align directly with production equipment while maintaining optimal orientation for robotic loading operations. Hospital delivery robots navigate narrow corridors more efficiently by shifting sideways rather than repeatedly turning within restricted spaces.

From a mathematical perspective, pure lateral movement represents a special case of the general steer-drive kinematic equations in which translational motion exists exclusively along the lateral axis while rotational and longitudinal motions are eliminated. Although conceptually straightforward, successful implementation requires highly accurate steering synchronization, identical wheel velocities, continuous closed-loop feedback, robust sensor fusion, and sophisticated disturbance compensation. These combined technologies enable modern Four-Wheel Steering autonomous mobile robots to perform highly accurate sideways translation that is difficult or impossible for conventional wheeled vehicle architectures.

---

### 4.2 Steering Angle Synchronization Requirements

Steering angle synchronization is one of the most critical requirements for achieving stable and accurate sideways motion in a Four-Wheel Steering steer-drive platform. During pure lateral translation, all wheel modules must maintain nearly identical steering orientations throughout the entire maneuver. Even small deviations between steering angles generate unequal traction forces that introduce unwanted rotational moments, positional drift, and tire scrubbing. Consequently, steering synchronization forms the foundation of multidirectional motion control and directly determines the positioning accuracy, stability, efficiency, and reliability of industrial autonomous mobile robots.

The synchronization requirement begins with the ideal kinematic assumption that every steering module shares the same steering angle during pure lateral movement. Let the desired steering angle be denoted by

[

\\theta_d

========

90\^\\circ

]

for positive lateral motion. Under ideal conditions,

[

\\theta_1

========

\\theta_2

\\theta_3

\\theta_4

\\theta_d

]

This equality guarantees that every wheel rolls in precisely the same direction, thereby producing uniform lateral force across the vehicle.

In practical systems, however, steering motors inevitably experience small positioning errors due to encoder quantization, gearbox backlash, structural compliance, thermal expansion, manufacturing tolerances, and servo dynamics. Let the actual steering angle of wheel (i) be

[

\\theta_i

========

\\theta_d

\+

\\Delta\\theta_i

]

where (\\Delta\\theta_i) represents the steering angle error.

Even very small steering errors alter the direction of wheel traction. Because the generated traction force no longer acts exactly parallel to the desired lateral direction, each wheel contributes a small longitudinal force component. These longitudinal force components accumulate across the vehicle and generate unintended yaw moments. As the vehicle continues translating, these moments gradually rotate the chassis away from its intended orientation, reducing positioning accuracy and increasing path tracking error.

To quantify synchronization quality, steering controllers often define the steering synchronization error as

[

e_{\\theta}

==========

#\\max(\\theta_i)

\\min(\\theta_i)

]

This quantity measures the maximum angular difference between all steering modules. Industrial systems generally maintain synchronization errors well below one degree during precision positioning tasks, while semiconductor and inspection robots frequently require substantially tighter tolerances.

Closed-loop steering synchronization relies on high-resolution steering encoders mounted directly on every steering axis. At each control cycle, the desired steering angle generated by the inverse kinematic solver is compared with the measured steering angle,

[

e_i

===

#\\theta_d

\\theta_i

]

Each steering servo independently minimizes its own tracking error using high-bandwidth feedback control. Since all steering modules operate simultaneously through deterministic industrial communication networks such as EtherCAT, synchronized steering motion can be maintained even during rapid direction changes.

Synchronization becomes particularly important during steering transitions. When the vehicle changes from forward motion to crab motion or diagonal motion, all steering modules must rotate together while preserving relative angular consistency. If one steering module reaches its target significantly later than the others, the drive motors may generate asymmetric traction forces that produce temporary rotational disturbances. Motion controllers therefore frequently delay propulsion until all steering modules have reached acceptable synchronization thresholds.

Advanced synchronization algorithms incorporate feedforward compensation to improve transient steering response. Instead of responding solely to measured tracking error, feedforward controllers estimate the torque required to accelerate the steering mechanism based on actuator inertia, friction, and desired angular acceleration. This approach reduces synchronization delay and improves coordinated steering performance during high-speed maneuvers.

Mechanical design also plays an important role in synchronization accuracy. High-stiffness steering assemblies reduce elastic deformation under heavy loads, while precision bearings minimize steering compliance. Low-backlash gearboxes improve angular repeatability, and absolute encoders eliminate cumulative position uncertainty following power interruptions. Together, these mechanical improvements simplify servo control and increase synchronization consistency.

External disturbances continuously challenge steering synchronization during industrial operation. Uneven floor surfaces, wheel impacts, payload shifts, thermal expansion, cable drag, and mechanical wear gradually alter steering characteristics. Adaptive control algorithms estimate these changing system parameters online and automatically adjust servo gains to preserve synchronization throughout the operational lifetime of the robot.

Sensor fusion further enhances synchronization performance. Steering encoder measurements are complemented by inertial measurement units that detect unintended vehicle rotation resulting from steering mismatch. Visual localization and LiDAR localization independently estimate vehicle orientation and identify accumulated synchronization errors that may not be observable using steering sensors alone. Combining these measurements enables continuous correction of steering alignment while improving overall motion accuracy.

Safety considerations are closely associated with steering synchronization. Large steering deviations during high-speed lateral motion may significantly reduce vehicle stability and increase collision risk. Industrial safety controllers therefore continuously monitor steering synchronization quality. Whenever synchronization error exceeds predefined thresholds, vehicle speed is automatically reduced or motion is temporarily suspended until acceptable steering alignment has been restored.

As industrial autonomous mobile robots continue demanding higher positioning precision and greater operational flexibility, steering synchronization becomes increasingly sophisticated. Emerging control architectures incorporate Model Predictive Control, adaptive estimation, distributed synchronization algorithms, and AI-assisted parameter optimization to coordinate independent steering modules with exceptional accuracy. By ensuring that every wheel maintains precisely coordinated steering orientation throughout multidirectional motion, these synchronization techniques enable Four-Wheel Steering platforms to achieve the smooth, precise, and reliable sideways mobility required by next-generation industrial automation systems.

### 4.1 순수 측면 이동(Pure Lateral Movement) 조건 (Pure Lateral Movement Conditions)

순수 측면 이동(Pure Lateral Movement)은 **4륜 조향(4WS, Four-Wheel Steering)** 스티어 드라이브(Steer Drive) 이동로봇의 가장 대표적인 운동 기능 가운데 하나이며, 일반적으로 **크랩 주행(Crab Motion)**이라고도 불린다. 일반적인 바퀴형 차량은 측면 위치를 변경하기 위해 먼저 차량의 방향을 회전시켜야 하지만, 스티어 드라이브 플랫폼은 차체의 방향(Heading)을 유지한 상태에서 좌우 방향으로 직접 이동할 수 있다. 이러한 능력은 산업용 자율주행 이동로봇(AMR)의 운용 방식을 근본적으로 변화시키며, 불필요한 조향 동작을 제거하고 이동 거리를 줄이며 위치 정밀도를 크게 향상시킨다. 순수 측면 이동은 반도체 제조, 정밀 도킹(Precision Docking), 자동 창고(Automated Warehouse), 공작기계 자동 로딩(Machine Tending), 병원 물류(Hospital Logistics), 유연 생산 시스템(Flexible Manufacturing System) 등 협소한 공간에서 매우 중요한 역할을 수행한다.

순수 측면 이동의 운동학(Kinematics)은 일반적인 평면 강체 운동(Planar Rigid-body Motion) 모델에서 시작된다. 차량의 운동은 다음과 같은 세 개의 독립적인 상태 변수(State Variable)로 표현된다.

\* 종방향 속도(Longitudinal Velocity) (V_x)

\* 횡방향 속도(Lateral Velocity) (V_y)

\* 요 각속도(Yaw Rate) (\\Omega)

이 세 변수는 차량의 병진 운동(Translation)과 회전 운동(Rotation)을 완전히 표현한다.

이상적인 순수 측면 이동에서는 차량은 오직 좌우 방향으로만 이동해야 하며, 전후 이동이나 회전은 발생해서는 안 된다. 따라서 목표 운동 조건은 다음과 같이 정의된다.

[

V_x = 0

]

[

V_y = V_L

]

[

\\Omega = 0

]

여기서 (V_L)은 명령된 측면 이동 속도(Commanded Lateral Velocity)를 의미한다.

이 조건을 강체 운동 방정식(Rigid-body Motion Equations)에 대입하면 각 휠 모듈(Wheel Module)의 속도는 매우 단순한 형태가 된다. 회전 속도가 존재하지 않고 종방향 이동도 제거되므로, 모든 바퀴는 차체 내 위치와 관계없이 동일한 속도 벡터(Velocity Vector)를 갖는다.

각 바퀴의 속도 성분은 다음과 같이 표현된다.

[

V_{xi}=0

]

[

V_{yi}=V_L

]

즉, 차량 전체에 걸쳐 동일한 속도장이 형성된다.

회전 주행에서는 앞바퀴와 뒷바퀴 또는 좌우 바퀴 사이에 속도 차이가 존재하지만, 순수 측면 이동에서는 이러한 차이가 전혀 없다. 네 개의 모든 바퀴는 동일한 속도로 동일한 방향을 향하여 움직이며 차량 전체의 측면 이동을 만들어낸다.

각 바퀴의 조향각(Steering Angle)은 바퀴의 구름 방향(Rolling Direction)이 목표 속도 벡터와 일치하도록 결정된다.

역기구학(Inverse Kinematics)을 적용하면

[

\\theta_i

========

atan2(V_L,0)

]

이 된다.

양(+)의 측면 이동에서는 모든 조향 모듈이 약 **90°** 방향으로 정렬되고, 반대 방향 이동에서는 약 **−90°** 방향으로 정렬된다.

모든 바퀴가 동일한 조향 방향을 유지하므로 차량은 회전 모멘트(Rotational Moment)를 발생시키지 않고 하나의 강체(Rigid Body)처럼 좌우 방향으로 평행 이동한다.

각 바퀴의 선속도(Linear Velocity)는 속도 벡터의 크기로부터 계산된다.

[

v_i

===

\\sqrt{V_{xi}\^{2}+V_{yi}\^{2}}

\|V_L\|

]

따라서 모든 구동 모터(Drive Motor)는 동일한 회전 속도로 동작하며,

[

\\omega_i

========

\\frac{\|V_L\|}{r}

]

로 표현된다.

여기서 (r)은 유효 바퀴 반경(Effective Wheel Radius)이다.

모든 바퀴가 동일한 속도를 유지함으로써 차량 전체에 균일한 추진력이 생성되고, 원하지 않는 회전 운동이 발생하지 않는다.

순수 측면 이동은 바퀴가 자신의 조향 방향을 따라 자연스럽게 굴러가는 이상적인 구름 조건(Ideal Rolling Condition)을 가정한다. 바퀴는 측면으로 미끄러지지 않고 조향 방향으로만 추진력을 생성하므로, 스키드 조향(Skid Steering)처럼 의도적인 타이어 끌림(Tire Scrubbing)이 발생하지 않는다. 그 결과 구름 저항(Rolling Resistance)이 작고 기계적 마모(Mechanical Wear)가 감소하며 에너지 효율(Energy Efficiency)이 크게 향상된다.

수학적으로는 단순한 모델이지만 실제 산업 환경에서는 지속적인 외란(Disturbance) 보상이 필요하다. 각 바퀴의 조향각이 조금만 달라져도 차량에는 요 모멘트(Yaw Moment)가 발생하여 자세가 서서히 회전하게 된다. 또한 바퀴 직경 차이, 타이어 마모, 바닥 마찰 계수의 변화, 적재 하중의 불균형, 차체 구조의 탄성 변형 등은 모두 위치 오차와 자세 오차를 유발한다.

따라서 고정밀 스티어 드라이브 제어기는 조향 엔코더(Steering Encoder), 휠 엔코더(Wheel Encoder), 관성측정장치(IMU), 라이다 위치 인식(LiDAR Localization), 비전 기반 위치 인식(Visual Localization) 및 센서 융합(Sensor Fusion)을 이용하여 차량의 상태를 지속적으로 추정하고 오차를 실시간으로 보정한다.

중량급 산업용 AMR에서는 동적 특성(Dynamic Characteristics)도 매우 중요하다. 측면으로 급가속하면 차량의 좌우 바퀴 사이에서 하중 이동(Load Transfer)이 발생하고 접지력이 변하게 된다. 이에 따라 일부 바퀴에서는 슬립(Slip)이 발생할 수 있으므로, 최신 견인력 제어(Traction Control)는 모터 전류, 바퀴 속도 및 슬립 상태를 지속적으로 감시하여 구동 토크를 자동으로 재분배한다.

순수 측면 이동은 산업 자동화에서 매우 큰 장점을 제공한다. 자동 창고에서는 선반 옆으로 직접 접근할 수 있고, 반도체 제조에서는 웨이퍼 캐리어(Wafer Carrier)의 진동을 최소화할 수 있으며, 공작기계 자동 로딩에서는 차량의 방향을 유지한 상태로 설비에 접근할 수 있다. 병원 물류에서는 좁은 복도에서 여러 번 회전하지 않고도 좌우로 이동하여 효율적으로 운행할 수 있다.

결국 순수 측면 이동은 일반적인 스티어 드라이브 운동학의 특수한 형태로 볼 수 있으며, 횡방향 병진 운동만 존재하고 종방향 운동과 회전 운동은 모두 제거된 상태이다. 개념적으로는 단순한 운동이지만 실제 구현에서는 정밀한 조향 동기화, 동일한 바퀴 속도 유지, 폐루프 제어(Closed-loop Control), 센서 융합 및 외란 보상이 함께 이루어져야 한다. 이러한 기술이 결합됨으로써 현대의 4륜 조향 자율주행 이동로봇은 기존 바퀴형 차량에서는 구현하기 어려운 매우 정밀한 측면 이동 성능을 제공할 수 있다.

### 4.2 조향각 동기화(Steering Angle Synchronization) 요구사항 (Steering Angle Synchronization Requirements)

조향각 동기화(Steering Angle Synchronization)는 **4륜 조향(4WS)** 스티어 드라이브 플랫폼에서 안정적이고 정확한 측면 이동을 구현하기 위한 가장 중요한 요구사항 가운데 하나이다. 순수 측면 이동에서는 모든 휠 모듈이 거의 동일한 조향각을 유지해야 하며, 이동하는 동안에도 이 상태가 지속적으로 유지되어야 한다. 조향각에 작은 차이만 발생해도 바퀴가 생성하는 추진력의 방향이 서로 달라지며, 그 결과 원하지 않는 회전 모멘트, 위치 오차 및 타이어 끌림이 발생한다. 따라서 조향각 동기화는 전방향 이동(Holonomic Motion)의 핵심 요소이며, 산업용 자율주행 이동로봇의 위치 정밀도, 안정성, 에너지 효율 및 신뢰성을 결정하는 중요한 기술이다.

이상적인 운동학에서는 모든 바퀴가 동일한 조향각을 가져야 한다. 예를 들어 양(+) 방향의 측면 이동에서는 목표 조향각을 다음과 같이 정의할 수 있다.

[

\\theta_d

========

90\^\\circ

]

이 경우 이상적인 조건은

[

\\theta_1

========

\\theta_2

\\theta_3

\\theta_4

\\theta_d

]

가 된다.

이 관계가 유지되면 모든 바퀴는 정확히 동일한 방향으로 굴러가며 차량 전체에 균일한 측면 추진력이 발생한다.

그러나 실제 시스템에서는 다양한 원인으로 인해 조향 오차가 발생한다. 엔코더 분해능(Encoder Resolution), 감속기의 백래시(Backlash), 차체의 탄성 변형(Structural Compliance), 열팽창(Thermal Expansion), 제조 공차(Manufacturing Tolerance), 서보 응답 특성(Servo Dynamics) 등이 모두 조향각 오차를 유발한다.

i번째 바퀴의 실제 조향각은

[

\\theta_i

========

\\theta_d

\+

\\Delta\\theta_i

]

로 표현된다.

여기서 (\\Delta\\theta_i)는 조향 오차(Steering Angle Error)이다.

조향 오차가 발생하면 바퀴의 추진력은 더 이상 목표한 측면 방향과 정확히 일치하지 않는다. 각 바퀴에서 작은 종방향 힘(Longitudinal Force)이 추가로 발생하게 되며, 이러한 힘이 누적되면 차량에는 원하지 않는 요 모멘트(Yaw Moment)가 생성된다. 차량은 측면 이동을 수행하면서 서서히 회전하게 되고, 위치 정밀도와 경로 추종 성능(Path Tracking Performance)이 저하된다.

조향 동기화의 품질은 일반적으로 다음과 같은 **조향 동기화 오차(Steering Synchronization Error)**로 평가한다.

[

e_{\\theta}

==========

#\\max(\\theta_i)

\\min(\\theta_i)

]

이 값은 네 개 바퀴의 조향각 가운데 최대값과 최소값의 차이를 의미한다. 일반적인 산업용 AMR에서는 이 오차를 **1° 이하**로 유지하며, 반도체 제조 장비나 고정밀 검사 로봇에서는 이보다 훨씬 더 엄격한 수준의 동기화 정확도를 요구한다.

조향각 동기화는 고해상도 조향 엔코더를 이용한 **폐루프 제어(Closed-loop Control)**로 구현된다. 각 제어 주기마다 역기구학(Inverse Kinematics)이 계산한 목표 조향각과 실제 조향각을 비교한다.

조향 오차는

[

e_i

===

#\\theta_d

\\theta_i

]

로 정의된다.

각 조향 서보 모터는 자신의 오차를 독립적으로 최소화하도록 제어되며, EtherCAT과 같은 결정론적(Deterministic) 실시간 통신망을 통해 모든 조향 모듈이 동시에 동기화된다. 이러한 구조 덕분에 차량이 빠르게 방향을 변경하는 경우에도 모든 바퀴가 동일한 조향 상태를 유지할 수 있다.

조향 전환(Steering Transition) 과정에서는 동기화가 더욱 중요하다. 차량이 직진에서 크랩 주행 또는 대각선 이동으로 전환될 때 모든 바퀴는 동시에 새로운 각도로 회전해야 한다. 만약 일부 바퀴가 늦게 도착하면 추진력이 비대칭적으로 발생하여 일시적인 회전 운동이 발생할 수 있다. 따라서 최신 제어기는 모든 바퀴가 허용 오차 범위 내에 도달할 때까지 구동력을 제한하거나 지연시키는 전략을 사용한다.

최근의 조향 제어기에는 **피드포워드 제어(Feedforward Control)**도 함께 적용된다. 조향 오차에만 의존하지 않고 조향 기구의 관성(Inertia), 마찰(Friction), 목표 각가속도(Angular Acceleration)를 이용하여 필요한 토크를 미리 계산한다. 이러한 방식은 조향 응답을 빠르게 하고 여러 바퀴의 동기화 오차를 줄여준다.

기계적인 설계 역시 조향 동기화에 중요한 영향을 준다. 강성이 높은 조향 구조는 하중에 의한 변형을 줄이고, 정밀 베어링은 조향 유격을 감소시킨다. 저백래시 감속기(Low-backlash Gearbox)는 반복 위치 정밀도를 높이며, 절대형 엔코더(Absolute Encoder)는 전원 재인가 후에도 누적 위치 오차 없이 정확한 조향각을 제공한다.

산업 환경에서는 다양한 외란이 지속적으로 발생한다. 노면의 불균일, 충격, 적재 하중 이동, 온도 변화, 케이블 장력, 기계 마모 등은 조향 특성을 변화시킨다. 따라서 적응형 제어(Adaptive Control)는 이러한 변화를 실시간으로 추정하고 제어기 이득을 자동으로 조정하여 항상 동일한 조향 성능을 유지한다.

센서 융합(Sensor Fusion)은 조향 동기화를 더욱 향상시킨다. 조향 엔코더 정보 외에도 IMU는 차량의 의도하지 않은 회전을 감지하며, 라이다 위치 인식과 비전 기반 위치 인식은 차량의 실제 자세를 추정하여 조향 오차를 독립적으로 확인한다. 이러한 정보를 통합하면 조향 센서만으로는 검출하기 어려운 오차까지 보정할 수 있다.

안전성(Safety)도 조향 동기화와 밀접한 관련이 있다. 고속 측면 이동 중 조향 오차가 커지면 차량 안정성이 급격히 저하되고 충돌 위험이 증가한다. 따라서 산업용 안전 제어기는 조향 동기화 상태를 지속적으로 감시하며, 허용 오차를 초과하면 차량 속도를 자동으로 줄이거나 이동을 일시적으로 중단하여 안전을 확보한다.

최근에는 **모델 예측 제어(Model Predictive Control, MPC)**, 적응형 추정(Adaptive Estimation), 분산 동기화 알고리즘(Distributed Synchronization Algorithm), **인공지능 기반(AI-assisted)** 파라미터 최적화 기술이 조향 제어에 적용되고 있다. 이러한 기술들은 여러 개의 독립 조향 모듈을 매우 높은 정확도로 동기화하여, 산업용 4륜 조향 플랫폼이 요구하는 부드럽고 정확하며 신뢰성 높은 측면 이동을 가능하게 한다. 결국 **조향각 동기화는 차량 수준의 운동 계획과 바퀴 수준의 액추에이터 제어를 연결하는 핵심 기술**이며, 차세대 스마트 팩토리와 첨단 물류 자동화 시스템에서 스티어 드라이브 플랫폼의 성능을 결정하는 가장 중요한 요소 가운데 하나이다.

##  

## 05 Precision positioning kinematics

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Final Precision Docking Kinematics

Final precision docking represents the last and most demanding stage of autonomous navigation for a Four-Wheel Steering (4WS) steer-drive mobile robot. During this phase, the robot transitions from general path following to high-accuracy positioning immediately before interacting with a charging station, manufacturing machine, inspection equipment, conveyor interface, or automated storage system. Unlike long-distance navigation, where centimeter-level localization is often sufficient, precision docking requires the vehicle to continuously reduce both translational and rotational errors until the final pose satisfies strict industrial tolerances. The kinematic model used during this stage therefore emphasizes small-motion control, high-frequency feedback, and precise synchronization of steering and drive modules.

The desired docking pose is defined by a target position ((x_d, y_d)) and a target heading angle (\\theta_d). At every control cycle, the localization system estimates the actual vehicle pose ((x, y, \\theta)), and the controller computes the remaining docking error. The position error is expressed as

$$e_{x} = x_{d} - x$$

$$e_{y} = y_{d} - y$$

while the heading error becomes

[

e_{\\theta}=\\theta_d-\\theta

]

These three errors form the state vector used by the docking controller.

Instead of commanding aggressive motion, the controller converts these errors into small velocity commands that gradually drive the vehicle toward the target. A proportional feedback model is commonly adopted,

[

V_x=K_xe_x

]

[

V_y=K_ye_y

]

[

\\Omega=K_{\\theta}e_{\\theta}

]

where (K_x), (K_y), and (K_{\\theta}) are feedback gains selected according to vehicle dynamics and required positioning accuracy.

These desired chassis velocities are then transformed into steering angles and wheel velocities through the inverse kinematic equations. As the vehicle approaches the docking point, the commanded velocities become progressively smaller. Motion planners usually apply velocity scaling functions that continuously reduce speed according to the remaining distance from the target. This prevents overshoot while minimizing oscillation around the docking position.

Final docking often combines multiple sensing modalities. Wheel odometry provides smooth short-term motion estimation, inertial measurement units stabilize heading estimation, LiDAR localization corrects accumulated drift, and high-resolution vision systems identify docking markers or fiducial targets. Sensor fusion algorithms continuously update the estimated vehicle pose, allowing the controller to perform extremely small steering corrections throughout the final approach.

Another important characteristic of final docking kinematics is the frequent use of lateral motion. Rather than repeatedly executing forward and reverse corrections, a steer-drive platform may simply perform crab motion to remove lateral errors while maintaining vehicle orientation. Similarly, zero-radius rotation eliminates heading errors without disturbing the translational position. These multidirectional capabilities significantly reduce docking time while improving repeatability.

Mechanical compliance is also considered during final positioning. Small elastic deformation within tires, suspension components, steering mechanisms, and docking fixtures introduces slight differences between theoretical and actual vehicle positions. Consequently, many industrial docking systems intentionally slow the vehicle during the last few centimeters while allowing continuous sensor correction. Some systems additionally employ compliant guide mechanisms or tapered alignment structures that absorb residual positioning errors after physical contact occurs.

The combination of high-frequency closed-loop control, multidirectional kinematics, accurate sensor fusion, and synchronized wheel control enables modern steer-drive platforms to achieve repeatable precision docking even under varying payload conditions and changing industrial environments. This capability has become essential for automated manufacturing systems requiring reliable interaction between autonomous mobile robots and stationary production equipment.

---

### 5.2 Conditions for Reaching ±20 mm

Achieving a final positioning accuracy of ±20 mm represents a realistic engineering target for many industrial autonomous mobile robot applications. Such accuracy is sufficient for automated charging stations, machine tending, pallet handling, industrial inspection, and numerous manufacturing processes. Reaching this level of precision, however, requires the coordinated optimization of vehicle mechanics, sensing, control algorithms, and environmental conditions rather than relying on a single technology.

The first requirement is an accurate localization system. Wheel odometry alone cannot maintain ±20 mm accuracy over long travel distances because encoder errors, wheel slip, and tire deformation accumulate continuously. Therefore, odometry must be combined with external localization methods such as LiDAR-based SLAM, reflector localization, vision-based positioning, AprilTag detection, or Ultra-Wideband positioning depending on the operating environment. Sensor fusion algorithms integrate these measurements to produce an accurate estimate of vehicle position and orientation.

The second requirement is precise steering synchronization. All steering modules must accurately reach their commanded steering angles before propulsion begins. Even small steering errors introduce unwanted yaw motion that accumulates during the docking process. Industrial systems typically maintain steering synchronization errors below one degree, while higher-precision applications may require significantly tighter tolerances.

Mechanical rigidity is equally important. Chassis deformation under heavy payloads alters wheel geometry and changes the effective kinematic model. High-rigidity frame structures, precision steering bearings, low-backlash gearboxes, and accurately manufactured wheel modules minimize these effects. Tire stiffness should remain sufficiently high to reduce elastic deformation during low-speed positioning.

Motion control algorithms also contribute significantly to positioning performance. Instead of driving directly toward the target at constant speed, modern controllers gradually reduce vehicle velocity according to remaining position error. Smooth acceleration and deceleration profiles limit inertial disturbances while preventing oscillation around the desired docking location. Model Predictive Control and adaptive feedback control further improve positioning by anticipating future vehicle motion and compensating for dynamic effects.

Environmental conditions strongly influence achievable accuracy. Flat industrial floors with consistent friction characteristics produce more repeatable positioning than uneven outdoor terrain. Stable lighting improves vision-based localization, while unobstructed LiDAR visibility enhances scan matching reliability. Controlled factory environments therefore naturally support higher positioning accuracy than highly dynamic outdoor applications.

Communication latency must also remain sufficiently small. Steering commands, drive motor control, localization updates, and sensor measurements should be synchronized through deterministic industrial communication networks such as EtherCAT or Time-Sensitive Networking. Delayed control signals may introduce small positioning errors that become significant during the final docking phase.

Regular calibration further improves long-term performance. Wheel diameter changes caused by wear, steering encoder offsets, sensor alignment errors, and mechanical assembly tolerances gradually reduce positioning accuracy if left uncompensated. Periodic calibration procedures update kinematic parameters and maintain consistent vehicle behavior throughout its operational lifetime.

When these mechanical, sensing, control, communication, and environmental requirements are simultaneously satisfied, modern steer-drive autonomous mobile robots can repeatedly achieve positioning accuracies of approximately ±20 mm while maintaining stable operation under practical industrial conditions.

---

### 5.3 Worked Examples

The practical application of precision positioning kinematics can be illustrated through representative industrial examples demonstrating how the theoretical equations are applied during actual robot operation.

Consider a semiconductor transport robot approaching a processing machine. The docking target is located at coordinates (12.000 m, 4.500 m) with a desired heading of 90 degrees. Sensor fusion estimates the current vehicle pose as (11.982 m, 4.486 m) with a heading of 88.5 degrees. The resulting positioning errors are therefore 18 mm in the longitudinal direction, 14 mm in the lateral direction, and 1.5 degrees in heading.

The feedback controller converts these errors into low-speed correction commands. Because both longitudinal and lateral errors exist simultaneously, the controller generates a diagonal translational motion while also commanding a small rotational correction. The inverse kinematic solver calculates steering angles and wheel velocities for each module, allowing the vehicle to approach the docking point smoothly without performing separate forward and sideways movements. As the remaining error decreases, the controller continuously reduces vehicle speed until the final pose satisfies the required positioning tolerance.

A second example involves automated charging. An industrial AMR approaches a charging station equipped with electrical contacts requiring accurate alignment. Long-distance navigation is performed using LiDAR localization, while the final 300 mm of motion relies primarily on visual fiducial markers mounted on the charging station. Vision measurements detect small lateral offsets that are corrected directly using crab motion. Heading errors are eliminated through zero-radius rotation before the vehicle completes the final forward approach. Because steering and drive commands remain continuously synchronized, the charging connectors engage reliably without repeated positioning attempts.

Another representative example can be found in heavy machine tending. A steer-drive robot transporting a 700 kg payload delivers components to a CNC machining center. The large payload increases vehicle inertia and slightly deforms the chassis, altering the effective wheel geometry. Adaptive control algorithms compensate for these dynamic changes by continuously updating steering and velocity commands according to real-time sensor feedback. Although payload conditions vary from one production cycle to another, the robot consistently achieves positioning accuracy within ±20 mm because the controller automatically adapts its kinematic model to changing operating conditions.

These examples demonstrate that precision positioning is not achieved by mathematical equations alone. Successful docking results from the integration of accurate kinematic modeling, robust localization, adaptive feedback control, synchronized steering, precise mechanical design, and continuous sensor fusion. Together, these technologies enable Four-Wheel Steering autonomous mobile robots to perform highly reliable docking operations across a wide range of industrial applications while maintaining repeatability, efficiency, and operational safety.

### 5.1 최종 정밀 도킹 운동학 (Final Precision Docking Kinematics)

최종 정밀 도킹(Final Precision Docking)은 **4륜 조향(4WS, Four-Wheel Steering)** 스티어 드라이브(Steer Drive) 자율주행 이동로봇이 수행하는 자율주행 과정 가운데 가장 마지막 단계이자 가장 높은 정밀도를 요구하는 단계이다. 이 단계에서는 차량이 일반적인 경로 추종(Path Following) 상태에서 벗어나 충전 스테이션(Charging Station), 생산 설비(Manufacturing Machine), 검사 장비(Inspection Equipment), 컨베이어 인터페이스(Conveyor Interface), 자동창고(Automated Storage System)와 같은 목표 설비에 정확하게 접근하여 위치를 맞춘다. 장거리 주행에서는 수 센티미터 수준의 위치 정확도만으로도 충분하지만, 최종 도킹 단계에서는 차량의 위치(Position)와 자세(Orientation)를 지속적으로 보정하여 매우 작은 오차 범위 내에서 목표 자세(Target Pose)에 도달해야 한다. 따라서 이 단계의 운동학 모델은 작은 이동량(Small Motion), 높은 제어 주기(High-frequency Feedback), 정밀한 조향 및 구동 모듈의 동기화를 중심으로 구성된다.

도킹 목표는 목표 위치 ((x_d, y_d))와 목표 자세각(Heading Angle) (\\theta_d)로 정의된다. 제어 주기마다 위치 인식 시스템(Localization System)은 현재 차량의 자세 ((x, y, \\theta))를 계산하고, 제어기는 목표와 현재 상태의 차이를 오차(Error)로 계산한다.

종방향 위치 오차는

[

e_x=x_d-x

]

횡방향 위치 오차는

[

e_y=y_d-y

]

자세 오차는

[

e_{\\theta}=\\theta_d-\\theta

]

로 표현된다.

이 세 가지 오차는 최종 도킹 제어기의 상태 벡터(State Vector)를 구성하며, 차량의 운동을 결정하는 핵심 정보가 된다.

최종 도킹에서는 급격한 움직임을 생성하지 않는다. 대신 오차를 매우 작은 속도 명령으로 변환하여 차량이 목표 위치에 천천히 접근하도록 한다. 일반적으로 비례 제어(Proportional Feedback)를 사용하여 다음과 같이 속도를 생성한다.

[

V_x=K_xe_x

]

[

V_y=K_ye_y

]

[

\\Omega=K_{\\theta}e_{\\theta}

]

여기서

\* (K_x) : 종방향 제어 이득

\* (K_y) : 횡방향 제어 이득

\* (K_{\\theta}) : 자세 제어 이득

이다.

계산된 차량 속도는 역기구학(Inverse Kinematics)을 이용하여 각 바퀴의 조향각과 회전 속도로 변환된다.

차량이 목표 위치에 가까워질수록 제어기는 명령 속도를 지속적으로 감소시킨다. 대부분의 모션 플래너(Motion Planner)는 목표까지 남은 거리에 비례하여 속도를 줄이는 속도 스케일링(Velocity Scaling)을 적용한다. 이러한 방법은 오버슈트(Overshoot)를 방지하고 목표 위치 주변에서의 진동(Oscillation)을 최소화한다.

최종 도킹에서는 다양한 센서가 동시에 사용된다. 휠 오도메트리(Wheel Odometry)는 단기적인 이동량을 계산하고, 관성측정장치(IMU)는 자세를 안정적으로 추정한다. LiDAR 기반 위치 인식은 장거리 누적 오차를 제거하며, 고해상도 비전 시스템(High-resolution Vision System)은 도킹 마커(Fiducial Marker), AprilTag 또는 QR 마커를 인식하여 최종 위치를 매우 정밀하게 계산한다. 센서 융합(Sensor Fusion)은 이러한 정보를 통합하여 차량의 자세를 지속적으로 갱신하고, 매우 작은 조향 수정과 위치 보정을 가능하게 한다.

최종 도킹 운동학의 또 다른 특징은 **측면 이동(Crab Motion)**을 적극적으로 활용한다는 점이다. 일반 차량처럼 여러 번 전진과 후진을 반복하지 않고, 스티어 드라이브는 크랩 주행으로 횡방향 오차를 직접 제거할 수 있다. 또한 자세 오차는 제자리 회전(Zero Radius Rotation)을 통해 위치를 변경하지 않고 수정할 수 있다. 이러한 전방향 이동(Holonomic Motion)은 도킹 시간을 단축시키고 반복 위치 정밀도(Repeatability)를 크게 향상시킨다.

기계적인 순응성(Mechanical Compliance)도 고려해야 한다. 타이어의 탄성 변형, 서스펜션, 조향 기구 및 도킹 장치의 미세한 변형으로 인해 실제 위치는 이론적인 계산과 약간 차이가 발생한다. 따라서 산업용 도킹 시스템은 마지막 수 센티미터 구간에서 차량 속도를 매우 낮추고, 센서 피드백을 이용하여 지속적으로 오차를 수정한다. 일부 시스템은 순응형 가이드(Compliant Guide)나 테이퍼 형태의 정렬 구조(Tapered Alignment Structure)를 사용하여 기계적인 접촉 이후에도 남은 미세한 오차를 자동으로 흡수한다.

결국 최종 정밀 도킹은 **고주기 폐루프 제어(High-frequency Closed-loop Control)**, 전방향 운동학(Holonomic Kinematics), 고정밀 센서 융합, 조향 및 구동의 정밀 동기화를 기반으로 구현된다. 이러한 기술들이 결합됨으로써 현대의 스티어 드라이브 플랫폼은 적재 하중 변화나 산업 환경 변화에도 불구하고 매우 높은 반복 정밀도를 유지하면서 안정적으로 도킹을 수행할 수 있으며, 자동화 생산설비와 자율주행 이동로봇을 연결하는 핵심 기술로 자리 잡고 있다.

---

### 5.2 ±20 mm 위치 정밀도 달성을 위한 조건 (Conditions for Reaching ±20 mm)

최종 위치 정밀도 **±20 mm**는 현재 대부분의 산업용 자율주행 이동로봇에서 현실적으로 달성 가능한 대표적인 목표이다. 이 수준의 정밀도는 자동 충전기(Auto Charging Station), 공작기계 자동 로딩(Machine Tending), 팔레트 운반(Pallet Handling), 산업용 검사(Industrial Inspection) 및 다양한 자동화 생산 공정에서 충분한 성능을 제공한다. 그러나 이러한 정밀도는 하나의 기술만으로 얻어지는 것이 아니라, 기계 설계(Mechanical Design), 센서(Sensing), 제어(Control), 통신(Communication) 및 작업 환경(Environment)이 모두 최적화되어야 달성할 수 있다.

첫 번째 조건은 **정확한 위치 인식(Localization)**이다. 휠 오도메트리만으로는 바퀴 슬립, 엔코더 오차 및 타이어 변형 때문에 장거리 이동 시 ±20 mm 정확도를 유지할 수 없다. 따라서 LiDAR 기반 SLAM, 반사판 위치 인식(Reflector Localization), 비전 기반 위치 인식(Vision Localization), AprilTag, UWB(Ultra-Wideband) 등 외부 위치 인식 시스템과 센서 융합을 수행해야 한다. 센서 융합 알고리즘은 여러 센서의 장점을 결합하여 차량의 위치와 자세를 매우 정확하게 추정한다.

두 번째 조건은 **조향각 동기화(Steering Synchronization)**이다. 모든 조향 모듈은 구동이 시작되기 전에 목표 조향각에 정확하게 도달해야 한다. 조향 오차는 작은 요 운동(Yaw Motion)을 발생시키며, 이러한 오차는 최종 도킹 과정에서 누적되어 위치 정밀도를 저하시킨다. 일반적인 산업용 시스템에서는 조향 오차를 1° 이하로 유지하며, 반도체 및 정밀 검사 장비에서는 이보다 더욱 엄격한 기준을 적용한다.

세 번째는 **기계적 강성(Mechanical Rigidity)**이다. 중량물이 적재되면 차체가 미세하게 변형되고, 이는 바퀴의 기하학적 배치를 변화시켜 운동학 모델과 실제 움직임 사이에 차이를 만든다. 이를 최소화하기 위해 강성이 높은 차체 구조, 정밀 조향 베어링, 저백래시 감속기(Low-backlash Gearbox) 및 정밀 가공된 휠 모듈을 사용한다. 또한 타이어는 저속 정밀 위치 제어 시 탄성 변형이 최소화될 만큼 충분한 강성을 가져야 한다.

모션 제어(Motion Control) 알고리즘도 매우 중요한 역할을 한다. 차량을 일정한 속도로 목표까지 이동시키는 것이 아니라, 목표까지 남은 거리와 자세 오차에 따라 속도를 점진적으로 감소시키는 프로파일(Profile)을 사용한다. 이러한 방식은 관성에 의한 오버슈트와 진동을 줄이며, **모델 예측 제어(Model Predictive Control, MPC)**와 적응형 제어(Adaptive Control)는 차량의 미래 움직임을 예측하여 위치 정밀도를 더욱 향상시킨다.

환경 조건(Environmental Conditions)도 큰 영향을 미친다. 평탄하고 마찰 계수가 일정한 산업용 바닥은 반복 정밀도가 매우 높지만, 실외의 불규칙한 노면에서는 동일한 수준의 정밀도를 유지하기 어렵다. 또한 안정적인 조명은 비전 기반 위치 인식의 성능을 높이며, LiDAR의 시야가 확보될수록 스캔 정합(Scan Matching)의 정확도도 향상된다. 따라서 통제된 공장 환경은 ±20 mm 수준의 위치 정밀도를 달성하기에 매우 적합하다.

통신 지연(Communication Latency)도 최소화되어야 한다. 조향 명령, 구동 제어, 위치 인식 데이터 및 센서 측정은 EtherCAT 또는 TSN(Time-Sensitive Networking)과 같은 결정론적 산업용 네트워크를 통해 실시간으로 동기화되어야 한다. 제어 지연이 발생하면 최종 도킹 단계에서 작은 위치 오차가 누적될 수 있다.

정기적인 보정(Calibration)도 필수적이다. 바퀴 마모에 따른 직경 변화, 조향 엔코더 오프셋, 센서 장착 오차 및 기계적 공차는 시간이 지날수록 위치 정확도를 감소시킨다. 따라서 주기적인 캘리브레이션을 통해 운동학 파라미터를 업데이트하면 장기간 사용하더라도 안정적인 위치 정밀도를 유지할 수 있다.

결국 **±20 mm의 위치 정밀도는 단일 기술이 아닌 기계 구조, 센서, 제어 알고리즘, 통신 시스템 및 작업 환경이 동시에 최적화될 때 안정적으로 달성될 수 있는 성능**이다. 현대의 스티어 드라이브 AMR은 이러한 요소를 통합하여 실제 산업 현장에서 반복적으로 ±20 mm 수준의 정밀도를 구현하고 있다.

---

### 5.3 계산 예제 (Worked Examples)

정밀 위치 제어 운동학은 실제 산업 현장에서 다양한 방식으로 적용된다. 다음의 예제는 앞서 설명한 운동학 방정식이 실제 AMR의 제어 과정에서 어떻게 활용되는지를 보여준다.

첫 번째 예는 반도체 운반 로봇(Semiconductor Transport Robot)의 도킹이다. 목표 위치는 **(12.000 m, 4.500 m)**이며, 목표 자세는 **90°**이다. 센서 융합 시스템은 현재 차량의 위치를 **(11.982 m, 4.486 m)**, 현재 자세를 **88.5°**로 계산하였다.

따라서 차량의 오차는 다음과 같다.

\* 종방향 오차 : **18 mm**

\* 횡방향 오차 : **14 mm**

\* 자세 오차 : **1.5°**

제어기는 이러한 오차를 이용하여 매우 작은 속도 명령을 생성한다. 종방향과 횡방향 오차가 동시에 존재하므로 차량은 대각선 이동(Diagonal Motion)을 수행하며, 동시에 작은 회전 명령을 생성하여 자세를 수정한다. 역기구학은 각 바퀴의 조향각과 속도를 계산하며, 차량은 여러 번 전후 이동을 반복하지 않고 부드럽게 목표 위치에 접근한다. 오차가 감소할수록 속도는 자동으로 줄어들며, 최종적으로 요구되는 위치 정밀도 이내에서 정지한다.

두 번째 예는 자동 충전(Auto Charging)이다. 산업용 AMR은 충전 스테이션에 설치된 전기 접점을 정확하게 맞추어야 한다. 장거리 이동은 LiDAR 기반 위치 인식을 사용하지만, 마지막 약 **300 mm** 구간에서는 충전 스테이션에 부착된 비전 마커(Fiducial Marker)를 이용한다. 비전 시스템은 작은 횡방향 오차를 검출하며, 차량은 크랩 주행을 이용하여 이를 직접 수정한다. 이후 제자리 회전을 통해 자세 오차를 제거한 후 마지막 직진을 수행하여 충전 커넥터를 정확하게 결합한다. 조향과 구동은 항상 동기화되어 있으므로 반복적인 위치 수정 없이 안정적으로 충전이 이루어진다.

세 번째 예는 **700 kg**의 부품을 운반하는 중량급 공작기계 자동 로딩(Machine Tending)이다. 대형 적재물은 차량의 관성과 차체 변형을 증가시키며, 실제 운동학 모델을 변화시킨다. 적응형 제어(Adaptive Control)는 실시간 센서 데이터를 이용하여 이러한 변화를 지속적으로 보상하며, 조향각과 속도 명령을 자동으로 수정한다. 적재 중량이 작업마다 달라지더라도 제어기는 새로운 차량 특성을 추정하여 운동학 모델을 업데이트하므로, 최종 위치는 항상 **±20 mm** 이내의 오차를 유지할 수 있다.

이러한 예제들은 **정밀 위치 제어는 단순히 운동학 방정식만으로 달성되는 것이 아니라는 점**을 보여준다. 실제 산업 현장에서는 정확한 운동학 모델, 고정밀 위치 인식, 적응형 폐루프 제어, 조향 동기화, 높은 기계적 강성 및 지속적인 센서 융합이 함께 작동해야 한다. 이러한 요소들이 유기적으로 결합될 때, **4륜 조향 스티어 드라이브 자율주행 이동로봇은 다양한 산업 환경에서 높은 반복 정밀도와 안정성을 유지하면서 신뢰성 있는 정밀 도킹 작업을 수행할 수 있다.**
