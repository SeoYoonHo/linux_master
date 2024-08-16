1. /var/log/pods 에 쿠버네티스 pod의 로그가 있음
2. 부팅시 메시지 손실을 방지하기 위해 커널링 버퍼 생성 -> printk() 함수에 의한 모든 메시지 저장 -> 해당 버퍼를 syslog에 저장
3. logrotate는 기본적으로 rename명령을 기반으로 동작

문제1. 모든 서비스(*)에 대해 가장 최고 수준의 위험한 상황인 경우에(emerg, panic) root 및 ihduser 사용자의 터미널로 관련 로그를 전송하는 설정은?(rsys.conf)

문제2. 메일 서비스에서 발생하는 error 수준 메시지만 /var/log/main_error에 기록하는 설정(rsys.conf)




정답1
*.emerg      root,ihduser
정답2
mail.=error     /var/log/main_error