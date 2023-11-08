---
title: "FPGA Project : TPS25940"
excerpt: "TPS25940 Datasheet에 대해 학습합니다."
categories:
  - FPGA Project
---

<br>

<br>

### 목표 설계 사양 설정하기

| DESIGN PARAMETER                         | EXAMPLE VALUE |
| ---------------------------------------- | ------------- |
| Input voltage, V(IN)                     | 5V            |
| Undervoltage lockout set point, V(UV)    | switch        |
| Overvoltage protection set point, V(LIM) | 5.5V          |
| Load at Start-Up, RL(SU)                 | ??            |
| Current limit, I(LIM)                    | 0.75A         |
| Load capacitance, C(OUT)                 | 100uF         |
| Maximum ambient temperatures, TA         | 85°C          |



### TPS25940 Datasheet

2.7-V to 18-V @ 0.6-A to 5.3-A

#### Function

1. V(IN) < (V(OUT) – 66mV) 일 때 역전류 차단 기능 제공 (Reverse current Blocking)
2. Over Current Protect
3. Programmable dVo/dt control
4. Over Voltage Protect
5. Under Voltage Protect 
6. thermal shutdown
7. hot plug in
8. hot swap
9. in-rush bloking
10. brown down



power management devices with a full suite of protection functions

#### Protect

`Over Current`, `dVo/dt Ramp ` , `Over Voltage`, `Under Voltage` , `thermal shutdown`



For system status monitoring and downstream load control, the device provides `PGOOD`, `\FLT` and precise current monitor output.



TPS25940-Q1 monitor V(IN) and V(OUT) to provide true reverse current blocking when` V(IN) < (V(OUT) – 66mV)`



### 용어정리

OVPR : Over Voltage Protect Rising

OVPF : Over Voltage Protect Falling

EVR : Under Voltage Rising

ENF : Under Voltage Falling

DEVSLP : Deep Sleep

ILIM : Current Limit

IMON : Current Monitor

\FLT : Fault Flag



### Pin Configuration and Functions 

<img width="400" alt="35" src="https://github.com/sehun98/TIL/assets/100746863/6b206fcf-3aba-480f-9a64-6f52fce3e8e1">



- dVdT핀은 캐패시터와 함께 연결되며 출력의 Ramp rate를 결정합니다. (10nF -> 4.15ms)  

`tdVdT = 8.3 x 104 x V(IN) x C(dVdT)`





- ILIM핀은 저항과 함께 연결되며 과부하 및 단락 전류 제한을 결정합니다.

`I(ILIM) = 89 / R(ILIM)`



- IMON핀은 
  GND로 연결하면 전류가 비례 전압으로 변환됩니다. 

  analog current monitor로 사용되기도 합니다.

  사용하지 않으면 floating 상태로 둡니다.

| state    | Description                      |
| -------- | -------------------------------- |
| Floating | unused                           |
| GND      | 전류가 비례 전압으로 변환됩니다. |

`R(IMON) = V(IMONmax) / (I(ILIM) * 52 * 10^-6) [kohm]`

3.9 = 0.5 / (x * 52 * 10^-6)

128.205 = 



- OVP핀은 Over Voltage Threshold 결정합니다. event 발생시 `\FLT` 핀이 동작합니다.

`V(OVPR) = ( R1 / (R2 + R1) ) * V(OV)`

=> 0.99V = (R1 / (R2 + R1) ) * 5.5V

=> (R1 / (R2 + R1) )  = 0.1754



- EN/UVLO핀은  Under Voltage 결정합니다.  
  스위치를 연결하여 Device에 전원을 공급하는 용도로 사용할 수 있습니다.



- \FLT 핀 오픈드레인 출력으로 이벤트 시 동작합니다.



- DEVSLP핀은 저전력 모드 제어입니다.

| state    | Description            |
| -------- | ---------------------- |
| High     | Deep Sleep mode Active |
| Floating | unused                 |
| GND      | unused                 |



<br>
<br>

