**Differential Drive & Steer Drive Engineering**

# Chapter 02 Mobile Robot Kinematics Basics

## 01 Coordinate Systems

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

### 1.1 Global Frame

---

The Global Frame, sometimes referred to as the World Frame, Map Frame, or Reference Frame, is the highest-level coordinate system used in robotics, autonomous vehicles, and mobile robot navigation. It provides a fixed and consistent reference against which the position, orientation, and movement of a robot can be described. Every autonomous navigation system ultimately requires a stable coordinate system that remains unchanged regardless of how the robot moves. The Global Frame fulfills this role by acting as the universal reference for all localization, mapping, planning, and navigation operations.

In a mobile robot environment, the Global Frame is typically established when a map is created. During the mapping process, all detected landmarks, walls, obstacles, equipment, and infrastructure elements are assigned coordinates relative to this frame. Once the map is generated, every position within the operational environment can be uniquely described using Global Frame coordinates. This enables robots to determine where they are, where they need to go, and how they should move between locations.

The concept of a Global Frame is similar to geographic coordinates used on Earth. Just as latitude and longitude provide a universal reference for global navigation, the Global Frame provides a universal reference for robot navigation within a facility, warehouse, factory, hospital, or outdoor environment. The robot may continuously move and rotate, but the Global Frame remains fixed and unchanged.

In indoor environments, the Global Frame is often defined by the SLAM system. When a robot creates a map using LiDAR, cameras, or other sensors, the initial mapping position commonly becomes the origin of the Global Frame. Every subsequent position estimate is then calculated relative to that origin. In larger facilities, the Global Frame may be aligned with building coordinates, engineering drawings, or factory layouts to facilitate integration with other systems.

In outdoor autonomous systems, the Global Frame may be associated with geographic coordinate systems such as WGS84, Universal Transverse Mercator (UTM), or local engineering coordinate systems. GNSS receivers provide positioning information relative to these frames, enabling robots to operate across large outdoor areas while maintaining accurate localization.

The Global Frame is fundamental for path planning and fleet management. Fleet management systems often coordinate dozens or hundreds of robots simultaneously. To avoid collisions and optimize traffic flow, all robot positions must be represented within a common coordinate system. Without a shared Global Frame, coordinated navigation would become extremely difficult.

Sensor fusion algorithms also rely heavily on the Global Frame. Data from LiDAR, cameras, IMUs, wheel encoders, GNSS receivers, and radar systems are combined to estimate the robot's state. These sensors may operate within different coordinate systems, but their outputs must ultimately be transformed into a common reference frame to enable consistent interpretation.

Another important application of the Global Frame is digital twin integration. Modern factories increasingly use digital twin systems to monitor robot operations. The virtual representation of the facility uses a fixed coordinate system that mirrors the physical environment. The robot's real-time position can therefore be displayed and analyzed within the digital twin using Global Frame coordinates.

The accuracy of the Global Frame directly affects navigation performance. Mapping errors, localization drift, coordinate misalignment, and sensor calibration errors can all degrade robot performance. Consequently, establishing and maintaining an accurate Global Frame is one of the most important tasks in autonomous system engineering.

As autonomous robotics evolves toward larger fleets and more complex environments, the importance of a consistent Global Frame continues to increase. It serves as the foundation upon which localization, planning, coordination, and intelligent decision-making are built.

### 1.2 Body Frame

---

While the Global Frame provides a fixed reference for the environment, the Body Frame provides a moving reference attached directly to the robot itself. The Body Frame, sometimes called the Robot Frame, Vehicle Frame, or Local Frame, is one of the most frequently used coordinate systems in robotics because it describes motion, sensor measurements, and control commands relative to the robot's own structure.

The origin of the Body Frame is typically placed at a well-defined location on the robot. Common choices include the geometric center of the chassis, the center of the drive axle, the center of mass, or the midpoint between drive wheels. The axes are fixed to the robot and move together with it. As the robot translates and rotates, the Body Frame undergoes the same motion.

In mobile robotics, the Body Frame convention usually defines the positive X-axis as the forward direction of travel, the positive Y-axis as the left side of the robot, and the positive Z-axis as the upward direction. This convention follows the right-hand coordinate system widely used in robotics and aerospace engineering.

One of the primary advantages of the Body Frame is that motion commands are naturally expressed within it. Velocity commands generated by navigation software often specify forward velocity, lateral velocity, and rotational velocity relative to the robot's current orientation. These commands are significantly easier to interpret within the Body Frame than within the Global Frame.

Most onboard sensors also operate naturally within the Body Frame. LiDAR sensors measure obstacle locations relative to the robot. Cameras detect objects relative to the camera position. IMUs measure acceleration and angular velocity relative to the robot's orientation. Wheel encoders measure wheel motion relative to the chassis. Consequently, raw sensor data is usually represented in Body Frame coordinates before being transformed into other reference frames.

The Body Frame plays a central role in robot kinematics and dynamics. Vehicle motion models describe how wheel speeds, steering angles, and actuator outputs generate movement relative to the robot. Differential drive, steer drive, mecanum drive, and omni drive systems all rely on Body Frame representations when calculating motion commands and control responses.

Control systems also depend heavily on the Body Frame. Path-following controllers often compute tracking errors relative to the robot\'s current position and orientation. These errors are converted into velocity commands expressed in the Body Frame. By continuously updating these commands, the robot can follow planned trajectories with high accuracy.

Sensor calibration is another important application. The position and orientation of each sensor mounted on the robot must be defined relative to the Body Frame. These fixed relationships are known as extrinsic calibration parameters. Accurate calibration ensures that data from multiple sensors can be combined consistently.

The Body Frame is also essential for robotic manipulators mounted on mobile platforms. When a robot arm is installed on an AMR, the arm's base coordinate system is typically defined relative to the Body Frame. This relationship allows manipulation tasks to remain accurate even while the robot moves through the environment.

Because the Body Frame moves with the robot, it continuously changes relative to the Global Frame. Understanding the relationship between these two frames is therefore one of the most fundamental concepts in robotics. This relationship is described mathematically through coordinate transformations, which form the basis of localization, navigation, and motion planning systems.

### 1.3 Coordinate Transformation and Homogeneous Transform

Coordinate transformation is the mathematical process used to convert positions, orientations, velocities, and sensor measurements from one coordinate frame to another. In robotics, coordinate transformations are required constantly because different sensors, controllers, actuators, and software modules often operate within different reference frames. Without a systematic method for transforming coordinates, it would be impossible to integrate these components into a coherent robotic system.

The simplest coordinate transformation involves translation. Translation describes a change in position between two coordinate systems while maintaining the same orientation. For example, a LiDAR sensor mounted 300 mm in front of the robot center has a translated coordinate system relative to the Body Frame.

Rotation transformations describe differences in orientation between coordinate systems. A camera mounted at an angle relative to the robot chassis produces measurements in a rotated coordinate frame. To integrate camera observations with other sensor data, the camera coordinates must be rotated into the Body Frame or Global Frame.

In practical robotic systems, translation and rotation occur simultaneously. A sensor may be located at a different position and orientation relative to the robot. Similarly, the robot itself continuously changes both position and orientation relative to the Global Frame. Consequently, robotics requires a unified mathematical framework capable of handling both translation and rotation together.

This requirement is addressed through Homogeneous Transformation. A homogeneous transform represents translation and rotation within a single matrix. In two-dimensional robotics, homogeneous transformations are commonly represented using 3×3 matrices. In three-dimensional robotics, 4×4 matrices are used.

The key advantage of homogeneous transformations is that multiple coordinate transformations can be combined through simple matrix multiplication. For example, a point measured in a camera coordinate system can be transformed into the Body Frame, then into the Global Frame, by multiplying the corresponding transformation matrices. This process allows complex robotic systems to maintain consistent spatial relationships among numerous coordinate frames.

Homogeneous transformations form the foundation of robot kinematics. Every robotic manipulator, mobile robot, autonomous vehicle, and drone relies on transformation matrices to describe spatial relationships. Forward kinematics calculates the position of robot components by chaining transformations together. Inverse kinematics solves for actuator commands required to achieve desired positions.

The Robot Operating System (ROS and ROS 2) implements these concepts through the TF and TF2 frameworks. These systems maintain a dynamic tree of coordinate frames and automatically compute transformations between them. Frames such as map, odom, base_link, laser, camera, imu, and wheel_link are continuously updated and managed within this framework.

Localization systems also depend on coordinate transformations. The robot's estimated pose consists of its position and orientation relative to the Global Frame. This pose is represented mathematically as a homogeneous transformation between the Global Frame and the Body Frame. As the robot moves, this transformation changes continuously.

Modern autonomous systems may contain dozens of coordinate frames. Cameras, LiDARs, IMUs, GNSS receivers, robot arms, end effectors, wheels, and external infrastructure all introduce additional coordinate systems. Homogeneous transformations provide the mathematical language that allows these components to communicate consistently and accurately.

For this reason, coordinate transformations and homogeneous transforms are considered among the most fundamental concepts in robotics. They provide the bridge connecting perception, localization, navigation, motion planning, control, manipulation, and autonomous decision-making into a unified engineering framework.

### 1.1 전역 좌표계 (Global Frame)

---

### 1.2 차체 좌표계 (Body Frame)

---

### 1.3 좌표 변환과 동차 변환 행렬

## 02 Forward Kinematics

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Differential Drive Forward Kinematics Equations

---

Forward kinematics is the mathematical process of determining the motion of a robot based on known actuator inputs. In mobile robotics, forward kinematics converts wheel rotational velocities into vehicle linear and angular velocities. For differential drive robots, forward kinematics forms the foundation of localization, odometry, path planning, and motion control. Every navigation system operating on a differential drive platform ultimately depends on accurate forward kinematic calculations.

A differential drive robot typically consists of two independently driven wheels mounted on opposite sides of the chassis. Let the left wheel angular velocity be denoted as ωL and the right wheel angular velocity as ωR. The wheel radius is represented by r, and the distance between the two drive wheels is represented by L, often referred to as the wheel track width.

The first step in differential drive forward kinematics is converting wheel angular velocity into wheel linear velocity. Since linear velocity is equal to angular velocity multiplied by wheel radius, the left and right wheel velocities can be expressed as:

vL = r · ωL

vR = r · ωR

These wheel velocities determine the overall motion of the robot. When both wheels move at the same velocity, the robot travels in a straight line. When the wheel velocities differ, the robot follows a curved path. The robot\'s forward velocity is obtained by averaging the wheel velocities:

v = (vR + vL) / 2

This velocity represents the translational speed of the robot along its forward direction. The angular velocity of the robot around its vertical axis is determined by the difference between wheel velocities:

ω = (vR − vL) / L

This equation reveals one of the fundamental characteristics of differential drive systems. Turning motion is generated entirely by the velocity difference between the two wheels. If both wheel velocities are equal, angular velocity becomes zero and the robot moves straight ahead. If one wheel moves faster than the other, a rotational component is introduced.

The instantaneous center of rotation (ICR) is another important concept. During a turn, the robot rotates about a point located somewhere along the extension of the wheel axle. The distance from the robot center to the ICR can be calculated as:

R = (L/2) · (vR + vL) / (vR − vL)

This radius determines the curvature of the robot\'s trajectory. Large radii correspond to gentle turns, while small radii correspond to sharp turns.

Once linear and angular velocities are known, the robot pose can be updated. If the robot position in the Global Frame is represented by x, y, and heading angle θ, the continuous-time kinematic model becomes:

dx/dt = v cos θ

dy/dt = v sin θ

dθ/dt = ω

These equations describe how the robot moves through the environment over time. Numerical integration methods such as Euler integration or Runge-Kutta integration are often used to compute the updated position.

Differential drive forward kinematics is widely used because of its simplicity and computational efficiency. However, real-world factors such as wheel slip, uneven floors, tire deformation, encoder noise, and payload variation introduce errors. Therefore, practical systems combine forward kinematics with sensor fusion techniques using IMUs, LiDARs, cameras, and localization algorithms.

Despite these limitations, differential drive forward kinematics remains one of the most important mathematical models in mobile robotics. It provides the basis for odometry estimation, trajectory generation, motion control, and autonomous navigation in thousands of robotic systems deployed worldwide.

### 2.2 Steer Drive Forward Kinematics Equations

Steer drive systems employ a fundamentally different mobility architecture compared with differential drive robots. In a steer drive robot, propulsion and steering are controlled independently. Each steerable wheel module typically contains a traction motor that generates forward motion and a steering actuator that controls wheel orientation. This configuration allows the vehicle to move in highly controlled directions while maintaining superior positioning accuracy.

The forward kinematics of a steer drive system depends on both wheel velocity and steering angle. Consider a steer drive wheel with traction velocity v and steering angle δ relative to the vehicle body frame. The wheel generates velocity components in both the longitudinal and lateral directions.

The velocity components can be expressed as:

vx = v cos δ

vy = v sin δ

These equations decompose wheel motion into the vehicle coordinate system. The overall vehicle motion is determined by combining the contributions from all steerable wheel modules.

For a simple bicycle model commonly used to represent steer drive vehicles, the vehicle is assumed to have a single front steering wheel and a rear drive wheel. Let L represent the wheelbase distance between front and rear axles. The vehicle linear velocity is represented by v and steering angle by δ.

The forward kinematic equations become:

dx/dt = v cos θ

dy/dt = v sin θ

dθ/dt = (v/L) tan δ

These equations closely resemble those of automotive steering systems and are widely used in autonomous vehicle modeling.

An important parameter in steer drive kinematics is the turning radius. The turning radius can be calculated using:

R = L / tan δ

This equation shows that steering angle directly determines trajectory curvature. Small steering angles produce large turning radii, while large steering angles create tighter turns.

Modern industrial AMRs frequently use dual steer drive or four-wheel steer drive architectures. In these systems, multiple steering angles and wheel velocities must be coordinated simultaneously. The kinematic equations become more complex because each wheel follows a unique trajectory while maintaining a common vehicle motion.

For four-wheel steer systems, the steering geometry is often designed according to Ackermann Steering principles. Ackermann geometry ensures that all wheels rotate about a common instantaneous center of rotation, minimizing tire scrubbing and improving motion efficiency. This approach significantly reduces tire wear and improves path-following accuracy.

Forward kinematics for multi-wheel steer drive systems is commonly represented using matrix-based formulations. Vehicle velocity vectors are mapped to individual wheel velocities and steering angles through Jacobian matrices. These formulations enable efficient real-time control and trajectory tracking.

One of the primary advantages of steer drive forward kinematics is predictability. Because wheel orientation directly controls motion direction, steer drive systems generally exhibit lower trajectory errors than differential drive systems. This makes them particularly suitable for precision docking, automated manufacturing, semiconductor handling, and heavy payload transportation.

However, steer drive kinematics requires accurate steering angle measurement and synchronization. Errors in steering calibration, encoder measurements, or wheel alignment can significantly degrade performance. Consequently, steer drive systems often employ high-resolution encoders, real-time EtherCAT communication, and advanced control algorithms to maintain accuracy.

As industrial robotics continues to demand higher payload capacities and positioning accuracy, steer drive forward kinematics has become a critical component of modern AMR design. Understanding these equations is essential for developing advanced navigation and motion control systems.

### 2.3 Omni Drive Forward Kinematics Equations

ω1, ω2, ω3, ω4

Omni Drive Forward Kinematics describes how wheel motions are transformed into robot body motion in a holonomic mobile robot. Unlike Differential Drive and most conventional vehicle architectures, Omni Drive robots can move freely in any direction while simultaneously rotating. This capability is achieved through specialized wheel designs such as Omni Wheels and Mecanum Wheels equipped with passive rollers.

The fundamental characteristic of Omni Drive is the existence of three independent planar degrees of freedom. The robot body velocity is represented by:

Vx = forward velocity

Vy = lateral velocity

ω = angular velocity

These three variables can be controlled simultaneously and independently. As a result, the robot can translate and rotate at the same time without requiring prior reorientation.

Consider a four-wheel Mecanum platform. Each wheel contains rollers mounted at approximately 45 degrees relative to the wheel rotation axis. Because of this geometry, the force generated by each wheel is decomposed into longitudinal and lateral components.

Let the wheel angular velocities be:

and let the wheel radius be r.

The body velocity can be expressed as a linear combination of wheel velocities:

Vx = (r/4)(ω1 + ω2 + ω3 + ω4)

Vy = (r/4)(−ω1 + ω2 + ω3 − ω4)

ω = (r/4R)(−ω1 + ω2 − ω3 + ω4)

where R represents the effective distance from the robot center to the wheel contact points.

These equations illustrate a major difference between Omni Drive and Differential Drive. In Differential Drive, lateral velocity is constrained to zero. In Omni Drive, lateral velocity is a directly controllable state variable.

For three-wheel Omni platforms arranged at 120-degree intervals, the forward kinematic equations differ slightly because the wheel geometry changes. Nevertheless, the overall principle remains identical. The wheel velocity vectors are projected onto the robot body frame, and the combined contribution of all wheels determines the final robot motion.

A matrix formulation is typically used:

V = JW

where:

V = body velocity vector

J = kinematic transformation matrix

W = wheel velocity vector

The transformation matrix depends entirely on wheel arrangement, roller orientation, wheel placement geometry, and chassis dimensions.

The Forward Kinematics equations allow the robot controller to estimate actual robot motion from wheel encoder measurements. These estimates are essential for odometry, localization, trajectory tracking, and motion control.

However, Omni Drive systems are more sensitive to real-world disturbances than Steer Drive platforms. Because the wheels rely on passive rollers, slip can occur more easily. Floor contamination, roller wear, vibration, uneven surfaces, and manufacturing tolerances all introduce errors into the kinematic model.

For this reason, industrial Omni Drive robots often combine encoder-based forward kinematics with IMU fusion, visual localization, LiDAR SLAM, and adaptive slip compensation algorithms. These techniques compensate for the limitations of ideal kinematic assumptions.

Despite these challenges, Omni Drive Forward Kinematics provides unmatched maneuverability. The ability to move laterally, diagonally, and rotationally without changing vehicle orientation makes Omni Drive highly attractive for semiconductor wafer transport systems, narrow-aisle warehouse robots, research platforms, mobile manipulators, and flexible manufacturing automation systems.

The mathematical framework of Omni Drive Forward Kinematics forms the foundation for all higher-level motion planning and control algorithms. By understanding how wheel velocities are transformed into body motion, engineers can design robots capable of smooth, accurate, and highly agile omnidirectional navigation in complex industrial environments.

### 2.1 차동 구동 순기구학 방정식

---

vL = r × ωL

vR = r × ωR

v = (vR + vL) / 2

ω = (vR − vL) / L

R = (L/2) × (vR + vL) / (vR − vL)

dx/dt = v cos θ

dy/dt = v sin θ

dθ/dt = ω

### 2.2 스티어 드라이브 순기구학 방정식

vx = v cos δ

vy = v sin δ

dx/dt = v cos θ

dy/dt = v sin θ

dθ/dt = (v/L) tan δ

R = L / tan δ

### 2.3 옴니 구동 전진 기구학 방정식(Omni Drive Forward Kinematics Equations)

ω1, ω2, ω3, ω4

Vx = (r/4)(ω1 + ω2 + ω3 + ω4)

Vy = (r/4)(−ω1 + ω2 + ω3 − ω4)

ω = (r/4R)(−ω1 + ω2 − ω3 + ω4)

V = JW

## 03 Inverse Kinematics

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Deriving Wheel Velocities from Target Velocity

---

Inverse kinematics is the mathematical process of determining actuator commands required to achieve a desired robot motion. While forward kinematics calculates vehicle motion from known wheel velocities, inverse kinematics performs the opposite operation. Given a desired vehicle velocity, heading change, or trajectory command, inverse kinematics determines the wheel velocities, steering commands, or actuator positions necessary to produce that motion. In mobile robotics, inverse kinematics forms the foundation of motion control, path tracking, trajectory following, and autonomous navigation.

For differential drive robots, the most common control objective is specifying a desired linear velocity and angular velocity. Let the desired forward velocity be represented by v and the desired angular velocity be represented by ω. The objective of inverse kinematics is to calculate the left and right wheel velocities that will generate these desired motions.

From forward kinematics, the vehicle velocity relationships are known:

v = (vR + vL)/2

ω = (vR − vL)/L

where vL and vR represent the left and right wheel linear velocities and L represents the distance between the drive wheels.

The inverse kinematic solution is obtained by solving these equations simultaneously. Rearranging the equations yields:

vR = v + (L/2)ω

vL = v − (L/2)ω

These equations represent one of the most important results in differential drive control. They directly convert desired vehicle motion into wheel commands. Every differential drive controller ultimately performs this calculation before transmitting commands to motor controllers.

Several special cases illustrate the behavior of these equations. When the desired angular velocity is zero, both wheel velocities become equal and the robot moves in a straight line. When the desired linear velocity is zero and a nonzero angular velocity is specified, the wheels rotate in opposite directions, producing a pure rotational motion around the robot center. When both linear and angular velocities are nonzero, the robot follows a curved trajectory.

Motor controllers generally require wheel angular velocities rather than wheel linear velocities. Therefore, an additional conversion is required using the wheel radius r:

ωR = vR/r

ωL = vL/r

These values become the actual commands sent to the wheel motors.

Inverse kinematics becomes especially important during trajectory tracking. Path planners typically generate velocity commands rather than wheel commands. The navigation system may determine that the robot should move at 1.2 m/s while turning at 0.3 rad/s. The inverse kinematic module immediately converts these values into wheel velocities that can be executed by the drive system.

In practical systems, additional constraints must be considered. Motors have maximum speed limits, acceleration limits, torque limits, and thermal restrictions. Consequently, the calculated wheel velocities may require scaling or modification before execution. Advanced motion controllers continuously monitor these constraints while preserving the intended trajectory as closely as possible.

Sensor feedback is also integrated into inverse kinematic control loops. Encoders measure actual wheel velocities and compare them with commanded values. Any deviation generates correction signals through feedback controllers such as PID algorithms. This closed-loop process ensures accurate execution of inverse kinematic commands.

Modern autonomous robots often operate in highly dynamic environments where velocity commands change continuously. Consequently, inverse kinematic calculations are performed hundreds or even thousands of times per second. Although the equations appear simple, they represent a critical bridge between high-level navigation decisions and low-level actuator control.

As autonomous robotics continues to evolve, inverse kinematics remains one of the most fundamental mathematical tools for converting desired robot behavior into executable wheel commands. It transforms abstract motion objectives into physical actions, allowing robots to move precisely and efficiently within their operating environments.

### 3.2 Steer Drive Steering Angle Inverse Kinematics

Inverse kinematics for steer drive systems is more sophisticated than that of differential drive robots because both wheel velocity and steering angle must be determined simultaneously. Instead of controlling motion through wheel speed differences alone, steer drive systems independently control wheel orientation and traction velocity. As a result, inverse kinematic calculations must determine not only how fast each wheel should rotate but also the precise angle at which each wheel should be positioned.

The simplest steer drive model is the bicycle model, which represents the vehicle using a single steerable front wheel and a rear drive wheel. Given a desired vehicle velocity v and angular velocity ω, the objective is to calculate the required steering angle δ.

From forward kinematics, the relationship between vehicle motion and steering angle is:

ω = (v/L) tan δ

where L is the wheelbase of the vehicle.

Rearranging the equation yields the inverse kinematic solution:

δ = arctan((Lω)/v)

This equation determines the steering angle required to generate the desired turning motion. The steering angle increases as angular velocity increases and decreases as vehicle velocity increases.

The resulting behavior aligns with intuitive driving experience. At low speeds, large steering angles produce tight turns. At higher speeds, smaller steering angles generate similar trajectory curvatures. This relationship explains why high-speed vehicles typically use relatively small steering angles.

For industrial AMRs employing dual steer drive systems, inverse kinematics becomes significantly more complex. Each steering module must receive both a steering angle command and a wheel velocity command. The control system must ensure that all wheels remain consistent with a common vehicle motion objective.

The concept of an Instantaneous Center of Rotation (ICR) plays a central role in steer drive inverse kinematics. During turning, every wheel must align toward the same ICR to avoid tire scrubbing and unnecessary mechanical stress. Consequently, steering angles are calculated such that the wheel axes intersect at a common rotational center.

For a four-wheel steer drive vehicle, the steering angle of each wheel depends on its position relative to the vehicle center and the desired turning radius. Inner wheels generally require larger steering angles than outer wheels because they follow tighter trajectories. This relationship is described by Ackermann Steering Geometry, which remains one of the most important concepts in steer drive design.

Modern AMRs frequently use independent steering modules with electronic steering control. In these systems, inverse kinematics is often implemented using matrix formulations. Desired vehicle velocities are represented as velocity vectors, and transformation matrices compute individual wheel angles and wheel speeds. These calculations can be extended to vehicles with four, six, or even eight independently steerable wheels.

Another important application is crab steering. In crab steering mode, all wheels are oriented to the same angle, allowing the vehicle to move diagonally without changing its heading. Inverse kinematics must calculate a common steering angle for all wheels while maintaining synchronized wheel velocities. This capability is particularly valuable for precision positioning and maneuvering in confined industrial environments.

Heavy-duty industrial robots introduce additional challenges. Large payloads increase wheel loading and may create steering lag due to mechanical compliance and actuator limitations. Consequently, inverse kinematic algorithms often incorporate dynamic compensation terms to account for steering system delays, wheel slip, and load variations.

Sensor feedback is essential for steer drive inverse kinematics. Steering encoders continuously measure actual wheel angles and compare them with desired angles. Any discrepancies are corrected through closed-loop control algorithms. High-resolution absolute encoders, EtherCAT communication networks, and real-time controllers are commonly used to maintain steering accuracy.

As industrial AMRs continue to increase in payload capacity and positioning requirements, steer drive inverse kinematics has become a critical component of autonomous mobility systems. It provides the mathematical framework that transforms desired vehicle trajectories into coordinated steering and wheel motion commands. Without accurate inverse kinematics, precise navigation, automated docking, heavy-load transport, and advanced fleet operations would not be possible.

Together, differential drive inverse kinematics and steer drive inverse kinematics form the core mathematical foundation of mobile robot motion control. They connect high-level navigation objectives with low-level actuator behavior and enable robots to transform planned paths into real-world movement with precision, efficiency, and reliability.

### 3.3 Omni Drive Inverse Kinematics and Roller Geometry

Omni Drive inverse kinematics is fundamentally different from Differential Drive and Steer Drive because Omni Drive systems are holonomic. Rather than computing steering angles, the inverse kinematic problem focuses on determining the wheel angular velocities required to generate a desired body velocity. The unique roller geometry of Omni Wheels and Mecanum Wheels plays a central role in this process.

A holonomic robot can independently control longitudinal velocity Vx, lateral velocity Vy, and rotational velocity ω. These three motion components define the desired body velocity vector. The inverse kinematic objective is to calculate the angular velocity of each wheel that will collectively produce this motion.

The solution depends strongly on wheel geometry. In a conventional wheel, force is generated only along the rolling direction. In an Omni Wheel, passive rollers allow free motion perpendicular to the wheel plane. In a Mecanum Wheel, rollers are mounted at approximately 45 degrees, creating force vectors that contain both longitudinal and lateral components.

The roller angle determines how wheel rotation contributes to robot motion. Because of this geometric relationship, each wheel produces a velocity contribution that can be projected onto the robot body frame. The combined effect of all wheels determines the overall robot motion.

For a four-wheel Mecanum platform, the inverse kinematic equations can be expressed in matrix form. Given the desired body velocity vector:

[Vx Vy ω]T

the wheel angular velocity vector is obtained through a kinematic transformation matrix:

W = J⁻¹V

where W contains the wheel velocities and J represents the wheel geometry matrix.

The resulting wheel velocity equations typically take the form:

ω1 = (1/r)(Vx − Vy − Rω)

ω2 = (1/r)(Vx + Vy + Rω)

ω3 = (1/r)(Vx + Vy − Rω)

ω4 = (1/r)(Vx − Vy + Rω)

where r is wheel radius and R represents the effective distance from the robot center to the wheel contact point.

These equations demonstrate the unique capabilities of Omni Drive systems. A pure lateral motion command produces a completely different wheel velocity pattern from a forward motion command. Similarly, rotational motion is generated through coordinated velocity differences among all wheels.

Roller geometry significantly influences system performance. Mecanum wheels with 45-degree rollers provide balanced longitudinal and lateral force generation, making them suitable for omnidirectional motion. Standard Omni Wheels with 90-degree rollers exhibit different force characteristics and are often used in three-wheel or four-wheel omni-drive configurations.

The roller geometry also introduces challenges. Since force transmission occurs through passive rollers, some energy is inevitably lost. Roller compliance, bearing friction, manufacturing tolerances, and wear all influence kinematic accuracy. As rollers age, their effective contact geometry changes, which can introduce errors into the inverse kinematic model.

To address these issues, industrial systems frequently implement calibration procedures and adaptive compensation algorithms. These techniques adjust the kinematic parameters based on observed performance, improving motion accuracy over the lifetime of the robot.

Omni Drive inverse kinematics is essential for applications requiring extreme maneuverability. Semiconductor wafer transport systems, mobile manipulators, cleanroom robots, research platforms, and narrow-aisle logistics robots all rely on accurate wheel velocity calculations to achieve smooth omnidirectional motion. The mathematical relationship between body velocity, wheel velocity, and roller geometry ultimately enables the remarkable agility that distinguishes Omni Drive robots from all other mobile robot architectures.

### 3.1 목표 속도로부터 바퀴 속도 계산

---

v = (vR + vL) / 2

ω = (vR − vL) / L

vR = v + (L/2)ω

vL = v − (L/2)ω

ωR = vR / r

ωL = vL / r

### 3.2 스티어 드라이브 조향각 역기구학

ω = (v/L) tan δ

δ = arctan((Lω)/v)

### 3.3 옴니 구동 역기구학 및 롤러 기하학(Omni Drive Inverse Kinematics and Roller Geometry)

ω1 = (1/r)(Vx − Vy − Rω)

ω2 = (1/r)(Vx + Vy + Rω)

ω3 = (1/r)(Vx + Vy − Rω)

ω4 = (1/r)(Vx − Vy + Rω)

## 04 Motion Constraints

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Non-holonomic Constraints

---

Non-holonomic constraints are among the most important concepts in mobile robot motion analysis. A non-holonomic system is a system whose motion is restricted by velocity constraints that cannot be expressed solely as position constraints. In practical terms, this means that although a robot may physically exist in a two-dimensional or three-dimensional space, it cannot move freely in every direction at every instant. Its motion is constrained by the geometry of its wheels, steering mechanism, and contact conditions with the ground.

Most industrial mobile robots, autonomous mobile robots (AMRs), automobiles, trucks, forklifts, and autonomous vehicles belong to the non-holonomic category. Differential drive robots and steer drive robots are the most common examples. These vehicles can move forward and backward and can rotate, but they cannot instantly move sideways without first changing orientation.

Consider a differential drive robot operating on a flat floor. The robot possesses three state variables: position in the X direction, position in the Y direction, and heading angle θ. Although three independent coordinates are required to describe the robot\'s pose, only two independent control inputs are available. These inputs are typically linear velocity and angular velocity. Because lateral motion is impossible, the robot is subject to a non-holonomic constraint.

Mathematically, the lateral velocity component in the body frame is constrained to zero. The robot cannot generate motion perpendicular to its wheel direction. This limitation arises from wheel-ground contact mechanics. Conventional wheels roll easily along their rolling direction but strongly resist motion in the lateral direction.

The implications of non-holonomic constraints are significant for path planning and control. A robot cannot simply move directly to any target location. Instead, it must follow a feasible trajectory that respects its motion limitations. For example, reaching a point located directly to the side requires a sequence of forward motion and rotation rather than a direct sideways translation.

Many classical robotics algorithms are specifically designed to handle non-holonomic systems. Path planning methods such as Dubins paths, Reeds-Shepp paths, lattice planners, and kinodynamic planning algorithms explicitly incorporate vehicle motion constraints. These approaches generate trajectories that can actually be executed by the robot.

Differential drive robots are particularly affected by non-holonomic behavior. Although they can rotate in place, they cannot perform lateral translation. Steer drive vehicles share similar limitations. Even though steering provides greater maneuverability, motion remains constrained by wheel orientation and steering geometry.

Non-holonomic constraints also influence localization and control. Motion prediction models must respect the vehicle\'s allowable motions. Control algorithms must continuously generate commands that satisfy the robot\'s kinematic limitations while tracking the desired trajectory.

In industrial environments, non-holonomic systems often provide advantages despite their limitations. Conventional wheels offer higher traction, greater payload capacity, lower energy consumption, and simpler mechanical design compared with holonomic alternatives. As a result, most industrial AMRs, warehouse robots, pallet movers, and heavy-duty transport platforms continue to rely on non-holonomic architectures.

Understanding non-holonomic constraints is therefore essential for robot designers, control engineers, and navigation system developers. These constraints define the fundamental motion capabilities of the vehicle and influence every aspect of planning, localization, control, and autonomous operation.

### 4.2 Holonomic Constraints and Omni Drive

---

Holonomic motion represents the opposite end of the mobility spectrum from non-holonomic motion. A holonomic robot can independently control all of its available degrees of freedom within the operating plane. In practical terms, this means the robot can move in any direction and rotate simultaneously without requiring intermediate reorientation maneuvers. Holonomic mobility provides exceptional flexibility and is a defining characteristic of Omni Drive and Mecanum Drive systems.

A mobile robot operating on a flat surface generally possesses three planar degrees of freedom: longitudinal translation, lateral translation, and rotation. These motions are commonly represented as:

Vx = forward velocity

Vy = lateral velocity

ω = angular velocity

A holonomic robot can independently command all three quantities. As a result, the robot can translate sideways while maintaining its orientation, move diagonally without turning, or rotate while simultaneously moving in any direction. This capability dramatically increases maneuverability compared with non-holonomic platforms.

The key enabler of holonomic motion is specialized wheel geometry. Omni Wheels employ passive rollers mounted around the wheel circumference, allowing free motion perpendicular to the wheel rolling direction. Mecanum Wheels use rollers mounted at approximately 45 degrees, creating force vectors that generate both longitudinal and lateral motion components.

Because of these roller structures, the wheel-ground interaction no longer imposes the same lateral velocity restrictions found in conventional wheels. Instead of constraining sideways motion, the rollers allow controlled lateral displacement. Consequently, the robot gains access to a complete set of planar motion commands.

The kinematic representation of a holonomic robot typically includes all three velocity components as independent control variables:

[Vx Vy ω]T

Motion planners and controllers can therefore generate trajectories that are impossible for Differential Drive systems. For example, an Omni Drive robot approaching a workstation can move directly sideways into alignment without changing its heading. This ability significantly reduces maneuvering time and improves operational efficiency in confined environments.

The benefits of holonomic motion are particularly evident in semiconductor manufacturing, electronics assembly, research laboratories, and collaborative robotic workspaces. In these environments, robots often operate within highly constrained spaces where traditional turning maneuvers are undesirable or impossible.

Despite these advantages, holonomic systems also introduce new challenges. The increased number of actuators and the complexity of wheel geometry require more sophisticated control algorithms. Velocity decomposition, wheel synchronization, and slip compensation become essential components of the control architecture.

Furthermore, the theoretical holonomic capability assumes ideal wheel-ground interactions. In practice, roller compliance, friction variations, and manufacturing tolerances can reduce the effectiveness of omnidirectional motion. Therefore, real-world implementations often require calibration procedures and adaptive control techniques.

Holonomic motion should not be viewed merely as a mathematical property. It directly influences system productivity, workspace utilization, and operational flexibility. For applications requiring maximum maneuverability, Omni Drive architectures provide capabilities that cannot be achieved using conventional non-holonomic systems.

As industrial automation continues to demand greater flexibility, holonomic drive technologies are becoming increasingly important. Their ability to generate arbitrary planar motion makes them valuable tools for next-generation AMRs operating in dynamic and space-constrained environments.

### 4.3 Slip and Real-World Constraints

Theoretical kinematic models often assume ideal operating conditions. Wheels are assumed to roll perfectly without slipping, the ground is assumed to be flat and rigid, sensors are assumed to provide accurate measurements, and actuators are assumed to respond precisely to commands. Real-world robotic systems rarely operate under such ideal conditions. Slip and other practical constraints introduce significant deviations between theoretical predictions and actual robot behavior.

Wheel slip is one of the most common sources of error in mobile robotics. Slip occurs whenever the wheel rotation does not correspond exactly to the vehicle\'s actual movement. This phenomenon can occur during acceleration, braking, turning, obstacle crossing, or operation on low-friction surfaces.

Longitudinal slip occurs when wheels spin faster or slower than the actual ground speed. For example, a heavily loaded AMR accelerating on a smooth concrete floor may experience wheel spin. The wheel encoder indicates motion, but the vehicle may move less than expected. This creates odometry errors and localization drift.

Lateral slip occurs when wheels slide sideways relative to their intended direction of travel. Differential drive robots often experience lateral slip during aggressive turning maneuvers. Steer drive vehicles may experience tire scrubbing when steering geometry is imperfect. Mecanum and omni drive robots may experience significant lateral slip due to the inherent characteristics of their wheel designs.

Surface conditions strongly influence slip behavior. Concrete, epoxy floors, steel plates, tiles, asphalt, gravel, wet surfaces, and dusty environments all provide different friction characteristics. A robot that performs accurately in a laboratory may exhibit substantially different behavior in an industrial facility.

Payload variation is another important real-world constraint. Changes in payload alter wheel loading, traction forces, braking performance, suspension behavior, and energy consumption. A robot carrying a full load may respond differently from the same robot operating without cargo. Consequently, motion control algorithms often require adaptive behavior to maintain consistent performance.

Mechanical compliance introduces additional challenges. Tires deform under load, suspension systems flex, steering mechanisms exhibit backlash, and structural components experience elastic deformation. These effects may appear small individually but can significantly affect positioning accuracy over time.

Environmental factors also influence robot motion. Temperature variations affect tire properties, motor performance, battery output, and sensor accuracy. Vibration from nearby machinery may degrade localization performance. Dust and debris may affect wheel traction and sensor operation.

Sensor limitations further contribute to real-world constraints. Wheel encoders accumulate errors, IMUs experience drift, LiDAR measurements contain noise, cameras are affected by lighting conditions, and GNSS systems may suffer from multipath effects or signal blockage. Consequently, no single sensor can provide perfect information about robot motion.

Modern autonomous systems address these challenges through sensor fusion. Data from wheel encoders, IMUs, LiDARs, cameras, GNSS receivers, radar systems, and other sensors are combined to estimate the robot\'s actual state more accurately. Advanced filtering techniques such as Kalman Filters, Extended Kalman Filters, Unscented Kalman Filters, and factor graph optimization are commonly employed.

Real-world constraints ultimately define the difference between theoretical robotics and deployable robotics. A motion model that performs perfectly in simulation may fail in industrial environments unless these constraints are considered. Successful mobile robot design therefore requires not only understanding kinematic equations but also understanding how physical reality modifies and limits theoretical behavior.

For this reason, modern AMR development increasingly emphasizes robust localization, adaptive control, slip estimation, sensor fusion, and environmental awareness. These technologies allow robots to maintain reliable operation even when real-world conditions differ substantially from ideal assumptions. Understanding slip and real-world constraints is therefore essential for transforming mathematical models into practical autonomous systems capable of operating safely and effectively in industrial environments.

### 4.1 비홀로노믹 제약

---

### 4.2 홀로노믹 제약과 옴니 구동(Holonomic Constraints and Omni Drive)

---

[Vx Vy ω]T

### 4.3 슬립과 실제 환경 제약

## 05 Odometry Basics

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Encoder Based Odometry

---

Encoder-based odometry is the most fundamental method used to estimate the position and orientation of a mobile robot. The term odometry refers to the process of estimating vehicle motion by measuring wheel rotations and integrating those measurements over time. Almost every mobile robot, from small educational platforms to large industrial autonomous mobile robots (AMRs), utilizes encoder-based odometry as one of its primary localization sources.

An encoder is a sensor attached to a motor shaft or wheel axle that measures rotational movement. As the wheel rotates, the encoder generates pulses or digital position information that can be used to determine how far the wheel has traveled. Incremental encoders produce pulses corresponding to angular displacement, while absolute encoders provide the exact rotational position at any moment. Both types are widely used in robotics depending on the required accuracy and system architecture.

The basic principle of encoder-based odometry is straightforward. If the wheel radius is known and the amount of wheel rotation is measured, the linear distance traveled by the wheel can be calculated. For a wheel with radius r rotating through an angle θ, the traveled distance s is given by:

s = rθ

This simple relationship forms the foundation of odometry calculations.

For differential drive robots, wheel encoder measurements from the left and right wheels are combined to estimate both translation and rotation. If the left wheel travels a distance ΔsL and the right wheel travels a distance ΔsR during a sampling interval, the average vehicle displacement is:

Δs = (ΔsR + ΔsL)/2

The change in heading angle can be estimated as:

Δθ = (ΔsR − ΔsL)/L

where L is the distance between the drive wheels.

Using these values, the robot\'s pose can be updated incrementally. If the current position is represented by coordinates x, y, and heading θ, the new pose can be estimated through numerical integration. This process is repeated continuously, allowing the robot to track its motion through the environment.

Encoder-based odometry offers several advantages. It is inexpensive, computationally efficient, and independent of external infrastructure. Unlike GPS or vision systems, encoders function indoors, outdoors, in darkness, and in environments where external references may be unavailable. They also provide high update rates, often exceeding hundreds or thousands of measurements per second.

These characteristics make encoder odometry particularly valuable for motion control. Velocity controllers rely heavily on encoder feedback to maintain accurate wheel speeds and execute motion commands precisely. Even robots equipped with sophisticated localization systems continue to depend on encoder measurements for low-level control.

However, encoder-based odometry also has significant limitations. Because position estimates are obtained through integration, errors accumulate over time. Small measurement inaccuracies eventually grow into substantial localization errors. Wheel slip, uneven terrain, encoder quantization, wheel diameter variation, and mechanical wear all contribute to this error accumulation.

The performance of encoder-based odometry depends heavily on wheel-ground interaction. Under ideal rolling conditions, odometry can provide highly accurate short-term position estimates. In real-world industrial environments, however, perfect rolling conditions rarely exist. Consequently, encoder odometry is often combined with additional sensors to improve long-term accuracy.

Despite its limitations, encoder-based odometry remains one of the most important components of mobile robot localization systems. It provides continuous motion information, supports closed-loop control, and serves as the foundation upon which more advanced localization techniques are built.

### 5.2 Odometry Error Model

---

Although encoder-based odometry provides valuable motion estimates, its accuracy is fundamentally limited by various error sources. Understanding these errors is essential for designing reliable localization systems and predicting long-term navigation performance. The collection of mechanisms that generate inaccuracies in odometry estimation is commonly referred to as the odometry error model.

Odometry errors can generally be divided into systematic errors and non-systematic errors. Systematic errors are repeatable and predictable. They arise from imperfections in robot geometry, sensor calibration, and mechanical design. Non-systematic errors are random and often result from environmental interactions such as wheel slip and surface irregularities.

One common systematic error source is wheel diameter mismatch. In theory, both drive wheels should have identical diameters. In practice, manufacturing tolerances, tire wear, inflation differences, and material deformation create small discrepancies. Even a tiny difference in wheel diameter can cause the robot to gradually drift from its intended trajectory.

Another important systematic error source is incorrect wheelbase estimation. The distance between the drive wheels is a critical parameter in odometry calculations. If the actual wheelbase differs from the value used in software, heading estimates become inaccurate. Over long distances, this error can produce substantial orientation drift.

Encoder resolution also contributes to odometry error. Encoders measure wheel rotation using discrete increments. This quantization introduces small measurement uncertainties. Although individual quantization errors may be negligible, their cumulative effect becomes noticeable during extended operation.

Mechanical factors further influence odometry accuracy. Backlash in gearboxes, bearing wear, wheel eccentricity, suspension compliance, and chassis deformation all affect wheel motion measurements. These effects are particularly significant in heavy-duty industrial robots carrying large payloads.

Non-systematic errors are often more difficult to model because they depend on environmental conditions. Wheel slip is perhaps the most significant source of odometry error. Slip occurs whenever wheel rotation does not accurately correspond to vehicle motion. During acceleration, braking, turning, or operation on low-friction surfaces, slip may cause substantial discrepancies between estimated and actual movement.

Surface characteristics strongly influence slip behavior. Smooth concrete, epoxy flooring, steel plates, wet surfaces, dusty environments, and outdoor terrain each exhibit different friction properties. Consequently, odometry performance may vary dramatically across different operating environments.

Payload variation introduces additional complexity. Changes in payload distribution alter wheel loading and traction characteristics. A robot operating with an empty payload may exhibit different odometry performance compared with the same robot carrying its maximum rated load.

The cumulative nature of odometry error is particularly important. Because odometry continuously integrates motion measurements, errors do not remain constant. Instead, they grow over time and distance. This phenomenon is known as error propagation. Even small errors eventually accumulate into significant localization uncertainty.

Mathematical models are often used to characterize odometry uncertainty. Covariance matrices, probabilistic motion models, and stochastic error propagation techniques provide quantitative estimates of localization confidence. These models play a central role in modern localization algorithms such as Kalman Filters, Particle Filters, and graph-based optimization systems.

Understanding odometry error models enables engineers to design more robust navigation systems. By identifying dominant error sources and compensating for them through calibration, sensor fusion, and adaptive control techniques, localization performance can be significantly improved. Consequently, odometry error analysis remains a critical aspect of mobile robot system design.

### 5.3 IMU Fusion Basics

While wheel encoders provide valuable information about wheel motion, they cannot directly measure vehicle orientation, acceleration, or dynamic motion. To overcome these limitations, modern mobile robots integrate Inertial Measurement Units (IMUs) into their localization systems. IMU fusion combines encoder measurements with inertial sensor data to produce a more accurate estimate of the robot\'s state.

An IMU typically contains accelerometers, gyroscopes, and sometimes magnetometers. Accelerometers measure linear acceleration along multiple axes. Gyroscopes measure angular velocity, while magnetometers provide heading information relative to Earth\'s magnetic field. Together, these sensors provide continuous measurements of the robot\'s motion dynamics.

The primary advantage of IMUs is that they directly measure rotational motion. Wheel encoders estimate orientation indirectly through wheel movement, whereas gyroscopes measure angular velocity directly. This capability is especially valuable during turning maneuvers where encoder errors may become significant.

Consider a differential drive robot executing a turn. Encoder-based odometry estimates heading change using wheel displacement differences. However, wheel slip or uneven traction may introduce errors. The gyroscope independently measures the robot\'s rotational rate, providing an additional source of orientation information. Combining these measurements improves overall heading accuracy.

Accelerometers contribute information about vehicle acceleration and dynamic behavior. Although integrating acceleration measurements alone typically produces significant drift, accelerometer data provides valuable short-term motion information and supports state estimation during rapid maneuvers.

The challenge of IMU usage lies in sensor imperfections. Gyroscopes exhibit bias drift, meaning small measurement errors accumulate over time. Accelerometers are sensitive to vibration, noise, and gravity effects. Magnetometers are vulnerable to electromagnetic interference. Consequently, raw IMU measurements cannot generally be used directly for accurate localization.

Sensor fusion addresses these limitations by combining complementary sensor characteristics. Encoders provide reliable long-term distance measurements but suffer from slip-induced errors. IMUs provide high-frequency motion measurements but experience drift. By integrating both sensor types, their strengths can compensate for each other\'s weaknesses.

One of the most widely used fusion methods is the Kalman Filter. The Kalman Filter estimates the robot\'s state by combining sensor measurements with a mathematical motion model. The filter continuously predicts the robot\'s motion and corrects those predictions using incoming sensor data. Variants such as the Extended Kalman Filter (EKF) and Unscented Kalman Filter (UKF) are commonly used in robotics.

Modern AMR systems often implement encoder-IMU fusion within ROS and ROS 2 localization frameworks. Packages such as robot_localization combine wheel odometry, IMU measurements, GNSS data, LiDAR localization, and vision-based estimates into a unified state estimate. This multi-sensor approach significantly improves localization robustness.

IMU fusion is particularly important in environments where wheel slip is common. Industrial warehouses, manufacturing facilities, outdoor logistics yards, and autonomous vehicle platforms frequently encounter conditions that degrade encoder-only localization. IMU data provides an independent motion reference that improves resilience against these disturbances.

As autonomous systems continue to evolve, sensor fusion becomes increasingly important. Encoder measurements, IMUs, LiDARs, cameras, GNSS receivers, and radar systems are now routinely combined to achieve centimeter-level localization performance. Within this sensor ecosystem, IMU fusion serves as a critical bridge between low-level motion sensing and high-level autonomous navigation.

For this reason, understanding IMU fusion fundamentals is essential for anyone involved in mobile robot design, localization, navigation, or autonomous system development. It represents one of the most practical and widely deployed techniques for improving robot state estimation in real-world operating environments.

### 5.1 엔코더 기반 오도메트리

---

s = rθ

Δs = (ΔsR + ΔsL) / 2

Δθ = (ΔsR − ΔsL) / L

### 5.2 오도메트리 오차 모델

---

### 5.3 IMU 융합 기초
