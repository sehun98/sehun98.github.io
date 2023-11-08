---
title: "FPGA Project : FT2232"
excerpt: "USB 통신 FT2232에 대해 학습합니다."
categories:
  - FPGA Project
---

<br>

<br>

### FT232RL과 FT2232

FT232는 대중적으로 많이 사용되는 USB to UART IC 입니다.

FT232는 MCU에서 UART 신호를 USB를 통해 Virtual COM Poart, VCP로 보내는 Bridge 역할을 합니다.

따라서 센서에서 사용되는 SPI, I2C, CAN 통신의 경우 MCU를 거쳐 UART 신호로 바꾼 후 USB로 전송되어야 합니다.

FT232를 통한 UART 통신은 비교적 느린 통신 방식으로 최대 속도 12Mbps로 제한된다는 점이 존재합니다.

<img width="750" alt="36" src="https://github.com/sehun98/TIL/assets/100746863/0711d58f-9c4f-4799-b798-494eee5cb865">

따라서 FT2232는 SPI, I2C, JTAG 통신을 USB와 직접 연결하여 사용 할 수 있으며 최대 속도 480Mbps 통신이 가능합니다.



### FT2232 구성 방법

1. 3V3 LDO 전압을 인가해야 합니다.
2. 12MHz의 오실레이터를 인가해야 합니다.
3. 93C46의 EEPROM은 Fast UART, FIFO 등의 특수한 경우에 필요합니다.
4. VPLL과 VPHY 핀에 3V3 전압을 비드를 통해 공급해야 합니다.
5. 이때 비드는 `임피던스 40옴, 주파수 100MHz, 전류 1.5A`의 조건의 MI0805K400R을 권장합니다.
6.  크리스탈은` FA-328V` 12MHz의 제품을 사용하며 Load Capacitor로 4pF 두 개를 사용합니다.
7. 크리스탈 배치는 IC에 최대한 가깝게 배치합니다.



### A포트 - UART to USB

<img width="750" alt="37" src="https://github.com/sehun98/TIL/assets/100746863/16c043f2-2c66-46c2-9a44-c055540dd7aa">

사진출처 : FT2232 Datasheet



UART 통신을 위해 ADBUS [0], [1]를 사용할 것입니다.



### B포트 - SPI 

SPI 통신을 위해 MPSSE를 사용하여 BDBUS [0] .. [3] Bus를 사용 할 것입니다.



### 가상 컴포트 연결

FT2232를 컴퓨터와 연결하여 장치 관리자를 열면 가상 컴포트가 잡혀야 합니다.

이때 두개의 가상 컴포트가 잡히는데 숫자가 낮은 것이 A채널, 숫자가 높은 것이 B채널 입니다.



### MPSSE 사용법

SPI 통신은 별도로 드라이버를 만들어야 합니다. MPSSE 기능을 `FTchip`에서 라이브러리를 받아야 합니다.

MPSSE는 별도로 탑재된 기능이 아닌 라이브러리에 가깝습니다.

MPSSE는 SPI, I2C, JTAG 통신을 사용하기 위해 사용되며, libMPSSE 라이브러리를 이용하여 구현할 수 있습니다.
MPSSE를 통한 FT2232의 SPI 통신은 Mode0와 Mode2만 지원합니다.

최대 통신 속도는 30MHz이며 보통 1MHz ~ 10MHz 사이에서 많이 사용됩니다.

MPSSE 라이브러리 중에서 ChannelConfig 라는 클래스를 이용하여 SPI 통신 설정을 할 수 있습니다.

MSBFirst와 LSBFirst모드는 별도로 선택 할 수 없습니다.

```c
uint8 latency = 250;
uint32 channels = 0;
uint8* chipID;
char buf[10];

/* SPI 통신 주파수 1,000,000Hz = 1MHz
 * latency = 250
 * SPI Mode 0
 * CS pin : BDBUS3
 */ CS pin : Active Low
channelConf.ClockRate = 1000000;
channelConf.LatencyTimer = latency;
channelConf.configOptions = SPI_CONFIG_OPTION_MODE0 | SPI_CONFIG_OPTION_CS_DBUS3 | SPI_CONFIG_OPTION_CS_ACTIVELOW;
// channelConf.Pin = 0xF0B0F0B0;
channelConf.Pin = 0x00000000;

// libMPSSE 초기화
Init_libMPSSE();
 
```

SPI_Write, SPI_Read, SPI_ReadWrite를 사용하여 통신을 할 수 있습니다.



### MPSSE 라이브러리 다운로드

다운로드 링크입니다.

https://www.ftdichip.com/Support/SoftwareExamples/MPSSE/LibMPSSE-SPI.htm

Example을 받으면 lib 파일과 헤더 파일이 있습니다.

AN_178 어플리케이션 노트를 참고하여 libMPSSE의 사용법을 알 수 있습니다.

샘플 소스는 sample 폴더의 static.c 코드를 참고합니다.



93C46 EEPROM과 USB로 통신하는 소스 코드입니다.



1. FT2232의 라이브러리를 사용하기 위해 header file을 include 합니다.

```c
/* Include D2XX header */
#include "ftd2xx.h"

/* Inclue libMPSSE header */
#include "libMPSSE_spi.h"

```

2. 핸들을 선언합니다.

```c
static FT_HANDLE ftHandle;
```

3. 초기화를 진행합니다.

```c
FT_STATUS status = FT_OK;
FT_DEVICE_LIST_INFO_NODE devList = {0};
ChannelConfig channelConf = {0};
uint8 address = 0;
uint32 channels = 0;
uint16 data = 0;
uint8 i = 0;
uint8 latency = 255;

channelConf.ClockRate = 5000;
channelConf.LatencyTimer = latency;
channelConf.configOptions = SPI_CONFIG_OPTION_MODE0 | SPI_CONFIG_OPTION_CS_DBUS3 | SPI_CONFIG_OPTION_CS_ACTIVELOW;
// FinalVal-FinalDir-InitVal-InitDir (for dir 0 = in, 1 = out) */
```

ClockRate 단위는 Hz 단위 이며, 5000Hz는 5KHz이므로 1MHz를 사용하기 위해서는 1000000으로 설정합니다.

SPI 모드는 0, 2만 사용할 수 있습니다.

또한 보통 CS가 LOW 상태일 때 Active되므로 SPI_CONFIG_OPTION_CS_ACTIVELOW로 설정합니다.

4. libMOPSSE를 호출합니다.

```c
Init_libMPSSE();
```

5. 각 채널을 오픈하고 초기화 합니다.

```c
status = SPI_OpenChannel(CHANNEL_TO_OPEN, &ftHandle);
APP_CHECK_STATUS(status);
status = SPI_InitChannel(ftHandle, &channelConf);
APP_CHECK_STATUS(status);
```

6. SPI 통신 설정은 끝났습니다.

```c
SPI_Write(ftHandle, 버퍼, 보낼 데이터 크기, &전송된 데이터 크기, 전송옵션)
SPI_Read(ftHandle, 버퍼, 보낼 데이터 크기, &전송된 데이터 크기, 전송옵션)
SPI_ReadWrite(ftHandle, 읽기 버퍼, 쓰기 버퍼, 보낼 데이터 크기, &전송된 데이터 크기, 전송옵션)
```

전송 옵션은 다음과 같습니다.

7. 전송옵션

- SPI_TRANSFER_OPTIONS_SIZE_INBYTES
  전송 시 바이트 단위로 데이터를 보냄 (끝을 BITS로 바꾸면 비트 단위)

- SPI_TRANSFER_OPTIONS_CHIPSELECT_ENABLE
  전송 시작 전 CS라인을 자동으로 Active 상태로 만든다.

- SPI_TRANSFER_OPTIONS_CHIPSELECT_DISABLE

  전송 후 CS 라인을 자동으로 Deactivated 상태로 만든다.

  

SPI_Write 등과 같은 함수 다음에 사용되는 APP_CHECK_STATUS(status) 함수는 status값에 따라 오류를 내뿜고 프로그램을 중지시키는 역할을 합니다.



만약 쓰는 데이터가 3바이트, 데이터 쓰기가 끝난 후 읽어야 되는 데이터가 7바이트라면 보낼 바이트 크기는 10바이트가 되어야 합니다.

```c
SPI_ReadWrite(ftHandle, readBuffer, writeBuffer, 10, &sizeTransfered, TFR_OPS);
```

이렇게 되면 readBuffer에서는 첫 3개 바이트는 dummy이며 실제로 데이터는 네번째 부터 들어온다고 볼 수 있습니다.





참고 홈페이지 : https://m.blog.naver.com/jswcomkr/221554641458



<br>
<br>

