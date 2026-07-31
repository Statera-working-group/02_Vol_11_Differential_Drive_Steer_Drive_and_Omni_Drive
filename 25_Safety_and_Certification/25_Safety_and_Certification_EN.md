**Differential Drive & Steer Drive Engineering**

# Chapter 25 Safety & Certification

## 01 Industrial AMR safety standards

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 ISO 3691-4: Automated Industrial Truck Safety Requirements

---

The rapid deployment of Autonomous Mobile Robots (AMRs) in manufacturing, warehousing, logistics, and semiconductor industries has significantly increased the importance of internationally recognized safety standards. Unlike traditional industrial machinery that operates inside fenced work areas, AMRs share their workspace with pedestrians, forklifts, manually operated vehicles, and other autonomous systems. Consequently, safety can no longer rely solely on physical barriers. Instead, the vehicle itself must continuously detect hazards, evaluate risk, and execute protective actions while maintaining productive operation. Among the international standards addressing these requirements, ISO 3691-4 has become one of the most influential standards governing the safety of driverless industrial trucks and autonomous mobile robots operating in industrial environments.

ISO 3691-4 defines safety requirements for the design, integration, operation, verification, and maintenance of driverless industrial trucks and their associated systems. Rather than focusing exclusively on individual hardware components, the standard adopts a complete system perspective. Mechanical design, electrical architecture, sensing systems, software behavior, communication, charging operations, maintenance procedures, and operational environments are all considered together to ensure overall vehicle safety.

A fundamental principle of ISO 3691-4 is risk reduction through systematic engineering. Every AMR should undergo a comprehensive hazard identification process before deployment. Potential hazards include collisions with pedestrians, interactions with forklifts, uncontrolled vehicle movement, excessive speed, braking failures, charging hazards, communication failures, navigation errors, payload instability, and unexpected environmental changes. Each identified hazard is evaluated according to severity, probability of occurrence, and the possibility of human avoidance. Protective measures are then implemented until residual risk reaches an acceptable level.

Environmental perception represents one of the core safety functions required under the standard. Safety laser scanners, LiDAR systems, cameras, ultrasonic sensors, bumpers, and proximity sensors collectively monitor the vehicle\'s surroundings. Protective fields dynamically change according to travel direction, vehicle speed, payload characteristics, and operating mode. Warning zones initiate controlled speed reduction, while intrusion into protective zones immediately activates emergency stopping. This adaptive protective field concept allows productivity to remain high without compromising operator safety.

Vehicle speed management receives particular attention within ISO 3691-4. Maximum speed should not remain constant under all operating conditions. Instead, speed must adapt according to available visibility, turning radius, pedestrian density, environmental complexity, payload weight, and braking capability. Intelligent speed limitation significantly reduces collision severity while improving overall operational safety.

Emergency stopping requirements are similarly comprehensive. Multiple emergency stop devices should remain accessible and immediately remove hazardous motion whenever activated. Safe stopping behavior must remain predictable regardless of software state, communication condition, or operating mode. Braking performance, stopping distance, and response time should be validated under representative operating conditions including maximum payload and worst-case environmental scenarios.

Autonomous navigation functions must also satisfy strict reliability requirements. Localization algorithms, obstacle detection, route planning, and traffic management should demonstrate stable operation despite environmental variation. Loss of localization confidence, sensor failure, communication interruption, or inconsistent positioning should automatically initiate predefined safe operating behavior rather than allowing continued autonomous motion under uncertain conditions.

Verification plays an essential role throughout compliance assessment. Laboratory testing alone is insufficient. Vehicle behavior must be evaluated within representative industrial environments containing pedestrians, production equipment, varying floor conditions, intersections, charging stations, and typical logistics traffic. Documentation of design assumptions, safety analyses, validation procedures, maintenance requirements, and operational limitations forms an important component of compliance.

ISO 3691-4 therefore establishes a comprehensive safety framework extending beyond mechanical protection alone. By integrating hazard analysis, adaptive sensing, intelligent motion control, operational procedures, and systematic validation, the standard enables AMRs to operate safely alongside human workers while maintaining the productivity demanded by modern industrial automation.

### 1.2 IEC 62061: Machinery Safety and Safety Integrity Level (SIL)

---

Modern industrial automation increasingly depends upon programmable electronic control systems responsible for preventing hazardous machine behavior. As robots, autonomous vehicles, collaborative equipment, and intelligent manufacturing systems become more software intensive, the reliability of safety-related control systems becomes critically important. IEC 62061 provides an internationally recognized framework for designing, implementing, validating, and maintaining safety-related electrical, electronic, and programmable electronic control systems for machinery. Within industrial AMRs, this standard plays a central role in ensuring that safety functions achieve predictable and quantifiable performance throughout the operational lifetime of the vehicle.

A fundamental concept within IEC 62061 is the Safety Integrity Level, commonly referred to as SIL. Rather than describing general product quality, SIL represents the probability that a safety function will successfully perform its intended protective action whenever required. Higher SIL levels correspond to lower probabilities of dangerous failure and therefore provide greater risk reduction. The standard defines four Safety Integrity Levels, ranging from SIL1 through SIL4, although industrial mobile robots typically implement safety functions achieving SIL2 or SIL3 depending upon application risk assessment.

Risk assessment forms the starting point for SIL determination. Engineers first identify hazardous situations associated with vehicle motion, steering, braking, charging, maintenance, human interaction, communication failure, software malfunction, or sensor degradation. Each hazard is evaluated according to severity of potential injury, frequency of exposure, duration of hazardous conditions, and possibility of avoiding harm. The required SIL level is then selected according to the amount of risk reduction necessary for acceptable operation.

Safety functions within an AMR frequently include Safe Torque Off, Safe Stop, Safe Speed Monitoring, Safe Direction Monitoring, emergency stop processing, obstacle detection supervision, charging safety, and protective field switching. Each safety function is developed independently according to the required SIL target while maintaining traceability throughout design, implementation, testing, and validation.

Hardware architecture significantly influences SIL achievement. Redundant sensors, independent processing channels, cross-checking algorithms, fault detection mechanisms, diagnostic monitoring, and fail-safe output stages improve fault tolerance while reducing the probability of dangerous failure. However, redundancy alone does not guarantee compliance. Systematic design methodology, controlled component selection, documented engineering procedures, and comprehensive verification are equally important.

Software development under IEC 62061 follows rigorous lifecycle management. Requirements specification, software architecture, detailed design, implementation, code review, testing, verification, configuration management, and change control are all formally documented. Traceability between hazards, safety requirements, software implementation, and validation evidence ensures that every safety objective remains verifiable throughout development.

Diagnostic coverage represents another important concept. Safety systems continuously monitor sensor operation, communication quality, processor execution, memory integrity, actuator behavior, encoder feedback, and electrical outputs. Internal diagnostics detect many faults before they develop into hazardous failures, allowing controlled transition toward predefined safe states whenever abnormal conditions occur.

Validation extends beyond functional testing. Complete safety functions must demonstrate compliance under representative operating conditions, including simulated faults, communication interruption, power variation, environmental stress, sensor degradation, and hardware failure. Objective evidence generated during validation supports certification while providing confidence that safety performance remains consistent throughout real industrial operation.

For AMR developers, IEC 62061 encourages systematic engineering rather than reactive problem solving. Safety becomes an integral design objective established during the earliest project phases instead of being added after mechanical and software development has already been completed. This approach reduces redesign effort while improving long-term product reliability.

Ultimately, IEC 62061 provides the engineering methodology required to transform functional safety from theoretical analysis into practical industrial implementation. By combining rigorous risk assessment, structured hardware and software development, diagnostic monitoring, quantitative reliability evaluation, and comprehensive validation, the standard enables industrial AMRs to achieve predictable and internationally recognized safety performance suitable for demanding autonomous applications.

### 1.3 ISO 13849-1: Performance Level (PL)

Functional safety within industrial machinery may be evaluated using different international methodologies depending upon system architecture and application characteristics. While IEC 62061 introduces the Safety Integrity Level approach, ISO 13849-1 establishes an alternative framework based upon Performance Level, commonly abbreviated as PL. Because many industrial AMR components---including emergency stop circuits, safety laser scanners, protective doors, enabling devices, braking systems, and motion control functions---are certified according to ISO 13849-1, understanding Performance Level is essential for designing compliant autonomous mobile robots.

ISO 13849-1 addresses safety-related parts of machine control systems regardless of implementation technology. Mechanical components, hydraulic systems, pneumatic devices, electrical hardware, programmable electronics, and integrated safety controllers may all contribute toward achieving the required Performance Level. Rather than evaluating software reliability alone, the standard considers the complete safety function from sensor input through logic processing to final actuator response.

Performance Levels range from PLa through PLe, where PLa represents the lowest safety capability and PLe provides the highest probability of successful protective action. Selection of the required Performance Level begins with risk assessment. Hazards are evaluated according to injury severity, frequency of exposure, and possibility of avoiding dangerous situations. The resulting risk graph identifies the minimum Performance Level necessary for each safety function.

Several key parameters determine the achieved Performance Level. Category describes the structural architecture of the safety function, ranging from simple single-channel systems to highly fault-tolerant redundant architectures. Mean Time To Dangerous Failure evaluates expected component reliability throughout operational life. Diagnostic Coverage measures the effectiveness of fault detection mechanisms. Common Cause Failure analysis evaluates the likelihood that redundant channels could fail simultaneously because of shared design weaknesses or environmental influences. Together, these factors determine the final achievable Performance Level.

Within industrial AMRs, many safety functions target PLd or PLe depending upon application risk. Safety laser scanners continuously monitor protective fields surrounding the vehicle. Emergency stop circuits immediately remove propulsion torque whenever hazardous conditions arise. Safe braking functions prevent uncontrolled vehicle movement following communication failure. Encoder monitoring compares independent position measurements to detect abnormal wheel behavior. Each function may achieve different Performance Levels according to its contribution toward overall system safety.

Integration of certified safety components substantially simplifies compliance. Servo drives supporting Safe Torque Off, safety controllers certified to PLd or PLe, emergency stop devices, light curtains, and safety laser scanners may all be combined into validated safety architectures. However, overall system Performance Level depends upon the complete safety function rather than individual certified components alone.

Verification requires detailed engineering documentation. Safety block diagrams, reliability calculations, component specifications, diagnostic strategies, fault analyses, and validation procedures demonstrate that the implemented safety architecture satisfies the required Performance Level. Software tools supporting ISO 13849 calculations assist engineers in evaluating architecture performance during system development.

Maintenance also influences long-term safety. Periodic inspection, diagnostic testing, calibration, replacement intervals, and software management ensure that achieved Performance Level remains valid throughout the operational lifetime of the machinery. Predictive maintenance supported by continuous diagnostic monitoring further improves long-term reliability while reducing unexpected downtime.

Industrial AMRs frequently combine ISO 13849-1 and IEC 62061 because different subsystems may follow different certification methodologies. Modern safety controllers, servo drives, laser scanners, and integrated safety modules often support both PL and SIL certification, providing system integrators with greater flexibility during safety architecture development.

Ultimately, ISO 13849-1 provides a practical engineering framework for designing, verifying, and maintaining machine safety control systems. Through structured risk assessment, quantified reliability analysis, architectural evaluation, diagnostic monitoring, and systematic validation, Performance Level methodology enables industrial AMRs to achieve consistent and internationally accepted functional safety suitable for collaborative operation within complex industrial environments.

### 1.1 ISO 3691-4: 무인 산업용 차량 안전 요구사항 (ISO 3691-4: Automated Industrial Truck Safety Requirements)

---

### 1.2 IEC 62061: 기계 안전과 안전 무결성 수준 (IEC 62061: Machinery Safety and Safety Integrity Level, SIL)

---

### 1.3 ISO 13849-1: 성능 수준 (ISO 13849-1: Performance Level, PL)

## 02 Safety functions

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 STO (Safe Torque Off)

---

Safe Torque Off (STO) is the most fundamental functional safety function implemented in modern industrial servo drives and Autonomous Mobile Robots (AMRs). Its primary objective is to immediately eliminate motor torque whenever a hazardous situation is detected, preventing any further powered motion while maintaining the integrity of the overall control system. Unlike conventional emergency stop methods that simply disconnect electrical power, STO removes the ability of the inverter to energize the motor phases while allowing diagnostic electronics, communication networks, safety controllers, and monitoring functions to remain operational. This distinction enables engineers to investigate faults, collect diagnostic information, and safely recover system operation without requiring a complete power restart.

Within industrial AMRs, STO is typically activated when emergency stop buttons are pressed, protective safety fields are violated, safety laser scanners detect pedestrians inside dangerous zones, communication with certified safety controllers is interrupted, or serious hardware faults are identified. The safety controller continuously supervises multiple safety inputs and evaluates whether hazardous motion should be terminated. Once the safety logic determines that continued movement is unsafe, STO commands are transmitted to every propulsion and steering drive simultaneously.

The internal implementation of STO is considerably more sophisticated than a simple electrical disconnect. Modern servo drives contain redundant safety channels that independently disable gate signals controlling the inverter power transistors. Since the switching devices responsible for motor current generation can no longer operate, electromagnetic torque cannot be produced regardless of software state or external motion commands. This architecture significantly reduces the probability that software defects or communication failures could unintentionally restart motor motion.

For mobile robots equipped with multiple steer-drive modules, STO must operate synchronously across every drive axis. Heavy industrial AMRs frequently employ four propulsion motors together with four steering motors. If only selected drives were disabled while others continued producing torque, uncontrolled vehicle behavior could occur. Therefore, distributed safety communication technologies such as Functional Safety over EtherCAT (FSoE) coordinate simultaneous STO activation across all motion axes with deterministic timing.

STO should not be confused with mechanical braking. Removing motor torque alone does not necessarily stop vehicle movement immediately, particularly when transporting heavy payloads possessing significant inertia. Consequently, many industrial systems combine STO with braking systems or Safe Stop functions that first reduce kinetic energy before torque removal occurs. Engineers must therefore carefully evaluate vehicle mass, payload characteristics, stopping distance, and operating environment when selecting appropriate safety strategies.

Functional safety standards including IEC 61800-5-2 define STO as one of the core drive-integrated safety functions. Certification typically requires redundant internal hardware, continuous diagnostic monitoring, fault detection capability, and systematic design methodology satisfying internationally recognized functional safety requirements. Many industrial servo manufacturers therefore provide certified STO functionality as standard equipment, significantly simplifying system integration.

Diagnostic capability remains another major advantage. Because communication electronics remain energized following STO activation, engineers retain access to fault logs, encoder status, communication diagnostics, battery condition, and network health. Maintenance personnel can therefore identify root causes before restoring operation, improving system availability while reducing maintenance time.

Cybersecurity considerations increasingly influence STO implementation as industrial robots become network connected. Unauthorized software access should never possess the capability to disable safety functions or override STO commands. Certified safety communication protocols maintain logical separation between ordinary operational commands and safety-critical control information, ensuring that cybersecurity incidents cannot easily compromise protective behavior.

Testing and validation form essential elements of STO deployment. Functional verification includes emergency stop activation, protective field intrusion, communication interruption, simulated drive faults, redundant channel verification, recovery procedures, and restart authorization. Validation should occur under representative operating conditions including maximum payload, varying floor friction, multiple travel speeds, and realistic industrial traffic scenarios.

Ultimately, STO represents the foundation upon which higher-level functional safety architectures are constructed. By guaranteeing immediate elimination of hazardous motor torque through certified hardware mechanisms independent of application software, STO provides industrial AMRs with a reliable final protective layer supporting safe human-robot collaboration throughout demanding industrial environments.

### 2.2 SS1 (Safe Stop 1)

---

Safe Stop 1 (SS1) extends the concept of functional safety beyond immediate torque removal by introducing controlled deceleration before final motor shutdown. Whereas Safe Torque Off instantly eliminates motor torque regardless of current vehicle motion, SS1 first commands the drive system to execute a monitored braking sequence until vehicle speed reaches zero or an acceptable threshold. Only after successful deceleration does STO become active, permanently removing motor torque. This coordinated sequence significantly improves safety whenever uncontrolled emergency stopping could itself introduce additional hazards.

Industrial AMRs transporting heavy payloads frequently possess considerable kinetic energy. Abrupt torque removal without controlled deceleration may increase stopping distance, reduce vehicle stability, shift transported cargo, or create unexpected mechanical stress within drivetrain components. SS1 therefore becomes particularly valuable for heavy logistics robots, automotive manufacturing vehicles, semiconductor transportation systems, and autonomous inspection platforms operating with high-value or fragile payloads.

The SS1 process begins when a safety-related event is detected. Examples include intrusion into protective safety fields, emergency stop activation, communication faults within safety controllers, excessive vehicle speed, navigation uncertainty, or detection of abnormal mechanical behavior. Rather than disabling motor torque immediately, the safety controller commands predefined deceleration profiles according to application-specific requirements.

Servo drives continuously monitor actual vehicle deceleration throughout the braking sequence. Encoder feedback verifies that wheel velocity decreases according to expected behavior. If measured deceleration remains within acceptable limits, braking continues until complete standstill is achieved. At that point STO safely removes remaining motor torque, preventing any possibility of unintended restart. Should deceleration fail because of mechanical faults, braking problems, or drive malfunction, STO activates immediately to guarantee the highest achievable level of protection.

Multiple SS1 implementation strategies exist depending upon application requirements. Time-monitored SS1 verifies that vehicle reaches standstill within predetermined stopping time. Velocity-monitored SS1 continuously supervises wheel speed throughout the deceleration process. Position-monitored implementations additionally verify stopping distance whenever precise motion limitation becomes important. Engineers select appropriate monitoring methods according to hazard analysis and required functional safety level.

Heavy industrial AMRs particularly benefit from controlled deceleration because payload stability directly influences overall operational safety. Battery modules, semiconductor carriers, optical inspection equipment, precision measurement devices, medical supplies, and automotive components may all suffer damage if subjected to excessive braking forces. Smooth deceleration profiles therefore protect both transported products and vehicle mechanical systems while maintaining safe interaction with nearby personnel.

Integration with regenerative braking further improves system performance. During controlled deceleration, propulsion motors may temporarily operate as generators, converting vehicle kinetic energy back into electrical energy stored within batteries or dissipated through braking resistors. Coordinated regenerative braking improves energy efficiency while reducing mechanical brake wear throughout long-term industrial operation.

Communication reliability becomes critically important during SS1 execution. Functional safety communication networks such as FSoE continuously exchange braking commands, velocity feedback, diagnostic information, and safety status between vehicle controllers and distributed servo drives. Deterministic communication timing ensures synchronized braking across multiple drive modules, preventing undesirable yaw motion or vehicle instability during emergency deceleration.

Mechanical braking systems frequently complement electronic deceleration. After vehicle speed reaches zero, spring-applied holding brakes secure stationary positioning even if external forces attempt to move the robot. This combination proves particularly important on inclined surfaces, loading ramps, or applications involving heavy payloads where gravitational forces remain significant after propulsion torque disappears.

Verification procedures evaluate numerous operating scenarios including maximum payload, varying floor friction, degraded battery voltage, communication delay, partial drive failure, emergency stop activation during maximum speed, and simultaneous steering maneuvers. Successful validation demonstrates that stopping performance remains predictable despite environmental variation.

Ultimately, SS1 provides an intelligent compromise between productivity and safety. Rather than treating every hazardous condition identically, controlled deceleration preserves vehicle stability, protects transported equipment, minimizes mechanical stress, and still guarantees complete elimination of hazardous motion through subsequent STO activation. Consequently, SS1 has become one of the most widely implemented safety functions within modern industrial mobile robotics.

### 2.3 SS2 (Safe Stop 2)

---

Safe Stop 2 (SS2) provides another important functional safety strategy for industrial motion control, differing fundamentally from Safe Stop 1 in its treatment of motor torque following vehicle standstill. Similar to SS1, SS2 begins with monitored controlled deceleration whenever hazardous conditions are detected. However, instead of activating Safe Torque Off after stopping, servo control remains energized while actively maintaining precise position through closed-loop motor control. Hazardous motion is prevented without sacrificing positioning accuracy or control authority.

This characteristic makes SS2 particularly valuable whenever maintaining exact mechanical position is essential. Many industrial AMRs integrate robotic manipulators, vision inspection systems, precision docking mechanisms, lifting devices, or automated loading interfaces requiring continuous servo holding capability. Immediately removing motor torque following stopping could allow slight mechanical displacement caused by gravity, external forces, payload imbalance, or drivetrain elasticity. SS2 prevents such unwanted movement by maintaining active position regulation after controlled stopping.

Within precision inspection robots, repeatable positioning directly influences measurement quality. High-resolution cameras, laser scanners, structured light sensors, or metrology equipment frequently require millimeter-level repeatability throughout inspection processes lasting several minutes. Servo position holding enabled by SS2 ensures that measurement geometry remains stable despite external disturbances, improving inspection accuracy without compromising functional safety.

Industrial docking applications similarly benefit from maintained servo control. AMRs performing automatic charging, pallet transfer, conveyor interface alignment, or robotic loading often require continuous positioning force while connected to external equipment. If motor torque were completely removed, docking accuracy could degrade due to mechanical compliance or external loading. SS2 preserves controlled positioning throughout these interactions.

Implementation of SS2 requires continuous supervision of servo controller health, encoder feedback, communication integrity, and position error. Safety controllers verify that commanded holding position remains stable within predefined tolerance limits. Unexpected displacement, excessive position deviation, encoder disagreement, or communication failure immediately initiates additional protective actions according to system safety architecture.

Safe Operating Stop (SOS) frequently follows SS2 in many industrial implementations. Once controlled stopping is complete, servo drives actively maintain stationary position while continuously monitoring whether any hazardous motion occurs. Position monitoring remains safety certified, ensuring that unexpected movement immediately triggers higher-level protective functions if necessary.

Energy consumption differs significantly between SS1 and SS2. Because servo amplifiers remain energized throughout stationary holding, electrical power continues supporting position regulation. However, for applications requiring high precision, this additional energy consumption is generally justified by improved positioning performance and reduced mechanical drift.

Mechanical design also influences SS2 effectiveness. High-backlash gearboxes, flexible drivetrain components, or poorly balanced payloads may require increased servo holding torque to maintain stationary position. Engineers therefore evaluate drivetrain stiffness, mechanical compliance, payload characteristics, and disturbance forces during system design to ensure stable long-term position control.

Communication architecture remains critical because distributed servo drives must continue exchanging encoder feedback, current references, diagnostic information, and safety status throughout stationary operation. Functional safety communication protocols ensure deterministic monitoring despite ongoing network activity.

Validation procedures examine position holding accuracy under varying payload conditions, external disturbances, communication interruptions, encoder faults, and power fluctuations. Long-duration holding tests evaluate thermal behavior, servo stability, and diagnostic reliability while confirming that hazardous motion remains prevented throughout stationary operation.

Ultimately, SS2 extends functional safety beyond merely stopping hazardous motion. By combining controlled deceleration with continuously supervised closed-loop position regulation, it enables industrial AMRs to remain safely stationary while preserving precise positioning required for sophisticated industrial automation tasks involving inspection, manipulation, docking, and collaborative manufacturing.

### 2.4 SLS (Safely Limited Speed)

---

Safely Limited Speed (SLS) is a certified functional safety function designed to ensure that machine or vehicle speed never exceeds predefined safety limits during specific operating conditions. Unlike emergency stopping functions that react after hazardous situations develop, SLS allows productive operation to continue while actively restricting motion within safe velocity boundaries. This capability has become increasingly important for industrial AMRs operating near human workers, collaborative robots, maintenance personnel, and sensitive production equipment.

Many industrial activities require robot motion while people remain nearby. Examples include maintenance procedures, manual loading assistance, collaborative assembly, quality inspection, teaching operations, commissioning, and system diagnostics. Completely stopping robot motion during every human interaction would significantly reduce productivity. SLS instead enables controlled low-speed operation where residual risk remains acceptably low.

Implementation begins by defining application-specific speed thresholds through hazard analysis. Maximum allowable speed depends upon payload mass, vehicle dimensions, stopping distance, environmental complexity, pedestrian density, and potential injury severity. Certified safety controllers continuously compare actual wheel velocity measured by redundant encoders against permitted limits. Any attempt to exceed predefined speed thresholds immediately activates additional protective safety functions.

Encoder redundancy plays a critical role in SLS reliability. Independent measurement channels verify actual wheel speed using separate sensing principles or redundant encoder systems. Continuous cross-checking detects sensor disagreement, wiring faults, signal degradation, or electronic failures before hazardous overspeed conditions develop. Diagnostic coverage therefore contributes directly toward required functional safety certification.

Dynamic speed limitation significantly enhances operational flexibility. Rather than maintaining one fixed speed limit, AMRs may automatically adjust permissible velocity according to protective field size, vehicle direction, payload condition, environmental risk, or operational mode. Wide open factory aisles permit higher speeds, whereas narrow corridors, intersections, charging stations, or collaborative workspaces require substantially lower velocity limits.

Integration with perception systems further improves SLS performance. Safety laser scanners, LiDAR sensors, cameras, and artificial intelligence continuously evaluate surrounding conditions. Increasing pedestrian density or unexpected obstacle detection may automatically reduce allowable speed before hazardous situations develop. Predictive speed adaptation therefore improves both productivity and operational safety.

Drive controllers execute speed limitation through closed-loop motion regulation rather than abrupt torque interruption. Acceleration commands are modified to prevent overspeed while preserving smooth vehicle motion. Passengers, fragile payloads, optical inspection systems, and precision instruments therefore experience reduced vibration compared with emergency stopping strategies.

Fleet management systems may additionally coordinate SLS across multiple robots. Congested traffic zones, shared intersections, narrow passages, and collaborative work areas automatically enforce lower speed profiles for every vehicle entering defined regions. Centralized traffic management thereby improves both efficiency and safety across large industrial facilities.

Verification procedures include overspeed simulation, encoder fault injection, communication interruption, varying payload conditions, floor friction changes, and transition between multiple operational modes. Engineers validate that actual vehicle speed never exceeds certified safety limits despite hardware faults or environmental variation.

Ultimately, SLS demonstrates that functional safety need not reduce productivity unnecessarily. By continuously supervising and limiting motion within carefully defined velocity boundaries, industrial AMRs achieve safe collaboration with human workers while maintaining efficient autonomous operation across diverse industrial environments.

### 2.5 SBC (Safe Brake Control)

Safe Brake Control (SBC) is a functional safety function responsible for ensuring that mechanical braking systems operate reliably whenever hazardous motion must be prevented. While electronic safety functions such as STO remove motor torque, mechanical brakes remain essential whenever vehicles must resist external forces, maintain stationary position, operate on inclined surfaces, or securely hold heavy payloads after propulsion torque has been eliminated. SBC therefore forms a critical complement to other drive-integrated safety functions within industrial AMRs.

Modern industrial servo systems frequently employ spring-applied, electrically released holding brakes integrated directly into propulsion or steering motors. During normal operation electrical power releases the brake, allowing unrestricted motor rotation. Whenever hazardous conditions occur or electrical power disappears, spring force automatically engages the brake, mechanically preventing further shaft movement. SBC supervises this process to ensure braking occurs correctly under all operating conditions.

Brake control sequencing requires careful coordination with motion control. Applying mechanical brakes while motors continue producing significant torque may introduce excessive mechanical stress, gearbox damage, or unstable vehicle behavior. Conversely, removing motor torque before brake engagement may permit uncontrolled coasting. SBC therefore synchronizes propulsion control, regenerative braking, mechanical brake engagement, and diagnostic monitoring into carefully coordinated safety sequences.

Heavy industrial AMRs transporting one-ton or larger payloads particularly depend upon reliable mechanical braking. Vehicle inertia, gravitational loading, and external disturbances may continue generating motion even after propulsion torque disappears. Mechanical brakes therefore provide essential secondary protection, especially during emergency stopping, battery failure, communication interruption, maintenance activities, or parking on inclined surfaces.

Brake monitoring significantly improves diagnostic capability. Safety controllers supervise brake release confirmation, engagement timing, electrical current, actuator health, response delay, and position feedback whenever available. Unexpected brake behavior immediately generates diagnostic alarms while initiating predefined protective actions according to system safety architecture.

Steering modules may also incorporate dedicated holding brakes. Maintaining steering orientation after emergency stopping prevents unintended wheel rotation caused by external forces or uneven floor conditions. Stable steering geometry contributes to overall vehicle stability while simplifying controlled restart procedures after faults are resolved.

Automatic charging applications illustrate another important SBC use case. During charging, vehicles must remain securely positioned despite connector forces, cable tension, accidental contact, or floor vibration. Mechanical holding brakes maintain precise docking alignment while electrical charging proceeds safely. Similar positioning requirements exist for robotic loading stations, conveyor interfaces, precision inspection equipment, and lift mechanisms.

Integration with redundant safety communication ensures coordinated braking across multiple drive modules. Distributed servo drives receive synchronized brake commands through certified safety protocols while continuously reporting brake status to vehicle safety controllers. Simultaneous brake engagement prevents asymmetric stopping behavior that could otherwise destabilize large mobile platforms.

Maintenance considerations receive significant attention because brake performance gradually changes through mechanical wear. Diagnostic systems monitor brake operating cycles, response characteristics, engagement current, and holding capability to support predictive maintenance. Scheduled replacement based upon measured brake condition improves reliability while minimizing unexpected downtime.

Validation procedures examine emergency stopping under maximum payload, inclined surfaces, degraded battery voltage, communication failure, repeated braking cycles, thermal variation, and intentional brake faults. Engineers verify holding capability, stopping consistency, diagnostic effectiveness, and recovery procedures throughout representative industrial operating conditions.

Ultimately, SBC ensures that electronic functional safety is supported by equally reliable mechanical protection. By coordinating brake sequencing, monitoring brake health, supervising engagement performance, and maintaining secure stationary positioning, Safe Brake Control enables industrial AMRs to achieve dependable functional safety throughout transportation, docking, charging, maintenance, and collaborative operation.

### 2.1 STO (안전 토크 차단, Safe Torque Off)

---

### 2.2 SS1 (안전 정지 1, Safe Stop 1)

---

### 2.3 SS2 (안전 정지 2, Safe Stop 2)

---

### 2.4 SLS (안전 제한 속도, Safely Limited Speed)

---

### 2.5 SBC (안전 브레이크 제어, Safe Brake Control)

## 03 Safety architecture design

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Safety Controller Selection

---

The safety controller represents the central decision-making element of an industrial Autonomous Mobile Robot (AMR) functional safety system. While propulsion controllers, motion controllers, navigation computers, and artificial intelligence processors manage normal vehicle operation, the safety controller operates independently with the sole responsibility of reducing risk whenever hazardous conditions are detected. This separation between operational control and safety control is one of the fundamental principles of modern functional safety engineering. The safety controller continuously monitors safety devices, evaluates hazardous situations, and executes certified protective actions regardless of the operating state of the vehicle or the application software.

Selecting an appropriate safety controller requires considerably more than comparing processor performance or communication bandwidth. Engineers must first identify the functional safety requirements derived from hazard analysis and risk assessment. Required Safety Integrity Level (SIL) or Performance Level (PL), the number of safety inputs and outputs, communication interfaces, diagnostic capability, environmental specifications, redundancy architecture, and future expansion requirements all influence controller selection. A controller that satisfies current project requirements while providing sufficient scalability for future software upgrades and hardware expansion generally offers the most practical long-term engineering solution.

Industrial AMRs typically integrate numerous safety-related devices, including emergency stop switches, safety laser scanners, bumper sensors, encoder monitoring systems, safety door switches, brake feedback circuits, battery safety monitoring, steering diagnostics, and charging station interfaces. The safety controller must collect information from all of these devices in deterministic real time while executing certified safety logic with predictable response timing. Modern safety controllers therefore incorporate dedicated safety processors, redundant execution channels, continuous self-diagnostics, and certified operating systems designed specifically for safety-critical applications.

Communication capability has become increasingly important as industrial robots adopt distributed control architectures. Functional Safety over EtherCAT (FSoE), CIP Safety, PROFIsafe, and other certified safety communication protocols allow safety information to be transmitted over industrial Ethernet without requiring independent safety wiring. The safety controller therefore functions as the network coordinator, exchanging certified safety messages with servo drives, remote safety I/O modules, intelligent sensors, and safety-enabled motion controllers. This architecture simplifies electrical design while improving diagnostic visibility throughout the entire vehicle.

Processing performance is another consideration, although raw computational speed is rarely the dominant selection criterion. Safety algorithms generally consist of deterministic logic, voting mechanisms, redundancy verification, timing supervision, and fault monitoring rather than computationally intensive artificial intelligence. Reliability, predictable execution time, deterministic scheduling, and diagnostic coverage therefore take precedence over processing throughput.

Software development environments supplied by safety controller manufacturers significantly influence engineering productivity. Certified function blocks supporting emergency stop processing, protective field switching, Safe Torque Off (STO), Safe Stop functions, Safe Brake Control (SBC), speed supervision, encoder monitoring, and communication diagnostics reduce implementation effort while maintaining compliance with international safety standards. Graphical programming environments additionally simplify validation and long-term maintenance.

Cybersecurity has also become an important selection criterion. Although operational networks increasingly connect to enterprise systems and cloud services, safety functions must remain isolated from unauthorized modification. Modern safety controllers therefore implement secure boot mechanisms, authenticated firmware updates, protected configuration storage, access control, and logical separation between operational and safety communication.

Environmental robustness should match industrial deployment conditions. Temperature range, vibration tolerance, electromagnetic compatibility, ingress protection, and long-term component availability directly affect operational reliability. Heavy-duty industrial AMRs operating continuously within factories, logistics centers, or outdoor industrial environments require controllers capable of maintaining certified safety performance under demanding physical conditions.

Maintenance and lifecycle support represent additional practical considerations. Industrial automation equipment often remains in service for more than ten years. Long-term firmware support, spare part availability, engineering software compatibility, comprehensive documentation, diagnostic tools, and manufacturer technical assistance significantly influence lifecycle cost and system maintainability.

Ultimately, selecting a safety controller is a strategic engineering decision rather than a simple hardware procurement activity. The controller establishes the foundation upon which the entire functional safety architecture is built, coordinating sensing, communication, diagnostics, motion supervision, and protective actions into one certified safety system. A well-selected safety controller not only satisfies current regulatory requirements but also provides the flexibility, reliability, and scalability necessary for future generations of industrial autonomous mobile robots.

### 3.2 Safety LiDAR SIL2 Integration

---

Safety LiDAR has become one of the most essential sensing technologies for industrial Autonomous Mobile Robots operating within shared human-machine environments. Unlike conventional navigation LiDAR used primarily for localization and mapping, safety LiDAR performs certified protective functions that directly contribute to functional safety compliance. Integration of Safety Integrity Level 2 (SIL2) certified safety LiDAR enables an AMR to continuously monitor its surroundings, detect human presence, evaluate hazardous situations, and initiate protective actions before collisions occur. Proper integration therefore requires coordinated consideration of sensing technology, communication architecture, functional safety standards, vehicle dynamics, and system-level risk assessment.

The primary objective of safety LiDAR is not obstacle avoidance alone but certified risk reduction. Every measurement produced by the sensor contributes to determining whether continued vehicle motion remains safe. The safety controller continuously evaluates protective field status received from the LiDAR and compares it against current operating conditions, including travel direction, vehicle speed, payload characteristics, steering angle, and operational mode. Protective responses are then executed according to certified safety logic.

Protective fields generally consist of multiple concentric zones. The outer monitoring area functions as an information region where approaching objects are detected without immediately affecting vehicle behavior. The warning zone initiates speed reduction whenever pedestrians or obstacles approach predefined distances. The innermost protective field triggers emergency stopping through Safe Stop or Safe Torque Off functions whenever intrusion creates unacceptable collision risk. Dynamic protective field switching allows these zones to change automatically according to operating speed and travel direction, maximizing productivity while preserving safety.

SIL2-certified integration requires deterministic communication between safety LiDAR and the safety controller. Certified communication protocols such as FSoE or manufacturer-specific safety interfaces guarantee message integrity, timing supervision, sequence verification, and fault detection. Communication interruptions, corrupted messages, synchronization errors, or unexpected sensor behavior automatically generate safe system responses rather than allowing continued operation under uncertain conditions.

Sensor placement significantly influences detection performance. Safety LiDAR should provide complete coverage of expected travel paths while minimizing blind zones around the vehicle. Large industrial AMRs often employ multiple safety LiDAR units positioned at the front, rear, and corners to achieve nearly three hundred sixty-degree protection. Overlapping detection areas further improve redundancy while reducing vulnerability to environmental occlusion.

Environmental conditions present additional engineering challenges. Dust, smoke, reflective surfaces, sunlight, water droplets, and transparent materials may influence laser measurements. Certified safety LiDAR continuously performs internal diagnostics monitoring optical performance, scanning mechanisms, laser output, signal processing, and communication integrity. Any detected degradation immediately reports diagnostic information to the safety controller, allowing predefined protective actions before hazardous failures develop.

Integration with vehicle motion control improves operational efficiency. Instead of treating every detected object identically, intelligent safety systems combine LiDAR information with localization, vehicle velocity, steering angle, payload weight, and predicted trajectory. Adaptive protective field management therefore minimizes unnecessary emergency stops while maintaining certified safety performance. Production throughput consequently increases without compromising operator protection.

Validation extends well beyond laboratory testing. Engineers evaluate protective field accuracy, stopping distance, response time, detection reliability, communication robustness, and diagnostic performance under representative industrial conditions. Various pedestrian approaches, reflective objects, multiple moving obstacles, environmental disturbances, and maximum payload conditions should all be included within verification procedures.

Maintenance planning also supports long-term reliability. Periodic cleaning of optical windows, functional testing, calibration verification, firmware management, diagnostic review, and field validation ensure that certified performance remains consistent throughout operational life. Predictive maintenance based upon diagnostic trends can further reduce unexpected sensor failures.

Ultimately, SIL2 safety LiDAR integration transforms environmental perception into a certified functional safety subsystem rather than a conventional navigation sensor. Through deterministic communication, dynamic protective field management, continuous diagnostics, and coordinated interaction with the safety controller, safety LiDAR enables industrial AMRs to safely operate alongside human workers while maintaining efficient autonomous productivity.

### 3.3 Hardware Interlock Circuit Design

Hardware interlock circuits represent one of the most reliable layers within industrial functional safety architecture because their operation does not depend upon high-level software execution or artificial intelligence algorithms. Instead, dedicated electrical circuits directly supervise critical safety conditions and interrupt hazardous energy whenever predefined abnormal situations occur. Within industrial Autonomous Mobile Robots, hardware interlocks complement programmable safety controllers by providing deterministic electrical protection against failures that could otherwise result in uncontrolled vehicle motion or unsafe equipment behavior.

The fundamental philosophy of hardware interlock design is fail-safe operation. Electrical circuits are arranged so that loss of power, broken wiring, connector failure, damaged components, or unexpected electrical faults naturally drive the system toward a safe state rather than allowing hazardous motion to continue. Normally closed safety contacts therefore remain energized only during healthy operating conditions. Any interruption immediately opens the safety circuit, removing drive enable signals and initiating protective actions.

Emergency stop circuits form the most recognizable hardware interlock implementation. Multiple emergency stop switches distributed around the vehicle connect through redundant safety channels monitored continuously by the safety controller. Pressing any emergency stop immediately interrupts hardware enable signals supplied to propulsion drives, steering drives, and braking systems. Because hardware interruption occurs independently of application software, protective response remains reliable even if the primary control computer experiences software failure.

Drive enable circuits represent another essential interlock mechanism. Servo amplifiers require hardware permission signals before generating motor torque. Safety relays or certified semiconductor outputs controlled by the safety controller provide these enable signals only when every required safety condition has been satisfied. Loss of communication, encoder faults, safety LiDAR activation, battery abnormalities, charging interface engagement, or controller malfunction automatically remove drive enable status.

Brake interlocks coordinate mechanical holding systems with electronic motion control. Mechanical brakes should engage only after propulsion torque has decreased to safe levels while simultaneously preventing unintended vehicle movement following power loss. Hardware timing circuits, brake feedback monitoring, and redundant brake status signals verify successful brake engagement before allowing maintenance access or charging operations.

Battery safety also benefits from hardware interlocks. High-voltage contactors, pre-charge circuits, insulation monitoring devices, overcurrent protection, temperature monitoring, and emergency disconnect mechanisms collectively isolate electrical energy whenever battery faults, short circuits, thermal events, or maintenance conditions require safe shutdown. Independent hardware protection significantly reduces dependence upon software decision-making during rapidly developing electrical faults.

Charging stations frequently implement dedicated interlock circuits preventing vehicle motion while charging connectors remain engaged. Mechanical connector detection switches, charging contact feedback, isolation monitoring, and power relay supervision ensure propulsion systems cannot activate until charging has been safely completed and physical disconnection verified. Similar interlocks protect automated loading systems, robotic manipulators, maintenance access panels, and lifting mechanisms.

Redundancy considerably improves interlock reliability. Dual-channel circuits independently monitor critical safety signals while continuous cross-checking detects discrepancies between channels. Certified safety relays evaluate timing relationships, contact integrity, short circuits, and cross faults before permitting hazardous motion. Such architectures satisfy the diagnostic coverage required by modern functional safety standards.

Electrical design should also consider electromagnetic compatibility. Industrial environments contain large motors, inverters, welding equipment, radio transmitters, and switching power supplies capable of introducing electrical noise. Shielded wiring, galvanic isolation, surge protection, proper grounding, and careful cable routing improve immunity while preserving reliable safety signal transmission.

Verification includes continuity testing, fault injection, power interruption, short circuit simulation, timing measurement, relay endurance evaluation, connector failure analysis, and environmental stress testing. Engineers intentionally introduce representative hardware faults to confirm that interlock circuits consistently drive the vehicle toward safe operating conditions regardless of software state.

Ultimately, hardware interlock circuits provide the final independent protective barrier within industrial AMR safety architecture. By directly controlling hazardous energy through deterministic electrical mechanisms, they complement programmable safety controllers, reduce dependence upon software reliability, improve fault tolerance, and establish the robust multi-layered protection strategy required for safe autonomous operation in modern industrial environments.

### 3.1 안전 제어기 선정 (Safety Controller Selection)

---

### 3.2 SIL2 안전 LiDAR 통합 (Safety LiDAR SIL2 Integration)

---

### 3.3 하드웨어 인터록 회로 설계 (Hardware Interlock Circuit Design)

## 04 Risk assessment

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Risk Assessment Process According to ISO 12100

---

Risk assessment is the foundation of every industrial machine safety program and serves as the starting point for designing a safe Autonomous Mobile Robot (AMR). Rather than introducing protective devices after mechanical and electrical systems have already been completed, ISO 12100 promotes a systematic engineering methodology in which safety considerations are incorporated throughout the entire product development lifecycle. For industrial AMRs operating in shared human-machine environments, this proactive approach is particularly important because hazards arise not only from mechanical motion but also from autonomous decision-making, sensor limitations, software behavior, communication failures, and environmental uncertainty.

The ISO 12100 methodology begins by clearly defining the intended use of the machine. For a one-ton-class industrial AMR, engineers first identify the expected operating environment, including factory layouts, warehouse aisles, loading stations, charging areas, maintenance facilities, and pedestrian traffic zones. Vehicle specifications such as maximum speed, payload capacity, turning radius, battery system, steering architecture, and navigation technology are documented together with expected operating modes, including autonomous transportation, manual teaching, maintenance, charging, docking, and emergency recovery. Defining intended use also requires identifying reasonably foreseeable misuse, since operators may unintentionally use the system in ways that were not originally anticipated.

Once machine limits have been established, hazard identification begins. Engineers systematically evaluate every phase of the machine lifecycle, including transportation, installation, commissioning, calibration, normal operation, charging, software updates, maintenance, troubleshooting, and decommissioning. Mechanical hazards such as collision, crushing, shearing, trapping, and falling loads are considered alongside electrical hazards including battery faults, insulation failure, overcurrent, short circuits, and thermal runaway. Additional hazards arise from software malfunction, localization errors, communication interruption, unexpected obstacle behavior, environmental changes, cybersecurity attacks, and human operational mistakes.

Each identified hazard is then evaluated through formal risk estimation. ISO 12100 recommends considering three primary factors: the severity of possible injury, the frequency and duration of human exposure, and the probability that a hazardous event can be avoided. These parameters allow engineers to prioritize risks requiring immediate design attention. High-severity hazards involving frequent exposure and limited avoidance capability naturally demand stronger protective measures than low-risk situations.

Risk reduction follows a structured hierarchy. The first priority is inherently safe design, where hazards are eliminated through engineering decisions rather than protective equipment. Examples include reducing vehicle speed, lowering the center of gravity, increasing structural stability, selecting safer battery voltages, or designing rounded vehicle edges to minimize impact severity. If hazards cannot be completely eliminated, safeguarding measures such as safety LiDAR, emergency stop systems, protective field monitoring, functional safety controllers, hardware interlocks, and redundant communication channels are implemented. Administrative controls including operator training, maintenance procedures, warning labels, and operating manuals represent the final layer of protection after engineering measures have been exhausted.

Verification and validation complete the assessment process. Every implemented safety measure must demonstrate measurable effectiveness under representative operating conditions. Functional testing, fault injection, emergency stopping evaluation, protective field verification, charging safety tests, communication failure simulations, and long-duration operational testing collectively provide objective evidence that residual risk has been reduced to an acceptable level. Documentation generated throughout this process becomes an essential component of regulatory compliance and future product maintenance.

Risk assessment should not be viewed as a one-time activity performed only during initial development. Industrial AMRs continue evolving through software updates, hardware improvements, new payload configurations, and changing operational environments. Consequently, ISO 12100 encourages continuous review of risk whenever significant design modifications occur. Maintaining an up-to-date risk assessment ensures that safety architecture evolves together with product capability throughout the operational lifetime of the robot.

Ultimately, ISO 12100 transforms safety from a reactive inspection activity into a proactive engineering discipline. By systematically identifying hazards, estimating associated risks, implementing prioritized protective measures, and continuously validating their effectiveness, manufacturers create industrial AMRs capable of operating safely alongside human workers while maintaining high productivity and long-term reliability.

### 4.2 Hazard Scenario List for a One-Ton-Class AMR

---

Developing a one-ton-class Autonomous Mobile Robot introduces significantly greater safety challenges than smaller service robots because increased vehicle mass, higher kinetic energy, larger stopping distances, and heavier payloads substantially increase the consequences of hazardous events. Effective risk assessment therefore requires systematic identification of realistic hazard scenarios that may occur throughout the complete operational lifecycle. Rather than considering isolated component failures, engineers analyze interactions among mechanical systems, electrical equipment, software, sensors, communication networks, human operators, and environmental conditions.

Collision with pedestrians represents one of the highest-priority hazard scenarios. Human workers may unexpectedly enter the robot\'s travel path while carrying materials, pushing carts, or operating forklifts. Reduced visibility at intersections, blind corners, and production cells further increases collision probability. Safety LiDAR, dynamic protective fields, speed limitation, emergency stopping, and traffic management systems collectively reduce collision risk while maintaining operational efficiency.

Vehicle-to-vehicle interaction presents another important hazard. Industrial facilities increasingly deploy multiple AMRs operating simultaneously alongside manually driven forklifts, automated guided vehicles, and mobile manipulators. Communication failures, localization errors, or scheduling conflicts may create intersection collisions or congestion. Fleet management systems, priority rules, virtual traffic control, and redundant localization improve cooperative operation while minimizing collision probability.

Payload-related hazards require special attention. Improperly secured loads may shift during acceleration, braking, or turning, changing vehicle stability and increasing rollover risk. Excessive payload height may obstruct sensors or alter the center of gravity, while overloaded vehicles may exceed structural or braking capability. Continuous payload monitoring, stability analysis, weight verification, and acceleration limitation significantly reduce these risks.

Charging operations introduce both electrical and mechanical hazards. High-current charging connectors, battery thermal events, damaged cables, moisture, connector contamination, or improper docking alignment may create fire, electrical shock, or equipment damage. Charging stations therefore incorporate mechanical alignment guides, connector verification, insulation monitoring, battery communication, emergency disconnect circuits, and charging interlocks preventing vehicle motion while charging remains active.

Battery failures represent another major hazard category. Thermal runaway, overcharging, excessive discharge, internal short circuits, cooling failure, mechanical impact, and cell imbalance may all lead to hazardous battery conditions. Battery Management Systems continuously monitor voltage, current, temperature, insulation resistance, and State of Charge while automatically disconnecting battery power whenever unsafe operating conditions develop.

Navigation failures can also generate hazardous situations. Sensor degradation, temporary localization loss, reflective surfaces, environmental changes, damaged floor markings, wireless communication interruption, or software defects may reduce navigation accuracy. Safe operating modes should automatically reduce speed, increase sensing redundancy, or safely stop vehicle motion whenever localization confidence falls below predefined thresholds.

Mechanical failures include steering actuator malfunction, brake degradation, wheel damage, suspension failure, gearbox wear, encoder faults, and structural fatigue. Predictive maintenance supported by continuous diagnostic monitoring enables early fault detection before hazardous failures occur during normal production.

Human operational errors remain unavoidable despite advanced automation. Incorrect maintenance procedures, bypassing safety devices, improper software configuration, unauthorized parameter modification, inadequate operator training, or accidental emergency stop reset may all compromise system safety. Access control, configuration management, maintenance procedures, operator certification, and audit logging reduce these human-related risks.

Environmental hazards include slippery floors, uneven surfaces, unexpected obstacles, poor lighting, electromagnetic interference, smoke, dust, water, vibration, and temperature extremes. These factors influence sensor performance, braking distance, communication quality, and mechanical reliability. Comprehensive environmental testing and adaptive operational strategies improve robustness under varying industrial conditions.

The resulting hazard scenario list serves as the primary input for functional safety architecture development. Every identified scenario is linked to corresponding protective functions such as Safe Torque Off, Safe Stop, Safety LiDAR, Safe Brake Control, hardware interlocks, battery protection, communication supervision, and emergency recovery procedures. This traceability ensures that every significant hazard receives an appropriate engineering response.

Ultimately, hazard scenario analysis enables engineers to anticipate realistic operational risks before product deployment. Systematic identification, evaluation, and mitigation of these scenarios provide the foundation for achieving internationally recognized functional safety while supporting reliable operation of one-ton-class industrial AMRs within demanding manufacturing and logistics environments.

### 4.3 Charging Station Safety Design

Automatic charging stations represent one of the most safety-critical subsystems within industrial Autonomous Mobile Robot deployments because they combine high electrical power, autonomous vehicle motion, mechanical docking, battery management, and human interaction within a single operational process. A charging station must therefore be designed not only for charging efficiency but also for functional safety, electrical protection, mechanical reliability, and long-term maintainability. Safe charging architecture becomes particularly important for one-ton-class AMRs whose battery capacity and charging current are substantially greater than those of smaller mobile robots.

Safety begins with mechanical docking design. The charging station should include passive alignment features such as tapered guide rails, V-shaped positioning structures, centering cones, or funnel-shaped mechanical guides that compensate for small positioning errors during autonomous docking. These passive mechanisms reduce mechanical impact while minimizing stress on charging connectors. Precision docking sensors including LiDAR, vision systems, proximity sensors, or contact detection switches provide additional positioning verification before electrical connection is permitted.

Electrical safety requires multiple independent protection layers. Battery Management Systems communicate continuously with charging controllers using industrial communication protocols such as CAN or RS-485 to exchange battery voltage, current limits, temperature, State of Charge, State of Health, and charging permission. Charging begins only after successful communication verification, connector confirmation, insulation monitoring, and safety diagnostics have all completed successfully.

Pre-charge circuits play an important role in protecting electrical components. Before connecting the main battery to the charger, current flows through controlled pre-charge resistors to gradually equalize voltage across power capacitors. This process prevents damaging inrush current capable of reducing connector lifetime, damaging power electronics, or producing electrical arcing. Once voltage stabilization has been confirmed, the main contactors close automatically to initiate full charging.

Charging stations should incorporate multiple hardware interlocks preventing hazardous operation. Vehicle propulsion remains disabled while charging connectors are engaged. Charging cannot begin until successful docking has been confirmed. Connector release is prohibited while significant charging current remains present. Emergency stop activation immediately disconnects charging power while maintaining safe electrical isolation. Independent contactor feedback continuously verifies successful switching operations throughout the charging cycle.

Fire prevention represents another major design consideration. Temperature sensors positioned within battery packs, charging connectors, power electronics, and charging cables continuously monitor thermal conditions. Abnormal temperature rise automatically reduces charging current or terminates charging completely. Smoke detectors, thermal cameras, and fire suppression systems may provide additional protection within large industrial charging facilities operating multiple autonomous vehicles simultaneously.

Ground fault detection and insulation monitoring improve electrical safety throughout charging operations. Continuous measurement of insulation resistance identifies deteriorating cable insulation, connector contamination, moisture ingress, or unexpected leakage currents before hazardous electrical faults develop. Residual current monitoring further enhances protection for maintenance personnel and nearby operators.

Communication reliability directly influences charging safety. Loss of battery communication, inconsistent State of Charge information, abnormal voltage measurements, or unexpected charging behavior immediately interrupts charging while generating diagnostic information for maintenance personnel. Charging control software should never continue operation when battery condition becomes uncertain.

Functional safety verification includes repeated docking tests, connector endurance evaluation, communication interruption simulation, emergency stop validation, insulation fault testing, overtemperature protection, battery fault simulation, and power interruption recovery. Validation under representative industrial conditions demonstrates reliable long-term operation despite environmental variation, repeated charging cycles, and normal mechanical wear.

Future charging infrastructure may additionally support wireless charging technologies eliminating exposed electrical contacts. Although wireless systems reduce connector wear and simplify maintenance, they introduce new safety challenges including foreign object detection, electromagnetic field management, thermal supervision, alignment verification, and charging efficiency optimization. Many manufacturers therefore adopt a phased development strategy beginning with proven contact charging while preparing future migration toward wireless charging as technology matures.

Ultimately, charging station safety design integrates mechanical guidance, electrical protection, battery communication, functional safety, hardware interlocks, thermal monitoring, and intelligent diagnostics into a comprehensive safety architecture. Properly engineered charging stations not only maximize operational availability but also ensure safe autonomous energy replenishment throughout the complete lifecycle of industrial AMR deployments.

### 4.1 ISO 12100 기반 위험도 평가 절차 (Risk Assessment Process According to ISO 12100)

---

### 4.2 1톤급 AMR 위험 시나리오 목록 (Hazard Scenario List for a One-Ton-Class AMR)

---

### 4.3 충전 스테이션 안전 설계 (Charging Station Safety Design)

## 05 Certification process

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 CE Certification Procedure in Europe

---

The CE certification process represents one of the most important regulatory milestones for industrial Autonomous Mobile Robots (AMRs) intended for the European market. Unlike product quality certification, the CE marking primarily demonstrates that a manufacturer has verified compliance with all applicable European Union legislation related to safety, health, environmental protection, and electromagnetic compatibility. For a one-ton-class industrial AMR operating alongside human workers, CE certification provides legal authorization for product placement within the European Economic Area while demonstrating that systematic engineering processes have been followed to reduce risks to an acceptable level.

The certification process begins by identifying all applicable European Directives and Regulations. Depending on the final product configuration, an industrial AMR may fall under the Machinery Regulation, Electromagnetic Compatibility Directive, Radio Equipment Directive, Low Voltage Directive where applicable, Battery Regulation, and other product-specific legislation. Determining the correct legal framework is critical because every subsequent engineering activity, including design verification, documentation, testing, and conformity assessment, depends upon these regulatory requirements.

After identifying applicable legislation, engineers perform a comprehensive risk assessment according to ISO 12100. Every hazard associated with mechanical movement, electrical power, battery systems, software behavior, autonomous navigation, human interaction, charging operations, maintenance activities, and foreseeable misuse is systematically evaluated. The resulting hazard analysis becomes the foundation for defining functional safety requirements and selecting appropriate protective measures such as Safety LiDAR, emergency stopping systems, Safe Torque Off, hardware interlocks, redundant communication channels, and certified safety controllers.

Compliance with harmonized European standards significantly simplifies the conformity assessment process. Standards including ISO 3691-4 for industrial mobile robots, IEC 62061 for machinery functional safety, ISO 13849-1 for Performance Level design, IEC 60204-1 for electrical equipment, and IEC 61496 for electro-sensitive protective equipment provide recognized engineering methods for demonstrating regulatory compliance. Although using harmonized standards is not always mandatory, doing so provides a strong presumption of conformity during certification.

Prototype verification follows the design phase. Functional testing, electromagnetic compatibility testing, environmental testing, vibration testing, battery safety evaluation, braking performance measurement, emergency stopping validation, navigation accuracy verification, charging safety assessment, and long-duration endurance testing collectively demonstrate that the implemented safety architecture performs as intended under representative operating conditions. Any identified deficiencies must be corrected before the conformity assessment continues.

An essential component of CE certification is preparation of the Technical Documentation. This documentation includes system architecture descriptions, mechanical drawings, electrical schematics, software architecture, bill of materials, risk assessment reports, verification records, validation reports, functional safety analysis, test results, maintenance procedures, operating manuals, declaration of incorporated components, supplier certificates, and traceability information. Technical documentation must provide sufficient evidence that the product complies with all applicable legal requirements and should remain available for inspection by regulatory authorities for many years after product placement.

Following successful verification, the manufacturer prepares the EU Declaration of Conformity. This legally binding document identifies the product, applicable directives, harmonized standards, manufacturer information, authorized representative where applicable, and responsible engineering authority. By signing this declaration, the manufacturer formally accepts responsibility for regulatory compliance.

The CE mark is then permanently affixed to the product together with required product identification labels, serial numbers, manufacturer information, and warning markings. However, certification responsibilities do not end after product release. Manufacturers must maintain configuration management, document engineering changes, monitor field performance, investigate safety incidents, and update technical documentation whenever significant design modifications occur. Software updates affecting safety functions must also undergo appropriate verification before deployment.

For industrial AMRs incorporating advanced autonomous functions, cybersecurity considerations have become increasingly important. Secure software updates, access control, communication integrity, configuration protection, and software lifecycle management are now closely integrated with traditional machinery safety requirements. Consequently, successful CE certification increasingly depends upon cooperation among mechanical, electrical, software, functional safety, and cybersecurity engineering teams.

Ultimately, CE certification should be viewed not simply as a regulatory obligation but as a comprehensive engineering methodology that systematically demonstrates the safety, reliability, and legal compliance of industrial AMRs throughout their entire operational lifecycle.

### 5.2 KC Certification Procedure in Korea

---

KC certification represents the primary national conformity assessment framework for industrial equipment marketed within the Republic of Korea. Similar to European regulatory systems, the Korean certification process ensures that industrial Autonomous Mobile Robots satisfy national requirements related to electrical safety, electromagnetic compatibility, radio communication, battery systems, machinery safety, and human protection before commercial deployment. Although many engineering principles overlap with international standards, manufacturers must carefully understand Korean regulatory procedures and documentation requirements to achieve successful certification.

The certification process begins by determining the regulatory classification of the product. Industrial AMRs integrate multiple technologies including electrical power systems, wireless communication devices, industrial controllers, batteries, charging systems, sensors, and autonomous navigation computers. Each subsystem may be subject to different Korean technical regulations administered by separate authorities. Therefore, early regulatory planning prevents unnecessary redesign later in the development process.

Electrical safety verification represents one of the first engineering activities. Engineers evaluate insulation design, protective grounding, overcurrent protection, emergency disconnect mechanisms, battery protection circuits, thermal management, cable routing, enclosure integrity, and electrical fault tolerance. Battery charging systems, high-current connectors, DC power distribution, and isolation monitoring receive particular attention for heavy industrial AMRs because of the significant electrical energy involved during operation and charging.

Electromagnetic compatibility testing is another critical requirement. Industrial environments contain numerous sources of electromagnetic interference including variable-frequency motor drives, welding equipment, wireless communication systems, and high-power switching devices. AMRs must demonstrate both electromagnetic emission compliance and immunity to external disturbances. Stable operation during electromagnetic exposure ensures reliable navigation, communication, safety monitoring, and functional safety performance under realistic industrial conditions.

Wireless communication equipment integrated into the AMR requires radio conformity assessment according to Korean communication regulations. Wi-Fi, Bluetooth, LTE, 5G, industrial wireless networks, and GNSS receivers may each require evaluation depending upon frequency bands, transmission power, and intended operational use. Proper radio certification ensures compatibility with national spectrum management policies while minimizing interference with other communication systems.

Functional safety has become increasingly important within Korean industrial automation. Although KC certification itself may not explicitly certify all functional safety requirements, manufacturers frequently adopt internationally recognized standards including ISO 3691-4, IEC 62061, and ISO 13849-1 as engineering references. Performing comprehensive risk assessments, implementing certified safety functions, validating emergency stopping performance, and documenting safety architecture significantly strengthen both domestic certification activities and future international market expansion.

Comprehensive technical documentation is prepared throughout development. Mechanical drawings, electrical schematics, software architecture, communication diagrams, battery specifications, risk assessment reports, EMC test reports, operating manuals, maintenance procedures, warning labels, safety analyses, component certificates, and quality management records collectively demonstrate engineering compliance. Clear traceability between identified hazards, implemented protective functions, verification results, and final documentation simplifies certification review.

Product testing normally includes electrical safety evaluation, insulation resistance measurement, leakage current verification, temperature rise analysis, environmental testing, EMC measurements, wireless communication evaluation, battery charging verification, emergency stop validation, and operational reliability testing. Manufacturers frequently perform extensive pre-compliance testing before submitting products to accredited laboratories in order to minimize certification delays and redesign costs.

Following successful evaluation, certification records, approval documents, product labeling, and user documentation are finalized before commercial distribution. Manufacturers must maintain production consistency, configuration management, component traceability, and quality control throughout mass production. Significant hardware modifications, battery changes, communication module replacements, or safety-related software updates may require additional review or supplementary testing depending upon the nature of the modification.

Many Korean manufacturers developing export-oriented industrial AMRs intentionally align their engineering processes with both KC and international certification requirements from the earliest development stages. This integrated approach reduces duplicated engineering effort while simplifying simultaneous certification for Korea, Europe, North America, and other global markets.

Ultimately, KC certification provides far more than regulatory approval. It establishes systematic engineering discipline, improves product reliability, strengthens customer confidence, and creates a structured pathway toward successful commercialization of advanced industrial AMR platforms within both domestic and international markets.

### 5.3 Third-Party TÜV Certification Strategy

Third-party certification by TÜV represents one of the most effective methods for demonstrating the functional safety and engineering credibility of industrial Autonomous Mobile Robots. While many regulatory frameworks allow manufacturers to declare conformity through self-assessment, independent evaluation by an internationally recognized certification organization provides additional confidence for customers, regulatory authorities, insurance providers, and business partners. For heavy industrial AMRs operating in safety-critical manufacturing environments, third-party certification frequently becomes a significant competitive advantage.

A successful TÜV certification strategy should begin during system architecture design rather than after prototype completion. Safety requirements, hardware architecture, software development processes, diagnostic mechanisms, redundancy concepts, and verification activities should all be planned according to internationally accepted functional safety standards from the earliest project stages. Attempting to retrofit safety features late in development generally increases cost, delays schedules, and complicates certification.

The certification strategy normally begins with early technical consultation. Engineering teams discuss intended product functionality, applicable standards, target Safety Integrity Levels or Performance Levels, expected operating environments, and planned certification scope with TÜV specialists. Early feedback helps identify potential compliance issues before major engineering resources are committed to hardware development.

Comprehensive documentation forms the foundation of third-party assessment. System requirements, safety concepts, hazard analyses, ISO 12100 risk assessments, safety architecture descriptions, hardware schematics, software lifecycle documentation, verification procedures, validation reports, fault analysis, diagnostic coverage calculations, Failure Mode and Effects Analysis (FMEA), Fault Tree Analysis (FTA), and traceability matrices collectively demonstrate engineering maturity. High-quality documentation significantly improves certification efficiency because auditors can clearly understand design decisions and supporting technical evidence.

Independent engineering review is another major benefit of TÜV certification. Experienced functional safety specialists examine hardware architecture, software implementation, communication protocols, emergency stopping logic, diagnostic coverage, safety controller configuration, Safety LiDAR integration, battery protection systems, charging architecture, and human-machine interfaces. Recommendations generated during these reviews often improve both safety performance and long-term maintainability beyond minimum regulatory requirements.

Verification activities typically include document reviews, software assessments, hardware inspections, laboratory testing, functional testing, fault injection experiments, communication failure simulation, environmental testing, emergency recovery evaluation, safety function validation, and production quality audits. Particular attention is given to ensuring that every identified hazard is linked through complete traceability to corresponding protective functions, implementation evidence, verification records, and residual risk evaluation.

Configuration management plays a critical role throughout certification. Hardware revisions, software versions, firmware updates, supplier changes, and safety parameter modifications must all remain fully traceable. Certified configurations should be protected through rigorous change management procedures so that future product updates do not unintentionally invalidate previous certification results.

Manufacturers should also establish a long-term certification roadmap. Initial certification may focus on core functional safety requirements, while later product generations expand certification scope to include cybersecurity, advanced autonomous functions, collaborative operation, wireless charging systems, cloud connectivity, remote diagnostics, and AI-assisted operational decision support. Planning certification as a multi-generation strategy reduces repeated engineering effort while enabling continuous product evolution.

From a commercial perspective, TÜV certification significantly strengthens market competitiveness. Many multinational manufacturers, automotive companies, semiconductor facilities, pharmaceutical factories, and logistics operators increasingly require independently certified safety systems before purchasing industrial automation equipment. Consequently, third-party certification often accelerates customer acceptance, simplifies procurement approval, supports global market expansion, reduces contractual risk, and enhances corporate reputation.

Ultimately, a well-planned TÜV certification strategy transforms functional safety from a regulatory obligation into a strategic engineering asset. By integrating internationally recognized safety processes throughout the complete product lifecycle, manufacturers can develop industrial AMRs that achieve higher technical credibility, improved global acceptance, reduced project risk, and stronger long-term commercial success.

### 5.1 유럽 CE 인증 절차 (CE Certification Procedure in Europe)

---

### 5.2 한국 KC 인증 절차 (KC Certification Procedure in Korea)

---

### 5.3 제3자 TÜV 인증 전략 (Third-Party TÜV Certification Strategy)
