**Differential Drive & Steer Drive Engineering**


# Chapter 04 Differential Drive Fundamentals

##  

## 01 Differential Drive Principle

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Turning via Left-Right Wheel Speed Difference

Differential drive is one of the most widely used locomotion architectures in mobile robotics because of its mechanical simplicity, low cost, and reliable control characteristics. The fundamental principle of differential drive is that vehicle steering is achieved by controlling the speed difference between the left and right drive wheels. Unlike conventional automobiles that use dedicated steering mechanisms to change wheel orientation, a differential drive robot changes its direction of travel entirely through differential wheel velocities.

A typical differential drive system consists of two independently driven wheels positioned on opposite sides of the vehicle chassis. Additional caster wheels or passive support wheels are often included to maintain balance and support vehicle weight. The drive wheels are responsible for both propulsion and steering. Because each wheel can rotate at a different speed, a wide variety of vehicle motions can be generated using only two motors and relatively simple control algorithms.

When both wheels rotate at the same speed in the forward direction, the robot travels in a straight line. The linear velocity of the vehicle is directly related to the rotational speed of the wheels. Under ideal conditions, the robot maintains a constant heading because equal traction forces are generated on both sides of the chassis. This operating condition represents the simplest motion mode and is frequently used during long-distance navigation.

Turning occurs when a speed difference is introduced between the two drive wheels. If the right wheel rotates faster than the left wheel, the robot turns toward the left. Conversely, if the left wheel rotates faster than the right wheel, the robot turns toward the right. The magnitude of the speed difference determines the curvature of the resulting path. Small speed differences generate large-radius turns, while large speed differences produce tighter turns.

One of the most important characteristics of differential drive systems is their ability to perform zero-radius turning. When one wheel rotates forward and the other rotates backward at the same speed, the robot rotates about its own geometric center. This maneuver is often referred to as spin turning or in-place rotation. Such capability is highly valuable in confined industrial environments where maneuvering space is limited.

The steering behavior of a differential drive robot is governed by kinematic relationships between wheel velocity, wheel separation distance, and vehicle angular velocity. As the difference between left and right wheel speeds increases, the angular velocity of the robot increases correspondingly. Control systems exploit these relationships to generate precise trajectory-following behavior.

Although the concept appears straightforward, practical implementation introduces several challenges. The differential drive architecture inherently relies on tire-ground interaction to generate steering forces. During turning, the wheels cannot naturally align themselves with the actual vehicle trajectory because their orientations remain fixed. As a result, lateral slip and tire scrubbing occur, particularly during sharp turns or zero-radius rotations.

The severity of wheel scrubbing depends on vehicle weight, wheel material, floor surface properties, and turning radius. Lightweight indoor robots typically experience minimal problems, while heavy industrial AMRs weighing over one ton may generate substantial lateral forces during turning. These forces increase tire wear, reduce energy efficiency, and introduce additional loads into the drivetrain.

Differential drive systems also exhibit sensitivity to wheel diameter mismatches and traction variations. If one wheel experiences greater slip than the other, the robot may deviate from its intended path. For this reason, many systems combine wheel encoders with inertial measurement units, LiDAR sensors, and localization algorithms to compensate for wheel slip and maintain accurate navigation.

Motion control for differential drive robots generally involves calculating the desired wheel velocities required to achieve a target linear velocity and angular velocity. These commands are then translated into motor speed references. Modern controllers continuously monitor wheel feedback and adjust motor outputs to maintain stable motion even under varying load conditions.

From an engineering perspective, differential drive remains attractive because it minimizes mechanical complexity. The absence of steering linkages, steering motors, and steering actuators reduces manufacturing cost and maintenance requirements. However, these advantages must be balanced against limitations associated with slip generation, tire wear, and reduced efficiency during aggressive turning maneuvers.

For indoor AMRs, warehouse robots, service robots, and educational platforms, differential drive continues to be one of the most practical mobility solutions. Its ability to generate complex trajectories using simple wheel-speed control makes it a foundational concept in mobile robotics and autonomous navigation.

---

### 1.2 ICC (Instantaneous Center of Curvature)

The concept of the Instantaneous Center of Curvature (ICC) is fundamental to understanding the motion of differential drive robots. While wheel speed differences explain how a robot turns, the ICC provides a geometric interpretation of the resulting motion. It serves as the theoretical point around which the robot rotates at a given instant and forms the basis for differential drive kinematic modeling.

When a differential drive robot is moving, every point on the robot follows a circular trajectory unless the vehicle is traveling perfectly straight. At any instant in time, these circular trajectories can be represented as rotation around a common center point. This common center is known as the Instantaneous Center of Curvature.

The location of the ICC depends entirely on the relative velocities of the left and right wheels. If both wheels rotate at identical speeds, the turning radius becomes infinitely large, and the ICC effectively moves to infinity. In this situation, the robot travels in a straight line because no curvature exists in the trajectory.

If the wheel speeds differ, the ICC moves to a finite location on the plane. The robot then follows a circular path whose radius is determined by the wheel speed ratio. The side of the robot moving more slowly lies closer to the ICC, while the faster side lies farther away. As the wheel speed difference increases, the ICC moves closer to the vehicle centerline, producing tighter turns.

An especially important case occurs during in-place rotation. When the left wheel rotates forward at the same speed that the right wheel rotates backward, the ICC lies exactly at the geometric center of the robot. The turning radius becomes zero, and the vehicle rotates without any translational motion. This capability is one of the defining characteristics of differential drive systems.

The ICC concept provides an elegant framework for describing robot kinematics. Instead of analyzing the motion of individual wheels separately, engineers can model the entire vehicle as rotating around a single point. This simplification greatly facilitates trajectory planning, motion prediction, and controller design.

Mathematically, the position of the ICC is determined by wheel separation distance and wheel velocities. As wheel speeds change continuously, the ICC also moves continuously. Consequently, a complex trajectory can be viewed as a sequence of instantaneous circular motions with varying ICC locations.

Path-planning algorithms frequently use ICC-based models to predict vehicle behavior. By calculating the expected ICC for a given wheel-speed command, the controller can estimate future vehicle position and orientation. This information is essential for autonomous navigation, obstacle avoidance, and trajectory tracking.

The ICC model also helps explain the origin of slip phenomena in differential drive systems. During a turn, all wheels ideally follow circular paths centered on the ICC. However, because the wheels are constrained to fixed orientations, perfect rolling motion is generally impossible. Small lateral sliding motions occur to satisfy the geometric constraints imposed by the vehicle configuration.

In lightweight robots operating on smooth surfaces, these slip effects are often negligible. In heavy industrial AMRs, however, the discrepancy between ideal ICC-based motion and actual wheel-ground interaction can become significant. Tire deformation, floor compliance, and vehicle mass all contribute to deviations from ideal kinematic behavior.

Engineers often compare ICC-based kinematic predictions with real-world sensor measurements to estimate slip and improve localization accuracy. Wheel encoders provide theoretical motion estimates, while inertial sensors, vision systems, and LiDAR measurements reveal actual vehicle behavior. Sensor fusion algorithms then combine these sources to obtain more accurate state estimation.

The ICC concept is also valuable for understanding maneuverability. Large turning radii correspond to ICC locations far from the vehicle, resulting in smooth, gradual turns. Small turning radii correspond to ICC locations close to the robot, enabling highly maneuverable behavior in confined environments. Designers can therefore evaluate vehicle agility by analyzing how wheel-speed combinations influence ICC location.

In modern robotics, the Instantaneous Center of Curvature remains one of the most important geometric tools for understanding mobile robot motion. It connects wheel kinematics, vehicle trajectories, motion control, localization, and slip analysis into a unified framework. A thorough understanding of ICC behavior is therefore essential for engineers developing differential drive robots, industrial AMRs, and autonomous navigation systems.

### 1.1 좌우 바퀴 속도 차이를 이용한 선회(Turning via Left-Right Wheel Speed Difference)

차동 구동(Differential Drive)은 이동 로봇(Mobile Robot) 분야에서 가장 널리 사용되는 이동 방식 중 하나이다. 이는 구조가 단순하고 제작 비용이 낮으며 제어가 비교적 쉽기 때문이다. 차동 구동의 핵심 원리는 좌측 바퀴(Left Wheel)와 우측 바퀴(Right Wheel)의 속도 차이(Speed Difference)를 이용하여 차량의 방향을 제어하는 것이다. 일반 자동차처럼 별도의 조향 장치(Steering Mechanism)로 바퀴 방향을 바꾸는 것이 아니라, 양쪽 바퀴의 회전 속도를 다르게 만들어 차량을 회전시킨다.

일반적인 차동 구동 시스템은 차량 좌우에 위치한 두 개의 독립 구동 바퀴(Independently Driven Wheel)로 구성된다. 차량의 균형을 유지하기 위해 캐스터 휠(Caster Wheel) 또는 보조 지지 휠(Support Wheel)이 추가되는 경우가 많다. 두 개의 구동 바퀴는 추진(Propulsion)과 조향(Steering)을 동시에 담당한다. 각각의 바퀴가 독립적으로 제어되기 때문에 두 개의 모터만으로도 다양한 주행 동작을 구현할 수 있다.

양쪽 바퀴가 동일한 속도로 전진하면 차량은 직진(Straight Motion)을 수행한다. 이 경우 좌우에서 발생하는 견인력(Traction Force)이 균형을 이루기 때문에 차량의 자세(Heading)는 유지된다. 이러한 직진 주행은 가장 기본적인 동작이며 장거리 이동(Long-Distance Navigation)에서 자주 사용된다.

선회(Turning)는 좌우 바퀴 속도에 차이를 주면서 발생한다. 예를 들어 오른쪽 바퀴가 왼쪽 바퀴보다 더 빠르게 회전하면 차량은 왼쪽으로 회전한다. 반대로 왼쪽 바퀴가 더 빠르게 회전하면 차량은 오른쪽으로 회전한다. 이때 속도 차이의 크기가 선회 반경(Turning Radius)을 결정한다. 작은 속도 차이는 큰 반경의 완만한 회전을 만들고, 큰 속도 차이는 작은 반경의 급격한 회전을 만든다.

차동 구동의 가장 큰 특징 중 하나는 제자리 회전(Zero-Radius Turn) 능력이다. 한쪽 바퀴가 전진하고 다른 쪽 바퀴가 동일한 속도로 후진하면 차량은 자신의 중심을 기준으로 회전하게 된다. 이를 스핀 턴(Spin Turn) 또는 제자리 회전(In-Place Rotation)이라고 한다. 이러한 기능은 좁은 통로(Narrow Aisle)나 제한된 공간에서 매우 유용하다.

차동 구동의 조향 특성은 휠 속도(Wheel Velocity), 휠 간 거리(Wheel Separation Distance), 차량 각속도(Angular Velocity)의 관계에 의해 결정된다. 좌우 속도 차이가 커질수록 차량의 회전 속도도 증가한다. 제어기(Control System)는 이러한 운동학(Kinematics) 관계를 이용하여 원하는 경로를 추종한다.

개념은 단순하지만 실제 환경에서는 다양한 문제가 발생한다. 차동 구동은 바퀴 방향이 고정(Fixed Orientation)되어 있기 때문에 차량이 회전할 때 바퀴가 실제 이동 경로와 정확히 일치하지 못한다. 따라서 횡방향 슬립(Lateral Slip)과 타이어 스크러빙(Tire Scrubbing)이 발생한다.

스크러빙의 정도는 차량 중량(Vehicle Mass), 타이어 재질(Tire Material), 바닥 상태(Floor Condition), 선회 반경에 따라 달라진다. 소형 실내 로봇은 영향이 작지만 1톤 이상의 산업용 AMR는 상당한 횡력을 발생시킬 수 있다. 이러한 힘은 타이어 마모(Tire Wear)를 증가시키고 에너지 효율(Energy Efficiency)을 저하시킨다.

차동 구동은 휠 직경 차이(Wheel Diameter Mismatch)나 접지력 변화(Traction Variation)에도 민감하다. 한쪽 바퀴에서 더 큰 슬립이 발생하면 차량은 의도한 경로에서 벗어날 수 있다. 이를 보완하기 위해 엔코더(Encoder), IMU(Inertial Measurement Unit), LiDAR, 위치 추정(Localization) 알고리즘이 함께 사용된다.

제어 측면에서는 원하는 선속도(Linear Velocity)와 각속도(Angular Velocity)를 계산한 후 이를 좌우 휠 속도로 변환한다. 이후 모터 제어기(Motor Controller)는 목표 속도를 유지하도록 지속적으로 출력값을 조정한다.

차동 구동의 가장 큰 장점은 기계적 단순성(Mechanical Simplicity)이다. 조향 모터(Steering Motor), 조향 링크(Steering Linkage), 조향 액추에이터(Steering Actuator)가 필요하지 않으므로 제작 비용과 유지보수 비용이 낮다. 그러나 이러한 장점은 슬립, 타이어 마모, 선회 시 효율 저하와 같은 단점과 함께 고려되어야 한다.

실내 AMR, 물류 로봇(Warehouse Robot), 서비스 로봇(Service Robot), 교육용 로봇(Educational Robot) 분야에서 차동 구동은 여전히 매우 실용적인 솔루션이다. 단순한 휠 속도 제어만으로도 복잡한 이동 궤적(Trajectory)을 생성할 수 있기 때문에 이동 로봇 공학의 가장 기본적인 개념으로 자리 잡고 있다.

---

### 1.2 순간 곡률 중심(ICC, Instantaneous Center of Curvature)

순간 곡률 중심(Instantaneous Center of Curvature, ICC)은 차동 구동 로봇의 운동을 이해하기 위한 가장 중요한 기하학적(Geometric) 개념 중 하나이다. 좌우 바퀴 속도 차이가 차량을 어떻게 회전시키는지를 설명한다면, ICC는 그 결과로 발생하는 운동을 기하학적으로 설명해 준다. 특정 순간 차량이 회전하고 있는 가상의 중심점이며, 차동 구동 운동학(Differential Drive Kinematics)의 핵심이 되는 개념이다.

차동 구동 차량이 움직일 때 차량의 모든 점(Point)은 직진 상태가 아니라면 원형 궤적(Circular Trajectory)을 따라 이동한다. 특정 순간을 기준으로 보면 차량 전체는 하나의 공통 중심점을 기준으로 회전하는 것처럼 표현할 수 있다. 이 공통 중심점이 바로 순간 곡률 중심(ICC)이다.

ICC의 위치는 좌우 바퀴 속도에 의해 결정된다. 양쪽 바퀴가 동일한 속도로 회전하면 선회 반경은 무한대(Infinite Radius)가 된다. 이 경우 ICC는 무한히 먼 곳에 존재한다고 간주되며 차량은 직진한다.

반대로 좌우 바퀴 속도가 다르면 ICC는 차량 근처의 특정 위치에 존재하게 된다. 차량은 그 ICC를 중심으로 원운동(Circular Motion)을 수행한다. 느리게 회전하는 쪽 바퀴는 ICC에 더 가깝고, 빠르게 회전하는 쪽 바퀴는 ICC에서 더 멀리 위치한다. 속도 차이가 커질수록 ICC는 차량 중심선(Centerline)에 가까워지며 선회 반경은 작아진다.

특히 중요한 경우는 제자리 회전이다. 왼쪽 바퀴가 전진하고 오른쪽 바퀴가 동일한 속도로 후진하는 경우 ICC는 차량의 기하학적 중심(Geometric Center)에 위치한다. 이때 선회 반경은 0이 되며 차량은 평행 이동 없이 회전만 수행한다. 이러한 특성은 차동 구동의 대표적인 장점이다.

ICC 개념은 차량 운동학을 단순화하는 데 매우 유용하다. 각 바퀴의 운동을 개별적으로 분석하는 대신 차량 전체를 하나의 중심점을 기준으로 회전하는 강체(Rigid Body)로 모델링할 수 있기 때문이다. 이는 경로 계획(Path Planning), 운동 예측(Motion Prediction), 제어기 설계(Control Design)를 훨씬 쉽게 만든다.

수학적으로 ICC 위치는 휠 간 거리와 각 휠 속도에 의해 계산된다. 휠 속도가 지속적으로 변화하면 ICC 위치도 계속 이동한다. 따라서 실제 주행 경로는 서로 다른 ICC를 중심으로 하는 순간적인 원운동들의 연속으로 볼 수 있다.

경로 계획 알고리즘은 ICC 기반 모델을 자주 사용한다. 특정 휠 속도 명령이 주어졌을 때 예상 ICC를 계산하면 차량의 미래 위치(Position)와 방향(Orientation)을 예측할 수 있다. 이러한 정보는 자율주행(Autonomous Navigation), 장애물 회피(Obstacle Avoidance), 경로 추종(Path Tracking)에 필수적이다.

ICC는 슬립(Slip)의 원인을 설명하는 데에도 매우 유용하다. 이상적으로는 모든 바퀴가 ICC를 중심으로 원운동을 해야 하지만, 차동 구동의 바퀴는 방향이 고정되어 있기 때문에 완벽한 순수 구름 운동(Pure Rolling Motion)이 불가능하다. 따라서 작은 횡방향 미끄러짐이 발생하며 이를 통해 기하학적 제약 조건을 만족시킨다.

소형 로봇에서는 이러한 슬립 효과가 거의 무시될 수 있지만, 중량급 산업용 AMR에서는 상당한 차이를 만들 수 있다. 타이어 변형(Tire Deformation), 바닥 탄성(Floor Compliance), 차량 질량 등이 이상적인 ICC 모델과 실제 차량 운동 사이의 오차를 증가시킨다.

실제 시스템에서는 ICC 기반 운동학 모델과 센서 데이터를 비교하여 슬립을 추정한다. 엔코더는 이론적인 이동량을 제공하고, IMU, 비전 시스템(Vision System), LiDAR는 실제 이동량을 측정한다. 센서 융합(Sensor Fusion) 알고리즘은 이 정보를 결합하여 보다 정확한 차량 상태(State Estimation)를 계산한다.

ICC 개념은 기동성(Maneuverability)을 이해하는 데에도 중요하다. ICC가 차량에서 멀리 위치할수록 큰 선회 반경과 부드러운 회전이 발생한다. 반대로 ICC가 차량 가까이에 위치할수록 작은 반경의 회전이 가능해져 좁은 공간에서도 높은 기동성을 확보할 수 있다.

현대 이동 로봇 공학에서 순간 곡률 중심(ICC)은 휠 운동학(Wheel Kinematics), 차량 궤적(Vehicle Trajectory), 모션 제어(Motion Control), 위치 추정(Localization), 슬립 분석(Slip Analysis)을 하나로 연결하는 핵심 개념이다. 따라서 차동 구동 로봇, 산업용 AMR, 자율주행 시스템을 개발하는 엔지니어에게 ICC에 대한 이해는 필수적인 기본 지식이라고 할 수 있다.

##  

## 02 Two-Wheel Drive Architecture

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Two Drive Wheel Configuration

The two-drive-wheel configuration is the fundamental mechanical architecture used in most differential drive mobile robots. It is widely adopted because it provides an effective balance between simplicity, maneuverability, reliability, and cost. In this architecture, two independently driven wheels generate all propulsion and steering forces required for vehicle movement. Unlike automobiles that separate propulsion and steering functions into different subsystems, a two-wheel differential drive system integrates both functions into the same pair of wheels.

The two drive wheels are typically mounted on opposite sides of the vehicle chassis and aligned along a common axle line. Each wheel is connected to an independent motor and often includes a gearbox that provides the required torque multiplication. By controlling the rotational speed and direction of each wheel separately, the robot can move forward, move backward, turn with various radii, or rotate in place without requiring any dedicated steering mechanism.

One of the key advantages of the two-drive-wheel configuration is mechanical simplicity. The architecture eliminates steering linkages, steering motors, tie rods, steering racks, and other mechanical components commonly found in conventional vehicle steering systems. This reduction in mechanical complexity lowers manufacturing costs, reduces maintenance requirements, and improves overall system reliability. For industrial applications where uptime is critical, simplicity often translates directly into operational benefits.

Vehicle motion is generated entirely through wheel velocity control. When both wheels rotate at identical speeds, the robot moves in a straight line. When one wheel rotates faster than the other, the vehicle follows a curved trajectory. If one wheel rotates forward while the other rotates backward, the robot rotates about its center. These motion modes are achieved purely through software control of wheel speeds, making differential drive one of the most elegant examples of software-defined vehicle steering.

The geometric placement of the drive wheels significantly influences vehicle performance. The distance between the wheels, commonly referred to as track width, affects stability, turning behavior, and load distribution. A wider wheel spacing generally improves lateral stability and reduces rollover risk but increases the overall vehicle width. Narrower configurations improve maneuverability in confined spaces but may reduce stability under heavy loads.

Load distribution is another important consideration. The majority of vehicle weight is typically supported by the drive wheels because traction generation depends on normal force between the wheel and the ground. Increasing load on the drive wheels generally improves traction capability, acceleration performance, and braking effectiveness. However, excessive loading can increase rolling resistance, wheel wear, and bearing stress.

Motor sizing within a two-drive-wheel architecture depends on total vehicle mass, desired acceleration, maximum speed, slope-climbing requirements, and expected payload conditions. Heavy-duty AMRs may require high-torque motors combined with planetary gearboxes or harmonic reduction systems to generate sufficient wheel torque. The drive system must be capable of overcoming inertia, rolling resistance, slope forces, and transient dynamic loads encountered during operation.

Dynamic performance is closely related to wheel placement. Since all steering forces are generated through differential wheel speeds, vehicle turning behavior depends on traction availability and wheel-ground interaction. On high-friction surfaces, turning may generate significant tire scrubbing forces. On low-friction surfaces, wheel slip may occur and affect localization accuracy.

Energy efficiency is another important characteristic of the two-drive-wheel configuration. Because the system contains relatively few moving components, mechanical losses are often lower than those found in more complex steering architectures. This simplicity contributes to longer operating times and improved battery utilization.

From a control perspective, the two-drive-wheel architecture is particularly attractive because its kinematic model is relatively straightforward. Vehicle position and orientation can be estimated using wheel encoder measurements combined with known wheel geometry. This simplicity has made differential drive systems the preferred platform for research, education, service robotics, warehouse automation, and many indoor AMR applications.

Despite its advantages, the configuration also has limitations. Lateral slip during turning, tire scrubbing, reduced efficiency during aggressive maneuvers, and sensitivity to wheel diameter variations can affect performance. These challenges become increasingly significant as vehicle mass increases. Nevertheless, for a wide range of robotic applications, the two-drive-wheel configuration remains one of the most practical and widely deployed mobility architectures.

---

### 2.2 Caster Wheel Support Role

While the drive wheels generate propulsion and steering forces in a differential drive robot, additional support wheels are generally required to maintain vehicle balance and distribute weight. The most common solution is the caster wheel. Although caster wheels are mechanically simple components, they play a critical role in overall vehicle stability, maneuverability, load carrying capability, and operational reliability.

A caster wheel is a passive wheel assembly that freely rotates about a vertical pivot axis while also rotating around its wheel axle. Unlike drive wheels, caster wheels are not connected to motors and do not actively generate traction forces. Instead, they automatically align themselves with the direction of vehicle movement. This self-aligning behavior allows the caster to support the vehicle without significantly interfering with differential drive motion.

The primary function of the caster wheel is weight support. A differential drive robot with only two drive wheels would be statically unstable because it would lack sufficient contact points to maintain balance. By adding one or more caster wheels, the vehicle gains additional support points that create a stable support polygon. This allows the robot to carry payloads safely while maintaining predictable ground contact.

The location of the caster wheel significantly influences vehicle behavior. Many differential drive robots use a single caster wheel positioned either at the front or rear of the chassis. Other designs employ multiple casters to improve load distribution and increase stability. The optimal configuration depends on vehicle size, payload requirements, operating environment, and dynamic performance objectives.

Caster wheel placement affects center-of-gravity management. Ideally, the majority of vehicle weight should remain on the drive wheels because traction generation depends on wheel loading. If too much weight is transferred to the caster wheel, available traction at the drive wheels decreases, reducing acceleration performance and braking effectiveness. Therefore, chassis designers carefully balance load distribution between drive wheels and caster supports.

Although caster wheels are passive components, they introduce their own dynamic effects. During direction changes, the caster must rotate about its pivot axis before aligning with the new direction of travel. This process is often called caster reorientation. During rapid maneuvering, caster reorientation may generate transient forces, vibration, or steering disturbances.

Caster flutter is another phenomenon occasionally observed in high-speed robots. Under certain operating conditions, the caster assembly may oscillate rapidly around its pivot axis. This oscillation can generate noise, increase wear, and negatively affect vehicle stability. Proper caster design, damping mechanisms, and geometry optimization are often used to mitigate this behavior.

Rolling resistance generated by caster wheels must also be considered. While caster wheels are not driven, they still contribute to overall vehicle resistance. Bearing quality, wheel material, wheel diameter, and floor conditions all influence caster rolling losses. For large industrial AMRs carrying heavy payloads, these losses can become significant.

Floor transitions and obstacle crossing present additional challenges. Caster wheels are often smaller than drive wheels and may have reduced ability to traverse gaps, thresholds, and uneven surfaces. Consequently, caster wheel design must consider expected floor conditions. Larger diameter casters generally improve obstacle negotiation capability but require additional installation space.

Heavy-duty industrial AMRs frequently employ reinforced caster assemblies capable of supporting substantial loads. Structural stiffness, bearing strength, wheel material durability, and shock resistance become increasingly important as vehicle weight increases. In some applications, spring-loaded caster mechanisms are used to improve ground contact consistency and reduce impact loading.

The dynamic interaction between drive wheels and caster wheels is often overlooked during preliminary design. However, caster behavior can significantly influence vehicle motion, especially during acceleration, braking, and turning. Advanced simulation models sometimes include caster dynamics to improve prediction accuracy and controller performance.

From a systems perspective, the caster wheel acts as a supporting partner to the drive wheels. While it does not directly contribute to propulsion, it enables stable operation by providing additional support, improving load distribution, and maintaining vehicle balance. A well-designed caster system enhances reliability, maneuverability, and operational efficiency, making it an essential element of the overall differential drive architecture.

In modern AMRs, caster wheels may appear simple, but their influence extends throughout the mechanical, dynamic, and operational characteristics of the vehicle. Proper caster selection and integration are therefore important engineering decisions that contribute significantly to the performance and durability of the entire robotic platform.

### 2.1 두 개의 구동 바퀴 구성(Two Drive Wheel Configuration)

두 개의 구동 바퀴(Two Drive Wheel) 구성은 대부분의 차동 구동(Differential Drive) 이동 로봇에서 사용되는 가장 기본적인 기계 구조(Mechanical Architecture)이다. 이 구조는 단순성(Simplicity), 기동성(Maneuverability), 신뢰성(Reliability), 경제성(Cost Efficiency)의 균형이 뛰어나기 때문에 널리 사용된다. 이 구조에서는 두 개의 독립 구동 바퀴가 차량의 추진(Propulsion)과 조향(Steering)에 필요한 모든 힘을 생성한다. 일반 자동차처럼 추진과 조향 기능이 분리되어 있지 않고, 동일한 두 개의 바퀴가 두 역할을 동시에 수행한다.

구동 바퀴는 일반적으로 차량 섀시(Chassis)의 좌우 양측에 배치되며 동일한 축선(Axle Line) 위에 위치한다. 각 바퀴는 독립적인 모터(Motor)와 연결되며, 대부분 충분한 토크(Torque)를 얻기 위해 감속기(Gearbox)가 함께 사용된다. 두 바퀴의 회전 속도와 방향을 독립적으로 제어함으로써 차량은 전진, 후진, 다양한 반경의 선회, 그리고 제자리 회전까지 수행할 수 있다.

두 개의 구동 바퀴 구조가 가지는 가장 큰 장점은 기계적 단순성(Mechanical Simplicity)이다. 일반 차량에 필요한 조향 링크(Steering Linkage), 타이로드(Tie Rod), 스티어링 랙(Steering Rack), 조향 모터(Steering Motor) 등의 기계 장치를 제거할 수 있다. 이는 제조 비용 절감뿐만 아니라 유지보수(Maintenance) 비용 감소와 신뢰성 향상으로 이어진다. 산업 현장에서는 가동률(Uptime)이 매우 중요하기 때문에 이러한 단순성은 큰 장점이 된다.

차량의 움직임은 전적으로 휠 속도 제어(Wheel Velocity Control)에 의해 결정된다. 양쪽 바퀴가 동일한 속도로 회전하면 직진(Straight Motion)을 수행하고, 한쪽 바퀴가 더 빠르게 회전하면 곡선 주행(Curved Motion)이 이루어진다. 한쪽 바퀴가 전진하고 다른 쪽이 후진하면 차량은 자신의 중심을 기준으로 회전한다. 이러한 모든 움직임은 기계적 조향 장치 없이 소프트웨어(Software) 기반 속도 제어만으로 구현된다.

구동 바퀴의 기하학적 배치(Geometric Placement)는 차량 성능에 큰 영향을 미친다. 바퀴 사이 거리인 윤거(Track Width)는 안정성(Stability), 선회 성능(Turning Performance), 하중 분배(Load Distribution)에 영향을 준다. 윤거가 넓을수록 횡방향 안정성이 향상되고 전도 위험(Tipover Risk)이 감소하지만 차량 폭이 증가한다. 반대로 윤거가 좁으면 좁은 공간에서 기동성은 향상되지만 안정성은 감소할 수 있다.

하중 분배 또한 매우 중요하다. 일반적으로 차량 중량의 대부분은 구동 바퀴에 실리도록 설계된다. 이는 접지력(Traction)이 수직하중(Normal Force)에 비례하기 때문이다. 구동 바퀴에 더 많은 하중이 걸리면 가속 성능, 제동 성능, 등판 성능이 향상된다. 그러나 과도한 하중은 구름 저항(Rolling Resistance), 타이어 마모(Tire Wear), 베어링 응력(Bearing Stress)을 증가시킨다.

모터 선정(Motor Sizing)은 차량 총중량, 목표 가속도, 최고 속도, 경사 주행 능력(Slope-Climbing Capability), 적재 조건(Payload Condition)에 따라 결정된다. 중량급 산업용 AMR는 일반적으로 고토크 모터(High-Torque Motor)와 유성 감속기(Planetary Gearbox) 또는 하모닉 감속기(Harmonic Drive)를 사용한다. 구동계는 관성(Inertia), 구름 저항, 경사 하중, 동적 충격 하중을 모두 극복할 수 있어야 한다.

차량의 동적 성능(Dynamic Performance)은 바퀴 위치와 접지 상태에 크게 영향을 받는다. 차동 구동은 좌우 휠 속도 차이만으로 조향력을 생성하기 때문에 노면과의 마찰(Friction)에 크게 의존한다. 마찰력이 높은 바닥에서는 타이어 스크러빙(Tire Scrubbing)이 증가할 수 있고, 마찰력이 낮은 바닥에서는 휠 슬립(Wheel Slip)이 발생할 수 있다.

에너지 효율(Energy Efficiency) 측면에서도 장점이 있다. 구동계에 움직이는 부품이 상대적으로 적기 때문에 기계적 손실(Mechanical Loss)이 적고 배터리 활용 효율(Battery Utilization Efficiency)이 높다. 이러한 특징은 장시간 운행이 필요한 AMR에서 매우 중요하다.

제어(Control) 측면에서는 운동학 모델(Kinematic Model)이 비교적 단순하다. 휠 엔코더(Wheel Encoder) 정보와 휠 기하학 정보를 이용하여 차량 위치와 자세를 쉽게 계산할 수 있다. 이러한 단순성 때문에 차동 구동은 연구용 로봇, 교육용 로봇, 서비스 로봇, 물류 AMR 등에서 가장 널리 사용되는 구조가 되었다.

물론 한계도 존재한다. 선회 시 횡방향 슬립(Lateral Slip), 타이어 스크러빙, 급격한 회전 시 효율 저하, 휠 직경 차이에 대한 민감성 등이 존재한다. 특히 차량 중량이 증가할수록 이러한 문제는 더욱 커진다. 그럼에도 불구하고 두 개의 구동 바퀴 구조는 현재까지도 가장 실용적이고 널리 사용되는 이동 로봇 구조 중 하나이다.

---

### 2.2 캐스터 휠의 지지 역할(Caster Wheel Support Role)

차동 구동 로봇에서 구동 바퀴는 추진력과 조향력을 생성하지만, 차량의 균형을 유지하고 하중을 분산하기 위해서는 추가적인 지지 바퀴(Support Wheel)가 필요하다. 가장 일반적으로 사용되는 방식이 캐스터 휠(Caster Wheel)이다. 캐스터는 단순한 부품처럼 보이지만 차량의 안정성(Stability), 기동성(Maneuverability), 하중 지지 능력(Load Carrying Capability), 신뢰성(Reliability)에 매우 중요한 역할을 한다.

캐스터 휠은 수직 회전축(Pivot Axis)을 중심으로 자유롭게 회전할 수 있으며, 동시에 휠 축(Wheel Axle)을 중심으로도 회전하는 수동형(Passive) 휠이다. 구동 바퀴와 달리 모터와 연결되어 있지 않으며 추진력을 생성하지 않는다. 대신 차량의 이동 방향에 맞추어 자동으로 방향을 정렬(Self-Alignment)한다. 이러한 특성 덕분에 차량 운동을 방해하지 않으면서도 안정적인 지지를 제공할 수 있다.

캐스터 휠의 가장 중요한 역할은 하중 지지(Weight Support)이다. 만약 차동 구동 차량이 두 개의 구동 바퀴만 가지고 있다면 정적으로 불안정(Statically Unstable)하여 균형을 유지할 수 없다. 캐스터를 추가하면 지면 접촉점(Contact Point)이 증가하여 안정적인 지지 다각형(Support Polygon)을 형성할 수 있다. 이를 통해 차량은 적재물을 안정적으로 운반할 수 있게 된다.

캐스터의 위치는 차량 거동에 큰 영향을 미친다. 많은 차동 구동 로봇은 차량 전방 또는 후방에 하나의 캐스터를 배치한다. 반면 대형 산업용 AMR는 여러 개의 캐스터를 사용하여 하중을 분산시키기도 한다. 최적의 배치는 차량 크기, 페이로드, 작업 환경, 목표 성능에 따라 달라진다.

캐스터 배치는 무게중심(CoG, Center of Gravity) 관리와도 밀접한 관련이 있다. 이상적으로는 차량 중량의 대부분이 구동 바퀴에 실려야 한다. 접지력은 수직하중에 비례하기 때문이다. 만약 캐스터가 너무 많은 하중을 지지하면 구동 바퀴의 접지력이 감소하여 가속 성능과 제동 성능이 저하될 수 있다. 따라서 설계자는 구동 바퀴와 캐스터 사이의 하중 분배를 신중하게 설계한다.

비록 캐스터는 수동형 부품이지만 동적 특성(Dynamic Characteristics)에 영향을 미친다. 차량이 방향을 바꾸면 캐스터는 새로운 이동 방향에 맞추어 회전해야 한다. 이를 캐스터 재정렬(Caster Reorientation)이라고 한다. 급격한 방향 전환 시에는 캐스터가 회전하는 과정에서 추가적인 힘과 진동이 발생할 수 있다.

캐스터 플러터(Caster Flutter)는 고속 차량에서 종종 관찰되는 현상이다. 특정 조건에서 캐스터가 피벗 축을 중심으로 빠르게 진동하는 현상으로, 소음(Noise), 마모(Wear), 안정성 저하를 유발할 수 있다. 이를 방지하기 위해 적절한 감쇠(Damping)와 구조 최적화가 필요하다.

캐스터도 구름 저항을 발생시킨다. 비록 추진력은 생성하지 않지만 차량 이동에 저항하는 힘을 만들어낸다. 베어링 품질, 휠 재질, 휠 직경, 노면 상태는 모두 캐스터의 구름 저항에 영향을 준다. 중량급 AMR에서는 이 저항도 무시할 수 없는 수준이 될 수 있다.

바닥 단차(Floor Transition)나 장애물(Obstacle)을 통과할 때도 캐스터는 중요한 역할을 한다. 일반적으로 캐스터는 구동 바퀴보다 작기 때문에 문턱(Threshold), 틈새(Gap), 울퉁불퉁한 바닥(Uneven Surface)을 통과하는 능력이 떨어질 수 있다. 따라서 실외 또는 산업 환경에서는 보다 큰 직경의 캐스터를 사용하는 경우가 많다.

중량급 산업용 AMR에서는 강화형 캐스터(Reinforced Caster Assembly)가 사용된다. 구조 강성(Structural Stiffness), 베어링 강도(Bearing Strength), 휠 내구성(Durability), 충격 저항성(Shock Resistance)이 매우 중요하다. 일부 시스템은 스프링 장착 캐스터(Spring-Loaded Caster)를 사용하여 지면 접촉을 안정적으로 유지하기도 한다.

구동 바퀴와 캐스터 사이의 상호작용(Dynamic Interaction)은 초기 설계 단계에서 종종 간과되지만 실제 성능에 큰 영향을 준다. 가속, 감속, 선회 과정에서 캐스터 거동은 차량의 운동 특성을 변화시킬 수 있다. 따라서 고급 시뮬레이션에서는 캐스터 동역학(Caster Dynamics)까지 포함하여 해석하기도 한다.

시스템 관점에서 캐스터는 구동 바퀴의 보조 파트너(Support Partner)라고 할 수 있다. 직접 추진력을 생성하지는 않지만 차량 균형을 유지하고 하중을 분산하며 안정적인 주행을 가능하게 한다. 잘 설계된 캐스터 시스템은 신뢰성, 기동성, 효율성을 향상시키며 차동 구동 아키텍처의 핵심 구성 요소가 된다.

현대 AMR에서 캐스터는 단순한 보조 바퀴처럼 보일 수 있지만, 실제로는 차량의 기계적 특성, 동역학 특성, 운용 성능 전반에 영향을 미치는 중요한 부품이다. 따라서 적절한 캐스터 선정과 통합 설계는 전체 로봇 플랫폼의 성능과 내구성을 결정하는 중요한 엔지니어링 요소라고 할 수 있다.

##  

## 03 Caster Wheel Concept

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Passive Caster vs Active Caster

Caster wheels are essential supporting components in many mobile robot platforms, particularly in differential drive architectures. Although their primary purpose is to provide additional support points and maintain vehicle stability, not all caster systems are identical. In modern AMR design, caster wheels are generally categorized into Passive Casters and Active Casters. Understanding the differences between these two approaches is important because they significantly influence vehicle maneuverability, load distribution, control complexity, energy consumption, and overall system performance.

A Passive Caster is the most common caster type used in mobile robotics. It consists of a wheel mounted on a swivel mechanism that freely rotates about a vertical axis. The caster does not contain any drive motor or steering actuator. Instead, it automatically aligns itself with the vehicle's direction of motion through the interaction between the wheel and the ground. This self-aligning behavior makes passive casters mechanically simple, inexpensive, and highly reliable.

The primary advantage of a passive caster is its simplicity. Because no motors, encoders, controllers, or power electronics are required, passive caster systems have low manufacturing costs and minimal maintenance requirements. This simplicity makes them particularly attractive for indoor AMRs, warehouse robots, service robots, and educational platforms where cost and reliability are critical considerations.

Passive casters also contribute to lightweight vehicle design. Since the caster assembly contains relatively few components, its mass is typically much lower than that of an actively controlled wheel module. This reduction in system weight improves energy efficiency and reduces overall vehicle complexity.

However, passive casters also introduce several dynamic challenges. During vehicle direction changes, the caster must physically rotate into alignment with the new direction of travel. This process creates a transient delay known as caster reorientation. During rapid maneuvers, caster reorientation can generate vibration, oscillation, and additional rolling resistance. These effects become more pronounced as vehicle speed and payload increase.

In heavy-duty AMRs, passive caster behavior may influence motion accuracy. When a vehicle accelerates, decelerates, or turns aggressively, the caster can produce transient forces that slightly alter the intended trajectory. Although these effects are generally small, they may become significant in applications requiring high positioning precision.

Active Casters address many of these limitations by introducing powered steering and, in some cases, powered drive capability. An active caster typically contains a steering motor that directly controls wheel orientation. Some designs also include a drive motor integrated into the wheel assembly. Because wheel direction is actively controlled, the system no longer depends on passive self-alignment.

The primary advantage of active casters is improved maneuverability and motion control. Since wheel orientation can be commanded directly, the vehicle can respond more quickly to steering inputs and follow trajectories more accurately. Active casters are particularly valuable in high-precision industrial applications where docking accuracy, positioning repeatability, and smooth motion are critical requirements.

Active casters also reduce many of the dynamic issues associated with passive caster reorientation. Because the wheel is already aligned before motion begins, transient disturbances are minimized. This results in smoother vehicle behavior, reduced vibration, and improved path-tracking performance.

Another significant advantage is enhanced load management. Active caster systems can distribute forces more effectively among multiple wheel modules, improving traction utilization and reducing localized wheel loading. This capability becomes increasingly important in vehicles carrying heavy payloads exceeding one ton.

Despite these advantages, active casters introduce substantial complexity. Steering motors, motor controllers, encoders, power distribution systems, and control algorithms are all required. The additional hardware increases system cost, weight, maintenance requirements, and software complexity. Engineers must also develop sophisticated coordination algorithms to synchronize wheel steering angles and vehicle motion.

From a safety perspective, active casters require fault-management strategies. Loss of steering control, encoder failure, or communication interruptions can directly affect vehicle behavior. Redundant sensing and safety monitoring are therefore often incorporated into active caster architectures.

The choice between passive and active casters ultimately depends on application requirements. Passive casters remain the preferred solution for cost-sensitive systems, moderate payloads, and relatively simple operating environments. Active casters become increasingly attractive when high payload capacity, precision navigation, advanced maneuverability, and dynamic performance are primary objectives.

As industrial AMRs continue to evolve toward heavier payloads and higher precision requirements, active caster technologies are becoming more common. Nevertheless, passive casters remain an elegant and highly effective solution for a wide range of robotic applications.

---

### 3.2 Number of Casters and Stability

The number of caster wheels used in a mobile robot has a significant influence on vehicle stability, load distribution, maneuverability, structural loading, and overall operational performance. While caster wheels are often viewed as secondary components compared with drive wheels, their quantity and placement play a critical role in determining how a vehicle behaves under both static and dynamic conditions.

At the most fundamental level, vehicle stability depends on the support polygon created by the wheel-ground contact points. The support polygon defines the area within which the vehicle's projected center of gravity must remain in order to prevent tipping. Increasing the number of support points generally enlarges or reshapes this polygon, influencing stability characteristics.

The simplest differential drive robots often use a single caster wheel combined with two drive wheels. This three-point support configuration creates a triangular support polygon. One of the major advantages of this arrangement is that all three wheels always remain in contact with the ground, even on slightly uneven surfaces. Because three points define a plane, the vehicle avoids overconstraint problems that can occur in systems with more support wheels.

Single-caster configurations are widely used in indoor AMRs, educational robots, and service robots because they offer simplicity, low cost, and excellent maneuverability. The vehicle remains lightweight and experiences minimal rolling resistance. However, the relatively small support polygon may limit stability when carrying heavy payloads or operating on uneven terrain.

As payload requirements increase, designers often introduce two caster wheels instead of one. The resulting four-point support system generally consists of two drive wheels and two caster wheels. This arrangement improves load distribution and increases stability, particularly for larger vehicles. The support polygon becomes wider, allowing the vehicle to accommodate higher centers of gravity and heavier payloads.

Two-caster systems are common in industrial AMRs because they provide a good balance between stability and mechanical simplicity. Nevertheless, four-point support introduces new challenges. Manufacturing tolerances, floor unevenness, and structural deflection can cause one wheel to lose contact with the ground. This effect may alter load distribution and influence traction performance.

Heavy-duty AMRs often employ multiple caster wheels to support very large payloads. Vehicles designed to carry hundreds of kilograms or several tons may use four, six, or even more caster assemblies distributed throughout the chassis. Multiple casters reduce local wheel loading and help prevent excessive structural stress.

Load distribution becomes particularly important in vehicles carrying concentrated payloads such as battery packs, robotic manipulators, inspection systems, or industrial tooling. Multiple caster wheels help distribute these loads across a larger area, reducing peak stresses on both the chassis and the floor surface.

However, increasing the number of casters does not always improve performance. Additional caster wheels increase rolling resistance, system weight, and mechanical complexity. More contact points also create greater sensitivity to manufacturing tolerances and floor irregularities. As a result, engineers must carefully balance stability benefits against potential disadvantages.

Dynamic stability considerations extend beyond simple static support analysis. During acceleration, braking, and turning, load transfer occurs between wheels. The effectiveness of a particular caster configuration depends on how well it manages these dynamic load shifts. Poor caster placement can increase wheel unloading, reduce traction, or create undesirable vibration.

Caster positioning is often more important than caster quantity alone. A carefully designed three-point support system may outperform a poorly designed six-point configuration. Engineers therefore evaluate wheel loads, center-of-gravity location, vehicle geometry, and expected operating conditions when selecting caster layouts.

For large industrial AMRs exceeding one ton, simulation tools are frequently used to evaluate stability performance. Multibody dynamics models predict wheel reaction forces, support polygon margins, load transfer behavior, and rollover resistance under realistic operating scenarios. These analyses help determine the optimal number and placement of caster wheels.

The selection of caster quantity is therefore a systems engineering decision rather than a simple mechanical choice. Stability, traction, payload capacity, maneuverability, durability, floor conditions, and manufacturing constraints must all be considered simultaneously. A properly designed caster configuration enables safe, efficient, and reliable operation while supporting the broader objectives of the mobile robot platform.

### 3.1 수동 캐스터(Passive Caster)와 능동 캐스터(Active Caster)

캐스터 휠(Caster Wheel)은 많은 이동 로봇(Mobile Robot), 특히 차동 구동(Differential Drive) 구조에서 사용되는 중요한 지지 장치(Support Component)이다. 캐스터의 기본 목적은 차량을 지지하고 안정성을 제공하는 것이지만, 모든 캐스터가 동일한 방식으로 동작하는 것은 아니다. 현대 AMR에서는 일반적으로 수동 캐스터(Passive Caster)와 능동 캐스터(Active Caster)로 구분되며, 이 두 방식은 기동성(Maneuverability), 하중 분배(Load Distribution), 제어 복잡성(Control Complexity), 에너지 소비(Energy Consumption), 전체 시스템 성능(System Performance)에 큰 차이를 만든다.

수동 캐스터는 이동 로봇에서 가장 널리 사용되는 캐스터 형태이다. 수직 회전축(Pivot Axis)을 중심으로 자유롭게 회전하는 스위블(Swivel) 구조와 휠(Wheel)로 구성된다. 수동 캐스터에는 구동 모터(Drive Motor)나 조향 액추에이터(Steering Actuator)가 존재하지 않는다. 대신 휠과 지면 사이의 상호작용을 통해 이동 방향에 맞추어 자동으로 정렬(Self-Alignment)된다. 이러한 특성 때문에 수동 캐스터는 구조가 단순하고 비용이 저렴하며 높은 신뢰성을 제공한다.

수동 캐스터의 가장 큰 장점은 기계적 단순성(Mechanical Simplicity)이다. 모터, 엔코더(Encoder), 제어기(Controller), 전력 전자 장치(Power Electronics)가 필요하지 않기 때문에 제조 비용과 유지보수 비용이 매우 낮다. 이러한 이유로 물류 AMR, 서비스 로봇(Service Robot), 교육용 로봇(Educational Robot), 실내 이동 로봇에서 널리 사용된다.

수동 캐스터는 시스템 경량화(Lightweight Design)에도 유리하다. 캐스터 구조 자체가 단순하기 때문에 질량(Mass)이 작고, 결과적으로 차량 전체 무게 감소와 에너지 효율(Energy Efficiency) 향상에 기여한다.

그러나 수동 캐스터는 동적 특성(Dynamic Characteristics) 측면에서 몇 가지 한계를 가진다. 차량이 방향을 변경할 때 캐스터는 새로운 이동 방향으로 회전해야 하며, 이 과정에서 캐스터 재정렬(Caster Reorientation)이 발생한다. 재정렬 과정에서는 일시적인 지연(Delay), 진동(Vibration), 추가적인 구름 저항(Rolling Resistance)이 발생할 수 있다. 차량 속도가 높거나 적재 중량이 증가할수록 이러한 현상은 더욱 두드러진다.

중량급 산업용 AMR에서는 수동 캐스터가 위치 정확도(Position Accuracy)에 영향을 줄 수 있다. 급가속, 급감속, 급선회 시 캐스터가 생성하는 과도력(Transient Force)이 차량의 실제 궤적(Trajectory)을 약간 변화시킬 수 있으며, 정밀 도킹(Docking)이나 검사 작업에서는 무시하기 어려운 수준이 될 수 있다.

능동 캐스터는 이러한 문제를 해결하기 위해 개발된 방식이다. 능동 캐스터는 조향 모터(Steering Motor)를 통해 휠 방향을 직접 제어하며, 일부 설계에서는 구동 모터까지 포함한다. 따라서 수동적인 자기 정렬(Self-Alignment)에 의존하지 않고 원하는 방향으로 휠을 정확히 제어할 수 있다.

능동 캐스터의 가장 큰 장점은 우수한 기동성과 정밀 제어 능력이다. 휠 방향을 직접 명령할 수 있기 때문에 조향 응답 속도가 빠르고 경로 추종(Path Tracking) 정확도가 높다. 이는 자동 충전 도킹(Auto Charging Docking), 정밀 위치 제어(Precision Positioning), 산업용 검사 시스템 등에서 매우 중요한 장점이 된다.

또한 능동 캐스터는 수동 캐스터에서 발생하는 재정렬 문제를 거의 제거한다. 차량이 움직이기 전에 휠 방향이 이미 정렬되어 있기 때문에 진동과 충격이 감소하며 보다 부드러운 주행 특성을 제공한다.

하중 관리(Load Management) 측면에서도 장점이 있다. 여러 개의 능동 캐스터는 차량 전체에 걸쳐 힘을 균일하게 분산시킬 수 있어 접지력 활용이 향상되고 특정 휠에 과도한 하중이 집중되는 현상을 줄일 수 있다. 이러한 특성은 1톤 이상의 중량급 AMR에서 특히 중요하다.

반면 능동 캐스터는 상당한 복잡성을 가진다. 조향 모터, 드라이브, 엔코더, 전원 공급 시스템, 제어 알고리즘 등이 추가되어야 하며, 이에 따라 비용과 무게가 증가한다. 또한 여러 휠의 조향 각도를 동기화하기 위한 복잡한 제어 소프트웨어가 필요하다.

안전성(Safety) 측면에서도 고려할 사항이 많다. 조향 제어 실패, 엔코더 오류, 통신 장애는 차량의 주행 특성에 직접적인 영향을 줄 수 있다. 따라서 능동 캐스터 시스템은 일반적으로 이중화(Redundancy)와 안전 감시(Safety Monitoring) 기능을 포함한다.

결국 수동 캐스터와 능동 캐스터의 선택은 응용 분야(Application Requirement)에 따라 결정된다. 비용과 단순성이 중요한 경우에는 수동 캐스터가 적합하며, 고중량, 고정밀, 고기동성이 요구되는 경우에는 능동 캐스터가 유리하다.

최근 산업용 AMR가 점점 더 높은 정밀도와 중량 운반 능력을 요구받으면서 능동 캐스터의 활용이 증가하고 있지만, 수동 캐스터 역시 여전히 매우 효율적이고 경제적인 솔루션으로 널리 사용되고 있다.

---

### 3.2 캐스터 개수(Number of Casters)와 안정성(Stability)

이동 로봇에서 사용되는 캐스터 휠의 개수는 차량의 안정성(Stability), 하중 분배(Load Distribution), 기동성(Maneuverability), 구조 하중(Structural Loading), 전반적인 운용 성능(Operation Performance)에 큰 영향을 미친다. 캐스터는 종종 보조 부품으로 생각되지만 실제로는 차량의 정적 안정성(Static Stability)과 동적 안정성(Dynamic Stability)을 결정하는 중요한 요소이다.

차량의 안정성은 기본적으로 휠과 지면이 접촉하는 점들로 형성되는 지지 다각형(Support Polygon)에 의해 결정된다. 무게중심(Center of Gravity)의 투영점(Projected CoG)이 이 지지 다각형 내부에 존재해야 차량이 안정적으로 유지된다. 따라서 지지점의 수와 위치는 차량 안정성에 직접적인 영향을 미친다.

가장 단순한 차동 구동 로봇은 두 개의 구동 바퀴와 하나의 캐스터 휠을 사용한다. 이러한 3점 지지 구조(Three-Point Support Configuration)는 삼각형 형태의 지지 다각형을 형성한다. 세 개의 점은 항상 하나의 평면(Plane)을 정의하기 때문에 바닥이 약간 고르지 않더라도 모든 바퀴가 지면과 접촉할 수 있다. 이는 매우 큰 장점이다.

단일 캐스터 구성은 실내 AMR, 교육용 로봇, 서비스 로봇에서 널리 사용된다. 구조가 단순하고 무게가 가벼우며 구름 저항이 적다. 또한 매우 우수한 기동성을 제공한다. 그러나 지지 다각형이 상대적으로 작기 때문에 높은 무게중심이나 무거운 적재물을 운반할 경우 안정성이 제한될 수 있다.

적재 능력이 증가하면 설계자는 하나 대신 두 개의 캐스터를 사용하는 경우가 많다. 두 개의 구동 바퀴와 두 개의 캐스터를 사용하는 4점 지지 구조(Four-Point Support Configuration)는 보다 넓은 지지 다각형을 형성한다. 이는 안정성을 향상시키고 더 무거운 페이로드를 지지할 수 있게 한다.

두 개의 캐스터를 사용하는 구조는 산업용 AMR에서 매우 흔하게 볼 수 있다. 안정성과 단순성의 균형이 좋기 때문이다. 그러나 4점 지지 구조는 새로운 문제도 발생시킨다. 제조 공차(Manufacturing Tolerance), 바닥 불균일성(Floor Unevenness), 프레임 변형(Structural Deflection)에 의해 특정 바퀴가 지면에서 들릴 수 있다. 이는 하중 분배와 접지력(Traction)에 영향을 준다.

수백 kg에서 수 톤급의 중량급 AMR는 여러 개의 캐스터를 사용하기도 한다. 4개, 6개 또는 그 이상의 캐스터를 차량 전체에 배치하여 하중을 분산시키고 국부적인 응력(Local Stress)을 감소시킨다.

대형 배터리(Battery Pack), CAD2SCAN 시스템, 로봇팔(Robot Manipulator), 산업용 장비와 같은 집중 하중(Concentrated Load)을 가진 차량에서는 다수의 캐스터가 특히 중요하다. 하중을 넓은 영역에 분산시켜 프레임과 바닥에 가해지는 응력을 줄일 수 있기 때문이다.

그러나 캐스터를 많이 사용하는 것이 항상 좋은 것은 아니다. 캐스터 수가 증가하면 구름 저항이 증가하고 시스템 무게도 증가한다. 또한 더 많은 접촉점은 제조 공차와 바닥 상태에 더욱 민감해진다. 따라서 안정성 향상과 부작용 사이의 균형이 필요하다.

동적 안정성은 단순한 정적 안정성과 다르다. 차량이 가속, 감속, 선회할 때 하중 이동이 발생한다. 따라서 캐스터 배치가 동적 하중을 얼마나 효과적으로 관리하는지가 중요하다. 잘못 설계된 캐스터 배치는 특정 바퀴의 접지력을 감소시키거나 진동을 증가시킬 수 있다.

실제로는 캐스터의 개수보다 배치 위치가 더 중요할 수 있다. 적절하게 설계된 3점 지지 구조가 잘못 설계된 6점 지지 구조보다 더 나은 성능을 보이는 경우도 있다. 따라서 설계자는 휠 하중(Wheel Load), 무게중심 위치, 차량 형상, 운용 환경을 종합적으로 고려하여 캐스터 배치를 결정한다.

1톤 이상의 산업용 AMR에서는 다물체 동역학(Multibody Dynamics) 시뮬레이션을 사용하여 안정성을 평가하는 경우가 많다. 이를 통해 휠 반력(Wheel Reaction Force), 하중 이동, 전도 안정성(Rollover Stability), 지지 여유(Support Margin)를 분석할 수 있다.

결론적으로 캐스터 개수의 결정은 단순한 기계 설계 문제가 아니라 시스템 엔지니어링(System Engineering) 문제이다. 안정성, 접지력, 적재 능력, 기동성, 내구성(Durability), 바닥 조건, 제조 비용 등을 동시에 고려해야 한다. 적절하게 설계된 캐스터 구성은 차량이 안전하고 효율적이며 신뢰성 있게 운행될 수 있도록 지원하는 중요한 요소이다.

##  

## 04 Turning Mechanism

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Zero Radius Turn

Zero Radius Turn is a turning mechanism in which a mobile robot rotates about its own geometric center without requiring any translational movement. During this maneuver, the turning radius becomes effectively zero, meaning the robot can change its heading while remaining at the same physical location. This capability is particularly valuable in confined environments where maneuvering space is limited and precise orientation adjustments are required.

From a kinematic perspective, a Zero Radius Turn occurs when the robot\'s translational velocity is zero while its angular velocity remains non-zero. The vehicle center remains stationary while the entire chassis rotates around a vertical axis passing through the center of the robot. This motion is commonly observed in Differential Drive robots, Steer Drive systems configured for in-place rotation, and certain Omni Drive architectures.

In a Differential Drive robot, Zero Radius Turn is achieved by commanding the left and right wheels to rotate at equal speeds in opposite directions. If the left wheel rotates forward and the right wheel rotates backward with identical velocity magnitude, the resulting linear velocity becomes zero while a pure rotational velocity is generated.

The fundamental equations can be expressed as:

v = (vR + vL)/2

ω = (vR − vL)/L

When:

vR = −vL

the linear velocity becomes:

v = 0

and the robot rotates around its center.

This maneuver offers several practical advantages. The most obvious benefit is maneuverability. In narrow aisles, warehouse intersections, factory workstations, and confined inspection zones, the robot can reorient itself without requiring additional clearance. This reduces the amount of free space needed for navigation and improves operational efficiency.

Zero Radius Turn also simplifies path planning in constrained environments. Instead of performing large-radius turning maneuvers, the robot can stop, rotate to a desired orientation, and continue moving along a new path. This capability is especially useful for indoor AMRs operating in densely populated industrial facilities.

However, the maneuver introduces significant frictional challenges. During Zero Radius Turn, the wheel contact patches experience substantial lateral scrubbing because the wheels are forced to move sideways relative to their rolling direction. This scrubbing generates friction losses, tire wear, floor wear, and increased power consumption.

The severity of these effects depends on vehicle weight, wheel material, floor material, and turning frequency. Lightweight robots may experience relatively minor consequences, but heavy industrial AMRs carrying payloads of several hundred kilograms or more can generate very large scrubbing forces. These forces increase motor torque requirements and reduce overall energy efficiency.

Steer Drive systems approach Zero Radius Turn differently. Rather than relying solely on wheel speed differences, each wheel is first rotated into a tangential orientation relative to the vehicle center. Once aligned, all wheels contribute to rotational motion while minimizing lateral scrubbing. This approach significantly reduces friction losses and improves efficiency.

Omni Drive and Mecanum Drive robots provide another solution. Their roller-based wheel structures allow lateral motion at the wheel-ground interface. As a result, Zero Radius Turn can be performed with considerably less scrubbing than conventional wheels. However, roller contact transitions introduce vibration and dynamic force fluctuations that must be managed through control algorithms.

The Instantaneous Center of Curvature (ICC) provides an important theoretical framework for understanding Zero Radius Turn. During this maneuver, the ICC coincides exactly with the geometric center of the robot. Every point on the chassis follows a circular trajectory around this center point, with velocity proportional to its distance from the center.

Control systems must carefully manage acceleration and deceleration during Zero Radius Turn. Rapid rotational acceleration can produce wheel slip, especially on low-friction surfaces. Excessive rotational speed may also compromise localization accuracy and sensor performance. Consequently, industrial robots often implement rotational velocity limits and smooth motion profiles.

From a localization perspective, Zero Radius Turn presents both advantages and challenges. Since the robot remains at a fixed position, translational error accumulation is minimized. However, rotational error may increase if wheel slip occurs. Sensor fusion techniques combining encoders, IMUs, LiDAR, and vision systems are frequently used to improve orientation estimation.

In modern autonomous mobile robots, Zero Radius Turn remains one of the most valuable maneuvering capabilities. Its ability to maximize maneuverability while minimizing required operating space makes it a fundamental feature in logistics robots, warehouse automation systems, service robots, inspection platforms, and industrial AMRs.

---

### 4.2 Arc Turn

Arc Turn is a turning mechanism in which a mobile robot follows a curved trajectory while simultaneously translating and rotating. Unlike Zero Radius Turn, where the vehicle rotates in place, Arc Turn allows the robot to maintain continuous forward motion during heading changes. This turning strategy is widely used because it provides smoother motion, higher efficiency, reduced wheel wear, and improved dynamic stability.

An Arc Turn can be visualized as motion along a segment of a circle. Every point on the robot follows a curved path, and the curvature of that path is determined by the turning radius. The robot continuously changes its orientation while progressing along the trajectory, creating a natural and fluid movement pattern.

The fundamental concept underlying Arc Turn is the Instantaneous Center of Curvature (ICC). During motion, the robot behaves as though it is rotating around a virtual point located somewhere outside the vehicle body. The distance between the robot center and the ICC defines the turning radius.

For Differential Drive robots, Arc Turn is generated by commanding different velocities to the left and right wheels. Unlike Zero Radius Turn, the wheel velocities are not equal and opposite. Instead, both wheels move in the same general direction but at different speeds.

The turning radius can be expressed as:

R = (L/2) × (vR + vL)/(vR − vL)

where:

R = turning radius

L = wheel separation

vR = right wheel velocity

vL = left wheel velocity

When the wheel velocities become equal, the turning radius approaches infinity and the robot travels in a straight line. As the velocity difference increases, the turning radius decreases and the curvature becomes tighter.

Arc Turn is highly energy efficient because wheel motion remains closer to pure rolling conditions. Since the wheels are not forced to move sideways, lateral scrubbing is significantly reduced compared with Zero Radius Turn. This reduction in friction lowers energy consumption and extends wheel life.

Steer Drive systems achieve Arc Turn through coordinated steering and drive control. Each wheel is oriented toward a common turning center, ensuring that all wheels roll along their natural trajectories. This approach minimizes slip and allows smooth, precise motion even for heavy payload vehicles.

The geometry of Steer Drive Arc Turn follows the principles of Ackermann Steering Geometry and generalized multi-wheel steering kinematics. Every wheel points toward the ICC, allowing the vehicle to negotiate curves with minimal tire deformation and friction losses.

Omni Drive systems can also execute Arc Turn, although their capabilities extend beyond conventional curved motion. Since holonomic platforms can independently control longitudinal velocity, lateral velocity, and angular velocity, Arc Turn becomes one of many possible trajectory types. The robot can simultaneously move forward, sideways, and rotate, creating motion patterns that may not correspond to simple circular arcs.

Arc Turn offers important advantages for trajectory tracking and path following. Because motion remains continuous, acceleration profiles can be smoother than those associated with repeated stop-and-rotate maneuvers. This smoothness improves passenger comfort in service robots, reduces mechanical stress, and enhances overall system efficiency.

Dynamic stability also benefits from Arc Turn. Sudden rotational accelerations associated with Zero Radius Turn can create transient forces that affect vehicle stability. Continuous curved motion distributes these forces more gradually, reducing peak loads on wheels, motors, and structural components.

Path planning algorithms frequently favor Arc Turns because they better reflect the natural motion constraints of wheeled vehicles. Algorithms such as Dubins Paths, Reeds-Shepp Curves, Pure Pursuit, and Model Predictive Control often generate trajectories composed of straight segments and arcs. These paths are easier for real vehicles to execute accurately than sequences of abrupt directional changes.

The choice between Zero Radius Turn and Arc Turn depends heavily on application requirements. Zero Radius Turn maximizes maneuverability in confined spaces, while Arc Turn maximizes efficiency, smoothness, and dynamic performance. Many industrial AMRs utilize both strategies, selecting the most appropriate turning mode according to available space, vehicle speed, payload conditions, and operational objectives.

Together, Zero Radius Turn and Arc Turn form the foundation of mobile robot turning behavior. Understanding the kinematics, dynamics, friction characteristics, and control implications of these mechanisms is essential for designing efficient, accurate, and reliable autonomous mobile robot systems.

### 4.1 제자리 회전(Zero Radius Turn)

제자리 회전(Zero Radius Turn)은 이동 로봇(Mobile Robot)이 병진 이동(Translational Motion) 없이 자신의 기하학적 중심(Geometric Center)을 기준으로 회전하는 주행 방식이다. 이때 회전 반경(Turning Radius)은 사실상 0이 되며, 로봇은 현재 위치를 유지한 채 방향만 변경할 수 있다. 이러한 능력은 협소한 공간에서의 기동성(Maneuverability)을 크게 향상시키기 때문에 물류창고, 공장, 검사 설비, 서비스 로봇 등 다양한 분야에서 매우 중요하게 활용된다.

기구학(Kinematics) 관점에서 제자리 회전은 선속도(Linear Velocity)는 0이고 각속도(Angular Velocity)는 0이 아닌 상태를 의미한다. 즉, 차량 중심은 움직이지 않지만 차체 전체는 수직축(Vertical Axis)을 중심으로 회전한다. 이러한 운동은 차동 구동(Differential Drive), 스티어 구동(Steer Drive), 그리고 일부 옴니 구동(Omni Drive) 시스템에서 구현할 수 있다.

차동 구동에서는 좌우 바퀴를 동일한 속도이지만 반대 방향으로 회전시켜 제자리 회전을 구현한다. 예를 들어 왼쪽 바퀴가 전진하고 오른쪽 바퀴가 동일한 속도로 후진하면 선속도는 상쇄되고 순수 회전 운동만 발생한다.

기본 방정식은 다음과 같다.

v = (vR + vL)/2

ω = (vR − vL)/L

여기서

vR = −vL

인 경우

v = 0

이 되며 차량은 중심축을 기준으로 회전한다.

제자리 회전의 가장 큰 장점은 뛰어난 공간 활용성이다. 좁은 통로(Narrow Aisle), 창고 교차로(Warehouse Intersection), 생산 설비 주변, 검사 공간 등에서 추가 공간 없이 방향을 변경할 수 있다. 따라서 내비게이션 효율이 향상되고 이동 경로도 단순해진다.

또한 경로 계획(Path Planning) 측면에서도 유리하다. 로봇은 정지 후 원하는 방향으로 회전한 뒤 새로운 경로를 따라 이동할 수 있다. 이는 복잡한 환경에서 경로 생성을 단순화하는 데 도움이 된다.

하지만 제자리 회전은 상당한 마찰 문제(Friction Problem)를 유발한다. 회전 중 바퀴는 원래의 구름 방향과 다른 방향으로 움직이려 하기 때문에 접촉 패치(Contact Patch)에서 횡방향 스크러빙(Lateral Scrubbing)이 발생한다. 이 과정에서 에너지 손실(Energy Loss), 타이어 마모(Tire Wear), 바닥 마모(Floor Wear), 전력 소비 증가가 발생한다.

이러한 현상은 차량 중량, 바퀴 재질, 바닥 재질, 회전 빈도에 따라 달라진다. 경량 AMR에서는 영향이 제한적일 수 있지만 수백 kg 또는 수 톤급 산업용 AMR에서는 상당한 마찰력이 발생하여 효율을 저하시킨다.

스티어 구동은 제자리 회전을 보다 효율적으로 수행한다. 먼저 각 바퀴를 차량 중심에 대한 접선 방향(Tangential Direction)으로 조향한 후 회전을 수행한다. 이렇게 하면 횡방향 스크러빙이 크게 감소하며 에너지 효율도 향상된다.

옴니 구동과 메카넘 구동(Mecanum Drive)은 롤러(Roller)를 이용하여 횡방향 이동을 허용하므로 일반 바퀴보다 훨씬 적은 스크러빙으로 제자리 회전을 수행할 수 있다. 그러나 롤러 접촉 전환(Roller Contact Transition)에 의한 진동과 힘 변동이 발생할 수 있다.

순간 회전 중심(ICC, Instantaneous Center of Curvature)은 제자리 회전을 이해하는 중요한 개념이다. 제자리 회전 시 ICC는 차량 중심과 정확히 일치한다. 차량의 모든 점은 이 중심을 기준으로 원형 궤적(Circular Trajectory)을 따라 이동하며, 중심으로부터 멀수록 선속도가 증가한다.

제어 시스템(Control System)은 회전 가속도와 감속도를 적절히 제어해야 한다. 급격한 회전은 휠 슬립(Wheel Slip)을 유발할 수 있으며, 특히 저마찰 노면에서는 위치 정확도를 저하시킬 수 있다. 따라서 산업용 로봇은 일반적으로 회전 속도 제한과 부드러운 속도 프로파일(Velocity Profile)을 적용한다.

위치추정(Localization) 측면에서는 장점과 단점이 동시에 존재한다. 병진 이동이 없기 때문에 위치 오차는 증가하지 않지만, 회전 중 발생하는 슬립 때문에 방향 오차(Heading Error)는 증가할 수 있다. 이를 보완하기 위해 IMU, LiDAR, 비전 시스템(Vision System), 엔코더(Encoder)를 결합한 센서 융합(Sensor Fusion)이 사용된다.

현대 산업용 AMR에서 제자리 회전은 가장 중요한 기동 기능 중 하나이다. 제한된 공간에서 최대의 기동성을 제공하기 때문에 물류 로봇, 창고 자동화 시스템, 서비스 로봇, 검사 로봇, 산업용 AMR에서 필수 기능으로 활용되고 있다.

---

### 4.2 아크 회전(Arc Turn)

아크 회전(Arc Turn)은 이동 로봇이 회전하면서 동시에 전진 또는 후진하는 곡선 주행 방식이다. 제자리 회전이 위치를 유지한 채 방향만 바꾸는 것과 달리, 아크 회전은 연속적인 이동과 방향 변경을 동시에 수행한다. 이러한 방식은 더 부드러운 움직임(Smooth Motion), 높은 에너지 효율(Energy Efficiency), 낮은 타이어 마모, 향상된 동적 안정성(Dynamic Stability)을 제공하기 때문에 실제 산업 환경에서 매우 널리 사용된다.

아크 회전은 원(Circle)의 일부를 따라 이동하는 운동으로 이해할 수 있다. 차량은 이동하면서 지속적으로 자세(Orientation)를 변경하며, 그 결과 자연스럽고 유연한 곡선 경로를 형성한다.

아크 회전의 핵심 개념 역시 순간 회전 중심(ICC)이다. 차량은 실제로는 보이지 않는 가상의 회전 중심을 기준으로 회전한다고 가정할 수 있으며, 차량 중심과 ICC 사이의 거리가 회전 반경(Turning Radius)을 결정한다.

차동 구동에서는 좌우 바퀴 속도를 다르게 설정하여 아크 회전을 생성한다. 제자리 회전과 달리 두 바퀴는 같은 방향으로 회전하지만 속도가 다르다.

회전 반경은 다음과 같이 표현할 수 있다.

R = (L/2) × (vR + vL)/(vR − vL)

여기서

R = 회전 반경

L = 바퀴 간 거리(Wheel Separation)

vR = 오른쪽 바퀴 속도

vL = 왼쪽 바퀴 속도

를 의미한다.

좌우 바퀴 속도가 동일하면 회전 반경은 무한대(Infinite Radius)가 되며 직선 주행이 이루어진다. 반대로 속도 차이가 커질수록 회전 반경은 작아지고 더 급격한 곡선 주행이 발생한다.

아크 회전은 에너지 효율이 매우 높다. 바퀴가 거의 순수 구름 운동(Pure Rolling Motion)을 유지하기 때문에 횡방향 스크러빙이 최소화된다. 결과적으로 마찰 손실(Friction Loss)이 감소하고 타이어 수명이 증가한다.

스티어 구동에서는 조향과 구동을 동시에 제어하여 아크 회전을 수행한다. 모든 바퀴는 동일한 ICC를 향하도록 조향되며, 각 바퀴는 자신의 궤적을 따라 자연스럽게 굴러간다. 따라서 슬립이 매우 적고 대형 차량에서도 부드러운 회전이 가능하다.

이러한 구조는 애커만 조향 기하학(Ackermann Steering Geometry) 및 다륜 조향 기구학(Multi-Wheel Steering Kinematics)의 원리를 따른다. 모든 바퀴가 동일한 회전 중심을 향하기 때문에 타이어 변형과 마찰 손실이 최소화된다.

옴니 구동도 아크 회전을 수행할 수 있지만 그 이상의 능력을 가진다. 홀로노믹 플랫폼(Holonomic Platform)은 Vx, Vy, ω를 독립적으로 제어할 수 있기 때문에 단순한 원호(Arc)뿐 아니라 전진, 측면 이동, 회전을 동시에 수행하는 복합 운동도 가능하다.

아크 회전은 경로 추종(Path Tracking)에서도 매우 유리하다. 연속적인 움직임을 유지할 수 있기 때문에 정지-회전-출발 방식보다 더 부드러운 가속 프로파일을 생성할 수 있다. 이는 승차감을 향상시키고 기계적 충격을 줄이며 전체 시스템 효율을 높인다.

동적 안정성 측면에서도 아크 회전은 유리하다. 제자리 회전에서는 큰 회전 가속도가 순간적으로 발생하지만, 아크 회전에서는 회전력이 점진적으로 분산되므로 바퀴, 모터, 프레임에 작용하는 최대 부하(Peak Load)가 감소한다.

경로 계획 알고리즘도 아크 회전을 선호하는 경우가 많다. Dubins Path, Reeds-Shepp Curve, Pure Pursuit, MPC(Model Predictive Control) 등의 알고리즘은 직선(Straight Line)과 원호(Arc)를 조합하여 실제 차량이 실행하기 쉬운 경로를 생성한다.

제자리 회전과 아크 회전 중 어떤 방식을 사용할지는 작업 환경에 따라 달라진다. 제자리 회전은 협소 공간에서 최고의 기동성을 제공하며, 아크 회전은 효율성, 부드러움, 동적 성능을 극대화한다.

실제 산업용 AMR은 일반적으로 두 가지 방식을 모두 사용한다. 공간이 충분할 경우에는 아크 회전을 사용하여 효율을 높이고, 공간이 제한될 경우에는 제자리 회전을 사용하여 기동성을 확보한다.

결국 제자리 회전(Zero Radius Turn)과 아크 회전(Arc Turn)은 이동 로봇의 모든 회전 동작의 기초를 구성한다. 이러한 회전 메커니즘의 기구학(Kinematics), 동역학(Dynamics), 마찰 특성(Friction Characteristics), 제어 특성(Control Characteristics)을 정확하게 이해하는 것은 효율적이고 정밀하며 신뢰성 있는 자율주행 이동 로봇 시스템을 설계하는 데 필수적이다.

##  

## 05 Industrial Applications

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Light Duty Logistics AMR

Light Duty Logistics AMRs represent one of the most widely deployed categories of autonomous mobile robots in modern industrial environments. These robots are designed to transport relatively small payloads while maximizing operational efficiency, deployment simplicity, and cost effectiveness. Typical payload capacities range from several kilograms to a few hundred kilograms, making them suitable for material transport, warehouse replenishment, component delivery, order fulfillment, and internal logistics operations.

The rapid growth of e-commerce, smart manufacturing, and warehouse automation has accelerated the adoption of Light Duty Logistics AMRs. Unlike traditional conveyor systems, these robots provide flexible transportation capabilities without requiring fixed infrastructure. Routes can be modified through software updates rather than physical facility changes, enabling organizations to adapt quickly to evolving production requirements.

Most Light Duty Logistics AMRs employ Differential Drive architectures due to their mechanical simplicity and low cost. Two independently driven wheels combined with passive caster wheels provide adequate maneuverability for indoor environments. The control algorithms are relatively straightforward, maintenance requirements are low, and component costs remain competitive. These characteristics make Differential Drive particularly attractive for large fleet deployments where total ownership cost is a critical factor.

In warehouse applications, AMRs commonly transport bins, cartons, totes, and lightweight pallets between storage locations and workstations. The robots typically operate on smooth industrial floors and follow predefined routes generated by fleet management software. Because payload requirements remain moderate, the limitations associated with wheel scrubbing and turning resistance are generally acceptable.

Navigation systems for Light Duty Logistics AMRs often combine LiDAR-based localization, visual markers, QR codes, and encoder-based odometry. Since vehicle speeds are relatively low and operating environments are controlled, these navigation approaches provide sufficient positioning accuracy for daily operations. Typical docking accuracy requirements range from a few centimeters to several millimeters depending on the application.

Energy efficiency is another significant advantage. Lower payloads reduce traction requirements, rolling resistance, and motor power demand. As a result, compact battery systems can provide many hours of operation. This enables efficient fleet scheduling and minimizes charging infrastructure requirements.

Safety is particularly important in logistics environments where robots frequently share space with human workers. Light Duty Logistics AMRs are typically equipped with safety LiDARs, emergency stop systems, obstacle detection sensors, and certified safety controllers. These systems allow robots to operate safely in dynamic environments while maintaining productivity.

Scalability is one of the strongest advantages of this AMR category. Facilities can gradually increase fleet size as operational demands grow. Additional robots can often be integrated without major modifications to facility infrastructure. Fleet management systems dynamically assign transportation tasks, balance workloads, and optimize traffic flow among multiple robots.

Many modern factories use Light Duty Logistics AMRs as an intermediate automation layer between manual transportation and fully automated material handling systems. The robots can coexist with forklifts, conveyors, and human operators while providing substantial productivity improvements. This flexibility has made them particularly attractive for industries such as electronics manufacturing, pharmaceutical production, semiconductor assembly, and consumer goods logistics.

The relatively low system cost compared with heavy-duty transport platforms further accelerates adoption. Organizations can often achieve favorable return on investment within a relatively short period due to labor savings, reduced transportation delays, improved traceability, and enhanced operational flexibility.

Although Light Duty Logistics AMRs are highly effective within their intended operating range, their design assumptions are optimized for moderate payloads and controlled indoor environments. As payload demands increase, additional engineering considerations become necessary. These considerations define the transition point between light-duty logistics robots and heavy-duty industrial transport platforms.

---

### 5.2 Limitations Below Heavy Load Threshold

While Light Duty Logistics AMRs offer excellent performance for moderate payload transportation, their design architecture introduces limitations as operating conditions approach heavy-load requirements. Understanding these limitations is essential when selecting a drive system, designing a vehicle platform, or planning long-term deployment strategies.

The most significant limitation arises from wheel-ground interaction forces. As payload increases, the normal force acting on each wheel increases proportionally. Higher normal forces generate greater rolling resistance, larger bearing loads, increased tire deformation, and higher drive torque requirements. Components that perform adequately under light-duty conditions may experience accelerated wear when subjected to heavier loads.

Differential Drive systems are particularly affected by increasing payload. During turning maneuvers, lateral scrubbing forces grow substantially with vehicle weight. Since conventional Differential Drive wheels cannot align themselves with the actual turning path, the contact patches experience significant side loading. This phenomenon increases energy consumption, tire wear, floor wear, and motor stress.

For payloads approaching several hundred kilograms, these effects become increasingly noticeable. Frequent turning operations may require significantly higher torque than straight-line motion. Motor sizing margins that appear sufficient during initial testing may become inadequate under sustained heavy-duty operation.

Structural limitations also emerge as payload increases. Chassis deflection becomes more significant, affecting wheel alignment and load distribution. Uneven load sharing between wheels can increase slip, reduce traction efficiency, and create unpredictable handling characteristics. Precision docking performance may deteriorate as structural compliance increases.

Battery systems face additional challenges. Heavier payloads require more energy for acceleration, deceleration, and climbing. As power demand increases, battery discharge rates rise and operating time decreases. Organizations may need larger batteries, more frequent charging cycles, or higher-capacity charging infrastructure to maintain productivity.

Thermal management becomes increasingly important near the heavy-load threshold. Motors, gearboxes, motor controllers, and batteries generate additional heat as torque demand rises. Without adequate cooling systems, elevated operating temperatures can reduce component lifespan and limit continuous-duty performance.

Dynamic stability is another consideration. Higher payloads increase vehicle inertia, which affects braking performance, emergency stopping distance, and obstacle avoidance behavior. Control systems must compensate for these effects through more sophisticated motion planning and dynamic control algorithms.

Navigation accuracy may also degrade under heavy loads. Increased wheel deformation, greater slip probability, and changing contact conditions introduce errors into encoder-based odometry. Although sensor fusion can compensate for many of these effects, localization systems often require higher-quality sensors and more advanced algorithms as vehicle mass increases.

Floor loading constraints become important as well. Industrial facilities designed for light-duty automation may not be optimized for repeated heavy-load operation. Floor flatness, surface wear resistance, expansion joints, and structural loading limits all influence long-term performance.

These limitations explain why many industrial organizations transition from Differential Drive architectures to Steer Drive architectures as payload requirements increase. Steer Drive systems reduce lateral scrubbing, improve energy efficiency, minimize tire wear, and maintain higher positioning accuracy under heavy loads. Although mechanical complexity increases, the operational benefits often outweigh the additional cost.

The exact transition point varies depending on application requirements, floor conditions, operating speed, duty cycle, and positioning accuracy targets. In many industrial environments, payloads below approximately 200--300 kg can be handled efficiently by conventional Light Duty Logistics AMRs. As payloads approach 500 kg and beyond, the advantages of more advanced drive architectures become increasingly compelling.

Consequently, understanding the limitations below the heavy-load threshold is not merely a matter of identifying weaknesses. It is a critical step in selecting the appropriate robot architecture for future scalability, operational efficiency, maintenance cost reduction, and long-term system reliability. Proper alignment between payload requirements and drive system capabilities ensures that an AMR platform remains effective throughout its operational life cycle.

### 5.1 경량 물류 AMR(Light Duty Logistics AMR)

경량 물류 AMR(Light Duty Logistics AMR)은 현대 산업 환경에서 가장 널리 보급된 자율주행 이동 로봇(Autonomous Mobile Robot) 유형 중 하나이다. 이러한 로봇은 비교적 작은 페이로드(Payload)를 운반하면서도 높은 운영 효율성(Operational Efficiency), 구축 용이성(Deployment Simplicity), 비용 효율성(Cost Effectiveness)을 제공하도록 설계된다. 일반적으로 수 kg에서 수백 kg 수준의 하중을 운반할 수 있으며, 자재 이송(Material Transport), 창고 보충(Warehouse Replenishment), 부품 공급(Component Delivery), 주문 처리(Order Fulfillment), 공장 내 물류 작업 등에 널리 활용된다.

전자상거래(E-commerce), 스마트 제조(Smart Manufacturing), 창고 자동화(Warehouse Automation)의 성장과 함께 경량 물류 AMR의 보급도 급속히 증가하고 있다. 기존 컨베이어 시스템(Conveyor System)과 달리 AMR은 고정 인프라(Fixed Infrastructure)가 필요하지 않으며, 경로 변경도 물리적인 설비 변경이 아니라 소프트웨어 업데이트를 통해 수행할 수 있다. 따라서 생산 라인 변경이나 공정 재배치가 잦은 환경에서 매우 높은 유연성을 제공한다.

대부분의 경량 물류 AMR은 차동 구동(Differential Drive)을 채택한다. 두 개의 독립 구동 바퀴와 수동 캐스터 휠(Passive Caster Wheel)만으로 충분한 기동성을 확보할 수 있기 때문이다. 기계 구조가 단순하고 유지보수가 용이하며, 제어 알고리즘도 비교적 간단하다. 또한 부품 비용이 낮기 때문에 대규모 플릿(Fleet) 구축 시 총소유비용(TCO, Total Cost of Ownership)을 줄일 수 있다.

창고 환경에서는 박스(Box), 빈(Bin), 토트(Tote), 소형 팔레트(Pallet) 등을 작업장과 저장 구역 사이에서 운반하는 역할을 수행한다. 일반적으로 평탄한 산업용 바닥(Industrial Floor)에서 운용되며, 플릿 관리 시스템(Fleet Management System)이 생성한 경로를 따라 이동한다. 하중이 상대적으로 낮기 때문에 차동 구동에서 발생하는 스크러빙(Scrubbing)이나 회전 저항(Turning Resistance)의 영향은 비교적 제한적이다.

경량 물류 AMR의 내비게이션 시스템은 LiDAR Localization, 비전 마커(Visual Marker), QR 코드(QR Code), 엔코더 기반 오도메트리(Encoder-Based Odometry)를 조합하여 구성되는 경우가 많다. 차량 속도가 비교적 낮고 운용 환경이 통제되어 있기 때문에 이러한 방식만으로도 충분한 위치 정확도를 확보할 수 있다. 일반적인 도킹(Docking) 정확도는 수 mm에서 수 cm 수준이다.

에너지 효율(Energy Efficiency) 또한 중요한 장점이다. 하중이 낮기 때문에 접지력(Traction) 요구가 적고 구름 저항(Rolling Resistance)도 낮다. 결과적으로 비교적 작은 배터리만으로도 장시간 운용이 가능하다. 이는 충전 인프라(Charging Infrastructure)의 규모를 줄이고 플릿 운영 효율을 향상시키는 데 도움이 된다.

안전성(Safety)은 물류 환경에서 매우 중요한 요소이다. AMR은 사람과 같은 공간을 공유하기 때문에 안전 LiDAR(Safety LiDAR), 비상 정지(Emergency Stop), 장애물 감지(Obstacle Detection), 안전 컨트롤러(Safety Controller)를 장착한다. 이를 통해 생산성을 유지하면서도 안전한 협업이 가능해진다.

확장성(Scalability)은 경량 물류 AMR의 가장 큰 장점 중 하나이다. 물류량 증가에 따라 로봇 수를 점진적으로 늘릴 수 있으며, 추가 차량을 투입하더라도 시설 구조를 크게 변경할 필요가 없다. 플릿 관리 시스템은 작업을 자동 분배하고 교통 흐름(Traffic Flow)을 최적화하여 여러 대의 로봇을 효율적으로 운영한다.

많은 제조 공장에서는 경량 물류 AMR을 수작업 운반(Manual Transport)과 완전 자동 물류 시스템(Fully Automated Material Handling System) 사이의 중간 단계 자동화 솔루션으로 활용하고 있다. 전자 산업(Electronics Industry), 제약 산업(Pharmaceutical Industry), 반도체 산업(Semiconductor Industry), 소비재 산업(Consumer Goods Industry) 등에서 특히 높은 활용도를 보인다.

또한 중량급 운반 로봇에 비해 시스템 가격이 낮기 때문에 투자 회수 기간(Return on Investment)도 짧은 편이다. 인건비 절감, 운반 지연 감소, 물류 추적성(Traceability) 향상, 운영 유연성 증대 등의 효과를 통해 높은 경제성을 제공한다.

그러나 이러한 경량 물류 AMR은 기본적으로 중간 수준 이하의 하중과 실내 환경을 전제로 설계되어 있다. 따라서 하중이 증가하기 시작하면 추가적인 설계 고려 사항이 필요하며, 이는 경량 플랫폼과 중량급 산업용 운반 플랫폼을 구분하는 중요한 기준이 된다.

---

### 5.2 중량 한계 이하 영역에서의 제약 사항(Limitations Below Heavy Load Threshold)

경량 물류 AMR은 중간 수준의 물류 운반에서는 매우 우수한 성능을 제공하지만, 하중이 증가하여 중량급 운반 영역에 접근하게 되면 다양한 한계가 나타난다. 이러한 제약을 이해하는 것은 적절한 구동 방식(Drive System) 선정, 플랫폼 설계, 장기적인 확장 전략 수립에 매우 중요하다.

가장 큰 한계는 바퀴와 지면 사이의 상호작용(Wheel-Ground Interaction)에서 발생한다. 하중이 증가하면 바퀴에 작용하는 수직 하중(Normal Force)도 증가한다. 이는 구름 저항(Rolling Resistance), 베어링 부하(Bearing Load), 타이어 변형(Tire Deformation), 구동 토크 요구량 증가로 이어진다. 경량 하중에서는 문제가 없던 부품도 중량 증가에 따라 마모가 급격히 증가할 수 있다.

특히 차동 구동은 하중 증가의 영향을 크게 받는다. 회전 시 발생하는 횡방향 스크러빙(Lateral Scrubbing)이 차량 중량에 비례하여 증가하기 때문이다. 일반 차동 구동 바퀴는 실제 회전 궤적에 맞춰 방향을 조정할 수 없으므로 접촉 패치(Contact Patch)에서 상당한 측면 힘(Side Force)이 발생한다.

페이로드가 수백 kg 수준에 접근하면 이러한 현상이 눈에 띄게 증가한다. 회전 시 필요한 토크가 직선 주행보다 훨씬 커질 수 있으며, 초기 설계 시 충분하다고 판단된 모터 용량도 장기 운용에서는 부족해질 수 있다.

구조적 한계(Structural Limitation)도 나타난다. 하중 증가에 따라 섀시 변형(Chassis Deflection)이 커지고, 이는 휠 정렬(Wheel Alignment)과 하중 분배(Load Distribution)에 영향을 준다. 일부 바퀴에 하중이 집중되면 슬립 증가, 접지력 저하, 예측하기 어려운 주행 특성이 발생할 수 있다. 또한 정밀 도킹 성능도 저하될 수 있다.

배터리 시스템(Battery System) 역시 영향을 받는다. 무거운 하중은 더 많은 가속력과 제동력을 요구하기 때문에 에너지 소비가 증가한다. 결과적으로 운행 시간이 감소하며, 생산성을 유지하려면 더 큰 배터리 또는 더 많은 충전 스테이션이 필요할 수 있다.

열 관리(Thermal Management)도 중요한 문제가 된다. 모터, 기어박스, 모터 드라이버, 배터리는 토크 요구량이 증가함에 따라 더 많은 열을 발생시킨다. 적절한 냉각 시스템이 없다면 온도 상승으로 인해 부품 수명이 감소하고 연속 운전 성능도 제한될 수 있다.

동적 안정성(Dynamic Stability) 역시 변화한다. 차량 질량이 증가하면 관성(Inertia)이 커지기 때문에 제동 거리, 비상 정지 성능, 장애물 회피 성능에 영향을 준다. 따라서 보다 정교한 경로 계획(Path Planning)과 동적 제어(Dynamic Control)가 필요해진다.

위치 정확도(Position Accuracy)도 저하될 수 있다. 하중 증가로 인해 바퀴 변형이 증가하고 슬립 가능성이 높아지기 때문이다. 엔코더 기반 오도메트리의 오차가 증가하며, 이를 보완하기 위해 더 정밀한 LiDAR, IMU, Vision Sensor, Sensor Fusion 기술이 요구된다.

바닥 하중(Floor Loading)도 고려해야 한다. 경량 AMR을 기준으로 설계된 시설은 반복적인 중량 하중 운반에 적합하지 않을 수 있다. 바닥 평탄도(Floor Flatness), 내마모성(Wear Resistance), 이음새(Expansion Joint), 구조 강도(Structural Strength)가 장기 성능에 영향을 준다.

이러한 이유로 산업 현장에서는 하중 증가에 따라 차동 구동에서 스티어 구동(Steer Drive)으로 전환하는 경우가 많다. 스티어 구동은 횡방향 스크러빙을 크게 줄이고 에너지 효율을 향상시키며, 타이어 마모를 줄이고 위치 정확도를 유지할 수 있기 때문이다.

일반적으로 약 200\~300kg 이하의 페이로드에서는 경량 물류 AMR이 매우 효율적이다. 그러나 500kg 이상에 접근하기 시작하면 스티어 구동 또는 그 이상의 고급 구동 구조가 점점 더 유리해진다.

따라서 중량 한계 이하 영역에서의 제약을 이해하는 것은 단순히 현재 성능을 평가하는 것이 아니라 향후 확장성(Scalability), 유지보수 비용(Maintenance Cost), 운영 효율(Operation Efficiency), 장기 신뢰성(Long-Term Reliability)을 고려한 플랫폼 선택 과정이라고 볼 수 있다.

특히 힐스로보틱스(Hills Robotics)가 개발 중인 500kg, 1000kg, 1500kg급 산업용 AMR 관점에서는 약 300kg 이하에서는 차동 구동도 충분히 경쟁력이 있지만, 500kg 이상부터는 스티어 구동이 에너지 효율, 정밀도, 유지보수성 측면에서 더욱 적합한 선택이 되는 경우가 많다. 이는 중량 증가에 따라 슬립, 스크러빙, 구조 부하가 기하급수적으로 증가하기 때문이다.
