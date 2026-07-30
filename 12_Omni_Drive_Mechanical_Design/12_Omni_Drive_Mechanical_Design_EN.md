**Differential Drive & Steer Drive Engineering**

# Chapter 12 Omni Drive Mechanical Design

## 01 Omni and Mecanum wheel selection

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Selecting the appropriate omni wheel or Mecanum wheel is one of the most critical decisions in the design of an omnidirectional mobile robot. While kinematic algorithms determine how the robot moves mathematically, the wheel itself ultimately defines how effectively those commands are translated into real-world motion. Wheel selection influences traction, vibration, positioning accuracy, energy efficiency, durability, maintenance requirements, payload capacity, and long-term reliability. Even an advanced control system cannot compensate for an improperly selected wheel that is unsuitable for the intended operating environment.

Omni wheels and Mecanum wheels share the common objective of enabling omnidirectional motion through passive rollers. However, differences in roller material, wheel diameter, structural stiffness, bearing quality, load rating, and manufacturing precision produce significant differences in vehicle performance. Engineers must therefore evaluate wheel characteristics as part of the overall system rather than considering them as isolated mechanical components.

Industrial applications impose a wide range of requirements. Semiconductor transport robots emphasize extremely low vibration, smooth rolling behavior, and contamination control. Warehouse robots prioritize durability, payload capacity, and long service life under continuous operation. Hospital service robots require quiet operation, comfortable motion, and protection of sensitive floor surfaces. Heavy-duty manufacturing platforms demand high load capacity while maintaining stable positioning during precision docking operations.

Wheel selection also affects the performance of navigation and localization systems. Excessive wheel deformation, roller compliance, or inconsistent contact with the floor may introduce odometry errors that accumulate over time. Since wheel encoders measure rotational motion rather than actual vehicle displacement, any variation between theoretical and effective wheel geometry directly impacts localization accuracy. Consequently, wheel material and construction must be considered together with the control system.

Maintenance strategy represents another important consideration. Wheel rollers gradually wear under repeated loading, changing the effective wheel diameter and altering traction characteristics. Bearings experience continuous rotational loading that may eventually increase rolling resistance or introduce vibration. Industrial robots operating twenty-four hours per day therefore require wheel assemblies designed for predictable maintenance intervals, rapid replacement, and long operational life.

Ultimately, selecting the proper omni or Mecanum wheel involves balancing mechanical performance, environmental compatibility, manufacturing cost, expected service life, and operational reliability. A systematic engineering approach ensures that the wheel design complements the intended application while maximizing overall robotic performance throughout the product lifecycle.

---

### 1.1 Roller Material: PU vs Rubber vs Nylon

---

Roller material is one of the most influential factors affecting the performance of omni wheels and Mecanum wheels. Since passive rollers provide the only direct contact between the robot and the floor during multidirectional movement, their mechanical properties determine traction, vibration, rolling resistance, wear characteristics, noise generation, and floor compatibility. Three materials dominate industrial applications: polyurethane (PU), rubber, and nylon.

Polyurethane has become the preferred material for many industrial omnidirectional robots because it provides an excellent balance between durability, elasticity, and wear resistance. PU rollers maintain stable dimensions over extended operating periods while offering sufficient compliance to absorb minor floor irregularities. Their relatively low rolling noise and excellent abrasion resistance make them particularly suitable for semiconductor manufacturing, electronics assembly, warehouse automation, and precision industrial AMRs. Different hardness grades allow engineers to optimize performance for specific payloads and floor conditions.

Rubber rollers provide the highest friction coefficient among the three materials, resulting in excellent traction during acceleration, deceleration, and precise positioning. Their high elasticity effectively absorbs vibration and reduces transmitted shock, improving ride comfort and protecting sensitive payloads. However, rubber generally exhibits faster wear than polyurethane, especially under heavy loads or continuous industrial operation. Rolling resistance is also higher, increasing energy consumption and reducing overall propulsion efficiency. Rubber rollers are therefore commonly selected for service robots, medical robots, and applications where vibration reduction is more important than maximum durability.

Nylon rollers represent the opposite end of the material spectrum. Their high hardness minimizes deformation under heavy loads, producing excellent dimensional stability and low rolling resistance. This improves energy efficiency and maintains consistent kinematic behavior over long operating periods. However, the reduced compliance increases vibration transmission and acoustic noise. Nylon also provides lower friction than polyurethane or rubber, potentially reducing traction on smooth industrial floors. Consequently, nylon rollers are generally preferred for high-load transport systems, automated manufacturing equipment, and applications requiring maximum structural rigidity rather than vibration isolation.

Material selection also affects environmental compatibility. Polyurethane and rubber generally perform better on polished epoxy floors commonly found in factories and warehouses. Nylon performs well on hard concrete or precision-machined industrial flooring but may become noisy on rough surfaces. Temperature stability, chemical resistance, electrostatic discharge characteristics, and cleanroom compatibility further influence material choice in specialized industries.

Rather than identifying a universally superior material, engineers should select roller materials according to application requirements. Polyurethane offers the most balanced overall performance, rubber prioritizes traction and vibration isolation, while nylon emphasizes structural rigidity, dimensional stability, and high load capacity.

### 1.2 Wheel Diameter and Load Rating

---

Wheel diameter plays a fundamental role in determining the mechanical and dynamic performance of omnidirectional mobile robots. Diameter directly influences obstacle-climbing capability, rolling resistance, acceleration, maximum speed, motor torque requirements, and overall vehicle stability. At the same time, load rating defines the maximum continuous load each wheel can safely support without excessive deformation, premature wear, or mechanical failure.

Larger wheel diameters generally improve mobility by reducing the approach angle when crossing floor joints, expansion gaps, cable protectors, and minor obstacles. Rolling resistance decreases because the wheel experiences smaller angular displacement while traversing surface irregularities. Consequently, larger wheels provide smoother motion, reduced vibration, and improved energy efficiency during long-distance operation.

However, increasing wheel diameter also increases rotational inertia. Larger wheels require greater motor torque during acceleration and deceleration, potentially reducing dynamic responsiveness. Wheel assemblies become heavier and occupy more chassis space, affecting vehicle dimensions and packaging constraints. Engineers must therefore balance obstacle-crossing capability against dynamic performance and overall system weight.

Smaller wheels offer lower rotating inertia and faster dynamic response. They allow compact chassis designs suitable for robots operating in highly confined environments. Nevertheless, smaller wheels generate greater vibration when crossing floor imperfections and require higher rotational speeds to achieve the same vehicle velocity. Increased bearing speed may reduce service life under continuous industrial operation.

Load rating is equally important. Every wheel manufacturer specifies a maximum continuous load based on bearing capacity, roller strength, wheel hub stiffness, and expected service life. Dynamic loads generated during acceleration, braking, or collision may substantially exceed static vehicle weight. Engineers therefore incorporate appropriate safety margins when selecting wheel capacity.

Uneven load distribution presents another practical challenge. Manufacturing tolerances, chassis deformation, suspension characteristics, and payload location all influence how vehicle weight is distributed among individual wheels. Ideally, each wheel should carry approximately equal load during normal operation. Excessive loading of one wheel accelerates roller wear, increases bearing stress, and degrades positioning accuracy.

Heavy industrial AMRs frequently employ larger wheels with reinforced hubs and higher-capacity bearings to support payloads exceeding several hundred kilograms. Lightweight service robots, educational platforms, and laboratory automation systems typically prioritize compact dimensions and rapid maneuverability, favoring smaller wheel diameters.

Ultimately, wheel diameter and load rating should be selected as integrated system parameters rather than independent mechanical specifications. Proper optimization ensures smooth vehicle motion, reliable long-term operation, efficient motor utilization, and consistent positioning performance throughout the robot\'s operational lifetime.

### 1.3 Floor Condition Requirements: Flatness and Hardness

---

Floor condition is one of the most overlooked yet critical factors affecting the performance of omni wheel and Mecanum wheel mobile robots. Since omnidirectional wheels rely on multiple passive rollers that repeatedly engage and disengage from the floor, even relatively small surface irregularities can influence traction, vibration, positioning accuracy, odometry performance, and overall system reliability. Successful deployment therefore requires careful evaluation of floor flatness, hardness, cleanliness, and long-term maintenance.

Floor flatness directly influences wheel contact continuity. On highly uneven surfaces, individual rollers repeatedly encounter height variations that produce vertical oscillations throughout the chassis. These oscillations increase vibration, reduce sensor stability, and may temporarily decrease wheel traction. High-precision industrial applications therefore specify strict floor flatness tolerances to ensure consistent wheel contact and predictable robot motion.

Smooth epoxy-coated factory floors provide ideal operating conditions for omnidirectional robots. Such surfaces minimize vibration, reduce roller impact, improve encoder accuracy, and extend roller service life. Semiconductor fabrication facilities, electronics assembly plants, and pharmaceutical cleanrooms typically maintain exceptionally flat floors to support precision mobile automation.

Floor hardness also significantly affects performance. Hard surfaces such as polished concrete, epoxy resin, granite, or industrial tiles provide stable support while minimizing energy losses caused by floor deformation. Soft flooring materials, including carpet, rubber mats, or resilient vinyl surfaces, deform under wheel loading. This deformation increases rolling resistance, alters effective wheel geometry, and introduces localization errors because encoder measurements no longer correspond precisely to actual vehicle displacement.

Surface friction must also remain consistent. Excessively slippery floors increase wheel slip during acceleration and braking, while excessively rough surfaces accelerate roller wear and generate unnecessary vibration. Clean floors free from dust, oil, water, metal chips, and manufacturing debris further improve traction consistency while reducing bearing contamination.

Environmental factors should also be considered. Temperature variations may alter roller stiffness, while chemical exposure can degrade certain roller materials. Cleanroom environments require low-particle wheel materials and carefully controlled floor maintenance procedures to minimize airborne contamination generated by wheel-floor interaction.

Industrial facilities often establish floor quality standards specifically for autonomous mobile robots. These standards define allowable flatness deviations, surface hardness, friction characteristics, cleanliness requirements, and maintenance schedules. Periodic floor inspection ensures that long-term wear or damage does not gradually reduce robotic performance.

Rather than viewing floor conditions as external constraints, modern robotic system designers increasingly consider the floor as an integral component of the overall mobility system. Optimizing wheel design together with floor characteristics significantly improves navigation accuracy, reduces maintenance costs, extends wheel service life, and enhances the long-term reliability of omnidirectional robotic platforms.

### 1.1 롤러 재질 : PU vs Rubber vs Nylon (Roller Material: PU vs Rubber vs Nylon)

---

### 1.2 휠 직경과 허용 하중 (Wheel Diameter and Load Rating)

---

### 1.3 바닥 조건 요구 사항 : 평탄도와 경도 (Floor Condition Requirements: Flatness and Hardness)

## 02 Frame architecture for omni drive

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

The frame architecture of an omnidirectional mobile robot is far more than a structural support for wheels and payloads. It is the mechanical foundation that determines vehicle rigidity, weight distribution, dynamic stability, positioning accuracy, vibration characteristics, serviceability, and long-term reliability. Even when advanced control algorithms and high-performance motors are employed, poor frame architecture can introduce structural deformation, wheel misalignment, uneven load distribution, and excessive vibration, all of which reduce overall system performance. Consequently, frame design must be approached as an integrated mechatronic engineering discipline rather than simply a mechanical construction task.

Unlike conventional mobile platforms that primarily move forward, omni-drive robots continuously generate multidirectional force vectors during operation. These forces change direction rapidly as the robot performs lateral translation, diagonal motion, or simultaneous rotation and translation. The frame must therefore resist torsional loads, bending moments, and localized stresses while maintaining precise wheel geometry. Even slight structural deflection can alter wheel mounting angles and degrade the accuracy of the kinematic model, leading to cumulative positioning errors during autonomous navigation.

Modern industrial AMRs typically employ lightweight but highly rigid frame materials such as aluminum alloy extrusions, welded steel structures, carbon fiber composites, or hybrid frame architectures. Aluminum provides an excellent balance between stiffness, weight, corrosion resistance, and manufacturing flexibility. Steel offers higher rigidity and load capacity for heavy-duty platforms, while composite materials reduce mass for high-speed applications. The final material selection depends on payload requirements, manufacturing cost, environmental conditions, and expected service life.

Frame architecture also influences thermal management and electrical integration. Internal structural members frequently serve as mounting locations for batteries, motor controllers, power distribution units, communication devices, cooling systems, and onboard computers. Well-designed cable routing minimizes electromagnetic interference while simplifying maintenance and improving overall system reliability. Modular frame concepts further allow standardized robot platforms to support multiple payload configurations without redesigning the entire vehicle.

Another important consideration is manufacturability. Frames should be designed using standardized profiles, modular joints, and easily replaceable structural components. This approach simplifies assembly, reduces production cost, improves maintenance efficiency, and supports scalable manufacturing. Future upgrades such as additional sensors, robotic manipulators, or battery expansion can often be implemented without major structural modifications.

As industrial robots continue evolving toward heavier payloads, higher speeds, and increasingly autonomous operation, frame architecture becomes a multidisciplinary optimization problem involving mechanical engineering, structural analysis, vibration control, thermal management, manufacturing engineering, and robotic system integration. A properly engineered frame provides the stable mechanical platform upon which every other subsystem depends.

---

### 2.1 Symmetric Layout Design Principles

---

Symmetry is one of the most fundamental design principles in omni-drive mobile robot architecture because it directly influences kinematic consistency, load distribution, dynamic stability, and motion accuracy. A symmetric layout ensures that all wheels contribute equally to vehicle motion, allowing the mathematical assumptions used in the kinematic model to remain valid throughout operation.

In a perfectly symmetric chassis, the geometric center of the robot coincides closely with the center of mass under nominal loading conditions. Wheel positions are arranged at equal distances from the vehicle center, and each drive module experiences similar mechanical loading. This balanced configuration minimizes directional bias and produces nearly identical dynamic behavior regardless of travel direction.

Equal wheel spacing simplifies inverse and forward kinematic calculations because transformation matrices remain well conditioned. Motion commands generated by the controller are translated into wheel velocities with predictable accuracy, while encoder measurements more accurately reconstruct actual vehicle motion. As a result, localization accuracy and path-following performance improve significantly.

Structural symmetry also distributes mechanical stresses more evenly throughout the chassis. During acceleration, braking, or rotation, forces generated by the wheels propagate through the frame with minimal torsional imbalance. Reduced stress concentration improves fatigue life while maintaining dimensional stability over prolonged industrial operation.

Payload placement strongly influences symmetry. Ideally, heavy components such as batteries, onboard computers, power electronics, and manipulators should be positioned as close as possible to the geometric center of the platform. Balanced weight distribution minimizes wheel load variation, improves traction consistency, and reduces suspension deflection.

Symmetry further enhances fault tolerance. If minor manufacturing tolerances or wheel wear occur, their effects tend to remain evenly distributed rather than introducing significant directional drift. This characteristic simplifies calibration procedures and reduces long-term localization error accumulation.

Although perfect symmetry is not always achievable because of application-specific payloads, engineers generally seek to preserve as much geometric balance as possible. Asymmetric sensor placement, manipulator mounting, or battery arrangements are often compensated through structural reinforcement, counterweights, or adaptive control algorithms.

Ultimately, symmetric layout design forms the mechanical basis for predictable omnidirectional motion. It supports accurate kinematic modeling, stable dynamic behavior, efficient force transmission, and reliable long-term operation across a wide variety of industrial robotic applications.

### 2.2 Motor Mounting and Encoder Integration

---

Motor mounting represents one of the most critical aspects of omni-drive frame architecture because it directly affects drivetrain stiffness, positioning accuracy, vibration characteristics, and maintenance accessibility. Every motor converts electrical energy into wheel torque, and the structural interface between the motor and the chassis must maintain precise alignment throughout the robot\'s operational life.

Industrial omni-drive robots typically employ brushless DC motors or permanent magnet synchronous motors coupled with precision planetary gearboxes. These assemblies generate significant torque during acceleration, braking, and rapid multidirectional motion. Consequently, motor mounting brackets must resist both static and dynamic loading while preventing even minor positional shifts that could alter drivetrain geometry.

Rigid mounting significantly improves positioning accuracy. Flexible mounting structures may introduce elastic deformation under load, causing transient wheel misalignment and reducing motion repeatability. Finite element analysis is therefore frequently used during frame design to verify structural stiffness under worst-case operating conditions.

Thermal considerations are equally important. Motors generate heat continuously during operation, particularly in heavy-duty industrial applications. Mounting structures often function as heat conduction paths, transferring thermal energy from the motor housing into the chassis where it can be dissipated more effectively. Proper airflow and thermal isolation of sensitive electronic components further improve system reliability.

Encoder integration is essential for closed-loop motion control. Incremental encoders provide high-resolution rotational feedback for velocity and position control, while absolute encoders preserve position information following power interruptions. Encoder mounting must eliminate mechanical backlash, eccentricity, and vibration to ensure accurate measurement throughout the operating range.

Signal integrity represents another design consideration. Encoder cables should be routed separately from high-current motor power cables to minimize electromagnetic interference. Shielded cables, differential signaling, and proper grounding techniques improve measurement reliability in electrically noisy industrial environments.

Serviceability also influences motor mounting architecture. Modular mounting plates, standardized fasteners, and accessible electrical connectors reduce maintenance time while simplifying motor replacement. Industrial robots designed for continuous operation benefit significantly from rapid component replacement procedures that minimize production downtime.

Ultimately, motor mounting and encoder integration should be viewed as a unified electromechanical subsystem. Precise mechanical alignment, effective thermal management, reliable signal transmission, and maintenance-friendly design collectively determine the long-term accuracy and reliability of omnidirectional motion control.

### 2.3 Payload Deck and CoG Management

The payload deck forms the upper structural interface of an omni-drive robot and serves as the mounting platform for transported materials, robotic manipulators, inspection equipment, medical devices, or industrial process modules. While its primary purpose is supporting payloads, the deck also plays a central role in maintaining vehicle stability through careful management of the center of gravity (CoG).

Center of gravity location significantly influences vehicle dynamics. Ideally, the CoG should remain close to both the geometric center of the chassis and the wheel contact plane. A centrally located CoG distributes weight evenly across all wheels, maximizing traction consistency and minimizing uneven roller wear.

High CoG placement increases overturning moments during acceleration, braking, and lateral motion. This effect becomes particularly important for omni-drive robots because lateral acceleration occurs frequently during normal operation. Tall payloads therefore require careful structural analysis to ensure adequate stability margins under worst-case maneuvering conditions.

Heavy components should be positioned as low as practical within the chassis. Batteries, power electronics, motor controllers, and computing hardware are commonly installed beneath the payload deck to reduce CoG height while leaving the upper surface available for application-specific equipment. This layered architecture simultaneously improves stability and simplifies system integration.

Payload deck stiffness is equally important. Structural deflection under heavy loads may alter sensor alignment, manipulator calibration, or precision inspection geometry. Finite element analysis helps optimize deck thickness, reinforcement ribs, and support structures while minimizing unnecessary mass.

Dynamic payload variation introduces additional challenges. Mobile manipulators continuously change CoG location as robotic arms extend, retract, or lift objects. Advanced control systems may compensate through adaptive velocity limits, trajectory planning, or active suspension mechanisms to preserve stability throughout manipulation tasks.

Modularity has become increasingly important in industrial robot design. Standardized payload decks incorporating multiple mounting interfaces, cable routing channels, power connectors, and communication ports enable rapid integration of diverse application modules without redesigning the underlying vehicle platform. This approach significantly reduces engineering effort while improving product scalability.

Future omni-drive robots are expected to incorporate intelligent payload management systems capable of estimating real-time CoG location using force sensors, inertial measurements, and machine learning algorithms. These systems will dynamically adjust acceleration limits, path planning strategies, and wheel torque distribution to maximize both safety and operational efficiency under continuously changing payload conditions.

Well-designed payload deck architecture therefore extends beyond simple structural support. It becomes a critical component of the robot\'s mechanical, dynamic, and control systems, directly contributing to stability, positioning accuracy, operational flexibility, and long-term industrial reliability.

### 2.1 대칭 레이아웃 설계 원칙 (Symmetric Layout Design Principles)

### 2.2 모터 장착 및 엔코더 통합 (Motor Mounting and Encoder Integration)

### 2.3 적재 데크 및 무게 중심 관리 (Payload Deck and CoG Management)

## 03 Suspension and contact force

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Suspension design is one of the most influential mechanical factors affecting the performance, stability, and positioning accuracy of omnidirectional mobile robots. While considerable attention is often given to wheel selection, motor control, and navigation algorithms, the suspension system plays an equally important role by ensuring that every wheel maintains continuous contact with the ground. Omni wheels and Mecanum wheels rely on multiple passive rollers that generate driving forces only when consistent contact with the floor is maintained. Even brief loss of wheel contact can reduce traction, introduce odometry errors, degrade motion stability, and significantly decrease positioning accuracy.

Unlike conventional automobiles, which primarily use suspension systems to improve ride comfort, industrial autonomous mobile robots employ suspension systems to maintain predictable wheel loading and consistent force transmission. Because omni-drive robots frequently execute lateral motion, diagonal translation, and simultaneous rotation, each wheel experiences continuously changing force vectors. Uneven floor conditions, structural deformation, manufacturing tolerances, and payload variations further alter wheel loading. A properly engineered suspension compensates for these disturbances while preserving the geometric assumptions used by the robot\'s kinematic model.

Contact force distribution directly influences the quality of motion control. Ideally, every wheel should support approximately the same normal force so that traction remains balanced throughout all operating conditions. Unequal wheel loading increases the likelihood of wheel slip, causes uneven roller wear, and introduces directional bias that gradually accumulates into localization errors. Consequently, suspension systems must maintain both mechanical compliance and sufficient structural rigidity to support high-precision autonomous navigation.

Industrial AMRs commonly utilize passive suspension systems because they provide simplicity, reliability, and low maintenance requirements. Spring-loaded mechanisms, compliant wheel modules, rocker assemblies, and articulated mounting structures compensate for floor irregularities without requiring active control. More advanced robotic platforms may incorporate semi-active or fully active suspension systems that dynamically adjust wheel loading according to payload distribution, vehicle acceleration, and terrain conditions. Although these systems improve performance, they also increase mechanical complexity, cost, and maintenance effort.

Suspension architecture must also be integrated with frame design, wheel geometry, and payload management. Excessive suspension travel may alter wheel mounting geometry and reduce kinematic accuracy, while insufficient compliance prevents wheels from following uneven floor surfaces. Engineers therefore optimize suspension stiffness, damping characteristics, travel range, and structural rigidity simultaneously to achieve the desired balance between positioning precision and terrain adaptability.

As autonomous robots become increasingly responsible for transporting valuable products, performing precision manufacturing tasks, and collaborating safely with human workers, suspension design has evolved from a secondary mechanical consideration into a critical subsystem that directly influences overall robotic performance, operational safety, and long-term reliability.

---

### 3.1 Importance of Constant Wheel Ground Contact

---

Continuous wheel-ground contact is one of the most fundamental requirements for reliable omnidirectional motion. Every omni wheel or Mecanum wheel generates driving force only when its rollers maintain stable contact with the supporting surface. If one or more wheels temporarily lose contact with the floor due to uneven terrain, structural deformation, or payload imbalance, the corresponding drive forces immediately decrease, reducing motion accuracy and potentially destabilizing the entire control system.

Unlike conventional differential-drive vehicles, omnidirectional robots distribute motion generation among multiple independently driven wheels. Each wheel contributes a specific component of the overall force vector according to the vehicle\'s kinematic model. Consequently, losing contact at even a single wheel alters the force balance assumed by the controller. The remaining wheels must compensate for the missing traction, often producing unexpected rotation, lateral drift, or positioning errors.

Ground contact directly affects odometry accuracy as well. Wheel encoders assume that wheel rotation corresponds precisely to vehicle displacement. During partial wheel unloading or temporary loss of contact, wheels may continue rotating without generating equivalent vehicle motion. Encoder measurements therefore overestimate actual displacement, introducing cumulative localization errors that increase over time.

Payload distribution significantly influences contact quality. Heavy payloads positioned away from the geometric center increase wheel load variation, especially during acceleration and braking. Similarly, mobile manipulators continuously shift the vehicle\'s center of gravity while manipulating objects, altering wheel contact forces dynamically throughout operation. Maintaining continuous contact under these conditions requires carefully designed suspension systems and balanced structural layouts.

Floor quality represents another important factor. Small height differences caused by expansion joints, worn concrete, embedded rails, cable protectors, or manufacturing tolerances may temporarily unload individual wheels. Even height variations of only a few millimeters can significantly influence wheel loading because omnidirectional robots generally employ relatively rigid chassis structures.

Maintaining constant ground contact therefore improves multiple aspects of robotic performance simultaneously. Balanced traction enhances motion accuracy, consistent encoder measurements improve localization, uniform wheel loading reduces roller wear, and predictable force transmission simplifies controller tuning. These benefits collectively increase navigation reliability while extending component service life.

Modern industrial AMRs frequently employ compliance mechanisms, passive suspension modules, floating wheel assemblies, or articulated frame designs specifically to preserve wheel contact under realistic operating conditions. As positioning accuracy requirements continue increasing, constant wheel-ground contact remains one of the most essential design objectives in omnidirectional robotics.

### 3.2 Spring Loaded Passive Suspension Design

---

Spring-loaded passive suspension represents one of the most widely adopted suspension architectures for industrial omnidirectional mobile robots because it combines mechanical simplicity, reliability, and effective wheel contact maintenance. Unlike active suspension systems that require sensors, actuators, and electronic control, passive suspension relies entirely on carefully selected mechanical springs and structural geometry to accommodate floor irregularities.

Each wheel module typically incorporates an independent spring mechanism allowing limited vertical movement relative to the chassis. When a wheel encounters a raised surface, the spring compresses while maintaining nearly constant contact force. Conversely, when passing over a depression, the spring extends, preventing wheel separation from the floor. This simple compliance mechanism significantly improves traction consistency without introducing additional control complexity.

Spring stiffness represents the most important design parameter. Excessively stiff springs reduce suspension travel and prevent wheels from following uneven surfaces effectively. Wheel unloading becomes more likely, increasing localization error and reducing motion stability. Conversely, excessively soft springs permit excessive chassis movement, introducing unwanted oscillations that degrade positioning accuracy and sensor stability.

Preload adjustment provides another useful design feature. Initial spring compression establishes the nominal contact force acting on each wheel before payload loading. Adjustable preload mechanisms allow engineers to compensate for manufacturing tolerances, structural asymmetry, and different payload configurations while maintaining balanced wheel loading across the entire vehicle.

Passive suspension geometry must also minimize changes in wheel orientation during vertical motion. Ideally, wheel mounting angles remain nearly constant throughout suspension travel to preserve kinematic accuracy. Linkage mechanisms, guide rails, linear bearings, or compliant flexure structures help constrain wheel motion while maintaining geometric consistency.

Although passive suspension does not actively regulate wheel forces, its simplicity provides substantial practical advantages. Mechanical reliability remains high because relatively few moving components are involved. Energy consumption is negligible, maintenance requirements are minimal, and system cost remains significantly lower than electronically controlled suspension alternatives.

Industrial robots operating in warehouses, semiconductor facilities, hospitals, and manufacturing plants frequently benefit from spring-loaded suspension because floor irregularities generally remain small but unavoidable. Passive compliance sufficiently accommodates these variations while preserving the precise positioning required for autonomous docking and material handling.

As payload capacity increases, engineers often combine spring-loaded suspension with structural optimization, compliant wheel modules, and advanced localization algorithms. This integrated approach provides an excellent balance between mechanical robustness, positioning accuracy, manufacturing cost, and long-term operational reliability, making passive suspension the preferred solution for many commercial omnidirectional robotic platforms.

### 3.3 Floor Flatness Tolerance Analysis

---

Floor flatness tolerance analysis is an essential engineering activity for ensuring reliable operation of omnidirectional mobile robots. Because omni wheels and Mecanum wheels depend on continuous roller contact with relatively smooth surfaces, floor quality directly influences wheel loading, vibration, localization accuracy, and long-term mechanical durability. Understanding acceptable floor tolerances enables engineers to match robot design with realistic operating environments.

Floor flatness is typically specified as the maximum allowable height variation over a defined measurement distance. Small deviations that appear insignificant for human operators may produce measurable effects on robotic performance because wheel diameters are relatively small and positioning requirements are often within only a few millimeters.

When the floor contains local height variations, individual wheel modules experience alternating loading and unloading cycles. These repeated load fluctuations increase roller fatigue, accelerate bearing wear, and generate vibration throughout the chassis. Sensitive sensors including LiDAR, cameras, and inertial measurement units may experience reduced measurement quality because of these mechanical disturbances.

Kinematic accuracy also depends on floor flatness. Transformation matrices assume that wheel mounting geometry remains constant relative to the supporting surface. Significant floor irregularities alter effective wheel positions through suspension movement and chassis deformation, introducing small but cumulative errors into both forward and inverse kinematic calculations.

Finite element analysis and multibody dynamic simulation frequently support tolerance evaluation during robot development. Engineers simulate expected floor profiles, payload distributions, and suspension characteristics to predict wheel loading under realistic operating conditions. These analyses identify critical suspension parameters and determine acceptable floor quality requirements before prototype construction begins.

Practical industrial environments rarely provide perfectly flat floors. Expansion joints, manufacturing wear, concrete settlement, drainage slopes, embedded utilities, and localized repairs all introduce geometric variation. Consequently, robot designers generally specify allowable floor tolerances together with corresponding suspension capabilities and operational speed limits.

Routine floor inspection also contributes to long-term reliability. Laser profilometers, digital levels, three-dimensional scanning systems, and mobile inspection robots can monitor floor degradation over time. Preventive maintenance allows damaged areas to be repaired before they significantly affect robotic performance.

Rather than considering floor flatness solely as a facility issue, modern robotic engineering treats it as a system-level design parameter closely linked with suspension architecture, wheel selection, localization algorithms, and motion control. Optimizing these elements together enables omnidirectional robots to maintain precise navigation, stable motion, and reliable autonomous operation even under realistic industrial floor conditions.

### 3.1 일정한 휠-노면 접촉의 중요성 (Importance of Constant Wheel Ground Contact)

---

### 3.2 스프링 기반 패시브 서스펜션 설계 (Spring Loaded Passive Suspension Design)

---

### 3.3 바닥 평탄도 허용오차 분석 (Floor Flatness Tolerance Analysis)

## 04 Load distribution and bearing design

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Load distribution and bearing design form the mechanical foundation that determines the structural integrity, durability, and operational reliability of omnidirectional mobile robots. While kinematic algorithms govern how a robot should move and motor controllers determine how wheel torque is generated, the entire system ultimately depends on the ability of the wheel assemblies, bearings, axles, and hubs to safely transmit mechanical loads throughout years of continuous operation. Improper load estimation or insufficient bearing capacity may not immediately affect robot performance, but it gradually accelerates component wear, increases vibration, reduces positioning accuracy, and eventually leads to mechanical failure.

Omni-wheel and Mecanum-wheel platforms present unique load distribution challenges because driving forces are transmitted through multiple passive rollers rather than a continuous tire contact patch. Each wheel simultaneously experiences vertical loads generated by vehicle weight, longitudinal forces during acceleration and braking, lateral forces during sideways motion, and combined loading during omnidirectional movement. Consequently, structural components must be evaluated under complex multi-axis loading conditions rather than simple static compression.

The distribution of vehicle weight among individual wheels directly influences traction consistency, roller wear, bearing fatigue, and odometry accuracy. Ideally, each wheel should support nearly identical normal force throughout normal operation. However, manufacturing tolerances, payload location, chassis deformation, suspension movement, and dynamic acceleration continuously alter wheel loading. Engineers therefore apply both static and dynamic load analysis during the design phase to ensure that every structural component remains within its allowable stress limits.

Bearing selection represents one of the most critical engineering decisions because bearings experience continuous rotational loading during every vehicle movement. Their lifetime depends not only on static load capacity but also on rotational speed, lubrication quality, contamination, temperature, shock loading, and installation accuracy. Industrial robot designers typically evaluate bearing performance using internationally standardized fatigue-life calculations such as the ISO L10 life model, ensuring predictable service intervals and long-term operational reliability.

Axles and wheel hubs must likewise withstand repeated cyclic loading without excessive deformation or fatigue failure. Since omnidirectional robots frequently reverse direction, perform lateral translation, and execute rapid rotational maneuvers, their structural members experience highly variable stress histories. Finite element analysis, fatigue simulation, and experimental validation therefore play essential roles during product development.

As industrial robots increasingly transport heavier payloads while operating continuously in automated factories, warehouses, hospitals, and semiconductor facilities, load distribution and bearing design have evolved from basic mechanical calculations into multidisciplinary engineering activities integrating structural mechanics, fatigue analysis, tribology, manufacturing engineering, and predictive maintenance. Proper engineering in these areas significantly extends component life while improving positioning accuracy, operational safety, and overall system reliability.

---

### 4.1 Static Load Per Wheel Calculation

---

Static load calculation is the first step in designing a reliable wheel system for omnidirectional mobile robots. Before considering acceleration, braking, cornering, or vibration, engineers must determine how the total vehicle weight is distributed among individual wheels under stationary conditions. These calculations establish the baseline loading used for selecting wheels, bearings, axles, suspension components, and structural members.

The total static load consists of the combined weight of the chassis, batteries, motors, controllers, sensors, onboard computers, payload, and any attached robotic manipulators or inspection equipment. Under ideal conditions with a perfectly symmetric chassis and centrally located center of gravity, each wheel supports an equal proportion of the total vehicle weight. For a four-wheel robot, the nominal static load per wheel equals approximately one quarter of the total weight, while a three-wheel platform distributes the load equally among three contact points.

Real industrial robots rarely achieve perfect load symmetry. Batteries may occupy one side of the chassis, manipulators extend beyond the vehicle perimeter, and payloads vary continuously during operation. Consequently, engineers calculate wheel loads using the actual center-of-gravity location rather than assuming equal weight distribution. Static equilibrium equations determine the reaction forces acting on each wheel while accounting for vehicle geometry and payload position.

Safety factors are introduced because real operating conditions always differ from theoretical calculations. Manufacturing tolerances, assembly variation, floor irregularities, and uneven payload placement may temporarily increase wheel loading beyond the nominal value. Industrial mobile robots commonly employ safety factors between 1.5 and 2.5 depending on application severity, ensuring that wheel assemblies remain mechanically reliable even under unfavorable conditions.

Suspension characteristics also influence static load distribution. Compliant suspension systems help equalize wheel loading despite minor floor irregularities, while rigid chassis designs may transfer disproportionate loads onto specific wheels. Engineers therefore analyze suspension stiffness together with static equilibrium to predict realistic wheel forces.

Static calculations also support motor selection because wheel loading determines rolling resistance and required traction force. Increased wheel load generally improves traction but simultaneously raises rolling resistance and bearing loading. Optimizing these competing effects requires balancing payload capacity, energy efficiency, and mechanical durability.

Although static loading represents only the starting point of structural analysis, accurate static calculations establish the foundation for every subsequent engineering activity including bearing selection, fatigue analysis, suspension optimization, finite element simulation, and long-term reliability prediction.

### 4.2 Roller Bearing Selection and L10 Life

---

Roller bearings are among the most critical mechanical components within omni-wheel and Mecanum-wheel assemblies because they enable smooth wheel rotation while supporting both radial and axial loads. Their performance directly affects motion accuracy, energy efficiency, vibration characteristics, and long-term reliability. Bearing failure often results in increased rolling resistance, positioning errors, excessive heat generation, and ultimately vehicle downtime.

Selecting an appropriate bearing begins with identifying the expected loading conditions. Radial loads originate from vehicle weight and payload, while axial loads arise from multidirectional motion, wheel alignment errors, and lateral force transmission. Omnidirectional robots frequently generate combined loading conditions requiring bearings capable of supporting simultaneous radial and axial forces without excessive internal stress.

Bearing type depends on application requirements. Deep-groove ball bearings provide low friction and high rotational speed capability for lightweight robots. Angular-contact bearings better accommodate combined loading while maintaining positioning accuracy. Tapered roller bearings support heavier industrial payloads by distributing contact forces over larger rolling elements. Needle bearings provide compact packaging where installation space is limited.

Fatigue life prediction is commonly performed using the internationally standardized L10 life model. L10 life represents the number of revolutions at which 90 percent of identical bearings are statistically expected to survive under specified operating conditions. This standardized methodology enables engineers to compare bearing alternatives objectively while designing predictable maintenance schedules.

Several practical factors influence actual bearing life beyond theoretical calculations. Lubrication quality determines friction, temperature, and wear characteristics. Contamination from dust, moisture, chemicals, or metallic particles significantly accelerates bearing degradation. Misalignment introduced during assembly creates uneven internal loading that shortens fatigue life. Shock loading caused by floor irregularities or accidental collisions further reduces service life.

Industrial robotic systems therefore employ sealed bearings, high-quality lubricants, precision machining, and carefully controlled assembly procedures to maximize bearing longevity. Predictive maintenance strategies increasingly monitor bearing vibration, temperature, acoustic emission, and motor current signatures to identify early signs of degradation before catastrophic failure occurs.

Proper bearing selection ultimately balances mechanical capacity, fatigue life, friction characteristics, environmental compatibility, maintenance requirements, and overall system cost. Well-designed bearing systems significantly improve positioning repeatability while minimizing maintenance downtime throughout the robot\'s operational lifetime.

### 4.3 Axle and Hub Stress Analysis

---

Axles and wheel hubs form the primary structural interface between the drive system and the mobile robot chassis. Every driving force, braking force, payload load, and impact load passes through these components before reaching the wheels. Consequently, accurate stress analysis is essential for ensuring structural safety, long-term fatigue resistance, and reliable vehicle performance.

The axle primarily experiences bending moments generated by vertical wheel loads together with torsional stresses produced by motor torque transmission. During multidirectional motion, combined loading becomes particularly complex because lateral driving forces generate additional shear stresses. Engineers therefore evaluate axle strength using combined stress theories rather than considering bending and torsion independently.

Wheel hubs transfer loads between bearings, wheels, and axles while maintaining precise geometric alignment. Excessive hub deformation alters wheel orientation and introduces positioning errors into the robot\'s kinematic model. High hub stiffness therefore contributes directly to localization accuracy, motion repeatability, and stable omnidirectional movement.

Finite element analysis has become the standard engineering tool for evaluating axle and hub performance. Three-dimensional simulation predicts stress concentration, deformation, safety margins, and fatigue-critical regions under realistic loading conditions. Particular attention is paid to geometric discontinuities such as fillets, keyways, bolt holes, retaining grooves, and threaded sections because these features frequently become fatigue initiation sites.

Material selection strongly influences structural performance. Alloy steels provide high strength and excellent fatigue resistance for heavy industrial robots. Aluminum alloys reduce weight while maintaining acceptable stiffness for medium-duty applications. Advanced composites may be employed where minimum rotating inertia is required, although their higher manufacturing cost limits widespread industrial adoption.

Fatigue analysis represents a critical design activity because industrial robots experience millions of loading cycles throughout their operational life. Unlike static structural calculations, fatigue evaluation considers repeated stress fluctuations generated by acceleration, braking, payload changes, and multidirectional movement. Engineers generally design axles and hubs to maintain stresses well below material endurance limits while incorporating suitable safety factors for manufacturing variation and unexpected operating conditions.

Experimental validation complements analytical simulation. Static load testing verifies structural stiffness, while accelerated fatigue testing reproduces long-term operating conditions within compressed laboratory schedules. Strain gauges, displacement sensors, and digital image correlation techniques measure actual structural response, allowing engineers to validate finite element models and refine design assumptions.

Well-engineered axle and hub systems provide the mechanical stability required for accurate omnidirectional motion throughout years of industrial service. Their design directly influences positioning precision, drivetrain reliability, maintenance intervals, operational safety, and overall lifecycle cost, making stress analysis an indispensable element of professional robotic mechanical engineering.

### 4.1 휠당 정적 하중 계산 (Static Load Per Wheel Calculation)

---

### 4.2 롤러 베어링 선정 및 L10 수명 (Roller Bearing Selection and L10 Life)

---

### 4.3 차축 및 허브 응력 해석 (Axle and Hub Stress Analysis)

## 05 Vibration and noise characteristics

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

Vibration and noise are among the most important performance indicators of omnidirectional mobile robots because they directly influence positioning accuracy, payload stability, sensor performance, operator comfort, and long-term mechanical reliability. While omnidirectional wheel systems provide exceptional maneuverability, their unique roller-based construction inevitably introduces vibration mechanisms that differ significantly from those found in conventional pneumatic or solid wheels. Understanding these vibration sources allows engineers to improve robot performance through careful mechanical design, suspension optimization, wheel selection, and structural damping.

Unlike conventional wheels that maintain a continuous contact patch with the floor, omni wheels and Mecanum wheels generate motion through multiple passive rollers arranged around the wheel circumference. As the wheel rotates, individual rollers repeatedly enter and leave contact with the floor. This periodic contact transition creates cyclic variations in contact force, rolling radius, and wheel stiffness. Consequently, vibration is an inherent characteristic of omnidirectional wheel systems rather than a manufacturing defect.

The vibration generated by roller transitions propagates throughout the robot structure. Motors, gearboxes, wheel modules, chassis members, payload decks, onboard computers, cameras, LiDAR sensors, inertial measurement units, and robotic manipulators may all experience vibration-induced disturbances. High-frequency vibration can reduce localization accuracy, increase image blur, shorten component fatigue life, and degrade precision inspection or manipulation tasks.

Noise generation follows similar physical mechanisms. Every roller impact produces small impulsive forces that excite structural resonances within the wheel, frame, and surrounding environment. Floor material, roller hardness, wheel speed, payload weight, and suspension characteristics all influence the resulting acoustic signature. Industrial environments increasingly require quieter robotic systems, especially in hospitals, laboratories, offices, and collaborative manufacturing spaces where robots operate alongside human workers.

Modern engineering therefore treats vibration and noise reduction as system-level optimization problems rather than isolated wheel design issues. Roller geometry, roller material, bearing quality, suspension compliance, frame stiffness, payload mounting, motor control algorithms, and vehicle operating speed all contribute to overall vibration behavior. Simulation tools including multibody dynamics, finite element analysis, modal analysis, and acoustic simulation help engineers predict vibration performance before physical prototypes are constructed.

Advanced industrial robots increasingly incorporate vibration isolation mounts, compliant suspension systems, optimized wheel geometry, active motion control, and predictive maintenance algorithms to reduce vibration while maintaining precise omnidirectional mobility. As autonomous robots continue entering precision manufacturing, semiconductor production, healthcare, and laboratory automation, minimizing vibration and acoustic emissions becomes increasingly important for achieving both technical performance and user acceptance.

---

### 5.1 Roller Contact Polygon Effect and Vibration

---

One of the most distinctive vibration sources in omni wheels and Mecanum wheels originates from the roller contact polygon effect. Unlike conventional wheels that maintain nearly continuous contact with the ground through a circular tire profile, omnidirectional wheels contact the floor through discrete passive rollers arranged around the wheel circumference. As the wheel rotates, contact transfers repeatedly from one roller to the next, creating a polygon-like approximation of a continuous rolling surface.

This geometric characteristic causes the effective rolling radius to fluctuate periodically. Instead of maintaining a perfectly constant wheel radius, the robot experiences very small vertical displacements every time contact transitions between adjacent rollers. Although individual height variations may measure only fractions of a millimeter, these periodic disturbances occur continuously during motion and generate measurable vibration throughout the vehicle.

The vibration frequency depends primarily on wheel rotational speed and roller count. Wheels containing more rollers generally produce smaller contact transitions because the angular spacing between rollers decreases. Consequently, increasing roller count often reduces vibration amplitude while simultaneously increasing manufacturing complexity, wheel weight, and production cost.

Roller diameter also influences vibration behavior. Larger rollers generally improve obstacle traversal and distribute contact forces over larger areas, reducing local stress concentrations. Smaller rollers create smoother geometric approximations but may exhibit increased bearing loading and reduced durability. Engineers therefore optimize roller geometry according to application-specific requirements.

Roller material further affects impact behavior. Soft polyurethane rollers absorb contact energy more effectively than rigid nylon rollers, reducing high-frequency vibration while improving ride quality. However, increased material compliance may slightly reduce positioning precision because elastic deformation alters effective wheel geometry under load.

The contact polygon effect becomes particularly noticeable during high-speed operation or when traversing hard industrial floors. Smooth epoxy surfaces transmit vibration efficiently into the robot chassis, while softer flooring materials partially attenuate impact energy. Payload weight also modifies vibration characteristics because heavier loads increase contact force during roller transitions.

Engineers analyze these phenomena using multibody dynamic simulation, modal analysis, experimental accelerometer measurements, and frequency-domain signal analysis. Understanding the roller contact polygon enables designers to optimize wheel geometry, suspension stiffness, structural damping, and operating speed to minimize vibration while preserving omnidirectional mobility.

### 5.2 Vibration Damping Mount Strategies

---

Vibration damping strategies play a crucial role in improving the operational performance of omnidirectional robots because vibration generated at the wheels propagates through nearly every mechanical subsystem. Rather than attempting to eliminate vibration entirely, engineers seek to interrupt its transmission path before sensitive components experience significant excitation.

One common strategy involves vibration-isolated equipment mounting. Cameras, LiDAR sensors, inertial measurement units, onboard computers, and precision inspection devices are frequently installed using elastomeric isolation mounts, rubber bushings, silicone dampers, or viscoelastic materials. These compliant interfaces reduce high-frequency vibration while maintaining adequate structural stiffness for accurate sensing.

Motor mounting also contributes to vibration control. Although drive motors require rigid mechanical alignment for accurate torque transmission, carefully designed mounting interfaces can incorporate localized damping materials that reduce structural resonance without compromising drivetrain stiffness. Similar approaches are applied to gearbox mounting and wheel module interfaces.

Payload isolation becomes increasingly important when robots transport sensitive products such as semiconductor wafers, medical equipment, optical instruments, or precision electronic assemblies. Multi-stage isolation systems combine compliant mounts, floating payload platforms, and lightweight structural optimization to minimize transmitted acceleration while preserving positioning accuracy.

Frame design significantly influences damping effectiveness. High structural stiffness raises natural frequencies above dominant excitation frequencies, reducing resonance risk. Conversely, strategic damping layers incorporated within composite panels or sandwich structures dissipate vibrational energy before it propagates throughout the chassis.

Passive suspension systems provide another important vibration reduction mechanism. Spring-loaded wheel modules maintain continuous ground contact while absorbing floor irregularities and roller impacts. Proper selection of spring stiffness and damping characteristics prevents excessive oscillation while maintaining stable wheel loading.

Control algorithms increasingly contribute to vibration suppression. Smooth acceleration profiles, jerk-limited trajectory planning, wheel torque optimization, and adaptive velocity control reduce sudden force changes that excite structural vibration. Modern motor controllers further minimize torque ripple through advanced current regulation techniques.

Experimental validation remains essential because real robotic systems exhibit complex structural interactions difficult to predict analytically. Accelerometers, laser vibrometers, modal testing, and operational vibration measurements help identify dominant vibration paths and evaluate damping effectiveness. Combining mechanical isolation with intelligent control strategies provides the most effective solution for reducing vibration across diverse industrial applications.

### 5.3 Noise Profile Comparison: Omni vs Mecanum

---

Although omni wheels and Mecanum wheels share similar operating principles, their acoustic characteristics differ because of variations in roller orientation, contact mechanics, structural geometry, and force transmission. Understanding these differences helps engineers select appropriate wheel systems according to application-specific noise requirements.

Omni wheels generally produce lower overall noise during straight-line motion because their rollers rotate freely around axes oriented perpendicular to the primary rolling direction. Contact transitions remain relatively simple, and roller engagement with the floor produces comparatively smooth force variation under ideal operating conditions.

Mecanum wheels generate more complex contact patterns because each roller is mounted at approximately forty-five degrees relative to the wheel plane. During vehicle motion, longitudinal and lateral force components combine continuously within each roller. This multidirectional force transmission often increases micro-sliding between rollers and the floor, producing additional vibration and higher acoustic emissions compared with conventional omni wheels.

Operating speed strongly influences both wheel types. At low speeds, individual roller impacts may be distinguishable as repetitive clicking sounds. As speed increases, these impacts merge into broadband rolling noise dominated by higher-frequency structural vibration. Resonance within wheel hubs, frame members, or payload structures may further amplify specific frequency bands.

Floor material significantly affects acoustic performance. Hard epoxy, polished concrete, ceramic tile, and steel surfaces efficiently transmit impact energy, increasing perceived noise. Softer flooring materials absorb some contact energy, reducing both vibration and acoustic radiation. Roller material similarly influences sound generation, with polyurethane generally producing quieter operation than rigid nylon because of its greater energy absorption.

Payload weight modifies noise characteristics as well. Increased loading raises contact forces between rollers and the floor, potentially increasing impact intensity. However, additional vehicle mass may also reduce high-frequency chassis vibration by altering structural dynamics. The combined effect depends on wheel design, suspension characteristics, and overall vehicle architecture.

Noise measurements typically employ standardized sound pressure level testing together with frequency spectrum analysis. Engineers evaluate overall sound pressure, tonal components, transient impulses, and frequency distribution under representative operating conditions. These measurements support regulatory compliance while identifying opportunities for mechanical optimization.

From an application perspective, omni wheels are often preferred in hospitals, laboratories, cleanrooms, office environments, and collaborative workspaces where quiet operation is highly valued. Mecanum wheels remain widely used in industrial logistics, heavy material handling, and mobile manipulation where superior multidirectional force transmission outweighs moderate increases in acoustic emissions.

Ultimately, both wheel architectures can achieve excellent acoustic performance through optimized roller geometry, high-quality bearings, compliant suspension, precise manufacturing, and advanced motion control. Careful integration of these design elements enables modern omnidirectional robots to combine exceptional maneuverability with low vibration and acceptable operating noise across a broad range of industrial environments.

### 5.1 롤러 접촉 다각형 효과와 진동 (Roller Contact Polygon Effect and Vibration)

---

### 5.2 진동 감쇠 마운트 전략 (Vibration Damping Mount Strategies)

---

### 5.3 소음 특성 비교 : 옴니 휠과 메카넘 휠 (Noise Profile Comparison: Omni vs Mecanum)
