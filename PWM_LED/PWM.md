# PWM
### Do you konw PWM?
PWM을 처음 자세히 몰랐는데, 조금 더 자세히 알게되어 정리하게 되었습니다.

사전적으로 설명하면 PWM은 펄스의 폭을 컨트롤 하는 주기제어 방법입니다.

On되는 시간에 따라 그 주기가 달라지고, 주기가 낮다면 그에 따라 전압이 약해집니다.

아래 그림은 간단히 주기를 그려보았습니다.

![Alt text](https://github.com/Funniest/Raspbreey_pi-GPIO/blob/master/PWM_LED/img/Duty.PNG)

위 그림의 선은 헤르츠로 보면 될것 같고 올라와 있는것이 Duty입니다.

한 주기당 몇 Duty만큼 올라와 있냐 라는 뜻인 것 같습니다.

예를 들어보면 주기를 50만큼 세팅하고 Duty를 10%만큼 하였다고 가정합니다.

시간은 1/50 이니까 0.02가 1주기가  됩니다.

이때 Duty가 10%니 0.02 / 10%를 또 하면 0.002만큼 HIHG상태가 이어지고 0.018만큼 LOW가 일어납니다.

### 소스코드
본 소스코드는 Raspberry pi3의 python언어로 작성되었습니다.
```
#2017-03-31
#Create by minsung kim

import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)

P_led01 = 14
P_led02 = 15

GPIO.setup(P_led01,GPIO.OUT)
GPIO.setup(P_led02,GPIO.OUT)

#GPIO.output(P_led01, GPIO.HIGH)
GPIO.output(P_led02, GPIO.HIGH)

try :
        while True :
                GPIO.output(P_led01, GPIO.HIGH)
                time.sleep(0.002)
                GPIO.output(P_led01, GPIO.LOW)
                time.sleep(0.018)
except (KeyboardInterrupt, SystemExit) :
        print('Bye~~!')
        GPIO.cleanup()
```
