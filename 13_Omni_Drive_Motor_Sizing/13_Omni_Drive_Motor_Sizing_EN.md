**Differential Drive & Steer Drive Engineering**

# Chapter 13 Omni Drive Motor Sizing

## 01 Payload and friction analysis

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

Payload and friction analysis form the fundamental basis for designing reliable, efficient, and durable omnidirectional mobile robots. While kinematic models describe how wheel velocities generate vehicle motion, the actual ability of a robot to accelerate, decelerate, climb small obstacles, maintain precise positioning, and transport payloads depends on the interaction between the wheel system and the supporting surface. Engineers therefore evaluate payload capacity and friction characteristics together because these two factors determine the available traction force, required motor torque, energy consumption, wheel wear, and long-term operational reliability.

Unlike conventional pneumatic tires, omni wheels and Mecanum wheels generate propulsion through multiple passive rollers that continuously rotate around secondary axes. These rollers allow motion in directions other than the primary driving direction but simultaneously introduce additional rolling resistance, bearing friction, roller deformation, and energy losses. Consequently, the effective rolling resistance of omnidirectional robots differs significantly from that of conventional differential-drive platforms.

Payload directly influences nearly every aspect of vehicle performance. Increasing payload raises the normal force acting on each wheel, thereby improving available traction under ideal conditions. However, higher normal force also increases roller deformation, bearing loading, rolling resistance, drivetrain torque demand, and structural stress. Excessive payload may reduce acceleration capability, increase battery consumption, shorten bearing life, and decrease positioning accuracy due to greater elastic deformation throughout the mechanical structure.

Friction itself is not a fixed property but depends on numerous interacting variables including roller material, floor material, surface roughness, contamination, humidity, temperature, payload distribution, and vehicle speed. The multidirectional force transmission characteristic of omni-drive systems further complicates friction behavior because longitudinal and lateral force components continuously change during operation. Engineers therefore evaluate both static friction and dynamic friction while considering the anisotropic characteristics introduced by passive roller geometry.

Safety considerations require additional engineering margins beyond theoretical calculations. Manufacturing tolerances, unexpected payload variations, floor irregularities, wheel wear, environmental contamination, and long-term material aging all influence real-world performance. Appropriate safety factors ensure that wheel assemblies, motors, bearings, gearboxes, and structural members continue operating reliably even under unfavorable conditions.

Modern robotic engineering increasingly combines analytical calculations, multibody dynamic simulation, finite element analysis, experimental traction testing, and long-term field validation to optimize payload capability and friction performance simultaneously. Rather than maximizing a single parameter, engineers seek balanced system performance that provides reliable mobility, predictable positioning accuracy, reasonable energy consumption, and extended component lifetime throughout continuous industrial operation.

---

### 1.1 Effective Rolling Resistance with Passive Rollers

---

Rolling resistance represents one of the primary energy losses in any mobile robotic system. In omnidirectional robots, rolling resistance becomes significantly more complex because passive rollers continuously rotate while simultaneously transmitting driving forces through changing contact geometries. Understanding effective rolling resistance is therefore essential for accurate motor sizing, battery capacity estimation, thermal management, and vehicle performance prediction.

Unlike conventional wheels that maintain a continuous rolling contact, omni wheels and Mecanum wheels repeatedly transfer ground contact from one passive roller to the next. Every contact transition introduces small energy losses due to roller acceleration, bearing friction, elastic deformation, and localized impact. Although each individual loss is relatively small, the cumulative effect becomes significant during continuous industrial operation.

Several mechanisms contribute to effective rolling resistance. Bearing friction exists both within the primary wheel bearings and within every passive roller bearing. Since each omni wheel may contain numerous independently rotating rollers, the total number of bearings increases substantially compared with conventional wheel systems. Each bearing contributes a small but measurable frictional loss.

Material deformation introduces another important energy loss mechanism. Polyurethane rollers deform elastically under payload loading, storing and dissipating mechanical energy during every rotation cycle. Softer materials generally improve vibration isolation and traction but simultaneously increase hysteresis losses that appear as rolling resistance. Harder materials reduce deformation losses but may increase vibration and decrease floor conformity.

Contact geometry also affects resistance. During multidirectional motion, passive rollers frequently experience simultaneous rolling and micro-sliding because the resultant contact force does not always align perfectly with the roller rotation axis. This micro-slip increases frictional energy dissipation while contributing to roller wear and acoustic noise.

Payload significantly influences rolling resistance because increased normal force enlarges the contact area between rollers and the supporting surface. Greater deformation increases hysteresis while simultaneously raising bearing loading. Consequently, motor torque requirements increase approximately in proportion to payload under many practical operating conditions.

Surface characteristics further modify rolling resistance. Smooth epoxy floors typically provide low resistance and predictable performance, whereas rough concrete, expansion joints, contaminated surfaces, or soft flooring materials introduce additional mechanical losses. Moisture, dust, oil, and debris may further alter friction behavior unpredictably.

Engineers estimate effective rolling resistance using analytical models supported by experimental measurements performed under representative payloads and operating speeds. These data provide realistic inputs for motor selection, battery sizing, thermal analysis, and energy consumption prediction. Accurate rolling resistance estimation ultimately improves both mechanical reliability and overall system efficiency while reducing unnecessary design conservatism.

### 1.2 Safety Factor Selection for Omni Drive

---

Safety factor selection is a fundamental engineering practice that ensures omnidirectional mobile robots continue operating reliably despite uncertainties that inevitably arise between theoretical design calculations and real industrial environments. Rather than designing every component precisely at its calculated load limit, engineers intentionally incorporate additional structural capacity to accommodate unforeseen operating conditions throughout the robot\'s service life.

Omni-drive systems experience particularly complex loading because wheel forces continuously change direction during multidirectional motion. Acceleration, braking, sideways translation, rotation, obstacle traversal, payload variation, and uneven floor conditions generate combined mechanical stresses that are difficult to predict perfectly using analytical models alone. Safety factors therefore compensate for uncertainties associated with these multidirectional loading conditions.

Different components require different safety margins depending on failure consequences and loading characteristics. Structural frame members subjected primarily to static loading may require moderate safety factors, whereas wheel axles, hubs, suspension links, and bearings experiencing millions of fatigue cycles generally require larger margins. Components whose failure could immediately compromise vehicle safety typically receive the highest design margins.

Material variability also influences safety factor selection. Manufacturing processes introduce dimensional tolerances, residual stresses, heat-treatment variation, and surface finish differences that alter actual mechanical properties. Long-term environmental exposure including corrosion, temperature cycling, ultraviolet radiation, chemical contamination, and repeated loading gradually changes material behavior throughout the product lifecycle.

Operational uncertainty further justifies conservative engineering design. Industrial robots rarely operate exactly as assumed during laboratory calculations. Unexpected payload overload, operator misuse, emergency stops, accidental collisions, worn floor surfaces, contaminated environments, and maintenance errors all increase mechanical loading beyond nominal design conditions.

Fatigue considerations are particularly important because omni-drive robots frequently operate continuously for thousands of hours. Repeated acceleration, braking, directional changes, and roller impacts generate cyclic stresses that gradually accumulate microscopic material damage. Safety factors based solely on static strength may therefore prove inadequate unless fatigue behavior is also evaluated carefully.

International engineering standards often provide recommended safety factor ranges according to application type, loading uncertainty, and required reliability. Heavy industrial material handling systems generally employ larger safety factors than educational robots or research platforms because the consequences of structural failure are substantially greater.

Modern engineering increasingly supplements traditional safety factor methods with probabilistic reliability analysis, digital twin simulation, and predictive maintenance. Rather than relying exclusively on conservative overdesign, engineers continuously monitor structural health using vibration analysis, load sensing, temperature monitoring, and machine learning algorithms. Nevertheless, appropriate safety factor selection remains an indispensable element of professional omni-drive mechanical design, ensuring robust performance, long service life, operational safety, and dependable industrial productivity.

### 1.1 패시브 롤러를 고려한 유효 구름 저항 (Effective Rolling Resistance with Passive Rollers)

---

### 1.2 옴니 드라이브를 위한 안전율 선정 (Safety Factor Selection for Omni Drive)

## 02 Torque calculation for omni drive

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Torque calculation is one of the most important engineering activities in the design of an omnidirectional mobile robot because it directly determines motor selection, gearbox ratio, battery capacity, thermal performance, acceleration capability, and long-term drivetrain reliability. While kinematic analysis describes the relationship between wheel velocities and vehicle motion, torque analysis determines whether the mechanical system can actually generate the required forces under real operating conditions. An incorrectly estimated torque requirement may result in insufficient acceleration, excessive motor heating, premature gearbox wear, wheel slip, or complete inability to transport the intended payload.

Unlike conventional differential-drive robots, omni-drive platforms distribute propulsion among multiple independently controlled wheels. During forward motion, lateral translation, diagonal movement, and simultaneous rotation, each wheel contributes a different force component according to the inverse kinematic solution. Consequently, wheel torque is not constant but continuously changes depending on vehicle velocity, acceleration, motion direction, payload distribution, floor friction, and controller commands. Engineers therefore evaluate multiple operating scenarios rather than relying on a single nominal condition.

The total drive torque required at each wheel consists of several independent components. The first is rolling resistance torque generated by wheel-ground interaction and passive roller friction. The second is inertial torque required to accelerate the robot mass. Additional torque is required to overcome drivetrain friction, gearbox losses, bearing resistance, roller hysteresis, floor irregularities, and mechanical inefficiencies. When operating on ramps or traversing small obstacles, gravitational forces introduce further torque demands. The motor must therefore provide sufficient continuous torque for normal operation while maintaining adequate peak torque capability for transient conditions.

Payload distribution significantly affects torque requirements. A centrally located payload produces relatively uniform wheel loading, whereas an offset payload increases the torque demand on individual wheels due to unequal normal forces. Dynamic payloads such as robotic manipulators further complicate analysis because the center of gravity continuously changes during operation. Torque estimation must therefore consider both static loading conditions and time-varying dynamic effects.

Control strategy also influences torque demand. Smooth acceleration profiles with jerk limitation reduce peak torque while minimizing wheel slip and vibration. Conversely, aggressive motion commands require substantially higher instantaneous torque to achieve rapid acceleration and direction changes. Modern motion controllers therefore balance responsiveness, energy efficiency, mechanical durability, and positioning accuracy by intelligently distributing torque among all wheels.

Industrial robot designers typically combine analytical calculations, multibody dynamic simulation, experimental traction testing, and motor performance characterization when determining drivetrain specifications. Appropriate torque estimation ensures reliable operation while avoiding unnecessary oversizing that increases vehicle cost, weight, and energy consumption. Consequently, torque calculation represents a multidisciplinary engineering process integrating mechanics, control theory, electrical engineering, and system optimization.

---

### 2.1 Drive Torque per Wheel in Holonomic Motion

---

Holonomic motion allows an omnidirectional robot to move in any direction while independently controlling rotational motion. Unlike non-holonomic vehicles, which must align their heading before changing travel direction, holonomic robots simultaneously generate longitudinal velocity, lateral velocity, and angular velocity. This capability requires precise coordination of the torque generated by every drive wheel.

Each wheel contributes a specific force component determined by the robot\'s inverse kinematic transformation matrix. During pure forward motion, all wheels generally generate similar driving torque because their primary contribution is longitudinal propulsion. During lateral motion, however, force vectors are redistributed according to wheel orientation. Mecanum wheels accomplish this by resolving the roller contact forces into orthogonal components, while omni-wheel platforms employ wheel orientation angles to generate the desired lateral force.

The required wheel torque depends directly on the traction force assigned to each wheel. Traction force itself is determined by the desired vehicle acceleration together with rolling resistance, payload weight, and drivetrain losses. Once the required traction force is known, wheel torque is calculated simply by multiplying the force by the effective wheel radius. However, the effective radius of omni-drive wheels may vary slightly because passive rollers deform elastically under load.

Rotational motion introduces additional complexity because wheels located farther from the vehicle center contribute larger rotational moments. During pure rotation, wheels positioned symmetrically around the chassis generate equal but oppositely directed traction forces that collectively produce vehicle yaw. Combined translation and rotation require superposition of both force components, resulting in different torque values for each wheel.

Dynamic loading continuously modifies wheel torque throughout robot operation. Changes in payload distribution alter normal forces, which influence available traction and rolling resistance. Uneven floor surfaces, wheel wear, and minor manufacturing tolerances further modify the actual torque delivered by each wheel. Modern motor controllers therefore adjust wheel torque continuously using encoder feedback, current sensing, and traction control algorithms.

Accurate torque distribution provides several important advantages. Balanced wheel loading reduces tire wear, minimizes energy consumption, improves motion smoothness, and enhances localization accuracy by reducing wheel slip. It also prevents individual motors from operating near their thermal limits while allowing the entire drivetrain to share mechanical loading efficiently.

Modern omnidirectional robots frequently implement real-time torque allocation algorithms that account for wheel loading, motor temperature, traction estimation, and vehicle dynamics simultaneously. This adaptive approach improves efficiency, extends drivetrain life, and maintains stable vehicle motion under varying payloads and environmental conditions.

### 2.2 Worst Case Torque in Diagonal and Lateral Motion

---

The highest torque demand experienced by an omnidirectional robot rarely occurs during straight-line travel. Instead, worst-case operating conditions typically arise during diagonal translation, pure lateral motion, rapid direction changes, or simultaneous translation and rotation. These complex maneuvers require multiple wheels to generate maximum traction simultaneously while overcoming rolling resistance, inertial forces, and drivetrain losses.

Pure lateral motion is particularly demanding for Mecanum-wheel platforms because propulsion relies entirely on force components generated through the forty-five-degree roller orientation. Since only part of the wheel traction contributes directly to lateral movement, the effective mechanical efficiency decreases compared with forward motion. Consequently, motors must generate higher wheel torque to produce the same vehicle acceleration.

Diagonal motion also increases torque demand because longitudinal and lateral velocity components combine simultaneously. Depending on the commanded direction, certain wheels experience constructive force addition while others experience partial cancellation. Wheels contributing the greatest resultant force become torque-limiting components that determine overall drivetrain sizing.

Rapid acceleration further amplifies peak torque requirements. According to Newton\'s second law, traction force increases proportionally with vehicle acceleration. Since wheel torque equals traction force multiplied by wheel radius, aggressive motion commands may require peak motor torque several times greater than steady-state cruising conditions. Engineers therefore distinguish between continuous torque ratings and short-duration peak torque capability.

Payload location strongly influences worst-case analysis. An offset center of gravity increases normal force on specific wheels while unloading others. Although heavily loaded wheels can generate greater traction, they simultaneously experience increased rolling resistance and bearing friction. Unloaded wheels may reach traction limits sooner, increasing the risk of wheel slip during demanding maneuvers.

Environmental factors also contribute to worst-case conditions. Rough concrete floors, expansion joints, contaminated surfaces, ramps, and uneven payload distribution all increase required wheel torque. Temperature-dependent changes in motor performance and battery voltage further influence available torque during prolonged operation.

Industrial robot designers therefore evaluate multiple worst-case operating scenarios rather than relying solely on nominal calculations. Simulation models combine vehicle dynamics, friction estimation, drivetrain efficiency, and motor characteristics to identify the maximum expected wheel torque. Appropriate safety factors are then incorporated to accommodate uncertainties while maintaining acceptable thermal performance and mechanical reliability throughout the robot\'s operational life.

### 2.3 Worked Example: 100 kg AMR with Four Mecanum Wheels

---

Consider a four-wheel Mecanum autonomous mobile robot with a total operating mass of 100 kilograms, including chassis, batteries, onboard electronics, and payload. Assume the robot operates on a smooth epoxy floor using wheels with a diameter of 150 millimeters, corresponding to an effective wheel radius of 75 millimeters. The desired maximum acceleration is one meter per second squared while maintaining reliable omnidirectional mobility.

The total inertial force required to accelerate the robot equals the product of vehicle mass and acceleration. Under these assumptions, the robot requires approximately one hundred newtons of net traction force before accounting for rolling resistance and drivetrain losses. Assuming uniform weight distribution and ideal kinematic conditions, each wheel contributes approximately one quarter of the total longitudinal traction during straight-line acceleration.

Rolling resistance must also be included. Assuming an effective rolling resistance coefficient representative of industrial polyurethane rollers operating on epoxy flooring, the additional traction requirement increases modestly. Gearbox efficiency, bearing losses, roller deformation, and motor transmission losses further increase the required wheel force. Engineers generally combine these effects into an overall drivetrain efficiency factor rather than modeling every individual loss separately during preliminary design.

The required wheel torque is obtained by multiplying wheel traction force by the effective wheel radius. Under nominal forward acceleration, each wheel requires only a moderate continuous torque because the vehicle weight is distributed among four independently driven wheels. However, diagonal motion and simultaneous rotation increase the torque demand on individual wheels because force distribution becomes nonuniform.

To accommodate real industrial operation, designers typically multiply calculated continuous torque by an engineering safety margin. Peak motor torque is selected sufficiently above nominal operating torque to support emergency acceleration, obstacle traversal, payload variation, and temporary traction disturbances without exceeding motor thermal limits.

Motor selection then considers both continuous and peak torque ratings together with maximum rotational speed. The gearbox ratio is chosen so that the motor operates within its efficient speed range while providing adequate wheel torque across the desired vehicle velocity envelope. Battery capacity and motor controller current limits are subsequently verified to ensure that peak electrical demand remains within acceptable limits.

Finally, simulation and experimental validation confirm analytical calculations. Dynamometer testing, current measurements, encoder data, and vehicle acceleration experiments verify that the selected drivetrain satisfies performance requirements while maintaining acceptable motor temperatures, gearbox loading, and energy consumption. This systematic design methodology produces an omnidirectional mobile robot capable of reliable industrial operation while balancing performance, efficiency, durability, and overall system cost.

### 2.1 전방향 이동에서 휠당 구동 토크 (Drive Torque per Wheel in Holonomic Motion)

---

**Wheel Torque = Traction Force × Effective Wheel Radius**

### 2.2 대각선 및 측면 이동에서의 최대 토크 (Worst Case Torque in Diagonal and Lateral Motion)

---

### 2.3 계산 예제 : 100kg급 4륜 메카넘 AMR (Worked Example: 100 kg AMR with Four Mecanum Wheels)

**F = m × a = 100 × 1 = 100 N**

**Wheel Torque = Wheel Traction × Wheel Radius**

## 03 Speed and RPM calculation

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

Speed and rotational speed calculations form one of the most fundamental engineering tasks in the design of omnidirectional mobile robots because they establish the direct relationship between desired vehicle motion and individual wheel motion. Every autonomous mobile robot ultimately converts translational and rotational commands into wheel rotational speeds through its drive system. Consequently, accurate speed and revolutions-per-minute (RPM) calculations determine motor selection, gearbox ratio, encoder resolution, controller bandwidth, battery power requirements, and the achievable operating envelope of the robot.

Unlike conventional differential-drive vehicles, omni-drive and Mecanum-drive robots possess three independent degrees of freedom in planar motion. The robot can simultaneously move forward or backward, translate laterally, and rotate around its vertical axis. This capability significantly increases maneuverability but also makes wheel speed calculations considerably more complex. Each wheel rotates at a different speed depending on the desired combination of longitudinal velocity, lateral velocity, and angular velocity. The controller must therefore continuously solve the inverse kinematic equations and convert body motion into individual wheel RPM values.

The relationship between linear velocity and wheel RPM is fundamentally determined by wheel diameter. Larger wheels travel farther during each revolution, reducing required motor RPM for a given vehicle speed while increasing rotational inertia. Smaller wheels require higher rotational speed but often provide better acceleration and more compact vehicle packaging. Gear reduction ratios further modify this relationship by allowing motors to operate within their optimal efficiency range while producing the required wheel speed and torque.

Real industrial robots rarely operate under ideal conditions. Rolling resistance, wheel deformation, passive roller friction, manufacturing tolerances, payload variation, and floor conditions continuously influence actual wheel speed. During acceleration and deceleration, temporary speed deviations occur because motors require finite time to generate torque while the robot body responds to inertia. Consequently, speed calculation is closely integrated with closed-loop motor control using encoder feedback and current regulation to maintain accurate vehicle motion.

Maximum vehicle speed is also constrained by numerous practical limitations beyond motor capability alone. Passive roller dynamics, traction limits, roller slip, bearing performance, vibration, structural resonance, and safety considerations all establish upper operating limits. Increasing wheel speed without considering these factors may reduce positioning accuracy, increase component wear, and compromise vehicle stability. Engineers therefore optimize wheel diameter, motor speed, gearbox ratio, and controller parameters together to achieve balanced performance rather than simply maximizing velocity.

Modern industrial AMRs increasingly combine analytical speed calculation, multibody dynamic simulation, digital twin verification, and experimental validation to determine realistic operating limits. The objective is not only to achieve high travel speed but also to maintain precise localization, stable payload transport, low vibration, efficient energy consumption, and reliable long-term operation under diverse industrial conditions.

---

### 3.1 Wheel RPM from Target Linear and Angular Velocity

---

Determining individual wheel RPM from desired vehicle motion represents one of the core calculations performed by every omnidirectional robot controller. Whenever the navigation system generates a motion command, the controller must immediately calculate the rotational speed required for each wheel so that the robot follows the intended trajectory accurately. This process is based on inverse kinematics, which transforms body-centered motion into wheel rotational motion.

The desired vehicle motion is generally described using three independent velocity components. The longitudinal velocity represents forward or backward movement along the robot\'s x-axis. The lateral velocity represents sideways motion along the y-axis. Angular velocity describes rotation around the vertical axis. Because omni-drive robots possess full holonomic mobility, these three velocity components may be commanded simultaneously, allowing the robot to move diagonally while rotating at the same time.

Each wheel experiences a unique velocity depending on its location relative to the robot center. The translational velocity contributes equally according to wheel orientation, while rotational velocity contributes according to the wheel\'s distance from the center of rotation. Wheels farther from the center generate larger rotational velocity components because they travel longer circular paths during vehicle rotation.

Once the required wheel linear velocity has been determined, wheel RPM can be calculated directly from the effective wheel circumference. Since one wheel revolution moves the robot by approximately one wheel circumference under ideal rolling conditions, the relationship between wheel speed and rotational speed remains straightforward. Larger wheel diameters require fewer revolutions to achieve the same linear velocity, whereas smaller wheels require proportionally higher RPM.

Gear reduction significantly affects motor RPM. The wheel rotational speed is multiplied by the gearbox ratio to determine the corresponding motor rotational speed. High gear reductions allow relatively small electric motors to generate substantial wheel torque while operating within their efficient speed range. However, excessive reduction limits maximum vehicle speed and may reduce drivetrain efficiency due to additional gearbox losses.

Encoder resolution must also be considered. Accurate velocity control depends on sufficient encoder counts per wheel revolution to provide smooth speed estimation. High-resolution encoders improve low-speed positioning accuracy and enable precise closed-loop control but increase computational requirements and system cost.

During combined translation and rotation, each wheel typically rotates at a different speed. Some wheels accelerate while others decelerate, and one or more wheels may even reverse direction depending on the commanded motion. The motor controller continuously updates wheel RPM several hundred or even several thousand times per second, ensuring smooth trajectory tracking despite changing vehicle dynamics.

Real operating conditions introduce additional corrections beyond ideal kinematic calculations. Wheel deformation slightly changes the effective rolling radius, passive roller compliance influences actual displacement, and wheel slip modifies the relationship between wheel rotation and vehicle motion. Advanced control systems therefore compare predicted motion with encoder feedback, inertial measurements, and localization sensors to compensate for these effects in real time.

Modern industrial robots increasingly implement adaptive wheel-speed estimation algorithms that account for payload variation, floor friction, wheel wear, and drivetrain efficiency. These intelligent control strategies improve motion accuracy while maintaining smooth operation across a wide range of industrial environments.

### 3.2 Maximum Speed Constraints and Roller Slip

---

Although motor specifications often suggest very high theoretical wheel speeds, the maximum practical operating speed of an omnidirectional robot is determined by numerous mechanical, dynamic, and environmental limitations. Simply increasing motor RPM does not necessarily improve productivity because excessive speed may introduce wheel slip, vibration, positioning error, thermal overload, and safety risks. Understanding these constraints is therefore essential when designing industrial omni-drive systems.

One of the primary limiting factors is passive roller dynamics. Unlike conventional wheels, omni wheels and Mecanum wheels continuously transfer contact from one roller to the next as the wheel rotates. At moderate speeds this transition occurs smoothly, but at higher rotational speeds the repeated contact changes generate increasing vibration, impact forces, and acoustic noise. The roller bearings themselves also experience greater rotational acceleration, increasing frictional losses and mechanical wear.

Roller slip represents another major speed limitation. Ideally, every roller rolls freely while transmitting the required traction force. However, as wheel speed increases, the direction of the contact force frequently differs from the instantaneous roller rotation axis. Small amounts of micro-slip therefore occur naturally. Excessive speed, rapid acceleration, or reduced floor friction amplify this sliding effect, increasing energy loss, roller wear, and positioning error.

Traction limits establish another important constraint. The maximum usable driving force depends on the coefficient of friction between the roller material and the floor surface together with the available normal force acting on each wheel. When commanded acceleration exceeds available traction, wheel slip occurs before the desired vehicle acceleration is achieved. Motor controllers therefore limit torque output based on estimated traction conditions to maintain stable vehicle motion.

Vehicle dynamics further restrict maximum speed. Higher travel velocity increases stopping distance, payload oscillation, suspension excitation, and structural vibration. Tall payloads experience greater inertial moments during rapid directional changes, increasing rollover risk and reducing positioning precision. Consequently, industrial safety standards often impose application-specific speed limits according to payload mass, operating environment, and human interaction requirements.

Thermal considerations also become increasingly important at high speed. Motors draw greater current during sustained high-power operation, increasing copper losses and winding temperature. Gearboxes generate additional frictional heat, while roller bearings experience higher rotational velocity and lubricant shear. Continuous operation near maximum RPM may therefore reduce component lifetime unless adequate cooling is provided.

Surface quality strongly influences maximum achievable speed. Smooth epoxy floors permit higher operating velocities than rough concrete because roller transitions occur more uniformly. Expansion joints, floor cracks, embedded rails, dust, oil contamination, and moisture all increase the likelihood of wheel slip and vibration. Consequently, identical robots may exhibit significantly different maximum safe speeds depending on facility conditions.

Modern industrial AMRs employ multiple strategies to prevent excessive roller slip. Closed-loop traction control monitors encoder feedback, inertial sensors, and motor current to detect abnormal wheel acceleration. Adaptive velocity planning automatically reduces speed before entering sharp turns, narrow aisles, docking stations, or low-friction surfaces. Motion controllers further limit jerk and acceleration to reduce sudden load transfer between wheels.

Engineers typically validate theoretical speed limits through experimental testing using progressively increasing velocity profiles under representative payloads and floor conditions. Measurements of wheel slip, vibration, motor temperature, energy consumption, localization accuracy, and stopping performance establish realistic operating envelopes. Rather than maximizing top speed alone, successful omni-drive design seeks the optimal balance between productivity, precision, mechanical durability, passenger or payload safety, and long-term system reliability.

### 3.1 목표 선형 속도와 각속도로부터 휠 RPM 계산 (Wheel RPM from Target Linear and Angular Velocity)

---

### 3.2 최고 속도 제한 요소 및 롤러 슬립 (Maximum Speed Constraints and Roller Slip)

## 04 Gear ratio and efficiency

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Gear ratio selection is one of the most influential design decisions in an omnidirectional mobile robot because it directly determines the balance between wheel torque, vehicle speed, energy efficiency, drivetrain durability, and overall system responsiveness. Although the electric motor provides the primary source of mechanical power, its torque and speed characteristics rarely match the requirements of the wheels directly. A gearbox therefore serves as the mechanical interface that converts the high-speed, relatively low-torque output of the motor into the lower-speed, higher-torque motion required by the drive wheels. Selecting an appropriate reduction ratio is not simply a matter of increasing torque. It requires balancing multiple competing objectives including acceleration capability, maximum travel speed, thermal performance, battery utilization, gearbox efficiency, motor operating efficiency, and long-term reliability.

Omnidirectional robots introduce additional complexity because each wheel continuously experiences changing load directions. Unlike conventional differential-drive vehicles that primarily transmit longitudinal forces, omni wheels and Mecanum wheels simultaneously generate longitudinal, lateral, and rotational force components. Consequently, motor torque demand varies continuously depending on the commanded vehicle motion. During diagonal translation, lateral movement, or simultaneous translation and rotation, different wheels operate under significantly different loading conditions. The selected gear ratio must therefore provide sufficient torque under the most demanding operating scenarios while still allowing adequate maximum vehicle speed during normal operation.

Mechanical efficiency represents another equally important design consideration. Every gearbox introduces energy losses through gear meshing friction, bearing friction, lubricant shear, and mechanical deformation. Additional efficiency losses arise from passive roller bearings, roller deformation, and the changing contact geometry characteristic of omnidirectional wheels. As a result, the mechanical efficiency of an omni-drive system is influenced not only by gearbox design but also by wheel architecture, roller material, floor condition, payload, and driving strategy. Engineers therefore evaluate the complete drivetrain rather than individual components in isolation.

The interaction between gear ratio and efficiency also influences thermal behavior. Larger reduction ratios generally increase available wheel torque while reducing required motor current during heavy loading. However, additional gearbox stages may increase mechanical losses and generate more heat. Conversely, smaller reduction ratios reduce gearbox losses but require higher motor current, increasing electrical losses within the motor windings. The optimal design therefore seeks the highest overall drivetrain efficiency rather than maximizing either gearbox efficiency or motor efficiency individually.

Modern industrial robots increasingly utilize integrated system optimization, combining motor efficiency maps, gearbox characteristics, dynamic simulation, thermal analysis, and experimental validation. Rather than selecting a gearbox solely from catalog specifications, engineers evaluate the expected operating duty cycle, payload profile, acceleration requirements, floor conditions, and energy consumption simultaneously. This holistic approach ensures that the drivetrain achieves high productivity, excellent positioning accuracy, long service life, and low operating cost throughout continuous industrial operation.

---

### 4.1 Reduction Ratio Selection for Omnidirectional Motors

---

The reduction ratio of a gearbox determines how motor speed is converted into wheel speed and how motor torque is amplified before reaching the drive wheels. Selecting the appropriate reduction ratio is therefore one of the most important mechanical design decisions for an omnidirectional mobile robot. A properly selected ratio allows the motor to operate within its most efficient speed range while delivering sufficient wheel torque for all expected operating conditions.

Electric motors generally produce their highest efficiency at relatively high rotational speeds, often several thousand revolutions per minute. However, industrial mobile robots typically require wheel rotational speeds that are much lower. A gearbox bridges this difference by reducing rotational speed while proportionally increasing output torque. The reduction ratio defines the relationship between motor RPM and wheel RPM, directly influencing maximum vehicle speed, acceleration capability, and climbing performance.

A high reduction ratio provides greater wheel torque, making it suitable for heavy payloads, steep ramps, and frequent acceleration. The increased torque improves traction utilization and reduces motor current during demanding operations. However, excessive reduction limits maximum travel speed because wheel RPM decreases proportionally. Additional gearbox stages may also increase frictional losses, mechanical complexity, weight, and manufacturing cost.

A low reduction ratio allows higher vehicle speed because wheel RPM remains relatively close to motor speed. This configuration is advantageous for lightweight robots operating over long travel distances with modest payloads. Nevertheless, lower torque multiplication requires the motor to generate higher torque directly, increasing current consumption and thermal loading during acceleration or heavy payload transport.

Omnidirectional robots require particularly careful ratio selection because wheel loading changes continuously with vehicle motion. During pure forward travel, wheel torque remains relatively balanced. During lateral translation or combined rotational movement, however, certain wheels experience significantly greater loading. Engineers therefore select the reduction ratio according to the worst expected operating condition rather than average driving requirements.

The reduction ratio also influences control performance. High gear reductions reduce sensitivity to motor torque ripple and improve low-speed controllability because wheel motion becomes smoother. Conversely, extremely large gear reductions increase drivetrain compliance and backlash, potentially reducing positioning accuracy during rapid direction changes. Precision planetary gearboxes with minimal backlash are therefore commonly used in industrial omnidirectional robots.

Motor efficiency maps, gearbox efficiency curves, thermal models, and vehicle dynamic simulations are increasingly integrated during gearbox selection. Instead of maximizing either speed or torque independently, engineers optimize the reduction ratio to minimize overall energy consumption while satisfying acceleration, payload capacity, maximum speed, and reliability requirements. The resulting drivetrain achieves balanced performance suitable for continuous industrial operation across diverse working environments.

### 4.2 Efficiency Penalty from Roller Contact Angle

---

One of the unique characteristics of omnidirectional wheel systems is that propulsion forces are transmitted through passive rollers mounted at specific orientations relative to the primary wheel rotation. While this configuration enables multidirectional mobility, it also introduces unavoidable mechanical efficiency penalties because not all generated wheel force contributes directly to the desired vehicle motion.

Conventional wheels transmit nearly all driving force along the rolling direction. In contrast, Mecanum wheels utilize rollers mounted at approximately forty-five degrees, while omni-wheel platforms rely on wheel orientation to resolve driving forces into multiple directional components. As a result, only a portion of the generated wheel force contributes directly to the commanded vehicle motion, while the remaining force components are redirected or internally balanced within the drivetrain.

This geometric force decomposition effectively reduces propulsion efficiency. During lateral translation, for example, Mecanum wheels generate both longitudinal and lateral force components simultaneously. The undesired longitudinal components cancel one another through the vehicle structure, while only the lateral components contribute to actual vehicle movement. Although this cancellation enables omnidirectional motion, part of the available motor torque is effectively consumed without producing useful translational work.

Passive roller bearings introduce additional efficiency losses. Every roller rotates independently as contact conditions change, creating bearing friction, lubricant shear, and rotational inertia. Frequent transitions between adjacent rollers generate small impact forces and micro-slip, particularly during high-speed operation or rapid acceleration. These phenomena further reduce overall drivetrain efficiency while increasing vibration and acoustic noise.

Roller deformation also contributes to efficiency loss. Polyurethane rollers undergo elastic compression under load, storing and dissipating mechanical energy through hysteresis. Softer materials improve traction and vibration isolation but generally exhibit greater hysteresis losses than harder materials. Engineers therefore balance energy efficiency against ride quality, floor conformity, and positioning precision when selecting roller materials.

Floor conditions significantly influence contact-angle efficiency penalties. Smooth epoxy floors provide predictable contact behavior with relatively low rolling resistance. Rough concrete, contaminated surfaces, expansion joints, and uneven flooring increase micro-slip and roller deformation, reducing effective propulsion efficiency. Payload distribution further modifies these effects because higher wheel loading increases both available traction and hysteresis losses.

Engineers evaluate these efficiency penalties using force-vector analysis, multibody dynamic simulation, finite element contact modeling, and experimental power measurements. Rather than attempting to eliminate efficiency losses entirely, modern omnidirectional robot design seeks to minimize unnecessary losses through optimized roller geometry, high-quality bearings, efficient gearboxes, precise wheel alignment, intelligent torque distribution, and advanced motion planning.

Ultimately, the modest efficiency penalty associated with roller contact angles is generally outweighed by the substantial advantages of omnidirectional mobility. The ability to perform lateral translation, zero-radius rotation, precise docking, and highly maneuverable motion often produces significantly greater improvements in overall operational productivity than the relatively small reduction in mechanical efficiency. Consequently, optimized omni-drive systems continue to be widely adopted in semiconductor manufacturing, warehouse automation, medical robotics, laboratory automation, and other industries requiring exceptional maneuverability within confined working spaces.

### 4.1 전방향 이동 모터를 위한 감속비 선정 (Reduction Ratio Selection for Omnidirectional Motors)

---

### 4.2 롤러 접촉 각도에 따른 효율 손실 (Efficiency Penalty from Roller Contact Angle)

## 05 Motor and driver selection

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Motor and driver selection is one of the most critical engineering decisions in the development of an omnidirectional mobile robot because the electrical drive system directly determines mobility performance, positioning accuracy, energy efficiency, thermal behavior, reliability, and overall operating cost. Even when an omnidirectional platform has an optimized mechanical structure and an accurate kinematic model, poor motor or driver selection can severely limit acceleration, reduce positioning precision, increase vibration, and shorten component lifetime. Consequently, the drivetrain should always be designed as an integrated electromechanical system rather than as separate mechanical and electrical subsystems.

Unlike conventional mobile robots that often use only two drive motors, omni-drive platforms normally employ three or four independently controlled drive motors operating simultaneously. Each motor continuously changes speed and torque according to inverse kinematic calculations while responding to changing payloads, floor conditions, and motion commands. The motor driver must therefore provide precise current control, high-speed communication, synchronized motion execution, and stable closed-loop feedback across all drive axes.

The selection process begins by defining the required mechanical performance. Engineers calculate the maximum vehicle speed, required wheel torque, acceleration capability, payload capacity, duty cycle, and thermal operating conditions. These mechanical requirements are then translated into motor torque, rotational speed, continuous power, peak power, and gearbox specifications. Electrical considerations such as supply voltage, battery capacity, current limits, regenerative braking capability, communication protocols, encoder compatibility, and electromagnetic compatibility must also be evaluated simultaneously.

System integration plays an equally important role. Motors, drivers, encoders, batteries, controllers, and communication networks must operate as a synchronized motion control system. Inconsistencies in driver response time, encoder resolution, or current regulation may cause unequal wheel behavior, resulting in wheel slip, vibration, trajectory deviation, or unnecessary energy consumption. Consequently, industrial omnidirectional robots often utilize matched motor-driver families specifically designed for coordinated multi-axis motion.

Modern robotics increasingly incorporates intelligent drive technologies such as field-oriented control (FOC), adaptive current regulation, automatic motor identification, thermal protection, regenerative energy management, predictive diagnostics, and real-time condition monitoring. These advanced features not only improve motion quality but also extend component lifetime and simplify maintenance throughout continuous industrial operation.

The final motor and driver selection therefore represents a balance between performance, efficiency, reliability, maintainability, cost, and future scalability. Successful drivetrain design ensures smooth omnidirectional motion while minimizing energy consumption and maximizing operational productivity across a wide range of industrial environments.

---

### 5.1 BLDC vs Servo Selection for Omni Drive

---

Selecting between brushless DC (BLDC) motors and servo motors is one of the most important decisions when designing an omnidirectional drive system. Both technologies are widely used in industrial robotics, yet they exhibit significantly different performance characteristics, control complexity, cost, and application suitability. The optimal choice depends on the intended operating environment, required positioning accuracy, payload capacity, and overall system objectives.

BLDC motors are attractive because of their relatively simple construction, high efficiency, compact size, and competitive cost. They generate smooth rotational motion with minimal maintenance since they eliminate mechanical brushes and commutators. Combined with modern field-oriented control algorithms, BLDC motors can achieve excellent speed regulation and sufficient torque for many industrial AMRs operating in warehouses, factories, hospitals, and logistics centers.

Servo motors provide additional advantages when extremely precise motion control is required. A servo system integrates a high-performance motor, high-resolution encoder, and sophisticated closed-loop controller capable of simultaneously regulating position, velocity, and torque. This enables outstanding positioning accuracy, rapid dynamic response, minimal speed fluctuation, and excellent repeatability during complex omnidirectional maneuvers.

Torque characteristics differ considerably between the two technologies. Servo motors typically produce higher peak torque relative to their continuous rating, allowing rapid acceleration, deceleration, and direction changes without significant performance degradation. BLDC motors generally provide excellent continuous efficiency but may require larger motor sizes or higher gear reductions to achieve equivalent transient performance.

Control performance also influences selection. Servo drives continuously monitor encoder feedback at extremely high update rates, allowing accurate compensation for disturbances such as varying payloads, floor irregularities, or wheel slip. Modern BLDC controllers increasingly incorporate similar feedback capabilities, narrowing the performance gap, although premium servo systems still provide superior dynamic precision.

Cost remains an important practical consideration. BLDC systems generally offer lower purchase cost, reduced controller complexity, and simpler commissioning procedures. Servo systems require higher-quality encoders, more advanced controllers, and additional tuning, increasing initial investment. However, improved positioning accuracy, reduced maintenance, and higher productivity may justify these additional costs in precision manufacturing applications.

Typical application trends reflect these differences. Warehouse logistics robots, hospital delivery platforms, and general material handling systems frequently employ BLDC motors because they provide excellent performance at reasonable cost. Semiconductor handling robots, precision inspection systems, collaborative manufacturing platforms, and mobile manipulators often utilize servo motors where positioning accuracy and dynamic response outweigh higher equipment costs.

Ultimately, neither technology is universally superior. The most appropriate choice results from careful evaluation of payload, positioning requirements, operating duty cycle, environmental conditions, lifecycle cost, maintenance strategy, and future expansion plans.

### 5.2 Matched Four-Axis Driver Configuration

---

An omnidirectional robot equipped with four independently driven wheels requires a coordinated four-axis motor control architecture. Although each motor operates independently according to inverse kinematic calculations, the entire drivetrain must behave as a synchronized motion system. Driver matching therefore becomes essential for maintaining stable vehicle motion, minimizing wheel slip, and achieving precise trajectory tracking.

Matched four-axis driver configurations utilize identical or closely compatible motor drivers across all wheel modules. Consistent electrical characteristics ensure that current regulation, torque response, communication latency, and feedback processing remain nearly identical for every drive axis. This symmetry simplifies controller design while improving motion consistency during multidirectional operation.

Current control represents one of the most important synchronization requirements. Since wheel torque is directly proportional to motor current, inconsistent current regulation between drivers immediately produces unequal wheel forces. Even relatively small current deviations may generate unwanted vehicle rotation, lateral drift, or increased wheel slip during acceleration.

Communication architecture strongly influences synchronization quality. Modern industrial robots commonly employ deterministic fieldbus protocols such as EtherCAT, CANopen, or industrial Ethernet to exchange motion commands and feedback data. These networks provide synchronized update timing across all motor drivers, allowing coordinated execution of complex motion trajectories with sub-millisecond timing accuracy.

Encoder compatibility is equally important. Identical encoder resolution and sampling frequency ensure consistent velocity estimation and position feedback among all wheels. Differences in encoder performance may cause individual wheels to respond differently despite identical motion commands, reducing localization accuracy and trajectory repeatability.

Power distribution must also be carefully designed. Shared DC bus architectures reduce wiring complexity while enabling regenerative braking energy generated by one motor to be consumed by another motor accelerating simultaneously. This improves overall drivetrain efficiency and reduces battery loading during highly dynamic maneuvers.

Modern multi-axis driver systems increasingly integrate advanced diagnostic capabilities. Continuous monitoring of motor current, temperature, voltage, encoder status, communication quality, and fault conditions allows predictive maintenance while preventing catastrophic failures. Automatic fault isolation further improves system availability because individual drive modules can safely disable themselves without damaging the remaining drivetrain.

Integrated software support significantly reduces commissioning effort. Unified configuration tools, synchronized firmware updates, common communication interfaces, and centralized diagnostic software simplify installation, parameter tuning, troubleshooting, and long-term maintenance. Consequently, industrial robot manufacturers increasingly adopt standardized multi-axis motion platforms rather than combining unrelated motor drivers from multiple suppliers.

### 5.3 Selection Checklist for Omni Drive

---

A systematic selection checklist helps engineers ensure that every important design factor has been evaluated before finalizing an omnidirectional drivetrain. Because mechanical, electrical, thermal, and control subsystems interact closely, overlooking even one parameter may compromise overall vehicle performance despite satisfactory individual component specifications.

The selection process begins by clearly defining vehicle requirements. Total operating mass, payload capacity, maximum velocity, acceleration, climbing ability, duty cycle, operating environment, and positioning accuracy establish the fundamental performance targets. These requirements determine the required wheel torque, motor power, gearbox ratio, and battery capacity.

Mechanical compatibility should then be verified. Engineers confirm wheel diameter, gearbox mounting dimensions, shaft configuration, allowable radial and axial loading, bearing capacity, backlash, torsional stiffness, and structural integration. Adequate safety factors must be incorporated for fatigue loading, unexpected payload variations, and manufacturing tolerances.

Electrical compatibility requires equal attention. Supply voltage, continuous current, peak current, regenerative braking capability, power distribution architecture, connector ratings, electromagnetic compatibility, and protection circuits must satisfy both motor and driver specifications. Thermal analysis confirms that motors and drivers remain within allowable operating temperatures during continuous industrial duty.

Control system evaluation follows next. Encoder type, encoder resolution, communication protocol, synchronization capability, control frequency, current loop bandwidth, velocity loop performance, and trajectory generation should all satisfy application requirements. Compatibility with the primary robot controller and software framework must also be confirmed.

Reliability and maintenance considerations extend beyond initial performance. Expected bearing life, gearbox lifetime, motor insulation class, environmental sealing, vibration resistance, cable durability, spare part availability, diagnostic capability, firmware support, and vendor technical assistance all influence long-term ownership cost.

Validation testing completes the selection process. Engineers verify analytical calculations using prototype experiments including acceleration tests, continuous duty operation, thermal measurements, power consumption analysis, positioning accuracy evaluation, vibration assessment, and emergency stop testing. Any discrepancies between predicted and measured performance are incorporated into subsequent design refinements.

A comprehensive selection checklist transforms drivetrain design from a component purchasing exercise into a structured engineering methodology. By evaluating mechanical performance, electrical integration, control capability, efficiency, reliability, maintainability, and lifecycle cost simultaneously, engineers develop omnidirectional mobile robots capable of delivering stable, precise, and dependable operation throughout years of demanding industrial service.

### 5.1 옴니 드라이브를 위한 BLDC와 서보 모터 선정 (BLDC vs Servo Selection for Omni Drive)

---

### 5.2 4축 일체형 드라이버 구성 (Matched Four-Axis Driver Configuration)

---

### 5.3 옴니 드라이브 선정 체크리스트 (Selection Checklist for Omni Drive)
