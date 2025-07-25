
# 1장. 컴퓨터과학

## 컴퓨터 구조의 큰 그림

컴퓨터가 이해하는 정보 : 명령어와 데이터 (둘다 0과 1로 이루어져 있음)

컴퓨터의 핵심 부품 : CPU, 메모리(주기억장치), 캐시 메모리, 보조기억장치, 입출력장치

1. CPU
정보를 읽어들이고 해석하고 실행하는 부품. 사람으로 치면 뇌에 해당

CPU의 주요부품
- ALU(산술연산장치) : 사칙연산, 논리연산과 같은 연산을 수행할 회로로 구성되어 있는 일종의 계산기 
- 제어장치 : 명령어를 해석해 제어신호라는 전기 신호를 내보내는 장치. 제어신호란 부품을 작동시키기 위한 신호
- 레지스터 : CPU 내부의 작은 임시 저장 장치. 데이터와 명령어를 처리하는 과정의 중간값을 저장

2. 메인 메모리와 캐시 메모리

메인메모리

현재 실행 중인 프로그램을 구성하는 데이터와 명령어를 저장하는 장치로서 프로그램을 실행하기 위해서는 프로그램이 메모리에 저장되어 있어야 한다.
메인 메모리 역할을 하는 하드웨어는 RAM과 ROM이 있고 일반적으로는 RAM을 칭한다.
CPU가 원하는 정보에 빠르게 접근하기 위해 '주소'라는 개념을 사용하고 전원이 공급되지 않으면 저장된 정보가 지워지는 휘발성인 특성이 있다.

캐시 메모리 

CPU와 메모리 사이에는 반드시 하나 이상의 캐시 메모리가 존재한다
CPU가 조금이라도 빨리 메모리에 접근하기 위해 사용하는 저장장치로 즉, 빠른 메모리 접근을 보조하는 장치이다.

3. 보조기억장치

메인 메모리의 휘발성인 특성을 보조 하기 위해 전원이 꺼져도 정보가 사라지지 않는 비휘발성인 특징을 가지고
메인 메모리보다 값이 저렴하여 더 많은 용량을 가지고 있으나 느린 메모리 접근 속도를 가진 특징이 있다.

메인 메모리는 현재 실행할 프로그램을 저장한다면 보조기억장치는 보관할 프로그램을 저장한다고 할 수 있다.
따라서 CPU는 보조기억장치에서 곧바로 저장된 프로그램을 가져와 실행할 수 없고 주기억장치에 복사하여 실행할 수 있다. 

4. 입출력장치

컴퓨터 외부에 연결되어 컴퓨터 내부와 정보를 교환하는 장치

보조기억장치와 입출력장치는 완전 배타적인 개념이 아니며 보조기억장치도 결국 메모리의 보조적인 역할을 수행하는 특별한 입출력장치로 볼 수 있다.

5. 그 외 메인보드와 버스
앞서 살펴본 컴퓨터의 중요 부품들은 메인보드라고 불리는 기판에 연결되어 있다.
메인 보드에 연결된 각 부품들은 각자의 역할을 적절히 수행하기 위해 정보들을 주고 받는데 
각 컴퓨터 부품들이 정보를 주고 받는 통로를 '버스'라고 하고 버스의 종류는 다양하지만 그 중 '시스템버스'가 가장 중요하다고 할 수 있다.

## 컴퓨터가 이해하는 정보

0과 1을 나타내는 가장 작은 정보 단위를 '비트'라고 하고 N비트는 2^n개의 정보를 나타낼 수 있다.

[프로그램의 크기를 나타내는 단위]
1byte = 8bit
1Kb = 1000byte
1Mb = 1000Kb
1Gb = 1000Mb
1Tb = 1000Gb

1. 데이터 - 0과 1로 숫자 표현하기

CPU는 컴퓨터 내부에서 2진법을 사용하여 숫자를 이해하고 2진수로 표현된 수는 아래첨자로 (2)를 붙이거나 2진수 앞에 0b 붙인다.
2진법으로 숫자를 나타내면 길이가 너무 길어진다는 단점을 보완하기 위하여 컴퓨터가 이해하는 정보를 표현할 때는 16진법도 같이 사용한다.

[2진수로 소수점 나타내기]

```
int a = 0.1;
int b = 0.2;
int c = 0.3;

if (a + b == c){
    System.out.println("True");
        } 
else{
    System.out.println("Not True");
                }
```

위 코드이 결과가 True가 나올 것 같지만 결과는 Not Ture인데 이러한 오차가 발생하는 이유는 컴퓨터 내부에서는 소수점을 나타내기 위해
대표적으로 부동 소수점 표현 방식을 이용하는데 이 방식은 정밀도에 한계가 있기 때문에 이러한 오차가 발생한다.

오늘날 대부분의 컴퓨터는 2진수의 진수와 가수를 IEEE 754라는 방법의 부동소수점 방식으로 저장한다.
유의할 점은 10진수 소수를 2진수로 표현할 때 10진수 소수와 2진수 소수의 표현이 딱 떨어지지 않을 수 있다는 점이다.
컴퓨터의 저장공간은 무한하지 않기 때문에 무한히 많은 소수점을 저장할 수 없으므로 위와 같은 코드 예시와 같은 오차가 발생할 수 있는 것이다.





