## 01 48 V vs 72 V selection

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

01 48V vs 72V Selection

### 1.1 Voltage Decision Factor Analysis

---

### 1.2 48V Peak Current 104A Analysis Under Sequential Operation

---

### 1.3 Conditions Requiring 72V and Trade-offs

### 1.1 전압 결정 요소 분석 (Voltage Decision Factor Analysis)

---

적절한 시스템 전압(System Voltage)을 선택하는 것은 자율주행 이동로봇(Autonomous Mobile Robot, AMR)의 전기 아키텍처(Electrical Architecture)를 설계할 때 가장 중요한 의사결정 가운데 하나이다. 현재 산업용 이동로봇에서는 **48V**와 **72V** 배터리 시스템이 모두 널리 사용되고 있지만, 최적의 전압은 단순히 모터 출력(Motor Power)만으로 결정되지 않는다. 시스템 전압은 배터리 구성(Battery Configuration), 인버터 효율(Inverter Efficiency), 케이블 규격(Cable Sizing), 열관리(Thermal Management), 안전성(Safety), 충전 시스템(Charging Infrastructure), 부품 수급(Component Availability), 유지보수(Maintenance), 그리고 향후 플랫폼 확장성(Platform Scalability)까지 전체 차량 설계에 영향을 미친다. 따라서 시스템 전압은 단순한 전기 계산이 아니라 시스템 전체(System-level Optimization)를 고려하여 결정해야 한다.

가장 먼저 고려해야 하는 요소는 **전력 전달 효율(Power Transmission Efficiency)**이다. 전력(Power)은 전압(Voltage)과 전류(Current)의 곱으로 결정된다. 동일한 전력을 전달할 경우 전압이 높아질수록 필요한 전류는 감소한다. 전류가 감소하면 도체 저항에 의한 손실은 **I²R 법칙(I²R Relationship)**에 따라 크게 줄어든다. 즉 전류가 조금만 감소해도 케이블 발열(Cable Heating), 커넥터 온도 상승(Connector Temperature Rise), 인버터 도통 손실(Conduction Loss)이 크게 감소한다. 따라서 지속적으로 높은 출력을 사용하는 시스템에서는 일반적으로 높은 전압이 더 높은 전기 효율(Electrical Efficiency)을 제공한다.

그러나 효율만이 전압을 결정하는 기준은 아니다. 대부분의 산업용 AMR은 최대 출력(Maximum Power)으로 계속 운행하지 않는다. 실제 운전에서는 추진 모터(Propulsion Motor)가 부분 부하(Partial Load) 상태로 동작하는 시간이 훨씬 길며, 가속과 감속은 매우 짧은 시간 동안만 발생한다. 또한 조향(Steering), 위치 제어(Position Control), 센서(Sensor) 및 컴퓨팅 장치(Computing System)는 각각 다른 부하 특성을 가진다. 따라서 순간 최대 출력(Peak Power)만을 기준으로 시스템을 설계하면 실제 운행 조건보다 훨씬 과도한 용량의 전기 시스템이 구성되어 비용, 무게, 복잡성만 증가할 수 있다.

**부품의 공급성(Component Availability)** 역시 매우 중요한 요소이다. 현재 산업 시장에서는 48V 배터리, 모터 컨트롤러(Motor Controller), DC/DC 컨버터(DC/DC Converter), 접촉기(Contactor), 배터리 관리 시스템(Battery Management System, BMS), 충전기(Charger), 안전 장치(Safety Device) 등 매우 다양한 제품이 표준화되어 있다. 전동 지게차(Electric Forklift), AGV, 서비스 로봇(Service Robot), 통신 장비(Telecommunication Equipment), 에너지 저장 시스템(Energy Storage System) 등에서 오랫동안 사용되어 왔기 때문에 생산량이 많고 가격 경쟁력이 높으며 기술 지원도 풍부하다. 반면 72V 제품은 존재하지만 상대적으로 특수 시장(Specialized Market)에 사용되기 때문에 공급업체가 적고 가격도 높은 편이다.

**안전성(Safety)** 측면에서도 48V는 장점이 있다. 48V와 72V 모두 적절한 보호 회로가 필요하지만, 48V는 많은 국제 규격에서 위험 저전압(Hazardous Extra-Low Voltage) 기준 이하로 분류되는 경우가 많다. 따라서 절연(Insulation) 요구사항이 비교적 단순하고, 커넥터 설계가 쉬우며, 유지보수 시 감전(Electric Shock)의 위험도 낮다. 결과적으로 안전 인증(Safety Certification)과 유지보수 교육도 상대적으로 단순해질 수 있다.

**열관리(Thermal Management)**도 중요한 결정 요소이다. 72V는 동일 출력에서 전류가 감소하므로 케이블 단면적(Cable Cross Section)을 줄일 수 있고 발열도 감소한다. 그러나 대부분의 산업용 AMR은 최대 출력으로 지속 운행하지 않기 때문에 실제 열관리 측면에서의 차이는 예상보다 크지 않은 경우가 많다. 적절한 케이블 규격과 고효율 전력전자(Power Electronics), 그리고 스마트 전류 관리(Current Management)를 적용하면 48V 시스템도 산업용 열관리 요구사항을 충분히 만족할 수 있다.

**배터리 구조(Battery Architecture)** 역시 전압 선택에 영향을 준다. 48V 리튬인산철 배터리(Lithium Iron Phosphate, LFP)는 72V보다 직렬 연결되는 셀(Cell)의 개수가 적다. 셀 수가 적으면 BMS 설계가 단순해지고 셀 밸런싱(Cell Balancing)이 쉬워지며 제조 공정도 단순해진다. 또한 장기간 사용 시 셀 간 불균형(Cell Mismatch) 발생 가능성도 감소한다. 유지보수와 배터리 교체 역시 보다 간단하게 수행할 수 있다.

반면 **확장성(Scalability)**도 함께 고려해야 한다. 향후 더 큰 적재 중량(Payload), 더 높은 주행 속도(Travel Speed), 더 많은 보조 장치(Auxiliary Equipment)를 사용할 계획이라면 48V의 실질적인 한계에 도달할 수 있다. 따라서 현재는 48V를 사용하더라도 향후 72V로 쉽게 확장할 수 있는 모듈형 전기 인터페이스(Modular Electrical Interface)를 설계하는 것이 장기적인 플랫폼 경쟁력 확보에 도움이 된다.

결국 시스템 전압은 단순한 전기 계산이 아니라 실제 운행 시나리오(Mission Profile)를 기준으로 결정해야 한다. 적절한 순차 운전(Sequential Operation), 스마트 전력 관리(Intelligent Power Management), 산업용 적재 중량을 사용하는 대부분의 AMR에서는 성숙한 48V 시스템이 우수한 성능을 제공한다. 반면 지속적인 고출력 운전, 대형 차량, 향후 플랫폼 확장성이 중요한 경우에는 72V 시스템이 더 적합할 수 있다.

### 1.2 순차 운전(Sequential Operation) 조건에서 48V 최대 전류 104A 분석 (48V Peak Current 104A Analysis Under Sequential Operation)

---

48V 시스템을 설계할 때 가장 자주 제기되는 질문 가운데 하나는 여러 전기 장치가 동시에 동작하면 전류(Current)가 너무 커지는 것이 아닌가 하는 점이다. 추진 모터, 조향 모터, 산업용 컴퓨터(Industrial Computer), LiDAR, 카메라(Camera), 통신 장비(Communication Equipment), 배터리 관리 시스템(BMS), 보조 장치(Auxiliary Device) 등을 모두 합산하면 매우 큰 전류가 필요한 것처럼 보인다. 그러나 실제 산업용 AMR은 이러한 모든 장치가 동시에 최대 출력으로 동작하는 경우가 거의 없으며, 대부분 **순차 운전(Sequential Operation)** 방식을 사용하여 부하를 분산시킨다.

순차 운전은 현대 AMR의 전력 관리(Power Management)의 핵심 개념이다. 제어기(Motion Controller)는 모든 액추에이터(Actuator)를 동시에 최대 출력으로 동작시키지 않고, 주요 부하가 서로 다른 시점에 발생하도록 제어한다. 예를 들어 차량이 가속할 때는 추진 모터가 우선적으로 큰 출력을 사용하며, 조향 동작은 대부분 그 직전에 완료된다. 일정 속도로 주행하는 동안에는 추진 모터의 부하는 크게 감소하고, 조향 모터는 방향을 변경할 때만 순간적으로 동작한다. 정밀 도킹 단계에서는 추진 출력은 매우 낮아지고 조향 정밀도가 더욱 중요해진다. 따라서 실제 운행에서는 모든 장치의 최대 전류가 동시에 발생하지 않는다.

예를 들어 48V 기반 산업용 AMR을 생각해 보면, 급가속 시에는 추진 모터가 높은 전류를 소비하지만 조향 모터는 방향을 변경하는 짧은 시간 동안만 동작한다. 목표 조향각에 도달하면 유지 토크(Holding Torque)는 매우 작아진다. 반면 산업용 컴퓨터, LiDAR, 카메라, 통신 장치, 안전 제어기(Safety Controller)는 차량 가속 여부와 관계없이 거의 일정한 전력을 소비한다. 따라서 이들 장치는 순간 최대 전류 증가에 미치는 영향이 제한적이다.

이러한 순차 운전을 적용하면 약 **104A 수준의 최대 전류(Peak Current)**는 48V 시스템에서도 충분히 현실적인 수준이다. 이러한 최대 전류는 매우 짧은 시간 동안만 발생하며, 연속 운전(Continuous Operation)에서는 훨씬 낮은 평균 전류(Average Current)가 흐른다. 적절한 방전 성능을 가진 리튬인산철 배터리는 이러한 순간 방전(Peak Discharge)을 충분히 지원할 수 있으며, 배터리 전압도 안정적으로 유지할 수 있다. 현대의 LFP 배터리는 연속 방전 전류보다 훨씬 높은 순간 방전 전류를 허용하는 경우가 많아 추가적인 안전 여유(Safety Margin)를 제공한다.

**배터리 관리 시스템(BMS)**은 이러한 운용을 더욱 안전하게 만든다. BMS는 전류(Current), 전압(Voltage), 온도(Temperature), 셀 밸런싱(Cell Balancing), 방전 한계(Discharge Limit)를 지속적으로 감시한다. 만약 과도한 부하가 발생하면 차량 가속을 일시적으로 제한하거나, 일부 장치의 동작을 순차적으로 조정하거나, 중요한 시스템에 우선적으로 전력을 공급하는 방식으로 배터리를 보호한다.

모터 컨트롤러(Motor Controller) 역시 전류 제한(Current Limiting) 기능을 제공한다. 서보 드라이브(Servo Drive)는 무제한 전류를 허용하지 않고 배터리 상태, 온도, 모터 특성, 차량 견인력(Traction)에 따라 토크를 자동으로 제한한다. 따라서 순간 전류도 예측 가능한 범위 안에서 관리된다. 또한 회생 제동(Regenerative Braking)은 감속 시 운동 에너지(Kinetic Energy)를 다시 배터리로 회수하여 가속 시 소비된 에너지 일부를 보상한다.

케이블과 커넥터 역시 이러한 최대 전류를 고려하여 설계된다. 연속 전류(Continuous Current), 순간 전류(Transient Current), 주변 온도(Ambient Temperature), 전압 강하(Voltage Drop), 커넥터 저항(Connector Resistance), 허용 온도 상승(Allowable Temperature Rise)을 모두 고려하여 적절한 규격을 선정한다. 적절한 산업용 케이블과 커넥터를 사용하면 약 100A 수준의 순간 전류는 충분히 안전하게 처리할 수 있다.

열 특성(Thermal Behavior) 역시 이러한 구조를 뒷받침한다. 순간 최대 전류는 매우 짧은 시간 동안만 흐르므로 평균 발열(Average Heating)은 연속 최대 전류를 기준으로 계산한 값보다 훨씬 작다. 따라서 적절한 듀티 사이클(Duty Cycle) 관리가 이루어진다면 비교적 작은 전기 시스템으로도 충분한 열관리가 가능하다.

결과적으로 단순히 최대 전류만 보고 시스템을 설계하면 필요 이상으로 과도한 설계가 이루어질 수 있다. 순차 운전, 스마트 전력 스케줄링(Intelligent Power Scheduling), 적응형 모터 제어(Adaptive Motor Control), BMS를 함께 적용하면 실제 전기적 부하는 크게 감소한다. 따라서 최고 속도 약 **20 km/h 이하**, 스마트 전력 관리가 적용된 대부분의 산업용 AMR에서는 **104A 수준의 순간 최대 전류를 지원하는 48V 시스템**만으로도 충분한 성능을 확보할 수 있으며, 비용, 무게, 효율, 시스템 단순성 측면에서도 가장 균형 잡힌 선택이 된다.

### 1.3 72V가 필요한 조건과 트레이드오프(Trade-offs) (Conditions Requiring 72V and Trade-offs)

48V 시스템은 대부분의 산업용 AMR 요구사항을 만족하지만, 일부 응용 분야에서는 **72V 시스템**이 더욱 적합할 수 있다. 중요한 점은 단순히 "전압이 높을수록 좋다"는 이유가 아니라 실제 운용 조건(Mission Requirement), 연속 출력(Continuous Power), 열관리(Thermal Limitation), 향후 플랫폼 확장성(Platform Scalability)을 종합적으로 고려하여 선택해야 한다는 것이다. 72V는 분명한 기술적 장점을 제공하지만 동시에 시스템 복잡성과 비용도 증가한다.

72V를 선택하는 가장 대표적인 이유는 **지속적인 고출력 추진(Sustained High-power Propulsion)**이다. 1톤 이상의 중량을 운반하거나, 장시간 경사로(Ramp)를 오르거나, 거친 실외 노면(Rough Outdoor Terrain)을 주행하는 차량은 지속적으로 높은 모터 출력을 요구한다. 이러한 환경에서는 높은 전압을 사용하여 전류를 줄이면 케이블 손실, 커넥터 발열, 인버터의 열부하를 크게 감소시킬 수 있다.

**고속 실외 자율주행 차량(High-speed Outdoor Autonomous Vehicle)**도 72V의 대표적인 적용 대상이다. 차량 속도가 증가할수록 공기 저항(Aerodynamic Drag), 구름 저항(Rolling Resistance), 구동계 손실(Drivetrain Loss)이 빠르게 증가한다. 일반적으로 **20\~25 km/h 이상의 지속적인 고속 주행**에서는 실내 AMR보다 훨씬 높은 전력이 필요하며, 이 경우 72V는 낮은 전류로 동일한 출력을 공급하여 효율을 높이고 열관리를 쉽게 만든다.

또한 **고출력 보조 장치(Auxiliary System)**가 많은 플랫폼도 72V를 고려할 수 있다. 대형 로봇팔(Robotic Manipulator), 유압 장치(Hydraulic Actuator), 산업용 검사 장비(Industrial Inspection Equipment), 고성능 GPU 컴퓨터(High-performance Computing Platform), 능동 서스펜션(Active Suspension), 대용량 냉각 시스템(Environmental Conditioning Unit) 등을 동시에 사용하는 경우에는 전체 전력 요구량이 48V 시스템의 실질적인 한계를 넘어설 수 있다. 이때 72V는 보다 안정적인 전력 공급을 가능하게 한다.

장거리 실외 운행(Long-distance Outdoor Operation)도 72V의 장점을 크게 활용할 수 있는 분야이다. 전류가 감소하면 저항 손실이 줄어들어 전체 에너지 효율이 향상되며, 특히 장시간 연속 운행하는 대형 물류 차량에서는 장기적인 운영 비용 절감 효과를 얻을 수 있다.

그러나 72V에는 여러 가지 **트레이드오프(Trade-off)**가 존재한다.

첫 번째는 **부품 가격(Component Cost)**이다. 72V를 지원하는 모터 컨트롤러, BMS, 충전기, DC/DC 컨버터는 48V보다 선택 가능한 제품이 적고 가격도 높다.

두 번째는 **배터리 구조(Battery Architecture)**이다. 72V는 더 많은 셀을 직렬로 연결해야 하므로 BMS 설계가 복잡해지고 셀 밸런싱(Cell Balancing)도 더욱 어려워진다.

세 번째는 **안전성(Safety)**이다. 높은 전압은 더 높은 절연 성능(Insulation), 강화된 커넥터(Robust Connector), 보다 엄격한 안전 절차(Safety Procedure)를 요구하며, 유지보수 인력도 추가적인 전기 안전 교육(Electrical Safety Training)을 받아야 한다.

유지보수(Maintenance) 역시 복잡해진다. 진단 절차(Diagnostic Procedure)가 증가하고 예비 부품(Spare Parts)의 조달 기간도 길어질 수 있다. 일부 국가에서는 인증(Certification) 절차도 더욱 까다로워질 수 있다.

**충전 인프라(Charging Infrastructure)**도 함께 변경되어야 한다. 기존의 48V 충전기를 그대로 사용할 수 없으며, 새로운 충전기, 충전 커넥터, 통신 인터페이스, BMS 설정이 모두 필요하다. 따라서 48V와 72V 차량이 혼재된 플릿(Fleet)을 운영하면 관리 복잡성이 증가한다.

경제성(Economic Analysis)을 고려하면 72V는 연속적인 고출력 운전에서만 초기 투자 비용을 회수할 수 있는 경우가 많다. 대부분의 시간을 부분 부하로 운행하는 산업용 AMR에서는 48V가 훨씬 경제적이다. 반면 대형 실외 물류 차량, 고출력 산업용 운반 차량, 특수 목적 자율주행 플랫폼에서는 효율 향상과 열관리 개선 효과가 초기 비용 증가를 충분히 상쇄할 수 있다.

따라서 **48V와 72V의 선택은 단순한 전압 비교가 아니라 시스템 전체의 최적화 문제**이다. 작업 시나리오(Mission Profile), 적재 중량(Payload), 주행 속도(Travel Speed), 보조 장치 전력(Auxiliary Power Demand), 열관리(Thermal Performance), 배터리 성능(Battery Capability), 유지보수 전략(Maintenance Strategy), 부품 생태계(Component Ecosystem), 충전 인프라(Charging Infrastructure), 총소유비용(Total Cost of Ownership, TCO)을 모두 함께 고려해야 한다.

현재 대부분의 **실내 산업용 AMR**에서는 **순차 운전(Sequential Operation)**과 **스마트 전력 관리(Intelligent Power Management)**를 적용한 **48V 시스템이 성능, 비용, 안전성, 단순성의 균형이 가장 뛰어난 선택**이다. 반면 **대형 실외 AMR**, **고속 자율주행 플랫폼**, **고출력 특수 장비**와 같이 실제 요구 전력이 48V 시스템의 실질적인 한계를 초과하는 경우에만 **72V 시스템**이 가장 적합한 선택이 된다.

## 02 Sequential operation power analysis

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

### 2.1 Drive Mode Power Consumption Average 2605W

---

### 2.2 Scan Mode Power Consumption 1410W

---

### 2.3 Weighted Average Power 1736W Derivation

### 2.1 주행 모드 평균 소비전력 2605W (Drive Mode Power Consumption Average 2605W)

---

자율주행 이동로봇(Autonomous Mobile Robot, AMR)의 전력 분석(Power Analysis)은 단순한 이론적 최대 부하(Worst-case Operation)를 기준으로 수행해서는 안 된다. 실제 산업 환경에서 AMR은 주행(Drive), 도킹(Docking), 스캔(Scanning), 대기(Waiting), 통신(Communication) 등 다양한 운용 상태를 반복적으로 전환한다. 각각의 운용 모드는 서로 다른 전력 소비 특성을 가지며, 모든 장치가 동시에 최대 전력을 사용하는 경우는 거의 발생하지 않는다. 따라서 각 운용 모드별 평균 소비전력(Average Power Consumption)을 분석하는 것이 배터리 용량(Battery Capacity), 열관리(Thermal Management), 시스템 최적화(System Optimization)를 위한 가장 현실적인 접근 방법이다.

**주행 모드(Drive Mode)**는 AMR이 작업장(Workstation), 창고(Warehouse), 충전 스테이션(Charging Station), 검사 위치(Inspection Point) 사이를 이동하면서 실제 운반 작업을 수행하는 상태를 의미한다. 이 구간에서는 추진 모터(Propulsion Motor)가 가장 큰 전력 소비원이 된다. 추진 모터는 차량의 관성(Inertia), 구름 저항(Rolling Resistance), 바닥의 요철(Floor Irregularity), 경사로(Ramp) 등을 극복하기 위해 지속적으로 높은 출력을 발생시킨다.

반면 **조향 모터(Steering Motor)**는 차량이 방향을 변경할 때만 동작한다. 목표 조향각(Steering Angle)에 도달한 이후에는 유지 토크(Holding Torque)만 필요하므로 소비전력이 급격히 감소한다. 따라서 추진 모터는 연속적으로 동작하지만 조향 모터는 간헐적으로만 작동하며, 전체 평균 소비전력에서 차지하는 비중은 상대적으로 작다.

주행 중에는 **온보드 컴퓨팅 플랫폼(Onboard Computing Platform)**도 지속적으로 동작한다. 산업용 Edge 컴퓨터는 **SLAM(Simultaneous Localization and Mapping)**, 센서 융합(Sensor Fusion), 경로 계획(Path Planning), 장애물 회피(Obstacle Avoidance), 궤적 생성(Trajectory Generation), 플릿 통신(Fleet Communication), 안전 모니터링(Safety Monitoring), 차량 진단(Vehicle Diagnostics)을 동시에 수행한다. 최근 산업용 AMR은 실시간 AI 알고리즘을 실행하기 위해 고성능 CPU와 GPU를 사용하지만, 이러한 컴퓨팅 장치는 차량의 가속 여부와 관계없이 비교적 일정한 전력을 소비한다. 따라서 컴퓨팅 시스템은 주행 모드 동안 안정적인 기본 부하(Base Load)를 형성한다.

**환경 인식 센서(Perception Sensor)** 역시 주행 중 지속적으로 동작한다. LiDAR는 고속으로 주변 환경을 스캔하여 위치추정(Localization)과 장애물 인식을 수행하며, RGB 카메라(RGB Camera), 깊이 카메라(Depth Camera), IMU(Inertial Measurement Unit), 초음파 센서(Ultrasonic Sensor), GNSS 수신기, 안전 LiDAR(Safety Laser Scanner) 등도 동시에 운용된다. 각각의 센서는 개별적으로는 작은 전력을 소비하지만, 모든 센서를 합산하면 전체 시스템에서는 상당한 소비전력을 차지하게 된다.

**통신 장치(Communication Equipment)**도 지속적으로 전력을 사용한다. 산업용 Wi-Fi, Private 5G, Ethernet Switch, CAN 인터페이스, EtherCAT Master, 배터리 관리 시스템(BMS), 분산 I/O(Distributed I/O)는 플릿 관리 시스템(Fleet Management System), 다른 로봇, 클라우드 서버, 안전 시스템과 지속적으로 데이터를 교환한다. 이러한 장치는 차량이 움직이든 정지하든 거의 일정한 소비전력을 유지한다.

또한 **보조 전기 시스템(Auxiliary Electrical System)**도 전체 소비전력을 증가시키는 요소이다. DC/DC 컨버터는 센서, 임베디드 제어기(Embedded Controller), 통신 장치, 조명(Lighting), 경고등(Warning Indicator), 비상 회로(Emergency Circuit), 사용자 인터페이스(User Interface)에 안정적인 저전압 전원을 공급한다. 냉각 팬(Cooling Fan), 열관리 장치(Thermal Management System), 브레이크 제어기(Brake Electronics), 전력 분배 장치(Power Distribution Module) 역시 필요에 따라 지속적으로 동작한다.

이러한 모든 구성 요소를 실제 산업 현장의 듀티 사이클(Duty Cycle)에 맞추어 분석하면 **약 2,605W의 평균 소비전력**은 중형 및 대형 산업용 AMR에서 충분히 현실적인 수치이다. 이 값은 추진 모터의 지속적인 운전과 함께 컴퓨팅, 센서, 통신, 보조 장치가 동시에 동작하는 상황을 반영한 평균값이다. 물론 가속이나 장애물 회피 시 순간적으로 전력이 증가할 수 있지만, 이러한 피크 전력(Peak Power)은 매우 짧은 시간 동안만 발생하므로 장기적인 평균 소비전력에는 큰 영향을 주지 않는다.

여기서 **순차 운전(Sequential Operation)**이 중요한 역할을 한다. 추진 모터의 최대 출력은 조향 모터의 최대 출력이나 센서 처리의 최대 부하와 동시에 발생하지 않는다. 제어기는 전력 소비가 시간적으로 분산되도록 스케줄링(Power Scheduling)을 수행하여 불필요한 최대 부하의 중첩을 방지한다. 결과적으로 순간적으로는 높은 전력이 필요하더라도 평균 전류(Current)는 배터리와 전기 시스템이 충분히 감당할 수 있는 범위 안에서 유지된다.

이와 같은 평균 소비전력은 배터리 용량 선정(Battery Capacity Estimation), 열설계(Thermal Design), 충전기 용량(Charger Sizing), 케이블 규격(Cable Selection), 인버터(Inverter) 선정, 그리고 운행 가능 시간(Runtime Prediction)을 계산하는 가장 중요한 입력 데이터가 된다. 실제 운행 조건을 기반으로 설계하면 과도한 용량의 전기 시스템을 피할 수 있으며, 비용과 중량을 줄이면서도 높은 효율을 달성할 수 있다.

### 2.2 스캔 모드 소비전력 1410W (Scan Mode Power Consumption 1410W)

---

산업용 AMR은 목적지에 도착한 이후 운반 작업에서 검사(Inspection) 또는 데이터 수집(Data Acquisition) 단계로 전환되는 경우가 많다. 이러한 상태를 **스캔 모드(Scan Mode)**라고 한다. 스캔 모드에서는 차량의 이동이 거의 없거나 완전히 정지한 상태에서 다양한 센서를 이용하여 주변 환경이나 검사 대상의 데이터를 정밀하게 수집한다. 추진 전력은 크게 감소하지만, 반대로 센서 처리와 AI 연산은 증가하게 된다.

스캔 모드에서 가장 큰 변화는 **추진 모터의 소비전력 감소**이다. 목적지에 도착하면 구동 모터는 정지하거나 매우 작은 위치 보정(Position Correction)만 수행한다. 조향 모터 역시 정밀 위치 보정을 위한 미세한 움직임만 수행하므로 대부분의 시간 동안 거의 전력을 소비하지 않는다. 따라서 주행 모드에서 가장 큰 전력 소비원이었던 추진 계통은 스캔 모드에서는 거의 전력을 사용하지 않는다.

반면 **센서 시스템(Sensor System)**의 활용도는 크게 증가한다. LiDAR는 최고 해상도(High-resolution Scanning)로 주변 환경을 반복적으로 스캔하며, 산업용 카메라는 일정한 조명 아래에서 고해상도 이미지를 촬영한다. 구조광 센서(Structured-light Sensor), 깊이 카메라(Depth Camera), 레이저 프로파일러(Laser Profiler), 열화상 카메라(Thermal Camera), 3차원 검사 장비(3D Inspection System) 등이 동시에 동작하여 매우 많은 데이터를 생성한다. 또한 검사 품질을 높이기 위해 추가적인 조명 시스템(Lighting System)이 동작하는 경우도 많다.

**인공지능 처리(AI Processing)**의 부하도 증가한다. 산업용 Edge GPU는 객체 인식(Object Detection), 결함 검출(Defect Detection), 의미론적 분할(Semantic Segmentation), 3차원 재구성(3D Reconstruction), 치수 측정(Dimensional Measurement), 이상 탐지(Anomaly Detection), 예지보전(Predictive Maintenance) 알고리즘을 수행한다. GPU의 사용률은 주행 모드보다 높아질 수 있지만, 추진 모터가 거의 정지하기 때문에 전체 시스템 소비전력은 오히려 감소한다.

**데이터 관리(Data Management)**도 스캔 모드에서 중요한 역할을 한다. 수집된 대용량 검사 데이터는 고속 SSD에 저장되고, 이후 공장 서버나 클라우드 분석 시스템으로 전송된다. 데이터 압축(Data Compression), 암호화(Encryption), 동기화(Synchronization), MES(Manufacturing Execution System)와의 통신도 동시에 수행된다.

**통신 시스템(Communication System)**은 주행 모드와 동일하게 계속 동작한다. 검사 결과, 차량 상태, 환경 데이터, 진단 정보는 플릿 관리 시스템과 상위 제어 시스템으로 지속적으로 전송된다. 따라서 통신 장치는 이동 여부와 관계없이 거의 일정한 소비전력을 유지한다.

**열관리(Thermal Management)**의 특성도 달라진다. 추진 모터는 거의 열을 발생시키지 않지만 GPU, CPU, SSD와 같은 연산 장치는 지속적으로 높은 열을 발생시킨다. 따라서 냉각 팬(Cooling Fan)이나 액체 냉각(Liquid Cooling)은 차량 속도가 아니라 프로세서의 온도에 따라 제어된다. 지능형 열관리 시스템은 필요한 경우에만 냉각 장치를 동작시켜 불필요한 전력 소비를 줄인다.

이러한 실제 운용 특성을 고려하면 **약 1,410W의 평균 소비전력**은 고성능 산업용 검사 로봇의 스캔 모드에서 매우 현실적인 값이다. 주행 모드보다 소비전력이 감소하는 가장 큰 이유는 추진 모터의 소비전력이 거의 없어지기 때문이다. 반면 센서, 컴퓨팅, 통신, 안전 시스템은 계속 동작하므로 일정한 전력은 지속적으로 필요하다.

스캔 모드는 현대 산업용 AMR의 중요한 특징을 보여준다. 즉, 이동 단계에서는 전력이 기계적인 운동(Mechanical Motion)에 사용되지만, 검사 단계에서는 대부분의 에너지가 정보 처리(Information Processing)에 사용된다. 이러한 전력 소비 특성을 정확히 분석하면 검사 중심의 AMR에서 배터리 사용 시간(Runtime), 열관리, 에너지 스케줄링을 보다 정확하게 설계할 수 있다.

### 2.3 가중 평균 소비전력 1736W 산출 과정 (Weighted Average Power 1736W Derivation)

배터리 용량(Battery Capacity)은 개별 운용 모드가 아니라 **전체 미션(Mission Profile)**을 기준으로 결정되어야 한다. 산업용 AMR은 주행, 스캔, 도킹, 대기, 통신, 충전을 반복적으로 수행한다. 따라서 전체 에너지 소비를 계산하기 위해서는 각 운용 모드의 소비전력과 해당 모드가 전체 운행 시간에서 차지하는 비율(Time Ratio)을 함께 고려해야 한다. 이러한 방법이 **가중 평균 소비전력(Weighted Average Power)** 계산이다.

가중 평균 소비전력의 개념은 매우 단순하다. 주행 모드나 스캔 모드 중 하나만 계속 수행한다고 가정하는 것이 아니라, 실제 운행 시간에서 각각이 차지하는 비율(Duty Cycle)을 적용한다. 이후 각 소비전력에 해당 시간 비율을 곱하여 합산하면 전체 미션에서의 평균 소비전력을 얻을 수 있다. 이러한 방식은 실제 산업 환경을 가장 잘 반영하는 에너지 계산 방법이다.

예를 들어 하나의 산업용 검사 로봇이 전체 운행 시간 중 **25%는 주행 모드**, **75%는 스캔 모드**를 수행한다고 가정하자. 앞에서 계산한 평균 소비전력을 적용하면 다음과 같은 계산이 가능하다.

**가중 평균 소비전력 = (2,605W × 0.25) + (1,410W × 0.75)**

이를 계산하면 전체 미션의 평균 소비전력은 **약 1,736W**가 된다.

이 결과는 단순한 산술 계산 이상의 의미를 가진다. 추진 모터는 순간적으로 높은 전력을 소비하지만 전체 운행 시간에서는 검사 작업이 훨씬 긴 비중을 차지하기 때문에 실제 평균 소비전력은 주행 모드 소비전력보다 훨씬 낮아진다. 따라서 배터리 용량을 결정할 때는 순간 최대 출력이 아니라 실제 미션 비율을 반영해야 한다.

가중 평균 소비전력은 **배터리 사용 시간(Runtime)** 계산에도 매우 중요하다. 배터리의 사용 가능한 에너지(Usable Energy)를 가중 평균 소비전력으로 나누면 실제 운행 가능한 시간을 매우 정확하게 예측할 수 있다. 이는 순간 최대 출력이나 정격 출력만을 사용하는 계산보다 훨씬 현실적인 결과를 제공한다.

**열관리(Thermal Analysis)**에서도 동일한 원리가 적용된다. 전기 부품은 순간적인 최대 출력보다 장시간의 평균 발열(Average Heat Dissipation)에 의해 온도가 결정된다. 따라서 냉각 시스템 역시 가중 평균 소비전력을 기준으로 설계하면 팬(Fan)의 소비전력을 줄이고 시스템 중량과 복잡성도 감소시킬 수 있다.

**충전 전략(Charging Strategy)** 역시 가중 평균 소비전력을 기준으로 수립된다. 플릿 관리 시스템은 남은 배터리 용량(Remaining Battery Capacity), 예상 소비전력, 운행 시간을 기반으로 충전 시점을 결정한다. 보다 정확한 평균 소비전력은 충전기 활용률을 높이고 대기 시간을 줄이며 전체 플릿(Fleet)의 생산성을 향상시킨다.

실제 운행에서는 대기(Idle), 정밀 도킹(Precision Docking), 비상 정지(Emergency Stop), 유지보수(Maintenance Mode), 원격 진단(Remote Diagnostics) 등 다양한 운용 상태가 추가될 수 있다. 이러한 모든 상태에 대해 각각의 소비전력과 운용 시간을 적용하면 더욱 정확한 가중 평균 소비전력을 계산할 수 있다.

물론 실제 운행에서는 적재 중량(Payload), 바닥 상태(Floor Condition), 가속 패턴(Acceleration Profile), 주변 온도(Ambient Temperature), 통신량(Communication Activity), AI 연산량(Computing Workload)에 따라 순간 소비전력이 달라질 수 있다. 그러나 장시간 운행에서는 이러한 변화가 평균화되므로 가중 평균 소비전력은 매우 안정적인 설계 기준이 된다. 또한 실제 플릿 운행 데이터를 지속적으로 수집하면 듀티 사이클을 더욱 정확하게 보정하여 배터리 용량과 에너지 예측 정확도를 지속적으로 향상시킬 수 있다.

결과적으로 **약 1,736W의 가중 평균 소비전력**은 실제 미션 기반 전기 설계(Mission-oriented Electrical Design)의 중요성을 잘 보여준다. 순간 최대 전력만을 기준으로 배터리를 설계하는 것이 아니라, 전체 운용 사이클을 반영하면 더 높은 효율, 더 낮은 비용, 우수한 열관리, 그리고 정확한 운행 시간 예측이 가능해진다. 앞으로 산업용 AMR이 더욱 지능화되고 미션이 복잡해질수록 이러한 **가중 평균 에너지 분석(Weighted Average Energy Analysis)**은 전기 시스템 최적화(Electrical System Optimization)의 핵심 설계 방법으로 더욱 중요해질 것이다.

## 03 Multi-axis power distribution

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

### 3.1 Power Distribution for 4 Steer Drive Modules

---

### 3.2 DC-DC Converter Design

---

### 3.3 Dedicated Payload Power Line Example 1200W

### 3.1 4개의 스티어 드라이브 모듈을 위한 전력 분배 (Power Distribution for 4 Steer Drive Modules)

---

4륜 스티어 드라이브(Steer Drive) 기반 자율주행 이동로봇(Autonomous Mobile Robot, AMR)의 전력 분배(Power Distribution) 구조는 기존 차동 구동(Differential Drive) 방식보다 훨씬 복잡하다. 차동 구동은 두 개의 추진 모터(Propulsion Motor)에 전력을 공급하면 되지만, 4륜 스티어 드라이브는 **4개의 구동 모터(Drive Motor)**와 **4개의 조향 모터(Steering Motor)**, 그리고 온보드 컴퓨팅(Onboard Computing), 환경 인식 센서(Perception Sensor), 통신 장치(Communication Equipment), 안전 시스템(Safety System), 배터리 관리 시스템(Battery Management System, BMS), 각종 보조 장치(Auxiliary Subsystem)까지 모두 안정적으로 전력을 공급해야 한다.

따라서 전력 분배 시스템의 목적은 단순히 전기를 공급하는 것이 아니라 **안정적인 전압(Stable Voltage)**, **균형 잡힌 전류 분배(Balanced Current Flow)**, **높은 신뢰성(Reliability)**, **고장 분리(Fault Isolation)**, **결정론적 시스템 동작(Deterministic System Behavior)**을 보장하는 것이다.

전력 분배는 배터리 팩(Battery Pack)에서 시작된다. 일반적으로 48V 또는 72V 리튬인산철 배터리(Lithium Iron Phosphate, LFP)와 BMS로 구성된다. BMS는 배터리 전압(Pack Voltage), 셀 전압(Cell Voltage), 전류(Current), 온도(Temperature), 절연 상태(Insulation Status), 셀 밸런싱(Cell Balancing), 이상 상태(Fault Condition)를 지속적으로 감시한다.

배터리에서 나온 전력은 메인 컨택터(Main Contactor)와 과전류 보호 장치(Overcurrent Protection Device)를 통과한 후 **주 전력 분배 장치(Main Power Distribution Unit)**로 전달된다. 이 장치는 전체 시스템의 전기 허브(Electrical Hub) 역할을 수행하며, 각 서브시스템으로 전력을 분배하는 동시에 과전류 보호, 비상 차단(Emergency Isolation), 진단 기능(Diagnostic Function)을 제공한다.

각 스티어 드라이브 모듈은 독립된 전원 라인(Independent Power Branch)을 통해 전력을 공급받는다. 각 라인에는 개별 퓨즈(Fuse) 또는 전자식 차단기(Electronic Circuit Breaker)가 설치된다. 이러한 구조는 하나의 모듈에서 단락(Short Circuit)이나 과전류가 발생하더라도 다른 모듈까지 영향을 받지 않도록 한다. 특정 조향 모듈이 고장 나더라도 나머지 모듈은 제한된 성능으로 계속 운행할 수 있으며, 이는 차량의 안전 전략(Vehicle Safety Strategy)에 따라 제어된다. 이러한 모듈형 전력 분배(Modular Power Distribution)는 시스템 신뢰성을 크게 향상시키고 유지보수를 단순화한다.

각 스티어 드라이브 모듈 내부에서는 **추진(Propulsion)**과 **조향(Steering)**이 동일한 DC 전원을 사용하지만 전기적으로는 분리되어 있다. 추진 모터는 고출력 서보 드라이브(Servo Drive)가 제어하고, 조향 모터는 별도의 서보 앰프(Servo Amplifier)가 제어한다. 두 제어기는 EtherCAT과 같은 실시간 산업용 네트워크(Real-time Industrial Network)를 통해 지속적으로 동기화 정보를 교환하며, 가속, 감속, 회전, 정밀 도킹 시 차량 전체의 움직임을 조율한다.

**부하 균형(Load Balancing)** 역시 중요한 요소이다. 직선 주행에서는 4개의 구동 모듈이 비교적 균등하게 추진력을 분담한다. 그러나 회전 시에는 스티어링 기하학(Steering Geometry)에 따라 바깥쪽 바퀴와 안쪽 바퀴의 이동 거리가 달라진다. 이에 따라 바퀴마다 필요한 토크(Torque)와 소비전력이 달라진다. 모터 제어기는 차량 운동학(Vehicle Kinematics), 노면 상태(Surface Condition), 적재물 위치(Payload Position)를 고려하여 토크를 동적으로 분배하며, 불필요한 에너지 소비를 줄이고 차량의 안정성을 유지한다.

전력 분배 시스템은 순간적인 부하 변화도 처리해야 한다. 급가속(Acceleration), 경사로 주행(Hill Climbing), 장애물 통과(Obstacle Traversal), 긴급 회피(Emergency Avoidance) 시에는 추진 모터의 소비전력이 증가한다. 그러나 **순차 운전(Sequential Operation)** 덕분에 추진 모터와 조향 모터가 동시에 최대 출력을 사용하는 경우는 거의 없다. 이러한 부하 분산 효과 덕분에 케이블, 컨택터, 배터리를 과도하게 크게 설계하지 않아도 충분한 성능을 확보할 수 있다.

**보호 시스템(Protection Coordination)**도 매우 중요하다. 각 서보 드라이브는 전류 제한(Current Limiting), 과전압 보호(Overvoltage Protection), 저전압 감시(Undervoltage Monitoring), 과열 보호(Thermal Protection), 회생 제동(Regenerative Braking)을 자체적으로 수행한다. BMS는 전체 배터리의 에너지 흐름을 감시하며, 각 서브시스템은 개별 보호 장치(Local Protection Device)를 통해 독립적으로 보호된다. 이러한 계층형 보호 구조(Hierarchical Protection Architecture)는 고장의 전파를 방지하면서도 가능한 한 차량의 운행을 유지하도록 한다.

여러 개의 인버터(Inverter)가 동시에 동작하면 **전자기 간섭(Electromagnetic Interference, EMI)**도 중요한 문제가 된다. 고속 스위칭은 센서, 통신 장치, 정밀 전자기기에 영향을 줄 수 있다. 따라서 적절한 접지(Grounding), 차폐 케이블(Shielded Cable), 차동 통신(Differential Communication), EMI 필터(Filter), 전력선 배치(Power Routing)를 적용하여 전자기 노이즈를 최소화해야 한다.

확장성(Scalability)도 설계 단계에서 고려해야 한다. 모듈형 전력 분배 구조를 사용하면 향후 더 큰 적재 중량(Payload), 추가 스티어 모듈, 로봇팔(Robotic Manipulator), 검사 장비(Inspection System), 산업용 특수 장비를 쉽게 추가할 수 있다. 표준화된 커넥터(Standard Connector), 모듈형 버스바(Modular Busbar), 설정 가능한 보호 장치는 플랫폼 확장을 쉽게 하면서도 생산 효율을 유지하도록 한다.

결국 **4개의 스티어 드라이브 모듈을 위한 전력 분배 시스템**은 단순히 전기를 공급하는 장치가 아니다. 균형 잡힌 전류 분배, 고장 허용(Fault Tolerance), 전기적 분리(Electrical Isolation), 열 안정성(Thermal Stability), 진단 기능(Diagnostic Visibility), 미래 확장성(Future Scalability)을 제공하는 핵심 기반 기술이다. 산업용 AMR이 더욱 지능화되고 고성능화될수록 이러한 다축 전력 분배 기술은 전체 시스템의 신뢰성을 결정하는 핵심 요소가 된다.

### 3.2 DC/DC 컨버터 설계 (DC/DC Converter Design)

---

주 배터리(Main Battery)는 추진과 조향 시스템에 필요한 고전압 DC 전원을 공급하지만, 대부분의 전자 장치는 더 낮고 안정적인 전압을 필요로 한다. 따라서 **DC/DC 컨버터(DC/DC Converter)**는 고전압 배터리 전압을 다양한 저전압으로 변환하여 컴퓨팅, 센서, 통신, 제어기, 안전 장치 등에 공급하는 핵심 구성 요소이다.

48V 기반 산업용 AMR에서는 일반적으로 여러 개의 전압 레일(Voltage Rail)이 필요하다. **24V**는 산업용 센서, 릴레이(Relay), 안전 장치, 액추에이터에 사용되며, **12V**는 카메라(Camera), 통신 모듈, 냉각 팬(Cooling Fan), 조명(Lighting), 임베디드 장치에 공급된다. 또한 **5V**와 **3.3V**는 프로세서(Processor), 마이크로컨트롤러(Microcontroller), 메모리(Memory), 디지털 인터페이스를 위해 추가적인 Point-of-Load 컨버터를 통해 생성된다. 따라서 DC/DC 시스템은 단순한 전압 변환기가 아니라 **계층형 전력 구조(Hierarchical Power Architecture)**를 형성한다.

가장 중요한 설계 요소 가운데 하나는 **절연(Isolation)**이다. 절연형 DC/DC 컨버터(Galvanically Isolated DC/DC Converter)는 추진 시스템에서 발생하는 전기적 노이즈가 민감한 컴퓨팅 시스템으로 전달되는 것을 방지한다. 또한 접지 루프(Ground Loop)를 줄이고 공통 모드 노이즈(Common-mode Noise)를 감소시켜 정밀 센서의 측정 정확도를 향상시킨다. 산업 자동화에서는 안전 제어기, 통신 게이트웨이, 계측 장비 등에 절연형 컨버터가 널리 사용된다.

컨버터의 출력 용량(Power Capacity)은 실제 부하를 기준으로 결정해야 한다. GPU, LiDAR, 카메라, 산업용 Ethernet 스위치, 무선 통신 장치, 각종 전자 장치는 서로 다른 소비전력 특성을 가진다. 실제 부하 분석(Load Analysis)을 수행하면 불필요한 과대 설계를 줄일 수 있으며, 시스템의 무게와 비용도 절감된다.

효율(Efficiency)은 매우 중요한 요소이다. DC/DC 컨버터에서 손실되는 전력은 모두 열(Heat)로 변환된다. 최신 산업용 컨버터는 일반적으로 **95% 이상의 효율**을 달성하며, 이는 배터리 사용 시간을 연장하고 냉각 시스템의 부담을 줄이며 장기적인 신뢰성을 향상시킨다. 또한 컨버터는 정격 부하뿐 아니라 부분 부하(Partial Load)에서도 높은 효율을 유지해야 한다. 대부분의 AMR은 항상 최대 출력으로 운행하지 않기 때문이다.

열관리(Thermal Management)도 매우 중요하다. 고효율 컨버터라도 높은 전력 밀도(Power Density) 때문에 국부적인 온도 상승(Local Temperature Rise)이 발생할 수 있다. 저출력 컨버터는 알루미늄 히트싱크(Heat Spreader)만으로도 충분하지만, 고출력 컨버터는 강제 공랭(Forced Air Cooling)이나 중앙 열관리 시스템(Centralized Thermal Management)과 연계해야 할 수 있다. 적절한 공기 흐름(Airflow) 설계는 배터리와 GPU 주변의 과열을 방지한다.

최근에는 **이중화(Redundancy)**도 중요해지고 있다. 안전 제어기(Safety Controller), 비상 통신(Emergency Communication), 브레이크 제어(Brake Release), 상위 제어 프로세서는 별도의 DC/DC 컨버터를 사용하여 독립적으로 동작하기도 한다. 하나의 컨버터가 고장 나더라도 안전 기능은 유지되고 차량은 안전 상태(Safe State)로 전환된다.

전자기 적합성(Electromagnetic Compatibility, EMC)도 반드시 고려해야 한다. 스위칭 방식의 DC/DC 컨버터는 고주파 노이즈를 발생시키므로 입력 필터(Input Filter), 출력 필터(Output Filter), 차폐(Shielding), PCB 설계 최적화, 동기식 스위칭(Synchronous Switching)을 통해 산업용 EMC 규격을 만족해야 한다.

미래 확장성도 중요하다. 향후 더 많은 센서, 로봇팔, 검사 장비, AI 가속기(AI Accelerator)를 추가하면 저전압 소비전력이 증가하게 된다. 따라서 일정한 예비 용량(Power Margin)을 가진 모듈형 컨버터를 선택하면 향후 하드웨어 업그레이드를 쉽게 수행할 수 있다.

결국 DC/DC 컨버터는 단순히 전압을 변환하는 장치가 아니라, 로봇 내부의 모든 지능형 시스템이 안정적으로 동작하도록 만드는 **전기적 기반(Electrical Foundation)**이다. 높은 효율, 절연, 열 안정성, 이중화, 확장성이 결합될 때 산업 환경에서도 컴퓨팅, 센서, 통신, 자율주행 기능이 안정적으로 동작할 수 있다.

### 3.3 전용 페이로드 전원 라인 1200W 예시 (Dedicated Payload Power Line Example 1200W)

최근 산업용 AMR은 단순한 운반 차량이 아니라 다양한 **페이로드(Payload)**를 탑재하는 이동형 플랫폼(Mobile Platform)으로 발전하고 있다. 산업용 검사 장비(Industrial Inspection System), 협동 로봇팔(Collaborative Robotic Manipulator), 의료 장비(Medical Equipment), 물류 자동화 장치(Logistics Automation Module), 반도체 검사 시스템(Semiconductor Inspection System), 자율 청소 장비(Autonomous Cleaning System), 이동형 제조 장비(Mobile Manufacturing Tool) 등은 차량 추진과는 별도로 상당한 전력을 필요로 한다. 따라서 **전용 페이로드 전원 라인(Dedicated Payload Power Line)**을 구성하는 것이 현대 AMR 설계의 중요한 원칙이 되고 있다.

전용 전원 라인은 차량 시스템과 페이로드를 전기적으로 분리한다. 추진 시스템, 조향 시스템, 온보드 컴퓨팅, 페이로드는 모두 메인 전력 분배 장치(Main Power Distribution Unit)에서 각각 독립된 전원 라인을 통해 전력을 공급받는다. 이러한 구조는 페이로드에서 발생하는 큰 부하가 차량의 자율주행 성능에 영향을 주는 것을 방지한다.

예를 들어 **약 1,200W의 연속 전력을 사용하는 페이로드**를 생각해 보자. 이는 다수의 카메라와 조명을 사용하는 머신비전 시스템(Machine Vision System), 협동 로봇팔, 레이저 검사 장비(Laser Inspection Equipment), 정밀 계측기(Precision Measurement Instrument), GPU 기반 AI 컴퓨팅 시스템 등에 해당할 수 있다. 이러한 장비를 일반 보조 전원(Auxiliary Power)에 연결하면 차량 시스템 전체에 불필요한 전기적 부담이 발생한다.

따라서 전용 페이로드 라인에는 **독립적인 보호 장치(Protection Device)**, **컨택터(Contactor)**, **전류 감시(Current Monitoring)**, **전압 감시(Voltage Monitoring)**, **차량 제어기와의 통신 인터페이스(Communication Interface)**가 포함된다. BMS는 차량 소비전력과 페이로드 소비전력을 각각 독립적으로 감시한다. 배터리 잔량이 부족해지면 에너지 관리 시스템(Energy Management System)은 페이로드 전력을 우선 제한하고, 차량이 안전하게 충전소까지 복귀할 수 있는 최소 전력을 확보한다.

전기적 분리(Electrical Isolation)는 시스템 통합(System Integration)에도 큰 장점을 제공한다. 페이로드 제조사는 차량의 기본 전기 시스템을 변경하지 않고도 독립적인 전기 구조를 설계할 수 있다. 표준화된 고출력 커넥터(Standard High-power Connector), 통신 인터페이스, 기계적 장착 구조(Mounting Provision)는 동일한 차량 플랫폼에 다양한 산업용 장비를 빠르게 탑재할 수 있도록 해준다.

전원 품질(Power Quality)도 매우 중요하다. 산업용 검사 장비는 매우 안정적인 전압과 낮은 리플(Ripple), 낮은 전기적 노이즈를 요구한다. 따라서 전용 DC/DC 컨버터, 국부 필터(Local Filter), 절연 접지(Isolated Ground)를 적용하여 추진 인버터에서 발생하는 노이즈가 검사 장비의 측정 정확도에 영향을 주지 않도록 해야 한다. 이는 머신비전, 레이저 스캐너(Laser Scanner), 분광기(Spectroscopy Equipment), 의료 장비(Medical Instrument), 고속 데이터 수집 장비(High-speed Data Acquisition System)에서 특히 중요하다.

열관리도 차량과 페이로드를 함께 고려해야 한다. **1,200W의 페이로드**는 차량 추진과 무관하게 상당한 열을 발생시킬 수 있다. 따라서 열관리 시스템은 차량 전자장치와 페이로드 전자장치의 발열을 동시에 고려하여 냉각 장치를 제어해야 하며, 특정 공간의 국부 과열(Local Overheating)을 방지해야 한다.

안전 시스템(Safety Coordination)도 함께 연동되어야 한다. 비상 정지(Emergency Stop), 배터리 이상(Battery Fault), 과열(Overtemperature), 통신 장애(Communication Failure), 페이로드 이상(Payload Fault)은 모두 차량 안전 제어기와 연계되어야 한다. 필요 시 페이로드만 차단하고 차량은 안전하게 이동하거나, 차량 전체를 안전하게 정지시키는 전략을 선택할 수 있다.

에너지 관리(Energy Budgeting)도 더욱 정확해진다. 플릿 관리 시스템은 차량 소비전력과 페이로드 소비전력을 각각 계산하여 남은 운행 시간을 보다 정확하게 예측할 수 있다. 검사 작업이나 AI 연산량이 증가하면 소비전력이 크게 달라질 수 있으므로 독립적인 전력 모니터링은 매우 유용하다.

미래 확장성(Future Platform Evolution) 측면에서도 전용 페이로드 전원은 매우 큰 장점을 가진다. 앞으로 새로운 센서, 다양한 전압을 요구하는 장비, 새로운 통신 프로토콜을 사용하는 산업용 장비를 쉽게 추가할 수 있으며, 차량의 기본 추진 시스템은 그대로 유지할 수 있다. 이러한 구조는 AMR을 다양한 산업에 적용할 수 있는 범용 이동형 자동화 플랫폼(Universal Mobile Automation Platform)으로 발전시키는 핵심 요소가 된다.

결국 **1,200W 전용 페이로드 전원 라인**은 단순히 추가적인 전원을 제공하는 것이 아니다. 차량과 응용 장비를 분리하면서도 통합적으로 에너지를 관리하는 **모듈형 인터페이스(Modular Interface)**를 제공한다. 이를 통해 시스템 신뢰성(Reliability), 통합성(Integration), 안전성(Safety), 그리고 장기적인 확장성(Long-term Flexibility)을 모두 향상시킬 수 있으며, 차세대 산업 자동화 플랫폼의 핵심 설계 요소로 자리잡고 있다.

## 04 BMS for heavy AMR

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

### 4.1 Meaning of Pulse Current Tolerance 120A or More

---

### 4.2 CAN/RS485 Based CC-CV Charging Protocol

---

### 4.3 SoC-Based Autonomous Return and Charge Logic

### 4.1 120A 이상의 펄스 전류 허용(Pulse Current Tolerance)의 의미 (Meaning of Pulse Current Tolerance 120A or More)

---

배터리 관리 시스템(Battery Management System, **BMS**)은 중량급 자율주행 이동로봇(Autonomous Mobile Robot, **AMR**)에서 가장 중요한 핵심 시스템 가운데 하나이다. 배터리가 추진(Propulsion), 센서(Sensor), 컴퓨팅(Computing), 통신(Communication), 페이로드(Payload)에 필요한 에너지를 공급한다면, BMS는 배터리의 안전성을 유지하고 수명을 최대화하며 변화하는 운전 환경에서도 안정적인 전력 공급을 보장하는 지능형 관리 시스템(Intelligent Supervisory System)이다. 특히 고하중 산업용 AMR에서는 자주 언급되는 사양 가운데 하나가 **120A 이상의 펄스 전류 허용(Pulse Current Tolerance 120A or More)**이다. 이 사양의 의미를 정확하게 이해하는 것은 전기 시스템 설계와 차량 운행 전략을 결정하는 데 매우 중요하다.

**펄스 전류(Pulse Current)**는 배터리가 연속 방전(Continuous Discharge)보다 훨씬 높은 전류를 짧은 시간 동안 안전하게 공급할 수 있는 능력을 의미한다. 연속 방전 전류는 오랜 시간 동안 지속적으로 흐를 수 있는 전류를 의미하지만, 펄스 전류는 급가속(Rapid Acceleration), 경사로 주행(Ramp Climbing), 장애물 통과(Obstacle Traversal), 긴급 회피(Emergency Avoidance), 조향 전환(Steering Transition), 도킹 위치 보정(Docking Alignment)과 같은 매우 짧은 순간에만 발생한다. 일반적으로 이러한 전류는 수백 밀리초에서 수 초 정도 지속된 후 다시 정상적인 수준으로 감소한다.

연속 전류와 펄스 전류가 다른 이유는 배터리의 **전기화학(Electrochemistry)**과 **열 특성(Thermal Behavior)** 때문이다. 모든 리튬인산철 배터리(Lithium Iron Phosphate, **LFP**)는 내부 저항(Internal Resistance)을 가지고 있으며, 높은 전류가 흐르면 **줄의 법칙(Joule\'s Law)**에 따라 열이 발생한다. 만약 매우 높은 전류가 지속적으로 흐르면 셀(Cell)의 온도가 상승하여 배터리 열화(Aging)가 빨라지고 수명이 단축될 수 있다. 그러나 매우 짧은 시간 동안 발생하는 펄스 전류는 배터리의 열용량(Thermal Mass) 때문에 온도가 크게 상승하지 않으므로 안전하게 허용될 수 있다. 따라서 충분한 냉각 시간(Recovery Time)이 확보된다면 배터리는 연속 허용 전류보다 훨씬 높은 전류를 순간적으로 공급할 수 있다.

예를 들어 48V 기반의 중량급 AMR에서는 일반적인 운행 중 평균 방전 전류가 약 **30\~60A** 수준일 수 있다. 그러나 급가속이나 경사로를 오를 때는 추진 모터가 **100A 이상의 순간 전류**를 요구할 수 있다. 이때 **120A 이상의 펄스 전류 허용 능력**을 가진 배터리는 이러한 순간 부하를 안정적으로 공급할 수 있으며, 전압 강하(Voltage Sag)나 BMS의 보호 차단 없이 차량이 정상적으로 운행될 수 있다. BMS는 전류 크기(Current Magnitude), 펄스 지속 시간(Pulse Duration), 배터리 온도(Battery Temperature), 셀 전압(Cell Voltage)을 지속적으로 분석하여 현재의 방전 상태가 안전한 범위 안에 있는지를 실시간으로 판단한다.

펄스 전류 허용 능력은 차량의 **동적 성능(Dynamic Performance)**과 직접적으로 연결된다. 만약 순간 전류 공급 능력이 부족하면 차량의 가속 성능이 저하되고, 경사로 등판 능력이 감소하며, 긴급 장애물 회피 시 충분한 추진력을 얻지 못할 수 있다. 반대로 이러한 순간 부하를 위해 지나치게 큰 배터리를 사용하는 것은 차량 무게 증가, 비용 증가, 충전 시간 증가로 이어질 수 있다. 따라서 BMS는 실제 운행 조건(Mission Requirement)과 배터리 수명을 동시에 고려하여 최적의 전류 관리(Current Management)를 수행해야 한다.

또한 펄스 전류는 **전압 안정성(Voltage Stability)**에도 영향을 준다. 높은 전류가 순간적으로 흐르면 내부 저항 때문에 일시적인 전압 강하가 발생한다. 전압 강하가 너무 크면 추진 인버터(Inverter), 산업용 컴퓨터(Onboard Computer), 통신 장치, 센서 등이 저전압 상태(Undervoltage Condition)에 빠질 수 있다. 이를 방지하기 위해 BMS는 모터 제어기(Motor Controller)와 협력하여 전류 요구량을 조정하고 시스템 전압을 안정적으로 유지한다.

**셀 밸런싱(Cell Balancing)** 역시 중요한 역할을 한다. 셀마다 내부 저항이 조금씩 다르기 때문에 큰 전류가 흐르면 셀 간 전압 차이가 더욱 커질 수 있다. 능동형(Active) 또는 수동형(Passive) 밸런싱 시스템은 이러한 차이를 지속적으로 보정하여 전체 배터리 용량을 최대한 활용하고 장기적인 수명을 유지한다.

**열 모니터링(Thermal Monitoring)**도 펄스 전류 관리의 핵심 기능이다. 배터리 팩 내부에는 여러 개의 온도 센서가 배치되어 있으며, 순간적인 고전류가 발생하는 동안 셀의 온도를 지속적으로 감시한다. 만약 온도가 안전 기준에 접근하면 BMS는 허용 전류를 일시적으로 낮추거나 차량의 가속을 제한하고 모터 제어기에 토크 감소를 요청한다. 이러한 협조 제어(Coordinated Protection)는 차량의 정상 운행을 유지하면서도 배터리를 보호한다.

차량의 **미션 계획(Mission Planning)**도 펄스 전류를 고려하여 최적화할 수 있다. 엔지니어는 가속 프로파일(Acceleration Profile), 속도 계획(Velocity Planning), 조향 전환(Steering Transition), 페이로드 운용(Payload Handling)을 최적화하여 불필요한 고전류 발생을 줄일 수 있다. 또한 **순차 운전(Sequential Operation)**을 적용하면 추진 모터, 조향 모터, 페이로드, 보조 장치가 동시에 최대 전력을 사용하지 않으므로 배터리의 순간 전류 요구도 크게 감소한다.

결론적으로 **120A 이상의 펄스 전류 허용 능력**은 배터리가 항상 120A를 지속적으로 공급한다는 의미가 아니다. 이는 BMS가 전기적, 열적, 전기화학적 한계를 고려하여 매우 짧은 시간 동안 높은 전류를 안전하게 허용할 수 있는 동적 성능(Dynamic Capability)을 의미한다. 이러한 기능을 적절히 활용하면 중량급 산업용 AMR은 뛰어난 가속 성능과 높은 작업 효율을 확보하면서도 배터리의 안전성과 긴 수명을 동시에 유지할 수 있다.

### 4.2 CAN/RS485 기반 CC-CV 충전 프로토콜 (CAN/RS485 Based CC-CV Charging Protocol)

---

중량급 AMR이 장시간 안정적으로 운용되기 위해서는 효율적인 충전 시스템(Charging System)이 필수적이다. 현대의 리튬 배터리 시스템은 단순히 고성능 충전기(Charger)만 사용하는 것이 아니라, **배터리 관리 시스템(BMS)**과 충전기 사이의 지능형 통신(Intelligent Communication)을 기반으로 충전을 수행한다. **CAN(Controller Area Network)**과 **RS485(RS485)**는 이러한 통신을 수행하는 대표적인 산업용 인터페이스이며, 배터리의 안전성, 충전 효율, 수명 연장을 위해 널리 사용된다. 이들 통신망은 현대 산업용 AMR에서 사용하는 **정전류-정전압(Constant Current--Constant Voltage, CC-CV)** 충전 방식의 핵심 기반이 된다.

CC-CV 충전은 두 단계로 이루어진다. 먼저 **정전류(Constant Current, CC)** 단계에서는 충전기가 일정한 전류를 공급하며 배터리 전압은 점차 상승한다. 이 과정에서 대부분의 에너지가 빠르게 충전된다. 이후 배터리 전압이 설정된 최대 충전 전압에 도달하면 **정전압(Constant Voltage, CV)** 단계로 전환된다. 이때 충전 전압은 일정하게 유지되고 충전 전류는 점차 감소한다. 전류가 미리 설정된 종료 기준 이하로 떨어지면 충전이 완료된다. 이러한 방식은 셀의 과충전(Overvoltage)을 방지하면서 배터리를 완전 충전할 수 있는 가장 일반적인 방법이다.

충전기와 BMS가 **CAN 또는 RS485 통신**을 사용하면 충전 성능은 크게 향상된다. 충전이 시작되기 전에 BMS는 배터리 ID(Battery Identification), 허용 충전 전류(Allowable Charging Current), 최대 충전 전압(Voltage Limit), 배터리 온도(Temperature), 충전 상태(State of Charge, SoC), 배터리 건강 상태(State of Health, SoH), 이상 상태(Fault Status), 셀 밸런싱(Cell Balancing) 정보를 충전기로 전송한다. 충전기는 이러한 실시간 정보를 기반으로 출력 전압과 전류를 지속적으로 조절하며, 단순한 고정 충전기보다 훨씬 효율적이고 안전한 충전을 수행한다.

**CAN 통신**은 높은 신뢰성(Robustness), 결정론적 통신(Deterministic Communication), 우수한 진단 기능(Diagnostic Capability) 때문에 산업용 AMR에서 가장 널리 사용되는 방식이다. 표준 메시지(Standard Message)를 이용하여 충전기, BMS, 차량 제어기(Vehicle Controller), 플릿 관리 시스템(Fleet Management System)이 상태 정보를 공유할 수 있으며, 고장 진단(Fault Reporting), 이벤트 기록(Event Logging), 펌웨어 업데이트(Firmware Update), 원격 진단(Remote Diagnostics)도 함께 수행할 수 있다.

**RS485 통신**은 구현이 단순하고 통신 거리가 길며 전기적 노이즈에 강하고 비용이 낮다는 장점을 가진다. 많은 산업용 배터리 시스템은 **Modbus(Modbus)** 기반의 RS485 통신을 사용하여 충전기와 데이터를 교환한다. 통신 속도는 CAN보다 다소 느리지만, 배터리 충전에서는 수 ms 수준의 응답이면 충분하기 때문에 실제 운용에는 큰 문제가 없다.

배터리 **온도(Temperature)**는 충전 과정에서 매우 중요한 요소이다. 리튬 배터리는 너무 낮거나 높은 온도에서 충전하면 성능 저하와 수명 감소가 발생할 수 있다. BMS는 여러 개의 온도 센서를 이용하여 배터리 온도를 지속적으로 감시하며, 온도가 낮으면 충전 전류를 줄여 리튬 석출(Lithium Plating)을 방지하고, 온도가 높으면 과열을 방지하기 위해 충전 전류를 감소시킨다.

**셀 밸런싱(Cell Balancing)**은 CC-CV 충전 후반부에서 수행된다. 장기간 사용하면 셀 간 전압 차이가 조금씩 증가하게 된다. 정전압 단계에서 BMS는 능동형 또는 수동형 밸런싱 회로를 동작시켜 모든 셀이 동일한 전압에 도달하도록 조정한다. 이는 전체 배터리 용량을 최대한 활용하고 수명을 연장하는 데 매우 중요하다.

충전 중에는 **안전 모니터링(Safety Monitoring)**이 지속적으로 수행된다. 과전압(Overvoltage), 저전압(Undervoltage), 과열(Overtemperature), 통신 장애(Communication Failure), 절연 이상(Insulation Failure), 이상 전류(Current Fault), 커넥터 이상(Connector Fault), 충전기 고장(Charger Fault)이 감지되면 BMS와 충전기는 즉시 충전을 일시 중지하거나 종료하며 필요한 보호 동작을 수행한다.

**자율 충전 스테이션(Autonomous Charging Station)**에서는 차량이 도킹한 이후 충전 전에 먼저 통신을 수행한다. 차량과 충전기는 배터리 인증(Battery Identification), 충전 허가(Charging Authorization), 접속 확인(Connection Verification), 충전 준비 상태(Charging Readiness)를 확인한 후에만 전력을 공급한다. 이를 통해 오접속이나 잘못된 충전을 방지할 수 있다.

최근에는 **클라우드 기반 플릿 관리 시스템(Cloud-connected Fleet Management System)**도 충전 데이터를 지속적으로 수집한다. 충전 이력(Charging History), SoH, 충전 효율(Charging Efficiency), 에너지 소비(Energy Consumption), 진단 정보(Diagnostic Information)를 분석하여 예지보전(Predictive Maintenance)과 배터리 수명 최적화(Battery Lifecycle Optimization)를 수행한다. 또한 여러 대의 AMR을 운영하는 경우에는 충전 스케줄을 자동으로 조정하여 피크 전력(Peak Demand)을 줄이고 운영 효율을 높일 수 있다.

결국 **CAN/RS485 기반 CC-CV 충전 프로토콜**은 단순한 충전 기술이 아니라 BMS, 충전기, 차량 제어기, 플릿 관리 시스템이 하나의 지능형 에너지 관리 시스템(Intelligent Energy Management System)으로 동작하도록 하는 핵심 기술이다. 이를 통해 충전 효율, 배터리 안전성, 진단 기능, 운영 신뢰성, 그리고 배터리 수명을 모두 향상시킬 수 있으며, 완전 자율형 산업용 AMR의 안정적인 운용을 가능하게 한다.

### 4.3 SoC 기반 자율 복귀 및 충전 로직 (SoC-Based Autonomous Return and Charge Logic)

산업용 AMR의 가장 중요한 특징 가운데 하나는 사람의 개입 없이 스스로 에너지를 관리할 수 있다는 점이다. 현대의 AMR은 작업자가 배터리 잔량을 확인하여 충전을 지시하는 것이 아니라, **배터리 충전 상태(State of Charge, SoC)**를 지속적으로 계산하고 현재 수행 중인 작업을 분석하여 적절한 시점에 작업을 중단하고 충전소로 이동하며, 충전을 완료한 후 다시 작업을 재개한다. 이러한 자율 에너지 관리(Autonomous Energy Management)의 핵심이 바로 **SoC 기반 자율 복귀 및 충전 로직**이다.

**SoC(State of Charge)**는 배터리에 남아 있는 사용 가능한 에너지를 백분율(%)로 나타낸 값이다. 현대의 BMS는 단순히 배터리 전압만을 이용하여 SoC를 계산하지 않는다. 전류 적산(Coulomb Counting), 전압(Voltage), 온도(Temperature), 내부 저항(Impedance), 충전 및 방전 이력, 배터리 열화(Aging) 등을 종합하여 **칼만 필터(Kalman Filter)**나 **배터리 모델 기반 추정(Model-based Battery Observer)**과 같은 알고리즘을 사용하여 매우 정확한 SoC를 계산한다.

자율 복귀는 단순히 SoC가 일정 값 이하로 떨어졌다고 해서 시작되는 것이 아니다. 차량 제어기(Vehicle Controller)는 **남은 이동 거리(Remaining Distance)**, **예상 에너지 소비(Expected Energy Consumption)**, **적재 중량(Payload Weight)**, **노면 상태(Terrain Condition)**, **교통 상황(Traffic Congestion)**, **현재 작업의 중요도(Mission Priority)**, **충전기 사용 가능 여부(Charging Station Availability)**, **배터리 건강 상태(SoH)** 등을 동시에 고려한다. 따라서 동일한 SoC를 가진 두 대의 AMR이라도 작업 상황에 따라 서로 다른 충전 결정을 내릴 수 있다.

가능하면 현재 수행 중인 작업(Mission)은 끝까지 완료하는 것이 효율적이다. 만약 남은 배터리로 현재 작업을 마치고도 충전소까지 안전하게 복귀할 수 있다면 작업을 계속 수행한다. 반대로 현재 작업을 완료하면 충전소까지 갈 에너지가 부족할 것으로 예측되면 작업을 중단하고 즉시 충전소로 복귀한다. 이러한 **예측 기반 에너지 관리(Predictive Energy Management)**는 불필요한 충전을 줄이면서도 배터리 방전을 방지한다.

실제 산업용 AMR은 여러 단계의 SoC 기준을 사용한다. 정상 운행 영역(Normal Threshold)에서는 모든 작업을 자유롭게 수행한다. 주의 영역(Caution Threshold)에 들어가면 배터리 감시를 강화하고 일부 고전력 장비의 사용을 제한한다. 복귀 기준(Return Threshold)에 도달하면 충전소 복귀를 시작한다. 마지막으로 비상 영역(Emergency Threshold)에 도달하면 속도를 제한하고 안전 기능만 유지하면서 반드시 충전소로 이동한다.

플릿(Fleet) 환경에서는 **충전소 선택(Charging Station Selection)**도 매우 중요하다. 가장 가까운 충전소로 이동하는 것이 아니라, 각 충전기의 사용 상태, 대기 시간, 우선순위, 다른 AMR의 충전 계획을 함께 고려하여 최적의 충전소를 선택한다. 이러한 스케줄링은 전체 플릿의 생산성을 높이고 충전 대기 시간을 최소화한다.

충전소에 접근할 때도 충분한 **에너지 여유(Energy Reserve)**를 확보해야 한다. 차량은 충전소까지 이동할 뿐 아니라 정밀 도킹(Precision Docking), 충전기와의 통신, 충전 확인, 도킹 실패 시 재시도까지 수행할 수 있는 최소 에너지를 반드시 남겨 두어야 한다. 따라서 복귀 로직에는 항상 일정한 안전 여유(Safety Margin)가 포함된다.

충전소에 성공적으로 도킹하면 차량 제어기, BMS, 충전기가 자동으로 통신을 시작하고 충전 절차를 수행한다. 충전 중에는 SoC, **배터리 건강 상태(State of Health, SoH)**, 충전 전류, 온도, 셀 밸런싱, 진단 정보가 지속적으로 감시된다. 충전 종료 시점 역시 단순히 시간이 아니라 BMS가 실시간으로 판단한다.

작업 재개(Mission Resumption)도 지능적으로 이루어진다. 반드시 100% 충전까지 기다리는 것이 아니라, 다음 작업을 수행하기에 충분한 에너지만 확보되면 충전을 종료하고 다시 작업을 시작하는 **기회 충전(Opportunity Charging)** 전략이 널리 사용된다. 이를 통해 플릿 전체의 가동률(Utilization)을 더욱 높일 수 있다.

최근에는 **인공지능(AI)**도 에너지 관리에 활용되고 있다. 머신러닝(Machine Learning)은 과거 운행 데이터, 작업 패턴, 환경 조건, 계절별 온도 변화, 배터리 열화, 생산 계획을 분석하여 향후 에너지 소비를 예측한다. 이러한 AI 기반 충전 전략은 기존의 고정 규칙(Rule-based System)보다 더 정확하게 충전 시점을 결정하고 배터리 수명과 플릿 생산성을 동시에 향상시킨다.

결국 **SoC 기반 자율 복귀 및 충전 로직**은 단순한 배터리 모니터링 기능이 아니라, 배터리 상태 추정(Battery Estimation), 예측 기반 작업 계획(Predictive Mission Planning), 지능형 충전 관리(Intelligent Charging Management), 플릿 최적화(Fleet Optimization)를 통합하는 핵심 기술이다. 이러한 기능을 통해 중량급 산업용 AMR은 사람의 개입 없이 장시간 안정적으로 운용될 수 있으며, 향후 완전 자율형 스마트 팩토리(Fully Autonomous Smart Factory)의 핵심 에너지 관리 기술로 더욱 중요해질 것이다.

## 05 Auto charging station design

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

### 5.1 Contact Charging Station Mechanical Design

---

### 5.2 Entry Guide Design for 1 Ton Class AMR

---

### 5.3 Pre-Charge Safety Circuit

---

### 5.4 Phase 2 Wireless Charging Upgrade Strategy

### 5.1 접촉식 충전 스테이션 기계 설계 (Contact Charging Station Mechanical Design)

---

충전 스테이션(Charging Station)은 자율주행 이동로봇(Autonomous Mobile Robot, **AMR**) 시스템에서 사람의 개입 없이 장시간 연속 운전을 가능하게 하는 핵심 구성 요소이다. 배터리(Battery), 배터리 관리 시스템(Battery Management System, **BMS**), 충전 알고리즘(Charging Algorithm)이 중요한 기술이지만, 실제 현장에서 수천 번 이상의 충전 사이클을 안정적으로 수행할 수 있는지는 결국 **충전 스테이션의 기계 설계(Mechanical Design)**에 의해 결정된다. 특히 **1톤급 산업용 AMR**은 큰 차량 질량, 반복적인 도킹 충격(Docking Impact), 제조 공차(Manufacturing Tolerance), 바닥의 평탄도(Floor Flatness), 장기간의 산업 환경 노출을 모두 견디면서 안정적인 전기 접촉(Electrical Contact)을 유지해야 한다.

현재 산업용 중량급 AMR에서는 **접촉식 충전(Contact Charging)**이 가장 널리 사용된다. 접촉식 충전은 **높은 충전 효율(Charging Efficiency)**, 성숙한 기술(Mature Technology), 비교적 낮은 구축 비용(Infrastructure Cost), 그리고 대전력 충전(High-power Charging)에 대한 우수한 호환성을 제공한다. 무선 충전(Wireless Charging)과 달리 전력 손실이 매우 적으며 고출력에서도 열 발생이 상대적으로 적다. 따라서 물류센터(Logistics Center), 반도체 공장(Semiconductor Factory), 제조 공장(Manufacturing Facility)과 같이 가동률이 높은 산업 현장에서는 접촉식 충전이 여전히 가장 현실적인 선택이다.

충전 스테이션은 로봇이 완벽한 위치에 정지해야만 충전되는 구조가 아니라, **작은 위치 오차(Position Error)**를 기계적으로 흡수하는 구조로 설계되어야 한다. 아무리 정밀한 자율주행 시스템이라도 휠 마모(Wheel Wear), 바닥 상태(Floor Condition), 적재물 변화(Payload Variation), 위치 추정 오차(Localization Uncertainty), 센서 노이즈(Sensor Noise) 등에 의해 수 cm 정도의 위치 편차는 항상 발생한다. 따라서 기계 구조가 이러한 오차를 자연스럽게 보정하면서 안정적인 전기 접촉을 유지해야 한다.

대표적인 방식은 **테이퍼 가이드(Tapered Docking Funnel)**이다. 차량이 충전 스테이션에 접근하면 좌우 가이드가 차량을 점진적으로 중앙으로 유도(Self-centering)하며 최종 위치까지 안내한다. 이후 **스프링 방식의 충전 단자(Spring-loaded Charging Contact)**가 남아 있는 작은 오차를 흡수하면서 일정한 접촉 압력(Contact Pressure)을 유지한다.

충전 전극(Charging Electrode)은 일반적으로 **은도금 구리 합금(Silver-plated Copper Alloy)**이나 특수 처리된 구리 소재를 사용한다. 이러한 표면 처리는 높은 전기전도도(Electrical Conductivity)를 유지하면서 산화(Oxidation), 접촉 저항(Contact Resistance), 장기간 반복 사용에 따른 마모를 최소화한다. 충전 단자는 수만 회 이상의 반복 접촉을 견뎌야 하므로 전기적 성능과 기계적 내구성이 모두 중요하다.

스프링 방식의 접점은 제조 공차, 열팽창(Thermal Expansion), 진동(Vibration), 구조 변형(Structural Deformation)을 흡수한다. 접촉 압력은 너무 작으면 접촉 저항이 증가하고 발열이 발생하며, 너무 크면 기계적 마모가 증가하고 도킹 저항도 커진다. 따라서 **유한요소해석(Finite Element Analysis, FEA)**과 반복 내구 시험(Endurance Test)을 통해 최적의 접촉 압력을 결정해야 한다.

1톤급 AMR에서는 **도킹 충격(Docking Impact)**도 중요한 설계 요소이다. 차량 속도가 낮더라도 차량 질량이 크기 때문에 충돌 시 상당한 충격력이 발생한다. 이를 완화하기 위해 **엘라스토머 댐퍼(Elastomer Damper)**, 탄성 브래킷(Compliant Mounting Bracket), 충격 흡수 가이드(Shock-absorbing Guide)를 적용하며, 차량 제어기에서도 **저저크 감속 프로파일(Low-jerk Deceleration Profile)**을 사용하여 도킹 충격을 최소화한다.

산업 환경에서는 먼지(Dust), 습기(Moisture), 절삭유(Cutting Oil), 금속 분진(Metal Particle), 세정액(Cleaning Chemical), 온도 변화(Temperature Variation)가 지속적으로 발생한다. 따라서 보호 커버(Protective Cover), 자기 세정(Self-cleaning) 구조, 배수 구조(Drainage Channel), 밀폐형 하우징(Sealed Housing)을 적용하여 장기간 충전 신뢰성을 유지해야 한다.

충전 시작 전에 **도킹 확인 센서(Position Verification Sensor)**도 필요하다. 리미트 스위치(Limit Switch), 광센서(Optical Sensor), 근접 센서(Proximity Sensor), 힘 센서(Force Sensor), 전기적 접촉 감지(Electrical Continuity Detection)를 이용하여 차량이 정확히 도킹되었는지 확인한 후에만 충전을 시작한다. 이를 통해 접촉 불량으로 인한 스파크(Arcing)나 커넥터 손상을 방지할 수 있다.

유지보수(Maintenance)를 고려한 설계도 중요하다. 충전 단자, 스프링, 보호 커버, 가이드 등 마모 부품은 전체 스테이션을 분해하지 않고 쉽게 교체할 수 있어야 한다. **모듈형 충전 헤드(Modular Charging Head)**는 유지보수 시간을 크게 줄이고 생산 중단 시간을 최소화한다.

결국 **접촉식 충전 스테이션**은 기계공학(Mechanical Engineering), 전기공학(Electrical Engineering), 재료공학(Material Science), 자율주행 기술(Autonomous Navigation)이 결합된 시스템이다. 완벽한 위치 정밀도를 요구하는 것이 아니라, 실제 산업 환경에서 발생하는 다양한 오차를 스스로 흡수하면서 장기간 안전하고 안정적으로 전력을 전달하는 것이 설계의 핵심이다.

### 5.2 1톤급 AMR용 진입 가이드 설계 (Entry Guide Design for 1 Ton Class AMR)

---

충전 과정에서 마지막 도킹(Final Docking)의 성공 여부는 **진입 가이드(Entry Guide)** 설계에 크게 좌우된다. 아무리 위치 추정(Localization)의 정확도가 수 cm 수준이라 하더라도 휠 슬립(Wheel Slip), 적재 중량 변화(Payload Variation), 서스펜션 움직임(Suspension Movement), 바닥의 높이 차이(Floor Unevenness), 오도메트리 누적 오차(Odometry Error)로 인해 작은 위치 오차는 항상 발생한다. 따라서 충전 스테이션은 자율주행 시스템의 위치 정확도에만 의존하지 않고 기계적으로 차량을 올바른 위치로 유도해야 한다. 특히 **1톤급 AMR**에서는 차량 질량이 크기 때문에 이러한 기계적 유도가 더욱 중요하다.

진입 가이드는 자율주행에서 기계 정렬(Mechanical Alignment)로 전환되는 인터페이스 역할을 한다. 차량은 일정한 위치 허용 오차(Position Tolerance) 안으로 접근하기만 하면 되고, 이후에는 가이드 구조가 차량을 자연스럽게 중앙으로 유도하여 최종 충전 위치까지 안내한다.

가이드 형상은 일반적으로 좌우 대칭의 **테이퍼(Tapered Guide Surface)** 구조를 사용한다. 차량이 가이드 안으로 들어오면 좌우 오차에 따라 작은 횡방향 힘(Lateral Force)이 발생하고, 이 힘이 차량을 점차 중앙으로 이동시킨다. 가이드 각도(Taper Angle)는 매우 중요하다. 각도가 너무 크면 측면 충격이 증가하고, 너무 작으면 가이드 길이가 지나치게 길어진다. 따라서 설치 공간과 유도 성능을 모두 고려하여 최적의 각도를 결정해야 한다.

수직 방향 정렬(Vertical Alignment)도 고려해야 한다. 1톤급 차량은 적재 상태에 따라 타이어 변형(Tire Deformation), 서스펜션 압축(Suspension Compression), 바닥 높이 차이가 발생할 수 있다. 따라서 충전 단자는 **플로팅(Floating Mechanism)** 구조나 탄성 지지 구조를 적용하여 수직 위치 오차를 흡수하도록 설계해야 한다.

도킹 속도(Docking Speed)는 진입 가이드 설계와 밀접하게 연관된다. 속도가 빠를수록 충돌 에너지가 증가하고 위치를 보정할 시간이 줄어든다. 따라서 AMR은 충전 스테이션 근처에서 **저저크 감속(Low-jerk Deceleration)**을 수행하여 점진적으로 속도를 낮춘다. 결국 모션 제어(Motion Control)와 기계 가이드는 함께 설계되어야 한다.

접촉력(Contact Force)은 좌우가 균형 있게 분포되어야 한다. 한쪽에만 큰 힘이 발생하면 가이드 마모가 빨라지고 구조물에 불필요한 응력이 발생한다. 특히 1톤 이상의 차량에서는 반복 도킹 시 피로 응력(Fatigue Stress)이 누적될 수 있으므로 유한요소해석(FEA)을 통해 응력 분포를 분석하는 것이 일반적이다.

가이드 재질은 높은 내마모성(Wear Resistance)과 낮은 마찰계수(Low Friction)를 동시에 가져야 한다. 강화강(Hardened Steel), 엔지니어링 플라스틱(Engineering Plastic), **UHMW-PE(Ultra High Molecular Weight Polyethylene)**, 복합재료(Composite Material)가 많이 사용된다. 마모 부품은 교체 가능한 인서트(Replaceable Wear Insert) 구조로 설계하면 유지보수가 쉬워진다.

제조 공차(Manufacturing Tolerance)도 매우 중요하다. 차량 프레임, 휠 위치, 충전 스테이션 설치, 가이드 제작 공차, 바닥 평탄도 등이 모두 도킹 성공률에 영향을 준다. 따라서 통계적 공차 분석(Statistical Tolerance Analysis)을 통해 대량 생산 시에도 안정적인 도킹 성능을 확보해야 한다.

안전성(Safety)도 반드시 고려해야 한다. 도킹 중 비상 정지(Emergency Stop)가 발생하더라도 차량이 가이드에 걸리지 않고 쉽게 후진하여 빠져나올 수 있어야 한다. 이를 위해 항상 탈출 경로(Escape Path)를 확보하는 것이 중요하다.

산업 현장에서는 먼지, 금속 분진, 포장재, 물, 얼음, 세정액 등이 가이드에 쌓일 수 있다. 따라서 개방형(Open Structure), 배수 구조(Drainage Design), 보호 커버(Protective Shield), 정기 점검 절차를 적용하여 오염에 의한 도킹 실패를 최소화해야 한다.

최근에는 카메라(Camera), LiDAR, 힘 센서 등을 이용하여 도킹 품질(Docking Quality)을 지속적으로 분석하는 **디지털 진단(Digital Diagnostics)**도 적용되고 있다. 반복적인 도킹 데이터를 분석하면 가이드의 마모를 예측하고 예방 정비(Predictive Maintenance)를 수행할 수 있다.

결국 **진입 가이드**는 자율주행의 수 cm 수준 위치 오차를 충전 단자의 mm 수준 정밀도로 변환하는 핵심 장치이다. 기계적 자기 정렬(Self-centering)과 자율주행 제어가 결합될 때 1톤급 AMR도 매우 높은 충전 성공률을 달성할 수 있다.

### 5.3 충전 전 안전 회로 (Pre-Charge Safety Circuit)

---

자동 충전에서는 단순히 충전기를 연결하는 것만으로는 충분하지 않다. 실제 충전 전류가 흐르기 전에 기계적 연결(Mechanical Connection), 전기적 상태(Electrical Integrity), 통신(Communication), 절연(Insulation), 배터리 상태(Battery Health)가 모두 안전한지 확인해야 한다. 이러한 역할을 수행하는 것이 **충전 전 안전 회로(Pre-Charge Safety Circuit)**이다.

가장 중요한 목적은 **돌입 전류(Inrush Current)**를 방지하는 것이다. 방전된 배터리가 대용량 DC 링크 커패시터(DC Bus Capacitor)를 가진 충전기에 직접 연결되면 매우 큰 순간 전류가 흐를 수 있다. 이는 커넥터, 컨택터, 커패시터, 전력 반도체를 손상시키고 스파크를 발생시킬 수 있다. 프리차지 회로는 이러한 전류를 제한하면서 두 시스템의 전압을 천천히 동일하게 만든다.

충전은 먼저 도킹 확인(Position Confirmation) 이후 시작된다. 차량 위치 센서가 정상 도킹을 확인하고, BMS와 충전기가 배터리 ID, SoC, 온도, 충전 허용 전류 등을 교환한다. 모든 조건이 만족된 후에만 프리차지 회로가 동작한다.

프리차지 저항(Pre-charge Resistor)은 핵심 부품이다. 초기에는 이 저항을 통해 커패시터를 천천히 충전하고, 전압 차이가 거의 없어지면 메인 컨택터(Main Contactor)가 닫히면서 저항을 우회(Bypass)하여 정상 충전이 시작된다.

전압 감시(Voltage Monitoring)는 프리차지 동안 배터리 전압과 충전기 DC 버스 전압을 지속적으로 비교한다. 일정 시간 안에 전압이 정상적으로 같아지지 않으면 즉시 충전을 중단하고 이상 진단을 수행한다. 이는 컨택터 고장, 배선 문제, 커패시터 이상, 배터리 이상 등을 조기에 발견하는 데 도움이 된다.

절연 감시(Insulation Monitoring)도 중요하다. 고전압 배터리는 차량 섀시와의 절연 저항(Insulation Resistance)을 지속적으로 측정한다. 절연 저항이 기준 이하로 떨어지면 충전을 금지하고 유지보수를 수행해야 한다.

전류 감시(Current Monitoring)는 충전 중 예상과 다른 전류가 흐르는지를 확인한다. 과전류, 역전류, 불안정한 전류 변화가 발생하면 즉시 충전을 중단한다.

온도 감시(Thermal Monitoring)는 배터리, 충전기, 충전 단자, 전력 전자장치의 온도를 지속적으로 측정하며 필요하면 충전 전류를 자동으로 감소시킨다.

비상 정지(Emergency Stop), 충전 단자 분리, 절연 이상, 통신 장애, 연기 감지(Smoke Detection), 공장 화재 경보(Fire Alarm)도 모두 충전 회로와 연동되어 즉시 전원을 차단할 수 있어야 한다.

모든 충전 과정은 데이터 로그(Data Logging)로 저장된다. 충전 시간, 최대 전류, 전압 변화, 온도, 셀 밸런싱, 이상 기록을 분석하면 예지보전과 배터리 수명 관리에 활용할 수 있다.

또한 MES(Manufacturing Execution System), 플릿 관리 시스템(Fleet Management System), 공장 에너지 관리 시스템(Energy Management System)과 연동하여 생산 계획과 전력 소비를 함께 최적화할 수 있다.

결국 **프리차지 안전 회로**는 단순한 전기 회로가 아니라, 기계적 확인, 통신 검증, 전압 평형, 전류 제한, 절연 감시, 열관리, 안전 차단을 통합한 종합 안전 시스템으로서 수천 회 이상의 자동 충전에서도 높은 신뢰성을 보장한다.

### 5.4 2단계 무선 충전 업그레이드 전략 (Phase 2 Wireless Charging Upgrade Strategy)

현재 산업용 중량급 AMR에서는 **접촉식 충전(Contact Charging)**이 가장 높은 효율과 가장 낮은 구축 비용을 제공하지만, **무선 충전(Wireless Charging)** 기술은 빠르게 발전하고 있다. 따라서 많은 제조사는 현재는 접촉식 충전을 적용하되, 향후 무선 충전으로 쉽게 전환할 수 있도록 플랫폼을 설계하는 **단계적 업그레이드 전략(Phased Upgrade Strategy)**을 채택하고 있다.

**1단계(Phase 1)**에서는 접촉식 충전을 사용한다. 이는 높은 효율, 검증된 신뢰성, 간단한 유지보수, 풍부한 산업 경험을 제공한다. 이 단계에서 자율 도킹, 충전 통신, BMS 연동, 플릿 관리 시스템을 충분히 검증한다.

무선 충전은 여러 장점을 제공한다. 전기 접점이 없어지므로 접촉 마모, 산화, 오염 문제가 사라지고 유지보수 부담도 크게 감소한다. 먼지, 습기, 화학물질이 많은 산업 환경에서도 더욱 안정적으로 사용할 수 있다.

무선 충전은 **공진형 유도 결합(Resonant Inductive Coupling)**을 이용하여 송신 코일(Transmitter Coil)과 수신 코일(Receiver Coil) 사이에서 자기장을 통해 전력을 전달한다. 최근에는 효율이 크게 향상되었지만, 아직까지는 대전력 분야에서 접촉식 충전이 더 높은 효율을 제공한다.

무선 충전도 위치 정렬(Position Alignment)은 여전히 중요하다. 전기 접점은 없어졌지만 코일 위치가 정확해야 높은 효율을 유지할 수 있다. 따라서 카메라, LiDAR, 자기 정렬(Magnetic Alignment) 기술 등을 계속 활용해야 한다.

무선 충전은 열관리도 다르다. 코일과 페라이트(Ferrite), 전력 전자장치에서 발생하는 열을 관리해야 하며, 냉각 시스템과 차폐 구조(Shielding)를 적절히 설계해야 한다.

또한 **이물질 검출(Foreign Object Detection)** 기능도 필요하다. 금속 물체가 코일 사이에 들어가면 와전류(Eddy Current)에 의해 과열될 수 있다. 따라서 시스템은 자기장 특성과 결합 효율(Coupling Efficiency)을 지속적으로 감시하여 이상이 있으면 충전을 시작하지 않는다.

전자기 적합성(Electromagnetic Compatibility, EMC)도 중요한 설계 요소이다. 자기장이 센서, 통신 장치, 산업용 계측기, 의료 장비 등에 영향을 주지 않도록 국제 EMC 규격을 만족해야 한다.

따라서 현재 접촉식 충전을 사용하더라도 향후 무선 충전을 위해 차량에는 업그레이드 가능한 인터페이스를 미리 준비하는 것이 바람직하다. 표준화된 배터리 통신(Standard Battery Communication), 모듈형 충전 제어기(Modular Charging Controller), 확장 가능한 BMS 소프트웨어, 무선 충전 코일 설치 공간 등을 확보하면 향후 전환 비용을 크게 줄일 수 있다.

플릿 관리 소프트웨어도 충전 방식과 관계없이 동일한 인터페이스를 유지해야 한다. 접촉식이든 무선식이든 작업 계획, 충전 예약, 배터리 관리, 진단, 에너지 최적화는 동일한 방식으로 수행될 수 있어야 한다.

경제성 측면에서도 단계적 전략이 유리하다. 초기에는 접촉식 충전으로 투자 비용을 최소화하고, 향후 무선 충전 기술이 성숙하고 가격이 낮아지면 유지보수 절감 효과가 큰 현장부터 점진적으로 적용할 수 있다.

결국 **2단계 무선 충전 업그레이드 전략**은 접촉식 충전을 대체하는 것이 아니라 자연스럽게 발전시키는 기술 로드맵이다. 현재는 가장 안정적이고 경제적인 접촉식 충전을 사용하면서도, 미래에는 무선 충전으로 쉽게 전환할 수 있는 플랫폼을 구축하는 것이 장기적으로 가장 경쟁력 있는 설계 전략이 될 것이다.
