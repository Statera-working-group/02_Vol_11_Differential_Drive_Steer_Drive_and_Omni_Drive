**Differential Drive & Steer Drive Engineering**

# Chapter 20 Steer Drive Motor Sizing

## 01 Drive motor sizing

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Torque Calculation Based on 1055 kg Total Moving Mass

[

]

[

]

[

]

[

]

[

]

[

]

[

]

---

Drive motor sizing begins with an accurate estimation of the traction torque required to move the vehicle under all expected operating conditions. Selecting a motor solely on the basis of maximum vehicle speed or rated power often results in either an oversized system with unnecessary cost and energy consumption or an undersized system that overheats and fails to deliver the required dynamic performance. Therefore, the sizing process starts by analyzing the total moving mass, vehicle acceleration, rolling resistance, gradeability, wheel geometry, drivetrain efficiency, and desired operating duty cycle. These parameters collectively determine the continuous and transient torque requirements of the propulsion system.

For a steer-drive autonomous mobile robot with a total moving mass of **1055 kg**, the moving mass includes the chassis, batteries, onboard computers, sensors, payload, wiring, protective structures, and all auxiliary equipment. Rather than considering only the payload capacity, engineers evaluate the gross vehicle mass because every kilogram contributes to inertial loading during acceleration and braking. The total mass also determines the normal force acting on each drive wheel, directly influencing available traction and tire-ground interaction.

The first component of the required traction force is the rolling resistance. Rolling resistance originates from tire deformation, bearing friction, gearbox losses, and small floor irregularities. It can be approximated by

F_{rr}=C_{rr}mg

where (C_{rr}) is the rolling resistance coefficient, (m) is the total moving mass, and (g) is gravitational acceleration. On smooth industrial concrete floors, the rolling resistance coefficient typically ranges from 0.01 to 0.03 depending on tire material and wheel construction. Although relatively small compared with acceleration forces, rolling resistance represents the dominant continuous load during constant-speed travel.

The second force component is the acceleration force required to achieve the desired vehicle dynamics. According to Newton\'s second law,

F_a=ma

where (a) denotes the required vehicle acceleration. Faster acceleration improves productivity by reducing travel time between workstations but significantly increases motor torque demand. Since industrial autonomous mobile robots prioritize smooth motion and payload stability over aggressive acceleration, moderate acceleration values are generally selected to minimize mechanical stress and energy consumption.

If the vehicle must operate on ramps, additional climbing force must also be included. The gravitational component acting along the slope is expressed as

F_g=mg\\sin\\theta

where (\\theta) represents the slope angle. Even relatively small industrial ramps substantially increase required drive torque because gravitational loading continuously opposes vehicle motion. Consequently, motor sizing must always consider the maximum expected operating gradient rather than only level-floor conditions.

The total traction force required at the wheels becomes

F_t=F_{rr}+F_a+F_g

Additional correction factors are often introduced to account for drivetrain inefficiencies, wheel slip, manufacturing tolerances, and safety margins. These engineering factors ensure that the propulsion system maintains sufficient torque reserve under real industrial operating conditions.

Wheel torque is calculated by multiplying the traction force by the effective wheel radius,

T_w=F_tr

where (r) denotes the wheel radius. This wheel torque represents the total mechanical torque required to propel the complete vehicle.

For a four-wheel steer-drive platform employing four independently driven wheels, the required wheel torque is distributed among the four drive modules. Assuming uniform load distribution,

T_{module}=\\frac{T_w}{4}

However, practical control systems rarely assume perfectly equal load sharing because dynamic load transfer occurs during acceleration, braking, and cornering. Individual wheel torque allocation algorithms continuously compensate for changing wheel loads to maximize traction while preventing wheel slip.

Gearbox efficiency also influences required motor torque. Because mechanical losses occur within gear meshes and bearings, the motor must generate slightly more torque than theoretically required at the wheel. Motor torque is therefore determined by

T_m=\\frac{T_{module}}{\\eta G}

where (G) denotes the gearbox reduction ratio and (\\eta) represents drivetrain efficiency.

Modern drive motor sizing increasingly employs dynamic simulation rather than relying solely on analytical calculations. Multibody vehicle models evaluate transient acceleration, steering maneuvers, wheel slip, regenerative braking, payload variation, and uneven floor conditions. These simulations generate realistic torque profiles throughout representative industrial duty cycles, allowing engineers to optimize motor selection while avoiding excessive oversizing.

The resulting torque calculation establishes the engineering foundation for every subsequent drivetrain design decision. Motor selection, gearbox sizing, battery capacity, inverter rating, thermal management, and control algorithms all depend upon accurately predicting the torque required to move the complete **1055 kg** vehicle safely, efficiently, and reliably under its intended industrial operating conditions.

### 1.2 Continuous Torque vs Peak Torque

---

One of the most important considerations in drive motor selection is distinguishing between continuous torque and peak torque. Although manufacturers often advertise motors using their maximum torque capability, industrial autonomous mobile robots spend the overwhelming majority of their operating time under continuous rather than peak loading conditions. Consequently, understanding the relationship between these two torque ratings is essential for selecting motors that provide both reliable long-term operation and sufficient dynamic performance.

Continuous torque represents the maximum mechanical torque that a motor can produce indefinitely without exceeding its allowable operating temperature. During continuous operation, electrical losses within the windings generate heat proportional to current, while iron losses and bearing friction contribute additional thermal loading. Thermal equilibrium is eventually established when heat generation equals heat dissipation. Continuous torque is therefore fundamentally limited by the motor\'s thermal design rather than its electromagnetic capability.

Peak torque, in contrast, represents the maximum torque that the motor can produce for a relatively short duration before excessive temperature rise occurs. Modern permanent magnet synchronous motors often achieve peak torque values approximately two to three times greater than their continuous ratings. This temporary overload capability enables rapid acceleration, obstacle negotiation, short-duration hill climbing, emergency maneuvering, and recovery from unexpected disturbances without permanently damaging the motor.

Industrial autonomous mobile robots rarely operate continuously at peak torque. Instead, a typical duty cycle consists of repeated acceleration, constant-speed travel, deceleration, precision positioning, waiting periods, and docking operations. During acceleration, motor torque briefly approaches peak values. Once cruising speed is achieved, required torque decreases substantially because only rolling resistance and minor drivetrain losses remain. Consequently, average thermal loading remains much closer to the continuous rating than the peak rating.

Motor thermal behavior is commonly represented using thermal time constants. Because motor windings require considerable time to heat and cool, short-duration overloads do not immediately produce excessive temperatures. This thermal inertia permits temporary operation above the continuous rating provided that sufficient cooling time follows each overload event. Advanced motor controllers continuously estimate winding temperature using electrical models and embedded thermal sensors, automatically limiting torque whenever safe operating temperatures are approached.

Duty cycle analysis therefore plays a central role in motor selection. Rather than selecting a motor capable of continuously delivering maximum acceleration torque, engineers calculate the root-mean-square (RMS) torque over the complete operating cycle. RMS torque accurately represents average thermal loading and therefore determines whether a motor can safely perform the intended application without overheating. If RMS torque remains below the continuous rating, short-duration peak torque events can generally be accommodated without difficulty.

Gearbox selection also influences the relationship between continuous and peak torque. High reduction ratios multiply available wheel torque, reducing motor torque requirements during heavy load conditions. However, gearboxes themselves possess continuous and peak torque ratings that must be coordinated with motor capabilities. Mechanical overload beyond gearbox limits may result in gear tooth fatigue, bearing damage, or premature wear even if the motor remains within its permissible operating range.

Battery and inverter design further affect peak torque capability. High peak motor currents require sufficient battery discharge capability, inverter current capacity, and low electrical resistance throughout the power distribution system. Voltage sag during heavy acceleration may reduce available motor torque despite adequate electromagnetic design. Consequently, electrical system sizing must support both continuous energy delivery and transient power demand.

Regenerative braking introduces an additional consideration. During deceleration, the drive motor functions as a generator, producing negative torque while returning electrical energy to the battery. The magnitude of regenerative torque may approach positive peak torque under aggressive braking conditions. Motor controllers therefore coordinate regenerative braking with mechanical braking systems to achieve smooth vehicle deceleration while remaining within both motor and battery limitations.

Modern drive control software continuously manages torque allocation based on vehicle operating conditions. Torque limits may be dynamically adjusted according to battery state of charge, motor temperature, gearbox temperature, traction conditions, payload weight, and steering configuration. Adaptive torque management improves both performance and component longevity by utilizing available peak capability only when necessary.

Proper understanding of continuous versus peak torque prevents one of the most common motor sizing errors. Selecting motors solely according to peak specifications frequently produces insufficient thermal capacity, whereas sizing entirely according to continuous torque may unnecessarily increase system cost and weight. Balanced engineering design carefully considers duty cycle, thermal behavior, transient overload requirements, and long-term reliability to achieve optimal propulsion performance.

### 1.3 Worked Example --- P750

To illustrate the complete motor sizing procedure, consider the conceptual design of the **P750** industrial steer-drive autonomous mobile robot. The P750 represents a medium-to-heavy-duty logistics platform employing four independently driven steer-drive modules designed for precision indoor material handling. The vehicle is assumed to have a total moving mass of approximately **1055 kg**, including chassis, batteries, onboard electronics, sensors, safety equipment, and rated payload.

The design objective is to achieve smooth autonomous operation with excellent positioning accuracy rather than maximizing vehicle speed. Target operating speed is selected within the typical industrial range of approximately five to eight kilometers per hour, balancing productivity, safety, and energy efficiency. Moderate acceleration is specified to minimize payload disturbance while maintaining acceptable transport cycle times.

Using the total moving mass, engineers first estimate rolling resistance, acceleration force, and any anticipated climbing requirements according to the previously established analytical equations. These forces are combined to determine the total traction force acting at the wheel-ground interface. Applying the effective wheel radius converts traction force into total wheel torque required for vehicle propulsion.

Because the P750 utilizes four independent drive modules, the calculated wheel torque is distributed among the four wheels under nominal loading conditions. Dynamic vehicle control software continuously modifies this distribution according to steering angle, wheel slip, payload location, and instantaneous vehicle dynamics. Individual drive modules therefore rarely operate under identical loading despite equal nominal torque allocation.

A planetary gearbox is selected to provide the required torque multiplication while maintaining high efficiency and compact dimensions. Gear reduction significantly lowers motor torque requirements while allowing the motor to operate within its preferred speed range. High drivetrain efficiency minimizes electrical energy consumption and reduces thermal loading during prolonged industrial operation.

Motor selection begins with RMS torque analysis across a representative industrial duty cycle. Vehicle simulation incorporates repeated acceleration, straight-line travel, steering maneuvers, docking sequences, waiting periods, and regenerative braking events. The resulting RMS torque determines the minimum continuous motor rating required for reliable long-term operation. Peak torque capability is then verified to ensure adequate performance during acceleration, obstacle negotiation, and emergency maneuvers.

Thermal simulation evaluates motor winding temperatures throughout continuous operation. Heat generation from copper losses, iron losses, and inverter operation is balanced against natural or forced cooling capacity. Embedded temperature sensors provide additional protection by allowing real-time torque derating whenever thermal limits are approached during operation.

Battery sizing is coordinated with propulsion requirements. High-capacity lithium iron phosphate batteries provide stable voltage during both continuous operation and transient peak current demand. Regenerative braking partially recovers kinetic energy during deceleration, improving overall vehicle efficiency while reducing brake wear.

The servo control architecture synchronizes all four drive motors using deterministic industrial Ethernet communication. Real-time control algorithms continuously coordinate steering angle, wheel speed, motor torque, and vehicle trajectory. Closed-loop feedback from encoders, inertial sensors, and localization systems ensures accurate motion control despite changing payload conditions or floor irregularities.

Safety margins are incorporated throughout the design process. Additional torque reserve compensates for drivetrain aging, tire wear, manufacturing tolerances, contamination, unexpected payload variation, and environmental uncertainty. Rather than operating continuously near maximum capability, the selected propulsion system maintains sufficient performance margin to ensure reliable operation throughout the expected service life.

The completed P750 sizing example demonstrates that successful drive motor selection extends far beyond choosing the largest available motor. Accurate estimation of vehicle dynamics, realistic duty cycle analysis, thermal evaluation, gearbox optimization, battery coordination, control integration, and safety margin allocation together produce a balanced propulsion system capable of moving a **1055 kg** industrial autonomous mobile robot efficiently, reliably, and with the positioning precision required for modern automated material handling applications.

### 1.1 총 이동 질량 1055kg 기준 토크 계산 (Torque Calculation Based on 1055kg Total Moving Mass)

[

]

[

]

[

]

[

]

[

]

[

]

[

]

---

F_{rr}=C_{rr}mg

F_a=ma

F_g=mg\\sin\\theta

F_t=F_{rr}+F_a+F_g

T_w=F_tr

T_{module}=\\frac{T_w}{4}

T_m=\\frac{T_{module}}{\\eta G}

### 1.2 연속 토크와 최대 토크의 비교 (Continuous Torque vs Peak Torque)

---

### 1.3 P750 설계 예제 (Worked Example -- P750)

## 02 Steering motor sizing

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Steering Resistance Torque Calculation

[

]

[

]

---

Steering motor sizing begins with an accurate estimation of the steering resistance torque that must be overcome under every expected operating condition. Unlike the drive motor, whose primary responsibility is generating propulsion force, the steering motor rotates the entire steer-drive assembly to the commanded orientation while supporting significant vertical loads and resisting friction generated throughout the steering mechanism. If the steering motor is undersized, the module may exhibit slow steering response, poor trajectory tracking, oscillatory behavior, or complete failure to achieve the desired steering angle under heavy payload conditions. Conversely, excessive oversizing increases cost, weight, inertia, electrical consumption, and packaging complexity without proportional performance improvement. Therefore, steering resistance torque calculation represents the foundation of steering motor selection.

The steering resistance originates from multiple mechanical sources acting simultaneously. The largest contributor is bearing friction within the steering axis. The steering bearing supports the full vertical wheel load while allowing continuous rotational motion. As the normal load increases with vehicle mass and payload, bearing rolling resistance also increases proportionally. High-capacity crossed roller bearings and tapered roller bearings generally exhibit excellent stiffness but require careful preload adjustment because excessive preload significantly increases steering torque requirements.

Another important source of steering resistance is tire-ground interaction. During steering motion, the wheel contact patch experiences lateral deformation before the wheel begins rolling in the new direction. This deformation generates a resisting moment commonly referred to as tire scrub torque. Tire scrub becomes particularly significant when steering occurs while the vehicle is stationary or moving at extremely low speed. Soft polyurethane wheels, solid rubber tires, and pneumatic tires each exhibit different scrub characteristics due to differences in contact patch geometry and material compliance. Consequently, steering motor sizing must consider the specific wheel material selected for the autonomous mobile robot.

The steering gearbox also contributes mechanical resistance through gear mesh friction, bearing losses, and lubricant viscosity. Planetary gearboxes, harmonic drives, and worm gear mechanisms each possess unique efficiency characteristics. Although harmonic drives provide excellent positioning accuracy with nearly zero backlash, their efficiency under certain operating conditions may be lower than that of planetary gearboxes, requiring additional steering motor torque to compensate for mechanical losses.

Cable routing introduces another resisting component. Steering modules contain power cables, encoder wiring, communication lines, brake wiring, and sensor harnesses that continuously bend and twist during steering motion. Even when optimized cable routing techniques are employed, flexible cables generate elastic restoring forces that oppose steering rotation. Slip ring designs largely eliminate this contribution, whereas conventional flexible cable loops require careful evaluation of cable stiffness throughout the full steering range.

External environmental conditions may further increase steering resistance. Dust contamination, corrosion, inadequate lubrication, seal friction, low-temperature grease viscosity, and manufacturing tolerances all contribute additional mechanical torque requirements beyond ideal theoretical calculations. Engineering practice therefore introduces appropriate safety factors to ensure reliable steering performance under worst-case industrial conditions.

The total steering resistance torque can be represented as the sum of all individual torque components,

T_{total}=T_{bearing}+T_{scrub}+T_{gear}+T_{cable}+T_{seal}+T_{external}

where each term represents the resisting torque generated by bearings, tire scrub, gearbox friction, cable deformation, seal friction, and environmental influences. Although individual values vary according to vehicle configuration, this equation provides a systematic framework for steering motor sizing.

During vehicle motion, steering resistance changes continuously. At moderate travel speeds, rolling motion reduces tire scrub torque because the wheel naturally aligns with the new steering direction while moving. Consequently, the highest steering resistance frequently occurs during stationary steering or precision docking operations, where wheels must rotate against nearly static ground contact. Steering motor selection must therefore be based on these worst-case conditions rather than average operating torque.

Dynamic steering introduces rotational inertia into the calculation. The steering motor must accelerate the entire rotating assembly, including the wheel, drive motor, gearbox, steering housing, brake, encoder, and associated structural components. The required acceleration torque is determined by

T_{acc}=J\\alpha

where (J) represents the rotational moment of inertia of the steering assembly and (\\alpha) denotes the required angular acceleration. Heavy-duty steer-drive modules may possess substantial rotational inertia, making acceleration torque comparable to frictional steering resistance during rapid steering maneuvers.

Finite element analysis and multibody dynamic simulation are increasingly employed to validate steering torque calculations. These digital engineering tools predict bearing deformation, structural compliance, tire contact behavior, gearbox loading, and steering dynamics under realistic industrial operating conditions. Prototype testing using torque sensors further verifies analytical predictions before production release.

Modern steering motor controllers also contribute to overcoming steering resistance through advanced control strategies. Current control loops, feedforward torque compensation, disturbance observers, and adaptive friction compensation continuously estimate changing resistance during operation. These algorithms reduce steady-state steering error while minimizing unnecessary motor current and improving energy efficiency.

Ultimately, steering resistance torque calculation integrates mechanical design, wheel-ground interaction, structural dynamics, drivetrain characteristics, environmental conditions, and control engineering into a unified design methodology. Accurate estimation of steering resistance ensures that the selected steering motor provides sufficient torque reserve for reliable operation while avoiding unnecessary oversizing, thereby achieving high steering precision, excellent responsiveness, long component life, and efficient energy utilization throughout the operational lifetime of the autonomous mobile robot.

### 2.2 Steering Response Speed Criteria

[

]

[

]

Steering response speed is one of the most important performance indicators of a steer-drive autonomous mobile robot because it directly influences vehicle maneuverability, path tracking accuracy, obstacle avoidance capability, and overall operational efficiency. While sufficient steering torque ensures that the wheel can reach its commanded orientation under heavy loading, steering response speed determines how rapidly that orientation can be achieved. Excessively slow steering results in trajectory deviation, delayed obstacle avoidance, longer maneuvering times, and degraded productivity. Conversely, steering systems that respond too aggressively may introduce vibration, overshoot, oscillation, and unnecessary mechanical stress. Consequently, steering motor sizing must achieve an appropriate balance between response speed, positioning accuracy, mechanical durability, and energy efficiency.

Steering response is commonly characterized by the time required for the steering module to rotate from one commanded angle to another. Typical industrial autonomous mobile robots require steering transitions between 90 degrees and 180 degrees during normal operation. Applications involving omnidirectional motion, crab steering, and zero-radius rotation frequently demand rapid transitions between these steering configurations without interrupting vehicle motion. Therefore, steering response requirements are established according to the intended operational mission rather than a single universal specification.

The steering motion profile generally consists of three sequential phases. During the initial phase, the steering motor accelerates the rotating assembly until the desired angular velocity is reached. In the second phase, the module rotates at approximately constant angular velocity. Finally, the controller smoothly decelerates the steering assembly to eliminate overshoot while achieving precise final positioning. Modern servo controllers generate these motion profiles automatically using trapezoidal or S-curve velocity trajectories that minimize mechanical shock while maintaining rapid response.

Angular velocity is determined by the steering motor speed and gearbox reduction ratio according to

\\omega_s=\\frac{\\omega_m}{G}

where (\\omega_s) denotes steering angular velocity, (\\omega_m) represents motor rotational speed, and (G) is the gearbox reduction ratio. Larger reduction ratios improve steering torque but reduce steering speed, whereas smaller reduction ratios increase response speed at the expense of available torque. Gearbox selection therefore requires careful optimization to satisfy both dynamic and static performance requirements.

Required steering response time also depends upon vehicle speed. During slow precision docking operations, relatively moderate steering response is acceptable because vehicle motion is carefully controlled and path deviations remain small. However, higher travel speeds require substantially faster steering corrections to maintain accurate trajectory tracking. If steering response lags behind vehicle motion, localization errors accumulate and path-following performance deteriorates. Consequently, steering bandwidth must increase as maximum vehicle speed increases.

Steering response is additionally influenced by the rotational inertia of the steering assembly. Larger wheels, heavier drive motors, high-capacity gearboxes, integrated brakes, and reinforced structural housings all increase rotational inertia. According to rotational dynamics,

T=J\\alpha

greater inertia requires proportionally greater steering torque to achieve the same angular acceleration. Consequently, steering motor selection and mechanical packaging must be optimized simultaneously rather than independently.

Closed-loop servo control significantly improves steering response characteristics. High-resolution absolute encoders continuously measure steering position, enabling proportional-integral-derivative controllers to correct positioning errors in real time. Advanced controllers additionally incorporate feedforward acceleration compensation, disturbance observers, friction estimation, and model-based predictive control to achieve both rapid response and excellent positioning stability.

Overshoot control represents another important design criterion. Reaching the commanded steering angle rapidly is insufficient if the module oscillates before stabilizing. Excessive overshoot increases positioning time, produces unnecessary mechanical wear, and reduces vehicle stability. Well-tuned servo systems therefore optimize damping characteristics to achieve critically damped or slightly overdamped responses that minimize settling time while eliminating oscillatory behavior.

Communication latency must also be considered in steering response evaluation. Industrial Ethernet networks such as EtherCAT provide deterministic communication with update periods measured in microseconds to milliseconds. Low-latency communication enables synchronized steering among all four wheel modules, which is essential for coordinated omnidirectional motion. Delayed communication may cause transient steering mismatch between wheels, degrading vehicle kinematic performance.

Industrial validation of steering response typically involves repeated steering step tests under varying payload conditions. Engineers measure rise time, settling time, overshoot, steady-state error, and repeatability while evaluating steering performance across the full operating temperature range. Dynamic path-following experiments further verify that steering response satisfies localization and navigation requirements under representative industrial operating conditions.

Steering response criteria must also consider long-term reliability. Continuously operating the steering motor at maximum acceleration may achieve impressive response times but substantially increases gearbox loading, bearing stress, motor heating, and electrical power consumption. Practical industrial designs therefore prioritize repeatable, stable, and thermally sustainable steering performance over absolute minimum response time.

Ultimately, steering response speed criteria integrate motor dynamics, gearbox design, structural inertia, servo control, communication systems, thermal behavior, and vehicle kinematics into a unified engineering framework. Proper optimization enables the steer-drive module to achieve rapid yet stable steering transitions, precise path tracking, reliable omnidirectional mobility, and long operational life while maintaining efficient energy consumption across a wide range of industrial automation applications.

### 2.1 조향 저항 토크 계산 (Steering Resistance Torque Calculation)

[

]

[

]

---

T_{total}=T_{bearing}+T_{scrub}+T_{gear}+T_{cable}+T_{seal}+T_{external}

T_{acc}=J\\alpha

### 2.2 조향 응답 속도 기준 (Steering Response Speed Criteria)

[

]

\\omega_s=\\frac{\\omega_m}{G}

$$T = J\alpha$$

## 03 Torque requirements

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Low-Speed High-Torque Requirements in Docking Zone

---

Precision docking is one of the most demanding operating modes for an industrial Autonomous Mobile Robot (AMR) because the vehicle must simultaneously achieve extremely accurate positioning, smooth motion, and stable control while operating at very low speeds. Unlike normal transportation where momentum assists vehicle motion, docking requires the drive system to generate sufficient traction torque under near-static conditions. Consequently, the drive motor operates in a region characterized by low rotational speed but high torque output. This operating condition fundamentally influences motor sizing, gearbox selection, inverter design, battery capability, and control strategy. Proper understanding of low-speed high-torque requirements is therefore essential for designing reliable steer-drive platforms capable of repeatable precision docking.

During precision docking, the vehicle typically approaches the target station at speeds below approximately 0.3 to 0.5 m/s. At these velocities, rolling momentum becomes negligible, and the propulsion system must actively overcome rolling resistance, drivetrain friction, bearing resistance, floor irregularities, and steering-induced tire scrub using motor torque alone. Since the available kinetic energy is extremely small, any unexpected increase in resistance immediately affects vehicle motion. The control system must therefore produce highly accurate torque commands while maintaining stable wheel rotation without oscillation or hesitation.

One of the most important characteristics of low-speed operation is the requirement for high starting torque. At the initiation of vehicle movement, static friction between the wheel and floor exceeds dynamic friction. The drive motor must generate sufficient breakaway torque to overcome this initial resistance smoothly without causing wheel slip or sudden acceleration. Permanent Magnet Synchronous Motors (PMSMs) combined with Field-Oriented Control (FOC) are particularly well suited for this application because they can provide nearly rated torque even at zero rotational speed while maintaining excellent current regulation and smooth torque production.

Precision docking also demands exceptional torque linearity. The relationship between commanded motor current and generated wheel torque must remain predictable throughout the low-speed operating range. Nonlinear torque characteristics introduce positioning errors because small current changes may produce disproportionately large or small vehicle movements. Modern servo drives therefore employ current feedback loops with high bandwidth, accurate motor parameter estimation, and torque feedforward compensation to maintain linear torque behavior even under varying load conditions.

Gearbox selection strongly influences low-speed torque capability. High reduction ratios multiply motor torque at the wheel while simultaneously reducing motor rotational speed requirements. Planetary gearboxes are widely adopted because they combine high torque density, compact dimensions, excellent efficiency, and relatively low backlash. Harmonic drives provide even lower backlash and superior positioning accuracy but may exhibit lower efficiency under continuous heavy loading. The gearbox must therefore be selected according to the balance among torque multiplication, efficiency, durability, and positioning performance required by the intended application.

Wheel-ground interaction becomes particularly significant inside docking zones. During final positioning, small steering corrections often occur while the vehicle is nearly stationary. Tire deformation generates additional rolling resistance and scrub torque that increase required drive torque. Floor contamination, expansion joints, epoxy coatings, or slight surface unevenness further modify traction conditions. Consequently, engineering safety margins are incorporated into torque calculations to ensure consistent docking performance under realistic industrial environments rather than ideal laboratory conditions.

Torque ripple is another important consideration during low-speed motion. Electromagnetic torque pulsations originating from motor cogging, inverter switching, or gearbox transmission error can produce undesirable micro-oscillations in vehicle motion. Such oscillations reduce positioning accuracy and increase docking time. High-resolution encoders, optimized current control algorithms, sinusoidal commutation, and precision gearbox manufacturing significantly reduce torque ripple, enabling smoother low-speed operation.

Battery performance also influences available docking torque. Although vehicle speed is low, instantaneous motor current may remain relatively high because torque rather than power dominates the operating condition. Battery internal resistance, voltage stability, and state of charge therefore directly affect available motor torque. Lithium Iron Phosphate (LFP) batteries are frequently selected because they provide stable voltage characteristics, long cycle life, and excellent continuous current capability suitable for repeated industrial docking operations.

Control software plays an equally important role. Instead of commanding velocity directly, many advanced docking controllers operate primarily in torque control mode during the final positioning phase. Position error is converted into desired traction force through closed-loop controllers, allowing smooth and precise motion without overshoot. Model Predictive Control (MPC), disturbance observers, adaptive friction compensation, and feedforward control further improve positioning performance by compensating for varying payloads, floor conditions, and drivetrain nonlinearities.

Thermal considerations remain relevant despite low operating speed. Because cooling effectiveness decreases at low motor speed while current remains relatively high, copper losses become dominant. Continuous docking cycles without sufficient cooling intervals may therefore increase motor winding temperature. Motor thermal models, embedded temperature sensors, and automatic current derating protect the propulsion system while maintaining acceptable docking performance.

Experimental validation typically includes repeated docking trials under varying payloads, battery states, floor materials, and environmental conditions. Engineers evaluate final positioning accuracy, docking time, torque utilization, current consumption, wheel slip, and repeatability over thousands of docking cycles. These tests confirm that the selected drive system provides sufficient low-speed torque reserve while maintaining stable motion throughout prolonged industrial operation.

Ultimately, low-speed high-torque operation represents one of the most critical design conditions for industrial steer-drive robots. Successful motor sizing requires simultaneous consideration of traction mechanics, gearbox characteristics, motor electromagnetic behavior, battery capability, thermal performance, control algorithms, and environmental variability. By optimizing these factors as a unified system, autonomous mobile robots achieve highly repeatable precision docking, smooth low-speed maneuvering, reliable operation, and long-term mechanical durability in demanding industrial environments.

### 3.2 Ramp Climbing Torque Calculation

[

]

[

]

[

]

[

]

[

]

[

]

[

]

Ramp climbing represents one of the highest continuous torque demands encountered by industrial Autonomous Mobile Robots because the propulsion system must overcome both rolling resistance and the gravitational component acting along the slope while maintaining stable vehicle motion and adequate traction. Unlike short-duration acceleration events, climbing a ramp may require elevated motor torque over an extended period, making continuous torque capability and thermal performance particularly important. Consequently, ramp climbing torque calculation forms an essential component of drive motor sizing, gearbox selection, battery design, and overall vehicle performance evaluation.

The fundamental force opposing uphill motion is the component of gravitational force acting parallel to the inclined surface. This force is expressed by

F_g = mg\\sin\\theta

where (m) represents the total moving mass of the vehicle, (g) denotes gravitational acceleration, and (\\theta) is the ramp inclination angle. As the ramp angle increases, the gravitational force opposing motion increases proportionally, requiring greater traction force from the drive wheels. Even relatively modest industrial ramps of only several degrees can substantially increase required drive torque for heavy autonomous mobile robots.

Rolling resistance remains present while climbing and must be added to the gravitational component. The rolling resistance force is calculated by

F_{rr}=C_{rr}mg\\cos\\theta

where (C_{rr}) is the rolling resistance coefficient. Although the cosine term changes only slightly for moderate ramp angles, rolling resistance remains a significant contributor to the total required traction force, particularly for heavy vehicles operating on soft or high-friction flooring materials.

If the vehicle accelerates while climbing, inertial force must also be included,

F_a=ma

where (a) denotes the desired acceleration. Therefore, the total required traction force becomes

F_t=F_g+F_{rr}+F_a

This equation represents the complete longitudinal force that must be generated at the wheel-ground interface. Additional engineering correction factors are generally introduced to account for drivetrain losses, wheel slip, manufacturing tolerances, payload uncertainty, and safety margins.

Wheel torque is then determined by multiplying the required traction force by the effective wheel radius,

T_w=F_tr

where (r) is the effective rolling radius of the wheel. For vehicles employing four independently driven steer-drive modules, the nominal wheel torque is distributed among the four wheels,

T_{module}=\\frac{T_w}{4}

Actual torque distribution, however, is continuously modified by the vehicle controller because weight transfer occurs during climbing. The uphill wheels and downhill wheels experience different normal forces depending upon vehicle geometry, center of gravity location, suspension compliance, and acceleration. Torque vectoring algorithms dynamically adjust individual wheel torque to maximize traction while preventing wheel slip.

Available traction must always exceed required climbing force. Maximum transmissible traction is determined by

F_{max}=\\mu N

where (\\mu) represents the tire-floor coefficient of friction and (N) denotes the normal force acting on the drive wheel. If the required climbing force exceeds available traction, wheel slip occurs regardless of motor torque capability. Consequently, ramp-climbing performance depends not only upon motor size but also upon tire material, wheel loading, surface condition, and weight distribution.

Gearbox selection plays a decisive role in climbing performance. Higher reduction ratios increase available wheel torque while reducing motor speed. Heavy-duty industrial robots frequently employ planetary gearboxes because they provide high torque multiplication with excellent efficiency and compact dimensions. Gearbox efficiency must nevertheless be included in motor torque calculations since mechanical losses reduce the torque transmitted to the wheels.

Continuous thermal loading becomes especially important during long ramp climbs. Because high motor current is maintained over an extended duration, copper losses dominate motor heating. Thermal equilibrium may eventually be reached at temperatures approaching motor limits if cooling capacity is insufficient. Motor sizing therefore relies primarily on continuous torque capability rather than peak torque for evaluating climbing performance. Embedded temperature sensors and thermal protection algorithms automatically reduce motor current whenever safe operating temperatures are approached.

Battery performance significantly influences sustained climbing capability. Climbing requires prolonged high current discharge, making battery voltage stability, internal resistance, and thermal behavior important design considerations. High-capacity Lithium Iron Phosphate battery systems provide stable voltage under continuous heavy loading while offering excellent thermal stability and long service life suitable for industrial applications.

Vehicle stability must also be evaluated during ramp operation. As the center of gravity shifts relative to the wheelbase, axle loading changes, affecting both steering performance and traction distribution. Structural analysis verifies that frame deflection remains acceptable under combined gravitational and payload loading, while multibody dynamic simulation predicts weight transfer, tire loading, and suspension behavior throughout the climbing maneuver.

Modern traction control systems continuously monitor wheel speeds, motor currents, encoder signals, and inertial measurements to detect incipient wheel slip. When excessive slip is identified, torque is redistributed among individual drive modules while motor current is adjusted to maintain stable climbing. Adaptive control algorithms further compensate for changing payloads, wet floors, dust contamination, or varying friction conditions, significantly improving climbing reliability.

Validation of ramp climbing performance typically includes repeated tests across multiple ramp angles, payload conditions, battery charge levels, and surface materials. Engineers evaluate maximum climbable gradient, continuous motor temperature, current consumption, wheel slip ratio, climbing speed, and recovery performance after stopping on an incline. These experiments confirm analytical calculations while identifying practical limitations associated with real industrial environments.

Ramp climbing torque calculation therefore integrates vehicle dynamics, gravitational loading, traction mechanics, drivetrain efficiency, thermal management, battery capability, and intelligent control into a unified engineering methodology. Accurate calculation ensures that the propulsion system provides sufficient continuous torque reserve for reliable operation on inclined surfaces while maintaining energy efficiency, component durability, and safe vehicle behavior throughout the full range of industrial operating conditions.

### 3.1 도킹 구역에서의 저속 고토크 요구사항 (Low-Speed High-Torque Requirements in Docking Zone)

---

### 3.2 경사로 등판 토크 계산 (Ramp Climbing Torque Calculation)

[

]

[

]

[

]

[

]

[

]

[

]

[

]

F_g = mg\\sin\\theta

F_{rr}=C_{rr}mg\\cos\\theta

F_a=ma

F_t=F_g+F_{rr}+F_a

T_w=F_tr

T_{module}=\\frac{T_w}{4}

F_{max}=\\mu N

## 04 Gearbox selection

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Drive Axis Reduction Ratio Selection

[

]

---

The selection of the drive axis reduction ratio is one of the most influential decisions in the mechanical design of a steer-drive autonomous mobile robot because it directly determines the relationship between motor speed, wheel speed, available wheel torque, vehicle acceleration, maximum travel speed, energy efficiency, and overall drivetrain durability. Although modern permanent magnet synchronous motors provide excellent torque density and high rotational speeds, their operating characteristics rarely match the requirements of direct wheel drive. Consequently, a gearbox is introduced to transform the motor\'s high-speed, relatively low-torque output into the low-speed, high-torque motion required at the wheels. Choosing the appropriate reduction ratio therefore becomes a multidimensional optimization problem that balances vehicle performance, mechanical reliability, efficiency, and control stability.

The primary function of the reduction gearbox is torque multiplication. The relationship between motor torque and wheel torque is approximately expressed as

T_w=T_m\\times G\\times \\eta

where (T_w) is the wheel torque, (T_m) is the motor torque, (G) is the gearbox reduction ratio, and (\\eta) represents gearbox efficiency. A larger reduction ratio increases available wheel torque while proportionally decreasing wheel rotational speed. Conversely, a smaller reduction ratio enables higher vehicle speed but reduces available traction torque. Consequently, the reduction ratio must be selected according to the intended operational mission rather than maximizing a single performance parameter.

Industrial autonomous mobile robots generally operate at relatively low vehicle speeds compared with passenger vehicles, but they frequently transport heavy payloads while maintaining precise positioning accuracy. Therefore, gearbox selection prioritizes continuous torque capability, low-speed controllability, and positioning repeatability over maximum vehicle speed. Warehousing robots, precision docking platforms, heavy material handling systems, and industrial inspection robots all require sufficient wheel torque to accelerate smoothly under full payload while maintaining stable motion during precision positioning.

Motor operating efficiency strongly influences gearbox selection. Electric motors exhibit maximum efficiency only within a specific speed and torque range defined by their efficiency map. Selecting an appropriate reduction ratio allows the motor to operate near this optimal region throughout the majority of the vehicle duty cycle. If the reduction ratio is excessively large, the motor may rotate at unnecessarily high speeds during normal operation, increasing iron losses and inverter switching losses. Conversely, if the ratio is too small, the motor may operate continuously at low speed and high current, increasing copper losses and reducing thermal efficiency.

Vehicle acceleration requirements also affect reduction ratio selection. High reduction ratios provide greater wheel torque and therefore improve initial acceleration and climbing capability. However, excessive torque multiplication may exceed available tire-floor traction, causing wheel slip rather than increased acceleration. Consequently, engineers simultaneously evaluate gearbox ratio, tire friction coefficient, vehicle mass distribution, and traction control strategy to ensure that available torque can be effectively transmitted to the ground.

Maximum travel speed establishes another important design constraint. The relationship between motor speed and vehicle speed is determined by wheel diameter and gearbox ratio. Given a fixed motor maximum rotational speed, increasing the reduction ratio proportionally reduces achievable vehicle speed. Therefore, gearbox selection begins by identifying the required maximum operating speed for the intended industrial application. Most indoor autonomous mobile robots prioritize safe operation within relatively moderate speed ranges, allowing higher reduction ratios that improve torque capability without compromising productivity.

Gearbox efficiency must also be considered because every mechanical transmission introduces power losses. Planetary gearboxes generally provide efficiencies exceeding ninety-five percent under appropriate operating conditions, making them highly suitable for industrial steer-drive platforms. Harmonic drives offer excellent positioning accuracy with minimal backlash but may exhibit somewhat lower efficiency under continuous heavy loading. Cycloidal reducers provide exceptional shock resistance and overload capability, although their mechanical characteristics differ from planetary systems. The optimal gearbox therefore depends upon the relative importance of efficiency, positioning accuracy, overload capacity, maintenance requirements, and manufacturing cost.

Backlash represents another significant consideration. Excessive gearbox backlash introduces positioning errors during direction reversal and reduces steering precision during autonomous navigation. High-quality planetary gearboxes minimize backlash through precision manufacturing and preload adjustment, while harmonic drives nearly eliminate backlash altogether. Applications requiring millimeter-level docking accuracy frequently prioritize low-backlash gearboxes despite their higher cost.

Thermal performance is closely related to gearbox ratio selection. Large reduction ratios increase torque transmitted through gear meshes and bearings, generating additional frictional heat. Gearbox lubrication, housing thermal conductivity, ambient temperature, and continuous duty cycle therefore influence long-term reliability. Thermal simulation and experimental testing verify that gearbox temperatures remain within acceptable operating limits throughout prolonged industrial operation.

Drive ratio selection increasingly relies on integrated simulation rather than isolated calculations. Vehicle dynamics models, motor efficiency maps, gearbox efficiency characteristics, battery performance, and representative duty cycles are evaluated simultaneously using system-level optimization tools. Engineers compare multiple reduction ratios while analyzing acceleration, climbing performance, continuous current consumption, thermal loading, energy efficiency, and productivity. The selected gearbox ratio therefore represents the best compromise among numerous interacting design objectives rather than the optimum for a single performance criterion.

Experimental validation completes the gearbox selection process. Prototype vehicles undergo acceleration testing, maximum speed evaluation, hill climbing experiments, endurance trials, precision docking verification, and energy consumption measurements under representative payload conditions. These tests confirm that the selected reduction ratio satisfies all operational requirements while maintaining acceptable temperatures, stable control behavior, and long mechanical service life.

Ultimately, drive axis reduction ratio selection is not simply a gearbox sizing exercise but a comprehensive systems engineering decision integrating motor characteristics, vehicle dynamics, drivetrain efficiency, thermal behavior, tire traction, positioning accuracy, and operational requirements. Properly optimized reduction ratios enable steer-drive autonomous mobile robots to achieve efficient propulsion, excellent low-speed controllability, high payload capability, reliable climbing performance, and long-term durability across a broad range of industrial automation applications.

### 4.2 Back-Drivability Requirements

Back-drivability is an important mechanical characteristic that describes the ability of an external force acting on the wheel to rotate the gearbox and motor in the reverse direction without active motor torque. Although frequently overlooked during initial drivetrain design, back-drivability significantly influences vehicle safety, manual maneuverability, energy efficiency, shock absorption, regenerative braking behavior, and emergency recovery procedures. Consequently, evaluating back-drivability requirements is an essential part of gearbox selection for industrial steer-drive autonomous mobile robots.

The degree of back-drivability depends primarily upon gearbox design, reduction ratio, internal friction, and transmission efficiency. Planetary gearboxes generally exhibit excellent back-drivability because of their rolling gear contacts and relatively high mechanical efficiency. Harmonic drives possess moderate back-drivability depending upon reduction ratio and internal flexspline deformation. Worm gear reducers, by contrast, often exhibit self-locking behavior that severely limits reverse power transmission. Cycloidal reducers typically occupy an intermediate position depending on their specific mechanical configuration.

One major advantage of good back-drivability is improved collision tolerance. When a moving vehicle unexpectedly encounters an obstacle, externally applied forces can partially rotate the drivetrain instead of being transmitted directly into gears, bearings, and structural components. This passive compliance reduces impact loads and decreases the probability of mechanical damage during accidental collisions. Combined with torque-controlled servo drives, back-drivable transmissions contribute to safer human-robot interaction by allowing controlled mechanical compliance during physical contact.

Manual movement during maintenance represents another important consideration. Industrial facilities occasionally require autonomous mobile robots to be repositioned manually following electrical failures, emergency shutdowns, or maintenance activities. Highly back-drivable gearboxes allow maintenance personnel to push or tow the vehicle with relatively modest force after releasing the parking brake. Poorly back-drivable or self-locking transmissions may require mechanical disengagement mechanisms or dedicated service procedures before manual movement becomes possible.

Back-drivability also enhances regenerative braking performance. During vehicle deceleration, kinetic energy flows backward through the drivetrain toward the electric motor, allowing the motor to function as a generator and recharge the battery. Efficient reverse power transmission increases regenerative braking efficiency while reducing mechanical brake wear and overall energy consumption. Gearboxes exhibiting high internal friction dissipate a larger fraction of this recoverable energy as heat rather than electrical power.

However, excessive back-drivability is not always desirable. On inclined surfaces, highly back-drivable transmissions may allow vehicle rollback when propulsion torque is removed. Industrial autonomous mobile robots therefore typically incorporate spring-applied electromagnetic holding brakes that mechanically lock the drivetrain whenever electrical power is unavailable. These brakes ensure stationary vehicle positioning regardless of gearbox back-drivability characteristics.

Servo control algorithms must also account for gearbox back-drivability. Low-friction transmissions respond rapidly to external disturbances, requiring active torque compensation to maintain accurate positioning. Modern motion controllers continuously estimate external loads using disturbance observers and current feedback, enabling precise position holding while preserving compliant behavior whenever appropriate. This combination of mechanical back-drivability and intelligent control provides both positioning accuracy and operational safety.

Gearbox efficiency and back-drivability are closely related but not identical. High mechanical efficiency generally improves reverse power transmission, although bearing preload, lubricant viscosity, seal friction, and manufacturing tolerances also influence actual back-drivable performance. Consequently, laboratory measurements often include reverse efficiency testing alongside conventional forward efficiency evaluation.

Heavy industrial payloads introduce additional engineering considerations. Vehicles transporting loads exceeding one metric ton possess substantial kinetic energy during motion. Excessively compliant drivetrains may produce oscillatory behavior during rapid load changes or precision positioning. Engineers therefore optimize gearbox reduction ratio, structural stiffness, motor current control, and holding brake characteristics to balance compliance with positional stability.

Functional safety requirements frequently specify vehicle behavior following electrical power loss. Emergency stop events, controller failures, and battery disconnection scenarios require predictable vehicle responses. Mechanical holding brakes, redundant braking systems, and monitored brake engagement ensure that back-drivable gearboxes do not compromise operational safety under abnormal conditions.

Simulation tools increasingly support quantitative evaluation of back-drivability. Multibody dynamic models incorporate gearbox friction, motor inertia, brake characteristics, tire compliance, and vehicle mass distribution to predict drivetrain behavior during manual pushing, collision events, regenerative braking, emergency stopping, and slope holding. Experimental verification subsequently measures required pushing force, regenerative efficiency, stopping distance, brake holding capability, and impact force transmission under representative industrial operating conditions.

Modern steer-drive platforms often employ adaptive control strategies that intentionally exploit gearbox back-drivability. During normal autonomous operation, the controller maintains high positioning stiffness for accurate navigation. During collaborative operation, manual guidance, or service procedures, control parameters may be modified to permit compliant human interaction while maintaining overall vehicle stability. This flexibility significantly enhances usability across diverse industrial applications.

Ultimately, back-drivability requirements extend well beyond gearbox mechanics alone. They integrate transmission design, motor control, braking systems, vehicle safety, energy recovery, maintenance strategy, and human-machine interaction into a unified engineering framework. Proper optimization enables steer-drive autonomous mobile robots to achieve efficient energy utilization, reliable emergency behavior, safe manual handling, improved collision tolerance, and high operational reliability while satisfying the demanding requirements of modern industrial automation.

### 4.1 구동축 감속비 선정 (Drive Axis Reduction Ratio Selection)

[

]

---

T_w=T_m\\times G\\times \\eta

### 4.2 역구동성 요구사항 (Back-Drivability Requirements)

## 05 Brake selection

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Holding Brake Capacity Calculation

[

]

[

]

[

]

[

]

---

A holding brake is one of the most important safety components in a steer-drive autonomous mobile robot because its primary purpose is not to decelerate a moving vehicle but to maintain a stationary position whenever propulsion torque is removed. During normal operation, vehicle motion is controlled primarily through the drive motors and regenerative braking. However, when the vehicle reaches its destination, stops on an inclined surface, experiences an emergency shutdown, or loses electrical power, the holding brake becomes solely responsible for preventing unintended vehicle movement. Consequently, proper brake capacity calculation is a critical aspect of drivetrain design, ensuring both operational safety and compliance with industrial functional safety requirements.

The sizing process begins by identifying the worst-case operating condition under which the brake must hold the vehicle. This condition is generally not level-ground parking but rather maximum payload positioned on the steepest allowable ramp while subjected to external disturbances such as vibration, slight impacts, or uneven floor conditions. Engineers therefore calculate the maximum gravitational force acting along the slope rather than relying only on vehicle weight.

The longitudinal force acting on an inclined surface is expressed by

F_g = mg\\sin\\theta

where (m) represents the total vehicle mass including payload, (g) is gravitational acceleration, and (\\theta) denotes the maximum design ramp angle. This force continuously attempts to move the vehicle downhill whenever propulsion torque is unavailable.

The required holding torque at the wheel is calculated by

T_w = F_g \\times r

where (r) is the effective wheel radius. For a four-wheel independently driven steer-drive platform, the required holding torque is distributed among the four drive modules under ideal load conditions.

T_{module}=\\frac{T_w}{4}

However, practical engineering never assumes perfectly equal load distribution. Weight transfer caused by payload location, chassis flexibility, manufacturing tolerances, and floor unevenness may cause one wheel to experience significantly greater loading than the others. Consequently, brake sizing incorporates safety factors to account for unequal load sharing and unexpected operating conditions.

Gearbox reduction ratio directly affects brake torque requirements. Since the holding brake is commonly mounted on the motor shaft rather than the wheel axle, the gearbox multiplies the available holding torque. The required motor-side brake torque can therefore be approximated by

T_b=\\frac{T_{module}}{G\\eta}

where (G) is the gearbox reduction ratio and (\\eta) represents gearbox efficiency. Higher reduction ratios reduce the brake torque required at the motor shaft, although gearbox back-drivability characteristics must also be considered.

Safety factors represent an essential element of brake sizing. External disturbances, tire deformation, lubricant aging, manufacturing tolerances, friction variation, and unexpected overload conditions may significantly increase required holding torque. Industrial practice therefore commonly applies safety margins ranging from approximately 1.5 to 2.5 depending upon application criticality and applicable safety standards.

Brake thermal behavior is generally less demanding than that of service braking because holding brakes primarily operate under static conditions. Nevertheless, repeated engagement and release cycles generate heat through frictional contact, particularly in automated production environments involving frequent start-stop operation. Engineers therefore verify allowable switching frequency, friction material wear, and thermal stability throughout the anticipated service life.

Brake engagement time also influences system performance. Rapid engagement minimizes vehicle rollback following emergency stop commands or electrical power failure. However, excessively abrupt engagement may introduce mechanical shock into the drivetrain. Brake response characteristics are therefore coordinated with motor current decay, regenerative braking control, and vehicle motion planning to achieve smooth yet reliable stopping behavior.

Functional safety requirements impose additional design constraints. Safety-rated braking systems must reliably hold the vehicle under single-fault conditions while providing diagnostic capability for brake monitoring. Many industrial platforms continuously supervise brake coil current, engagement status, release timing, and mechanical wear to detect degradation before operational safety is compromised.

Experimental validation includes static holding tests on maximum design slopes, repeated brake cycling, emergency stop evaluation, long-duration parking verification, and brake wear measurements under representative environmental conditions. These experiments confirm that calculated brake capacity remains adequate throughout the intended operational lifetime.

Ultimately, holding brake capacity calculation integrates vehicle mass, slope geometry, gearbox characteristics, wheel dimensions, safety margins, thermal behavior, and functional safety requirements into a unified engineering methodology. Proper brake sizing ensures that industrial autonomous mobile robots remain securely stationary under all foreseeable operating conditions while maintaining long-term reliability and regulatory compliance.

### 5.2 Spring-Applied Brake Selection

Among the various braking technologies used in industrial autonomous mobile robots, the spring-applied electromagnetic brake has become the preferred solution for holding applications because it inherently provides fail-safe operation. Unlike electrically actuated braking systems that require electrical power to generate braking force, a spring-applied brake remains mechanically engaged whenever electrical power is absent. Electrical energy is required only to release the brake during normal vehicle operation. This operating principle ensures that the vehicle automatically enters a safe stationary condition following power failure, emergency shutdown, controller malfunction, or cable disconnection without requiring any active control intervention.

The operating mechanism is relatively straightforward. Multiple compression springs generate an axial clamping force that presses friction plates together, producing sufficient braking torque to lock the motor shaft. When electrical current energizes the brake coil, an electromagnetic field overcomes the spring force and separates the friction surfaces, allowing unrestricted motor rotation. Because braking force is produced mechanically by the springs rather than electrically, holding capability remains available even under complete loss of electrical power.

Brake selection begins by determining the required holding torque calculated during the previous design stage. The selected brake must provide a rated static holding torque exceeding the calculated requirement while incorporating an appropriate engineering safety margin. Engineers generally avoid selecting brakes that continuously operate near their maximum rated capacity because friction material wear, manufacturing variation, contamination, and long-term aging gradually reduce available holding torque throughout the service life.

Mechanical integration strongly influences brake selection. Modern steer-drive modules typically integrate the spring-applied brake directly onto the rear shaft of the drive motor, minimizing packaging volume while allowing the gearbox to multiply holding torque at the wheel. Compact integrated motor-brake assemblies simplify manufacturing, reduce component count, improve reliability, and facilitate maintenance through modular replacement.

Brake response characteristics are also carefully evaluated. Release time determines how quickly the vehicle can begin moving after receiving a motion command, whereas engagement time influences stopping performance during emergency events. Fast release improves productivity by minimizing startup delays, while rapid engagement enhances safety by reducing rollback distance following power removal. Nevertheless, brake timing must be coordinated with motor current control to prevent mechanical shock or excessive drivetrain loading.

Brake wear represents another important engineering consideration. Every engagement and release cycle generates microscopic wear on the friction surfaces. Although holding brakes experience considerably lower wear than service brakes because they engage primarily after vehicle motion has ceased, high-cycle industrial applications may still accumulate hundreds of thousands of switching operations over the system lifetime. Friction material selection, surface hardness, spring design, and environmental sealing therefore significantly influence maintenance intervals and long-term reliability.

Environmental protection requirements vary according to application. Indoor manufacturing facilities generally require protection against dust and oil contamination, whereas outdoor autonomous vehicles additionally encounter moisture, mud, temperature extremes, and corrosive environments. Brake housings therefore frequently incorporate sealed construction, corrosion-resistant materials, and high ingress protection ratings to maintain consistent braking performance throughout extended industrial operation.

Electrical characteristics must also be compatible with the vehicle power architecture. Brake coil voltage, current consumption, switching energy, and transient response are coordinated with the onboard power distribution system. Suppression circuits are commonly incorporated to eliminate voltage spikes generated when brake coils are de-energized, thereby protecting motor controllers and other electronic equipment from electrical interference.

Noise and vibration become increasingly important in precision industrial environments. Poorly designed brake mechanisms may generate audible clicking, vibration, or impact loads during engagement. Optimized spring geometry, controlled magnetic flux distribution, and precision-manufactured friction interfaces significantly reduce acoustic noise while improving mechanical durability and user acceptance.

Functional safety standards require predictable brake performance under fault conditions. Brake monitoring systems continuously supervise coil continuity, engagement confirmation, release detection, and electrical diagnostics. Some safety architectures employ redundant braking systems or dual-channel monitoring to achieve higher safety integrity levels required by industrial automation standards.

Verification testing includes static torque measurement, repeated switching endurance, thermal cycling, humidity exposure, vibration testing, emergency stop evaluation, and long-term wear assessment. Engineers additionally verify reliable brake release across the full operating temperature range and under varying supply voltage conditions to ensure consistent performance throughout the vehicle\'s expected lifetime.

The selection of a spring-applied brake therefore extends beyond simply matching a torque rating. It requires simultaneous consideration of mechanical integration, electrical compatibility, thermal behavior, environmental protection, switching performance, durability, maintenance strategy, and functional safety. Through comprehensive optimization of these interacting factors, the spring-applied brake provides reliable fail-safe holding capability, minimizes maintenance requirements, and ensures that steer-drive autonomous mobile robots maintain safe stationary positioning under both normal operation and abnormal fault conditions throughout their operational life.

### 5.1 홀딩 브레이크 용량 계산 (Holding Brake Capacity Calculation)

[

]

[

]

[

]

[

]

F_g = mg\\sin\\theta

T_w = F_g \\times r

T_{module}=\\frac{T_w}{4}

T_b=\\frac{T_{module}}{G\\eta}

### 5.2 스프링 작동식 브레이크 선정 (Spring-Applied Brake Selection)
