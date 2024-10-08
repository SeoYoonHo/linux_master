# 1회_20240722

날짜: 2024년 7월 22일
교재: 이기적 리눅스마스터 1급 기본서
단원: Section1,2
장소: 11층 A회의실

# Section1. 운영체제 개요

## 1. 운영체제 정의 및 목적, 역할

### 1.1 운영체제의 정의

1. 사용자와 하드웨어간의 인터페이스 제공 소프트웨어
2. 하드웨어의 효율적 관리(CPU, Memory)
3. 프로그래밍 인터페이스 제공

### 1.2 운영체제의 목적

1. Throughput 향상(일정시간동안 처리하는 일의 양)
2. Turnarount Time 최소화(시스템 응답시간)
3. 신뢰도 향상
4. 사용가능도 향상(가용 자원)

### 1.3 운영체제의 역할

1. 하드웨어 제어,입/출력 관리
2. 다중 이용자 기능
3. 자원 스케줄링
4. System call 제공(프로그램이 사용할 수 있도록 커널에서 제공하는 서비스)
5. 오류복구기능 제공
6. 데이터 저장기능 및 원격 네트워크 기능 제공
7. 사용자 인터페이스 제공

## 2. 운영체제의 구조와 기능

### 2.1 운영체제의 구조

1. 응용프로그램을 실행하거나 shell, gui, batch job등을 통해 운영체제 기능 사용 가능
2. 응용프로그램은 system call을 통해 커널서비스 사용
3. HAL(Hardware Abstracton Layer) 하드에웨어 추상계층 제공(하드웨어 인터페이스... 드라이버는 인터페이스 구현 필요)

### 2.2 운영체제의 기능

1.  리소스 관리 기능
2.  자원 스케줄링
3. 다양한 하드웨어 관리(LAN카드, USB등), 네트워크 제어기능
4. 데이터 관리 기능(ex. 파일시스템), 자원 공유기능
5. 자원 보호 기능(보안)
6. 오류검사/복구 기능(파일시스템 손상등)
7. 가상화 기능(윈도우의 Hyper-V)

## 3. 운영체제의 운용 기법

### 3.1 운영체제 운용 기법의 종류

1. 일괄처리 시스템(Batch Processing System)
    1. 여러 작업을 하나의 단일작업으로 묶어서 처리
    2. 작업이 실행되면 결과가 나올때까지는 기다려야함(중간개입 허용 X)
    3. 자원 효율성 떨어짐(ex, IO작업)
2. 다중 프로그래밍 시스템(Multi Programing System)
    1. CPU가 유휴상태(Idle)일 때 다른 프로그램에 자원 할당(ex, 한 프로그램에서 IO작업중일 때, 다른 프로그램에 CPU 자원 할당)
    2. 사용자 입장에서는 단일 CPU에서 여러 프로그램 실행되는것처럼 보임
3. 시분할 시스템(Time Sharing System)
    1. 타임 슬라이스 또는 타임 퀀넘이라 부르는 일정 작업 시간동안만 작업을 실행하는 기법
    2. 다중 프로그래밍보다 더욱 동시에 여러 작업일 실행되는것처럼 보임
4. 다중 처리 시스템(Multi-Processing System)
    1. CPU가 여러대. 병렬 처리 시스템이라고도 함(Parallel Processing System)
    2. 비대칭적 다중처리(프로세스의 주종 관계가 있음), 대칭적 다중처리로 나누어짐(주종관계 없음)
    3. 대칭적 다중처리는 SMP(Symmetric Multi-Processing)(프로세스간 메모리 공유)와 MPP(Massively Parallel Processing)(메모리 비공유)로 나누어짐 ([https://blog.naver.com/kkpa1002/20107715123](https://blog.naver.com/kkpa1002/20107715123))
5. 실시간 처리 시스템(Real Time Processing System)
    1. 수행 시간의 제약이 있는 시스템
    2. 제약의 엄격한 정도에 따라 경성/연성(Hard/Soft) 실시간 처리 시스템으로 나누어짐
    3. 경성은 보통 무기 제어, 산업 로봇등에서 사용
    4. 연성은 동영상 재생 시스템 등
6. 다중 모드 시스템(Multi-Mode System)
    1. 위의 시스템들을 혼용하여 사용하는 시스템
7. 분산 처리 시스템(Distribute Processing System)
    1. 독립적인 운영체제를 갖는 컴퓨터 시스템을 통신망으로 연결한 시스템
    2. 한 운영체제 하의 메모리 공유방식(강결함)이 아닌 통신으로 연결되고 상호작용하는 약결합 시스템
    3. 물리적인 시스템간 연결을 넘어 가상화등을 활용하여, 가상화 시스템간의 분산처리 형태로 진화

### 3.2 운영체제 운영기법의 발전

![스크린샷 2024-07-21 오후 12.34.49.png](1%E1%84%92%E1%85%AC_20240722%20ea5280ed5b454ab19cc9e9d8ddaf42c7/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2024-07-21_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.34.49.png)

## 4. 운영체제의 사례

### 4.1 데스크톱 및 서버 운영체제

1. 윈도우
    1. 1975년 빌게이츠와 폴 앨런이 설립한 MS에서 그래픽 인터페이스 운영체제
    2. 매년 2차례 대규모 업데이트
    3. window 10, xp, vista, 7, 8등의 모체가 되는 운영체제는 기업용 OS Windows NT3.1임
2. macOS
    1. 스티브 잡스와 워즈니악이 설립한 애플에서 개발한 유닉스/다윈 기반 mac 기기 전용 운영체제
    2. 스티브잡스가 설립했더 NeXT에서 만든 운영체제의 후속운영체제
3. 리눅스
    1. 핀란드 헬싱키 대학생 리누스 토발즈에 의해 개발된 유닉스 호환 운영체제.(1991.09.17 0.01버전 개발)
    2. 1991.10.5 0.02버전이 뉴스그룹에 발표 
    3. 수많은 개발자들이 공동으로 개발하는 공개프로젝트 형식으로 진행
    4. 리차드 스톨만의 GNU프로젝트에서 리눅스 커널에서 동작하는 다양한 어플리케이션을 개발하고 제공함.(데스크톱용 리눅스 포함)
    5. 데스크톱용: 우분투, 페도라, 데비안, 오픈수세 등
    6. 서버용: 레드햇, CenOS, 로키 리눅스, 우분투 서버 등
4. 유닉스
    1. 1969년 미국의 AT&T사의 벨 연구소에서 개발된 운영체제(다중사용자 방식의 시분할 운영체제)
    2. 대부분 C언어로 개발됨
    3. 초반에 무료로 연구소 및 대학교에 보급되어, 다양한 버전이 등장하게 되었음(SystemV, BSD)

### 4.2 모바일 및 임베디드 운영체제

1. 안드로이드
    1. 2005년 구글의 안드로이드사 인수후 2007년 11월 무료공개
    2. 리눅스 커널, C/C++ 라이브러리, 안드로이드 런타임 기반 구성
    3. 안드로이드 런타임이라는 가상머신 제공. 자바나 코틀린으로 개발된 애플리케이션을 별도의 프로세스에서 실행하는 구조
    4. OHA: Open Hand set Aliance에서 공개표준을 위해 개발중
2. iOS, watchOS, iPadOS, tvOS
    1. iOS: iPhone, iPod Touch, iPad를 구동하기 위한 운영체제
    2. watchOS: Apple Watch를 구동하기 위한 운영체제
    3. iPadOS: iPad를 위한 운영체제(콘텐츠 소비에서 생산하는 기기로)
    4. tvOS: 애플TV용 iOS 운영체제
3. 타이젠
    1. 인텔과 삼성의 주도로 만든 모바일, 웨어러블, IVI(차량용) 운영체제
    2. 구글의 안드로이드 견제용
    3. 모바일 X, 스마트 TV등에서 사용됨
4. 임베디드 리눅스
    1. 라즈비안: 라즈베리파이용 데비안 리눅스 기반 운영체제
    2. webOS: LG전자에서 개발중인 모바일 및 스마트TV OS

### 4.3 IoT(Internet of Things) 운영체제

1. Linux
    1. Android Things: 안드로이드 기반 사물 인터넷 플랫폼
    2. Ubuntu Core: 우분투 기반 IoT 운영체제(보안강화)
2. Windows IoT
    1. 엔터프라이즈, 모바일 엔터프라이즈, IoT 모바일, 코어 에디션으로 나뉨
3. RTOS
    1. FreeRTOS: 마이크로 컨트롤러용 오픈소스 운영체제
    2. VxWorks: 미국의 윈드리버사에서 판매하는 운영체제
    3. QNX: 유닉스 기반 실시간 상업용 운영체제(주로 임베디드 시장, 자동차 산업에서 사용)
4. 경량 OS
    1. Contiki: 한정된 메모리, 저전력, 무선통신, IoT디바이스에 초점을 둔  BSD라이선스 오픈서스 네트워크 운영체제(스마트 도시등에서 쓰임, 조명제어, 각종 알람시스템 등)
    2. TinyOS: UC버클리에서 개발한 센서 네트워크영 무료 운영체제
    3. RIOT: IoT 겨냥한 실시간 운영체제. 8,16,32bit 플랫폼 타겟

# Sections2. 리눅스의 기초

## 1. 리눅스 개요

### 1.1 리눅스 정의 & 의미

1. 1991년 리누스 토발즈에 의해 오픈소스로 개발된 유닉스 호환용 운영체제
2. 초기 개발된 형태는 단순히 리눅스 커널만을 의미(파일관리, 네트워크 관리등은 없음)
3. 현재는 FSF(Free Software Foundation)가 GNU프로젝트를 통해 다양한 배포판 제공 → GNU/Linux라고도 부름

### 1.2 리눅스의 일반적 특징

1. 이식성
    1. C언어 기반이라 이식성이 높음(Why?)
    2. 다양한 CPU 아키텍처에 적용
2. 자유 소프트웨어
    1. 다수의 개발자에 의해 수정/배포됨.(단 수정된 프로그램은 소스코드와 함께 배포되어야함.)
    2. 대부분 GPL(General Purpose License), LGPL(Library/Lesser General Purpose License)라이선스를 따름
3. 멀티 유저
    1. 다수의 사용자가 네트워크를 통하여 접근 가능
4. 멀티 프로그래밍
    1. 다수의 프로그램 실행가능
5. 계층적 파일 시스템
    1. 표준화된 디렉토리 구조 정의([https://sasca37.tistory.com/281](https://sasca37.tistory.com/281))
    
    ![Untitled](1%E1%84%92%E1%85%AC_20240722%20ea5280ed5b454ab19cc9e9d8ddaf42c7/Untitled.png)
    
6. 셸
    1. 기능수행을 위한 명령어 프로그램 제공
    2. 명령어 해석기능, 프로그래밍 기능, 환경설정 기능 제공
7. 보안
    1. 유닉스의 보안모델 임의접근제어(Discretionary Access Control), 확장 임의접근제어(Extended DAC) 제공 → DAC: 주체(사용자)마다 권한 부여
    2. 네트워크 정책에 따라 노드나 라우터로 동작 가능. netfilter, iptables, ebtables, arptable등의 모듈 제공
    3. IPSec 네트워크 스택 제공
    4. 강제접근제어(Mandatory Access Control)을 강화한 SELinux(Security Enhanced Linux)가 존재 → MAC : 주체(사용자) 보안등급에 따른 접근제어

### 1.3 리눅스의 기술적 특징

1. 모놀리틱 커널
    1. 운영체제 제공 서비스(파일시스템, 장치관리, I/O, 프로세스 처리기 등)를 하나의 커널로 구현하는 방식
    2. 효율적이지만 기능변경의 어려움이 있어 유지보수가 어려움
    3. 참고. [https://gamedoridori.tistory.com/155](https://gamedoridori.tistory.com/155)
2. 장치의 파일화
    1. 리눅스는 시스템의 자원을 모두 파일 단위로 인식.
    2. 파일은 디렉터리, 인반 파일, 특수파일로 나눌 수 있다. 특수파일은 다시 장치파일, 파이프 소켓등으로 나누어짐
    3. 장치파일: 문자 장치파일(키보드, 마우스 등), 블록 장치파일(하드디스크, CD등 저장장치)로 나누어짐
    4. 파이프: 프로세스간 통신(특정 프로그램의 표준출력을 다른 프로그램의 표준입력으로)
    5. 소켓: 네트워크 입출력 담당 API
    6. 참고. [https://dololak.tistory.com/290](https://dololak.tistory.com/290)
3. 다양한 파일 시스템의 지원
    1. ext2, ext3, ext4 자체파일 시스템 제공
    2. FAT32, NTFS 등 윈도우파일시스템 제공
    3. SMP, CIFS 네트워크 파일시스템 제공
    4. 저널링 파일 시스템을 지원 → 시스템의 변경사항을 기록([https://zoosso.tistory.com/494](https://zoosso.tistory.com/494))
4. 가상메모리
    1. 물리적인 메모리의 크기를 극복하기 위한 메모리 관리기법중 하나
    2. 각 프로그램이 실제 메모리 주소가 아니라 가상 메모리 주소를 할당하는 방식 → 실제 메모리 공간 이상의 데이터를 저장할 순 없지만, **공간을 연속적으로 사용가능**
    3. 동작중인 프로세스만 물리 메모리에 로드, 사용빈도가 낮은 메모리는 디스크에 저장(요구 페이징. Demand Paging)
    4. [https://jeongzero.oopy.io/359eaa11-b6e6-466c-a066-9ae582c886d4](https://jeongzero.oopy.io/359eaa11-b6e6-466c-a066-9ae582c886d4)
5. 스왑
    1. 디스크 ↔ 물리메모리 간의 데이터 이동 과정(스왑 아웃: 메모리 → 디스크4, 스왑 인: 디스크 → 메모리)
    2. 디스크상에 스왑공간이 존재하며, 전용 파일 또는 파티션 필요
    3. 스왑 빈도는 /etc/sysctl.conf의 vm,swapiness설정 → 10으로 설정하면 메모리의 가용량이 10%일 때 스왑 시도
    4. free 명령어로 스왑영역의 용량 확인 가능
    5. 동적으로 스왑공간의 크기조정 X → 공간낭비
6. 동적 라이브러리와 정적 라이브러리
    1. 정적라이브러리
        1. 컴파일시점 링크, 프로세스가 실행될 때 메모리 로드
        2. 여러 프로그램이 로드할 떄 메모리에 중복로드
        3. 실행속도 빠름
    2. 동적 라이브러리
        1. 특정 디렉터리에 만들어 모아 놓고 명령어와 링크를 걸어둠
        2. 명령어 사용시 파일을 가져와 메모리에 로드
        3. 효율적이지만 속도가 느림
        4. etc/ld.so.conf 를 검색하여 동적라이브러리 로드.
        5. [https://csj000714.tistory.com/491](https://csj000714.tistory.com/491)
7. 파이프
    1. 프로세스의 표준 출력을 다른 프로세스의 표준입력으로
    2. 터미널상 명령어 기호는 '|’
8. 리다이렉션
    1. 프로세스의 표준 입출력을 다른 파일, 화면, 장치등에서 받도록 재지정 할 수 있는 매커니즘
        
        ![스크린샷 2024-07-21 오후 4.00.37.png](1%E1%84%92%E1%85%AC_20240722%20ea5280ed5b454ab19cc9e9d8ddaf42c7/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2024-07-21_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.00.37.png)
        
    2. [https://sasca37.tistory.com/284](https://sasca37.tistory.com/284)
9. 가상콘솔
    1. 하나의 화면에서 여러개의 콘솔 사용 가능.
    2. 총 6개 제공, ctrl + alt + F1~F6을 통해 콘솔 생성가능
    3. 화면전환은 alt + F1~F6

### 1.4 리눅스의 장단점

1. 장점
    1. 오픈소스 → 라이선스 비용 절감
    2. 전세계 개발자들의 유지보수 → 안정성, 보안성
    3. 다양한 네트워크 환경 지원
    4. 목적에 따른 다양한 버전 지원(서버, 개발, 개인 등)
2. 단점
    1. 기술지원 네트워크의 부재
    2. 상용 소프트웨어 부족
    3. 최신 하드웨어 기기에 대한 드라이버 지원

## 2. 리눅스와 GNU 그리고 오픈소스 라이선스

### 2.1 리눅스와 GNU(GNU’s not Unix)

1. GNU GPL 라이선스
    1. 유닉스 소스코드 일체 사용안함
    2. GNU GPL라이선스를 갖는다. 누구나 자유롭게 사용, 변경, 배포가 가능 → 자유 소프트웨어
2. GNU
    1. GNU’s Not Unix → GNU는 유닉스가 아니다 라는 뜻 → 유닉스와 호환은 되지만 유닉스는 아님
    2. 소트웨어 상업화 반대(리차드 스톨만 주축)
3. 자유 소프트웨어
    1. 조건
        1. 어떠한 목적에서든 실행가능
        2. 프로그램 변경 가능
        3. 복제 및 배포가능
        4. 프로그램 환원 가능
    2. 변경과 환원은 소스코드 제공이 필요
4. 카피레프트
    1. 카피라이트(저작권)의 반대 → 사용자가 자유롭게 사용할 수 있도록 법률적 보장
    2. GNU GPL 라이선스가 카피레프트를 구현

### 2.2 오픈소스

1. 코드를 누구나 볼 수 있음
2. 자유소프트웨어와 유사하지만 → 오픈소스는 소스에 치중되어있음

### 2.3 오픈소스 라이선스

![스크린샷 2024-07-21 오후 4.39.21.png](1%E1%84%92%E1%85%AC_20240722%20ea5280ed5b454ab19cc9e9d8ddaf42c7/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2024-07-21_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.39.21.png)

1. GPL 라이선스
    1. 자유소프트웨어재단에서 만든 라이선스
    2. 소프트웨어의 실행, 연구, 공유, 수정의 자유를 보장
    3. GPLv1(소스코드 동시배포), GPLv2(소스코드 공개 X → 바이너리 공개X 즉, 사용못함), GPLv3(소프트웨어 특허에 대한 대처, 라이선스 호환 등)
2. LGPL 라이선스
    1. 자유소프트웨어 재단에서 GPL, BSD, MIT를 절충하여 만든 새로운 라이선스
    2. LGPL 프로그램은 카피레프트 적용하지만, 프로그램을 이용하는 타 프로그램은 카피레트프 X
    3. LGPL 프로그램 링크할 경우 소스코드 공개필요  X
    4. LGPL 프로그램 수정개발 → 소스코드 제공
    5. LGPL 프로그램 수정개발 → GPL가능 (반대X)
3. BSD 라이선스
    1. 버클리 캘리포니아 공개 소프트웨어 라이선스
    2. 프로그램 수정가능, 제한없이 배포 가능(단, 저작권지 이름, BSD 라이선스 표기)
    3. 소스코드 제공의 의무가 없음
4. 아파치 라이선스
    1. 아파치 재단에서 만든 라이선스
    2. 누구나 다운 가능, 상업적 목적 이용 가능
    3. 소스코드 제공의 의무가 없음
5. MPL 라이선스
    1. BSD, GPL 의 혼합
    2. 배포시 소스코드 공개의무 있음
    3. 포함된 MPL외의 다른 코드까지는 공개X
6. MIT 라이선스
    1. MIT 대학교 소프트웨어 라이선스
    2. 배포시 소스코드 제공의 의무 없음

## 3. 리눅스 역사와 리눅스 배포판

### 3.1 리눅스의 역사(자세한건 책)

1. 리차드 스톨만의 자유 소프트웨어운동(GNU GPL 라이선스 발표) - 1984~1991
2. 리누스 토발즈의 리눅스 배포(GNU GPL 라이선스 사용) - 1991 ~ 1993
3. 리눅스 커널 1.0 - 1994
4. 오픈소스 용어 사용 - 1998
5. 다양한 배포판(레드햇 리눅스 CentOS, 데비안 리눅스 우분투 등) - 2003 ~ 2005
6. CentOS 개발중단에 따른 로키 리눅스 등장 - 2020년 이후

### 3.2 리눅스 배포판 분류

1. [https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg](https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg) —> 엄청 많음
    
    ![Untitled](1%E1%84%92%E1%85%AC_20240722%20ea5280ed5b454ab19cc9e9d8ddaf42c7/Untitled%201.png)
    
2. 크게보면 데비안, 레드햇, 슬랙웨어 등으로 나눠볼 수 있음
3. 슬랙웨어 : 가장 오래된 배포판
4. 데비안 : 기업 재단보다는 커뮤니티에 의한 배포판 (패키지 관리자 : apt, dpkg)
5. 레드햇: 고객 유료 서비스를 통한 수익 창출(패키지관리자 : rpm, yum)

### 3.3 배포판 세부설명

상세설명은 책을 참고…

## 4. 리눅스 활용 분야

### 4.1 서버,메인 프레임

1. 웹서버 호스팅용도
2. 메인프레임 에서도 많이 사용됨(일종의 비싼 서버컴퓨터라고 보면 될듯)
3. 메인 프레임 : 장치를 다수의 사람에게 동시에 지원할 수 있는 컴퓨터 → 과거 개인용 컴퓨터가 없던 시절 사용하던 방법이 시초
4. 보안과 높은 안정성으로 아직도 사용이 많이됨(단점. 비쌈)

### 4.2 스마트 디바이스

1. 앞에서 말했듯 안드로이드도 리눅스 기반
2. 다양한 스마트 디바이스의 운영체제가 리눅스 기반

### 4.3 임베디드 디바이스

1. Android Thins, Ubuntu Core등 제공되고있음
2. 교육목적으로 오픈소스 하드웨어 널리 보급됨

### 4.4 게이밍 디바이스

1. 벨브사, 엔비디아 등에서 릴리즈되고 있다고 한다.

### 4.5 리눅스 클러스터

1. 고계산용 클러스터
    1. 과학 계산용
    2. 큰 계산을 위해 중소형급 시스템 여러대
2. 부하분산 클러스터
    1. 로드밸런서
3. 고가용성 클러스터
    1. Active - Standby 구조의 서버구축방법
    2. DR도 마찬가지
    3. 장애시간을 제로로 만드는것이 궁극적