**Differential Drive & Steer Drive Engineering**

# Chapter 09 Differential Drive Power & Electrical System

## 01 DC Bus Architecture

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

The DC bus architecture is one of the most fundamental elements in the electrical design of an Autonomous Mobile Robot (AMR). It serves as the primary power backbone that distributes electrical energy from the battery system to all major subsystems, including motor drives, onboard computers, sensors, communication modules, safety controllers, and auxiliary devices. A well-designed DC bus architecture directly influences system efficiency, reliability, thermal performance, safety, maintainability, and future scalability.

In modern industrial AMRs, the DC bus is typically implemented using either a 24V or 48V architecture. The selected voltage level affects cable sizing, power losses, current ratings, battery configuration, motor performance, and overall system cost. As robot payloads and power demands increase, the importance of selecting an appropriate DC bus voltage becomes increasingly significant.

The DC bus must support dynamic load conditions. During acceleration, braking, lifting operations, and high-speed navigation, current demand can vary rapidly. The electrical architecture must therefore accommodate transient peak loads without causing excessive voltage drops or instability. Proper bus design requires consideration of battery characteristics, cable resistance, motor driver requirements, protection mechanisms, and regenerative energy management.

Another critical function of the DC bus architecture is power segregation. Different subsystems often require different voltage levels and noise immunity characteristics. High-current motor drives generate switching noise that can interfere with sensitive sensors, communication interfaces, and computing systems. Consequently, power distribution strategies must ensure electrical isolation and stable voltage delivery throughout the robot.

As industrial robots become more sophisticated, onboard power consumption continues to increase. Modern AMRs may contain high-performance edge computers, AI accelerators, LiDAR sensors, multiple cameras, industrial Ethernet switches, and advanced communication systems. The DC bus architecture must therefore be designed not only for current requirements but also for future expansion.

The transition from traditional 24V systems toward 48V architectures reflects this trend. Higher voltage systems enable greater power transfer efficiency while reducing current-related losses. However, the optimal choice depends on payload class, system power requirements, safety considerations, regulatory requirements, and overall project objectives.

Understanding voltage selection, power distribution design, and motor driver sizing is essential for creating reliable and efficient robotic platforms. These considerations form the foundation of modern DC bus architecture and directly influence the performance and lifecycle cost of industrial AMRs.

---

### 1.1 24V vs 48V Selection Criteria

---

Selecting between a 24V and 48V DC bus architecture is one of the earliest and most important decisions in robot electrical system design. Although both voltage levels are widely used in industrial automation, they offer different advantages and limitations depending on application requirements.

Historically, 24V systems became the industrial standard because they provide a good balance between safety, simplicity, and component availability. A large ecosystem of sensors, PLCs, industrial I/O modules, safety devices, and communication equipment is designed around 24V operation. Consequently, low-power industrial robots often utilize a 24V architecture because integration is straightforward and component costs remain relatively low.

For small AMRs carrying payloads below approximately 100 kg to 200 kg, 24V systems are often entirely adequate. Motor power requirements remain modest, cable lengths are relatively short, and current levels remain manageable. Under these conditions, the simplicity of a 24V architecture may outweigh the benefits of higher voltages.

As power demand increases, however, the limitations of 24V become increasingly apparent. Electrical power is defined by the relationship:

Power = Voltage × Current

For a given power requirement, increasing voltage reduces the required current proportionally. A motor system consuming 2400 W requires approximately 100 A at 24V but only 50 A at 48V. This reduction in current significantly affects system design.

Lower current results in reduced cable losses. Since resistive power loss follows the relationship:

Power Loss = I²R

a reduction in current produces a disproportionately large reduction in energy loss. Halving current reduces cable heating losses by approximately four times. This improvement directly increases overall system efficiency.

Cable sizing also benefits from higher voltage operation. Lower current allows smaller conductor cross-sections while maintaining acceptable temperature rise and voltage drop characteristics. Reduced cable weight becomes especially important in mobile robotic platforms.

Motor performance often improves as well. Many modern servo drives and BLDC motor systems are optimized for 48V operation because higher voltage allows better dynamic response and greater peak power capability. Acceleration performance can therefore improve without increasing current requirements.

For industrial AMRs carrying payloads above approximately 300 kg to 500 kg, 48V architectures have become increasingly common. Heavy-duty systems frequently operate in the 48V range because total power demand may exceed several kilowatts during acceleration and climbing operations.

Safety considerations must also be evaluated. Both 24V and 48V are generally classified as low-voltage systems, but 48V introduces slightly higher arc energy and fault current considerations. Proper protection devices, insulation practices, and wiring standards remain essential.

In modern robotics, a practical rule of thumb is that 24V systems are appropriate for low-power platforms, while 48V systems become increasingly advantageous as payload, motor power, and onboard computing requirements grow. Consequently, most medium-duty and heavy-duty industrial AMRs now adopt 48V as their primary DC bus voltage.

### 1.2 Power Distribution Design

---

Power distribution design determines how electrical energy is delivered from the battery system to every subsystem within the robot. A well-designed distribution architecture ensures stable operation, minimizes voltage drops, improves fault isolation, and enhances overall system reliability.

The battery pack serves as the primary energy source. Power typically enters a central distribution unit where protection devices, contactors, current sensors, and emergency shutdown circuits are located. From this point, electrical power is distributed to major load categories through dedicated branches.

One of the most important design principles is separating high-power and low-power loads. Motor drives generate large current transients and switching noise that can affect sensitive electronics. Therefore, propulsion systems are usually isolated from computing systems, sensors, and communication devices through dedicated distribution paths.

Motor drivers generally receive power directly from the main DC bus through appropriately sized fuses and circuit breakers. These loads represent the largest power consumers and require conductors capable of handling substantial peak currents.

Computing systems often operate at lower voltages such as 24V, 19V, 12V, or even lower levels. DC-DC converters are used to derive these voltages from the main bus. High-efficiency isolated converters are commonly employed to improve electrical noise immunity.

Sensor networks typically require stable and clean power supplies. LiDAR systems, cameras, IMUs, GNSS receivers, industrial Ethernet switches, and wireless communication modules often share dedicated low-noise power rails. Voltage stability is particularly important because measurement accuracy can be affected by power fluctuations.

Redundancy considerations may also influence power distribution design. Safety-critical systems such as emergency stop controllers, safety PLCs, and brake release circuits may utilize independent power paths to ensure operation during partial system failures.

Grounding strategy is another critical consideration. Poor grounding practices can introduce electromagnetic interference, communication errors, and sensor instability. Star-ground configurations are frequently used to minimize ground loops and maintain signal integrity.

Voltage drop analysis must be performed during design. Long cable runs and high currents can create significant voltage losses. Engineers must verify that all subsystems receive adequate voltage under both nominal and peak-load conditions.

Modern AMRs frequently incorporate power monitoring systems that measure voltage, current, temperature, and energy consumption throughout the distribution network. These measurements support diagnostics, predictive maintenance, and energy management functions.

Effective power distribution design therefore extends beyond simply connecting components to a battery. It represents a comprehensive engineering process that directly impacts performance, reliability, safety, and maintainability.

### 1.3 Motor Driver Current Margin Calculation

---

Motor driver current margin calculation is essential for ensuring reliable robot operation under all expected operating conditions. Selecting a motor driver based solely on nominal motor current often leads to overheating, protection trips, reduced lifespan, or unexpected system failures.

Motor current requirements vary significantly during operation. While a motor may consume a relatively low average current during steady-state motion, transient conditions such as acceleration, braking, obstacle traversal, ramp climbing, and payload movement can generate substantially higher current demands.

The first step in driver sizing is determining the motor\'s continuous current requirement. Continuous current represents the average current that the motor can sustain indefinitely without exceeding thermal limits. This value provides the baseline for driver selection.

Peak current requirements must then be evaluated. Most industrial motors can briefly draw two to five times their continuous current during acceleration or high-load conditions. Servo motors often generate particularly high transient currents when rapid dynamic response is required.

A properly sized motor driver must support both continuous and peak current conditions. Selecting a driver with only minimal current headroom creates reliability risks because real-world operating conditions rarely match ideal laboratory assumptions.

Environmental conditions also influence current margin requirements. Elevated ambient temperatures reduce cooling effectiveness and increase thermal stress on electronic components. Industrial facilities may expose robots to temperatures significantly higher than standard laboratory conditions.

Payload variation represents another important factor. A robot designed for a nominal 300 kg payload may occasionally transport heavier loads or experience dynamic loading conditions that increase motor current demand. Current margins must accommodate these operational variations.

A common engineering practice is to size the motor driver continuous current rating approximately 20% to 50% above expected continuous motor current requirements. Peak current ratings are often selected with even larger safety margins depending on application dynamics.

For example, if a motor requires 30 A continuous current and 60 A peak current, a suitable driver might be rated for approximately 40 A continuous and 80 A peak operation. This margin improves reliability and reduces thermal stress.

Regenerative braking must also be considered. During deceleration, motors may return energy to the DC bus. The motor driver and power system must safely manage these regenerative currents without exceeding voltage limits.

Thermal modeling plays an increasingly important role in high-power AMRs. Heavy-duty robots may operate continuously for extended periods, causing sustained heating within motor drivers. Proper current margin selection helps maintain acceptable operating temperatures and extends component lifespan.

Current monitoring and diagnostics further improve system robustness. Modern motor drivers continuously monitor current consumption and provide protection functions such as overcurrent protection, short-circuit protection, thermal shutdown, and fault reporting.

Ultimately, current margin calculation is not simply a conservative design practice. It is a fundamental reliability engineering requirement that ensures the robot can operate safely and effectively under real-world conditions. Properly sized motor drivers contribute directly to system uptime, safety, efficiency, and long-term operational success.

### 1.1 24V 대 48V 선정 기준(24V vs 48V Selection Criteria)

---

Power = Voltage × Current

Power Loss = I²R

### 1.2 전력 분배 설계(Power Distribution Design)

---

### 1.3 모터 드라이버 전류 마진 계산(Motor Driver Current Margin Calculation)

## 02 Battery Capacity Calculation

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

Battery capacity calculation is one of the most critical engineering activities in the design of Autonomous Mobile Robots (AMRs). The battery system determines operating time, mission availability, charging frequency, vehicle weight, system cost, and overall productivity. A battery that is undersized may cause unexpected shutdowns and mission interruptions, while an oversized battery increases vehicle mass, cost, charging time, and energy inefficiency. Therefore, battery sizing must be based on a systematic evaluation of actual power consumption rather than rough estimations.

Modern AMRs contain many power-consuming subsystems. In addition to propulsion motors, robots may include onboard computers, AI accelerators, LiDAR sensors, cameras, industrial Ethernet switches, wireless communication modules, safety controllers, lighting systems, and auxiliary devices. Each subsystem contributes to the total energy demand, and their power consumption often varies dynamically throughout operation.

Battery capacity calculation begins with understanding how energy is consumed during a mission. Different operating modes such as standby, cruising, acceleration, docking, lifting, inspection, and charging preparation all have different power requirements. The overall battery size must be sufficient to support the expected mission duration while maintaining adequate reserve capacity for safety and battery longevity.

The chemistry of the battery also plays an important role. Different battery technologies provide different energy densities, cycle lives, charging characteristics, safety properties, and thermal behaviors. Lithium Iron Phosphate (LFP) and Nickel Manganese Cobalt (NMC) batteries are currently the two most widely used lithium-ion technologies in industrial mobile robots.

Another important consideration is battery aging. The nominal battery capacity available when the robot is new gradually decreases over time due to cycle aging and calendar aging. Engineers therefore include capacity margins to ensure acceptable operation throughout the battery's service life.

Environmental conditions further affect battery performance. Low temperatures reduce available capacity and increase internal resistance. High temperatures accelerate battery degradation. Duty cycle variations and unexpected operational demands also influence required energy reserves.

A properly designed battery system should therefore consider not only average power consumption but also peak loads, operating conditions, charging strategy, aging effects, and future expansion requirements. Accurate battery capacity calculation enables reliable operation, minimizes downtime, and optimizes total cost of ownership throughout the robot lifecycle.

---

### 2.1 Creating a Power Consumption Profile

---

The first step in battery capacity calculation is the development of a comprehensive power consumption profile. A power consumption profile represents the energy usage characteristics of all major subsystems during a typical operating cycle. Rather than assuming a single average power value, the profile captures variations in power demand across different operating modes.

Every AMR operates through multiple states. During standby mode, only essential electronics remain active, resulting in relatively low power consumption. During navigation, propulsion motors, sensors, and onboard computers become active simultaneously. Acceleration events require significantly more power than steady-state cruising. Additional functions such as lifting mechanisms, robotic arms, inspection equipment, or AI inference systems may further increase energy demand.

Propulsion typically represents the largest energy consumer. Motor power consumption depends on vehicle mass, payload, speed, acceleration, floor conditions, and route characteristics. A robot traveling at constant speed on a smooth floor may consume only a fraction of the power required during acceleration or hill climbing.

Computing systems have become increasingly important contributors to overall energy consumption. Traditional industrial PCs may consume between 20 W and 100 W, while modern AI-enabled edge computers equipped with GPUs can consume several hundred watts. For example, a high-performance edge computer containing an RTX-class GPU may consume 250 W to 600 W depending on workload.

Sensors also contribute significantly to total power demand. LiDAR sensors typically consume between 10 W and 50 W. Multiple cameras, depth sensors, IMUs, GNSS receivers, wireless communication systems, and industrial switches collectively add substantial power requirements.

To construct a power consumption profile, engineers identify all major subsystems and estimate their power usage under various operating conditions. Each subsystem is then assigned a duty cycle representing the percentage of time spent in each operating state.

For example, an AMR may spend 60% of its time cruising, 20% accelerating or decelerating, 10% docking, and 10% waiting or performing inspections. By multiplying subsystem power by operating duration, total energy consumption can be calculated more accurately than using simple averages.

Power logging measurements from prototype vehicles provide the most reliable data. Current sensors, battery monitoring systems, and onboard diagnostics can record actual power consumption during representative missions. These measurements help validate theoretical models and improve sizing accuracy.

Once the power profile has been established, engineers can determine average power consumption, peak power requirements, energy usage per mission, and battery capacity requirements. This profile becomes the foundation for all subsequent battery sizing calculations.

### 2.2 LFP vs NMC Battery Comparison

---

Battery chemistry selection significantly influences robot performance, operating cost, safety, and lifecycle economics. Among lithium-ion technologies, Lithium Iron Phosphate (LFP) and Nickel Manganese Cobalt (NMC) are the two most common choices for industrial AMRs.

LFP batteries are widely recognized for their exceptional safety characteristics. The lithium iron phosphate cathode chemistry exhibits excellent thermal stability and a significantly lower risk of thermal runaway compared with many alternative lithium-ion technologies. This safety advantage is particularly important in industrial environments where robots operate near personnel, equipment, and valuable infrastructure.

Cycle life represents another major advantage of LFP batteries. Industrial-grade LFP cells commonly achieve 3000 to 7000 charge-discharge cycles depending on operating conditions. Some high-quality cells exceed 8000 cycles. This extended lifespan reduces battery replacement frequency and lowers long-term operating costs.

LFP batteries also tolerate frequent charging and partial state-of-charge operation well. Opportunity charging strategies commonly used in warehouses and factories are therefore highly compatible with LFP chemistry.

The primary disadvantage of LFP technology is lower energy density. Typical LFP cells provide approximately 120 Wh/kg to 180 Wh/kg. As a result, an LFP battery pack is generally larger and heavier than an equivalent NMC pack providing the same energy capacity.

NMC batteries offer significantly higher energy density. Typical NMC cells achieve approximately 180 Wh/kg to 280 Wh/kg, enabling lighter and more compact battery systems. This advantage is particularly valuable in applications where vehicle weight, payload capacity, or packaging volume are critical constraints.

NMC batteries also generally provide higher peak power capability and better low-temperature performance. These characteristics make NMC attractive for high-performance applications requiring aggressive acceleration or extended operation in cold environments.

However, NMC batteries typically exhibit shorter cycle life than LFP batteries. Depending on operating conditions, cycle life commonly ranges from 1000 to 3000 cycles. Thermal management requirements are also generally more demanding due to lower thermal stability.

For industrial AMRs operating multiple shifts per day, lifecycle cost often becomes more important than maximum energy density. Consequently, many warehouse, manufacturing, and logistics robots increasingly utilize LFP batteries despite their larger size and weight.

In contrast, mobile platforms where weight and volume are dominant design constraints may favor NMC technology. Examples include outdoor autonomous vehicles, drones, and certain specialized mobile robotics applications.

Overall, LFP is often preferred for industrial AMRs due to its safety, durability, long cycle life, and lower total cost of ownership. NMC remains attractive when maximum energy density and reduced battery weight are primary objectives.

### 2.3 Capacity Calculation Example for 8-Hour Operation

---

An 8-hour operating requirement is one of the most common battery sizing targets in industrial AMR applications. A robot capable of operating for a full work shift without recharging provides maximum operational flexibility and simplifies fleet management.

Consider a representative industrial AMR operating with the following average power profile:

The propulsion system consumes approximately 450 W during normal operation. The onboard edge computer consumes approximately 250 W. Sensors including LiDAR, cameras, IMU, and communication equipment consume approximately 120 W. Auxiliary systems such as safety controllers, lighting, Ethernet switches, and cooling fans consume approximately 80 W.

The total average power consumption becomes:

Total Power = 450 W + 250 W + 120 W + 80 W

Total Power = 900 W

For an 8-hour mission:

Energy Requirement = Power × Time

Energy Requirement = 900 W × 8 h

Energy Requirement = 7200 Wh

This corresponds to:

7.2 kWh

However, the calculation cannot stop here because several correction factors must be included.

Battery systems should not be discharged completely. Most industrial lithium-ion systems operate within approximately 80% to 90% usable depth of discharge to improve battery life. Assuming 85% usable capacity:

Required Battery Capacity = 7200 Wh / 0.85

Required Battery Capacity ≈ 8470 Wh

Engineers typically include additional reserve capacity for aging, temperature effects, unexpected mission extensions, and future system upgrades. A reserve factor of approximately 15% to 25% is common.

Applying a 20% reserve:

Final Battery Capacity = 8470 Wh × 1.20

Final Battery Capacity ≈ 10,164 Wh

This value can be rounded to approximately:

10 kWh

If the robot utilizes a 48 V battery architecture:

Battery Capacity (Ah) = 10,000 Wh / 48 V

Battery Capacity ≈ 208 Ah

Therefore, a practical battery specification would be approximately:

48 V, 200--220 Ah LFP battery pack

For heavy-duty industrial AMRs carrying larger payloads or operating AI-intensive computing systems, battery capacities may increase to 15 kWh, 20 kWh, or even higher. Conversely, smaller indoor AMRs may operate successfully using battery packs below 5 kWh.

This example demonstrates that accurate battery sizing requires a detailed understanding of power consumption, operating duration, usable battery capacity, reserve margins, and future performance degradation. Properly performed capacity calculations ensure reliable operation while avoiding unnecessary battery cost and weight.

### 2.1 전력 소비 프로파일 작성(Creating a Power Consumption Profile)

---

### 2.2 LFP 대 NMC 배터리 비교(LFP vs NMC Battery Comparison)

---

### 2.3 8시간 운행 기준 용량 계산 예제(Capacity Calculation Example for 8-Hour Operation)

Edge Computer : 250W

Total Power

= 450W + 250W + 120W + 80W

= 900W

Energy = Power × Time

= 900W × 8h

= 7200Wh

7.2kWh

Required Capacity

= 7200Wh ÷ 0.85

Final Capacity

= 8470Wh × 1.20

10kWh

Battery Capacity (Ah)

= 10,000Wh ÷ 48V

48V

200\~220Ah

LFP Battery Pack

Edge Computer + RTX GPU

## 03 BMS and Charging

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

The Battery Management System (BMS) and charging system form the foundation of every modern Autonomous Mobile Robot (AMR). While the battery pack provides the electrical energy required for operation, the BMS ensures that this energy is used safely, efficiently, and reliably throughout the battery's lifecycle. Charging technology complements the BMS by restoring battery capacity while maintaining battery health and maximizing operational availability. Together, these two subsystems directly influence robot uptime, battery longevity, operational safety, maintenance cost, and overall fleet productivity.

Modern industrial AMRs typically utilize lithium-ion batteries, most commonly Lithium Iron Phosphate (LFP) or Nickel Manganese Cobalt (NMC) chemistries. These batteries require sophisticated electronic management because lithium-ion cells are sensitive to overcharging, over-discharging, excessive current, temperature extremes, and cell imbalance. Unlike traditional lead-acid batteries, lithium-ion batteries cannot be safely operated without continuous electronic supervision.

The BMS continuously monitors every battery cell and makes intelligent decisions regarding charging, discharging, balancing, and protection. It communicates with motor controllers, onboard computers, chargers, and fleet management systems to ensure safe operation under all conditions. Advanced BMS platforms also provide diagnostic information, predictive maintenance indicators, state-of-charge estimation, state-of-health analysis, and fault reporting.

Charging technology has evolved significantly as industrial automation has expanded. Instead of relying solely on overnight charging, many factories now employ opportunity charging, automatic charging stations, and intelligent charging schedules that allow robots to recharge during idle periods. This approach minimizes downtime while maintaining high fleet utilization.

Charging strategy must also consider battery chemistry. Different lithium-ion technologies require specific charging algorithms, voltage limits, current limits, and temperature compensation methods. Improper charging can significantly shorten battery life or even create safety hazards.

The integration of BMS, charger, battery, and fleet management software has therefore become a major design consideration in industrial robotics. A properly designed battery management and charging architecture not only improves safety but also extends battery lifetime, reduces operating costs, and increases overall system reliability. Understanding BMS functionality, CC-CV charging principles, and automatic charging infrastructure is therefore essential for designing modern industrial AMRs.

---

### 3.1 BMS Key Functions and Selection Criteria

---

The Battery Management System (BMS) is often referred to as the intelligence of the battery pack. While the battery stores electrical energy, the BMS continuously supervises battery operation to ensure safe, reliable, and efficient performance throughout the battery\'s service life.

The most fundamental responsibility of the BMS is cell voltage monitoring. A lithium-ion battery pack consists of multiple cells connected in series and parallel. Even cells manufactured in the same production batch gradually develop small differences in voltage, internal resistance, and capacity. Without continuous monitoring, these differences can accumulate and reduce overall battery performance.

Overcharge protection is one of the most critical safety functions. If any cell exceeds its maximum allowable voltage during charging, irreversible damage may occur. In severe cases, thermal runaway can develop, particularly in high-energy battery chemistries. The BMS therefore disconnects the charger or limits charging current whenever voltage limits are approached.

Over-discharge protection performs an equally important role. Excessive discharge can permanently damage lithium-ion cells and significantly reduce battery life. The BMS monitors individual cell voltages and disconnects loads before critical discharge levels are reached.

Current monitoring is another essential function. During acceleration, climbing, regenerative braking, or fault conditions, battery current may increase rapidly. The BMS measures both charging and discharging current and activates protection mechanisms whenever current exceeds safe operating limits.

Temperature monitoring is equally critical. Battery performance, charging capability, and safety all depend strongly on temperature. Multiple temperature sensors are distributed throughout the battery pack to detect abnormal heating. Charging may be restricted at low temperatures, while excessive temperatures trigger protective shutdowns to prevent damage.

Cell balancing significantly improves long-term battery performance. Small differences between individual cells gradually increase over repeated charge-discharge cycles. Active or passive balancing circuits redistribute energy or dissipate excess charge so that all cells remain at similar voltage levels. Balanced cells maximize usable capacity and extend battery lifetime.

Modern BMS platforms also estimate State of Charge (SOC) and State of Health (SOH). SOC indicates the remaining battery capacity available for operation, while SOH estimates battery aging and remaining useful life. These parameters are essential for fleet management, maintenance scheduling, and mission planning.

Communication capability has become an increasingly important selection criterion. Industrial BMS units commonly support CAN, CANopen, EtherCAT, RS-485, Modbus, or Ethernet interfaces, allowing integration with motor controllers, onboard computers, chargers, and fleet management software.

When selecting a BMS, engineers should evaluate voltage range, current rating, balancing capability, communication interfaces, protection functions, functional safety features, diagnostic capabilities, firmware flexibility, environmental protection, and compliance with industrial safety standards. A well-designed BMS not only protects the battery but also serves as a key component in the overall energy management architecture of the robot.

### 3.2 CC-CV Charging Protocol

---

The Constant Current -- Constant Voltage (CC-CV) charging protocol is the standard charging method used for nearly all modern lithium-ion battery systems. It provides an effective balance between charging speed, battery safety, and long-term battery life.

The charging process begins with the Constant Current (CC) phase. During this stage, the charger supplies a fixed charging current while battery voltage gradually increases. The charging current is typically selected according to battery specifications and thermal limitations. Because the battery can safely accept relatively high current when its state of charge is low, the CC phase restores a significant portion of battery capacity in a relatively short period.

As charging continues, battery voltage rises steadily until it reaches the predefined maximum charging voltage. For LFP batteries, this voltage is typically around 3.65 V per cell, while NMC batteries generally charge to approximately 4.2 V per cell. Exact values depend on cell manufacturer specifications.

Once the maximum charging voltage is reached, the charging process transitions into the Constant Voltage (CV) phase. During this stage, the charger maintains a fixed output voltage while charging current gradually decreases as the battery approaches full capacity.

The decreasing current during the CV phase is an important characteristic of lithium-ion charging. The battery naturally accepts less current as it becomes fully charged. Attempting to force higher current at this stage would generate excessive heat, accelerate battery aging, and potentially create safety risks.

Charging is typically terminated when current falls below a predetermined threshold, often between 3% and 10% of the initial charging current. At this point, the battery is considered fully charged.

The BMS continuously supervises the CC-CV process. It verifies cell voltages, temperatures, charging current, insulation status, and communication with the charger. If any abnormal condition occurs, the BMS immediately modifies charging parameters or disconnects the charging circuit.

Temperature compensation is another important consideration. Lithium-ion batteries should generally not be charged at very low temperatures because lithium plating may occur inside the cells, permanently reducing battery capacity. The BMS therefore limits or completely disables charging outside specified temperature ranges.

Fast charging strategies remain compatible with CC-CV principles but employ higher charging currents during the CC phase. However, higher charging rates increase thermal stress and may shorten battery lifespan unless appropriate cooling systems are implemented.

For industrial AMRs, CC-CV charging provides excellent reliability, predictable charging behavior, and broad compatibility with commercial battery systems. It remains the preferred charging protocol because of its simplicity, safety, and proven long-term performance.

### 3.3 Auto Charging Station Basics

---

Automatic charging stations have become an essential component of modern industrial AMR fleets. Rather than relying on manual battery replacement or scheduled overnight charging, robots can autonomously recharge whenever battery levels become low or operational schedules permit.

The primary objective of an automatic charging station is to maximize robot availability while minimizing human intervention. By allowing robots to recharge during idle periods, opportunity charging strategies significantly increase overall fleet productivity.

The docking process begins with navigation toward the charging station. Using LiDAR localization, visual markers, reflector targets, QR codes, or AprilTags, the robot approaches the charging location with progressively increasing positioning accuracy.

During the final docking stage, dedicated alignment sensors often provide precise relative positioning. Vision systems, infrared sensors, laser alignment devices, or mechanical guidance structures ensure accurate connector engagement.

Charging stations generally employ either contact-based or contactless charging technologies.

Contact-based systems use conductive charging terminals that physically connect to the robot. Spring-loaded charging pins, conductive rails, or docking contacts provide efficient power transfer with relatively low energy loss. These systems are currently the most widely used in industrial environments because of their simplicity, efficiency, and relatively low cost.

Wireless charging systems transfer energy through inductive coupling without physical electrical contacts. Because no exposed conductors exist, maintenance requirements may be reduced. However, wireless charging generally exhibits lower efficiency, slower charging speed, higher equipment cost, and tighter alignment requirements.

The charging station communicates continuously with both the robot and the BMS throughout the charging process. Authentication, battery identification, charging authorization, voltage verification, and safety checks are completed before charging current is applied.

Fleet management software often coordinates charging schedules across multiple robots. Rather than allowing every robot to charge simultaneously, intelligent scheduling algorithms distribute charging events to avoid electrical overload while maintaining sufficient operational capacity.

Safety mechanisms are incorporated throughout the charging process. Emergency stop circuits, insulation monitoring, connector status detection, overcurrent protection, temperature monitoring, and communication fault detection ensure safe operation under industrial conditions.

Modern charging stations also collect operational data including charging duration, transferred energy, charging efficiency, battery health trends, connector wear, and charging cycle history. These data support predictive maintenance and long-term fleet optimization.

For industrial AMRs operating continuously across multiple shifts, automatic charging stations have become far more than simple battery chargers. They represent intelligent energy management infrastructure that integrates battery technology, robotics, fleet management, and industrial automation into a unified operational ecosystem. Properly designed automatic charging systems improve uptime, reduce labor requirements, extend battery life, and maximize the economic performance of autonomous mobile robot fleets.

### 3.1 BMS 핵심 기능 및 선정 기준(BMS Key Functions and Selection Criteria)

---

### 3.2 CC-CV 충전 프로토콜(CC-CV Charging Protocol)

---

### 3.3 자동 충전 스테이션 기초(Auto Charging Station Basics)

## 04 Thermal Management

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

Thermal management is one of the most important engineering disciplines in the design of modern Autonomous Mobile Robots (AMRs). As robots become more powerful and incorporate larger propulsion systems, high-performance edge computers, AI accelerators, and high-capacity lithium-ion batteries, heat generation has become a limiting factor for performance, reliability, safety, and component lifetime. An effective thermal management strategy ensures that every subsystem operates within its specified temperature range while maintaining maximum efficiency and long-term durability.

Heat is generated throughout an AMR during normal operation. Electric motors produce heat due to copper losses, iron losses, friction, and mechanical loading. Motor drivers generate switching losses and conduction losses through power semiconductors. Batteries generate internal heat during charging, discharging, and regenerative braking due to internal resistance and electrochemical reactions. High-performance processors and GPUs further contribute significant thermal loads during AI inference and perception tasks.

Excessive temperature affects nearly every aspect of robot performance. Elevated motor temperatures reduce insulation life and increase winding resistance. Power electronics experience lower efficiency and accelerated aging. Lithium-ion batteries suffer capacity degradation, increased internal resistance, and reduced cycle life when exposed to high temperatures. Conversely, extremely low temperatures also reduce battery performance and charging capability.

Thermal management therefore extends beyond simple cooling. Engineers must understand how heat is generated, transferred, stored, and dissipated throughout the robot. Thermal design involves conduction, convection, radiation, airflow optimization, heatsink design, enclosure layout, cooling system selection, thermal interface materials, and intelligent temperature monitoring.

Modern industrial AMRs increasingly integrate thermal simulation into the design process using computational fluid dynamics (CFD) and finite element analysis (FEA). These simulations predict temperature distributions before hardware prototypes are built, reducing development time and improving design quality.

Effective thermal management improves system reliability, reduces maintenance costs, extends component lifetime, enables higher continuous power output, and ensures safe operation under demanding industrial conditions. Understanding motor thermal behavior, driver cooling design, and battery temperature management is therefore essential for developing high-performance industrial robotic platforms.

---

### 4.1 Motor Thermal Model

---

The thermal behavior of an electric motor is a fundamental consideration in AMR design because motor temperature directly influences efficiency, torque capability, insulation lifetime, and overall system reliability. A motor thermal model provides engineers with a mathematical representation of how heat is generated, stored, and dissipated during operation, enabling accurate prediction of motor temperature under various load conditions.

Heat generation within a motor originates from several mechanisms. Copper loss is typically the dominant source and is proportional to the square of the winding current according to the relationship (P_{cu}=I\^2R). During acceleration or heavy-load operation, current increases significantly, causing rapid heat generation within the stator windings.

Iron losses represent another major heat source. These losses consist of hysteresis loss and eddy current loss within the magnetic core. Unlike copper losses, iron losses depend primarily on motor speed and magnetic flux. At higher rotational speeds, iron losses become increasingly significant even when motor torque remains relatively low.

Mechanical losses also contribute to motor heating. Bearing friction, seal friction, and windage losses generated by rotor rotation convert mechanical energy into heat. Although these losses are generally smaller than copper and iron losses, they become more noticeable during continuous high-speed operation.

The thermal model treats the motor as a network of thermal resistances and thermal capacitances. Thermal resistance describes the difficulty of transferring heat from one component to another, while thermal capacitance represents the amount of heat energy that can be stored before temperature rises significantly. Together, these parameters determine how quickly motor temperature responds to changing operating conditions.

Motor temperature does not increase instantaneously. Due to thermal inertia, temperature rises gradually according to the thermal time constant. A motor may safely deliver peak torque for several seconds because internal temperature requires time to reach critical levels. This characteristic allows temporary overload operation while preventing continuous overheating.

Ambient conditions strongly influence motor thermal performance. High surrounding temperatures reduce cooling effectiveness because the temperature difference between the motor surface and the environment decreases. Poor ventilation, enclosed compartments, or exposure to direct sunlight can further increase operating temperature.

Cooling methods vary according to application requirements. Small AMRs often rely on natural convection, while larger industrial robots may employ forced-air cooling or liquid cooling. Proper airflow design around the motor significantly improves heat dissipation without increasing system complexity.

Modern servo drives frequently incorporate thermal models directly into their control algorithms. Rather than relying solely on temperature sensors, the controller continuously estimates winding temperature based on current, speed, ambient conditions, and accumulated thermal energy. Torque output can then be limited proactively before thermal damage occurs.

An accurate motor thermal model enables engineers to optimize motor selection, predict overload capability, improve cooling design, reduce unnecessary safety margins, and maximize continuous power output while maintaining long-term reliability.

### 4.2 Driver Heat Dissipation Design

---

Motor drivers convert electrical energy from the DC bus into precisely controlled power for the propulsion motors. Although modern power electronics achieve very high efficiencies, typically exceeding 95%, the remaining energy is converted into heat. In high-power industrial AMRs, even a small percentage of power loss can generate substantial thermal loads that must be effectively managed.

Heat within a motor driver originates primarily from semiconductor switching devices such as MOSFETs, IGBTs, or silicon carbide (SiC) transistors. Two principal loss mechanisms dominate: conduction loss and switching loss. Conduction loss occurs whenever current flows through the semiconductor, while switching loss occurs during each transition between the ON and OFF states. Higher switching frequencies generally improve motor current quality but also increase switching losses.

Gate driver circuits, current sensors, DC-link capacitors, magnetic components, and protection circuitry also contribute to heat generation. Although individually smaller than semiconductor losses, their combined thermal contribution can be significant during continuous operation.

Effective heatsink design forms the foundation of driver cooling. The heatsink increases the available surface area for heat transfer from power semiconductors to the surrounding air. Material selection is important because aluminum provides an excellent balance between thermal conductivity, weight, manufacturability, and cost, while copper offers superior thermal performance at higher weight and cost.

Thermal interface materials (TIMs) play a critical role by minimizing contact resistance between semiconductor packages and the heatsink. High-quality thermal grease, phase-change materials, or thermal pads improve heat transfer efficiency by filling microscopic air gaps between mating surfaces.

Airflow management significantly influences cooling performance. Natural convection may be sufficient for low-power systems, but medium-duty and heavy-duty AMRs frequently require forced-air cooling using axial or centrifugal fans. Proper airflow paths should direct cool air across the hottest components while minimizing recirculation of heated air.

Enclosure design also affects driver temperature. Poor internal layout can trap hot air around power electronics, reducing cooling effectiveness. Engineers should separate high-power components from heat-sensitive electronics and provide adequate ventilation openings where environmental conditions permit.

Thermal monitoring is essential for safe operation. Temperature sensors positioned near power semiconductors and heatsinks continuously monitor operating conditions. When temperatures approach specified limits, the driver may reduce output current, decrease switching frequency, activate additional cooling, or perform controlled shutdown to prevent damage.

In high-power industrial robots, liquid cooling is becoming increasingly common. Liquid cooling systems circulate coolant through cold plates attached to the driver modules, providing much higher heat transfer capability than air cooling. Although more complex, liquid cooling enables higher continuous power density and improved thermal stability.

Comprehensive driver heat dissipation design therefore combines efficient power electronics, optimized heatsinks, appropriate cooling methods, intelligent thermal monitoring, and careful mechanical integration to ensure reliable long-term operation.

### 4.3 Battery Thermal Management

---

Battery thermal management is one of the most critical aspects of lithium-ion battery system design because battery performance, safety, charging capability, and service life are all highly dependent on operating temperature. Maintaining batteries within their recommended temperature range is essential for achieving reliable and economical AMR operation.

Heat generation within lithium-ion batteries occurs primarily due to internal resistance during charging and discharging. As current flows through the battery, electrical energy is partially converted into heat according to Joule heating principles. High current during acceleration, regenerative braking, or fast charging can substantially increase heat generation.

Electrochemical reactions also contribute to battery temperature. These reactions vary depending on battery chemistry, state of charge, current level, and operating temperature. As battery temperature rises, reaction rates accelerate, which may further increase heat generation under certain conditions.

Excessively high temperatures have several negative consequences. Battery aging accelerates rapidly because elevated temperatures increase electrolyte degradation, electrode decomposition, and side reactions within the cells. Internal resistance may initially decrease, but long-term capacity loss becomes significantly greater. Continuous operation above recommended temperatures can dramatically shorten battery cycle life.

Very low temperatures present different challenges. Battery internal resistance increases, reducing available power output and usable capacity. Charging lithium-ion batteries at low temperatures may cause lithium plating on the anode surface, permanently reducing battery performance and creating potential safety hazards.

Battery thermal management systems therefore aim to maintain cell temperatures within an optimal operating window while minimizing temperature differences between individual cells. Uniform cell temperature improves balancing effectiveness, capacity utilization, and overall battery longevity.

Passive thermal management relies on thermal conduction, enclosure design, insulation materials, and natural convection to regulate battery temperature. This approach is simple, lightweight, and cost-effective, making it suitable for many indoor industrial AMRs operating under moderate environmental conditions.

Active thermal management provides greater temperature control. Forced-air cooling circulates air through battery compartments, while liquid cooling systems transfer heat using coolant channels integrated into battery modules. Phase-change materials may also be used to absorb transient heat loads during high-power operation.

The BMS continuously monitors battery temperatures using multiple sensors distributed throughout the pack. If temperatures exceed safe limits, charging current may be reduced, discharge power limited, cooling systems activated, or emergency shutdown initiated.

Battery thermal management becomes increasingly important for high-capacity battery packs above approximately 10 kWh, fast-charging systems, outdoor autonomous robots, and robots operating continuously across multiple shifts. Under these demanding conditions, advanced thermal design significantly improves battery safety, extends cycle life, and increases operational reliability.

Ultimately, battery thermal management is not merely a cooling problem but an integrated engineering discipline combining electrochemistry, heat transfer, control systems, and mechanical design. Proper thermal management enables lithium-ion batteries to deliver their full performance while maintaining safety and maximizing economic value throughout the robot\'s operational lifetime.

### 4.1 모터 열 모델(Motor Thermal Model)

---

**Pcu = I²R**

### 4.2 드라이버 방열 설계(Driver Heat Dissipation Design)

---

### 4.3 배터리 열 관리(Battery Thermal Management)

## 05 Wiring and Protection

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

Electrical wiring and protection form the foundation of a safe, reliable, and maintainable Autonomous Mobile Robot (AMR). While batteries, motor controllers, sensors, and onboard computers often receive the most attention during system design, the wiring infrastructure that interconnects these components is equally important. An improperly designed wiring system can cause excessive voltage drop, overheating, electromagnetic interference (EMI), unexpected shutdowns, equipment damage, or even fire hazards. Therefore, wiring and protection should be considered as integral engineering disciplines rather than simple electrical connections.

Modern industrial AMRs contain numerous electrical subsystems operating simultaneously. High-current propulsion motors, servo drives, battery management systems (BMS), industrial computers, AI accelerators, cameras, LiDAR sensors, communication devices, safety controllers, and auxiliary equipment all share the same electrical platform. Each subsystem has different voltage requirements, current characteristics, protection needs, and sensitivity to electrical noise. Consequently, wiring architecture must be carefully designed to satisfy the electrical and mechanical requirements of every subsystem.

A complete wiring system includes power cables, communication cables, grounding conductors, connectors, protection devices, cable routing structures, strain relief mechanisms, shielding, and environmental protection. Each element contributes to overall system reliability. Proper conductor sizing minimizes resistive losses and voltage drop. Appropriate protection devices isolate electrical faults before damage propagates throughout the system. Effective grounding reduces electromagnetic interference while improving measurement accuracy and communication stability.

Industrial robots also operate under demanding mechanical environments. Continuous vibration, repetitive motion, shock loading, temperature variation, humidity, dust, and chemical exposure all influence cable lifetime. Therefore, cable selection must consider not only electrical performance but also mechanical durability and environmental resistance.

Protection strategies must accommodate both normal operating conditions and abnormal fault conditions. Short circuits, overloads, insulation failures, connector damage, motor stalls, regenerative current surges, and battery faults should all be anticipated during design. Protection devices must respond rapidly enough to prevent damage while avoiding nuisance trips during normal transient events such as motor startup.

Modern AMRs increasingly employ distributed electrical architectures in which multiple intelligent controllers communicate through industrial Ethernet or fieldbus networks. This architecture requires careful separation of power wiring and communication wiring to minimize electromagnetic coupling and maintain signal integrity.

Ultimately, proper wiring and protection design improves safety, reduces maintenance requirements, simplifies troubleshooting, increases system uptime, and extends component lifetime. Cable sizing, protection device selection, and grounding design therefore represent essential engineering tasks in every industrial robotic platform.

---

### 5.1 Cable Cross Section Selection Criteria

---

Selecting the appropriate cable cross-sectional area is one of the most fundamental electrical design decisions in an AMR. Although cables may appear to be simple components, their dimensions directly influence voltage drop, energy efficiency, thermal performance, reliability, installation flexibility, and long-term operating cost.

The primary purpose of a conductor is to transfer electrical power while minimizing energy loss. Every conductor possesses electrical resistance, and this resistance causes voltage drop and heat generation whenever current flows. As current increases, resistive heating follows the relationship:

**Power Loss = I²R**

This equation demonstrates that heat generation increases with the square of current. Consequently, undersized conductors may experience excessive temperature rise even when voltage drop appears acceptable.

The first step in cable sizing is determining the maximum continuous current expected during normal operation. Engineers must consider not only average operating current but also transient conditions such as acceleration, hill climbing, regenerative braking, lifting operations, and simultaneous subsystem activation.

Voltage drop is another critical consideration. Excessive voltage drop reduces motor performance, decreases driver efficiency, affects sensor accuracy, and may cause onboard computers or communication devices to reset unexpectedly. Most industrial designs attempt to limit voltage drop to approximately 2% to 5% of the supply voltage, depending on application requirements.

Cable length significantly influences conductor selection. Longer cable runs exhibit higher resistance, requiring larger conductor cross-sections even when current remains unchanged. Mobile robots with distributed electrical architectures often contain multiple cable lengths that must be individually evaluated.

Ambient temperature also affects cable current capacity. Conductors installed in enclosed compartments or near heat-generating components experience reduced cooling capability. Elevated temperatures reduce allowable current ratings because insulation materials have specified maximum operating temperatures.

Mechanical flexibility represents another important design criterion. Repeated bending within moving cable carriers or articulated robotic mechanisms requires finely stranded conductors specifically designed for continuous flex applications. Standard industrial wiring may fail prematurely under repeated bending cycles.

Environmental protection must also be considered. Outdoor robots require cables resistant to moisture, ultraviolet radiation, oil, chemicals, abrasion, and temperature extremes. Industrial facilities may additionally require flame-retardant or halogen-free insulation materials depending on applicable safety regulations.

Shielded cables are commonly employed for encoder signals, communication networks, and sensitive sensor interfaces. Shielding minimizes electromagnetic interference generated by high-current motor cables and switching power electronics.

A practical engineering approach combines current capacity calculations, voltage drop analysis, thermal evaluation, mechanical durability assessment, and environmental considerations. Proper conductor selection minimizes energy loss while ensuring long-term reliability under all expected operating conditions.

### 5.2 Fuse and Circuit Breaker Selection

---

Electrical protection devices safeguard both equipment and personnel by interrupting abnormal fault currents before permanent damage occurs. Among the most commonly used protection devices in industrial AMRs are fuses and circuit breakers. Although both perform similar protective functions, they differ significantly in operating characteristics, response speed, maintenance requirements, and application suitability.

A fuse provides protection through a sacrificial conductive element that melts when current exceeds a specified value. Once activated, the fuse must be replaced before normal operation can resume. Because of their simple construction, fuses generally respond extremely quickly to high short-circuit currents and offer excellent fault interruption capability.

Circuit breakers operate differently. Rather than permanently melting, they utilize mechanical switching mechanisms that automatically or manually disconnect the circuit during abnormal current conditions. After the fault has been corrected, the breaker can typically be reset without component replacement.

Selecting appropriate protection ratings requires detailed understanding of normal operating currents, transient current peaks, fault current levels, conductor ratings, and equipment limitations. Protection devices should not be sized according to maximum possible current but rather according to the safe operating limits of the protected conductors and equipment.

Motor circuits require particular attention because startup current may significantly exceed steady-state operating current. A protection device selected too close to continuous operating current may trip repeatedly during normal acceleration. Time-delay fuses or motor-protection circuit breakers are therefore commonly used for propulsion systems.

Battery protection is especially important because lithium-ion battery packs can deliver extremely high fault currents. High-current battery fuses are typically installed close to the battery terminals to minimize the length of unprotected conductors. Additional contactors controlled by the Battery Management System provide another layer of protection.

Branch circuits supplying computers, sensors, communication equipment, and control electronics usually require individual protection devices. Distributed protection improves fault isolation because failure within one subsystem does not necessarily disable the entire robot.

Coordination between protection devices is another essential design objective. Selective coordination ensures that only the protection device nearest the fault opens while upstream devices remain energized. This minimizes operational disruption and simplifies fault diagnosis.

Modern electronic circuit breakers increasingly incorporate diagnostic capabilities including current monitoring, fault logging, remote reset functions, temperature monitoring, and communication interfaces. These features support predictive maintenance and improve fleet management capabilities.

Ultimately, effective protection design balances safety, reliability, selectivity, maintainability, and operational continuity. Proper selection of fuses and circuit breakers significantly reduces equipment damage, minimizes downtime, and improves overall system safety.

### 5.3 Grounding Design

---

Grounding design is a fundamental aspect of electrical system engineering that directly influences safety, electromagnetic compatibility (EMC), measurement accuracy, communication reliability, and fault protection. Although grounding is sometimes treated as a secondary consideration, improper grounding can cause intermittent failures that are extremely difficult to diagnose.

Grounding serves several independent purposes. Protective grounding provides a low-resistance path for fault currents, reducing electric shock hazards and enabling protective devices to operate rapidly during insulation failures. Functional grounding establishes stable electrical reference potentials for electronic circuits. Electromagnetic grounding minimizes noise and interference within communication and sensing systems.

Industrial AMRs commonly employ multiple grounding domains. High-power motor circuits, low-power control electronics, communication networks, sensor systems, and chassis structures may each require different grounding strategies depending on electrical characteristics.

Star grounding is one of the most widely recommended approaches for mobile robotic systems. In a star-ground configuration, individual subsystem grounds connect to a single central grounding point. This arrangement minimizes circulating currents and reduces ground-loop formation, thereby improving signal integrity.

Ground loops occur when multiple grounding paths exist between two electrical points. Differences in ground potential create unintended circulating currents that introduce electrical noise into sensitive measurement circuits. Analog sensors, IMUs, GNSS receivers, cameras, and communication interfaces are particularly susceptible to these effects.

Shield termination also requires careful consideration. Cable shields should provide effective electromagnetic protection without introducing unwanted ground currents. Depending on frequency range and system architecture, shields may be grounded at one end or both ends according to established EMC design principles.

The robot chassis frequently serves as a protective grounding structure. Metallic frames provide mechanical strength while also functioning as low-impedance current return paths under fault conditions. Proper bonding between chassis sections ensures consistent electrical potential throughout the vehicle.

Electromagnetic compatibility requirements become increasingly important as switching frequencies rise. Motor drives operating at high PWM frequencies generate significant electromagnetic emissions that may interfere with encoder signals, industrial Ethernet communication, wireless devices, and precision sensors. Appropriate grounding and shielding substantially reduce these problems.

Battery systems also require careful grounding consideration. Many industrial AMRs utilize floating DC systems in which neither battery terminal is permanently connected to chassis ground. Insulation monitoring devices continuously supervise isolation resistance and detect leakage faults before hazardous conditions develop.

Ground resistance should be minimized wherever protective grounding is required. Low-resistance grounding improves fault current flow and enables protection devices to operate within their specified response times. Reliable mechanical connections, corrosion-resistant materials, and periodic inspection all contribute to long-term grounding performance.

A successful grounding design integrates safety engineering, EMC principles, electrical protection, and communication reliability into a unified architecture. Proper grounding not only protects equipment and personnel but also enhances overall system stability, reduces troubleshooting effort, and ensures consistent long-term operation in demanding industrial environments.

### 5.1 케이블 단면적 선정 기준(Cable Cross Section Selection Criteria)

---

**Power Loss = I²R**

### 5.2 퓨즈 및 차단기 선정(Fuse and Circuit Breaker Selection)

---

### 5.3 접지 설계(Grounding Design)
